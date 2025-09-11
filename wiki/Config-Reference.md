# ⚙️ Config.xml Complete Reference

Comprehensive reference for all configuration parameters in FXP20 Key Injector's Config.xml file.

---

## 📋 Overview

The `Config.xml` file controls all aspects of FXP20 Key Injector behavior. This reference provides complete documentation for every available parameter, organized by functional category.

**File Location:** Same directory as `FXP20KeyInjector.exe`

---

## 🔧 Basic Structure

### XML Template
```xml
<?xml version="1.0" encoding="utf-8"?>
<FXP20KeyInjectorConfig>
  <!-- Configuration parameters go here -->
</FXP20KeyInjectorConfig>
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
<DataBits>8</DataBits>                         <!-- Integer: Data bits (7, 8) -->
<Parity>None</Parity>                          <!-- Enum: None, Odd, Even, Mark, Space -->
<StopBits>One</StopBits>                       <!-- Enum: None, One, Two, OnePointFive -->
<Handshake>None</Handshake>                    <!-- Enum: None, XOnXOff, RequestToSend, RequestToSendXOnXOff -->

<!-- Connection Behavior -->
<AutoConnect>true</AutoConnect>                <!-- Boolean: Auto-connect on startup -->
<AutoConnectDelay>5000</AutoConnectDelay>      <!-- Integer: Delay before auto-connect (ms) -->
<ConnectionTimeout>10000</ConnectionTimeout>    <!-- Integer: Connection timeout (ms) -->
<ReconnectOnError>true</ReconnectOnError>      <!-- Boolean: Auto-reconnect on disconnection -->
<MaxReconnectAttempts>5</MaxReconnectAttempts> <!-- Integer: Maximum reconnection attempts -->
<ReconnectDelay>5000</ReconnectDelay>          <!-- Integer: Delay between reconnect attempts (ms) -->
```

### Connection Validation
```xml
<!-- Connection Testing -->
<PingDevice>true</PingDevice>                  <!-- Boolean: Send ping to verify connection -->
<PingInterval>30000</PingInterval>             <!-- Integer: Ping interval (ms) -->
<PingTimeout>5000</PingTimeout>                <!-- Integer: Ping response timeout (ms) -->
<PingRetries>3</PingRetries>                   <!-- Integer: Ping retry attempts -->
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
<ClipboardPasteDelay>100</ClipboardPasteDelay> <!-- Integer: Delay before paste (ms) -->
<RestoreClipboard>true</RestoreClipboard>      <!-- Boolean: Restore original clipboard content -->
<ConfirmPaste>false</ConfirmPaste>             <!-- Boolean: Show paste confirmation -->
<MaxPasteLength>1000</MaxPasteLength>          <!-- Integer: Maximum paste data length -->
<PasteTimeout>5000</PasteTimeout>              <!-- Integer: Paste operation timeout (ms) -->
```

### Keyboard Injection Protocol  
```xml
<!-- Keyboard Injection Settings -->
<KeyInjectionDelay>10</KeyInjectionDelay>      <!-- Integer: Delay between characters (ms) -->
<CharacterTimeout>100</CharacterTimeout>       <!-- Integer: Timeout per character (ms) -->
<KeyPressTimeout>1000</KeyPressTimeout>        <!-- Integer: Max time per keypress (ms) -->
<RetryFailedKeys>3</RetryFailedKeys>           <!-- Integer: Retry count for failed keys -->
<SkipNonPrintable>false</SkipNonPrintable>    <!-- Boolean: Skip control characters -->
<SendModifierKeys>true</SendModifierKeys>      <!-- Boolean: Enable Ctrl, Alt, Shift keys -->
```

### MQTT Protocol
```xml
<!-- MQTT Connection Settings -->
<MQTTServer>127.0.0.1</MQTTServer>             <!-- String: MQTT broker IP/hostname -->
<MQTTPort>1883</MQTTPort>                      <!-- Integer: MQTT broker port -->
<MQTTUser>username</MQTTUser>                  <!-- String: Authentication username -->
<MQTTPassword>password</MQTTPassword>          <!-- String: Authentication password -->
<MQTTClientId>FXP20_001</MQTTClientId>         <!-- String: MQTT client identifier -->

<!-- MQTT Topics -->
<MQTTSendTopic>fxp20/data</MQTTSendTopic>      <!-- String: Topic for publishing tag data -->
<MQTTControlTopic>fxp20/control</MQTTControlTopic> <!-- String: Topic for control commands -->

<!-- MQTT Behavior -->
<MQTTKeepAlive>60</MQTTKeepAlive>              <!-- Integer: Keep-alive interval (seconds) -->
<MQTTReconnect>true</MQTTReconnect>            <!-- Boolean: Auto-reconnect to broker -->
<MQTTRetain>false</MQTTRetain>                 <!-- Boolean: Retain published messages -->
<MQTTQOS>1</MQTTQOS>                          <!-- Integer: Quality of Service (0, 1, 2) -->
<MQTTTimeout>30000</MQTTTimeout>               <!-- Integer: Connection timeout (ms) -->
```

---

## 🎯 Target Application Settings

### Window Filtering
```xml
<!-- Target Window Configuration -->
<WindowFilter>Notepad</WindowFilter>          <!-- String: Target window title/class -->
<WindowFilterExact>false</WindowFilterExact>   <!-- Boolean: Exact match required -->
<WindowFilterCaseSensitive>false</WindowFilterCaseSensitive> <!-- Boolean: Case sensitive matching -->
<WaitForWindow>true</WaitForWindow>            <!-- Boolean: Wait for target window -->
<WindowWaitTimeout>30000</WindowWaitTimeout>   <!-- Integer: Max wait time for window (ms) -->

<!-- Window Focus Management -->
<FocusWindow>true</FocusWindow>                <!-- Boolean: Bring target window to front -->
<RestoreFocus>true</RestoreFocus>              <!-- Boolean: Restore original focus after send -->
<FocusDelay>100</FocusDelay>                   <!-- Integer: Delay after focusing window (ms) -->
```

---

## 📊 Data Formatting

### Basic Formatting
```xml
<!-- Data Format Settings -->
<AddCR>true</AddCR>                           <!-- Boolean: Add carriage return (Enter) -->
<AddLF>false</AddLF>                          <!-- Boolean: Add line feed -->
<AddTab>false</AddTab>                        <!-- Boolean: Add tab character -->
<AddSpace>false</AddSpace>                    <!-- Boolean: Add space character -->

<!-- Text Transformation -->
<ConvertToUpper>false</ConvertToUpper>        <!-- Boolean: Convert to uppercase -->
<ConvertToLower>false</ConvertToLower>        <!-- Boolean: Convert to lowercase -->
<TrimWhitespace>true</TrimWhitespace>         <!-- Boolean: Remove leading/trailing spaces -->
<RemoveSpaces>false</RemoveSpaces>            <!-- Boolean: Remove all spaces -->
```

### Advanced Formatting
```xml
<!-- Custom Formatting -->
<DataPrefix></DataPrefix>                     <!-- String: Text to add before tag data -->
<DataSuffix></DataSuffix>                     <!-- String: Text to add after tag data -->
<FieldSeparator>,</FieldSeparator>            <!-- String: Separator between data fields -->

<!-- CSV Configuration -->
<AddCSVSeparator>false</AddCSVSeparator>      <!-- Boolean: Add CSV comma separator -->
<CSVSeparator>,</CSVSeparator>                <!-- String: Custom CSV separator character -->
<CSVQuoteChar>"</CSVQuoteChar>                <!-- String: CSV quote character -->
<CSVEscapeChar>\</CSVEscapeChar>              <!-- String: CSV escape character -->

<!-- Character Replacement -->
<ReplaceChars>false</ReplaceChars>            <!-- Boolean: Enable character replacement -->
<ReplaceFrom> </ReplaceFrom>                  <!-- String: Characters to replace -->
<ReplaceTo>_</ReplaceTo>                      <!-- String: Replacement characters -->
```

---

## 🎛️ GPIO Hardware Control

### GPIO Configuration
```xml
<!-- GPIO Button Control -->
<HookGPIOToStartReading>true</HookGPIOToStartReading> <!-- Boolean: Enable GPIO button trigger -->
<GPIOReadingDurationInMs>5000</GPIOReadingDurationInMs> <!-- Integer: Reading duration (ms) -->
<GPIOPin>1</GPIOPin>                          <!-- Integer: GPIO pin number -->
<GPIOActiveHigh>false</GPIOActiveHigh>        <!-- Boolean: Pin active state (true=HIGH, false=LOW) -->

<!-- GPIO Timing -->
<GPIODebounceMs>50</GPIODebounceMs>           <!-- Integer: Button debounce time (ms) -->
<GPIOMinPressTime>100</GPIOMinPressTime>      <!-- Integer: Minimum press duration (ms) -->
<GPIOMaxPressTime>10000</GPIOMaxPressTime>    <!-- Integer: Maximum press duration (ms) -->

<!-- GPIO Behavior -->
<GPIOTriggerMode>PRESS</GPIOTriggerMode>      <!-- Enum: PRESS, RELEASE, HOLD -->
<ContinuousGPIOReading>false</ContinuousGPIOReading> <!-- Boolean: Continuous vs timed reading -->
<GPIOSessionTimeout>30000</GPIOSessionTimeout> <!-- Integer: Max session duration (ms) -->
```

### Multi-GPIO Support
```xml
<!-- Multiple GPIO Buttons -->
<GPIOButton1Pin>1</GPIOButton1Pin>            <!-- Integer: First button pin -->
<GPIOButton1Action>START_READING</GPIOButton1Action> <!-- Enum: START_READING, STOP_READING, BEEP -->
<GPIOButton1Duration>5000</GPIOButton1Duration> <!-- Integer: Action duration (ms) -->

<GPIOButton2Pin>2</GPIOButton2Pin>            <!-- Integer: Second button pin -->
<GPIOButton2Action>STOP_READING</GPIOButton2Action> <!-- Enum: Action for second button -->

<GPIOButton3Pin>3</GPIOButton3Pin>            <!-- Integer: Third button pin -->
<GPIOButton3Action>BEEP</GPIOButton3Action>   <!-- Enum: Action for third button -->
```

---

## ⌨️ Keyboard Hook Control

### Keyboard Triggers
```xml
<!-- Keyboard Hook Configuration -->
<HookKeyboardToStartReading>true</HookKeyboardToStartReading> <!-- Boolean: Enable keyboard triggers -->
<HookKeyboardReadingDurationInMs>3000</HookKeyboardReadingDurationInMs> <!-- Integer: Reading duration (ms) -->

<!-- Trigger Keys -->
<StartReadingKey>F1</StartReadingKey>         <!-- String: Key to start reading -->
<StopReadingKey>F2</StopReadingKey>          <!-- String: Key to stop reading -->
<BeepKey>F3</BeepKey>                        <!-- String: Key to trigger beep -->

<!-- Key Combinations -->
<UseModifierKeys>true</UseModifierKeys>       <!-- Boolean: Enable Ctrl+Key, Alt+Key combinations -->
<RequireCtrl>false</RequireCtrl>             <!-- Boolean: Require Ctrl key -->
<RequireAlt>false</RequireAlt>               <!-- Boolean: Require Alt key -->
<RequireShift>false</RequireShift>           <!-- Boolean: Require Shift key -->
```

---

## 📡 RFID Reading Configuration

### Basic Reading Settings
```xml
<!-- Reading Behavior -->
<AutoStartReading>true</AutoStartReading>      <!-- Boolean: Start reading after connection -->
<AutoStartDelay>2000</AutoStartDelay>          <!-- Integer: Delay before auto-start (ms) -->
<ContinuousReading>true</ContinuousReading>    <!-- Boolean: Continuous vs session-based reading -->
<ReadingInterval>100</ReadingInterval>         <!-- Integer: Interval between reads (ms) -->

<!-- Duplicate Handling -->
<RemoveDuplicates>true</RemoveDuplicates>      <!-- Boolean: Filter duplicate tags -->
<DuplicateTimeoutMs>1000</DuplicateTimeoutMs> <!-- Integer: Duplicate filter timeout (ms) -->
<DuplicateMatchMode>EXACT</DuplicateMatchMode> <!-- Enum: EXACT, PARTIAL, FUZZY -->
```

### Advanced Reading Settings
```xml
<!-- Tag Processing -->
<BatchSize>10</BatchSize>                     <!-- Integer: Tags per batch -->
<BatchTimeout>5000</BatchTimeout>             <!-- Integer: Batch processing timeout (ms) -->
<MaxTagsPerSession>100</MaxTagsPerSession>    <!-- Integer: Maximum tags in one session -->

<!-- Error Handling -->
<RetryOnError>true</RetryOnError>             <!-- Boolean: Retry failed operations -->
<MaxRetries>3</MaxRetries>                    <!-- Integer: Maximum retry attempts -->
<RetryDelay>1000</RetryDelay>                 <!-- Integer: Delay between retries (ms) -->
<IgnoreReadErrors>false</IgnoreReadErrors>    <!-- Boolean: Continue on read errors -->
```

---

## 📡 Antenna and RF Settings

### Power Configuration
```xml
<!-- Transmit Power -->
<TransmitPower>25</TransmitPower>             <!-- Integer: Power index (0-30) -->
<MaxTransmitPower>30</MaxTransmitPower>       <!-- Integer: Maximum allowable power -->
<MinTransmitPower>10</MinTransmitPower>       <!-- Integer: Minimum working power -->
<AutoAdjustPower>false</AutoAdjustPower>      <!-- Boolean: Automatic power adjustment -->
<PowerStepSize>2</PowerStepSize>              <!-- Integer: Power adjustment increment -->
```

### Session Parameters
```xml
<!-- Gen2 Session Settings -->
<Session>S0</Session>                         <!-- Enum: S0, S1, S2, S3 -->
<Target>A</Target>                           <!-- Enum: A, B -->
<Action>INV_A</Action>                       <!-- Enum: Inventory action -->
<SessionTimeout>2000</SessionTimeout>         <!-- Integer: Session timeout (ms) -->

<!-- Timing Parameters -->
<InventoryDuration>1000</InventoryDuration>   <!-- Integer: Inventory round duration (ms) -->
<ReadTimeout>500</ReadTimeout>                <!-- Integer: Individual tag read timeout (ms) -->
<TagReportInterval>100</TagReportInterval>    <!-- Integer: Tag reporting frequency (ms) -->
```

### Regional Settings
```xml
<!-- Regulatory Configuration -->
<Region>NA</Region>                          <!-- Enum: NA (North America), EU (Europe), AP (Asia Pacific) -->
<ChannelList>1,2,3,4</ChannelList>           <!-- String: Comma-separated channel list -->
<HoppingEnabled>true</HoppingEnabled>         <!-- Boolean: Frequency hopping enabled -->
<DwellTime>200</DwellTime>                   <!-- Integer: Channel dwell time (ms) -->
<MaxEIRP>36</MaxEIRP>                        <!-- Integer: Maximum EIRP (dBm) -->
```

---

## 🔊 Audio Configuration

### Beep Settings
```xml
<!-- Audio Feedback -->
<BeepOnRead>true</BeepOnRead>                 <!-- Boolean: Beep when tag is read -->
<BeepDuration>200</BeepDuration>              <!-- Integer: Beep duration (ms) -->
<BeepFrequency>2000</BeepFrequency>           <!-- Integer: Beep frequency (Hz) -->
<BeepVolume>50</BeepVolume>                   <!-- Integer: Beep volume (0-100) -->

<!-- Session Audio -->
<BeepOnConnect>true</BeepOnConnect>           <!-- Boolean: Beep when device connects -->
<BeepOnDisconnect>true</BeepOnDisconnect>     <!-- Boolean: Beep when device disconnects -->
<BeepOnSessionStart>true</BeepOnSessionStart> <!-- Boolean: Beep at session start -->
<BeepOnSessionEnd>true</BeepOnSessionEnd>     <!-- Boolean: Beep at session end -->
<BeepOnError>true</BeepOnError>               <!-- Boolean: Beep on errors -->
```

### Advanced Audio
```xml
<!-- Custom Beep Patterns -->
<BeepPattern>Single</BeepPattern>             <!-- Enum: Single, Double, Triple, Custom -->
<CustomBeepPattern>200,100,200</CustomBeepPattern> <!-- String: Custom pattern (ms,pause,ms) -->
<BeepOnSpecificTags>false</BeepOnSpecificTags> <!-- Boolean: Beep only for specific tags -->
<BeepTagList>TAG001,TAG002</BeepTagList>      <!-- String: Comma-separated tag list -->
```

---

## 🖥️ User Interface Settings

### Window Behavior
```xml
<!-- Application Window -->
<StartMinimized>false</StartMinimized>        <!-- Boolean: Start application minimized -->
<MinimizeToTray>false</MinimizeToTray>        <!-- Boolean: Minimize to system tray -->
<ShowNotifications>true</ShowNotifications>    <!-- Boolean: Show popup notifications -->
<NotificationTimeout>5000</NotificationTimeout> <!-- Integer: Notification display time (ms) -->

<!-- GUI Elements -->
<ShowEPCSent>true</ShowEPCSent>               <!-- Boolean: Show sent EPC list -->
<ShowStatusBar>true</ShowStatusBar>           <!-- Boolean: Show status bar -->
<ShowToolbar>true</ShowToolbar>               <!-- Boolean: Show toolbar -->
<MaxEPCHistory>1000</MaxEPCHistory>           <!-- Integer: Maximum EPC history entries -->
```

### Visual Feedback
```xml
<!-- Status Indicators -->
<ShowConnectionStatus>true</ShowConnectionStatus> <!-- Boolean: Show connection status -->
<ShowReadingStatus>true</ShowReadingStatus>   <!-- Boolean: Show reading status -->
<StatusUpdateInterval>500</StatusUpdateInterval> <!-- Integer: Status update frequency (ms) -->

<!-- Colors and Themes -->
<StatusConnectedColor>Green</StatusConnectedColor> <!-- String: Color for connected status -->
<StatusDisconnectedColor>Red</StatusDisconnectedColor> <!-- String: Color for disconnected status -->
<StatusReadingColor>Blue</StatusReadingColor> <!-- String: Color for reading status -->
```

---

## 📊 Logging and Monitoring

### Log Configuration
```xml
<!-- Logging Settings -->
<EnableLogging>true</EnableLogging>           <!-- Boolean: Enable application logging -->
<LogLevel>Info</LogLevel>                     <!-- Enum: Debug, Info, Warning, Error -->
<LogFile>FXP20KeyInjector.log</LogFile>       <!-- String: Log file name -->
<LogMaxSize>10</LogMaxSize>                   <!-- Integer: Maximum log size (MB) -->
<LogMaxFiles>5</LogMaxFiles>                  <!-- Integer: Maximum number of log files -->

<!-- Log Content -->
<LogConnections>true</LogConnections>         <!-- Boolean: Log connection events -->
<LogReads>true</LogReads>                     <!-- Boolean: Log tag reads -->
<LogErrors>true</LogErrors>                   <!-- Boolean: Log error events -->
<LogPerformance>false</LogPerformance>        <!-- Boolean: Log performance metrics -->
<LogTimestamps>true</LogTimestamps>           <!-- Boolean: Include timestamps in logs -->
```

### Performance Monitoring
```xml
<!-- Performance Tracking -->
<TrackReadRate>true</TrackReadRate>           <!-- Boolean: Track tags per second -->
<TrackRSSI>true</TrackRSSI>                   <!-- Boolean: Track signal strength -->
<TrackRetryRate>true</TrackRetryRate>         <!-- Boolean: Track retry attempts -->
<TrackDuplicates>true</TrackDuplicates>       <!-- Boolean: Track duplicate counts -->
<PerformanceInterval>60000</PerformanceInterval> <!-- Integer: Performance reporting interval (ms) -->
```

---

## 🔧 Advanced Configuration

### Error Handling
```xml
<!-- Error Recovery -->
<AutoRecover>true</AutoRecover>               <!-- Boolean: Automatic error recovery -->
<RecoveryDelay>5000</RecoveryDelay>           <!-- Integer: Recovery attempt delay (ms) -->
<MaxRecoveryAttempts>3</MaxRecoveryAttempts>  <!-- Integer: Maximum recovery attempts -->
<ResetOnError>false</ResetOnError>            <!-- Boolean: Reset device on errors -->

<!-- Timeout Handling -->
<DefaultTimeout>5000</DefaultTimeout>         <!-- Integer: Default operation timeout (ms) -->
<CommandTimeout>10000</CommandTimeout>        <!-- Integer: Command execution timeout (ms) -->
<ResponseTimeout>3000</ResponseTimeout>       <!-- Integer: Response waiting timeout (ms) -->
```

### System Integration
```xml
<!-- Windows Integration -->
<RegisterFileTypes>false</RegisterFileTypes>   <!-- Boolean: Register config file types -->
<CreateDesktopShortcut>false</CreateDesktopShortcut> <!-- Boolean: Create desktop shortcut -->
<StartWithWindows>false</StartWithWindows>     <!-- Boolean: Start with Windows -->
<RunAsService>false</RunAsService>            <!-- Boolean: Run as Windows service -->

<!-- Security -->
<RequireElevation>false</RequireElevation>    <!-- Boolean: Require administrator rights -->
<SecureConfig>false</SecureConfig>            <!-- Boolean: Encrypt sensitive config data -->
<AllowRemoteConfig>false</AllowRemoteConfig>  <!-- Boolean: Allow remote configuration -->
```

---

## 📝 Configuration Examples

### Basic Desktop Setup
```xml
<?xml version="1.0" encoding="utf-8"?>
<FXP20KeyInjectorConfig>
  <!-- Basic desktop configuration -->
  <ComPort>COM5</ComPort>
  <BaudRate>921600</BaudRate>
  <Protocol>CLIPBOARDPASTE</Protocol>
  <WindowFilter>Notepad</WindowFilter>
  <AutoConnect>true</AutoConnect>
  <AutoStartReading>true</AutoStartReading>
  <RemoveDuplicates>true</RemoveDuplicates>
  <BeepOnRead>true</BeepOnRead>
  <AddCR>true</AddCR>
</FXP20KeyInjectorConfig>
```

### Production Warehouse Setup
```xml
<?xml version="1.0" encoding="utf-8"?>
<FXP20KeyInjectorConfig>
  <!-- Production warehouse configuration -->
  <ComPort>COM3</ComPort>
  <BaudRate>921600</BaudRate>
  <Protocol>MQTT</Protocol>
  <MQTTServer>192.168.1.100</MQTTServer>
  <MQTTPort>1883</MQTTPort>
  <MQTTUser>warehouse_user</MQTTUser>
  <MQTTPassword>secure_password</MQTTPassword>
  <MQTTSendTopic>warehouse/reader1/tags</MQTTSendTopic>
  <AutoConnect>true</AutoConnect>
  <AutoStartReading>true</AutoStartReading>
  <HookGPIOToStartReading>true</HookGPIOToStartReading>
  <GPIOReadingDurationInMs>5000</GPIOReadingDurationInMs>
  <RemoveDuplicates>true</RemoveDuplicates>
  <TransmitPower>25</TransmitPower>
  <Session>S0</Session>
  <BeepOnRead>true</BeepOnRead>
  <StartMinimized>true</StartMinimized>
  <EnableLogging>true</EnableLogging>
  <LogLevel>Info</LogLevel>
</FXP20KeyInjectorConfig>
```

### Mobile/Battery Optimized Setup
```xml
<?xml version="1.0" encoding="utf-8"?>
<FXP20KeyInjectorConfig>
  <!-- Battery-optimized mobile configuration -->
  <ComPort>COM4</ComPort>
  <BaudRate>460800</BaudRate>
  <Protocol>CLIPBOARDPASTE</Protocol>
  <WindowFilter>Mobile App</WindowFilter>
  <AutoConnect>true</AutoConnect>
  <HookGPIOToStartReading>true</HookGPIOToStartReading>
  <GPIOReadingDurationInMs>3000</GPIOReadingDurationInMs>
  <RemoveDuplicates>true</RemoveDuplicates>
  <TransmitPower>16</TransmitPower>
  <AutoAdjustPower>true</AutoAdjustPower>
  <Session>S1</Session>
  <BeepOnRead>false</BeepOnRead>
  <ShowEPCSent>false</ShowEPCSent>
  <EnableLogging>false</EnableLogging>
  <MinimizeToTray>true</MinimizeToTray>
</FXP20KeyInjectorConfig>
```

---

## ✅ Configuration Validation

### Validation Rules

#### Required Parameters
- **ComPort**: Must be valid COM port name
- **BaudRate**: Must be supported baud rate
- **Protocol**: Must be valid protocol name

#### Value Ranges
- **TransmitPower**: 0-30
- **GPIOReadingDurationInMs**: 100-300000
- **BaudRate**: 9600, 19200, 38400, 57600, 115200, 460800, 921600
- **Session**: S0, S1, S2, S3
- **Target**: A, B

#### Dependencies
- **MQTT settings**: Required when `Protocol=MQTT`
- **GPIO settings**: Required when `HookGPIOToStartReading=true`
- **Window settings**: Required for CLIPBOARDPASTE and KEYINJECTION protocols

### Configuration Testing
```xml
<!-- Validation Settings -->
<ValidateConfig>true</ValidateConfig>         <!-- Boolean: Validate configuration on load -->
<StrictValidation>false</StrictValidation>    <!-- Boolean: Strict vs permissive validation -->
<ShowValidationErrors>true</ShowValidationErrors> <!-- Boolean: Display validation errors -->
<BackupConfig>true</BackupConfig>             <!-- Boolean: Backup config before changes -->
```

---

## 🔧 Configuration Management

### File Operations
- **💾 Save Config**: Click "Save Config" button in GUI
- **📂 Load Config**: Click "Load Config" button to refresh from file
- **🔄 Reset**: Delete Config.xml to restore defaults
- **💾 Backup**: Copy Config.xml to backup location

### Version Control
```xml
<!-- Configuration Metadata -->
<ConfigVersion>1.0</ConfigVersion>            <!-- String: Configuration format version -->
<CreatedDate>2025-09-11</CreatedDate>         <!-- String: Configuration creation date -->
<ModifiedDate>2025-09-11</ModifiedDate>       <!-- String: Last modification date -->
<CreatedBy>Administrator</CreatedBy>          <!-- String: User who created config -->
<Description>Production warehouse setup</Description> <!-- String: Configuration description -->
```

---

## 📚 Related Resources

- **[Configuration Guide](Configuration.md)** - Step-by-step configuration tutorial
- **[User Interface Guide](User-Interface.md)** - GUI configuration options
- **[MQTT Integration](MQTT.md)** - MQTT-specific configuration
- **[GPIO Control](GPIO.md)** - GPIO configuration details
- **[Antenna Configuration](Antenna-Configuration.md)** - RF and antenna settings

---

*Need help with specific parameters? Check the related guides above or return to [Home](Home.md).*