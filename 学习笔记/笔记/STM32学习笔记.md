---
updated: 2026-05-11 15:33:44
focused: 00:01:47
---

# STM32的基本介绍

- STM32
  
    - st：意法半导体公司，M表示微控制器（微控制一般包括处理器、RAM、外设和IO口等等）
    
    - 32：表示32位的微控制器，支持的最大内存为2^32字节，大概等于4GB。

- STM32和ARM的关系
    - ARM公司拥有芯片内核设计的专利，它将芯片内核的专利向其他厂商进行授权，由其他厂商依据芯片内核和总线、RAM、IO、其他外设等设计成可以直接使用的芯片，其他厂商：英特尔、ST、华为、三星等等。

- ARM特点
  
    - 低功耗、低成本、高性能
    
    - 支持16位、32位的指令集

- ARM内核体系
  
    - A：特高性能，一般用在手机、平板、无人机
    
    - R：较高性能，一般用在军工行业、汽车行业等
    
    - M：低性能，一般工业控制、工厂智能控制系统等等

- 官方网站中的不同的STM32型号介绍
  
    - 图示![](https://api2.mubu.com/v3/document_image/4733041_0d094433-8d2c-45c4-eedb-715868373833.png?)
    
    - MCU（微控制器）：继承了CPU、内存和外接接口等等，位于一个芯片上，用于特定额度控制应用，比如管理洗衣机的功能、控制机器人的具体操作等等
    
    - MPU（微处理器）：通常指的是中央处理单元，负责的是指令和数据的处理，需要依赖于外部接口实现具体的操作

- STM32F103C6T6
  
    - STM32的型号代表的含义![](https://api2.mubu.com/v3/document_image/4733041_7d5c9c51-b78c-464d-c430-1fe490d687c2.png?)
    
    - F1系列采用的封装方式LQFP（引脚按照顺序只在边上出现），而BGA封装方式按照矩阵进行排列（和电脑CPU一样）

- STM32F103系列芯片的系统架构图，如下
  
    - 图示![](https://api2.mubu.com/v3/document_image/4733041_4965ddc4-962f-48e7-99fe-3930b4c5e87a.png?)
    
    - 中文参考手册中详细描述了STM32F103芯片的元器件的关系情况![](https://api2.mubu.com/v3/document_image/4733041_e896c8e7-bc55-405d-b7ac-6dc1a53cbd31.png?)
      
        - FLASH接口单独使用ICode总线是为了提高访问效率
        
        - DMA：数据搬运总线
        
        - AHB系统总线连接在总线矩阵上，而APB1和APB2连接在AHB总线上
        
        - 芯片手册上也说明STM32F1系列的工作电压为2V~3.6V（低电平是0V，高电平3.3V）
    
    - STM32的芯片阵脚介绍
      
        - 图示![](https://api2.mubu.com/v3/document_image/1f29efd8-d72f-4873-b0f9-378303725e01-4733041.jpg?)
        
        - 电源引脚：V开头的都是电源引脚，VDD(VCC)电源正极，VSS(GND)电源负极
        
        - GPIO引脚：P开头都是IO引脚
            - 可以使用该引脚进行输入和输出
        
        - 启动引脚：BOOT引脚
          
            - STM32的启动方式![](https://api2.mubu.com/v3/document_image/4733041_38de72d5-0fb7-42d4-ff0f-d8f4aa7f7041.png?)
            
            - BOOT1=X（0或者1）、BOOT0=0，表示STM32以flash的方式进行启动
                - 我们提供的开发板BOOT0和BOOT1都是接在了GND上，因此使用的是FLASH的方式启动的
            
            - BOOT1=0，BOOT0=1：以内置存储方式启动
            
            - BOOT1=1，BOOT0=1：以SRAM方式启动
        
        - 晶振引脚：OSC开头的都是晶振引脚
          
            - OSC32引脚代表外接32.768KHz的晶振源引脚，而OSC一般外接8MHz的晶振引脚
            
            - OSC引脚提供的时钟称为外部时钟
        
        - 复位引脚：NRST
        
        - STM32的程序下载方式
            - 由于我们的开发板提供串口和SWD（JTAG）下载，我们使用的是SWD方式，ST-LINK提供了可以将数据通过SWD接口下载至flash的操作
        
        - STM32的电源
          
            - 开发板使用USB1和SWD接口供电，如果要使用USB1需要使用降压模块，将电压降低到3.3V
            
            - 注意点：一般不要给板子外接多种电源，可能会造成电压超负荷。
        
        - STM32的最小系统
          
            - 可以让单片机工作的最小可使用外设叫做最小系统
            
            - 最小系统包括：电源电路、晶振电路、下载电路、复位电路。
                - 复位电路
                  
                    - 板载K1按键为复位按钮，按下K1按键板子会进行复位，加载新的flash数据。
                    
                    - 复位电路在刚开始给板子上电的时候会自动触发，完成复位

# HAL库的基本介绍

- ST公司按照CMSIS标准先后设计标准库和HAL库，HAL库目前使用比较多的STM32的开发方式

- 文件夹介绍
  
    - _htmresc：存放的ST公司的LOGO图标
    
    - Documentation：存放HAL库帮助文档，主要讲的是如何使用驱动库来编写自己的应用程序
    
    - Drivers：这个文件夹中有三个目录，BSP目录用于存放ST官方样板板载外设驱动，CMSIS目录用于存放符合CMSIS标准的文件，包括STM32的启动文件、DSP库文件、ARM Cortex内核文件、RTOS操作系统文件
      
        - CMSIS中必须用到的四个文件![](https://api2.mubu.com/v3/document_image/4733041_4bbe70be-96f6-45e4-a17c-616d53f40f94.png?)
        
        - core_cm3.h文件主要是处理一些与编译器相关的条件编译语句，用于屏蔽不同的编译器的差异
        
        - 下面这个文件主要是启动文件，比如一些比较重要的内容，如中断向量表就是存放在此文件中![](https://api2.mubu.com/v3/document_image/d80a4dd3-4f84-454d-9288-9a4cd64f225a-4733041.jpg?)
        
        - stm32f1xx.h
            - 在stm32中如果要使用任何外设，必须要引入此头文件，stm32芯片对应的寄存器的映像就存放在此目录中，也有很多的宏定义。
        
        - stm32f1xx_it.c
            - 中断服务函数存放在此文件中
    
    - Middlewares：存放一些中间件文件
    
    - Projects：存放的是驱动库编写的针对官方发行demo板的例子和工程文件
    
    - Utilities：ST官方评估板的一些源文件。

# HAL库实现STM32的程序

## 点亮LED灯

- GPIO的介绍

- STM32的GPIO的介绍，GPIO是通用输入输出端口的简称，可以通过软件来控制其输入和输出高低电平。

- GPIO结构框图
    - 图示![](https://api2.mubu.com/v3/document_image/4733041_dffb3301-f4a9-4057-9e0d-cef6ecf0d9f9.png?)![](https://api2.mubu.com/v3/document_image/4733041_eb9a76da-ef73-4393-bd06-58ed6fbdb99d.png?)

- 输入部分
  
    - 图示![](https://api2.mubu.com/v3/document_image/4733041_93ad3d6b-3969-46c9-8f91-7cc7990b7c61.png?)
    
    - 保护二极管
      
        - 使用半导体材料，单向导电
        
        - 当接入高电平的时候，如果超过了正常电平的情况，会通过VDD将多余电压分流到上部，保护流入芯片的电压是3.3V左右
        
        - 当接入低电平的时候，如果有低于0V的电平的情况，通过VSS将负电平阻止在芯片外部，起到保护芯片的作用
        
        - 注意：当接入的电平过高，也不能直接依赖二极管来保护，因为它是弱保护，一般只能保护小范围的电平浮动
    
    - 上拉电阻
        - 可以将电平上拉成高电平，主要是在IO空闲的时候确定状态，因为IO空闲时外部是高阻态的情况（不知道是高电平还是低电平），主要用于IO口的初始化
    
    - 下拉电阻
        - 可以将电平下拉成低电平，主要是在IO空闲的时候确定状态，因为IO空闲时外部是高阻态的情况（不知道是高电平还是低电平），主要用于IO口的初始化
    
    - 肖特基触发器
      
        - 将不规律的波形转化为规律的方波
        
        - 特点
          
            - 当输入的电压高于正向阈值的时候，输出为高
            
            - 当输入的电压低于负向阈值的时候，输出为低
            
            - 当输入的电压在正向和负向阈值之间，输出保持不变

- 输出部分
  
    - 图示![](https://api2.mubu.com/v3/document_image/4733041_0ec47b1e-8432-4523-e4fe-9ef455b4623e.png?)
    
    - P-MOS（N-MOS）管的导通条件为进入P-MOS（N-MOS）管电压和VDD（VSS）不一致

- 八种工作模式
  
    - 通用的输入模式
      
        - 输入浮空
            - 输入浮空就是既不上拉也不下拉，MOS管不导通，肖特基触发器打开，可以认为输入到IDR寄存器的电平是不确定（高阻态），这种模式一般不使用
        
        - 输入上拉
            - 输入上拉指的是上拉电阻接通，肖特基触发器打开，输出被禁止，IO空闲的时候如果要向IDR写入高电平，使用上拉电阻
        
        - 输入下拉
            - 输入下拉指的是下拉电阻接通，肖特基触发器打开，输出被禁止，IO空闲的时候如果要向IDR写入低电平，使用下拉电阻
    
    - 通用输出
      
        - 开漏模式输出
          
            - 只有N-MOS管导通，P-MOS是不工作的，ODR输出0的时候，通过输出控制器反向为1，N-MOS管就导通、向外输出低电平。如果ODR输出的是1，会被反向为0，N-MOS不导通。
            
            - 图示![](https://api2.mubu.com/v3/document_image/4733041_7b2c2f50-1a04-41b7-e55a-19df987d3fee.png?)![](https://api2.mubu.com/v3/document_image/4733041_aed8b4e4-32e3-4de2-b097-963d1dbd57ba.png?)
        
        - 推挽模式输出
          
            - 推挽模式下，P-MOS和N-MOS都可以工作，当ODR寄存器输出低电平的时候，反向为1，N-MOS管导通，向外输出低电平，如果ODR寄存器输出高电平的时候，反向为0，P-MOS管导通，向外输出高电平。
            
            - 图示![](https://api2.mubu.com/v3/document_image/4733041_869469bf-89c9-4df3-f0f1-645b93ba3558.png?)
    
    - 复用输出
      
        - 复用输出和通用输出的唯一区别在与电平信号的来源方便，复用功能的信号来自于片上外设，对于通用输出来说，信号来自于ODR
        
        - 复用开漏
            - 只有N-MOS管导通，P-MOS是不工作的，复用功能输出0的时候，通过输出控制器反向为1，N-MOS管就导通、向外输出低电平。如果复用功能输出的是1，会被反向为0，N-MOS不导通。
        
        - 复用推挽
            - 推挽模式下，P-MOS和N-MOS都可以工作，当复用功能输出低电平的时候，反向为1，N-MOS管导通，向外输出低电平，如果复用功能输出高电平的时候，反向为0，P-MOS管导通，向外输出高电平。
    
    - 模拟输入
      
        - 模拟输入的模式相爱上下拉电阻不使用、输出电路被禁止，肖特基触发器关闭
        
        - 模拟输入只有ADC和DAC上会使用

- LED灯的点亮
  
    - 电路图![](https://api2.mubu.com/v3/document_image/4733041_63663b5b-ed6c-4d46-a5eb-53268b855a54.png?)
    
    - 上图是板载LED的电路图，用PB5、PB6、PB7分别控制led2、led3、led4这三个灯，如果要让LED灯点亮，就需要给PB引脚输出高电平。

- GPOI的基本配置步骤
  
    - 1、使能时钟
        - __HAL_RCC_GPIOx_CLK_ENABLE(); // 其中x代表要选择哪一个GPIO口来操作，当前电路板上的LED使用PB组的引脚，所以这个函数应该写成
            - __HAL_RCC_GPIOB_CLK_ENABLE();
    
    - 2、设置GPIO口的工作模式（初始化）
        - 函数是HAL_GPIO_Init();
            - 参数有两个
              
                - GPIO_TypeDef *GPIOx，确定使能哪一组GPIO引脚
                    - 比如GPIOA、GPIOB等
                
                - GPIO_InitTypeDef *GPIO_Init
                  
                    - uint32_t Pin：选择相应的GPIOpin脚
                    
                    - uint32_t Mode：选择GPIO的工作模式
                    
                    - uint32_t Pull：设置当前引脚的上下拉
                    
                    - uint32_t Speed：设置速率，一般只在输出的时候设置
                      
                        - 低速模式：适用LED、按键、低速传感器等等简单的数字信号，无需快速响应
                        
                        - 高速模式：用于SPI、I2C、USART等外设需要高频的电信号，确保信号边沿满足时序要求
                        
                        - 速率的设置越高，代表GPIO驱动电路的响应速度越快，信号的跳变速度越快，跳变的边沿更加陡峭（即上升/下降的时间更短）。
    
    - 3、设置GPIO输出电流状态
        - HAL_GPIO_WritePin();
          
            - GPIO_TypeDef *GPIOx：确定是哪一组GPIO引脚
            
            - GPIO_Pin：确定具体是哪一个pin脚
            
            - GPIO_PinState PinState：确定向引脚中写入0（低电平）还是1（高电平）
              
                - GPIO_PIN_SET：高电平
                
                - GPIO_PIN_RESET：低电平
    
    - 代码演示
      
        - 文件路径![](https://api2.mubu.com/v3/document_image/4733041_0a91bb57-8636-4eab-f0b6-107ded41782a.png?)
        
        - 将路径添加到项目中![](https://api2.mubu.com/v3/document_image/4733041_3e66d95e-fa51-455c-c2de-a2a43d6a4e40.png?)
        
        - 在工程中创建Module部分，添加led.c文件![](https://api2.mubu.com/v3/document_image/4733041_c5d88fd2-6dc1-4815-b7e8-2848852fffbd.png?)
        
        - 在led.c中引入led.h后进行编译，即可将led.h挂载到led.c文件下![](https://api2.mubu.com/v3/document_image/4733041_8fc0b84a-a84c-49b6-e38f-29fcd220fbcb.png?)
        
        - led.h![](https://api2.mubu.com/v3/document_image/005e3fa4-a525-4386-ba61-d64a684b4ad2-4733041.jpg?)
        
        - led.c![](https://api2.mubu.com/v3/document_image/4733041_aacdffb0-1c78-4feb-acfc-70850b24eedf.png?)
        
        - main.c![](https://api2.mubu.com/v3/document_image/4733041_e795c4ff-941f-412b-f99f-5b08ac012fd7.png?)

## 蜂鸣器实现

- 蜂鸣器的基本介绍
  
    - 有源蜂鸣器
        - 表示蜂鸣器内部是自带震荡源的，可以为蜂鸣器提供一个震荡信号，可以理解为蜂鸣器工作的频率。
    
    - 无源蜂鸣器
        - 内部是没有震荡源的，可以设置其工作频率，因此可以模仿不同的声音，比如救护车、警车等等。

- 三极管
    - 三极管分为PNP三极管和NPN三极管
      
        - 三极管有：基极、集电极和发射极
        
        - NPN类型![](https://api2.mubu.com/v3/document_image/4733041_e4675fc6-71cc-4e68-9d66-04b3a58fc590.png?)
            - NPN类型三极管的导通条件是b极电压要高于e极电压0.7v，此时C极和b极电流都可以流向e极
        
        - PNP类型![](https://api2.mubu.com/v3/document_image/4733041_3867ec8e-0467-4b3e-a2c1-9c938cd3d574.png?)
            - PNP三级管的导通条件是e极电压要高于b极电压0,7v，此时e极和b极的电流都可以流向c极

- 蜂鸣器的硬件设计电路图
  
    - 图示![](https://api2.mubu.com/v3/document_image/4733041_448aba8d-97cd-4f16-e21f-eda457bd3c74.png?)
    
    - 根据STM32F1芯片手册，知道单个IO口最大输出电流是25mA，而蜂鸣器的驱动电流是30mA，虽然看起来可以直接用IO口来驱动，但是电路并未这样设计，原因是芯片的整个输出电流，最大是150mA，那么最多用6个IO口都输出25mA的电流，会将电流使用枯竭，所以一般IO口只做控制，不做驱动，驱动的电流是直接从板子的电源来获取的。

- beep.h![](https://api2.mubu.com/v3/document_image/f312d2e2-cec7-4787-a76c-8999c1e5e2f5-4733041.jpg?)

- beep.c![](https://api2.mubu.com/v3/document_image/4733041_fc68da8a-4cfd-4415-931c-899c1ea21acf.png?)

- main.c![](https://api2.mubu.com/v3/document_image/4733041_678b61f6-0dc7-4eaf-f89d-ef7db30a5e19.png?)

## 火焰传感器

- 图示![](https://api2.mubu.com/v3/document_image/4733041_afb80160-2409-41d6-ae37-a410b70a88a7.png?)

- 电路图![](https://api2.mubu.com/v3/document_image/4733041_3dceb624-f4f8-4eb5-b0a2-4b9e504b4211.png?)

- 火焰传感器是一种常用检测特定波长（760nm~1100nm）的红外光传感器，探测角度60°左右，对火焰光比较敏感，传感器的灵敏度可以调节。对火焰的探测距离与灵敏度和火焰强度是有关系的，一般在1米以内，有比较强的适用性，主要用于工业自动化、安全监控、消防预警等领域。

- 此模块有4个引脚分别是
  
    - VCC：电源引脚
    
    - GND：接地引脚
    
    - AO：模拟信号线（不用）
    
    - DO：数字信号线

- 此火焰模块在没有火焰的时候，DO引脚输出高电平，如果有火焰输出低电平，此时OD-LED灯会点亮。

- 顺时针拧的时候，可以增加灵敏度，逆时针会减小灵敏度。

- 代码演示
  
    - fire.h![](https://api2.mubu.com/v3/document_image/cf51c519-340f-4a17-b568-9be66aa3e9a8-4733041.jpg?)
    
    - fire.c![](https://api2.mubu.com/v3/document_image/4733041_8c59c33f-0700-4611-986c-9d3d7c7b3cef.png?)
    
    - main.c![](https://api2.mubu.com/v3/document_image/4733041_89d4abf0-4ba8-42f2-ab85-b4b72c96de2f.png?)

## STM32时钟系统

- STM32的时钟树
  
    - 时钟是具有周期性的脉冲信号，它可以为单片机提供一个稳定的机器周期从而让系统可以正常运行，使用任何外设之前必须要先使能时钟。
    
    - 图示![](https://api2.mubu.com/v3/document_image/3c0d02e5-c1d4-479d-a216-be5ef8912d9c-4733041.jpg?)
    
    - 解释说明
      
        - 名词解释：H：height、L：Low、S：speed、I：internal、E：external
        
        - HSE：高速外部时钟信号
            - 高速外部晶振，外部晶振是需要在开发板上外接晶振源的，板载无外接晶振的，一般外部晶振用石英、陶瓷等材料制作，基本没有误差。
        
        - LSE：低速外部晶振
        
        - HSI：高速内部晶振
            - 内部晶振在芯片内部，由ST公司自己设计好的电路，内部晶振实际使用是RC振荡器，RC振荡器对于频率的设置不是特别准确。
        
        - LSI：低速内部晶振
        
        - PLL：锁相环
          
            - 锁相环是一种用于比较输入和输出信号的反馈系统。
            
            - 锁相环主要在开发板中用于倍频操作
            
            - 锁相环一般包括鉴相器、滤波器、压控震荡器。
        
        - PLL选择器频率可以由HSI的2分频来提供，也可以由HSE的1分频或者2分频得到
        
        - 系统时钟（SYSCLK）可以由HSI、HSE、PLLCLK提供
        
        - AHB总线一般由SYSCLK的1分频得到的，APB1是由AHB总线上的2分频得到，APB2由AHB总线上的1分频得到
        
        - CSS时钟安全系统：如果检测到HSE时钟异常信号，则时钟系统CSS会自动将系统时钟源选择为HSI

- 时钟配置步骤
  
    - 由于开发板之后内部振荡器，所以直接使用HAL配置即可
    
    - 1、选择时钟源，配置PLL
        - HAL_RCC_OscConfig()函数，需要一个结构体指针，结构体的名称是RCC_OscInitTypeDef，其中的成员有
          
            - OscillatorType：选择需要配置的振荡器
            
            - HSEState：HSE的状态
            
            - HSEPredivValue：HSE的预分频系数
            
            - LSEState：LSE的状态
            
            - HSIState：HSI的状态
            
            - HSICalibrationValue：HSI的校准值，使用默认值即可RCC_HSICALIBRATION_DEFAULT
            
            - LSIState：LSI的状态
            
            - RCC_PLLInitTypeDef PLL
              
                - PLLState：锁相环的状态
                
                - PLLSource：PLL的时钟源
                
                - PLLMUL：PLL的倍频系数
    
    - 2、选择系统时钟源，配置总线分频器
        - HAL_RCC_ClockConfig()
          
            - 参数1：RCC_ClkInitTypeDef *RCC_ClkInitStruct
              
                - ClockType：要配置的时钟类型
                
                - SYSCLKSource：系统时钟源
                
                - AHBCLKDivider：AHB总线时钟预分频系数
                
                - APB1CLKDivider：APB1总线时钟预分频系数
                
                - APB2CLKDivider：APB2总线时钟预分频系数
            
            - 参数2：FLatency，指的是等待周期，因为FLASH的频率是24MHz，所以CPU的频率就决定了是否需要等待Flash，可以参考下面的等待周期说明![](https://api2.mubu.com/v3/document_image/5f1f685d-2dea-497a-bc3c-656e9ae360b2-4733041.jpg?)
                - 因此我们芯片的SYSCLK是64MHz，所以应该等待2个周期，所参数值就是：FLASH_LATENCY_2（2个等待周期）
                    - FLASH_LATENCY_0（0个等待周期）和FLASH_LATENCY_1（1个等待周期）都可以进行配置

- 代码演示
  
    - sysclk.h![](https://api2.mubu.com/v3/document_image/e8d60abf-732f-43f6-bbf0-e95475af6edf-4733041.jpg?)
    
    - sysclk.c![](https://api2.mubu.com/v3/document_image/4733041_9225adf8-b5db-4301-fa1a-a2f8c0972f38.png?)

## 系统滴答定时器（SysTcik）

- 概念
  
    - 属于M3内核的一个外设，是一个24位（2^24 - 1 = 16777215）的向下计数的定时器，当计数器计算到0的时候结束一次定时操作，因为HAL库没有提供SysTick的相关操作函数，所以需要使用寄存器来直接操作。
    
    - 由时钟树可知，systick时钟源来自于AHB总线的8分频得到的，就是8MHz。
    
    - 基本运行原理![](https://api2.mubu.com/v3/document_image/4733041_1d220dc2-531d-4818-bb38-f71c53ad004d.png?)

- SysTick定时器寄存器
  
    - 寄存器的信息在Cortex-M3 权威指南（134页）
    
    - CTRL寄存器
      
        - 图示![](https://api2.mubu.com/v3/document_image/4733041_358f09fd-8155-4065-e8d4-f99c4decbc91.png?)
        
        - 解释
          
            - COUNTFLAG是标志位，用来确定systick定时器是否计数结束，如果一轮计数完成，就置为1，否则为1。
            
            - CLKSOURCE选择systick时钟源，如果该位为1，表示其时钟是由系统时钟直接提供，64MHz，如果选择是0，代表是由系统时钟8分频得到的64/8MHz
            
            - TICKIN，如果是1表示systick的值到0的时候触发中断定时器，目前还不需要设置，这位也为0
            
            - ENABLE：该位为1代表对其进行使能，该位为0代表对其进行失能
    
    - LOAD寄存器，重装载寄存器
      
        - 图示![](https://api2.mubu.com/v3/document_image/4733041_7313d834-b477-4c1e-ff58-7b11596bb8c0.png?)
        
        - 解释
            - 因为是一个24位向下递减的计数器，所以重装载寄存器只使用低24位，即0~23bit。当系统复位的时候，其值为0，每次VAL=0的时候，会从LOAD寄存器中将值装载到VAL寄存器，开始进行计数。
    
    - VAL寄存器，当前数值寄存器
        - 图示![](https://api2.mubu.com/v3/document_image/4733041_4d9fa4ed-d8b9-4887-c21d-a5495051bb65.png?)

- SysTick定时器操作步骤
  
    - systick定时器的初始化
        - 主要设置systick定时器的时钟源：HAL_SYSTICK_CLKSourceConfig();
    
    - 设置延时函数delay_us()
      
        - 设置SysTick定时器的重装载初始值（SysTick->LOAD）
        
        - 清零SysTick定时器当前计数器的值（SysTick->VAL）
        
        - 打开SysTick定时器（SysTick->CTRL）
    
    - HAL库中有函数可以直接翻转相应引脚的电平值
        - 例![](https://api2.mubu.com/v3/document_image/4733041_79b42d1a-4af4-4457-ca3e-461ea4085b1f.png?)

- 代码演示
  
    - systick.h![](https://api2.mubu.com/v3/document_image/4733041_6d2779e3-660d-4c4e-8753-de528abc00e4.png?)
    
    - systick.c![](https://api2.mubu.com/v3/document_image/4733041_8ef2057e-808b-4250-8e98-599d4f176f3e.png?)
    
    - mian.c![](https://api2.mubu.com/v3/document_image/4733041_f612df07-598f-451f-aaa3-cc58749ac757.png?)

## 独立按键

- 按键介绍
  
    - 按键是一种电子开关，使用的时候按下按键就能接通电源，变成低电平，抬起的时候会变成高电平，板载有四个独立按键。
    
    - 图示![](https://api2.mubu.com/v3/document_image/4733041_fb993868-2204-45c9-d6c5-e12cb3015256.png?)
    
    - 按键管脚两端比较长的1-3,、2-4默认是导通状态，距离短的是1-2、3-4是断开状态，如果按下按键的时候，初始的导通变为断开，初始的断开变为导通，通常按键所用开关是机械开关，接触和断开的时候就会出现抖动的情况。
    
    - 按键按下和抬起的情况：![](https://api2.mubu.com/v3/document_image/f4a91b21-d364-4095-9fd2-75776d25331f-4733041.jpg?)
    
    - 由于机械开关的弹性作用，按键在开关和闭合的时候不会马上接通，在按下的时候一般会有10ms-15ms左右的延时，按键稳定闭合的时间长短由操作人员手动控制，当抬起的时候也需要经历相同时间的抖动，所以为了确保一次抖动只判断一次，需要消抖。
    
    - 消抖的方式一般由两种，一种是硬件消抖，一种是软件消抖，我们经常使用软件消抖（采用延时跳过抖动的时间段，再次判断电平的情况即可）

- 独立按键电路图![](https://api2.mubu.com/v3/document_image/4733041_c96681c2-5cf7-451f-fe6e-f0574cb8ec33.png?)

- 代码演示
  
    - key.h![](https://api2.mubu.com/v3/document_image/d197857f-30f6-49eb-9b89-015875c493a5-4733041.jpg?)
    
    - key.c![](https://api2.mubu.com/v3/document_image/4733041_27121e66-806a-4a49-c9c4-4a50259c0750.png?)![](https://api2.mubu.com/v3/document_image/4733041_cc1678dc-7035-4a78-a68d-dd16dfd3ce23.png?)
    
    - main.c![](https://api2.mubu.com/v3/document_image/4733041_181951ca-b569-4e55-a420-18ebf7b4f601.png?)

## 继电器

- 概念
    - 通过小电流来控制大电流的一种电控开关，广泛应用于自动控制系统，安全保护系统灯场景，工作原理：当继电器线圈通电的时候，线圈中的铁芯产生电磁力，吸动衔铁使3、4触点断开，3、5触点链接，当线圈断电之后，3、4触点链接、3、5触点断开，达到控制继电器是否通电的效果。

- 继电器电路图
  
    - 图示![](https://api2.mubu.com/v3/document_image/4733041_743ce7f0-2201-451b-9078-81185d447ed1.png?)
    
    - 这里是NPN三极管，需要PB4高电平，才能让电路导通
    
    - 烧录的时候需要外接3.3v电压，但是板子运行代码时候，操作继电器需要外接5V的电压。
    
    - 因为PB4被占用，所以需要引脚重映射，也就是引脚复用（AFIO）
      
        - 图示![](https://api2.mubu.com/v3/document_image/724aad80-f8da-4af7-9d0a-23dce61cc8b7-4733041.jpg?)
        
        - HAL库函数可以分别设置以上四种情况![](https://api2.mubu.com/v3/document_image/4733041_150ffc49-1301-4036-a14c-b38d65cb6aa2.png?)

## 声音传感器

- 图示![](https://api2.mubu.com/v3/document_image/4733041_c7001144-b93a-4ef2-f33d-7873a1fb5fd9.png?)

- 简介
  
    - 声音传感器内部是由一个对声音敏感的电容式驻极话筒，声波使话筒内的驻极体薄膜产生震动，导致电容发生变化，从而产生微小的电压，实现声音的检测。
    
    - 声音传感器内部有一个驻极话筒，当顶部的薄膜接收到声波，开始震动的时候，会导致电容发生变化，因为电荷的大小是不变的，所以会导致电压增大，这个原理是根据Q=CU（Q电荷、C代表电容、U代表电压），当有声音的时候会导致C变小，U变大，按理说应该向外输出高电平，在设计的电路中将其反向为低电平，所以对于我们这个检测声音的外设来说，低电平就是获取到声音。

- 电路图![](https://api2.mubu.com/v3/document_image/4733041_9d14f88e-2aed-40ab-f537-f79c4e70d5e3.png?)

- 如果检测到声音就让蜂鸣器响2s，没有声音就让蜂鸣器不响

- 代码演示
  
    - voice.h![](https://api2.mubu.com/v3/document_image/654ceb87-421b-4a21-917c-c5042d4e5fe4-4733041.jpg?)
    
    - voice.c![](https://api2.mubu.com/v3/document_image/4733041_2e614a07-afba-4620-d16c-eebfd742a314.png?)
    
    - main.c![](https://api2.mubu.com/v3/document_image/4733041_5ed9edde-6e8a-4bd5-8fec-28a839a34b9c.png?)

## 中断

- 简介
  
    - 主程序运行的时候，CPU接到更加紧急的任务而停止当前正在执行的任务，继而执行新任务，当新任务执行完成以后，必须返回继续执行主程序的任务的过程。
    
    - 中止：中止和中断不一样的是停止当前任务后不再继续执行原任务。

- 中断分类：内核中断和外部中断。

- NVIC基本概念
  
    - NVIC（Nested Vectored Interrupt Controller）嵌套向量中断控制器，NVIC可以认为是中断管理者，所有的中断必须要经过NVIC来进行处理。
    
    - NVIC支持256个中断（16个内核中断和240外部中断）和256个中断优先级（多个中断同时出现的时候，根据优先级来确定先执行哪个中断）
      
        - F1系列有70个中断（10个内核中断和60个外部中断）
        
        - 对于具体系列所能支持的中断，可以在启动文件中找到（启动文件中的第60行能看到相关中断向量表）
    
    - 中断服务函数
      
        - 所有的中断要经过NVIC来进行处理，但是NVIC是要通过中断服务函数来启动中断。
        
        - 中断服务函数是放在中断向量表中，这样方便使用中断向量表来找到对应的中断服务函数
            - 中断向量表中存放的就是中断服务函数的起始地址
    
    - NVIC作用图![](https://api2.mubu.com/v3/document_image/4733041_dc3c6fc1-7073-4d85-b561-769bf84cf1bb.png?)

- 中断的优先级分配
  
    - 抢占优先级
      
        - 抢占优先级越高，就意味着可以刚早的执行，抢占优先级高（数字越低越高）的可以打断抢占优先级低的任务。
        
        - 抢占优先级是具有绝对的优先性的。
    
    - 响应优先级
        - 如果抢占优先级相同，就应该设置响应优先级，响应优先级越高的（数字越小越高）越先执行，如果有一个低响应优先级的任务在执行，此时有一个高响应优先级的任务触发，不能打断低优先级的任务
    
    - 自然优先级
        - 如果多个中断进入到NVIC中，但是抢占优先级和响应优先级都一样，此时就需要使用中断向量表中的顺序来执行，在表中越靠前的中断先执行

- 中断优先级的分组
  
    - 分组0
        - 0位抢占优先级，4位响应优先级
    
    - 分组1
      
        - 1位抢占优先级，3位响应优先级
        
        - 抢占优先级可以设置为：0或者1、响应优先级可以设置为：0~7
    
    - 分组2
        - 2位抢占优先级，2位响应优先级
    
    - 分组3
        - 3位抢占优先级，1位响应优先级
    
    - 分组4
        - 4位抢占优先级，0位响应优先级

- EXTI中断
  
    - EXTI（External interrupt/event Controller）外部中断事件控制器，EXTI可以检测指定的IO口的电平情况，当指定的IO的电平发生变化的时候，就可以从EXTI向NVIC发送中断申请
    
    - 中断事件和事件
      
        - 中断事件：可以引发中断的事件，叫做中断事件，比如用EXTI检测IO的变化等。
        
        - 事件：事件不经过NVIC来处理，因此事件也不一定要经过CPU，一般连接在其他外设上，事件是包含中断事件的。
    
    - EXTI其实就是中断的触发源选择器

- EXTI的工作原理
  
    - 图示![](https://api2.mubu.com/v3/document_image/4733041_a8e2b9aa-2e35-4d0e-edce-7a440e97d494.png?)
    
    - 第一部分：边沿检测
      
        - 上升沿：从低电平跳变到高电平的瞬间过渡过程
        
        - 下降沿：从高电平跳变到低电平的瞬间过渡过程
        
        - 输入线可能会收到来自IO口的电平的变化值，进入到边沿检测电路，上面挂载了两个边沿检测寄存器，一个上升沿寄存器和一个下降沿触发选择器，当我们将上升沿触发选择器对应的位段置为1，就允许输入线进入的低变高的信号从边沿检测电路通过，如果没有将对应的位段置为1，就不允许上升沿信号通过，下降沿触发选择器也是同样的道理。
    
    - 第二部分：软件触发
        - 可以依赖软件中断事件寄存器来实现通过软件直接触发中断，如果将软件中断事件寄存器中对应的位段设置为1，就可以直接将中断信号向后传递，因为软件中断事件寄存器下面挂了一个或门，所以就算没有输入线没有任何的输入电流，也可以直接通过软件中断事件寄存器触发。
    
    - 第三部分：中断屏蔽/清除
        - 请求挂起寄存器，如果遇到传递过来的中断信号，会自动将请求挂起对应位置为1，然后传递到中断屏蔽寄存器下的与门，如果中断屏蔽寄存器需要将这个中断信号给阻止掉，就将对应位置为0即可，进行与门的按位与之后，就会将对应位直接处理成0，已达成屏蔽中断信号的操作，如果要中断信号通过，就需要将对应的位置为1。最终进入到NVIC中进行处理
    
    - 第四部分：事件屏蔽寄存器
        - 软件中断或者硬件中断的信号进入到事件屏蔽寄存器上的与门的时候，可以通过将事件屏蔽寄存器对应的位置0阻止信号通过或者置1允许信号通过，将其当做普通事件进行处理，而不是作为中断来传送到NVIC中。
    
    - 注意点：
      
        - 软件中断事件寄存器和事件屏蔽寄存器一般不常用，所以可以不过多关注。
        
        - 请求挂起寄存器是用来做中断标志位的，有中断信号过来的时候，将标志位置为1，NVIC才能进入中断，因此中断执行完毕之后，需要将中断标志位给再次清0。
        
        - 清除中断标志位，如果放在中断服务函数的最后，硬件还没有将标志位给清除掉，程序已经跳出了中断服务函数，这个时候NVIC又会识别到中断标志位，再次进入到中断服务函数中。

- EXTI和IO口的对应关系
  
    - EXTI和IO口的对应关系图![](https://api2.mubu.com/v3/document_image/b1f5120d-20d3-4af3-bec1-6a2a7f5bf4ab-4733041.jpg?)
    
    - 所有GPIO口都可以输出到EXTI线上，但是注意相同的pin脚（PA0和PB0）不能同时使用一个EXTI线
    
    - 触发方式
      
        - 硬件触发（通过IO口输出到EXTI线）
        
        - 软件触发（软件中断事件寄存器来触发）
    
    - 请求挂起寄存器
      
        - 当有中断信号到请求挂起寄存器的时候，寄存器的对应位置为1（中断标志位），如果中断事件屏蔽寄存器打开，就可以将中断信号传递给NVIC来处理
        
        - 当请求挂起寄存器发送了一次中断请求之后，需要将中断标志位给置0

- EXTI中HAL库的配置步骤
  
    - 基本流程
        - 首先执行中断初始化函数，由于初始化对触发条件和优先级都要进行设置，此时系统就在等待中断的触发，一旦触发了相应中断，则进入到中断服务函数中，中断服务函数要调用中断处理公用函数（设置PIN脚），中断处理公用函数会自动调用回调函数，并且将中断处理公用函数的参数传递到回调函数中执行。
    
    - 中断初始化函数
      
        - 使能GPIO时钟、使用HAL_GPIO_Init()函数可以设置EXTI和IO口之间的对应关系（设置哪一个引脚来触发EXTI中断），设置EXTI的触发模式（上升沿/下降沿/双边沿），设置初始化的上下拉
        
        - 设置中断分组
            - 使用函数：HAL_NVIC_SetPriorityGrouping()，此函数只需要设置一次即可
        
        - 设置中断优先级
            - HAL_NVIC_SetPriority()
              
                - 第一个参数：选择用什么方式触发中断，我们用的是exti其中的EXTI0_IRQn
                
                - 第二个参数：抢占优先级
                
                - 第三个参数：响应优先级
        
        - 使能中断
            - HAL_NVIC_EnableIRQ()
    
    - 中断服务函数
      
        - 编写EXTI0_IRQHandler()中断服务函数，清除中断的标志位
        
        - STM32仅有EXTI0~4、EXTI9_5、EXTI15_10，7个外部中断服务函数，如果多个引脚共用了同一个中断服务函数，比如EXTI9_5_IRQHandler()，进入到中断服务函数时还需要后还需要通过EXTI_PR寄存器来判断到底是哪一个线来触发的。
    
    - 编写中断回调函数
        - 中断服务函数会自动调用中断回调函数，在HAL库中所有的外部中断服务函数都会调用此函数。

- 代码演示
  
    - exti.h![](https://api2.mubu.com/v3/document_image/3b200025-91b5-4be3-b85a-ca45d73d7232-4733041.jpg?)
    
    - exti.c![](https://api2.mubu.com/v3/document_image/4733041_556e0256-3998-4a21-8e1e-496ad6b65502.png?)
    
    - main.c![](https://api2.mubu.com/v3/document_image/4733041_d3ec8912-be7c-47c1-9690-972eb24b9db3.png?)