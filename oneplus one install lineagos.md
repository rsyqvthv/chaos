- 解锁bootlocker

`fastboot oem unlock`
`fastboot oem device-info`

- 刷custom recovery

> When you fastbootbflash recovery, remember: after flashing is complete, disconnect cable, press power button until phone turns off. The press vol down and power button to go into recovery. If you use the adb command to reboot it will go back to stock OS. Happens with me every time [via](https://forums.oneplus.com/threads/stuck-on-oxygen-os-2-1-4-how-to-reinstall-twrp.426837/)

注意不要直接进入系统, 而是先关机, 然后 `power+volume down` 进入recovery.

> You probably left the 'Update CM Recovery' option enabled when you updated .

也有因为这个无法让custom rom维持的.

- 在custom recovery中安装lineagoos

factory reset
format data
factory reset
以上步骤将素有加密文件全部删除.

twrp > advanced > adb sideload

电脑端: `adb sideload filename.zip`

出现了 `error 7`

- 尝试使用lineage os的custom recovery

成功.




