# Android Command Note

## Logcat

adb logcat -v time

adb logcat -v time -b main

adb logcat -v time -b system

adb logcat -v time -b events

adb logcat -v time -b radio

## Application

adb install <Apk File>

adb uninstall <Package Name>


## dumpsys

## Root

adb root

## Other

adb reboot

adb pull <Unit Path> <Local Path>

adb shell input keyevent <event key>

adb shell input text <string>

