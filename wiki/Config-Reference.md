# ⚙️ Config.xml Complete Reference

Comprehensive reference for all configuration parameters in FXP20 Key Injector's Config.xml file.

---

## 📋 Overview

The `Config.xml` file controls all aspects of FXP20 Key Injector behavior. This reference provides complete documentation for every available parameter, organized by functional category.

**File Location:** Same directory as `FXP20KeyInjector.exe`

⚠️ **Important Note**: This reference documents the complete configuration schema based on the actual config.xml structure. All parameters listed are supported by the application.

---

## ✅ Currently Supported Elements

Based on the actual config.xml structure, these elements are confirmed to work:

```xml
<?xml version="1.0" encoding="utf-8"?>
<Configuration>
  <!-- Basic Application Settings -->
  <TargetWindowFilter>Notepad</TargetWindowFilter>
  <ComPort>COM7</ComPort>
  <BaudRate>921600</BaudRate>
  <Protocol>CLIPBOARDPASTE</Protocol>
  <ClipboardPasteDelay>500</ClipboardPasteDelay>
  
  <!-- Auto-Startup -->
  <AutoConnect>true</AutoConnect>
  <AutoStartReading>true</AutoStartReading>
  <StartMinimized>true</StartMinimized>
  
  <!-- Data Formatting -->
  <AddCSVSeparator>false</AddCSVSeparator>
  <AddCR>true</AddCR>
  <AddLF>false</AddLF>
  
  <!-- Audio Feedback -->
  <BeepOnRead>true</BeepOnRead>
  <nbBeeps>1</nbBeeps>
  <beepSleepTime>400</beepSleepTime>
  
  <!-- Reading Control -->
  <BatchSize>10</BatchSize>
  <RemoveDuplicates>true</RemoveDuplicates>
  
  <!-- Keyboard Hook -->
  <HookKeyboardToStartReading>true</HookKeyboardToStartReading>
  <HookKeyboardKey>123</HookKeyboardKey>
  <HookKeyboardReadingDurationInMs>3000</HookKeyboardReadingDurationInMs>
  
  <!-- GPIO Control -->
  <PerformReadingWithGPIO>false</PerformReadingWithGPIO>
  <PerformReadingGPIOPort>1</PerformReadingGPIOPort>
  <PerformReadingDuration>3000</PerformReadingDuration>
  
  <!-- MQTT Settings -->
  <MQTTServer>127.0.0.1</MQTTServer>
  <MQTTPort>1883</MQTTPort>
  <MQTTUser>user</MQTTUser>
  <MQTTPassword>sko</MQTTPassword>
  <MQTTSendTopic>FXP20/EPC</MQTTSendTopic>
  <MQTTControlTopic>FXP20/Control</MQTTControlTopic>
  
  <!-- Antenna Configuration -->
  <AntennasConfig>
    <antennaConfig>
      <Antenna_ID>1</Antenna_ID>
      <TransmitPowerIndex>36</TransmitPowerIndex>
      <ReceiveSensitivityIndex>0</ReceiveSensitivityIndex>
      <SingulationControl_Session>SESSION_S0</SingulationControl_Session>
      <!-- Additional antenna parameters... -->
    </antennaConfig>
  </AntennasConfig>
</Configuration>
```

---

## 🔧 Basic Structure

### XML Template
```xml
<?xml version="1.0" encoding="utf-8"?>
<Configuration>
  <!-- Configuration parameters go here -->
</Configuration>
```

### Parameter Types
- **📝 String**: Text values (e.g., `<ComPort>COM5</ComPort>`)
- **🔢 Integer**: Numeric values (e.g., `<BaudRate>921600</BaudRate>`)
- **✅ Boolean**: True/false values (e.g., `<AutoConnect>true</AutoConnect>`)
- **📋 Enum**: Predefined options (e.g., `<Protocol>CLIPBOARDPASTE</Protocol>`)

---

## 🔌 Connection Settings

### Serial Communication
```xml
<!-- COM Port Configuration -->
<ComPort>COM5</ComPort>                        <!-- String: COM port name (e.g., COM1, COM2) -->
<BaudRate>921600</BaudRate>                    <!-- Integer: Baud rate (9600, 115200, 460800, 921600) -->

<!-- Connection Behavior -->
<AutoConnect>true</AutoConnect>                <!-- Boolean: Auto-connect on startup -->

```


---

## 📡 Data Delivery Protocols

### Protocol Selection
```xml
<!-- Protocol Configuration -->
<Protocol>CLIPBOARDPASTE</Protocol>            <!-- Enum: CLIPBOARDPASTE, KEYINJECTION, MQTT -->
```

### Clipboard Paste Protocol
```xml
<!-- Clipboard Paste Settings -->
<ClipboardPasteDelay>500</ClipboardPasteDelay> <!-- Integer: Delay before paste (ms) -->
```

### Keyboard Injection Protocol  
```xml
<Protocol>KEYINJECTION</Protocol>
```

### MQTT Protocol
```xml
<!-- MQTT Connection Settings -->
<MQTTServer>127.0.0.1</MQTTServer>             <!-- String: MQTT broker IP/hostname -->
<MQTTPort>1883</MQTTPort>                      <!-- Integer: MQTT broker port -->
<MQTTUser>username</MQTTUser>                  <!-- String: Authentication username -->
<MQTTPassword>password</MQTTPassword>          <!-- String: Authentication password -->

<!-- MQTT Topics -->
<MQTTSendTopic>fxp20/data</MQTTSendTopic>      <!-- String: Topic for publishing tag data -->
<MQTTControlTopic>fxp20/control</MQTTControlTopic> <!-- String: Topic for control commands -->

```

---

## 🎯 Target Application Settings

### Window Filtering
```xml
<!-- Target Window Configuration -->
<TargetWindowFilter>Notepad</TargetWindowFilter>  <!-- String: Target window title/class -->
```

---

## 📊 Data Formatting

### Basic Formatting
```xml
<!-- Data Format Settings -->
<AddCR>true</AddCR>                           <!-- Boolean: Add carriage return (Enter) -->
<AddLF>false</AddLF>                          <!-- Boolean: Add line feed -->

```

### CSV Configuration
```xml
<!-- CSV Configuration (supported) -->
<AddCSVSeparator>false</AddCSVSeparator>      <!-- Boolean: Add CSV comma separator -->

```

---

## 🎛️ GPIO Hardware Control

### GPIO Configuration
```xml
<!-- GPIO Button Control -->
<PerformReadingWithGPIO>true</PerformReadingWithGPIO> <!-- Boolean: Enable GPIO button trigger -->
<PerformReadingDuration>5000</PerformReadingDuration> <!-- Integer: Reading duration (ms) -->
<PerformReadingGPIOPort>1</PerformReadingGPIOPort>    <!-- Integer: GPIO port number -->

```

---

## ⌨️ Keyboard Hook Control

### Keyboard Triggers
```xml
<!-- Keyboard Hook Configuration -->
<HookKeyboardToStartReading>true</HookKeyboardToStartReading> <!-- Boolean: Enable keyboard triggers -->
<HookKeyboardKey>123</HookKeyboardKey>        <!-- Integer: Key code (e.g., 123 for F12) -->
<HookKeyboardReadingDurationInMs>3000</HookKeyboardReadingDurationInMs> <!-- Integer: Reading duration (ms) -->

```

---

## 📡 RFID Reading Configuration

### Basic Reading Settings
```xml
<!-- Reading Behavior -->
<AutoStartReading>true</AutoStartReading>      <!-- Boolean: Start reading after connection -->

<!-- Duplicate Handling -->
<RemoveDuplicates>true</RemoveDuplicates>      <!-- Boolean: Filter duplicate tags -->

```

### Advanced Reading Settings
```xml
<!-- Tag Processing -->
<BatchSize>10</BatchSize>                     <!-- Integer: Tags per batch -->

```

---

## 📡 Antenna and RF Settings

The FXP20 supports complex antenna configurations through the `AntennasConfig` section. This allows per-antenna settings for power, frequency, and RF parameters.

### AntennasConfig Structure
```xml
<!-- Antenna Configuration -->
<AntennasConfig>
  <antennaConfig>
    <Antenna_ID>1</Antenna_ID>                    <!-- Integer: Antenna ID (1-4) -->
    <RFMode_Tari>0</RFMode_Tari>                  <!-- Integer: RF mode Tari setting -->
    <RFMode_TableIndex>2</RFMode_TableIndex>      <!-- Integer: RF mode table index -->
    <ReceiveSensitivityIndex>0</ReceiveSensitivityIndex> <!-- Integer: Receive sensitivity -->
    <TransmitPowerIndex>36</TransmitPowerIndex>   <!-- Integer: Transmit power (0-36) -->
    <TransmitFrequencyIndex>1</TransmitFrequencyIndex> <!-- Integer: Frequency index -->
    <SingulationControl_Session>SESSION_S0</SingulationControl_Session> <!-- Enum: Session type -->
    <SingulationControl_TagPopulation>30</SingulationControl_TagPopulation> <!-- Integer: Tag population -->
    <SingulationControl_TagTransitTime>30</SingulationControl_TagTransitTime> <!-- Integer: Transit time -->
    <SingulationControl_PerformStateAwareSingulationAction>true</SingulationControl_PerformStateAwareSingulationAction> <!-- Boolean -->
    <SingulationControl_Sl_Flag>SL_ALL</SingulationControl_Sl_Flag> <!-- Enum: SL flag setting -->
    <SingulationControl_InventoryState>INVENTORY_STATE_AB_FLIP</SingulationControl_InventoryState> <!-- Enum: Inventory state -->
  </antennaConfig>
  <!-- Additional antennaConfig entries for multiple antennas -->
</AntennasConfig>
```

### Multiple Antenna Configuration
```xml
<AntennasConfig>
  <!-- Antenna 1: High power for long range -->
  <antennaConfig>
    <Antenna_ID>1</Antenna_ID>
    <TransmitPowerIndex>36</TransmitPowerIndex>
    <SingulationControl_Session>SESSION_S0</SingulationControl_Session>
  </antennaConfig>
  
  <!-- Antenna 2: Lower power for close range -->
  <antennaConfig>
    <Antenna_ID>2</Antenna_ID>
    <TransmitPowerIndex>15</TransmitPowerIndex>
    <SingulationControl_Session>SESSION_S2</SingulationControl_Session>
  </antennaConfig>
</AntennasConfig>
```

---

## 🔊 Audio Configuration

### Beep Settings
```xml
<!-- Audio Feedback -->
<BeepOnRead>true</BeepOnRead>                 <!-- Boolean: Beep when tag is read -->
<nbBeeps>1</nbBeeps>                         <!-- Integer: Number of beeps -->
<beepSleepTime>400</beepSleepTime>           <!-- Integer: Time between beeps (ms) -->
```

### Beep Examples
```xml
<!-- Single beep -->
<BeepOnRead>true</BeepOnRead>
<nbBeeps>1</nbBeeps>
<beepSleepTime>0</beepSleepTime>

<!-- Double beep -->
<BeepOnRead>true</BeepOnRead>
<nbBeeps>2</nbBeeps>
<beepSleepTime>200</beepSleepTime>

<!-- Triple beep -->
<BeepOnRead>true</BeepOnRead>
<nbBeeps>3</nbBeeps>
<beepSleepTime>150</beepSleepTime>
```

---

## 🖥️ User Interface Settings

### Window Behavior
```xml
<!-- Application Window -->
<StartMinimized>false</StartMinimized>        <!-- Boolean: Start application minimized -->

```


---

## 📝 Configuration Examples

### Basic Desktop Setup
```xml
<?xml version="1.0" encoding="utf-8"?>
<Configuration>
  <!-- Basic desktop configuration -->
  <ComPort>COM5</ComPort>
  <BaudRate>921600</BaudRate>
  <Protocol>CLIPBOARDPASTE</Protocol>
  <TargetWindowFilter>Notepad</TargetWindowFilter>
  <AutoConnect>true</AutoConnect>
  <AutoStartReading>true</AutoStartReading>
  <RemoveDuplicates>true</RemoveDuplicates>
  <BeepOnRead>true</BeepOnRead>
  <AddCR>true</AddCR>
</Configuration>
```

### Production Warehouse Setup
```xml
<?xml version="1.0" encoding="utf-8"?>
<Configuration>
  <!-- Production warehouse configuration -->
  <ComPort>COM3</ComPort>
  <BaudRate>921600</BaudRate>
  <Protocol>MQTT</Protocol>
  <MQTTServer>192.168.1.100</MQTTServer>
  <MQTTPort>1883</MQTTPort>
  <MQTTUser>warehouse_user</MQTTUser>
  <MQTTPassword>secure_password</MQTTPassword>
  <MQTTSendTopic>warehouse/reader1/tags</MQTTSendTopic>
  <MQTTControlTopic>warehouse/reader1/control</MQTTControlTopic>
  <AutoConnect>true</AutoConnect>
  <AutoStartReading>true</AutoStartReading>
  <PerformReadingWithGPIO>true</PerformReadingWithGPIO>
  <PerformReadingGPIOPort>1</PerformReadingGPIOPort>
  <PerformReadingDuration>5000</PerformReadingDuration>
  <RemoveDuplicates>true</RemoveDuplicates>
  <BeepOnRead>true</BeepOnRead>
  <nbBeeps>2</nbBeeps>
  <beepSleepTime>300</beepSleepTime>
  <StartMinimized>true</StartMinimized>
  <AntennasConfig>
    <antennaConfig>
      <Antenna_ID>1</Antenna_ID>
      <TransmitPowerIndex>25</TransmitPowerIndex>
      <SingulationControl_Session>SESSION_S0</SingulationControl_Session>
    </antennaConfig>
  </AntennasConfig>
</Configuration>
```

---

## ✅ Configuration Validation

### Validation Rules

#### Required Parameters
- **ComPort**: Must be valid COM port name
- **BaudRate**: Must be supported baud rate (921600 recommended)
- **Protocol**: Must be CLIPBOARDPASTE, KEYINJECTION, or MQTT

#### Value Ranges
- **TransmitPowerIndex**: 0-36 (configured per antenna in AntennasConfig)
- **PerformReadingDuration**: 100-300000 (milliseconds)
- **BaudRate**: 9600, 19200, 38400, 57600, 115200, 460800, 921600

#### Dependencies
- **MQTT settings**: Required when `Protocol=MQTT`
- **GPIO settings**: Required when `PerformReadingWithGPIO=true`
- **Window settings**: Required for CLIPBOARDPASTE and KEYINJECTION protocols


---

## 🔧 Configuration Management

### File Operations
- **💾 Save Config**: Click "Save Config" button in GUI
- **📂 Load Config**: Click "Load Config" button to refresh from file
- **🔄 Reset**: Delete Config.xml to restore defaults
- **💾 Backup**: Copy Config.xml to backup location


---

## 📚 Related Resources

- **[Configuration Guide](Configuration.md)** - Step-by-step configuration tutorial
- **[User Interface Guide](User-Interface.md)** - GUI configuration options
- **[MQTT Integration](MQTT.md)** - MQTT-specific configuration
- **[GPIO Control](GPIO.md)** - GPIO configuration details
- **[Antenna Configuration](Antenna-Configuration.md)** - RF and antenna settings

---

*Need help with specific parameters? Check the related guides above or return to [Home](Home.md).*