*Please be aware that this library / application / sample is provided as a community project without any guarantee of support*
=========================================================
# This tool is not officially supported by Zebra if you have any issues, use the Issues tab of this repository.
## As it is a personnal initiative, I'll do my best to fix issues, but I can not ensure that it will be done quickly.

Please, before using the tool, read the [documentation](https://github.com/ltrudu/FXP20KeyInjector_Releases/blob/master/FXP20KeyInjector-HowTo.docx?raw=true)

This tool is released under the [Zebra EULA](https://github.com/ltrudu/FXP20KeyInjector_Releases/blob/master/EULA.txt)

Please, take the time to read the EULA before using this tool.

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
