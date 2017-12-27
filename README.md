介绍
====

致力于研发下一代计算架构，移动计算应用，植根于中国，用创新思维，全球视野，开拓科技进步，目前集中于riscv开放指令集处理器，及其架构和周边研发。

# RISC-V简介

RISC-V （发音为“risk-five”）是一个全新计算机指令集架构（ISA），它由美国加州大学伯克利分校电子工程和计算机学院的老师和学生共同设计，最初设计用来帮助计算机架构研究和教学，但现在它的设计者们也希望它成为一个免费和开放的标准工业架构。

## 特性包括：
- 完全开放的指令集架构，任何人都可以免费应用指令集于自己的产品，不需要支付任何知识产权费用。
> 注：指令集架构就是一个标准体系，知识产品，没有实物，实现这一架构的集成电路就成为了CPU。
- 一个适合于做成硬件的真正的指令集架构，而不仅仅是能模拟或进行二进制翻译。
- 一个避免`“架构过度”`的指令集架构。“架构过度”指：针对某种微架构（例如：微操作码，有序，去耦合，乱序），或者某种实现技术（例如：完全自定义，专用集成电路，FPGA）
- 分割为以整数为基础的小指令集，这些小指令集可以被用于执行自定义加速器，或者进行教学。如果加入可选的标准扩展，就可以支持通用软件开发。
- 支持最新的2008 IEEE-754浮点数标准。
- 一个可扩展的指令集。支持用户级指令集扩展，和特殊变体。
- 支持32位和64位寻址空间的应用程序，操作系统内核，和硬件执行。
- 一个支持高并行的数核或大量核的指令集，也支持异构多处理器。
- 可选的变长指令可以扩展已有的指令集（指令编码空间），支持一个套可选的密集指令编码，以提高性能，固化编码大小，提高能源效率。
- 一个完全可虚拟指令集架构，简化了虚拟管理系统的开发。
- 简化了设计同时具有特权级和虚拟管理级指令集架构的过程。
## 指令集概览
1. 基本整数指令集
  - RISC-V指令集架构定义为一个基于基本整数指令的指令集架构，这一基本指令集必须出现在任何执行这一规范的实例中，可选的，可以增加扩展指令。这一基本指令集非常类似于早期的RISC处理器，除了没有分支延迟槽且支持变长指令编码。这一基本指令集经过`精挑细选`，限定于一个最小集合，但足以作为一个合适的`机器`供编译器，汇编器，链接器，操作系统（附加上特权等级指令）运行于其上或作为目标机。由此提供了一个用于自定义处理器指令集架构的“骨架”。
  - 基本指令集按照整数寄存器宽度和对应的用户地址空间大小，分为2个变体，
    - RV32I，提供32位用户级地址空间。
    - RV64I，提供64位用户级地址空间。  
  硬件实现和其上的操作系统可以提供其中之一或者两个同时提供。  
  基本整数指令集使用2的补码形式来表示有符号整数值。
  - 为支持小的微控制器，提供了RV32E扩展指令集，该指令集从RV32I基本指令集变化而来。
  - 为了未来的需要，提供了RV128I扩展指令集，该指令集提供给用户一个扁平的128位地址空间。
  > 注：128位地址空间是个非常巨大的地址空间，理论上我们连64位地址空间也用不掉。是不需要128位地址空间的。但作为扩展的一种可能，规范还是考虑到了，有聊胜于无嘛！
2. RISC-V不同于其他指令集架构在于其自定义扩展的支持，它在基本整数指令集的基础上提供了两种扩展，标准扩展指令集和非标准扩展指令集。
- 标准扩展指令集：这些指令集不能进行重新定义或修改，它们互相之间没有冲突，也不和任何基本指令集指令冲突。硬件实现可以选择支持其中任意一或多个标准扩展指令集。
- 非标准扩展指令集：这些指令集可以由用户高度自定义，允许同其它标准或非标准指令集冲突。
