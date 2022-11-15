# 暗影精灵2 i7-6700HQ 安装记录

## [黑苹果（hackintosh）系统安装总览](https://hackintosh.myitnote.com/)

## 常见错误集，参考博客

[安装黑苹果卡代码及界面解决方法，仅支持OpenCore](https://www.cainiaogaoji.com/index.php/archives/13/)

[OC Gen X详细讲解教程----目前最小白的黑苹果OC引导定制工具（真的没有更简单了）](https://www.bilibili.com/read/cv7581784?from=search&spm_id_from=333.337.0.0)

[黑苹果hackintosh安装调试手记 驱动调整](https://zhuanlan.zhihu.com/p/555048121)

## 参考安装工具

[ProperTree](https://link.zhihu.com/?target=https%3A//github.com/corpnewt/ProperTree)

 [SSDTTime](https://github.com/corpnewt/SSDTTime) 

[OCAuxiliaryTools](https://macx.top/19943.html)

[OpenCore Configurator](https://heipg.cn/tag/opencore-configurator)

- 根据你的 OpenCore 版本选择 OCC 版本
- 不喜欢 OCC 的话，[OCAuxiliaryTools](https://heipg.cn/tag/ocauxiliarytools) 或 [ProperTree](https://heipg.cn/tag/propertree) 也是极好的

- [Hackintool](https://heipg.cn/tag/hackintool)：用以验证定制结果
- [USBToolBox](https://heipg.cn/tag/usbtoolbox)：USB 接口发现及 USBMap.kext 生成工具

### 定制USB

[Windows下定制黑苹果USB接口macOS BigSur 11.3及以上系统版本USBToolBox端口USB定制](http://imacos.top/2022/08/22/windows-usb-macos-bigsur-11-3-usbtoolbox/)

[USB定制新姿势：Windows下定制黑苹果USB接口详细攻略](https://heipg.cn/tutorial/customize-usb-port-windows.html#%E5%87%86%E5%A4%87%E5%B7%A5%E4%BD%9C)

[USBToolBox](https://github.com/USBToolBox/tool)

[USBToolBox.kext/Contents](https://github.com/hacker1024/Dell-Inspiron-7586-Hackintosh/tree/ventura/master/EFI/OC/Kexts/USBToolBox.kext/Contents) 内核提取

## 使用[OC gen x](https://github.com/Pavo-IM/OC-Gen-X) 生成默认配置

暗影精灵2 i7-6700HQ 对应 MacBookPro,13,3 型号

| MacBookPro13,3 | 2016年 | 15英寸Retina | i7 6700HQ | HD Graphics 530+Pro 450 | i7 6820HQ | Pro 455 | i7 6920HQ | Pro 460 | 12.0 Monterey |
| -------------- | ------ | ------------ | --------- | ----------------------- | --------- | ------- | --------- | ------- | ------------- |
|                |        |              |           |                         |           |         |           |         |               |

OC Gen X自动化生成的EFI引导文件，还缺少一些信息，还需要完善一下

ACPI补丁

核显ID及缓冲帧 参考[别人的EFI文件](https://github.com/markxsq/HP_OMEN-2_i7_Monterey_OC-0.8.4) 

核显 HD530

没有OC主题(可选，需要版本对应)

OC主题，需要Resources文件，加Q群（1125705781） 

## 配置SSDT

[参考官方](https://dortania.github.io/Getting-Started-With-ACPI/ssdt-platform.html#desktop)

根据台式机和笔记本配置相应的ACPI文件

推荐使用 [SSDTTime](https://github.com/corpnewt/SSDTTime) 在windows可用

## 更新kext

![oc clean](https://img2020.cnblogs.com/blog/405098/202009/405098-20200907160549928-1743136108.png)

# **禁用睡眠**

打开终端，输入sudo pmset -b sleep 0，换行输入sudo pmset -b disablesleep 1。

如果要恢复睡眠，输入sudo pmset -b sleep 5，换行输入sudo pmset -b disablesleep 0。

## 禁用独显

boot-args: `-wegnoegpu`

```shell
-v keepsyms=1 agdpmod=pikera  -v debug=0x100 -wegnoegpu
```

## 使用oc引导需要注意，在bigsur更高的系统**需要定制USB**

否则，就算是相同机型也无法使用。问题主要来自于定制USB中的硬盘。定制好USB不要随意更换硬盘，否则需要重新进入windows定制硬盘。

[Windows下定制黑苹果USB接口macOS BigSur 11.3及以上系统版本USBToolBox端口USB定制](http://imacos.top/2022/08/22/windows-usb-macos-bigsur-11-3-usbtoolbox/)

[HeliPort](https://github.com/OpenIntelWireless/HeliPort)

[OpenCore Configurator](https://macoshome.com/hackintosh/htools/2100.html#Down)
