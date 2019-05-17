# Switch Pro 手柄

## 蓝牙模式的尝试

1. 配对。长按同步按钮或者截屏按钮，下方4个led滚动显示，进入配对状态。
1. 再次连接。随便长按一个按钮，就会连接。
1. 安装`xboxdrv`。
1. 建立一个udev规则文件。`/etc/udev/rules.d/99-nintendo-switch-pro-controller.rules`

        ⭕ cat 99-nintendo-switch-pro-controller.rules 
        SUBSYSTEM=="input", ATTRS{name}=="Pro Controller", SYMLINK+="switch-pro-con", TAG+="systemd", ENV{SYSTEMD_WANTS}="nintendo-switch-pro-controller.service"
        SUBSYSTEM=="input", ATTRS{name}=="Pro Controller", ACTION=="remove", RUN+="/bin/systemctl stop nintendo-switch-pro-controller"

1. 建立一个service文件。`/etc/systemd/system/nintendo-switch-pro-controller.service`

        ⭕ cat nintendo-switch-pro-controller.service 
        [Unit]
        Description=Nintendo Switch Pro Controller emulation by xboxdrv
        After=bluetooth.target
        
        [Service]
        ExecStart=/usr/bin/xboxdrv --evdev /dev/switch-pro-con --silent --detach-kernel-driver --mimic-xpad --evdev-absmap ABS_X=x1,ABS_Y=y1,ABS_RX=x2,ABS_RY=y2,ABS_HAT0X=dpad_x,ABS_HAT0Y=dpad_y --evdev-keymap BTN_TL=lt,BTN_TR=rt,BTN_SOUTH=a,BTN_EAST=b,BTN_C=x,BTN_NORTH=y,BTN_WEST=lb,BTN_Z=rb,BTN_SELECT=tl,BTN_START=tr,BTN_TL2=back,BTN_TR2=start --calibration x1=-27667:0:21355,y1=-19800:0:29072,x2=-25555:0:22545,y2=-17992:0:29024 --trigger-as-button --dbus disabled --ui-buttonmap guide=void --device-name "Nintendo Switch Pro Controller"
        KillMode=process

[Install]
Alias=nswitch-pro-con.service

> 文件内容参考[这里](https://www.reddit.com/r/RetroPie/comments/67lhv3/nintendo_switch_pro_controller_is_fully_working/)，xboxdrv路径要修改的。

此刻，我并不知道xboxdrv如何工作。目前`/dev/switch-pro-con`没有生成，说明udev规则没执行。


## 如何找到usb设备文件。
```
⭕ lsusb|g Nintendo
Bus 001 Device 007: ID 057e:2009 Nintendo Co., Ltd     <====PID/VID

⭕ sed -n '/057e/,/Handler/p' /proc/bus/input/devices 
I: Bus=0003 Vendor=057e Product=2009 Version=0111
N: Name="Nintendo Co., Ltd. Pro Controller"
P: Phys=usb-0000:00:14.0-3/input0
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3:1.0/0003:057E:2009.0005/input/input19
U: Uniq=000000000001
H: Handlers=event5 js0      <====Handler

⭕ ls /dev/input/event5 /dev/input/js0
/dev/input/event5  /dev/input/js0

```
或者，安装`evtest`也可以看到是5号设备。

## USB模式的驱动

> https://github.com/FrotBot/SwitchProConLinuxUSB

一些需要的dev包没找到。

## 直接命令行

> https://joaorb64.github.io/2018/02/14/Configuring-a-Nintendo-Switch-Pro-Controller-on-Linux.html
```
⭕ sudo /usr/bin/xboxdrv --evdev /dev/input/event5 --silent --detach-kernel-driver --mimic-xpad --evdev-absmap ABS_X=x1,ABS_Y=y1,ABS_RX=x2,ABS_RY=y2,ABS_HAT0X=dpad_x,ABS_HAT0Y=dpad_y --evdev-keymap BTN_TL=lt,BTN_TR=rt,BTN_SOUTH=a,BTN_EAST=b,BTN_C=x,BTN_NORTH=y,BTN_WEST=lb,BTN_Z=rb,BTN_SELECT=tl,BTN_START=tr,BTN_TL2=back,BTN_TR2=start --calibration x1=-27667:0:21355,y1=-19800:0:29072,x2=-25555:0:22545,y2=-17992:0:29024 --trigger-as-button --dbus disabled --ui-buttonmap guide=void --device-name "Nintendo Switch Pro Controller"

⭕ sudo xboxdrv --evdev /dev/input/event5 --silent --detach-kernel-driver --mimic-xpad --trigger-as-button --force-feedback --evdev-absmap ABS_X=x1,ABS_Y=y1,ABS_RX=x2,ABS_RY=y2,ABS_HAT0X=dpad_x,ABS_HAT0Y=dpad_y --evdev-keymap BTN_TL=lt,BTN_TR=rt,BTN_SOUTH=a,BTN_EAST=b,BTN_C=x,BTN_NORTH=y,BTN_WEST=lb,BTN_Z=rb,BTN_SELECT=tl,BTN_START=tr,BTN_TL2=back,BTN_TR2=start,BTN_MODE=guide
```
奇怪为什么游戏都只认xbox手柄。启动xboxdrv，游戏就能进入手柄提示状态。按键通常还要重新map，而且没有gui指导，很不直观。

    ⭕ sudo xboxdrv --evdev /dev/input/event16 --evdev-debug
xboxdrv直接debug，按任何键没有输出。不知道为什么。

最终还是`antimicro`设置好，至少map键位有gui。只是使用时，对应的键位有时候记不住（因为没有对应的游戏屏幕的提示）。