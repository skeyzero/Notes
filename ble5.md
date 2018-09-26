# CC2640学习笔记
## 定时器   
定时器

## 定时器结构，使用定时器需要顶一个定时器结构，估计用来存储定时器变量用的。
static Clock_Struct         CLK;

##定时器初始化，在Init函数中初始化。

	//定时器初始化
	//CLK		Clock结构体，用于保存相关变量（大概）
	//Fn_CB		回调函数，这里参考例程作用是在回调函数中，在事件队列中

	Util_constructClock(&CLK,Fn_CB,1000,0,false,EVT_TIMEOUT_1S);
   
## 启动定时器，初始化后需要启动定时器，否则定时器不会自动启动
Util_startClock(&CLK);//启动定时器
## 事件处理在simple_peripheral.c的SimpleBLEPeripheral_taskFxn中
	if(events & USR_EVT)
	{
		Util_startClock(&CLK);//启动定时器
		Fn_USRCODE_Handle();
	}