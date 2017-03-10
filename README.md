# Android Command Note

## Logcat

adb logcat -v time

adb logcat -v time -b main

adb logcat -v time -b system

adb logcat -v time -b events

adb logcat -v time -b radio

adb shell logcat -b all

adb logcat -B


### Android 6.0〜

adb shell logcat -v color


### Android 7.0〜

adb logcat -e android

adb logcat -m 100


## log

adb shell log [message]

adb shell log -t [tag name] [message]

adb shell log -p [log level] [message]


## Bugreport

adb  bugreport


## Bugreportz

adb shell bugreportz


## Application

adb install [Apk File]

adb uninstall [Package Name]


## pm - PackageManager

adb shell pm list packages

adb shell pm list packages -e

adb shell pm list packages -d

adb shell pm list packages -s

adb shell pm list packages -3

adb shell pm path [Package Name]

adb shell pm clear [Package Name]


## dumpsys

adb shell dumpsys

[adb shell dumpsys -l](./outputs/dumpsys-l.md)

adb shell dumpsys [system service]

adb shell dumpsys service [service name]

adb shell dumpsys activity activities

adb shell dumpsys activity top

adb shell dumpsys activity all

adb shell dumpsys activity provider

adb shell dumpsys activity provider all

adb shell dumpsys gfxinfo

adb shell dumpsys jobscheduler

adb shell dumpsys netpolicy

adb shell dumpsys alarm

adb shell dumpsys dbinfo

adb shell dumpsys dbinfo [Package Name]


## run-as

adb shell run-as [Package Name]


## Root

adb root


## Input Text

adb shell input text [string]


## Input Key Event

#### adb shell input keyevent [event key]

adb shell input keyevent KEYCODE_HOME

adb shell input keyevent KEYCODE_BACK

adb shell input keyevent KEYCODE_MENU


## am

adb shell am start -a android.intent.action.VIEW -d [DATA_URI]

adb shell am start -a android.settings.WEBVIEW_SETTINGS

adb shell am broadcast -a [Intent]

adb shell am hang


## アプリケーションのデータとキャッシュを残したままアンインストールする

* adb shell cmd package uninstall -k [Package Name]


## System properties

adb shell getprop

adb shell getprop [property name]

adb shell setprop [property name] [property value]


## screenrecord

adb shell screenrecord /sdcard/test.mp4

adb shell screenrecord --size 720x1080 /sdcard/test.mp4

adb shell screenrecord --bit-rate 10000000 /sdcard/test.mp4

adb shell screenrecord --time-limit 120 /sdcard/test.mp4

adb shell screenrecord --bugreport /sdcard/test.mp4



### "unofficial" options

adb shell screenrecord --rotate /sdcard/test.mp4

adb shell screenrecord --output-format raw-frames /sdcard/test

[screenrecordの"unofficial" optionsは夢がいっぱいだった](http://qiita.com/operandoOS/items/aced3c76cdb4a738be53)


## Date

adb shell date -s YYYYMMDD.hhmmss

YYYYMMDD:年月日  hhmmss:時分秒

**要Root**

[【Android】adb shell date は System User or radio Groupじゃないと反映されない](http://qiita.com/operandoOS/items/61bbbed2568e27a6ee4e)

### Windows

adb shell date -s %date:~0,4%%date:~5,2%%date:~8,2%.%time:~0,2%%time:~3,2%%time:~6,2%

### Linux or Mac

adb shell date -s $(date +"%Y%m%d.%H%M%S")


## Dropbox

adb shell dumpsys dropbox

adb shell dumpsys dropbox --print

adb shell dumpsys dropbox --file


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


## Permission

adb shell pm list permissions -d -g

adb shell pm grant [permission.name] ...

adb shell pm revoke [permission.name] ...


## システム設定アプリで特定のアプリの設定画面を開く

shell am start -a android.settings.APPLICATION_DETAILS_SETTINGS -d package:[Package Name]

### Example

shell am start -a android.settings.APPLICATION_DETAILS_SETTINGS -d package:com.android.chrome


## dumpsys activity activitiesとpecoでゴニョゴニョして端末からapkを簡単に引っこ抜く

adb shell dumpsys activity activities | grep apk | sed -e 's/ *baseDir=//g' | peco | xargs adb pull

http://qiita.com/operandoOS/items/6fa77037560e52d11352


## Other

adb shell printenv

adb reboot

adb shell reboot recovery

adb pull [Unit Path] [Local Path]

adb push [File Path] [Unit Path]

adb jdwp
