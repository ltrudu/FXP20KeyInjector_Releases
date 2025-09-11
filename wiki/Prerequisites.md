# 📋 Prerequisites Guide

Complete system requirements and hardware compatibility information for FXP20 Key Injector.

---

## 🖥️ Operating System Requirements

### Supported Windows Versions
- ✅ **Windows 11** (All editions)
- ✅ **Windows 10** (Version 1903 or later)
- ✅ **Windows Server 2019**
- ✅ **Windows Server 2022**

### Architecture Support
- ✅ **x64 (64-bit)** - Recommended
- ✅ **x86 (32-bit)** - Supported

### Minimum System Specifications
- **💾 RAM**: 4 GB minimum, 8 GB recommended
- **💿 Storage**: 50 MB free disk space
- **🔌 USB**: USB 2.0 or higher ports
- **🌐 Network**: Optional (for MQTT features)

---

## ⚡ Software Dependencies

### .NET Framework Requirements
**Required**: .NET Framework 4.8 or higher

#### How to Check Current Version
1. **⌨️ Press** Windows + R
2. **📝 Type** `regedit` and press Enter
3. **📂 Navigate** to: `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full`
4. **👀 Look** for `Release` value:
   - **528040** or higher = .NET 4.8+
   - **461808** = .NET 4.7.2
   - **461308** = .NET 4.7.1

#### Installation
If .NET Framework 4.8 is not installed:
1. **📥 Download** from [Microsoft's official site](https://dotnet.microsoft.com/en-us/download/dotnet-framework/net48)
2. **▶️ Run** installer as Administrator
3. **🔄 Restart** computer when prompted
4. **✅ Verify** installation using registry check above

---

## 📱 Hardware Requirements

### Supported Zebra Devices
Primary support for **Zebra FXP20** series:
- ✅ **FXP20 RFID Reader**


### Zebra Device Specifications
- **📡 Frequency**: 860-960 MHz (UHF RFID)
- **⚡ Power**: USB-powered device
- **🔌 Connectivity**: USB 2.0+ connection
- **📊 Protocol**: Serial communication over COM ports

### Connection Requirements
- **🔌 USB Cable**: High-quality USB 2.0 or 3.0 cable
- **⚡ Power**: USB port capable of providing adequate power
- **📶 Drivers**: Zebra device drivers (usually auto-installed)

### Optional Hardware
- **🖱️ Powered USB Hub**: For multiple device connections
- **🔌 External Power Adapter**: For FXP20 charging
- **📡 External Antenna**: For extended range (device-dependent)

---

## 🌐 Network Prerequisites (MQTT Only)

### MQTT Broker Requirements
Only required if using MQTT protocol:
- **🏢 MQTT Broker**: Mosquitto, HiveMQ, AWS IoT, Azure IoT Hub
- **🌐 Network Access**: TCP port 1883 (standard) or 8883 (SSL)
- **👤 Authentication**: Username/password credentials
- **📊 Topic Permissions**: Publish/subscribe access to configured topics

### Network Configuration
- **🔥 Firewall**: Allow outbound connections on MQTT ports
- **🌍 Internet**: Required for cloud MQTT brokers
- **🏠 LAN**: Sufficient for local MQTT brokers

---

## 🛡️ Security Requirements

### User Permissions
- **📝 File Permissions**: Read/write access to installation directory
- **🔌 Device Access**: Permission to access serial/COM ports

### Antivirus Considerations
- **⚠️ False Positives**: Some antivirus may flag executable
- **📁 Exclusions**: Add installation folder to antivirus exclusions
- **🔍 Scanning**: Disable real-time scanning during installation

### Windows Security Features
- **🛡️ Windows Defender**: May require approval for first run
- **👤 UAC (User Account Control)**: Will prompt for elevation
- **🔒 SmartScreen**: May show warning for unrecognized app

---

## 🔧 Environment Setup

### Development Environment (Optional)
If planning to modify configurations extensively:
- **📝 Text Editor**: For XML configuration editing
- **🔧 XML Validator**: To verify Config.xml syntax
- **📊 MQTT Client**: For testing MQTT functionality

### Production Environment
- **🏢 Domain Environment**: Ensure COM port access policies
- **📊 Monitoring**: Consider system monitoring for production use
- **🔄 Backup**: Regular configuration backup procedures
- **📝 Logging**: Windows Event Viewer for troubleshooting

---

## ✅ Pre-Installation Checklist

### Before Download
- [ ] ✅ Windows 10/11 or Server 2019/2022
- [ ] ⚡ .NET Framework 4.8 installed
- [ ] 👤 Administrator access available
- [ ] 🔌 USB port available
- [ ] 💿 50 MB disk space free

### Hardware Check
- [ ] 📱 Zebra FXP20 device available
- [ ] 🔌 USB cable (preferably high-quality)
- [ ] ⚡ USB power connection
- [ ] 🏷️ Test RFID tags available

### Network Check (MQTT Users)
- [ ] 🌐 MQTT broker accessible
- [ ] 👤 MQTT credentials available
- [ ] 🔥 Firewall rules configured
- [ ] 📡 Network connectivity verified

---

## 🚨 Compatibility Issues

### Known Limitations
- **🚫 Windows 7/8**: Not supported (lacks .NET 4.8 support)
- **🚫 Windows Server 2016**: Limited support (requires .NET 4.8 manual install)
- **🚫 32-bit Windows**: May have performance limitations
- **🚫 Virtual Machines**: USB passthrough may cause issues

### Hardware Incompatibilities
- **🚫 Non-Zebra Devices**: Only Zebra FXP20 supported
- **🚫 Generic RFID Readers**: Protocol incompatibility
- **🚫 USB 1.1**: May not provide sufficient power
- **🚫 Bluetooth Connections**: Not supported (USB only)

### Software Conflicts
- **⚠️ COM Port Apps**: Other applications using same COM ports
- **⚠️ Antivirus Software**: May interfere with device communication
- **⚠️ Driver Conflicts**: Multiple RFID software installations
- **⚠️ .NET Versions**: Older .NET versions may cause conflicts

---

## 🔍 Verification Steps

### System Verification
```powershell
# Check Windows version
Get-ComputerInfo | Select-Object WindowsProductName, WindowsVersion

# Check .NET Framework version
Get-ChildItem 'HKLM:SOFTWARE\Microsoft\NET Framework Setup\NDP' -Recurse

# Check available COM ports
Get-WmiObject -Class Win32_SerialPort
```

### Hardware Verification
1. **🔌 Connect** FXP20 device via USB
2. **⏳ Wait** for driver installation
3. **🖥️ Open** Device Manager
4. **📂 Expand** "Ports (COM & LPT)"
5. **✅ Verify** FXP20 appears with COM port number

### Network Verification (MQTT)
```bash
# Test MQTT broker connectivity
telnet mqtt-broker-ip 1883

# Test with mosquitto client (if available)
mosquitto_pub -h localhost -p 1883 -u user -P password -t test -m "hello"
```

---

## 🆘 Prerequisites Troubleshooting

### .NET Framework Issues
- **📥 Download offline installer** if web installer fails
- **🔄 Restart** computer after installation
- **🧹 Clean** temporary files before retry
- **👤 Run** installer as Administrator

### Device Driver Problems
- **📥 Download** Zebra drivers manually from Zebra website
- **🔄 Restart** computer after driver installation
- **🔌 Try** different USB port
- **🖥️ Check** Device Manager for error codes

### Permission Issues
- **👤 Run** as Administrator
- **🔐 Check** user account permissions
- **🏢 Contact** IT administrator for domain environments
- **📁 Verify** installation folder permissions

---

## 📞 Getting Help

### Self-Service Resources
- **📋 [Installation Guide](Installation.md)** - Step-by-step setup
- **🔧 [Troubleshooting Guide](Troubleshooting.md)** - Problem solutions
- **🏠 [Home](Home.md)** - Documentation hub

### Support Resources
- **🐛 [GitHub Issues](https://github.com/ltrudu/FXP20KeyInjector_Releases/issues)** - Community support
- **📄 [Zebra Support](https://www.zebra.com/us/en/support.html)** - Hardware support
- **💻 [Microsoft Support](https://support.microsoft.com/)** - OS and .NET support

---

*Prerequisites verified? Continue with the [Installation Guide](Installation.md) or return to [Home](Home.md).*