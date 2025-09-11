# 📡 Send Protocols Guide

Complete guide to data delivery methods: Keyboard Injection, Clipboard Paste, and MQTT messaging.

---

## 🎯 Protocol Overview

FXP20 Key Injector supports three methods for delivering tag data to applications:

| Protocol | Speed | Compatibility | Use Case |
|----------|--------|---------------|----------|
| 📋 **CLIPBOARDPASTE** | ⚡ Fast | 🟢 High | General use, best performance |
| ⌨️ **KEYINJECTION** | 🐌 Slower | 🟡 Medium | Legacy apps, character control |
| 🌐 **MQTT** | ⚡ Fast | 🟢 High | Enterprise, multiple subscribers |

---

## 📋 Clipboard Paste Protocol

### How It Works
1. **🏷️ Tag Read**: FXP20 device reads RFID tag
2. **📋 Clipboard Copy**: Data copied to Windows clipboard
3. **🎯 Window Focus**: Target window receives focus
4. **📤 Paste**: Ctrl+V keystroke sent to paste data

### Advantages
- ⚡ **Fastest Performance**: Near-instantaneous data delivery
- 🔗 **High Compatibility**: Works with most Windows applications
- 💪 **Reliable**: Less prone to timing issues
- 📊 **Batch Support**: Can handle large data efficiently

### Configuration
```xml
<Protocol>CLIPBOARDPASTE</Protocol>
<ClipboardPasteDelay>100</ClipboardPasteDelay>  <!-- Milliseconds before paste -->
<WindowFilter>Target Application</WindowFilter>   <!-- Application to receive data -->
```

### Best Practices
- **⏱️ Timing**: Use minimal delay (100-500ms) for best performance
- **🎯 Focus**: Ensure target application can receive focus
- **📋 Compatible**: Verify target app accepts clipboard paste operations
- **🔄 Testing**: Always test with your specific target application

### Troubleshooting
- **🚫 No Data Appears**: Check window filter matches exactly
- **⏱️ Data Cut Off**: Increase `ClipboardPasteDelay`
- **🔄 Timing Issues**: Verify target app has proper focus
- **📋 Paste Problems**: Ensure target app supports Ctrl+V

---

## ⌨️ Keyboard Injection Protocol

### How It Works
1. **🏷️ Tag Read**: FXP20 device reads RFID tag
2. **🔤 Character Split**: Data split into individual characters
3. **⌨️ Key Events**: Each character sent as keyboard input
4. **⏱️ Timing**: Delays between characters for compatibility

### Advantages
- **🎛️ Character Control**: Fine-grained control over each character
- **📊 Legacy Support**: Works with older applications
- **🔧 Customizable**: Configurable timing and behavior
- **📝 Special Characters**: Can send control characters (Tab, Enter)

### Configuration
```xml
<Protocol>KEYINJECTION</Protocol>
<KeyInjectionDelay>10</KeyInjectionDelay>       <!-- Milliseconds between characters -->
<WindowFilter>Target Application</WindowFilter>  <!-- Application to receive keystrokes -->
<AddCR>true</AddCR>                              <!-- Add carriage return -->
<AddLF>false</AddLF>                             <!-- Add line feed -->
```

### Character Formatting Options
```xml
<!-- Data formatting settings -->
<AddCSVSeparator>false</AddCSVSeparator>         <!-- Add comma separator -->
<CSVSeparator>,</CSVSeparator>                   <!-- Custom separator -->
<AddCR>true</AddCR>                              <!-- Carriage return (Enter) -->
<AddLF>false</AddLF>                             <!-- Line feed -->
<AddTab>false</AddTab>                           <!-- Tab character -->
```

### Best Practices
- **⏱️ Speed vs Compatibility**: Faster timing may cause missing characters
- **🧪 Testing**: Test thoroughly with target application
- **📝 Special Chars**: Use CR/LF settings appropriately
- **🎯 Focus**: Ensure target application maintains focus

### Troubleshooting
- **🔤 Missing Characters**: Increase `KeyInjectionDelay`
- **⏱️ Too Slow**: Reduce delay but test thoroughly
- **📝 Wrong Format**: Adjust CR/LF/Tab settings
- **🎯 Lost Focus**: Check window management

### Advanced Key Injection
```xml
<!-- Advanced keyboard settings -->
<SendModifierKeys>true</SendModifierKeys>        <!-- Enable Ctrl, Alt, Shift -->
<KeyPressTimeout>1000</KeyPressTimeout>          <!-- Max time per character -->
<RetryFailedKeys>3</RetryFailedKeys>             <!-- Retry count for failed keys -->
```

---

## 🌐 MQTT Protocol

### How It Works
1. **🏷️ Tag Read**: FXP20 device reads RFID tag
2. **📡 MQTT Publish**: Data published to configured topic
3. **🌐 Broker Distribution**: MQTT broker distributes to subscribers
4. **📥 Multiple Consumers**: Any number of applications can receive data

### Advantages
- **📈 Scalable**: Multiple applications can receive same data
- **🏢 Enterprise**: Professional messaging protocol
- **🔄 Reliable**: Built-in reliability and retry mechanisms
- **🌍 Network**: Works across networks and internet

### Configuration
```xml
<Protocol>MQTT</Protocol>
<MQTTServer>192.168.1.100</MQTTServer>           <!-- MQTT broker IP/hostname -->
<MQTTPort>1883</MQTTPort>                        <!-- MQTT broker port -->
<MQTTUser>username</MQTTUser>                    <!-- Authentication username -->
<MQTTPassword>password</MQTTPassword>            <!-- Authentication password -->
<MQTTSendTopic>fxp20/data</MQTTSendTopic>       <!-- Topic for tag data -->
<MQTTControlTopic>fxp20/control</MQTTControlTopic> <!-- Topic for control commands -->
```

### Message Format
Published messages contain:
```json
{
  "timestamp": "2025-09-11T10:30:45Z",
  "device_id": "FXP20_001",
  "epc": "E20000123456789012345678",
  "rssi": -45,
  "antenna": 1
}
```

### Best Practices
- **🔐 Security**: Use strong authentication credentials
- **🏷️ Topics**: Design logical topic hierarchy
- **⚡ QoS**: Choose appropriate Quality of Service level
- **📊 Monitoring**: Monitor broker and network performance

### Troubleshooting
- **🔌 Connection Failed**: Check broker IP, port, credentials
- **📡 No Messages**: Verify topic names match exactly
- **🔐 Auth Errors**: Confirm username/password
- **🌐 Network Issues**: Check firewall, network connectivity

---

## 🔄 Protocol Comparison

### Performance Comparison

| Aspect | Clipboard Paste | Keyboard Injection | MQTT |
|--------|-----------------|-------------------|------|
| **⚡ Speed** | Fastest (10-50ms) | Slowest (1-10s) | Fast (50-200ms) |
| **📊 Data Size** | Large data ✅ | Limited by timing | Large data ✅ |
| **🔄 Reliability** | High | Medium | High |
| **🎯 Target Apps** | Single | Single | Multiple |
| **🌐 Network** | Local only | Local only | Network capable |

### Use Case Selection Guide

#### Choose Clipboard Paste When:
- ✅ **Performance** is critical
- ✅ **Single application** target
- ✅ **Standard Windows app** compatibility needed
- ✅ **Simple setup** preferred

#### Choose Keyboard Injection When:
- ✅ **Legacy applications** that don't support clipboard
- ✅ **Character-by-character** control needed
- ✅ **Special formatting** requirements (tabs, enters)
- ✅ **Precise timing** control needed

#### Choose MQTT When:
- ✅ **Multiple applications** need the data
- ✅ **Enterprise integration** required
- ✅ **Network distribution** needed
- ✅ **Scalable architecture** planned

---

## ⚙️ Protocol-Specific Configuration

### Clipboard Paste Settings
```xml
<!-- Clipboard paste configuration -->
<Protocol>CLIPBOARDPASTE</Protocol>
<ClipboardPasteDelay>100</ClipboardPasteDelay>
<RestoreClipboard>true</RestoreClipboard>        <!-- Restore original clipboard -->
<ConfirmPaste>false</ConfirmPaste>               <!-- Disable paste confirmation -->
<MaxPasteLength>1000</MaxPasteLength>            <!-- Limit paste data length -->
```

### Keyboard Injection Settings
```xml
<!-- Keyboard injection configuration -->
<Protocol>KEYINJECTION</Protocol>
<KeyInjectionDelay>10</KeyInjectionDelay>
<CharacterTimeout>100</CharacterTimeout>         <!-- Timeout per character -->
<SkipNonPrintable>false</SkipNonPrintable>      <!-- Skip control characters -->
<ConvertToUpper>false</ConvertToUpper>           <!-- Convert to uppercase -->
<ConvertToLower>false</ConvertToLower>           <!-- Convert to lowercase -->
```

### MQTT Settings
```xml
<!-- MQTT configuration -->
<Protocol>MQTT</Protocol>
<MQTTServer>localhost</MQTTServer>
<MQTTPort>1883</MQTTPort>
<MQTTUser>admin</MQTTUser>
<MQTTPassword>password123</MQTTPassword>
<MQTTSendTopic>warehouse/reader1/tags</MQTTSendTopic>
<MQTTControlTopic>warehouse/reader1/control</MQTTControlTopic>
<MQTTKeepAlive>60</MQTTKeepAlive>               <!-- Keep-alive interval -->
<MQTTReconnect>true</MQTTReconnect>             <!-- Auto-reconnect -->
<MQTTRetain>false</MQTTRetain>                  <!-- Retain messages -->
<MQTTQOS>1</MQTTQOS>                            <!-- Quality of Service -->
```

---

## 🧪 Testing Protocols

### Testing Procedure

#### 1. Basic Function Test
- **⚙️ Configure** protocol settings
- **🏷️ Present** test tag
- **✅ Verify** data reaches destination
- **📊 Check** timing and formatting

#### 2. Performance Test  
- **🏷️ Read** multiple tags rapidly
- **📊 Monitor** data delivery rate
- **⏱️ Measure** latency
- **🔄 Check** for lost data

#### 3. Reliability Test
- **🔄 Run** extended test sessions
- **🔌 Simulate** connection issues
- **📊 Monitor** error rates
- **🔄 Test** recovery scenarios

### Debug Tools

#### Built-in Debug Features
- **📝 Text to Send**: Manually test data delivery
- **📋 Send Clipboard**: Test clipboard paste mechanism
- **⌨️ Send Key Events**: Test keyboard injection
- **📊 Status Indicators**: Monitor protocol status

#### External Testing Tools
```bash
# MQTT testing with mosquitto
mosquitto_sub -h localhost -p 1883 -u user -P password -t "fxp20/data"
mosquitto_pub -h localhost -p 1883 -u user -P password -t "fxp20/control" -m "Connect"

# Windows clipboard monitoring
clip < test.txt  # Put text in clipboard
```

---

## 🔧 Protocol Troubleshooting

### Common Issues Across All Protocols

#### Data Not Delivered
1. **🔍 Check** protocol configuration
2. **🎯 Verify** target application setup
3. **🏷️ Test** with known-good tag
4. **📊 Monitor** status indicators

#### Partial Data Loss
1. **⏱️ Adjust** timing settings
2. **📊 Check** data format settings
3. **🔄 Test** with shorter data
4. **📈 Monitor** system performance

#### Performance Issues
1. **⚙️ Optimize** protocol settings
2. **📊 Monitor** system resources
3. **🌐 Check** network (MQTT only)
4. **🔧 Consider** protocol switch

### Protocol-Specific Troubleshooting

#### Clipboard Paste Issues
- **❌ Paste doesn't work**: App doesn't support Ctrl+V
- **🕐 Timing problems**: Increase `ClipboardPasteDelay`
- **📋 Clipboard conflicts**: Other apps using clipboard
- **🎯 Focus issues**: Window not receiving focus

#### Keyboard Injection Issues
- **⌨️ Missing characters**: Increase `KeyInjectionDelay`
- **🔤 Wrong characters**: Check keyboard layout
- **📝 Format issues**: Adjust CR/LF settings
- **⏱️ Too slow**: Reduce delay, test thoroughly

#### MQTT Issues
- **🔌 Connection failed**: Check broker, network, credentials
- **📡 No messages**: Verify topic configuration
- **🐌 Slow delivery**: Check broker performance
- **🔐 Security errors**: Verify authentication

---

## 📚 Advanced Protocol Features

### Protocol Switching
```xml
<!-- Dynamic protocol switching -->
<AutoSelectProtocol>true</AutoSelectProtocol>
<ProtocolFallback>CLIPBOARDPASTE</ProtocolFallback>
<ProtocolRetries>3</ProtocolRetries>
```

### Data Transformation
```xml
<!-- Data formatting options -->
<DataPrefix>RFID:</DataPrefix>                   <!-- Add prefix to data -->
<DataSuffix>\n</DataSuffix>                     <!-- Add suffix to data -->
<DataTransform>UPPERCASE</DataTransform>         <!-- Transform case -->
<RemoveSpaces>true</RemoveSpaces>               <!-- Remove whitespace -->
<ReplaceChars>true</ReplaceChars>               <!-- Character replacement -->
```

### Error Handling
```xml
<!-- Protocol error handling -->
<RetryOnError>true</RetryOnError>
<MaxRetries>3</MaxRetries>
<RetryDelay>1000</RetryDelay>
<FailoverProtocol>CLIPBOARDPASTE</FailoverProtocol>
<LogErrors>true</LogErrors>
```

---

## 📞 Related Resources

- **[MQTT Integration Guide](MQTT.md)** - Detailed MQTT setup
- **[Configuration Guide](Configuration.md)** - Complete Config.xml reference
- **[User Interface Guide](User-Interface.md)** - GUI protocol selection
- **[Troubleshooting Guide](Troubleshooting.md)** - Protocol-specific solutions

---

*Need help choosing or configuring protocols? Check the [Configuration Guide](Configuration.md) or return to [Home](Home.md).*