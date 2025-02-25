/*********************************************************************************************/
【*】程序简介

-工程名称：陀螺仪—MPU6050
-实验平台: 野火STM32 指南者  开发板 
-MDK版本：5.16
-ST固件库版本：3.5

【 ！】功能简介：
使用陀螺仪采集加速度、角速度、姿态角、温度、计步等数据，
并上传到MPU6050官方的python上位机进行姿态显示。

上位机的使用仅适合用于有python基础的用户。

学习目的：学习陀螺仪的使用。
本工程是移植自MPU6050官方驱动，包含了陀螺仪最完整的功能。

【*】注意事项：
1.本程序必须配合官方的python上位机使用！！串口向上位机传输的是数据包，所以直接用串口调试助手看是乱码，这是正常的！！

2.MDK工程配置C/C++选项中必须勾选“C99 Mode”选项(本工程默认已勾选，MDK默认不勾选的)


3.本工程默认使用软件IIC，使用硬件IIC时不能与液晶屏同时使用，
  
  因为液晶显示的FSMC的NADV与IIC1的SDA 是同一个引脚，互相影响了。
  
  若不用FSMC时，推荐用硬件IIC

  在bsp_i2c.h文件把宏 //#define HARD_IIC  的注释去掉可设置成使用硬件IIC,
  
  还需要关闭液晶显示相关的代码才能正常运行。
  
  在maic.c文件把宏 #define USE_LCD_DISPLAY  注释掉可设置成关闭液晶输出。

4.MPU6050的AD0引脚接GND时，地址为0x68 ,接3.3V时，地址为0x69，
  
  可在bsp_i2c.h文件修改宏MPU6050_ADDR的值来匹配硬件连接，默认AD0接地，使用0x68地址

   #define MPU6050_ADDR   0x68

【 ！】实验操作：

步骤如下(步骤可参考配套的教程，有图片说明)：
若会用户会python语言，
可使用配置资料里的“motion_driver6.12/eMPL-pythonclient”来测试。
在“motion_driver6.12/documentation/《App Note 1 - Motion Driver 6.12 Getting Started.pdf》”有使用方法的介绍。


【*】 引脚分配
陀螺仪（MPU6050）：
MPU6050芯片的I2C接口与STM32的I2C1相连,且已接上拉电阻。
		VCC <--->3.3或5V
		GND	<--->GND
		SCL	<--->PB6
		SDA	<--->PB7
		INT <--->PA11  传感器数据中断引脚
		AD0 <--->悬空或接地
		
串口(TTL-USB TO USART)：
CH340的收发引脚与STM32的发收引脚相连。
	RX<--->PA9
	TX<--->PA10
					


/*********************************************************************************************/

【*】 版本

-程序版本：1.0
-发布日期：2015-10

-版本更新说明：首次发布

/*********************************************************************************************/

【*】 联系我们

-野火论坛    :http://www.firebbs.cn
-淘宝店铺    :https://fire-stm32.taobao.com

/*********************************************************************************************/

