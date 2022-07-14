# RA6M4
 RA6M4 frist open
![在这里插入图片描述](https://img-blog.csdnimg.cn/6b811dcaa06a4672bc6fb550fed35df7.png)
# 1. CPK-RA6M4 开发板特点
基于瑞萨RA6M4 MCU开发的CPK-RA6M4 MCU评估板 ，通过 灵活配置软件包和IDE，可帮助用户对RA6M4 MCU 群组的特性轻松进行评估，并对嵌入系统应用程序进行开发。
## 1.1 搭载资源
![在这里插入图片描述](https://img-blog.csdnimg.cn/5aab5da578554aea8f2425bf23492125.png)
## 1.2 外观正面
![在这里插入图片描述](https://img-blog.csdnimg.cn/3a77b4b82c024748ab23cb4898f87c65.png)
## 1.3 外观反面
![在这里插入图片描述](https://img-blog.csdnimg.cn/7b45a669ea7f4fefa3a5d6c0df4e050d.png)
## 1.4 系统框图
![在这里插入图片描述](https://img-blog.csdnimg.cn/4703485ff1a7434cb8a9a25331aee16b.png)
## 1.5 板载原理图
![在这里插入图片描述](https://img-blog.csdnimg.cn/d0c57b9f50a147528196af49b0a811ac.png)
![在这里插入图片描述](https://img-blog.csdnimg.cn/fa85e6b9f731403eb8020fddab3ad42a.png)
![在这里插入图片描述](https://img-blog.csdnimg.cn/7054caeee0344066b38a51e71d27b3aa.png)
![在这里插入图片描述](https://img-blog.csdnimg.cn/df788a678b624197bd95ed9f602a3de5.png)
![在这里插入图片描述](https://img-blog.csdnimg.cn/5e8170f9fbbc4ac6b17bd57fcea1ff9a.png)

来源：
[《开发板用户手册》](https://www2.renesas.cn/cn/zh/document/mah/1527156?language=zh&r=1527191)
[原理图：](https://oss-club.rt-thread.org/uploads/20220314/460d66bee9aa09a6036f302890ebc737.pdf)

本文将使用瑞萨的 CPK-RA6M4 开发板介绍如何在 RA 系列 MCU 上让 RT-Thread 运行起来。开发环境的搭建将分为以下几个部分：
- RA 开发环境搭建
- 基于 RT-Thread Studio开发环境搭建
# 2. RA 开发环境搭建
## 2.1 必备工具
### 2.1.1 灵活配置软件包 (FSP) ：

可快速配置开发板的外设功能，请使用 v3.5.0 版本，目前可在github上下载3.5.0版本（下载地址：https://github.com/renesas/fsp/releases/tag/v3.5.0 ，注意文件名称为：setup_fsp_v3_5_0_rasc_v2021-10.exe）
![在这里插入图片描述](https://img-blog.csdnimg.cn/5cfd255bda3e4970b6f9610fc6582304.png)

<注意官网为3.8.0版本，不向前兼容，使用3.8.0版本会会导致本工程不可用>

### 2.1.2 CPK-RA6M4 板级支持包：
配合 FSP 一起使用，是开发板的图形化配置支持包,请使用 v3.5.0 版本

[可在Renesas官网下载：](https://www2.renesas.cn/cn/zh/products/microcontrollers-microprocessors/ra-cortex-m-mcus/cpk-ra6m4-evaluation-board)
![图片](https://img-blog.csdnimg.cn/03ee908986df47cd8006dd3d9bf384af.png)
网盘下载链接：https://cowtransfer.com/s/b9eddec169d544
已包含 上述FSP 软件和 FSP 板级支持包，从此链接下载可一步到位。


## 2.2 环境搭建

> 灵活配置软件包 (FSP)

1、打开链接下载 FSP，请确认下载的 3.5.0 版本，从网盘下载可忽略此下载步骤。

目前 RT-Thread 中  CPK-RA6M4 的 BSP 支持的版本是 3.5.0。可以在 BSP 的 README 中确认目前支持的 FSP 版本。
![图片](https://img-blog.csdnimg.cn/b665761bda7c41f0a27b22126dc8dfab.png)2、找到下载的文件打开（注意文件名称包含为rasc）：setup_fsp_v3_5_0_rasc_v2021-10.exe

![图片](https://img-blog.csdnimg.cn/f534d538831b4882aaaf762bdbf0a14c.png)
3、配置安装路径，安装完成后找到此路径，之后添加 CPK-RA6M4 板级支持包 时会用到

![图片](https://img-blog.csdnimg.cn/feb999602c7d4d3d840f493c6d3e73bc.png)
4、勾选 Licenese
![图片](https://img-blog.csdnimg.cn/a09ae82cc62743bcbc98cf9d5663b77f.png)
5、点击 install 等待安装完成。
![图片](https://img-blog.csdnimg.cn/42d84b30d3ca4fdc98bb81b05aa6e18a.png)
6、运行 rasc.exe，验证是否安装成功。路径：\eclipse\rasc.exe

![图片](https://img-blog.csdnimg.cn/03a6c1724649422ab931f8e6505b341c.png)
7、成功启动后关闭即可，继续接下来的操作

![在这里插入图片描述](https://img-blog.csdnimg.cn/4219a7b163fc4cc9b906133c7d7c6939.png)

## 2.3 CPK-RA6M4 板级支持包
1、此部分，你可以参考Renesas官网文档[《向FSP中添加CPK评估板的BSP 》](https://www2.renesas.cn/cn/zh/document/gde/1596896?language=zh&r=1527191)
下载 3.5.0 版本支持包。从网盘下载可忽略此下载步骤。
![图片](https://img-blog.csdnimg.cn/3bab66daee564bdd875674b1eb8c8fd7.png)
2、在下载的支持包中可以找到以下三个文件

![图片](https://img-blog.csdnimg.cn/79a3397b4c57424aae4a96bb2936b141.png)
3、此时找到 FSP 的安装路径，进入 \internal\projectgen\ra\ ，将文件复制到对应的文件夹中。

![图片](https://img-blog.csdnimg.cn/1e37dc1b9c9f4d4d854a8b5666012afa.png)
4、再次打开 rasc.exe，查看是否添加成功。点击 next 进入工程创建

![图片](https://img-blog.csdnimg.cn/ce1d9f107f684a0cbfa4091f6ac851cd.png)


5、确认是否存在已添加的 CPK-RA6M4 开发板的支持包，**此步骤仅为验证是否添加成功，不必继续创建工程，关闭即可。**

![图片](https://img-blog.csdnimg.cn/1fcc6c01d0ce482095aabc0b15168edc.png)
6、到此基本将瑞萨开发板相关的环境搭建完成。调试器 J-link 的安装，在下面的步骤中介绍。

# 3. RT-Thread 开发环境搭建
## 3.1 基于 RT-Thread studio

> 下载安装必备软件环境

 - 下载并安装 RT-Thread studio
 -  打开 RT-Thread studio，进入包管理器，下载 RT-Thread 的 bsp 支持包及相关工具。

![图片](https://img-blog.csdnimg.cn/c94dde4da85a4cc79f2b51103f9b43f3.png)


下载 BSP 支持包，勾选最新版即可。

![图片](https://img-blog.csdnimg.cn/d6fefa875e5d4a7cbb589934535df6f5.png)


PS:BSP 支持包会自动下载依赖的资源包：

 - RT-Thread 系统源码包
 - GCC工具链：版本 10.2.1
 - 调试器 J-link：版本 7.50a

![图片](https://img-blog.csdnimg.cn/13c67dab6cd647ec8f7d044ae12a7efb.png)


## 3.2 创建工程测试结果
1、打开 RT-Thread studio，新建 RT-Thread 项目 —> 基于开发板，创建CPK-RA6M4的工程
![图片](https://img-blog.csdnimg.cn/c016dfce0e1e458587bd96e0f9f2f8dd.png)

2、打开创建的工程，双击 RA Smart Configurator 即可打开刚刚安装的 FSP 配置工具图片
![在这里插入图片描述](https://img-blog.csdnimg.cn/1fca104219a142c6acb8b5c2369b523f.png)

3、第一次打开需要配置 FSP 路径，选择到安装路径即可。确认可打开 FSP 即可关闭，先不做修改继续后续操作。

![在这里插入图片描述](https://img-blog.csdnimg.cn/7ea88a197b7a4f078a0550fa221ef0dd.png)



![图片](https://img-blog.csdnimg.cn/bfacd7b950fe44fdb523b464067ede86.png)


![图片](https://img-blog.csdnimg.cn/54c0708155b34afc8dd3bcc1b3d8ed7c.png)


4、编译工程，确认工具链配置正确
![在这里插入图片描述](https://img-blog.csdnimg.cn/2e775884ce6845909390320b11438cbf.png)


5、接线：连接串口工具、USB-Jlink **(跳帽恢复到normal operation以及device mode)**
![图片](https://img-blog.csdnimg.cn/ba715bc1359b43ddbecf1b66f02330fa.png)

6、连接 UART7 （TX:P613; RX:P614）,波特率 115200。此路串口用于 RT-Thread 系统命令行交互。

![图片](https://img-blog.csdnimg.cn/5f1475c38f3c4a309c45152e2eb027a9.png)

7、下载程序到开发板，注意下载的是 HEX 文件。

- 查看运行结果

> 下载程序成功之后，系统会自动运行并打印系统信息。 连接开发板对应串口到 PC ,在终端工具里打开相应的串口（115200-8-1-N），复位设备后，可以看到 RT-Thread 的输出信息。输入 help命令可查看系统中支持的命令。
> 板载LED3会以1Hz频率闪烁

- 打开示波器
![在这里插入图片描述](https://img-blog.csdnimg.cn/c27974770fb24ac39413a561353ba341.png)
- 板载reset, 查看相关内置信息
![在这里插入图片描述](https://img-blog.csdnimg.cn/92b7e4cc31b44a9189d1f382609a451b.png)
- 打印结果如下

```c
 \ | /
- RT -     Thread Operating System
 / | \     4.1.0 build Jan 18 2022 18:48:37
 2006 - 2021 Copyright by rt-thread team

Hello RT-Thread!
msh >
RT-Thread shell commands:
icu_sample       - icu sample
list             - list all commands in system
list_device      - list device in system
list_timer       - list timer in system
list_msgqueue    - list message queue in system
list_mailbox     - list mail box in system
list_mutex       - list mutex in system
list_event       - list event in system
list_sem         - list semaphore in system
list_thread      - list thread
version          - show RT - Thread version information
clear            - clear the terminal screen
hello            - say hello world
free             - Show the memory usage in the system.
ps               - List threads in the system.
help             - RT - Thread shell help.
reboot           - Reboot System

msh >
```
8、应用入口函数

- 应用层的入口函数在 bsp\ra6m4-cpk\src\hal_emtry.c 中 的 void hal_entry(void) 。用户编写的源文件可直接放在 src 目录下。

```c
void hal_entry(void)
{
    rt_kprintf("\nHello RT-Thread!\n");    while (1)
    {
        rt_pin_write(LED3_PIN, PIN_HIGH);
        rt_thread_mdelay(500);
        rt_pin_write(LED3_PIN, PIN_LOW);
        rt_thread_mdelay(500);
    }
}
```
- main.c 在项目文件夹地re_ge下
![在这里插入图片描述](https://img-blog.csdnimg.cn/d7e7cbf34efd4547a3977655fa71077e.png)

```c
/* generated main source file - do not edit */
#include "hal_data.h"
            int main(void) {
              hal_entry();
              return 0;
            }

```

关于RA系列MCU 相关资源可见：
[《开发板用户手册》](https://www2.renesas.cn/cn/zh/document/mah/1527156?language=zh&r=1527191)
[RA系列MCU：](https://www2.renesas.cn/cn/zh/products/microcontrollers-microprocessors/ra-cortex-m-mcus)
[CPK-RA6M4 评估板页面：](https://www2.renesas.cn/cn/zh/products/microcontrollers-microprocessors/ra-cortex-m-mcus/cpk-ra6m4-evaluation-board)
[RA系列MCU RT-Thread BSP：](https://github.com/RT-Thread/rt-thread/tree/master/bsp/renesas)
[RA系列RT-Thread驱动介绍：](https://github.com/RT-Thread/rt-thread/blob/master/bsp/renesas/docs/RA%E7%B3%BB%E5%88%97%E9%A9%B1%E5%8A%A8%E4%BB%8B%E7%BB%8D.md)
[RA系列BSP外设驱动使用教程：](https://github.com/RT-Thread/rt-thread/blob/master/bsp/renesas/docs/RA%E7%B3%BB%E5%88%97BSP%E5%A4%96%E8%AE%BE%E9%A9%B1%E5%8A%A8%E4%BD%BF%E7%94%A8%E6%95%99%E7%A8%8B.md)
[RA系列使用 FSP 配置外设驱动](https://github.com/RT-Thread/rt-thread/blob/master/bsp/renesas/docs/RA%E7%B3%BB%E5%88%97%E4%BD%BF%E7%94%A8FSP%E9%85%8D%E7%BD%AE%E5%A4%96%E8%AE%BE%E9%A9%B1%E5%8A%A8.md)


参考文献：
[基于 RT-Thread Studio的CPK-RA6M4 开发环境搭建指南](https://mp.weixin.qq.com/s/phEV5jGjTOoe7Y0ihI6ftg)
