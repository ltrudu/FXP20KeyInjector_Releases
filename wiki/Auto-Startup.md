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
<FXP20KeyInjectorConfig>
  <!-- Auto-Startup Settings -->
  <AutoConnect>true</AutoConnect>
  <AutoStartReading>true</AutoStartReading>
  
  <!-- Connection Settings -->
  <ComPort>COM5</ComPort>
  <BaudRate>921600</BaudRate>
  
  <!-- Target Application -->
  <WindowFilter>Your Target Application</WindowFilter>
  <Protocol>CLIPBOARDPASTE</Protocol>
  
  <!-- Optional: Minimize to system tray -->
  <StartMinimized>true</StartMinimized>
  <MinimizeToTray>true</MinimizeToTray>
</FXP20KeyInjectorConfig>
```

---

## 🪟 Windows Startup Integration

### Option 1: Windows Startup Folder (Simple)

#### Add to User Startup
1. **⌨️ Press** Windows + R
2. **📝 Type** `shell:startup` and press Enter
3. **📂 Copy** FXP20KeyInjector.exe to this folder
4. **🔄 Restart** Windows to test

#### Add to System Startup (All Users)
1. **⌨️ Press** Windows + R  
2. **📝 Type** `shell:common startup` and press Enter
3. **👤 Run** as Administrator if prompted
4. **📂 Copy** FXP20KeyInjector.exe to this folder

### Option 2: Registry Startup Entry (Advanced)

#### Create Registry Entry
```batch
:: Run as Administrator
reg add "HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Run" /v "FXP20KeyInjector" /t REG_SZ /d "C:\Program Files\FXP20KeyInjector\FXP20KeyInjector.exe"

:: For all users (requires admin)
reg add "HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Run" /v "FXP20KeyInjector" /t REG_SZ /d "C:\Program Files\FXP20KeyInjector\FXP20KeyInjector.exe"
```

#### Remove Registry Entry
```batch
:: Remove user startup
reg delete "HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Run" /v "FXP20KeyInjector"

:: Remove system startup (requires admin)
reg delete "HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Run" /v "FXP20KeyInjector"
```

### Option 3: Task Scheduler (Most Reliable)

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
<Arguments>/autostart</Arguments>
<WorkingDirectory>C:\Program Files\FXP20KeyInjector</WorkingDirectory>
<Priority>4</Priority>
<RunLevel>HighestAvailable</RunLevel>
<RestartCount>3</RestartCount>
<RestartInterval>PT10M</RestartInterval>
```

---

## 🛡️ Service Installation (Enterprise)

### Option 4: Windows Service (Advanced Users)

For maximum reliability, install as a Windows service:

#### Service Wrapper Setup
1. **📥 Download** NSSM (Non-Sucking Service Manager)
2. **📂 Extract** to system PATH location
3. **👤 Open** Command Prompt as Administrator
4. **⚙️ Configure** service:

```batch
:: Install service
nssm install FXP20KeyInjector "C:\Program Files\FXP20KeyInjector\FXP20KeyInjector.exe"

:: Configure service
nssm set FXP20KeyInjector Start SERVICE_AUTO_START
nssm set FXP20KeyInjector ObjectName LocalSystem
nssm set FXP20KeyInjector Type SERVICE_WIN32_OWN_PROCESS

:: Start service
nssm start FXP20KeyInjector
```

#### Service Management
```batch
:: Check service status
sc query FXP20KeyInjector

:: Stop service
nssm stop FXP20KeyInjector

:: Remove service
nssm remove FXP20KeyInjector confirm
```

---

## ⚙️ Auto-Startup Configuration Reference

### Essential Config.xml Settings

#### Connection Automation
```xml
<!-- Automatic connection settings -->
<AutoConnect>true</AutoConnect>
<AutoConnectDelay>5000</AutoConnectDelay>  <!-- Wait 5 seconds before connecting -->
<ComPort>COM5</ComPort>                     <!-- Specify exact COM port -->
<BaudRate>921600</BaudRate>
<ConnectionTimeout>10000</ConnectionTimeout>
```

#### Reading Automation
```xml
<!-- Automatic reading settings -->
<AutoStartReading>true</AutoStartReading>
<AutoStartDelay>2000</AutoStartDelay>      <!-- Wait 2 seconds after connection -->
<ContinuousReading>true</ContinuousReading>
<RemoveDuplicates>true</RemoveDuplicates>   <!-- Filter duplicate tags -->
```

#### Application Integration
```xml
<!-- Target application settings -->
<WindowFilter>Inventory Management System</WindowFilter>
<Protocol>CLIPBOARDPASTE</Protocol>        <!-- Fastest data delivery -->
<WaitForWindow>true</WaitForWindow>         <!-- Wait for target window -->
<WindowWaitTimeout>30000</WindowWaitTimeout> <!-- Wait up to 30 seconds -->
```

#### User Interface Settings
```xml
<!-- UI behavior for automatic startup -->
<StartMinimized>true</StartMinimized>       <!-- Start minimized -->
<MinimizeToTray>true</MinimizeToTray>       <!-- Hide in system tray -->
<ShowNotifications>false</ShowNotifications> <!-- Disable popup notifications -->
<SilentMode>true</SilentMode>               <!-- Suppress non-critical dialogs -->
```

### Advanced Configuration Options

#### Retry and Error Handling
```xml
<!-- Connection retry settings -->
<ConnectionRetries>5</ConnectionRetries>
<RetryDelay>10000</RetryDelay>             <!-- 10 seconds between retries -->
<ReconnectOnError>true</ReconnectOnError>
<MaxReconnectAttempts>10</MaxReconnectAttempts>
```

#### GPIO and Hardware Settings
```xml
<!-- Hardware trigger settings -->
<HookGPIOToStartReading>true</HookGPIOToStartReading>
<GPIOReadingDurationInMs>5000</GPIOReadingDurationInMs>
<GPIOPin>1</GPIOPin>
<BeepOnRead>true</BeepOnRead>
<BeepDuration>200</BeepDuration>
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

:: Monitor service startup
sc query FXP20KeyInjector

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

#### Configuration Backup
```batch
:: Backup configuration
copy "C:\Program Files\FXP20KeyInjector\Config.xml" "C:\Backup\FXP20-Config-Backup.xml"

:: Restore configuration
copy "C:\Backup\FXP20-Config-Backup.xml" "C:\Program Files\FXP20KeyInjector\Config.xml"
```

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
- **⏱️ Increase** auto-connect delay
- **🔌 Verify** device is connected before Windows starts
- **⚙️ Check** COM port settings
- **🔄 Add** retry logic to configuration

#### Target Application Issues
- **⏱️ Increase** window wait timeout
- **🎯 Verify** window filter text
- **📋 Test** with simple application like Notepad
- **🔄 Add** startup delay for target application

### Performance Issues

#### Slow Startup
- **⏱️ Optimize** delay settings
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