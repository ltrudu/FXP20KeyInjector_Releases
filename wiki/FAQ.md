# ❓ Frequently Asked Questions

Common questions and answers about FXP20 Key Injector installation, configuration, and usage.

---

## 🚀 Getting Started

### Q: What is FXP20 Key Injector?
**A:** FXP20 Key Injector is a Windows application that integrates Zebra FXP20 handheld RFID readers with desktop applications. It reads RFID tags and automatically inputs the data into any Windows application through keyboard injection, clipboard paste, or MQTT messaging.

### Q: What devices are supported?
**A:** Currently supports:
- ✅ **Zebra FXP20 RFID Readers** (all variants)
- ❌ **Other RFID readers** are not supported

### Q: What operating systems are supported?
**A:** 
- ✅ **Windows 10** (Version 1903 or later)
- ✅ **Windows 11** (all versions)
- ✅ **Windows Server 2019/2022**
- ❌ **Windows 7/8** (lacks .NET 4.8 support)
- ❌ **macOS/Linux** (Windows only)

---

## 📥 Installation Questions

### Q: Do I need administrator rights?
**A:** Administrator rights are recommended for:
- Installing the application
- Accessing COM ports
- Running for the first time
- Setting up auto-startup

### Q: What prerequisites are required?
**A:** 
- **📱 Zebra FXP20 device**
- **💻 Windows 10/11**
- **⚡ .NET Framework 4.8 or higher**
- **🔌 USB cable** for device connection

### Q: Where should I install the application?
**A:** Recommended locations:
- **System-wide**: `C:\Program Files\FXP20KeyInjector\`
- **User-specific**: `C:\Users\[Username]\AppData\Local\FXP20KeyInjector\`
- **Portable**: Any folder with write permissions

### Q: Can I run multiple instances?
**A:** No, only one instance can connect to an FXP20 device at a time due to COM port exclusivity.

---

## 🔌 Connection Issues

### Q: My FXP20 device is not detected. What should I do?
**A:** Try these steps in order:
1. **🔌 Check** USB cable connection
2. **👤 Run** application as Administrator
3. **🔄 Click** "Refresh Values" button
4. **🖥️ Check** Device Manager for COM ports
5. **🔄 Try** a different USB port
6. **🔄 Restart** the application

### Q: The device connects but disconnects immediately. Why?
**A:** Common causes:
- **🔋 Low battery** on FXP20 device
- **⚡ Insufficient USB power** (try powered hub)
- **🔌 Poor cable quality** (try different cable)
- **⚙️ COM port conflicts** (close other applications using the port)

### Q: Can I use Bluetooth or Wi-Fi instead of USB?
**A:** No, FXP20 Key Injector requires a USB connection to the FXP20 device.

---

## 📊 Data Delivery Questions

### Q: Which protocol should I use?
**A:** Protocol recommendations:
- **📋 CLIPBOARDPASTE**: Best for most applications (recommended)
- **⌨️ KEYINJECTION**: For legacy applications or special formatting needs
- **🌐 MQTT**: For enterprise integration or multiple target applications

### Q: Tags are being read but no data appears in my application. Why?
**A:** Check these items:
1. **🎯 Window Filter**: Verify correct target window is selected
2. **👁️ Application Focus**: Ensure target application is active
3. **📋 Protocol**: Try switching between CLIPBOARDPASTE and KEYINJECTION
4. **🧪 Test**: Use the debug tools to send test data

### Q: The same tag is being read multiple times. How do I fix this?
**A:** Enable duplicate filtering:
```xml
<RemoveDuplicates>true</RemoveDuplicates>
<HookGPIOToStartReading>true</HookGPIOToStartReading>
<GPIOReadingDurationInMs>5000</GPIOReadingDurationInMs>
```

### Q: Can I customize the data format?
**A:** Yes, you can customize:
- **📝 Prefixes/Suffixes**: Add text before/after tag data
- **🔤 Case Conversion**: Convert to uppercase/lowercase
- **📋 Separators**: Add commas, tabs, or custom separators
- **⏭️ Line Endings**: Add carriage returns or line feeds

---

## ⚙️ Configuration Questions

### Q: Where is the configuration stored?
**A:** Configuration is stored in `Config.xml` in the same directory as the application executable.

### Q: Can I backup my configuration?
**A:** Yes, simply copy the `Config.xml` file to a backup location. Restore by copying it back.

### Q: How do I reset to default settings?
**A:** Delete the `Config.xml` file. The application will create a new one with default settings on next startup.

### Q: Can I share configuration between computers?
**A:** Yes, copy the `Config.xml` file, but you may need to adjust:
- COM port settings (device-specific)
- File paths (system-specific)  
- MQTT server addresses (network-specific)

---

## 🎛️ GPIO and Hardware

### Q: What are GPIO buttons used for?
**A:** GPIO buttons allow hands-free operation:
- **▶️ Start Reading**: Begin tag reading session
- **⏹️ Stop Reading**: End reading session
- **⏱️ Timed Sessions**: Read for a specified duration
- **🔄 Duplicate Filtering**: Remove duplicate tags during session

### Q: Which button triggers GPIO?
**A:** This depends on your FXP20 model. Common GPIO buttons:
- **🔴 Primary trigger button** (most common)
- **🟡 Side buttons** (model-dependent)
- **📱 Volume buttons** (if mapped)

Test different buttons to identify which triggers GPIO events.

### Q: How long should GPIO reading sessions be?
**A:** Recommended durations:
- **2-3 seconds**: Single tag reading
- **5-8 seconds**: Small batch (2-10 tags)
- **10-15 seconds**: Medium batch (10-50 tags)
- **15-30 seconds**: Large batch (50+ tags)

---

## 🌐 MQTT Questions

### Q: Do I need an MQTT broker?
**A:** Yes, MQTT protocol requires a broker. Options include:
- **🦟 Mosquitto** (recommended for local/testing)
- **☁️ Cloud services** (AWS IoT, Azure IoT Hub, HiveMQ)
- **🏢 Enterprise brokers** (existing corporate infrastructure)

### Q: What MQTT topics should I use?
**A:** Recommended topic structure:
- **📤 Data**: `fxp20/data` or `warehouse/reader1/tags`
- **📥 Control**: `fxp20/control` or `warehouse/reader1/commands`
- **📊 Status**: `fxp20/status` or `warehouse/reader1/status`

### Q: Can multiple applications receive the same tag data?
**A:** Yes, that's a key advantage of MQTT. Any number of applications can subscribe to the data topic and receive tag readings.

---

## ⚡ Performance Questions

### Q: How many tags per second can it process?
**A:** Performance varies by protocol:
- **📋 CLIPBOARDPASTE**: 10-50 tags/second
- **⌨️ KEYINJECTION**: 1-10 tags/second (depending on delay settings)
- **🌐 MQTT**: 20-100 tags/second (depending on broker)

### Q: Why is keyboard injection slow?
**A:** Keyboard injection sends each character individually with timing delays to ensure compatibility. To improve speed:
- **⏱️ Reduce** `KeyInjectionDelay` (test thoroughly)
- **📋 Switch** to CLIPBOARDPASTE protocol
- **🔧 Optimize** target application for faster input

### Q: The application uses a lot of memory. Is this normal?
**A:** Memory usage grows with tag history. To optimize:
- **🧹 Clear** EPC Sent list regularly
- **🔢 Disable** "Show EPC Sent" for high-volume operations
- **🔄 Restart** application periodically during extended use

---

## 🔧 Troubleshooting

### Q: The application won't start. What should I do?
**A:** Try these steps:
1. **⚡ Install** .NET Framework 4.8
2. **👤 Run** as Administrator
3. **🛡️ Disable** antivirus temporarily
4. **📂 Check** installation folder permissions
5. **📝 Delete** Config.xml file if present

### Q: I get a "COM port access denied" error. How do I fix it?
**A:** Common solutions:
- **👤 Run** as Administrator
- **🚫 Close** other applications using the COM port
- **🔄 Restart** the application
- **🖥️ Check** Device Manager for COM port conflicts

### Q: Tags are not being read reliably. What can I do?
**A:** Try these optimizations:
- **⚡ Increase** transmit power
- **⏱️ Extend** inventory duration
- **🔄 Increase** retry count
- **📊 Check** for RF interference
- **🏷️ Test** with known-good tags

---

## 🚀 Advanced Usage

### Q: Can I automate the application to start with Windows?
**A:** Yes, see the [Auto-Startup Guide](Auto-Startup.md) for complete instructions on:
- **🪟 Startup folder** method
- **📋 Registry** entries
- **⏰ Task Scheduler** setup
- **🔧 Windows Service** installation

### Q: Can I integrate with my existing software?
**A:** Yes, through several methods:
- **📋 Direct Input**: Use CLIPBOARDPASTE or KEYINJECTION to send data directly
- **🌐 MQTT**: Use MQTT for programmatic integration
- **📄 File Output**: Configure to write data to files
- **🔗 Database**: Use MQTT bridge to send data to databases

### Q: How do I customize the antenna power?
**A:** Configure transmit power in Config.xml:
```xml
<TransmitPower>20</TransmitPower>  <!-- Range: 0-30 -->
```
See [Power Index Reference](Power-Index.md) for detailed power level guidance.

---

## 🔐 Security Questions

### Q: Are passwords stored securely?
**A:** Currently, MQTT passwords are stored in plain text in Config.xml. Recommendations:
- **📁 Secure** the Config.xml file with file system permissions
- **🔐 Use** strong, unique passwords
- **🔄 Change** passwords regularly
- **🏢 Consider** enterprise security solutions for production

### Q: Can the application run in a restricted environment?
**A:** The application requires:
- **📝 File write** permissions (for Config.xml)
- **🔌 COM port** access
- **🌐 Network** access (for MQTT mode only)
- **📋 Clipboard** access (for CLIPBOARDPASTE protocol)

### Q: Is the application safe to use?
**A:** Yes, the application is safe:
- **🚫 No network** communication (except MQTT mode)
- **📂 Local data** processing only
- **🔒 No data collection** or telemetry
- **📄 Open source** documentation and configuration

---

## 📞 Support Questions

### Q: How do I get support?
**A:** Support options:
1. **📚 Check** this FAQ and documentation
2. **🔍 Search** [existing issues](https://github.com/ltrudu/FXP20KeyInjector_Releases/issues)
3. **🆕 Create** [new issue](https://github.com/ltrudu/FXP20KeyInjector_Releases/issues/new) with details

### Q: Is commercial support available?
**A:** This is a community project without official commercial support. For Zebra hardware support, contact Zebra Technologies directly.

### Q: Can I contribute to the project?
**A:** Yes! You can contribute by:
- **🐛 Reporting** bugs and issues
- **💡 Suggesting** features and improvements
- **📖 Improving** documentation
- **🧪 Testing** and providing feedback

### Q: Where can I find the latest version?
**A:** Download the latest version from the [Releases page](https://github.com/ltrudu/FXP20KeyInjector_Releases/releases).

---

## ❗ Error Messages

### Q: "Failed to connect to device" - What does this mean?
**A:** The application cannot establish communication with your FXP20. Check:
- **🔌 USB connection** is secure
- **🖥️ Device Manager** shows COM port
- **👤 Administrator rights** are granted
- **🚫 No other applications** are using the COM port

### Q: "MQTT connection failed" - How do I fix this?
**A:** MQTT connection issues are usually:
- **🌐 Incorrect** broker IP address or port
- **🔐 Wrong** username or password
- **🔥 Firewall** blocking port 1883
- **📡 Network** connectivity problems

### Q: "Window not found" - What should I do?
**A:** The target application window cannot be found:
- **🔄 Refresh** the window list
- **👁️ Ensure** target application is running and visible
- **📝 Check** window title matches exactly
- **🧪 Test** with a simple application like Notepad

---

## 💡 Tips and Best Practices

### Q: What are some general usage tips?
**A:** Best practices for optimal performance:
- **👤 Always run** as Administrator for best compatibility
- **💾 Save configuration** after making changes
- **🧪 Test thoroughly** before deploying in production
- **📊 Monitor** performance during high-volume operations
- **🔄 Keep backups** of working configurations

### Q: How can I optimize for my specific use case?
**A:** Consider these factors:
- **📊 Tag volume**: High volume → CLIPBOARDPASTE, MQTT
- **🔋 Battery life**: Lower power settings, shorter sessions
- **🎯 Precision needs**: Lower power, shorter ranges
- **🏢 Enterprise needs**: MQTT with proper broker infrastructure
- **📱 Mobile use**: GPIO buttons, battery optimization

---

*Still have questions? Check our [Support Guide](Support.md) or search [existing issues](https://github.com/ltrudu/FXP20KeyInjector_Releases/issues). Return to [Home](Home.md) for more documentation.*