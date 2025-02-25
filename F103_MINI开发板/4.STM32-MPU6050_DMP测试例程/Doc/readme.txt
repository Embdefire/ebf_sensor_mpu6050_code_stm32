/*********************************************************************************************/
【*】程序简介

-工程名称：陀螺仪—MPU6050
-实验平台: 野火STM32 MINI  开发板 
-MDK版本：5.16
-ST固件库版本：3.5

【 ！】功能简介：
使用陀螺仪采集加速度、角速度、姿态角、温度、计步等数据，并上传到“匿名上位机”进行姿态显示。

学习目的：学习陀螺仪的使用。
本工程是移植自MPU6050官方驱动，包含了陀螺仪最完整的功能。

【*】注意事项：
1.本程序必须配合“匿名上位机”使用！！串口向上位机传输的是数据包，所以直接用串口调试助手看是乱码，这是正常的！！

2.MDK工程配置C/C++选项中必须勾选“C99 Mode”选项(本工程默认已勾选，MDK默认不勾选的)



3.MINI开发板由于引脚资源不够，不能使用硬件IIC驱动！

4.MPU6050的AD0引脚接GND时，地址为0x68 ,接3.3V时，地址为0x69，
  
  可在bsp_i2c.h文件修改宏MPU6050_ADDR的值来匹配硬件连接，默认AD0接地，使用0x68地址

   #define MPU6050_ADDR   0x68

【 ！】实验操作：
步骤如下(步骤可参考配套的教程，有图片说明)：

1.按照引脚分配说明连接好MPU6050模块和开发板。

2.确认开发板的USB TO USART接口已与电脑相连，确认电脑端能查看到该串口设备。

3..打开配套资料里的 “匿名上位机”软件，在软件界面打开 开发板对应的串口(波特率为115200)，

把“基本收码”、“高级收码”、“飞控波形”功能设置为on状态。点击上方图中的基本收发、波形显示、飞控状态图标，会弹出窗口。

4.在软件的“基本收发”、“波形显示”、“飞控状态”页面可看到滚动数据、随着模块晃动而变化的波形以及模块姿态的3D可视化图形。


【*】 引脚分配
陀螺仪（MPU6050）：
MPU6050芯片的I2C接口与STM32的I2C1相连,且已接上拉电阻。
		VCC <--->3.3或5V
		GND	<--->GND
		SCL	<--->PA2
		SDA	<--->PA3
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

