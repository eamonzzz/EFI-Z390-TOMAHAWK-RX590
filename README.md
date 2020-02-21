# MSI Z390 Tomahawk Macintosh OC && Clover



微星 Z390 Tomahawk 战斧导弹 + RX590 + i5 9600kf  黑苹果 EFI 


## 我的配置

| 硬件        | 型号                   |
| ----------- | ---------------------- |
| 主板        | MSI Z390 MAG Tomahawk  |
| CPU         | Intel i5-9600KF        |
| 显卡        | 蓝宝石 RX590 8G 超白金 |
| 声卡        | Realtek ALC892         |
| 无线 + 蓝牙 | 博通 BCM94360CD        |

---

## 说明

项目中CLOVER是在淘宝上嫖的，能够成功引导，但是没有去精简，里面很多内容。如果你使用CLOVER引导不成功，请自行修改，或者用OpenCore版本的EFI试试。

目前我正在使用的是OC引导，自己根据 [xjin大神](https://blog.xjn819.com/?p=543) 的博客配置的，如果不是很了解OpenCore，建议详细阅读一遍大神的博客。

## 完美情况

- [x] macOS 版本
  - [x] 10.15.x
- [x] 显卡（HDMI接4k显示器）
  - [x] AMD RX590 
- [x] 睡眠/唤醒
- [x] 有线网卡
- [x] 所有 USB 插口
- [x] 无线 WiFi
- [x] 原生电源管理
- [x] 声卡(Realtek ALC892)
  - [x] HDMI 显示器输出
- [x] 蓝牙
  - [x] Airdrop
  - [x] 耳机
  - [x] 其他未测试
- [x] 模拟NVRAM

- [x] 声卡
  - [x] 主板后置
  - [x] 机箱前置

## 更新记录

2020-02-22:

1. 重新定制USB
2. 解决RTC ALARM引起的定时唤醒
3. 添加6D补丁SSDT-GPRW，修复XDCI CNVW睡眠唤醒问题

2020-02-14:

1. 完成 usb 定制--添加USBPorts.kext定制驱动（驱动中的USBInjectAll.kext可以删除了，我这里是在config.plist中禁用的，并没有删）
2. 在 ACPI中添加了SSDT-UIAC.aml，这是定制USB时导出的，使用了USBPorts.kext之后，这个补丁可以不加载（我只是添加了该文件并未在config.plist进行注入）
3. 此外还更新了“解除usb端口限制开关”，既：将 XhciPortLimit 设置为false

2020-02-09：

1. 升级OpenCore版本至 0.5.6
2. 升级和删除部分驱动
3. 由于从OC 0.5.5 版本开始，已经支持300系列主板的原生nvram，且教程相对简单，所以这次提交的配置中包含了模拟nvram的配置（但是SSDT-PMC.aml文件需要按照 [xjn 大佬博客](https://blog.xjn819.com/?p=543) 3.12 章节描述进行修改）

## 安装注意事项

### 主板设置（参考@黑果小兵）

#### 禁用如下：

| 英文                                 | 中文                                                     |
| :----------------------------------- | :------------------------------------------------------- |
| Fast Boot                            | 快速启动                                                 |
| CFG Lock (MSR 0xE2 write protection) | CFG 锁 (MSR 0xE2 写入保护)                               |
| VT-d                                 | [VT-d](https://zhidao.baidu.com/question/495526512.html) |
| CSM                                  | 兼容性支持模块                                           |

#### 启用如下：

| 英文               | 中文                 |
| :----------------- | :------------------- |
| Above 4G decoding  | 大于 4G 地址空间解码 |
| EHCI/XHCI Hand-off | 接手 EHCI/XHCI 控制  |

### 机型配置修改：

不管使用的是OC还是Clover，请修改 `config.plist` 文件中机型以及主板序列号等信息（OC里我使用类似 `xxxxxx` 来代替了，使用的时候替换掉）

### 当前版本

- Opencore 0.5.6



### 系统截图

概览

![](https://raw.githubusercontent.com/eamonzzz/my-picture-bed/master/blog-images20200209112343.png)

显示器

![显示器](https://raw.githubusercontent.com/eamonzzz/my-picture-bed/master/blog-images20200209112501.png)

USB

![USB](https://raw.githubusercontent.com/eamonzzz/my-picture-bed/master/blog-images20200209112602.png)

网卡

![网卡](https://raw.githubusercontent.com/eamonzzz/my-picture-bed/master/blog-images20200209112640.png)

显卡

![图形卡](https://raw.githubusercontent.com/eamonzzz/my-picture-bed/master/blog-images20200209112717.png)

电源

![电源](https://raw.githubusercontent.com/eamonzzz/my-picture-bed/master/blog-images20200209112832.png)

蓝牙

![蓝牙](https://raw.githubusercontent.com/eamonzzz/my-picture-bed/master/blog-images20200209112903.png)

声卡

![声卡](https://raw.githubusercontent.com/eamonzzz/my-picture-bed/master/blog-images20200209112944.png)

原生电源

![原生电源](https://raw.githubusercontent.com/eamonzzz/my-picture-bed/master/blog-images20200209114100.png)

