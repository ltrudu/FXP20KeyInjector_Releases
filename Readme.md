*Please be aware that this library / application / sample is provided as a community project without any guarantee of support*
=========================================================
# This tool is not officially supported by Zebra if you have any issues, use the Issues tab of this repository.
## As it is a personnal initiative, I'll do my best to fix issues, but I can not ensure that it will be done quickly.

The FXP20KeyInjector is a Windows application that add Keyboard Injection, Clipboard Paste and MQTT capabilities to the FXP20 RFID reader.

You can trigger a reading session with a keyboard touch, or a button connected to the GPI ports.

The application can start minimized, automatically connects to the reader and start reading tags automatically when a connexion is done.

Please, before using the tool, read the [documentation](https://github.com/ltrudu/FXP20KeyInjector_Releases/blob/master/FXP20KeyInjector-HowTo.docx?raw=true)

This tool is released under the [Zebra EULA](https://github.com/ltrudu/FXP20KeyInjector_Releases/blob/master/EULA.txt)

Please, take the time to read the EULA before using this tool.

You will find two demo apps in the following repositories:

- POS demo : https://github.com/ltrudu/FXP20DemoPos
- PackBench demo : https://github.com/ltrudu/FXP20DemoBench

=========================================================
# ChangeLog
=========================================================

## 2025-09-09 :

Added a section in  the documentation to explain how to autostart the application, autoconnect to the reader and even autostart reading tags when the connection is done.


## 2025-09-08 : 

Added RemoveDuplicates element in the Config.xml file.

This functionality works when the PerformReadingWithGPIO or HookKeyboardToStartReading is set to true.

If it is set to true, it will ensure that during the PerformReadingDuration or HookKeyboardReadingDurationInMs time of reading tags, only unique tags will be reported.

Any duplicate tag or re-read tags during this period of reading will be filtered.
