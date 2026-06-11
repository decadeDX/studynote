---
updated: 2026-06-11 10:00
focused:
---
# 1. 概述

## 1.1 什么是 RTOS
RTOS（Real-Time Operating System，实时操作系统）有很多种，但由于 **FreeRTOS 免费、开源**，因此它是世界上最流行的 RTOS 系统（90% 以上使用 FreeRTOS）。

## 1.2 FreeRTOS 特点

|     | 特点          | 说明                                                    |
| --- | ----------- | ----------------------------------------------------- |
|     | **免费开源**    | 完全免费，源代码公开                                            |
|     | **可裁剪**     | 源码约 9000 行，使用者只需在 `FreeRTOSConfig.h` 中将不需要的宏注释或打开即可裁剪 |
|     | **轻量化设计**   | 内核精简，占用资源少                                            |
|     | **任务优先级不限** | 支持 0~31 优先级                                           |
|     | **任务数量不限**  | 理论上支持无数任务，仅受硬件内存和 Flash 限制                            |

> **官网**：https://www.freertos.org/

## 1.3 裸机程序 vs FreeRTOS

|     | 对比维度      | 裸机程序                              | FreeRTOS            |
| --- | --------- | --------------------------------- | ------------------- |
|     | **运行方式**  | 初始化执行一次，然后在 `while(1)` 死循环中完成所有任务 | 基于任务运行，任务调度器根据优先级调度 |
|     | **延时处理**  | 使用 `delay` 时 CPU 空转，什么都不干         | 延时期间 CPU 可运行其他任务    |
|     | **任务间影响** | 一个任务延时/阻塞，所有任务都需死等                | 任务之间互不影响            |
|     | **中断响应**  | 可通过中断响应，但中断嵌套存在优先级混乱问题            | 由调度器统一管理            |
|     | **适用场景**  | 外设少的小型系统、无人机中某一部分                 | 外设较多、业务复杂的项目        |

## 1.4 FreeRTOS、Linux、Windows 对比

### FreeRTOS

**一句话**：给单片机用的免费微型 RTOS，让多个任务"看起来同时"跑在一个单核 CPU 上，由优先级决定谁先跑。

**实际应用**：智能手环里屏幕刷新（高优先级）、蓝牙传输（中优先级）、计步算法（低优先级）跑在同一颗 STM32 上。你划屏幕时调度器立刻暂停计步，优先响应触摸。

**和我们在学内容的关联**：
- 跑在 [[STM32学习笔记|STM32]] 芯片上，是裸机开发的下一步
- 任务切换本质是 **PendSV 中断**触发的，中断知识是理解调度器的基础
- 裸机只有一个 `while(1)`，FreeRTOS 把它拆成多个独立的任务函数

### Linux

**一句话**：给能跑 MMU 的复杂芯片用的多用户多任务操作系统，有完整的内核、文件系统、驱动框架。

**实际应用**：[[瑞星微RK3506_linux学习|RK3506]] 跑的就是 Linux。写 GPIO 驱动不是直接操作寄存器，而是通过"设备树 + GPIO 子系统"框架来写——内核帮你管好了引脚复用、并发访问、权限控制。

**和我们在学内容的关联**：
- Linux 把硬件操作抽象成"子系统"，[[瑞星微RK3506芯片/10.GPIO子系统/01基础了解|驱动开发本质上是在框架里填回调函数]]
- 驱动最终呈现为设备文件（`/dev/xxx`），用户态用 `open/read/write` 操作——和 C 语言文件操作 `fopen/fclose` 同一套思想
- 每个进程有独立虚拟地址空间，比裸机的[[嵌入式学习笔记#二十九、内存空间区块划分|内存四区]]模型复杂得多

### Windows

**一句话**：微软的闭源桌面/企业操作系统，有最完善的 GUI 和商业软件生态。

**实际应用**：我们现在写代码用的电脑就是 Windows。Keil 编译 STM32、MobaXterm 调试串口、VS Code 写代码——嵌入式开发工具链大多跑在 Windows 上。

**和我们在学内容的关联**：
- 你在 Windows 上写代码 → 交叉编译器生成 ARM 机器码 → 烧到开发板运行，这个"写-编-烧-调"循环离不开 Windows
- 学习用的所有 IDE 和工具链都以 Windows 为操作台

### 三者定位总结

|     | 对比维度     | FreeRTOS              | Linux                  | Windows  |
| --- | -------- | --------------------- | ---------------------- | -------- |
|     | **定位**   | 单片机 RTOS              | 嵌入式/服务器 OS             | 桌面/企业 OS |
|     | **内核规模** | ~9000 行               | 百万行级                   | 千万行级     |
|     | **运行硬件** | STM32（Cortex-M，无 MMU） | RK3506（Cortex-A，有 MMU） | x86 PC   |
|     | **核心要学** | 任务创建、队列、信号量           | 设备树、驱动子系统、内核编译         | 开发工具链使用  |
|     | **当前阶段** | 🔶 正在入门               | 🔶 正在学 GPIO 驱动         | ✅ 已在用    |
|     | **一句话**  | 让单片机同时干多件事            | 让 APP 通过框架控制硬件         | 你干活的操作台  |

> **开发全景**：Windows 写代码编译 → 烧到 STM32（跑 FreeRTOS）或 RK3506（跑 Linux）→ 三个系统各司其职，定位不同。

---

# 2. 任务调度

## 2.1 任务调度方式

FreeRTOS 默认按照**抢占式 + 时间片轮询**的方式运行。共有三种任务调度方式：

### 2.1.1 抢占式调度

- 当两个任务的优先级**不同**时，高优先级任务可以**打断**正在运行的低优先级任务
- 低优先级任务**不能打断**高优先级任务
- 若高优先级任务一直运行，则低优先级任务**永远不能执行**

### 2.1.2 时间片调度

- 时间片轮询时，每一个节拍按照 **systick 定时器的节拍**来定
- $$T = 1 / f$$
- 时间片轮询就是对于**相同优先级**的任务，按照固定时间节拍**平均分配**运行时间，所有任务循环执行
- 所有任务公平地获得 CPU 时间

### 2.1.3 协作式调度

- 任务执行完之后必须**主动让出 CPU**，否则其他任务无法执行
- 类似于裸机中的任务执行方式

### 2.1.4 总结

- **优先级不同** → 抢占式调度
- **优先级相同** → 时间片轮询
- 三种调度方式可在 `FreeRTOSConfig.h` 中设置，**默认打开抢占 + 时间片**

---

## 2.2 任务优先级规则

- 高优先级可以打断低优先级运行，低优先级无法打断高优先级
- **优先级数字越大，优先级越高**（0 为最低优先级，31 为最高）

---

## 2.3 Systick 节拍

- 裸机中我们需自己编写 Systick 定时器来实现延时
- 在 FreeRTOS 中**不能设置任何和 Systick 相关的设置**，因为 FreeRTOS 自己接管了 Systick 定时器，所有设置已完成
- 延时直接使用 FreeRTOS 提供的 `vTaskDelay(n)`，表示延时 **n 毫秒**

---

## 2.4 任务状态

FreeRTOS 共有**四种任务状态**，除运行态外，其他三种任务状态都有对应的任务状态列表。

### 2.4.1 四种任务状态

|     | 状态      | 说明                                                  |
| --- | ------- | --------------------------------------------------- |
|     | **就绪态** | 任务刚被创建后即处于就绪态，可以转为运行态                               |
|     | **运行态** | 任务正在 CPU 中运行，同一时间只能有一个任务处于运行态                       |
|     | **阻塞态** | 任务被延时（delay）后进入阻塞态，延时结束后自动进入就绪态                     |
|     | **挂起态** | 使用 `suspend` 函数将任务临时挂起（暂停），必须使用 `resume` 函数才能恢复到就绪态 |

### 2.4.2 任务状态切换规则

![freeRTOS任务状态](../../../picture/java/freeRTOS任务状态.png)

**核心规则：**
- **只有就绪态**可以进入运行态
- 就绪态的任务可以通过 `suspend()` 进入挂起态
- **运行态** → 被抢占或时间片到 → **就绪态**
- **运行态** → `vTaskDelay()` → **阻塞态**
- **运行态** → `suspend()` → **挂起态**
- **阻塞态** → 延时结束 → 自动进入**就绪态**
- **阻塞态** → `suspend()` → **挂起态**
- **所有状态**都可以进入挂起态
- **挂起态**只能通过 `resume()` 进入**就绪态**

---

## 2.5 任务状态列表

> 任务状态一共有四种，除**运行态**外，其他三种任务状态都有任务状态列表。FreeRTOS 的优先级就是依靠任务状态列表来实现的。
> ![任务状态列表](../../../picture/java/任务状态列表.png)

- 当一个任务处于就绪态时，在**就绪列表**的对应优先级下就可以找到该任务
- **优先级列表**最大有 31 个（默认 5 个），每一个相同的优先级放在同一个列表中
- FreeRTOS 每次从**最高优先级列表**开始检查有无任务，有则直接执行

---

## 2.6 任务控制块（TCB）

任务控制块就是存放任务**所有信息**的数据结构，包括：

- 栈空间大小
- 优先级
- 上下文（寄存器值等）
- 任务状态
- 其他任务属性

---

## 2.7 任务事件

在 FreeRTOS 中，能使任务进入延时、阻塞、挂起等状态的机制称为**任务事件**。共有**四种**：

|     | 任务事件                  | 说明                        |
| --- | --------------------- | ------------------------- |
|     | **延时 `vTaskDelay`**   | 使任务进入阻塞态，延时结束后恢复就绪        |
|     | **信号量（Semaphore）**    | 用于任务间同步和资源互斥访问            |
|     | **任务队列（Queue）**       | 用于任务间数据传递                 |
|     | **事件标记（Event Group）** | 例如必须按下按键才能执行某一操作，按键就是事件标记 |

---

## 2.8 任务相关函数

> 一般情况下，所有任务的创建都使用**动态创建**。

### 2.8.1 创建任务：`xTaskCreate()`

**函数原型：**
```c
BaseType_t xTaskCreate( TaskFunction_t pxTaskCode,
                        const char * const pcName,
                        const configSTACK_DEPTH_TYPE usStackDepth,
                        void * const pvParameters,
                        UBaseType_t uxPriority,
                        TaskHandle_t * const pxCreatedTask );
```

**参数说明：**

|     | 参数              | 说明                     |
| --- | --------------- | ---------------------- |
|     | `pxTaskCode`    | 任务函数指针（任务体）            |
|     | `pcName`        | 任务名称（字符串，调试用）          |
|     | `usStackDepth`  | 任务栈大小（单位：字，非字节）        |
|     | `pvParameters`  | 传给任务的参数，一般不传时使用 `NULL` |
|     | `uxPriority`    | 任务优先级                  |
|     | `pxCreatedTask` | 任务句柄指针（用于后续操作该任务）      |

**注意点：**
- 返回值类型为 `BaseType_t`（FreeRTOS 专用基础类型）
- FreeRTOS 函数**无返回值**时一律以 `v` 开头，**有返回值**时以返回值类型确定，一般为 `x`
- **优先级不要设置为 0**：0 是 FreeRTOS 给空闲任务（Idle Task）预留的
- 运行态**必须始终有任务**在运行——若没有用户任务，FreeRTOS 会自动调用空闲任务占用 CPU

#### 动态创建的编写步骤

**1）编写 .h 文件：**
```c
#include "FreeRTOS.h"    // ⚠️ 必须放在所有 FreeRTOS 头文件之前
#include "task.h"
```

**2）编写 .c 文件 —— 任务体：**
```c
void vTaskLED(void *pvParameters)    // 形参必须为 void *pvParameters
{
    while (1)    // ⚠️ 任务体必须包含死循环，否则执行一次后任务就被删除
    {
        // 业务逻辑
        vTaskDelay(500);    // 大多数情况下必须添加延时（有信号量/队列时除外）
    }
}
```

> **为什么必须有 `while(1)`？** 任务函数本质上是一个永不返回的函数。如果任务体执行完毕返回，FreeRTOS 会将该任务删除。要让任务持续存在，必须用死循环。

> **为什么大多数情况要加 `vTaskDelay`？** 如果不加延时且没有阻塞机制（信号量、队列等），该任务会一直霸占 CPU，同优先级或更低优先级的任务永远无法执行。

**3）动态创建任务 & 启动调度器：**
```c
TaskHandle_t xLEDTaskHandle = NULL;

xTaskCreate(vTaskLED,      // 任务体
            "LED_Task",    // 任务名
            128,           // 栈大小
            NULL,          // 参数（不传参）
            2,             // 优先级（不要用 0）
            &xLEDTaskHandle); // 任务句柄

vTaskStartScheduler();    // ⚠️ 不管有多少任务，调度器只启动一次！
```

---

### 2.8.2 创建任务：`xTaskCreateStatic()`（静态创建）

**函数原型：**
```c
TaskHandle_t xTaskCreateStatic( TaskFunction_t pxTaskCode,
                                const char * const pcName,
                                const configSTACK_DEPTH_TYPE usStackDepth,
                                void * const pvParameters,
                                UBaseType_t uxPriority,
                                StackType_t * const puxStackBuffer,
                                StaticTask_t * const pxTaskBuffer );
```

**与动态创建的最大区别：**

|     |           | 动态创建 `xTaskCreate()` | 静态创建 `xTaskCreateStatic()`                                        |
| --- | --------- | -------------------- | ----------------------------------------------------------------- |
|     | **栈内存**   | FreeRTOS 自动从堆分配      | 用户自行提供（需传入 `puxStackBuffer`）                                      |
|     | **任务控制块** | FreeRTOS 自动分配        | 用户自行提供（需传入 `pxTaskBuffer`）                                        |
|     | **返回值**   | `BaseType_t`（成功/失败）  | `TaskHandle_t`（成功返回句柄，失败返回 `NULL`）                                |
|     | **宏开关**   | 官方已默认打开              | 需在 `FreeRTOSConfig.h` 中将 `configSUPPORT_STATIC_ALLOCATION` 设为 `1` |

> 基本上所有的 FreeRTOS 资源（任务、信号量、软件定时器、队列等）都有静态创建版本，都需在头文件中打开对应宏才能使用。

#### 静态创建的编写步骤

**1）编写任务栈和任务控制块（必须用 `static` 修饰）：**
```c
static StackType_t  pxIdleTaskStack[128];   // 任务栈
static StaticTask_t pxIdleTaskTCB;          // 任务控制块
```

> **为什么必须用 `static`？** 如果不用 `static`，这些数组是局部变量，函数返回后栈内存会被编译器回收——任务还在运行但栈没了，必然崩溃。同时 `static` 限制变量仅在当前 `.c` 文件生效（注意 `extern` 与 `static` 是互斥的）。

**2）使用静态函数创建任务：**
```c
TaskHandle_t xLEDTaskHandle = xTaskCreateStatic(
    vTaskLED,            // 任务体
    "LED_Task",          // 任务名
    128,                 // 栈大小
    NULL,                // 参数
    2,                   // 优先级
    pxIdleTaskStack,     // 用户提供的任务栈
    &pxIdleTaskTCB       // 用户提供的任务控制块
);

if (xLEDTaskHandle != NULL) {
    // 创建成功
} else {
    // 创建失败
}
```

---

### 2.8.3 删除任务：`vTaskDelete()`

**函数原型：**
```c
void vTaskDelete( TaskHandle_t xTaskToDelete );
```

**说明：**
- 需传入要被删除任务的**任务句柄**
- 动态创建的任务：句柄是 `xTaskCreate()` 的最后一个参数
- 静态创建的任务：句柄是 `xTaskCreateStatic()` 的返回值
- 若传入 `NULL`，表示**删除当前任务自己**
- 被删除的任务处于什么状态，那个状态会一直持续（不会自动恢复）

**实验示例**（按下按键 1 删除动态创建任务，按键 2 删除静态创建任务）：

```c
// LED 任务体
void vTaskLED(void *pv) {
    while (1) { /* 闪烁 LED */ }
}

// 按键删除任务体
void vTaskKeyDelete(void *pv) {
    while (1) {
        if (KEY1_PRESSED) {
            vTaskDelete(xDynamicLEDHandle);   // 删除动态任务
        }
        if (KEY2_PRESSED) {
            vTaskDelete(xStaticLEDHandle);    // 删除静态任务
        }
        vTaskDelay(20);
    }
}
```

---

### 2.8.4 挂起任务：`vTaskSuspend()`

**函数原型：**
```c
void vTaskSuspend( TaskHandle_t xTaskToSuspend );
```

**说明：**
- FreeRTOS 中**所有任务**都可以使用 `vTaskSuspend()` 挂起
- 传入任务句柄即可挂起对应任务
- 挂起后任务进入**挂起态**，CPU 不再执行

---

### 2.8.5 恢复任务

#### 在任务中恢复：`vTaskResume()`

**函数原型：**
```c
void vTaskResume( TaskHandle_t xTaskToResume );
```

**说明：**
- 传入任务句柄即可恢复被挂起的任务
- ⚠️ **无论任务被挂起多少次，只需调用一次 `vTaskResume()` 即可恢复**

**实验示例**（按键 1 挂起 LED4，按键 2 恢复 LED4；LED2 保持闪烁提示系统运行）：

```c
void vTaskKeyControl(void *pv) {
    while (1) {
        if (KEY1_PRESSED) {
            vTaskSuspend(xLED4Handle);    // 挂起 LED4
        }
        if (KEY2_PRESSED) {
            vTaskResume(xLED4Handle);     // 恢复 LED4
        }
        vTaskDelay(20);
    }
}
```

#### 在中断中恢复：`xTaskResumeFromISR()`

**函数原型：**
```c
BaseType_t xTaskResumeFromISR( TaskHandle_t xTaskToResume );
```

**中断实现通用步骤：**

|     | 步骤  | 内容                                  |
| --- | --- | ----------------------------------- |
|     | 1   | 初始化时钟和 GPIO                         |
|     | 2   | 设置中断优先级并使能中断（EXTI）                  |
|     | 3   | 编写中断服务函数（ISR）                       |
|     | 4   | 编写中断回调函数（**所有业务逻辑写在回调中，不写在 ISR 中**） |

**实验**（按键 1 挂起 LED4，EXTI 中断中恢复 LED4；LED2 保持闪烁）：

```c
// EXTI 中断回调函数
void HAL_GPIO_EXTI_Callback(uint16_t GPIO_Pin) {
    if (GPIO_Pin == KEY1_PIN) {
        BaseType_t xHigherPriorityTaskWoken = pdFALSE;
        xTaskResumeFromISR(xLED4Handle);    // 中断中恢复任务
        portYIELD_FROM_ISR(xHigherPriorityTaskWoken);
    }
}
```

---

### 2.8.6 常用 API 速查

|     | 函数                      | 功能           |
| --- | ----------------------- | ------------ |
|     | `vTaskDelay(n)`         | 延时 n 毫秒（阻塞态） |
|     | `vTaskSuspend()`        | 挂起任务         |
|     | `vTaskResume()`         | 恢复挂起的任务      |
|     | `xTaskCreate()`         | 动态创建任务       |
|     | `xTaskCreateStatic()`   | 静态创建任务       |
|     | `vTaskDelete()`         | 删除任务         |
|     | `vTaskStartScheduler()` | 启动调度器        |

---

### 2.8.7 小结

|     | 函数                           | 作用           | 返回值                           |
| --- | ---------------------------- | ------------ | ----------------------------- |
|     | `xTaskCreate()`              | 动态创建任务       | `BaseType_t`（pdPASS / pdFAIL） |
|     | `xTaskCreateStatic()`        | 静态创建任务       | `TaskHandle_t`（句柄 / NULL）     |
|     | `vTaskDelete(NULL)`          | 删除当前任务       | 无                             |
|     | `vTaskDelete(handle)`        | 删除指定任务       | 无                             |
|     | `vTaskSuspend(handle)`       | 挂起任务         | 无                             |
|     | `vTaskResume(handle)`        | 恢复任务（任务中调用）  | 无                             |
|     | `xTaskResumeFromISR(handle)` | 恢复任务（中断中调用）  | `BaseType_t`                  |
|     | `vTaskStartScheduler()`      | 启动调度器（只调用一次） | 无                             |

> **核心记忆点：**
> 1. 任务体必须有 `while(1)` —— 否则跑一次就没了
> 2. 大多数情况必须加 `vTaskDelay` —— 否则霸占 CPU
> 3. 优先级不要设 0 —— 那是空闲任务的
> 4. 静态创建的资源必须用 `static` 修饰 —— 防止栈被回收
> 5. 挂起多少次都只需恢复一次 —— 内部是计数还是标记取决于版本
> 6. 中断中的业务写回调、不写 ISR —— 保持 ISR 短小精悍

---

# 3. 队列

## 3.1 什么是队列

队列是**任务与任务之间、任务与中断之间**传递消息（数据）的一种机制。队列相当于一根管道，一边传数据，一边接收数据。队列遵循 **FIFO（先进先出）** 特性。

## 3.2 队列特点

### 3.2.1 FIFO（先进先出）

先发送的数据就应该先被接收到。就像排队一样，先来的人先被服务。

### 3.2.2 独立的缓冲区

在 FreeRTOS 的队列中，数据是**直接被拷贝进队列**的。对于原始数据来讲，非常安全。但是当数据量比较大时，也可以传递指针（避免大量数据拷贝）。

### 3.2.3 多任务读写

队列支持**多个任务同时向队列写入数据**和**多个任务同时从队列读取数据**。

### 3.2.4 队列大小固定

队列在创建时就要确定队列的大小，此大小不可改变。比如队列大小为 **n**，队列中每个数据长度为 **m**。

> 设当前队列中已有数据个数为 **m**（注意区分：小 m 是当前数据量，大 N 是队列总容量）。

### 3.2.5 自带阻塞机制

当队列为满或者为空时，可能会存在阻塞；任务此时在等待队列，等不到队列一般就进入阻塞状态（睡觉），此时 CPU 可以运行其他任务。

#### 入队阻塞（队列满）

当队列数据已满时（m = n），此时任务再向队列中写入数据（入队就是 m+1），由于队列已满，因此不能向队列继续写入，此时任务就进入了**阻塞状态**。

> 📦 **生活例子**：快递员向丰巢柜子放快递——柜子满了，快递员只能等待有人取走快递后才能继续放。

#### 出队阻塞（队列空）

当队列数据为空时（m = 0，此时队列称为**空队列**），任务要从队列中取数据（出队就是 m-1），由于队列为空，因此不能从队列取到数据，此时任务就进入了**阻塞状态**。

> 📦 **生活例子**：小明在快递没有放置时去丰巢取快递——柜子是空的，小明只能等待快递员放入后才能取。

---

## 3.3 队列相关函数

> ⚠️ 使用队列前需要：1）在 `FreeRTOSConfig.h` 中打开队列相关宏；2）引入 `queue.h` 头文件。

### 3.3.1 创建队列：`xQueueCreate()`

```c
QueueHandle_t xQueueCreate(uxQueueLength, uxItemSize);
```

| 参数 | 说明 |
| --- | --- |
| `uxQueueLength` | 队列长度，队列最大可以容纳的元素个数 |
| `uxItemSize` | 每一个元素的大小（单位：字节），一般使用 `sizeof` 关键字求得 |

**示例：**
```c
// 创建一个能容纳 5 个 uint32_t 数据的队列
QueueHandle_t xQueue = xQueueCreate(5, sizeof(uint32_t));
```

### 3.3.2 接收数据：`xQueueReceive()`

```c
BaseType_t xQueueReceive( QueueHandle_t xQueue,
                          void * const pvBuffer,
                          TickType_t xTicksToWait );
```

| 参数 | 说明 |
| --- | --- |
| `xQueue` | 队列句柄 |
| `pvBuffer` | 接收数据的缓冲区指针 |
| `xTicksToWait` | 队列等待时间（阻塞时间） |

**`xTicksToWait` 取值说明：**

| 值 | 行为 | 是否推荐 |
| --- | --- | --- |
| **0** | 不等待，立即返回。CPU 一直检查有没有数据可接收，有则拿走。 | ❌ **绝对不推荐**：写在 `while(1)` 中会导致 CPU 空转，无法执行其他任务 |
| **任意值**（如 100） | CPU 等待固定时间（毫秒级）再去检查。等待期间 CPU 可以运行其他任务。 | ✅ 推荐 |
| **`portMAX_DELAY`** | CPU **死等**数据，有数据则直接拿走。死等期间 CPU 完全可以运行其他任务（任务进入阻塞态）。 | ✅ 推荐（当确信数据一定会到来时） |

**示例：**
```c
uint32_t receivedValue;
// 死等数据，直到队列中有数据为止
if (xQueueReceive(xQueue, &receivedValue, portMAX_DELAY) == pdPASS) {
    // 成功接收到数据
}
```

### 3.3.3 发送数据：`xQueueSend()`

```c
BaseType_t xQueueSend( QueueHandle_t xQueue,
                       const void * pvItemToQueue,
                       TickType_t xTicksToWait );
```

| 参数 | 说明 |
| --- | --- |
| `xQueue` | 队列句柄 |
| `pvItemToQueue` | 要发送的数据指针 |
| `xTicksToWait` | 队列等待时间（阻塞时间） |

**`xTicksToWait` 取值说明：**

| 值 | 说明 |
| --- | --- |
| **0** | 不等待，队列满时立即返回失败 |
| **任意值** | 等待固定时间，超时后返回 |
| **`portMAX_DELAY`** | 死等，直到队列有空位 |

> 📌 **经验之谈**：发送数据一般直接使用 **0**（不阻塞），因为发送方通常不希望被阻塞。

**示例：**
```c
uint32_t sendValue = 100;
// 立即发送，不等待
xQueueSend(xQueue, &sendValue, 0);
```

---

## 3.4 使用场景

### 3.4.1 一个任务向队列发送数据

最简单的场景：任务 A 向队列写入数据，任务 B 从队列读取数据。

```c
// 发送任务
void vTaskSender(void *pvParameters) {
    uint32_t value = 0;
    while (1) {
        value++;
        xQueueSend(xQueue, &value, 0);
        vTaskDelay(500);  // 每 500ms 发送一次
    }
}

// 接收任务
void vTaskReceiver(void *pvParameters) {
    uint32_t received;
    while (1) {
        if (xQueueReceive(xQueue, &received, portMAX_DELAY) == pdPASS) {
            // 处理接收到的数据
        }
    }
}
```

### 3.4.2 多个任务向一个队列发送数据

多个生产者 → 一个队列 → 一个消费者，队列天然保证了数据不会丢失或混乱。

```c
// 发送任务 A
void vTaskSenderA(void *pvParameters) {
    uint32_t value = 0;
    while (1) {
        value = 1;  // 任务 A 发送 1
        xQueueSend(xQueue, &value, 0);
        vTaskDelay(300);
    }
}

// 发送任务 B
void vTaskSenderB(void *pvParameters) {
    uint32_t value = 0;
    while (1) {
        value = 2;  // 任务 B 发送 2
        xQueueSend(xQueue, &value, 0);
        vTaskDelay(500);
    }
}

// 接收任务
void vTaskReceiver(void *pvParameters) {
    uint32_t received;
    while (1) {
        if (xQueueReceive(xQueue, &received, portMAX_DELAY) == pdPASS) {
            // 根据接收值区分数据来源
            if (received == 1) { /* 来自任务 A */ }
            if (received == 2) { /* 来自任务 B */ }
        }
    }
}
```

### 3.4.3 实验：通过队列控制 LED4 闪烁

创建一个队列，通过队列控制 LED4 每隔 500ms 闪烁一次。

```c
#include "FreeRTOS.h"
#include "task.h"
#include "queue.h"

QueueHandle_t xLEDQueue;

// 发送任务：每 500ms 向队列发送一次翻转信号
void vTaskLEDSender(void *pvParameters) {
    uint32_t toggle = 1;
    while (1) {
        xQueueSend(xLEDQueue, &toggle, 0);
        vTaskDelay(500);
    }
}

// LED 控制任务：从队列接收信号后翻转 LED
void vTaskLEDController(void *pvParameters) {
    uint32_t signal;
    while (1) {
        if (xQueueReceive(xLEDQueue, &signal, portMAX_DELAY) == pdPASS) {
            HAL_GPIO_TogglePin(LED4_GPIO_Port, LED4_Pin);  // 翻转 LED4
        }
    }
}

int main(void) {
    // ...硬件初始化...

    // 创建队列：容纳 5 个 uint32_t 数据
    xLEDQueue = xQueueCreate(5, sizeof(uint32_t));

    // 创建任务
    xTaskCreate(vTaskLEDSender, "Sender", 128, NULL, 2, NULL);
    xTaskCreate(vTaskLEDController, "LED_Ctrl", 128, NULL, 2, NULL);

    vTaskStartScheduler();

    while (1) {}  // 不会执行到这里
}
```

---

## 3.5 队列使用注意事项

1. **队列创建的大小要合理**：太大浪费内存，太小可能导致发送方频繁阻塞
2. **接收数据不要使用 `xTicksToWait = 0`**：会导致 CPU 空转，白白浪费 CPU 资源
3. **发送数据通常使用 `xTicksToWait = 0`**：发送方一般不愿被阻塞
4. **使用队列后任务体中可以不加 `vTaskDelay`**：因为 `xQueueReceive` 本身就是阻塞函数，任务等数据时自动进入阻塞态，不霸占 CPU
5. **传递大数据时考虑传指针而非拷贝**：减少内存消耗，但要注意指针所指向的数据在接收方使用前不能被释放
