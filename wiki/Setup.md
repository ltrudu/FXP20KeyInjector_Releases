# 🛠️ Setup & Connection Guide

Complete guide for setting up your FXP20 Key Injector and connecting to your Zebra FX device.

---

## 📋 Setup Overview

The setup process involves three main phases:
1. **🔧 Configuration File Management** - Creating and managing Config.xml
2. **🔌 Device Connection** - Establishing communication with your FX device
3. **📡 Protocol Selection** - Choosing how to send tag data

---

## 🔧 Configuration File Management

### Automatic Configuration Creation
When FXP20KeyInjector launches for the first time:

- 📄 **Auto-Detection**: Application searches for existing Config.xml
- 🆕 **Default Creation**: If not found, creates Config.xml with default values
- 📍 **Location**: Same directory as FXP20KeyInjector.exe
- ✅ **Ready to Use**: Application immediately functional with defaults

### Loading and Saving Configuration

#### Load Config Button
- 📂 **Function**: Reads settings from Config.xml file
- 🔄 **Use Case**: Reload configuration after manual file editing
- ⚙️ **Effect**: Updates GUI with saved settings

#### Save Config Button  
- 💾 **Function**: Writes current GUI settings to Config.xml
- 📝 **Scope**: Saves GUI-accessible settings only
- ⚠️ **Note**: Some advanced settings require manual XML editing

### Configuration Best Practices
- 💾 **Save Early**: Save configuration after successful setup
- 🧪 **Test First**: Verify settings work before saving
- 📋 **Backup**: Keep backup copies of working configurations
- 📝 **Document**: Note any manual XML changes for future reference

---

## 🔌 Connection Configuration

### Device Discovery Process

#### Automatic Discovery
When FXP20KeyInjector launches:
1. **🔍 Scan Ports**: Automatically scans for connected FX devices
2. **📋 Populate List**: Fills COM Port dropdown with detected devices
3. **❌ Error Display**: Shows error if no devices found

#### Manual Refresh
- 🔄 **Refresh Values Button**: Updates COM port list
- 🆕 **Use Case**: When device connected after application launch
- 🔌 **Hot-Plug**: Detects newly connected devices

### COM Port Selection

#### Single Device Setup
1. **📱 Connect Device**: Plug in your FX device via USB
2. **🔍 Verify Detection**: Check that device appears in COM Port dropdown
3. **✅ Select Port**: Choose the correct COM port from list

#### Multiple Device Environment
- 🎯 **Trial Method**: Select port and test connection
- 💡 **LED Indicators**: Watch device LEDs to identify which connected
- 📝 **Label Devices**: Consider labeling devices for easier identification
- 📋 **Document Setup**: Record which COM port corresponds to which device

### COM Port Configuration
```xml
<ComPort>COM5</ComPort>
```
- 🔤 **Format**: COMx where x is the port number
- 🔄 **Auto-Save**: Selected port saved with configuration
- 🚀 **Auto-Connect**: Used for automatic connection on startup

### Communication Settings

#### Baud Rate Configuration
- ⚡ **Default**: 921600 (recommended)
- 🎛️ **Options**: 230400, 460800, 115200, 921600
- ✅ **Best Practice**: Keep default unless specific requirements
- 🔧 **Performance**: Higher rates = better performance

#### Connection Process
1. **⚙️ Configure**: Set COM port and baud rate
2. **🔌 Connect**: Click "Connect" button
3. **📡 Apply Settings**: Current configuration applied to device
4. **✅ Verify**: Check connection status and device response

---

## 📡 Send Protocol Configuration

### Protocol Selection Overview
Choose how tag data will be delivered to target applications:

#### CLIPBOARDPASTE (Recommended)
- ✅ **Best Performance**: Fastest and most stable
- 📋 **Method**: Copy to clipboard + paste (Ctrl+V)
- 🎯 **Best For**: Most applications, especially spreadsheets
- ⏱️ **Configurable Delay**: Default 500ms between pastes

#### KEYINJECTION  
- ⌨️ **Method**: Individual keystroke simulation
- 🐌 **Performance**: Slower than clipboard paste
- 🎯 **Best For**: Applications requiring keystroke events
- ⚠️ **Stability**: Less reliable than clipboard paste

#### MQTT
- 🌐 **Method**: Message broker communication
- 🏢 **Best For**: Enterprise integration, multiple consumers
- 🔧 **Requirements**: MQTT broker setup required
- 📊 **Benefits**: Remote control, multiple subscribers

### Target Window Configuration

#### Window Filter Setup
1. **📋 Open Target**: Launch your target application (Excel, database, etc.)
2. **🔄 Refresh**: Click "Refresh Values" to update window list
3. **🎯 Select Window**: Choose target from "Window List" dropdown
4. **✅ Auto-Fill**: Window filter automatically populated
5. **🔧 Fine-Tune**: Adjust filter for multiple windows if needed

#### Filter Matching Rules
- 🔍 **Partial Matching**: Filter searches within window titles
- 📝 **Case Sensitive**: Exact case matching required
- ✨ **Examples**:
  - "Notepad" matches "Untitled - Notepad" ✅
  - "notepad" does NOT match "Untitled - Notepad" ❌
  - "Excel" matches "Book1 - Microsoft Excel" ✅

### Automatic Connection Features

#### AutoConnect Configuration
```xml
<AutoConnect>true</AutoConnect>
```
- 🚀 **Function**: Automatically connects on application startup
- 🔌 **Requirements**: Valid COM port configured
- ⚠️ **Prerequisites**: Device must be available and ready

#### AutoStartReading Configuration
```xml
<AutoStartReading>true</AutoStartReading>
```
- ▶️ **Function**: Begins reading immediately after connection
- 🔗 **Dependency**: Works with both auto and manual connection
- 🎯 **Use Case**: Hands-free operation

---

## 🧪 Connection Testing

### Manual Connection Test
1. **🔌 Connect Device**: Ensure physical connection
2. **⚙️ Configure Settings**: Set COM port and baud rate
3. **🔗 Test Connection**: Click "Connect" button
4. **✅ Verify Status**: Check status label for success message
5. **📡 Test Reading**: Click "Start Reading" and present a tag

### Debug Testing
Use the debug section for validation:

#### Text Input Testing
1. **📝 Enter Text**: Type test data in "Text To Send" field
2. **🎯 Set Target**: Configure window filter for target application
3. **🧪 Test Methods**: 
   - Click "Send Key Events" for key injection test
   - Click "Send Clipboard" for clipboard paste test
4. **✅ Verify**: Confirm data appears in target application

### Common Connection Issues

#### Device Not Found
- **🔌 Check Cable**: Verify USB connection
- **🔄 Restart**: Unplug and reconnect device
- **🖥️ Device Manager**: Check Windows device manager
- **📱 Device Status**: Ensure device is powered and ready

#### Connection Failed
- **⚡ Baud Rate**: Try different baud rate settings
- **👤 Permissions**: Run application as Administrator
- **🔒 Port Busy**: Close other applications using the COM port
- **🔄 Retry**: Wait and attempt connection again

#### Data Not Reaching Target
- **🎯 Window Filter**: Verify filter matches target window exactly
- **👁️ Window Focus**: Ensure target application has focus
- **🔧 Protocol**: Try different send protocol (CLIPBOARDPASTE vs KEYINJECTION)
- **⏱️ Timing**: Adjust clipboard paste delay if needed

---

## 🚀 Production Setup

### Deployment Configuration
For production environments:

1. **⚙️ Configure Once**: Set up all parameters completely
2. **💾 Save Configuration**: Use "Save Config" to preserve settings
3. **🧪 Test Thoroughly**: Verify all functionality works correctly
4. **🚀 Enable Auto-Features**: Turn on AutoConnect and AutoStartReading
5. **👁️ Minimize**: Enable StartMinimized for background operation

### Startup Integration
```xml
<StartMinimized>true</StartMinimized>
<AutoConnect>true</AutoConnect>
<AutoStartReading>true</AutoStartReading>
```

### Monitoring and Maintenance
- 📊 **Status Monitoring**: Regularly check status indicators
- 🔄 **Connection Health**: Monitor for connection drops
- 📈 **Performance**: Watch tag processing counters
- 🧹 **Maintenance**: Periodically clear EPC sent lists

---

## 📋 Setup Checklist

### Pre-Setup
- [ ] 🔌 FX device connected and powered
- [ ] 💻 .NET Framework 4.8+ installed
- [ ] 👤 Administrator privileges available
- [ ] 📱 Target application identified

### Basic Setup
- [ ] 🚀 FXP20KeyInjector launched
- [ ] 🔍 COM port detected and selected
- [ ] 🔗 Connection established successfully
- [ ] 🎯 Target window filter configured
- [ ] 📡 Send protocol selected

### Advanced Setup
- [ ] ⚙️ Antenna settings configured (if needed)
- [ ] 🔊 Beep settings adjusted
- [ ] 🎛️ GPIO/Keyboard hooks configured (if needed)
- [ ] 🌐 MQTT broker configured (if needed)
- [ ] 🚀 Auto-startup features enabled

### Testing
- [ ] 🧪 Debug tools tested successfully
- [ ] 🏷️ Tag reading verified
- [ ] 📊 Data delivery confirmed
- [ ] 💾 Configuration saved
- [ ] 🔄 Auto-features tested

---

## 🔗 Related Topics

- **[Installation Guide](Installation.md)** - Installing the application
- **[Configuration Guide](Configuration.md)** - Detailed Config.xml reference
- **[User Interface Guide](User-Interface.md)** - Complete GUI walkthrough
- **[MQTT Integration](MQTT.md)** - Setting up MQTT mode
- **[Troubleshooting](Troubleshooting.md)** - Common setup issues

---

*Having setup issues? Check our [Troubleshooting Guide](Troubleshooting.md) or return to [Home](Home.md).*