# 六自由度喷涂机械臂

## Status

![stars](https://img.shields.io/github/stars/uav-operation-system/Robotic_Arm_for_UAV.svg) ![forks](https://img.shields.io/github/forks/uav-operation-system/Robotic_Arm_for_UAV.svg) ![tag](https://img.shields.io/github/tag/uav-operation-system/Robotic_Arm_for_UAV.svg) ![release](https://img.shields.io/github/release/uav-operation-system/Robotic_Arm_for_UAV.svg) ![issues](https://img.shields.io/github/issues/uav-operation-system/Robotic_Arm_for_UAV.svg)

## 概览

本代码为2020维源翼高空喷绘无人机机械臂代码。

这是一个[Keil5](http://www.keil.com/)工程，直接导入到Keil5中就可以编译运行。

遥控设备为PS2遥控，六路PWM波输出控制六个舵机，两个电磁铁分别控制抓住功能和控制喷口开启关闭。

## 编写环境

此份代码为Keil5+stm32cubemx所创建的工程

## 硬件资源

主控芯片为stm32f103rct6

![chip](https://github.com/uav-operation-system/Drone_Master_PID/raw/master/chip.png)

|定时器通道|单片机引脚|
|-|-|
|TIM1_CH1|PA8|
|TIM1_CH2|PA9|
|TIM1_CH3|PA10|
|TIM1_CH4|PA11|
|TIM2_CH1|PA15|
|TIM2_CH2|PB3|
 
## 遥控协议

|顺序|DO|DI|Bit0|Bit1|Bit2|Bit3|Bit4|Bit5|Bit6|Bit7
| ------------- |:-------------:| -----:|
|0|0x01|idle|

|1|0x42|ID|  

|2|idle|0x5A|

|3|idle|data|SELECT|L3|R3|START|UP|RIGHT|DOWN|LEFT|

|4|idle|data|L2|R2|L1|R1|△|○|╳|□|

|5|idle|data|PSS_RX（0x00=left、0xFF=right）|

|6|idle|data|PSS_RY（0x00=up、0xFF=down）|

|7|idle|data|PSS_LX（0x00=left、0xFF=right）|

|8|idle|data|PSS_LY（0x00=up、0xFF=down）|
