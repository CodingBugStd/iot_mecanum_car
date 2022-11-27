# 物联网全向移动平台

## 一、需求

1. 具备全向移动的能力
   - 高精度速度闭环
     - 低速时速度数量级>=100x衡量单位
     - 测速频率>=100Hz
     - 高动态响应
   - mecanum运动学模型正逆解
   - 坐标系转换
   - 运动积分
2. 姿态闭环
   - 航向角位置闭环
     - yaw误差不超过0.5°
     - 零漂补偿
     - 地磁传感器+陀螺仪

3. 上云
   - 能使用wifi热点上云
     - 腾讯云 or 阿里云
   - 能直接与上位机通过mqtt协议通讯
   - 能通过web端控制小车

## 二、硬件设计

### 1、控制电路

主控：stm32f103vet6

> - 具备4路编码器输入捕获
> - 4路10kHz 2000分辨率 可调脉宽pwm输出 -> 电机控制信号
> - 1路2~300kHz可调频率pwm通道 -> 蜂鸣器
> - 三路串口
>   - 与esp32c3通讯
>   - 与板载ch340连接usb用于调试
>   - 保留
> - 一路i2c
>   - 连接陀螺仪
>   - 连接磁力计
> - 一路支持DMA的SPI接口
>   - ssd1306显示
> - 两路支持DMA的ADC接口
>   - ADC键盘
>   - 电池电压检测







1. 主控:stm32

   - 具备4路编码器输入捕获
   - 4路10kHz 2000分辨率 可调脉宽pwm输出 -> 电机控制信号
   - 1路2~300kHz可调频率pwm通道 -> 蜂鸣器
   - 三路串口
     - 与esp32c3通讯
     - 与板载ch340连接usb用于调试
     - 保留
   - 一路i2c
     - 连接陀螺仪
     - 连接磁力计
   - 一路spi 支持DMA
     - ssd1306显示

2. 上云从机:esp32c3

   - 两路串口
     - 与主控通讯
     - 板载ch340用于程序下载烧录以及debug
   - 扩展spi flash

3. TB6612FNG SOP24  X 2

4. AMS1117 - 3.3 线性稳压IC

5. LM317KTTR TO-263-3 稳压IC X 2 -> TB6612FNG供电

6. CJMCU-008 3轴磁力计模块

7. mpu6050模块

8. 无源蜂鸣器电路

9. 5V供电电路

10. ADC键盘

11. ch340 X 2

    
