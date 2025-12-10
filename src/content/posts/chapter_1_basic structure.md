---
title: 'chapter_1_basic_structure'
published: 2025-12-10
draft: false
description: 'basic'
author: 'kado'
tags: ['CO']
toc: true
---

这份PPT的内容是关于**计算机组织与体系结构（Computer Organization & Architecture）**的第一章——**计算机的基本结构（Basic Structure of Computers）**，涵盖了计算机的类型、功能单元、基本操作概念、性能提升和历史发展等要点 。

以下是详尽的总结：

---

### 第一章：计算机的基本结构概览

#### 一、计算机功能单元 (Functional Units)

计算机系统由五个基本组成部分构成 ：

1.  **输入单元 (Input Unit)** 
2.  **输出单元 (Output Unit)** 
3.  **存储器 (Memory)** 
4.  **算术与逻辑单元 (ALU)** 
5.  **控制单元 (Control Unit)** 

**存储器单元的分类（续）** 

* **辅助存储器 (Secondary Storage)**：用于存储大量程序和数据，特别是那些不常被访问的信息 。
    * **示例**：
        * 磁性磁盘和磁带（如硬盘、软盘） 。
        * 光盘（如CD-ROMs） 。

**控制单元 (Control Unit)**

* **功能**：协调其他单元的操作 ，向其他单元发送控制信号并感知它们的状态 。

#### 二、计算机的操作 (Operations of a Computer)

1.  **信息输入与存储**：计算机通过输入单元接收程序和数据形式的信息，并将其存储到存储器中 。
2.  **信息处理**：在程序控制下，存储器中的信息被取出（Fetched）并送入**算术与逻辑单元 (ALU)** 进行处理 。
3.  **信息输出**：经过处理的信息通过输出单元离开计算机 。
4.  **活动指导**：机器内部的所有活动都由**控制单元**指导 。

#### 三、基本操作概念 (Basic Operational Concepts)

**1. 程序执行 (Program Execution)**

* **目的**：执行程序中指定的指令 。
* **过程**：处理器从存储器中一次读取（Fetch）一条指令，并执行该指令 。
* **循环**：程序执行包括重复执行“指令读取 (Instruction Fetch)”和“指令执行 (Instruction Execution)”的过程 。
* **指令周期**：执行周期由**取指令周期 (Fetch Cycle)** 和 **执行周期 (Execute Cycle)** 构成 。一个示例指令格式包括操作码（Opcode）和地址（Address）字段 。

**2. 中断 (Interrupt)**

* **定义**：中断是I/O设备向处理器发出的服务请求 。
* **带中断的指令周期**：在执行指令后，处理器会检查是否有中断请求，如有，则进入**中断周期 (Interrupt Cycle)** 进行处理 。

**3. 指令执行示例**

* **指令**：`Add LOCA, R0` (将存储器地址LOCA的内容加到寄存器R0) 。
* **步骤**：
    1.  将指令从存储器中取出并放入处理器（指令寄存器IR） 。
    2.  取出LOCA处的**操作数**，并将其与R0的内容相加（结合了存储器访问和ALU操作） 。
    3.  将结果和存回寄存器R0中 。
* **等效操作**：也可以通过两条指令实现：`Load LOCA, R1` (加载到R1) 和 `Add R1, R0` (R1加到R0) 。

#### 四、性能提升 (Performance)

**1. 单核CPU的限制**

* 为了更快地执行任务，必须提高时钟频率（Clock Time） 。
* 然而，过高地提高时钟频率会急剧增加功耗和散热量，导致处理器效率低下 。

**2. 并行性 (Parallelism)**

* **指令级并行 (Instruction-level Parallelism)** 
    * **流水线 (Pipelining)**：在第一条指令完成之前开始执行其他等待的指令 。
    * 流水线的基本思想是重叠指令的取指和执行过程 。
* **多核处理器 (Multicore Processors)** 

**3. 共享内存多处理器 (Shared-Memory Multiprocessor)**

* **最简MP**：多个处理器连接到单个总线访问内存，但**总线带宽**成为瓶颈 。
* **改进**：
    * 每个处理器配备**缓存 (Cache)**，以减少对内存的访问需求 。
    * 为进一步扩展处理器数量，每个处理器可配备**私有的本地内存 (private local memory)** 。

#### 五、历史回顾 (Historical Perspective)

| 代数 | 时间范围 | 核心技术 | 关键概念/人物 |
| :--- | :--- | :--- | :--- |
| **第零代 (机械计算机)** | 1642-1945  | 机械、电磁继电器  | **Blaise Pascal (1642)**：第一台能工作的计算器（加减法） 。**Leibniz (1672)**：增加了乘除法 。**Babbage**：差分机和分析机 。 |
| **第一代 (真空管)** | 1945-1955  | 真空管 (Vacuum Tubes)  | **存储程序概念 (John von Neumann)**：数据和指令存储在单一读写内存中 。内存内容按地址访问 。执行顺序通常是顺序的 。使用**汇编语言** 。 |
| **第二代** | | 晶体管 (Transistors)  | |
| **第三代** | | 集成电路 (Integrated Circuits)  | |
| **第四代** | | 大规模集成电路 (LSI) 和超大规模集成电路 (VLSI)  | |