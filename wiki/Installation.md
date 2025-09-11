# 🚀 Installation Guide

This guide will walk you through installing and setting up FXP20 Key Injector on your Windows system.

---

## 📋 Prerequisites

### Hardware Requirements
- 📱 **Zebra FX-series handheld device** (FX7500, FX9600, etc.)
- 💻 **Windows PC** with USB 2.0+ ports
- 🔌 **USB cable** or network connection to connect the FX device

### Software Requirements
- 🖥️ **Operating System**: Windows 10, Windows 11, or Windows Server
- ⚡ **.NET Framework 4.8 or higher** - [Download here](https://dotnet.microsoft.com/en-us/download/dotnet-framework/net48)
- 🌐 **MQTT Broker** (optional) - Only required for MQTT mode

---

## 📥 Download and Installation

### Step 1: Download the Application
1. Go to the [Releases page](https://github.com/ltrudu/FXP20KeyInjector_Releases/releases)
2. Download the latest `FXP20KeyInjector.7z` file

### Step 2: Install .NET Framework
If you don't have .NET Framework 4.8 installed:
1. Download from [Microsoft's official site](https://dotnet.microsoft.com/en-us/download/dotnet-framework/net48)
2. Run the installer as Administrator
3. Restart your computer if prompted

### Step 3: Extract the Application
1. Extract the `FXP20KeyInjector.7z` file to your desired location
   - **Recommended**: `C:\Program Files\FXP20KeyInjector`
   - **Alternative**: Any folder with write permissions

### Step 4: First Launch
1. Right-click on `FXP20KeyInjector.exe`
2. Select **"Run as Administrator"** (recommended for first run)
3. The application will create a default `Config.xml` file

---

## 🔌 Hardware Setup

### Connect Your Zebra Device
1. **USB Connection** (Recommended):
   - Connect your FX device to the PC via USB cable
   - Wait for Windows to install device drivers
   - The device should appear as a COM port

2. **Network Connection**:
   - Ensure both PC and FX device are on the same network
   - Configure the device's IP address in the application

### Verify Connection
1. Launch FXP20KeyInjector
2. Click **"Refresh Values"** to scan for connected devices
3. Your device should appear in the **COM Port** dropdown

---

## ⚙️ Basic Configuration

### First-Time Setup Wizard
When you first launch the application:

1. **Select COM Port**: Choose your FX device from the dropdown
2. **Test Connection**: Click **"Connect"** to verify communication
3. **Configure Target Window**: Set which application will receive tag data
4. **Choose Send Protocol**:
   - **CLIPBOARDPASTE**: Best performance (recommended)
   - **KEYINJECTION**: Character-by-character input
   - **MQTT**: For enterprise integration

---

## 🌐 Optional: MQTT Broker Setup

If you plan to use MQTT mode, you'll need a broker:

### Option 1: Mosquitto (Recommended)
1. Download [Mosquitto MQTT](https://mosquitto.org/download/)
2. Install with default settings
3. Add Mosquitto to your system PATH
4. See [Mosquitto Setup Guide](Mosquitto-Setup) for detailed configuration

### Option 2: Cloud MQTT Services
- AWS IoT Core
- Azure IoT Hub
- HiveMQ Cloud

---

## ✅ Verify Installation

### Quick Test
1. Open **Notepad** or any text editor
2. In FXP20KeyInjector:
   - Select Notepad in the Window Filter
   - Choose **CLIPBOARDPASTE** protocol
   - Click **Connect** to your device
   - Click **Start Reading**
3. Present an RFID tag to your FX device
4. The tag data should appear in Notepad

### Troubleshooting Installation Issues

#### COM Port Not Found
- **Check USB cable connection**
- **Install Zebra device drivers**
- **Try a different USB port**
- **Restart the application**

#### Permission Errors
- **Run as Administrator**
- **Check antivirus software** (may block the application)
- **Verify write permissions** in installation folder

#### .NET Framework Errors
- **Download and install .NET Framework 4.8**
- **Restart your computer**
- **Run Windows Update**

---

## 🚀 Next Steps

After successful installation:

1. 📖 **[Read the User Interface Guide](User-Interface)** to understand all features
2. ⚙️ **[Configure Advanced Settings](Configuration)** for your specific needs
3. 🎯 **[Set up Auto-Startup](Auto-Startup)** for production use
4. 🌐 **[Explore MQTT Integration](MQTT)** for enterprise scenarios

---

## 📞 Getting Help

If you encounter issues during installation:

1. 🔍 **Check [Troubleshooting Guide](Troubleshooting)**
2. 📋 **Search [Existing Issues](https://github.com/ltrudu/FXP20KeyInjector_Releases/issues)**
3. 🆕 **[Create New Issue](https://github.com/ltrudu/FXP20KeyInjector_Releases/issues/new)** with:
   - Your Windows version
   - .NET Framework version
   - FX device model
   - Error messages or screenshots

---

*Need help? Check our [Support Guide](Support) or visit the [main documentation](Home).*