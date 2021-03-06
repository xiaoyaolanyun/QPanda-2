.. QPanda 2 documentation master file, created by
   sphinx-quickstart on Tue Jan 22 14:31:31 2019.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

QPanda 2
====================================
|build-status|

.. |build-status| image:: https://travis-ci.org/OriginQ/QPanda-2.svg?branch=master
    :alt: build status
    :scale: 100%
    :target: https://travis-ci.org/OriginQ/QPanda-2

一种功能齐全，运行高效的量子软件开发工具包
---------------------------------------------

QPanda-2（Quantum Panda 2 Software Development Kit）是由本源量子推的开源量子程序开发工具包。其支持主流的量子逻辑门操作，并且可对不同平台下的量子程序进行针对性优化，可适配多种量子芯片。QPanda-2使用C++语言作为经典宿主语言，并支持以QRunes、QASM、QUil书写的量子语言。

目前，QPanda-2支持本地仿真运行模式，最高可支持到32位，它集成了量子虚拟机，封装了主流的量子算法。可在无芯片支持的情况下验证量子应用的可靠性和有效性。加上增加了控制流的概念使得量子程序可进行逻辑判断，从而符合高级语言的编程习惯。

在QPanda-2里，总共由三个过程组成：初始化生成、编译和运行。

* 初始化：初始化生成是允许用户设计不同的量子线路来处理对应需要解决的问题。

* 编译：而编译则是允许用户重写它们以在不同的后端运行（比如模拟器，不同公司的量子芯片等）。

* 运行：即是收集结果的过程，对于运行后的数据采集，取决于程序本身的设计需求去做相应的存储或者转化，运行的结果，也依赖于解决问题的需要而定。有的问题，可能需要依赖上一个量子程序运行结果才能执行下一个量子程序，诸如此类。

QPanda的设计思想
----------------------

考虑到量子计算的蓬勃发展和未来的广泛应用，QPanda 2.0做了很多前瞻性的设计。所以QPanda在设计时做了以下考虑：

1. 全系列兼容：
********************

QPanda 的目标是兼容所有量子计算机。底层量子计算机现在由于正处快速发展期，所以芯片、测控等实现细节都不确定。QPanda简化并规避了诸多量子计算机的物理细节而为用户提供了标准化的接口。通过QPanda构建的量子计算机，本身是通过经典的程序语言对其进行交互，所以它可以被用于任意的云量子计算机，本地量子计算机，或者是实验中的量子原型机。通过QPanda构建的量子应用则不会受到硬件变动的影响。

2. 标准架构：
*********************

QPanda提供了标准化的量子程序（Quantum Program）架构。架构者认为，在量子机器（Quantum Machine）中执行的程序和在经典计算机中执行的程序应该彻底区分开来，特别是涉及到经典控制的部分。物理上，芯片的退相干（Decoherence）时间极为短暂，这使得量子程序中的控制流并非在狭义的CPU中完成，而更有可能会采用极低延时的FPGA或其它嵌入式器件作为其测控系统实现。我们认为，量子机器包含了量子芯片与其测控系统，一个量子程序被视作是对一个原子的操作，直到执行完毕才返回结果给经典计算机。 量子程序的架构包含：量子逻辑门、量子线路、量子分支线路和量子循环线路。在QPanda-2里这几种元素均以接口的形式被提供，我们提供了一组这些接口的实现类作为基础的数据接口。用户可以重写这些接口并将实现类进行注册，系统会选择用户的类对默认实现类进行覆盖，并且保持其它结构的不变。

3. 标准化量子机器模型：
***********************

我们提供了标准化的量子机器模型。通常，量子程序是静态加载到量子机器里，并且量子程序本身也是被静态地构建的。这意味我们可以在量子程序被执行前，对量子程序进行静态检查和分析，获取其中的信息（而非执行它）。能检查的要素例如：量子比特是否越界，经典寄存器是否超过硬件允许的范围等等。而能进行的预处理则包含：任意的量子程序被替换到对应真实芯片的拓扑结构和基本逻辑门集合上（硬件兼容），量子程序的运行时长判断，量子程序的优化等等。 量子机器模型还定义了量子程序的标准构建过程。例如从量子比特池中申请空闲比特，从内存中申请空间，将程序加载到量子机器中，或者在已有的量子程序中附加一段新的量子程序。和量子程序的部分类似，量子机器本身的任何架构也是接口化的，用户也可以对接口进行覆写以应对不同硬件的需求。


.. toctree::
    :maxdepth: 1

    ChangeLog
   
目录：

.. toctree::
    :maxdepth: 2

    Tutorial

.. toctree::
    :caption: 深入学习
    :maxdepth: 2

    QGate
    QCircuit
    QWhile
    QIf
    QProg
    QuantumMachine
    Measure
    PMeasure

.. toctree::
    :caption: 工具组件
    :maxdepth: 2

    QGateValidity
    QGateCounter
    QProgClockCycle
    QProgStored
    QProgDataParse
    QRunesToQProg

.. toctree::
    :caption: 量子程序转换
    :maxdepth: 2
    
    QProgToQASM
    QProgToQRunes
    QProgToQuil

.. toctree::
    :caption: 量子算法
    :maxdepth: 2

    QAOA
    VQE

.. toctree::
    :caption: 算法组件
    :maxdepth: 2

    PauliOperator
    FermionOperator
    Optimizer

.. toctree::
    :caption: VQNet
    :maxdepth: 2
    
    Variable
    VarOperator
    Expression
    可变量子逻辑门
    可变量子线路
    GradientOptimizer
    VQNetExample