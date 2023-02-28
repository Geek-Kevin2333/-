
### 1 代码导读

#### 1.1 代码结构

```bash
.
│  .gitignore
│  pom.xml
│  README.md
│
├─src
│  ├─main
│  │  └─java
│  │      ├─cpu
│  │      │  │  CPU.java       # CPU类
│  │      │  │  CPU_State.java # CPU的寄存器列表
│  │      │  │  MMU.java
│  │      │  │
│  │      │  ├─alu
│  │      │  │
│  │      │  ├─instr
│  │      │  │  ├─all_instrs # 指令的实现类
│  │      │  │  │      Add.java          # ADD指令的实现
│  │      │  │  │      InstrFactory.java # 指令工厂，使用了Java反射机制
│  │      │  │  │      Instruction.java  # 指令接口，需要阅读
│  │      │  │  │      Opcode.java       # 指令的操作码，参考Intel 32位指令实现
│  │      │  │  │
│  │      │  │  └─decode # 取指令相关的类
│  │      │  │
│  │      │  ├─registers # 寄存器类的定义
│  │      │  │
│  │      │  └─utils
│  │      │
│  │      ├─kernel # 测试时的程序入口
│  │      │      Loader.java
│  │      │      MainEntry.java
│  │      │
│  │      ├─memory
│  │      │
│  │      ├─program
│  │      │      Log.java # 实现控制台输出
│  │      │
│  │      ├─transformer
│  │      │
│  │      └─util
│  │
│  └─test
│      └─java
│          └─cpu
│              └─instr
│                      ICCTest.java # 测试类
│
└─test # 6个测试用例分别使用到的指令序列
        icc_test_1.txt
        icc_test_2.txt
        icc_test_3.txt
        icc_test_4.txt
        icc_test_5.txt
        icc_test_6.txt

```
### 2 指导

#### 2.1 指令描述

完整的指令描述需要通过查阅i386手册获得。

#### 2.2 实现参考

ADD指令供进行参考。已经实现好的指令描述如下：

- opcode=0x05 ADD EAX, imm32
    - 指令结构：1字节opcode + 4字节立即数imm
    - 功能：DEST = SRC + imm32;
    - 目的操作数DEST：EAX寄存器中的值
    - 源操作数SRC：EAX寄存器中的值


## 3 参考资料

英特尔80386程序员参考手册(i386)intel：https://css.csail.mit.edu/6.858/2014/readings/i386.pdf
![opcode.jpg](https://s2.loli.net/2021/12/18/pNQdDocSO8zkWsn.jpg)

# -
