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
  - [x] 10.15.2
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

## 未测试/未做

- [x] 模拟NVRAM
- [x] 声卡
  - [x] 主板后置
  - [x] 机箱前置



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

- Opencore 0.5.3