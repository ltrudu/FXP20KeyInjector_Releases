# 🚀 Quick Start Guide

Get FXP20 Key Injector up and running in minutes with this streamlined setup guide.

---

## ⏱️ 5-Minute Setup

### Step 1: Prerequisites Check (30 seconds)
- ✅ Zebra FXP20 device available
- ✅ Windows 10/11 PC
- ✅ USB cable for connection
- ✅ .NET Framework 4.8+ installed

### Step 2: Download & Extract (1 minute)
1. **📥 Download** latest `FXP20KeyInjector.7z` from [Releases](https://github.com/ltrudu/FXP20KeyInjector_Releases/releases)
2. **📂 Extract** to desired location (e.g., `C:\Program Files\FXP20KeyInjector`)

### Step 3: Connect Device (1 minute)
1. **🔌 Connect** FXP20 to PC via USB
2. **⏳ Wait** for Windows to install drivers
3. **✅ Verify** device appears in Device Manager

### Step 4: Launch Application (30 seconds)
1. **▶️ Run** `FXP20KeyInjector.exe` as Administrator
2. **⚙️ Allow** Windows security prompts

### Step 5: Basic Configuration (2 minutes)
1. **🔄 Click** "Refresh Values" button
2. **📡 Select** your FXP20 COM port from dropdown
3. **🔗 Click** "Connect" button
4. **✅ Verify** connection status shows "Connected"

---

## 🧪 Quick Test

### Test with Notepad
1. **📝 Open** Notepad
2. **🎯 Select** "Notepad" in Window Filter dropdown
3. **📋 Choose** "CLIPBOARDPASTE" protocol (recommended)
4. **▶️ Click** "Start Reading"
5. **🏷️ Present** RFID tag to FXP20 device
6. **✅ Verify** tag data appears in Notepad

### Expected Results
- **🟢 Connection Status**: Shows "Connected"
- **📊 Last EPC Read**: Displays tag data
- **🔢 Tags Read**: Counter increments
- **📤 EPC Sent**: Counter increments
- **📝 Target App**: Receives tag data

---

## ⚙️ Essential Settings

### Recommended Initial Configuration
```xml
<!-- Optimal settings for most users -->
<Protocol>CLIPBOARDPASTE</Protocol>
<AutoConnect>true</AutoConnect>
<AutoStartReading>true</AutoStartReading>
<RemoveDuplicates>true</RemoveDuplicates>
```

### Protocol Selection Guide
- **📋 CLIPBOARDPASTE**: Best performance, most compatible
- **⌨️ KEYINJECTION**: Character-by-character input
- **🌐 MQTT**: Enterprise messaging (requires broker)

---

## 🎯 Common First-Time Tasks

### 1. Set Target Application
1. **🖥️ Open** your target application
2. **🔄 Click** "Refresh Values" in FXP20KeyInjector
3. **🎯 Select** application from Window Filter dropdown
4. **💾 Click** "Save Config" to remember setting

### 2. Configure Auto-Start
```xml
<!-- Add to Config.xml for automatic startup -->
<AutoConnect>true</AutoConnect>
<AutoStartReading>true</AutoStartReading>
<StartWithWindows>true</StartWithWindows>
```

### 3. Test Tag Reading
1. **▶️ Start** reading mode
2. **🏷️ Present** tag to device
3. **👁️ Watch** for data in target application
4. **🔧 Adjust** settings if needed

---

## 🔧 Troubleshooting Quick Fixes

### Device Not Found
- **🔌 Check** USB connection
- **🔄 Try** different USB port
- **👤 Run** as Administrator
- **🔄 Restart** application

### No Data in Target App
- **🎯 Verify** correct window selected
- **📋 Try** CLIPBOARDPASTE protocol
- **👁️ Ensure** target app has focus
- **🧪 Test** with Notepad first

### Connection Fails
- **🚫 Close** other COM port applications
- **⚙️ Try** different baud rate
- **🔄 Restart** device and application
- **👤 Run** as Administrator

---

## 📚 Next Steps

Once you have the basic setup working:

1. **📖 [Explore User Interface](User-Interface.md)** - Learn all features
2. **⚙️ [Advanced Configuration](Configuration.md)** - Customize settings
3. **🌐 [MQTT Setup](MQTT.md)** - Enterprise integration
4. **🔧 [Troubleshooting](Troubleshooting.md)** - Detailed problem solving

---

## 💡 Pro Tips

### Performance Optimization
- **📋 Use CLIPBOARDPASTE** for fastest data transfer
- **🔄 Enable duplicate filtering** to reduce noise
- **⏱️ Adjust timing** for your target application

### Reliability Tips
- **👤 Always run as Administrator** for best compatibility
- **💾 Save configuration** after making changes
- **🔄 Use Auto-Connect** for consistent startup

### Production Setup
- **📁 Install in Program Files** for system-wide access
- **🚀 Configure auto-startup** for hands-free operation
- **📊 Monitor connection status** regularly

---

## 🆘 Need Help?

- **📋 [Full Installation Guide](Installation.md)** - Detailed setup instructions
- **🔧 [Troubleshooting Guide](Troubleshooting.md)** - Problem solutions
- **💬 [Create Issue](https://github.com/ltrudu/FXP20KeyInjector_Releases/issues/new)** - Get community help

---

*Got FXP20 Key Injector running? Great! Check out the [User Interface Guide](User-Interface.md) to explore all features or return to [Home](Home.md).*