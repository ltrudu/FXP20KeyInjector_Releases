# 🔧 Troubleshooting Guide

Comprehensive troubleshooting guide for common FXP20 Key Injector issues and their solutions.

---

## 🆘 Quick Diagnosis

### 🔍 Problem Categories
- **🔌 [Connection Issues](#-connection-issues)** - Device not connecting or disconnecting
- **⌨️ [Data Delivery Issues](#️-data-delivery-issues)** - Tags not reaching target applications  
- **🖥️ [Application Issues](#️-application-issues)** - GUI problems, crashes, startup issues
- **🌐 [MQTT Issues](#-mqtt-issues)** - MQTT broker connection and messaging problems
- **⚡ [Performance Issues](#-performance-issues)** - Slow response, high latency, memory usage
- **⚙️ [Configuration Issues](#️-configuration-issues)** - Settings not working, file problems

---

## 🔌 Connection Issues

### Device Not Detected

#### Symptoms
- COM port dropdown is empty
- "No COM ports found" error message
- Device not listed after clicking "Refresh Values"

#### Solutions
1. **🔌 Check Physical Connection**
   - Verify USB cable is securely connected
   - Try a different USB cable
   - Test different USB ports on PC
   - Ensure FXP20 device is powered on

2. **👨‍💻 Check Device Manager**
   - Open Windows Device Manager
   - Look for FXP20 under "Ports (COM & LPT)"
   - If device shows with yellow warning, update drivers
   - If not visible, check "Universal Serial Bus controllers"

3. **🔄 Restart Components**
   - Unplug FXP20, wait 10 seconds, reconnect
   - Restart FXP20KeyInjector application
   - Try different USB port
   - Restart computer if necessary

4. **👤 Administrator Rights**
   - Right-click FXP20KeyInjector.exe
   - Select "Run as Administrator"
   - Confirm UAC prompt if shown

### Connection Fails

#### Symptoms
- COM port is detected but "Connect" button fails
- Error messages about port access
- Connection timeout errors

#### Solutions
1. **🚫 Close Conflicting Applications**
   ```bash
   # Check what's using the COM port
   netstat -ab | findstr :COM5
   ```
   - Close other RFID software
   - Exit device management applications
   - Check for background processes using the port

2. **⚙️ Try Different Baud Rates**
   - Start with 115200
   - Try 460800
   - Use 921600 (default) last
   - Save working configuration

3. **🔄 Reset Device Connection**
   - Disconnect device physically
   - Close FXP20KeyInjector
   - Reconnect device
   - Restart application
   - Try connection again

4. **🛡️ Check Windows Security**
   - Temporarily disable antivirus scanning of the application
   - Add FXP20KeyInjector to antivirus exclusions
   - Check Windows Defender settings

### Frequent Disconnections

#### Symptoms
- Device connects but disconnects shortly after
- Intermittent "Connection lost" messages
- Reading stops unexpectedly

#### Solutions
1. **🔌 Hardware Check**
   - Replace USB cable with high-quality cable
   - Use powered USB hub if needed
   - Check for loose connections
   - Test with different PC if available

2. **⚡ Power Management**
   - Open Device Manager
   - Find your COM port device
   - Right-click → Properties → Power Management
   - Uncheck "Allow computer to turn off this device"

3. **🔋 FXP20 Power Settings**
   - Check FXP20 power settings
   - Ensure adequate battery level
   - Verify power adapter if using external power
   - Check for overheating issues

---

## ⌨️ Data Delivery Issues

### Tags Not Reaching Target Application

#### Symptoms
- FXP20 reads tags (visible in "Last EPC Read")
- No data appears in target application
- "EPC Sent" counter remains at 0

#### Solutions
1. **🎯 Verify Window Filter**
   - Click "Refresh Values" to update window list
   - Select correct window from dropdown
   - Check that filter text matches window title exactly
   - Test with simple filter like "Notepad"

2. **👁️ Application Focus**
   - Ensure target application window is visible and active
   - Click in the target application before scanning
   - Avoid switching windows during tag reading
   - Test with simple text editor first

3. **🧪 Use Debug Tools**
   - Type test data in "Text To Send" field
   - Click "Send Clipboard" to test clipboard paste method
   - Click "Send Key Events" to test key injection method
   - Verify data appears in target application

4. **🔄 Try Different Send Protocol**
   - Switch from KEYINJECTION to CLIPBOARDPASTE
   - Or switch from CLIPBOARDPASTE to KEYINJECTION
   - CLIPBOARDPASTE is generally more reliable
   - Save configuration after finding working method

### Partial or Corrupted Data

#### Symptoms
- Only part of tag data appears
- Characters are missing or incorrect
- Data appears in wrong format

#### Solutions
1. **⏱️ Adjust Timing Settings**
   ```xml
   <!-- Increase clipboard paste delay -->
   <ClipboardPasteDelay>1000</ClipboardPasteDelay>
   ```
   - Increase delay for slower applications
   - Try values: 100ms, 500ms, 1000ms, 2000ms
   - Test to find minimum working delay

2. **🔤 Check Data Formatting**
   ```xml
   <!-- Configure data formatting -->
   <AddCSVSeparator>false</AddCSVSeparator>
   <AddCR>true</AddCR>
   <AddLF>false</AddLF>
   ```
   - Remove CSV separators if not needed
   - Adjust CR/LF settings for target application
   - Test with different combinations

3. **🎯 Target Application Compatibility**
   - Test with Notepad first (most compatible)
   - Check if target application accepts paste operations
   - Verify application can handle the data volume
   - Consider application-specific input requirements

### Duplicate Tag Readings

#### Symptoms
- Same tag appears multiple times
- Continuous reading of single tag
- High volume of duplicate entries

#### Solutions
1. **🔄 Enable Duplicate Filtering**
   ```xml
   <RemoveDuplicates>true</RemoveDuplicates>
   <HookKeyboardToStartReading>true</HookKeyboardToStartReading>
   <HookKeyboardReadingDurationInMs>3000</HookKeyboardReadingDurationInMs>
   ```

2. **⏱️ Use Timed Reading Sessions**
   - Configure GPIO or keyboard-triggered reading
   - Set appropriate reading duration
   - Use session-based reading instead of continuous

3. **📡 Antenna Configuration**
   - Adjust transmit power to reduce range
   - Modify antenna sensitivity settings
   - Configure session parameters appropriately

---

## 🖥️ Application Issues

### Application Won't Start

#### Symptoms
- Double-click has no effect
- Error messages on startup
- Application crashes immediately

#### Solutions
1. **⚡ Check .NET Framework**
   - Install .NET Framework 4.8 or higher
   - Download from [Microsoft's site](https://dotnet.microsoft.com/en-us/download/dotnet-framework/net48)
   - Restart computer after installation

2. **👤 Run as Administrator**
   - Right-click FXP20KeyInjector.exe
   - Select "Run as administrator"
   - Confirm UAC prompt

3. **📄 Check Config.xml**
   - Delete Config.xml file (will be recreated with defaults)
   - Check for XML syntax errors if manually edited
   - Ensure file is not corrupted or read-only

4. **🛡️ Antivirus Issues**
   - Add FXP20KeyInjector to antivirus exclusions
   - Temporarily disable real-time protection
   - Check quarantine folder for blocked files

### Application Freezes or Crashes

#### Symptoms
- Application becomes unresponsive
- Unexpected shutdowns
- Error dialog boxes

#### Solutions
1. **🔄 Restart Clean**
   - Close application completely
   - Disconnect FXP20 device
   - Restart application
   - Reconnect and try again

2. **📊 Check System Resources**
   - Open Task Manager
   - Monitor CPU and memory usage
   - Close unnecessary applications
   - Check available disk space

3. **🧹 Clear Application Data**
   - Clear "EPC Sent" list using Clear button
   - Restart application periodically during heavy use
   - Monitor tag processing counters

4. **⚙️ Reset Configuration**
   - Backup current Config.xml
   - Delete Config.xml file
   - Restart application to generate defaults
   - Reconfigure settings gradually

### GUI Issues

#### Symptoms
- Controls not responding
- Display corruption
- Missing interface elements

#### Solutions
1. **🖥️ Display Settings**
   - Check Windows display scaling (100% recommended)
   - Update graphics drivers
   - Try different screen resolution
   - Test on different monitor if available

2. **🔄 Application Reset**
   - Close and restart application
   - Run as Administrator
   - Check for Windows updates
   - Try compatibility mode (Windows 8/7)

---

## 🌐 MQTT Issues

### MQTT Connection Failed

#### Symptoms
- "MQTT connection failed" messages
- No data appearing on MQTT topics
- Control commands not working

#### Solutions
1. **🔍 Check Broker Status**
   ```bash
   # Test broker connectivity
   telnet mqtt-broker-ip 1883
   ```
   - Verify broker is running and accessible
   - Check network connectivity
   - Confirm port 1883 is open

2. **🔐 Authentication Issues**
   ```xml
   <!-- Verify credentials in Config.xml -->
   <MQTTUser>user</MQTTUser>
   <MQTTPassword>password</MQTTPassword>
   ```
   - Confirm username exists on broker
   - Verify password is correct
   - Check broker authentication configuration

3. **📡 Network Configuration**
   - Check firewall settings (port 1883)
   - Verify network connectivity
   - Test with MQTT client tools (MQTT Explorer)
   - Try different broker if available

### MQTT Messages Not Received

#### Symptoms
- FXP20KeyInjector shows MQTT connected
- No messages appear in subscriber applications
- Control commands don't work

#### Solutions
1. **🎯 Check Topic Configuration**
   ```xml
   <!-- Verify topic names -->
   <MQTTSendTopic>fxp20/data</MQTTSendTopic>
   <MQTTControlTopic>fxp20/control</MQTTControlTopic>
   ```
   - Ensure topics match between publisher and subscriber
   - Check for typos in topic names
   - Topics are case-sensitive

2. **🧪 Test with MQTT Client**
   ```bash
   # Subscribe to data topic
   mosquitto_sub -h localhost -p 1883 -u user -P password -t "fxp20/data"
   
   # Publish control command
   mosquitto_pub -h localhost -p 1883 -u user -P password -t "fxp20/control" -m "Connect"
   ```

3. **📊 Check QoS Settings**
   - Verify Quality of Service levels
   - Check retained message settings
   - Monitor broker logs for message delivery

---

## ⚡ Performance Issues

### Slow Tag Reading

#### Symptoms
- Long delays between tag presentations and data appearance
- High latency in data processing
- Sluggish application response

#### Solutions
1. **⚙️ Optimize Configuration**
   ```xml
   <!-- Reduce delays -->
   <ClipboardPasteDelay>100</ClipboardPasteDelay>
   <BatchSize>20</BatchSize>
   
   <!-- Use faster protocol -->
   <Protocol>CLIPBOARDPASTE</Protocol>
   ```

2. **🖥️ System Optimization**
   - Close unnecessary applications
   - Increase system RAM if needed
   - Use SSD storage if available
   - Update to latest Windows version

3. **📡 RF Optimization**
   - Adjust antenna power settings
   - Optimize antenna positioning
   - Reduce RF interference sources
   - Configure appropriate session settings

### High Memory Usage

#### Symptoms
- Application memory usage grows over time
- System becomes sluggish
- Out of memory errors

#### Solutions
1. **📊 Monitor and Clear Data**
   - Regularly click "Clear" button to empty EPC Sent list
   - Disable "Show EPC Sent" for high-volume operations
   - Restart application periodically during heavy use

2. **⚙️ Configuration Optimization**
   ```xml
   <!-- Reduce batch size for memory-constrained systems -->
   <BatchSize>5</BatchSize>
   ```

3. **🔄 Periodic Maintenance**
   - Schedule application restarts
   - Monitor system resources
   - Clear Windows temporary files
   - Defragment hard drive if using HDD

---

## ⚙️ Configuration Issues

### Config.xml Not Loading

#### Symptoms
- Settings revert to defaults on restart
- Manual configuration changes ignored
- "Configuration not found" messages

#### Solutions
1. **📍 Check File Location**
   - Ensure Config.xml is in same directory as FXP20KeyInjector.exe
   - Verify file is not hidden or read-only
   - Check file permissions (should be readable/writable)

2. **📄 Validate XML Syntax**
   - Check for proper XML formatting
   - Ensure all tags are properly closed
   - Validate special characters are properly encoded
   - Use XML validator tools if needed

3. **💾 Save and Load Process**
   - Use "Save Config" button after making GUI changes
   - Click "Load Config" to refresh from file
   - Test with minimal configuration first

### Invalid Configuration Values

#### Symptoms
- Settings don't take effect
- Error messages about configuration
- Application behaves unexpectedly

#### Solutions
1. **✅ Validate Settings**
   ```xml
   <!-- Correct format examples -->
   <ComPort>COM5</ComPort>                    <!-- Not: com5 or 5 -->
   <BaudRate>921600</BaudRate>               <!-- Must be valid baud rate -->
   <Protocol>CLIPBOARDPASTE</Protocol>       <!-- Exact case matching -->
   <AutoConnect>true</AutoConnect>           <!-- true/false, not yes/no -->
   ```

2. **🔄 Reset to Defaults**
   - Delete Config.xml file
   - Restart application
   - Reconfigure settings through GUI
   - Test each setting individually

---

## 🛠️ Advanced Troubleshooting

### Enable Logging

#### Windows Event Viewer
1. **🔍 Open Event Viewer** (Windows key + R, type `eventvwr.msc`)
2. **📂 Navigate** to Windows Logs → Application
3. **🔍 Filter** for events from FXP20KeyInjector
4. **📋 Review** error messages and timestamps

#### Application Debugging
1. **🧪 Use Debug Section** in application
2. **📊 Monitor Status Labels** for error messages
3. **🔢 Check Counter Values** for data flow verification
4. **📋 Review EPC Sent List** for successful transmissions

### System Diagnostics

#### Hardware Testing
```bash
# Check COM port availability
mode COM5
```

#### Network Testing (for MQTT)
```bash
# Test MQTT broker connectivity
telnet mqtt-server 1883

# Test with mosquitto clients
mosquitto_pub -h localhost -t test -m "hello"
mosquitto_sub -h localhost -t test
```

### Performance Monitoring

#### Task Manager Monitoring
- **💻 CPU Usage** - Should be low during normal operation
- **🧠 Memory Usage** - Monitor for memory leaks
- **💾 Disk I/O** - Check for excessive disk activity
- **🌐 Network** - Monitor MQTT traffic if applicable

#### Application Metrics
- **📊 Tags Processed** - Verify counter increments
- **⏱️ Response Times** - Monitor for increasing delays
- **🔌 Connection Stability** - Watch for frequent disconnections

---

## 📋 Troubleshooting Checklist

### Before Contacting Support
- [ ] ✅ Tried restarting application and device
- [ ] 🔌 Verified physical connections
- [ ] 👤 Run as Administrator
- [ ] 🔄 Reset configuration to defaults
- [ ] 🧪 Tested with debug tools
- [ ] 📊 Checked system requirements
- [ ] 🛡️ Verified antivirus exclusions
- [ ] 📄 Validated Config.xml syntax

### Information to Collect
- **🖥️ System Info**: Windows version, .NET Framework version
- **📱 Hardware**: FXP20 model, firmware version
- **⚙️ Configuration**: Current Config.xml settings
- **🐛 Error Messages**: Exact text of any error messages
- **📊 Behavior**: Detailed description of problem
- **🔄 Steps**: What actions lead to the issue
- **📈 Frequency**: How often does the problem occur

---

## 🆘 Getting Additional Help

### Self-Service Resources
1. **📚 [Documentation Wiki](Home.md)** - Complete user guides
2. **📄 [PDF Manual](https://github.com/ltrudu/FXP20KeyInjector_Releases/blob/master/FXP20KeyInjector-HowTo.pdf)** - Detailed technical documentation
3. **🔍 [GitHub Issues](https://github.com/ltrudu/FXP20KeyInjector_Releases/issues)** - Search existing issues

### Reporting Issues
When creating a new issue, include:

1. **📋 Issue Template**
   ```markdown
   ## Problem Description
   Brief description of the issue
   
   ## Steps to Reproduce
   1. Step one
   2. Step two
   3. Step three
   
   ## Expected Behavior
   What should happen
   
   ## Actual Behavior
   What actually happens
   
   ## System Information
   - Windows Version:
   - .NET Framework:
   - FXP20 Model:
   - Application Version:
   
   ## Configuration
   Relevant Config.xml settings or screenshots
   
   ## Error Messages
   Exact text of any error messages
   ```

2. **📊 Additional Information**
   - Screenshots or videos if relevant
   - Config.xml file (remove sensitive information)
   - Steps already tried from this troubleshooting guide
   - Whether issue is new or has worked before

### Community Support
- **💬 GitHub Discussions** - Community Q&A
- **🔍 Search Issues** - Check if others have similar problems
- **⭐ Star Repository** - Show support and get updates

---

## ⚠️ Known Issues and Workarounds

### Windows 11 Compatibility
- **Issue**: Some antivirus software flags application
- **Workaround**: Add to exclusions list, run as Administrator

### High DPI Displays
- **Issue**: GUI elements may appear small or misaligned
- **Workaround**: Set display scaling to 100%, use compatibility mode

### Multiple FXP20 Devices
- **Issue**: Difficulty identifying which COM port corresponds to which device
- **Workaround**: Connect one device at a time, use LED indicators, label devices

### Large Volume Processing
- **Issue**: Memory usage grows with high tag volume
- **Workaround**: Disable "Show EPC Sent", restart application periodically, use smaller batch sizes

---

*Still having issues? Create a [new issue](https://github.com/ltrudu/FXP20KeyInjector_Releases/issues/new) with detailed information or return to [Home](Home.md).*