# Android Command Note

## Logcat

adb logcat -v time

adb logcat -v time -b main

adb logcat -v time -b system

adb logcat -v time -b events

adb logcat -v time -b radio

## log

adb shell log [message]

adb shell log -t [tag name] [message]

adb shell log -p [log level] [message]


## Application

adb install [Apk File]

adb uninstall [Package Name]

## pm - PackageManager

adb shell pm list packages

adb shell pm list packages -e

adb shell pm list packages -d

adb shell pm list packages -s

adb shell pm list packages -3

## dumpsys

adb shell dumpsys

adb shell dumpsys | grep "DUMP OF SERVICE"

adb shell dumpsys [system service]

adb shell dumpsys service [service name]

adb shell dumpsys activity activities

adb shell dumpsys activity all

adb shell dumpsys activity provider

adb shell dumpsys activity provider all

adb shell dumpsys gfxinfo

## Root

adb root


## Key Event

#### adb shell input keyevent [event key]

adb shell input keyevent KEYCODE_HOME

adb shell input keyevent KEYCODE_BACK

adb shell input keyevent KEYCODE_MENU


## Alarm

adb shell dumpsys alarm

## System properties

adb shell getproc

adb shell getprop [property name]

adb shell setprop [property name] [property value]

## Date

adb shell date -s YYYYMMDD.hhmmss

YYYYMMDD:年月日  hhmmss:時分秒

**要Root**

[【Android】adb shell date は System User or radio Groupじゃないと反映されない](http://qiita.com/operandoOS/items/61bbbed2568e27a6ee4e)

### Windows

adb shell date -s %date:~0,4%%date:~5,2%%date:~8,2%.%time:~0,2%%time:~3,2%%time:~6,2%

### Linux or Mac

adb shell date -s $(date +"%Y%m%d.%H%M%S")

## Lint

lint [application directory] --html [file name].html

lint [application directory] --simplehtml [file name].html

### Windows

lint [application directory] --fullpath --quiet --html lint_%date:~0,4%%date:~5,2%%date:~8,2%-%time:~0,2%%time:~3,2%%time:~6,2%.html

### Linux or Mac

lint [application directory] --fullpath --quiet --html lint_$(date +"%Y%m%d-%H%M%S").html

## Kernal

adb shell dmesg

adb shell cat /proc/kmsg


## Other

adb reboot

adb shell reboot recovery

adb pull [Unit Path] [Local Path]

adb push [File Path] [Unit Path]

adb shell input text [string]
