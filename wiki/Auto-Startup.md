# 🚀 Auto-Startup Configuration Guide

Configure FXP20 Key Injector to start automatically with Windows and begin reading tags immediately.

---

## 🎯 Auto-Startup Overview

Auto-startup enables FXP20 Key Injector to:
- **🚀 Start with Windows** - Launch automatically at boot
- **🔗 Auto-Connect** - Connect to FXP20 device automatically  
- **▶️ Auto-Start Reading** - Begin tag reading without user intervention
- **🎯 Target Application** - Focus on specified application window

This is essential for production environments where the system should be ready immediately after startup.

---

## ⚙️ Configuration Options

### Method 1: GUI Configuration (Recommended)

#### Basic Auto-Startup Setup
1. **▶️ Launch** FXP20KeyInjector.exe
2. **⚙️ Configure** your normal settings (COM port, protocol, target window)
3. **✅ Test** that everything works manually first
4. **💾 Click** "Save Config" to store settings

#### Enable Auto-Features
Configure these settings in the application:
- **🔗 Auto-Connect**: Enable automatic device connection
- **▶️ Auto-Start Reading**: Begin reading immediately after connection
- **🎯 Window Filter**: Set target application for data delivery

### Method 2: Config.xml Configuration

Add these settings to your `Config.xml` file:

```xml
<?xml version="1.0" encoding="utf-8"?>
<Configuration>
  <!-- Auto-Startup Settings -->
  <AutoConnect>true</AutoConnect>
  <AutoStartReading>true</AutoStartReading>
  
  <!-- Connection Settings -->
  <ComPort>COM5</ComPort>
  <BaudRate>921600</BaudRate>
  
  <!-- Target Application -->
  <TargetWindowFilter>Your Target Application</TargetWindowFilter>
  <Protocol>CLIPBOARDPASTE</Protocol>
  
  <!-- Optional: Start minimized -->
  <StartMinimized>true</StartMinimized>
</Configuration>
```

---

## 🪟 Windows Startup Integration

### Option 1: Windows Startup Folder (Simple)

#### Add to User Startup
1. **⌨️ Press** Windows + R
2. **📝 Type** `shell:startup` and press Enter
3. **📂 Create a shortcut to** FXP20KeyInjector.exe in this folder
4. **🔄 Restart** Windows to test

#### Add to System Startup (All Users)
1. **⌨️ Press** Windows + R  
2. **📝 Type** `shell:common startup` and press Enter
3. **👤 Run** as Administrator if prompted
4. **📂 Create a shortcut to** FXP20KeyInjector.exe in this folder

### Option 2: Task Scheduler (Most Reliable)

#### Create Scheduled Task
1. **🔍 Open** Task Scheduler (`taskschd.msc`)
2. **➕ Click** "Create Basic Task"
3. **📝 Name**: "FXP20 Key Injector Startup"
4. **🎯 Trigger**: "When the computer starts"
5. **⚡ Action**: "Start a program"
6. **📂 Program**: Browse to FXP20KeyInjector.exe
7. **⚙️ Settings**: 
   - ✅ "Run with highest privileges"
   - ✅ "Run whether user is logged on or not"
   - ✅ "Wake the computer to run this task"

#### Advanced Task Settings
```xml
<!-- Task Scheduler XML configuration -->
<WorkingDirectory>C:\Program Files\FXP20KeyInjector</WorkingDirectory>
<Priority>4</Priority>
<RunLevel>HighestAvailable</RunLevel>
<RestartCount>3</RestartCount>
<RestartInterval>PT10M</RestartInterval>
```

---

## ⚙️ Auto-Startup Configuration Reference

### Essential Config.xml Settings

#### Connection Automation
```xml
<!-- Automatic connection settings -->
<AutoConnect>true</AutoConnect>
<ComPort>COM5</ComPort>                     <!-- Specify exact COM port -->
<BaudRate>921600</BaudRate>
```

#### Reading Automation
```xml
<!-- Automatic reading settings -->
<AutoStartReading>true</AutoStartReading>
```

#### Application Integration
```xml
<!-- Target application settings -->
<TargetWindowFilter>Inventory Management System</TargetWindowFilter>
<Protocol>CLIPBOARDPASTE</Protocol>        <!-- Fastest data delivery -->
<ClipboardPasteDelay>500</ClipboardPasteDelay>
```

#### User Interface Settings
```xml
<!-- UI behavior for automatic startup -->
<StartMinimized>true</StartMinimized>       <!-- Start minimized -->
```

#### GPIO and Hardware Settings
```xml
<!-- Hardware trigger settings -->
<PerformReadingWithGPIO>true</PerformReadingWithGPIO>
<PerformReadingDuration>5000</PerformReadingDuration>
<PerformReadingGPIOPort>1</PerformReadingGPIOPort>
<BeepOnRead>true</BeepOnRead>
<nbBeeps>1</nbBeeps>
<beepSleepTime>400</beepSleepTime>
```

---

## 🧪 Testing Auto-Startup

### Pre-Production Testing

#### Test Sequence
1. **⚙️ Configure** all settings manually first
2. **✅ Verify** everything works in manual mode
3. **💾 Save** configuration
4. **🔄 Close** application
5. **▶️ Test** auto-startup method
6. **📊 Monitor** startup behavior
7. **🏷️ Test** tag reading functionality

#### Validation Checklist
- [ ] ✅ Application starts automatically
- [ ] 🔗 Device connects automatically
- [ ] ▶️ Reading starts automatically
- [ ] 🎯 Data reaches target application
- [ ] 📊 No error messages appear
- [ ] 🔄 System recovers from device disconnection
- [ ] 👤 Works without user logged in (if using service)

### Debugging Auto-Startup Issues

#### Common Problems
- **⏱️ Timing Issues**: Device not ready when app starts
- **👤 Permission Issues**: Insufficient rights for COM port access
- **🎯 Window Focus**: Target application not ready
- **🔌 Hardware Issues**: Device not connected at startup

#### Debugging Tools
```batch
:: Check startup programs
wmic startup get caption,command,location,user

:: Check event logs
eventvwr.msc
```

---

## 🔧 Production Deployment

### Enterprise Deployment Checklist

#### Pre-Deployment
- [ ] 📋 Test on identical hardware configuration
- [ ] 🔧 Validate all configuration settings
- [ ] 👤 Confirm user permissions
- [ ] 📊 Test recovery scenarios
- [ ] 📝 Document configuration for support

#### Deployment Steps
1. **📂 Install** application to standard location
2. **⚙️ Configure** Config.xml with production settings
3. **🚀 Set up** chosen startup method
4. **🧪 Test** complete startup sequence
5. **📊 Monitor** initial operation
6. **📝 Document** configuration and support procedures

#### Post-Deployment Monitoring
- **📊 System Performance**: Monitor CPU, memory usage
- **🔗 Connection Stability**: Track disconnection events
- **📈 Tag Processing**: Monitor tag reading rates
- **🐛 Error Logging**: Check Windows Event Viewer
- **👤 User Feedback**: Collect user experience reports

---

## 🔧 Maintenance and Updates

### Ongoing Maintenance

#### Regular Tasks
- **🔄 Monitor** startup reliability
- **📊 Check** system performance
- **🔍 Review** error logs
- **🔄 Test** recovery procedures
- **📝 Update** documentation

#### Update Procedures
1. **💾 Backup** current configuration
2. **⏹️ Stop** auto-startup service/task
3. **📥 Install** new version
4. **🔄 Restore** configuration
5. **🧪 Test** functionality
6. **▶️ Re-enable** auto-startup

---

## 🆘 Troubleshooting Auto-Startup

### Startup Failures

#### Application Doesn't Start
- **🔍 Check** startup method is properly configured
- **👤 Verify** user permissions
- **📂 Confirm** application path is correct
- **📊 Check** Windows Event Viewer for errors

#### Connection Fails on Startup
- **🔌 Verify** device is connected before Windows starts
- **⚙️ Check** COM port settings

#### Target Application Issues
- **🎯 Verify** window filter text
- **📋 Test** with simple application like Notepad

### Performance Issues

#### Slow Startup
- **🚀 Use** Task Scheduler with priority settings
- **💾 Consider** SSD storage for faster boot times
- **📊 Monitor** system resource usage

#### Memory Usage
- **📊 Monitor** long-term memory usage
- **🔄 Schedule** periodic application restarts
- **⚙️ Optimize** configuration settings
- **🧹 Clear** tag history regularly

---

## 📚 Related Resources

- **[Configuration Guide](Configuration.md)** - Complete Config.xml reference
- **[User Interface Guide](User-Interface.md)** - GUI configuration options
- **[Troubleshooting Guide](Troubleshooting.md)** - Startup problem solutions
- **[Installation Guide](Installation.md)** - Initial setup procedures

---

*Auto-startup configured? Check the [User Interface Guide](User-Interface.md) for daily operation tips or return to [Home](Home.md).*