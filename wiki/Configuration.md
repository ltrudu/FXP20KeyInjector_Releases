# ⚙️ Configuration Guide

Complete reference for configuring FXP20 Key Injector through the Config.xml file and GUI settings.

---

## 📋 Configuration Overview

FXP20 Key Injector can be configured through:
- 🖥️ **GUI Settings** - Basic configuration through the user interface
- 📄 **Config.xml File** - Advanced configuration and automation settings
- 🔄 **Automatic Generation** - Default Config.xml created on first launch

---

## 📄 Config.xml File Structure

### File Location
The `Config.xml` file is located in the same directory as `FXP20KeyInjector.exe`.

### Automatic Creation
- 🆕 **First Launch**: If no Config.xml exists, default values are created
- 💾 **Manual Save**: Use "Save Config" button to update the file
- 🔄 **Manual Load**: Use "Load Config" button to reload from file

### File Format
```xml
<?xml version="1.0" encoding="utf-8"?>
<Configuration>
  <!-- Basic Settings -->
  <TargetWindowFilter>Notepad</TargetWindowFilter>
  <ComPort>COM5</ComPort>
  <BaudRate>921600</BaudRate>
  
  <!-- Protocol Settings -->
  <Protocol>CLIPBOARDPASTE</Protocol>
  <!-- Additional settings... -->
</Configuration>
```

---

## 🔧 Basic Configuration Settings

### Connection Settings

#### TargetWindowFilter
**Purpose**: Specifies which windows receive tag data
```xml
<TargetWindowFilter>Notepad</TargetWindowFilter>
```
- 📝 **Type**: String
- 🔍 **Function**: Partial matching of window titles
- ✨ **Example**: "Notepad" matches "Untitled - Notepad" and "Notepad++"
- ⚠️ **Case Sensitive**: Yes

#### ComPort
**Purpose**: COM port for FX device communication
```xml
<ComPort>COM5</ComPort>
```
- 📝 **Type**: String
- 🔌 **Format**: COMx (where x is the port number)
- 🔍 **Auto-Detection**: Use GUI to identify available ports
- ✨ **Example**: COM1, COM5, COM12

#### BaudRate  
**Purpose**: Communication speed with FX device
```xml
<BaudRate>921600</BaudRate>
```
- 📝 **Type**: Integer
- ⚡ **Default**: 921600 (recommended)
- 🎛️ **Options**: 230400, 460800, 115200, 921600
- ⚠️ **Note**: Keep default for best performance

---

## 📡 Send Protocol Configuration

#### Protocol
**Purpose**: Method for delivering tag data to applications
```xml
<Protocol>CLIPBOARDPASTE</Protocol>
```
- 📝 **Type**: String
- 🎛️ **Options**:
  - `CLIPBOARDPASTE` - Clipboard paste (recommended)
  - `KEYINJECTION` - Character-by-character input
  - `MQTT` - MQTT messaging protocol

#### ClipboardPasteDelay
**Purpose**: Delay between clipboard paste operations
```xml
<ClipboardPasteDelay>500</ClipboardPasteDelay>
```
- 📝 **Type**: Integer (milliseconds)
- ⏱️ **Default**: 500ms
- 🎯 **Range**: 100ms minimum (0ms possible but not recommended)
- 🔧 **Tuning**: Lower values for faster systems

#### Data Formatting Options
```xml
<AddCSVSeparator>true</AddCSVSeparator>
<AddCR>true</AddCR>
<AddLF>false</AddLF>
```
- 📊 **AddCSVSeparator**: Adds semicolon (;) after each tag
- ↩️ **AddCR**: Adds carriage return character
- ⬇️ **AddLF**: Adds line feed character

---

## 🚀 Automation Settings

#### AutoConnect
**Purpose**: Automatically connect to FX device on startup
```xml
<AutoConnect>true</AutoConnect>
```
- 📝 **Type**: Boolean (true/false)
- 🔌 **Function**: Connects using configured ComPort
- ⚠️ **Requirement**: Device must be available at specified port

#### AutoStartReading
**Purpose**: Begin tag reading immediately after connection
```xml
<AutoStartReading>true</AutoStartReading>
```
- 📝 **Type**: Boolean (true/false)
- ▶️ **Function**: Starts reading when connection is established
- 🔗 **Dependency**: Works with AutoConnect or manual connection

#### StartMinimized
**Purpose**: Start application minimized to system tray
```xml
<StartMinimized>true</StartMinimized>
```
- 📝 **Type**: Boolean (true/false)
- 👁️ **Function**: Application starts in system tray
- 🔄 **Note**: May briefly appear during SDK initialization

---

## 🎛️ Advanced Reading Controls

#### BeepOnRead Settings
```xml
<BeepOnRead>true</BeepOnRead>
<nbBeeps>1</nbBeeps>
<beepSleepTime>1000</beepSleepTime>
```
- 🔊 **BeepOnRead**: Enable audio feedback
- 🔢 **nbBeeps**: Number of beeps per tag (≥1)
- ⏱️ **beepSleepTime**: Beep duration in milliseconds

#### BatchSize
**Purpose**: Number of tags processed per read cycle
```xml
<BatchSize>10</BatchSize>
```
- 📝 **Type**: Integer (≥1)
- ⚡ **Default**: 10
- 🎯 **Performance**: Higher values may improve throughput
- ⚠️ **Caution**: Change only if you understand implications

---

## ⌨️ Keyboard Hook Configuration

#### HookKeyboardToStartReading
**Purpose**: Use keyboard shortcuts to trigger reading
```xml
<HookKeyboardToStartReading>true</HookKeyboardToStartReading>
<HookKeyboardKey>123</HookKeyboardKey>
<HookKeyboardReadingDurationInMs>5000</HookKeyboardReadingDurationInMs>
```
- 🎹 **HookKeyboardToStartReading**: Enable keyboard hook
- 🔤 **HookKeyboardKey**: ASCII code for trigger key (default: F12 = 123)
- ⏱️ **HookKeyboardReadingDurationInMs**: Reading duration in milliseconds

**Common Key Codes:**
- F12: 123 (default)
- F1: 112
- Space: 32
- Enter: 13

---

## 🎛️ GPIO Configuration

#### PerformReadingWithGPIO
**Purpose**: Use hardware buttons to trigger reading
```xml
<PerformReadingWithGPIO>true</PerformReadingWithGPIO>
<PerformReadingGPIOPort>1</PerformReadingGPIOPort>
<PerformReadingDuration>3000</PerformReadingDuration>
```
- 🔘 **PerformReadingWithGPIO**: Enable GPIO control
- 🔢 **PerformReadingGPIOPort**: GPI port number (≥1)
- ⏱️ **PerformReadingDuration**: Reading duration in milliseconds

**Requirements:**
- StartReading must be active
- GPIO port activation triggers timed reading session
- Use StopReading to exit GPIO mode

---

## 🔄 Duplicate Filtering

#### RemoveDuplicates
**Purpose**: Filter duplicate tags during timed reading sessions
```xml
<RemoveDuplicates>true</RemoveDuplicates>
```
- 📝 **Type**: Boolean (true/false)
- 🎯 **Scope**: Works with HookKeyboardToStartReading and PerformReadingWithGPIO
- ⏱️ **Duration**: Active during reading session timeouts
- 🔄 **Function**: Ensures unique tags per session

---

## 🌐 MQTT Configuration

#### MQTT Connection Settings
```xml
<MQTTServer>127.0.0.1</MQTTServer>
<MQTTPort>1883</MQTTPort>
<MQTTUser>user</MQTTUser>
<MQTTPassword>password</MQTTPassword>
```
- 🌐 **MQTTServer**: Broker IP address or hostname
- 🔌 **MQTTPort**: Broker port (1883 default)
- 👤 **MQTTUser**: Authentication username
- 🔐 **MQTTPassword**: Authentication password (plain text)

#### MQTT Topics
```xml
<MQTTSendTopic>fxp20/data</MQTTSendTopic>
<MQTTControlTopic>fxp20/control</MQTTControlTopic>
```
- 📤 **MQTTSendTopic**: Topic for outgoing tag data
- 📥 **MQTTControlTopic**: Topic for incoming control commands

**Control Commands:**
- `Connect` - Connect to FX device
- `Disconnect` - Disconnect from FX device
- `StartReading` - Begin tag reading
- `StopReading` - Stop tag reading
- `Beep` - Trigger device beep
- `UnBeep` - Stop beeping

---

## 📡 Antenna Configuration

The Config.xml file contains detailed antenna configuration for each antenna port:

### Antenna Structure
```xml
<AntennasConfig>
  <antennaConfig>
    <Antenna_ID>1</Antenna_ID>
    <RFMode_Tari>0</RFMode_Tari>
    <RFMode_TableIndex>2</RFMode_TableIndex>
    <ReceiveSensitivityIndex>0</ReceiveSensitivityIndex>
    <TransmitPowerIndex>100</TransmitPowerIndex>
    <TransmitFrequencyIndex>1</TransmitFrequencyIndex>
    <SingulationControl_Session>SESSION_S1</SingulationControl_Session>
    <SingulationControl_TagPopulation>30</SingulationControl_TagPopulation>
    <SingulationControl_TagTransitTime>30</SingulationControl_TagTransitTime>
    <SingulationControl_PerformStateAwareSingulationAction>true</SingulationControl_PerformStateAwareSingulationAction>
    <SingulationControl_Sl_Flag>SL_ALL</SingulationControl_Sl_Flag>
    <SingulationControl_InventoryState>INVENTORY_STATE_AB_FLIP</SingulationControl_InventoryState>
  </antennaConfig>
  <!-- Additional antennas (2-4) follow same structure -->
</AntennasConfig>
```

### Antenna Settings Explained

#### Basic RF Settings
- 🔢 **Antenna_ID**: Antenna number (1=internal, 2-4=external)
- 📡 **RFMode_Tari**: Tag response timing (≥0)
- 📊 **RFMode_TableIndex**: RF mode (0, 1, 2, or 3)
- 📶 **ReceiveSensitivityIndex**: Reception sensitivity (0)
- ⚡ **TransmitPowerIndex**: Power level (0-170, see [Power Index](Power-Index))

#### Advanced Settings
- 🏷️ **SingulationControl_Session**: Session type (SESSION_S1, S2, S3, S4)
- 👥 **SingulationControl_TagPopulation**: Expected tag count (≥1)
- 🚶 **SingulationControl_TagTransitTime**: Tag movement speed (≥1)
- 🧠 **SingulationControl_PerformStateAwareSingulationAction**: Advanced handling
- 🎛️ **SingulationControl_Sl_Flag**: Select flags (SL_ALL, SL_FLAG_ASSERTED, SL_FLAG_DEASSERTED)
- 📊 **SingulationControl_InventoryState**: State management (INVENTORY_STATE_AB_FLIP, STATE_A, STATE_B)

---

## 🔧 Configuration Best Practices

### Performance Optimization
- ⚡ Keep **BaudRate** at 921600
- 📊 Set appropriate **BatchSize** for your workflow
- ⏱️ Minimize **ClipboardPasteDelay** for your system
- 🎯 Use specific **TargetWindowFilter** to reduce overhead

### Automation Setup
- 🚀 Enable **AutoConnect** for production use
- ▶️ Use **AutoStartReading** for hands-free operation
- 👁️ Enable **StartMinimized** for background operation
- 💾 Always test configuration before automating

### Reliability Settings
- 🔄 Enable **RemoveDuplicates** for session-based reading
- 🔊 Configure appropriate **beep settings** for user feedback
- ⏱️ Set reasonable **reading durations** for GPIO/keyboard hooks
- 🌐 Use strong authentication for MQTT setups

---

## 🧪 Testing Configuration

### Validation Steps
1. **📄 Syntax Check**: Ensure valid XML structure
2. **🔌 Connection Test**: Verify device communication
3. **🎯 Target Test**: Confirm window filtering works
4. **📊 Data Flow**: Test tag reading and delivery
5. **🔄 Automation**: Verify auto-startup features

### Common Configuration Errors
- ❌ **Invalid COM port** - Device not found
- ❌ **Wrong window filter** - Data not delivered
- ❌ **MQTT connection failure** - Check broker settings
- ❌ **Permission errors** - Run as Administrator

---

## 🔗 Related Topics

- **[User Interface Guide](User-Interface)** - GUI configuration options
- **[Setup Guide](Setup)** - Initial device setup
- **[MQTT Integration](MQTT)** - Detailed MQTT configuration
- **[Auto-Startup Guide](Auto-Startup)** - Windows startup configuration
- **[Power Index Reference](Power-Index)** - RF power level details
- **[ASCII Codes](ASCII-Codes)** - Keyboard hook key codes

---

*Need help with configuration? Check [Troubleshooting](Troubleshooting) or return to [Home](Home).*