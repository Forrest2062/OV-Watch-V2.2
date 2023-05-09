# OV-Watch-V2.2
Smart Watch, MCU: STM32F411CEU6, UI: LVGL, OS:FreeRTOS 

描述
系统组成
系统框图如下所示，主控使用STM32F411CEU6，操作系统使用FreeRTOS，图形库使用的LVGL。传感器部分：手势识别使用6轴MPU6050；心率血氧使用的是EM7028（没有用MAX30102是因为之前太贵了），EM7028的资料很少，之前自己写的局部寻峰算法来计算心率但是效果不好，现在改成了使用官方的库，后面V2.3版本心率血氧传感器将会改成MAX30102，开发资料也更多；海拔测量用的气压计SPL06-001；电子指南针使用LSM303DLHC；蓝牙使用的HC-04模块，后面V2.3版本可以换成很便宜的国产芯片KT6328A，它开着蓝牙可以实现低功耗，大力推荐。

SxhIWPJrJjfo6wAMFCYGshw6LTLI13lUeqeJ7oPy.png

功能说明
大致功能表如下图所示：

1nxRkoxYs8CVWheAlxerIN9jpB0BQsp5A8p7SIOo.png

1.电源部分：手表使用的是3.7V锂电池，通过TPS63020提供3V3电源，V2.2版本充电口留了两个焊盘，用来接触磁吸充电口。特别注意，V2.0版本使用的无线充电，使用了芯片T3168，但是用无线充电的话，加上线圈和多的器件，体积就非常大了，同时还有散热问题。

 

2.蓝牙部分：现在用的是HC-04（邮票孔封装），后面的版本会改成用国产芯片KT6328A。

 

3.辅助功能部分：计算器：当时做带浮点数的计算器做得很烦，字符串处理很麻烦。现在这个计算器是通过一个数字栈和一个符号栈实现的，具体看代码。

 

4.NFC部分：V2.0版本的IC卡复制器模块介绍详见：https://oshwhub.com/no_chicken/ICka-fu-zhi-qi

在V2.2版本中，为了精简减小体积，仅有UID卡，可以被外部读卡器读写。而在V2.0版本中，用的是RC522和一张UID卡组成的，可以自行复制外部IC卡，然后也可以被外部读卡器读写如下图所示：

EBK7PmpgIULRS9Smr1n5sKSRgqPzzkDldXgD88er.png

 

硬件设计说明
PCB分为两个板，一个Core板，一个Back板，Back板包括了传感器部分和蓝牙模块。

 
UI界面、实物图片
部分界面图：

6UTyGvATttKbdoJQoOHAXlvzlXhNxyM4cSZhLry9.png

实物图：

l61P4SN4I9gB3B4Jfw5HDjwtPRld3WAiwCIqGxV0.jpegcykp1oyM0wHCcGNV79PtPsDrTD49cXmCbvBX38a6.png

 

 
注意事项
焊的时候很烦，0402太小了，热风qiang吹的时候尽量用高温小风，免得把器件吹走了。
