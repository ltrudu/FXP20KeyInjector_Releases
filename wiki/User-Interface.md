# 🖥️ User Interface Guide

Complete walkthrough of the FXP20 Key Injector graphical user interface and all available controls.

---

## 🎯 Interface Overview

The FXP20 Key Injector interface is organized into several logical sections for easy navigation and operation.

### Main Window Sections
- **🔧 Setup Section** - Connection and configuration controls
- **📊 Status Section** - Real-time feedback and monitoring  
- **📋 Data Section** - Tag reading results and history
- **🐛 Debug Section** - Testing and troubleshooting tools

---

## 🔧 Setup Section

### 1. Window List Dropdown
**Purpose**: Shows all currently open Windows applications

- 📋 **Function**: Lists all windows with their exact titles
- 🔄 **Refresh**: Click "Refresh Values" (14) to update the list
- 🎯 **Auto-Fill**: Selecting a window automatically fills the Window Filter (2)
- 💡 **Tip**: Helper tool to identify target application names

### 2. Window Filter Input
**Purpose**: Specifies which applications will receive tag data

- 📝 **Function**: Text filter for matching window titles
- 🔍 **Matching**: Searches for the filter text within window names
- ✨ **Example**: "Notepad" matches both "Notepad" and "Notepad++"
- ⚠️ **Case Sensitive**: Filter search is case-sensitive

### 3. COM Port Dropdown  
**Purpose**: Selects the communication port for your FX device

- 🔌 **Function**: Lists all detected FX device COM ports
- 🔄 **Multiple Devices**: Shows all connected FX devices
- 🎯 **Selection**: Use trial-and-error if multiple devices are connected
- 💡 **Tip**: Check LED indicators on devices to identify which is connected

### 4. Baud Rate Dropdown
**Purpose**: Sets communication speed with the FX device

**Available Speeds:**
- 230400
- 460800  
- 115200
- **921600** (Default - Recommended)

⚠️ **Important**: Keep default setting (921600) for best performance and stability

### 5. Antenna Config Button
**Purpose**: Configure antenna-specific RF parameters

**Opens modal window with settings:**
- 📡 **RFMode** - RF communication mode
- ⏱️ **Tari** - Tag response timing
- 📶 **Receive Sensitivity** - Reception sensitivity level
- ⚡ **Transmit Power** - RF transmission power
- 🔢 **Hop Index** - Frequency hopping configuration

⚠️ **Requirements**:
- Reader must be connected first
- Apply settings before changing antennas
- Settings are antenna-specific

### 6. Reader Parameters Button
**Purpose**: Configure reader-specific inventory parameters

**Available Settings:**
- 🏷️ **SESSION Type** (S1, S2, S3, S4)
- 👥 **Population** - Expected tag population
- 🚶 **Transit** - Tag movement speed
- 📊 **Inventory State** - Tag state management
- 🎛️ **SLFlags** - Select flags behavior
- 🧠 **State Aware Singulation** - Advanced tag handling

### 7. Load Config Button
**Purpose**: Load settings from Config.xml file

- 📂 **Function**: Reads configuration from Config.xml
- 🔄 **Refresh**: Updates GUI with saved settings
- 📍 **Location**: Loads from application folder

### 8. Save Config Button  
**Purpose**: Save current GUI settings to Config.xml

- 💾 **Function**: Writes current settings to file
- ⚙️ **Scope**: Only saves GUI-configurable settings
- 📝 **Note**: Some advanced settings require manual Config.xml editing

---

## 📊 Send Protocol Section

### 9. Send Protocol Dropdown
**Purpose**: Choose how tag data is delivered to target applications

#### CLIPBOARDPASTE (Recommended)
- ✅ **Best performance and stability**
- 📋 **Method**: Copies tag data to clipboard, then pastes (Ctrl+V)
- ⏱️ **Default Delay**: 500ms between pastes (configurable)
- 🎯 **Use Case**: Most applications, especially spreadsheets

#### KEYINJECTION
- ⌨️ **Method**: Sends individual keystrokes character by character
- 🐌 **Speed**: Slower than clipboard paste
- 🎯 **Use Case**: Applications requiring keystroke simulation
- ⚠️ **Stability**: Less stable than clipboard paste

#### MQTT
- 🌐 **Method**: Sends data via MQTT messaging protocol
- 🏢 **Use Case**: Enterprise integration and remote applications
- 🔧 **Setup**: Requires MQTT broker configuration
- 📊 **Benefits**: Multiple subscribers, remote control capabilities

### 10-12. Data Formatting Options

#### 10. Add CSV Separator
- ➕ **Function**: Adds semicolon (;) after each tag
- 📊 **Use Case**: Creating CSV files
- ✅ **Checkbox**: Toggle on/off

#### 11. Add CR (Carriage Return)
- ↩️ **Function**: Adds carriage return after each tag
- 📝 **Format**: Windows line ending component
- ✅ **Checkbox**: Toggle on/off

#### 12. Add LF (Line Feed)
- ⬇️ **Function**: Adds line feed after each tag
- 🐧 **Format**: Unix/Linux line ending component
- ✅ **Checkbox**: Toggle on/off

### 13. Batch Read Size
**Purpose**: Number of tags processed per read cycle

- 🔢 **Default**: 10 tags
- ⚡ **Performance**: Higher values = better throughput
- ⚠️ **Caution**: Only change if you understand the impact

---

## 🎛️ Control Section

### 14. Refresh Values Button
**Purpose**: Update dynamic lists with current system state

- 🔄 **Updates**: Window List (1) and COM Port (3) dropdowns
- 🆕 **Use Case**: When applications are opened after FXP20 launch
- 📱 **Device Detection**: Finds newly connected FX devices

### 15. Beep On Read Checkbox
**Purpose**: Enable audio feedback when tags are read

- 🔊 **Function**: FX device beeps for each successful tag read
- ✅ **Toggle**: Enable/disable audio feedback
- 🎵 **Configurable**: Beep count and duration in Config.xml

### 16-19. Connection and Reading Controls

#### 16. Connect Button
- 🔌 **Function**: Establish connection to selected FX device
- ⚙️ **Process**: Applies current configuration to device
- 💚 **Status**: Button state indicates connection status

#### 17. Disconnect Button  
- ❌ **Function**: Disconnect from FX device
- 🛑 **Auto-Stop**: Automatically stops reading if active
- 🔄 **Clean**: Properly closes communication channel

#### 18. Start Reading Button
- ▶️ **Function**: Begin tag reading process
- 📋 **Requirement**: Device must be connected first
- 🔄 **Continuous**: Reads until stopped

#### 19. Stop Reading Button
- ⏹️ **Function**: Stop tag reading process  
- 💾 **Safe**: Does not disconnect device
- 🔄 **Resumable**: Can restart reading without reconnecting

---

## 📊 Status and Data Section

### 20-21. Status Information

#### 20. Status Label
- 📊 **Function**: Shows current application state
- 🔄 **Real-time**: Updates during operations
- 📋 **Examples**: "Waiting for user actions", "Reading tags", "Connected"

#### 21. Tags Processed Counter
- 🔢 **Function**: Total count of processed tags since application start
- 📊 **Persistent**: Cannot be reset (restart app to reset)
- 📈 **Cumulative**: Increases with each tag read

### 22-25. Tag Data Display

#### 22. Last EPC Read
- 🏷️ **Function**: Shows the most recently read tag data
- 🔄 **Real-time**: Updates immediately when tags are read
- 📋 **Format**: Raw EPC data as received from device

#### 23. EPC Sent List
- 📋 **Function**: Scrollable list of all sent tag data
- 📊 **History**: Shows tags sent to target applications
- 🔄 **Updates**: Only when "Show EPC Sent" (24) is enabled

#### 24. Show EPC Sent Checkbox
- 👁️ **Function**: Controls visibility of sent tags in list (23)
- ✅ **When Enabled**: Tags appear in both Last EPC (22) and EPC Sent list (23)
- 📊 **Performance**: Disable for high-volume operations

#### 25. Clear Button
- 🧹 **Function**: Empties the EPC Sent list (23)
- 🔄 **Scope**: Only clears display list, not processing counter
- 💨 **Immediate**: Takes effect instantly

---

## 🐛 Debug Section

### 26-28. Testing Tools

#### 26. Text To Send Input
- 📝 **Function**: Manual text input for testing
- 🧪 **Purpose**: Test send methods without RFID tags
- ⌨️ **Usage**: Type any text to simulate tag data

#### 27. Send Key Events Button
- ⌨️ **Function**: Send Text To Send (26) using Key Injection method
- 🧪 **Purpose**: Test keyboard injection functionality
- 🎯 **Target**: Uses current Window Filter (2) setting

#### 28. Send Clipboard Button  
- 📋 **Function**: Send Text To Send (26) using Clipboard Paste method
- 🧪 **Purpose**: Test clipboard paste functionality
- 🎯 **Target**: Uses current Window Filter (2) setting

---

## 💡 Best Practices

### Optimal Workflow
1. **🔌 Connect device first** - Establish communication before configuration
2. **⚙️ Configure antenna settings** - Apply settings before reading
3. **🎯 Test with debug tools** - Verify window filtering before live reading
4. **📊 Monitor status indicators** - Watch for connection/reading state changes
5. **💾 Save configurations** - Preserve working setups for future use

### Performance Tips
- 🔄 Use **CLIPBOARDPASTE** for best performance
- 📊 Disable "Show EPC Sent" for high-volume operations  
- ⚡ Keep default baud rate (921600)
- 🎯 Use specific window filters to reduce processing overhead

### Troubleshooting with UI
- 🧪 Use debug section to test connectivity
- 📊 Monitor status labels for error messages
- 🔄 Use Refresh Values when devices don't appear
- 📋 Check EPC Sent list to verify data flow

---

## 🔗 Related Topics

- **[Configuration Guide](Configuration.md)** - Advanced Config.xml settings
- **[Setup Guide](Setup.md)** - Connection and device configuration
- **[Troubleshooting](Troubleshooting.md)** - Common UI issues and solutions
- **[MQTT Integration](MQTT.md)** - MQTT protocol configuration

---

*Having UI issues? Check our [Troubleshooting Guide](Troubleshooting.md) or return to [Home](Home).*
