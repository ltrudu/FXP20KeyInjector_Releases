# 🏷️ FXP20 Key Injector

[![License](https://img.shields.io/badge/License-Zebra%20EULA-blue)](https://github.com/ltrudu/FXP20KeyInjector_Releases/blob/master/EULA.txt)
[![Platform](https://img.shields.io/badge/Platform-Windows-blue)]()
[![Hardware](https://img.shields.io/badge/Hardware-Zebra%20FX%20Series-green)]()

> **📋 Community Project Notice**  
> *This tool is provided as a community project without any guarantee of support. It is not officially supported by Zebra. For issues, please use the Issues tab of this repository.*

---

## 🎯 What is FXP20 Key Injector?

**FXP20 Key Injector** is a powerful Windows application that transforms your Zebra FX-series handheld devices into efficient RFID/NFC tag readers. The application automatically reads tags and injects the data directly into your active applications as keyboard input, making data collection seamless and efficient.

### ✨ Key Features

- 🔄 **Automatic Tag Reading**: Continuously reads RFID/NFC tags from connected Zebra devices
- ⌨️ **Multiple Input Methods**: Keyboard injection, clipboard paste, and MQTT messaging
- 🚀 **Auto-Startup Support**: Configure the application to start automatically with Windows  
- 🔗 **Auto-Connect**: Automatically connect to your RFID reader on startup
- 🎛️ **GPIO Integration**: Use hardware buttons to trigger tag reading sessions
- 🔧 **Advanced Configuration**: Customize reading duration, duplicate filtering, and more
- 🎯 **Duplicate Filtering**: Remove duplicate tag reads during reading sessions
- 📊 **Real-time Feedback**: Visual indicators for connection status and tag reading activity
- 🌐 **MQTT Support**: Professional messaging protocol for complex integrations

---

## 📖 Documentation

### 📚 Main Documentation
- **[📋 Complete Documentation Wiki](https://github.com/ltrudu/FXP20KeyInjector_Releases/blob/master/wiki/Home.md)** - Comprehensive user guide and reference
- **[📄 Detailed DocX Manual with Interactive Links](https://github.com/ltrudu/FXP20KeyInjector_Releases/blob/master/FXP20KeyInjector-HowTo.docx?raw=true)** - **[📄 Detailed PDF Manual](https://github.com/ltrudu/FXP20KeyInjector_Releases/blob/master/FXP20KeyInjector-HowTo.pdf)** - Complete technical documentation

### Quick Links

- 🚀 **[Installation Guide](https://github.com/ltrudu/FXP20KeyInjector_Releases/wiki/Installation.md)**
- ⚙️ **[Configuration Guide](https://github.com/ltrudu/FXP20KeyInjector_Releases/wiki/Configuration.md)**
- 🖥️ **[User Interface Guide](https://github.com/ltrudu/FXP20KeyInjector_Releases/wiki/User-Interface.md)**
- 🛠️ **[Setup & Connection](https://github.com/ltrudu/FXP20KeyInjector_Releases/wiki/Setup.md)**
- 🌐 **[MQTT Integration](https://github.com/ltrudu/FXP20KeyInjector_Releases/wiki/MQTT.md)**
- 🔧 **[Troubleshooting](https://github.com/ltrudu/FXP20KeyInjector_Releases/wiki/Troubleshooting.md)**

---

## 🛠️ Quick Installation

### Prerequisites
- 📱 Zebra FXP20 Reader
- 💻 Windows 10/11
- 🔗 USB connection to the FXP20 Reader
- ⚡ .NET Framework 4.8+

### Installation Steps
1. **Download** the latest FXP20KeyInjector.7z from releases
2. **Extract** to your desired location  
3. **Run** FXP20KeyInjector.exe
4. **Configure** your device connection
5. **Start** reading tags!

---

## 🔧 Core Functionality

### Keyboard Wedge Mode
The application acts as a keyboard wedge, automatically typing RFID tag data into any active Windows application. Perfect for:
- 📝 Form filling
- 📦 Inventory management systems

### MQTT Mode  
Professional messaging protocol support for enterprise integration:
- 🔗 Connect to MQTT brokers
- 📡 Send tag data to multiple applications
- 🎛️ Remote control capabilities
- 🏢 Enterprise system integration

### GPIO Control
Use physical hardware buttons on your Zebra device:
- ▶️ Start/stop reading with button press
- ⏱️ Configurable reading durations
- 🔄 Hands-free operation

---

## 📜 License & Legal

This software is licensed under the **Zebra End User License Agreement (EULA)**.

📄 **[Read the Complete EULA](https://github.com/ltrudu/FXP20KeyInjector_Releases/blob/master/EULA.txt)**

### Important Notes
- ⚠️ **Community project** - no official Zebra support
- 🔒 Software is **licensed, not sold**
- 🏢 For **Zebra hardware use only**
- 📋 **Must accept EULA before use**

---

## 📈 Recent Updates

### 🆕 Latest Version (September 9, 2025)
- ➕ **Auto-startup configuration** - Start with Windows
- 🔗 **Enhanced auto-connect** - Seamless device connection
- 🎯 **Auto-start reading** - Begin scanning immediately after connection
- 📚 **Comprehensive documentation** updates

### 🔧 Previous Updates (September 8, 2025)
- ✨ **NEW**: `RemoveDuplicates` feature in Config.xml
- 🔄 Enhanced duplicate filtering during GPIO and keyboard-triggered reading
- ⏱️ Improved reading session management
- 🎛️ Better hardware GPIO integration

---

## 🤝 Support & Contributing

### Getting Help
1. 📖 Check the [Wiki](https://github.com/ltrudu/FXP20KeyInjector_Releases/blob/master/wiki/Home.md)
2. 🔍 Search existing [Issues](https://github.com/ltrudu/FXP20KeyInjector_Releases/issues)
3. 🆕 Create a new issue with detailed information

### Contributing
- 🐛 **Report bugs** via GitHub Issues
- 💡 **Suggest features** and improvements
- 📖 **Help improve documentation**
- ⭐ **Star the repository** to show support

---

## ⚡ Quick Start

1. **📥 Download** and extract the application
2. **🔌 Connect** your Zebra FX device
3. **▶️ Run** FXP20KeyInjector.exe
4. **⚙️ Configure** connection settings via GUI
5. **📋 Open** your target application
6. **🏷️ Start scanning** - tag data appears automatically!

---

*📞 For Zebra hardware support, contact Zebra Technologies directly. For application issues, use this repository's Issues section.*
