

## introduction
§Operating systems provide an environment for execution of programs and services to programs and users
> programs: 进程
> allocate resources to programs 分配资源给进程
 - Computer system :  hardware,  operating system,  application programs,  user
 - Interrupts
 - Real-Time Embedded Systems
> 
> 
 - [ ] **嵌入式系统**是专门为某一特定功能设计的计算机系统，它通常嵌入在一个更大的设备中，例如  微波炉中的控制系统  汽车中的防抱死制动系统（ABS）
 - [ ] **实时系统**是指必须在规定的时间内完成某些任务的系统。
 - The basic unit of computer storage is the bit, which contain one 0 or 1, and a **byte** is 8 bits; a **kilobyte** or **KB** is 1024 bytes; a **megabyte (MB)** is 1024*1024 bytes; a **gigabyte (GB)** is 1024^3 bytes; a **terabyte (TB)** is 1024^4 bytes.
 - An operating system is software that manages the computer hardware, as well as providing an environment for application programs to run.

- **API (Application Programming Interface)** 是应用程序与操作系统或其他软件系统之间的交互接口。
- **System Call（系统调用）** 是操作系统提供给用户程序的接口，用于在**用户态**（受限制的环境）和**内核态**（拥有全部权限）之间进行交互。
a way in which a computer program requests a service from the kernel of the operating system.
>****A system call**** is a programmatic way in which a computer program requests a service from the kernel of the operating system it is executed on. A system call is a way for programs to ****interact with the operating system****. A computer program makes a system call when it requests the operating system’s kernel.  
****系统调用****是一种编程方式，计算机程序通过这种方式从执行它的操作系统的内核请求服务。系统调用是程序****与操作系统交互****的一种方式。计算机程序在请求操作系统的内核时进行系统调用。
System call ****provides**** the services of the operating system to the user programs via the Application Program Interface(API). It provides an interface between a process and an operating system to allow user-level processes to request services of the operating system. System calls are the only entry points into the kernel system. All programs needing resources must use system calls.
系统调用通过应用程序接口 （API） ****向用户程序提供****操作系统的服务。它提供进程和操作系统之间的接口，以允许用户级进程请求操作系统的服务。系统调用是进入内核系统的唯一入口点。
A user program can interact with the operating system using a system call.
A system call is a mechanism used by programs to request services from the operating system (OS).

    What is the purpose of system calls?
    System calls allow user-level processes to request services of the operating system.
    - command interpreter 命令解释器
   A command interpreter allows the user to interact with a program using commands in the form of text lines. 命令解释器允许用户使用文本行形式的命令与程序进行交互。
   The purpose of the command **interpreter** is to serve as an interface between the user and the operating system. It allows users to interact with the operating system by accepting user commands and executing them. The command interpreter is usually separate from the kernel for security and flexibility reasons.  
命令**解释**器的目的是充当用户和操作系统之间的接口。它允许用户通过接受用户命令并执行它们来与操作系统进行交互。出于安全性和灵活性的原因，命令解释器通常与内核分开。

    What is the purpose of the command interpreter? Why is it usually separate from the kernel?
- To start a new process, the shell executes a fork() system call. Then, the selected program is loaded into memory via an exec() system call, and the program is executed.
通常，`fork()` 和 `exec()` 是配合使用的。典型的操作流程是：

1.  父进程调用 `fork()` 创建一个子进程。
2.  子进程调用 `exec()` 来加载并执行新的程序。

` What system calls have to be executed by a command interpreter or shell in order to start a new process on a UNIX system? `
`1. The parent process calls 'fork()' to create a child process.
2. The child process calls 'exec()' to load and execute the new program.`

- **system programs**
system programs are a special software which give us facility to manage and control the computer’s hardware and resources. Helpful in performing essential operation which can’t be handled by application software .它为我们提供了管理和控制计算机硬件和资源的能力。并有助于执行应用程序软件无法处理的基本操作。
Note : The user can only view up-to-the System Programs he cannot see System Calls 注 ： 用户只能查看系统程序，而无法查看系统调用。

 `What is the propose of the system programs?`

- **Layered Structure**  分层结构
Layered Structure is a type of system structure in which the different services of the operating systemare split into various layers, where each layer has a specific well-defined task to perform.分层结构是一种系统结构，其中[操作系统](https://www.geeksforgeeks.org/operating-systems/)的不同服务被分成不同的层，其中每一层都有一个特定的明确定义的任务要执行。


## QUIT	
 1. We have stressed the need for an operating system to make efficient use of the computing hardware. When is it appropriate for the operating system to forsake this principle and to “waste” resources? Why is such a system not really wasteful?
> Single-user systems should maximize use of the system for the user. A GUI might “waste” CPU cycles, but it optimizes the user’s interaction with the system.
> `GUI虽然比CLI消耗更多资源，但它的价值体现在提升了用户的操作效率和舒适感上。`
> Command-Line  (CLI), Graphics  User  Interface  (GUI)
 2. What is the main difficulty that a programmer must overcome in writing an operating system for a real-time environment?
 >The main difculty is keeping the operating system within the fixed time constraints of a real-time system. If the system does not complete a task in a certain time frame, it may cause a breakdown of the entire system.



<!--stackedit_data:
eyJwcm9wZXJ0aWVzIjoidGl0bGU6IHBpY1xuYXV0aG9yOiBmZW
lcbiIsImRpc2N1c3Npb25zIjp7IjFDOFAxTWFuekFvSkZVTjki
Onsic3RhcnQiOjI4NjAsImVuZCI6Mjk1MSwidGV4dCI6IldoYX
QgaXMgdGhlIHB1cnBvc2Ugb2YgdGhlIGNvbW1hbmQgaW50ZXJw
cmV0ZXI/IFdoeSBpcyBpdCB1c3VhbGx5IHNlcGFyYXRlIGZyb2
3igKYifSwiWDljSnBUOWRJTFYxcXZUYyI6eyJzdGFydCI6Mzg4
NCwiZW5kIjozOTI5LCJ0ZXh0IjoiYFdoYXQgaXMgdGhlIHByb3
Bvc2Ugb2YgdGhlIHN5c3RlbSBwcm9ncmFtcz9gIn19LCJjb21t
ZW50cyI6eyJubDM3d2Y4UkdTZlZVMHo5Ijp7ImRpc2N1c3Npb2
5JZCI6IjFDOFAxTWFuekFvSkZVTjkiLCJzdWIiOiJnbzoxMDUy
OTEzMDU1MTM4Mjk5ODkwMDciLCJ0ZXh0IjoiSXQgcmVhZHMgY2
9tbWFuZHMgZnJvbSB0aGUgdXNlciBvciBhIGZpbGUgYW5kIGV4
ZWN1dGVzIHRoZW0sIHR1cm5pbmcgdGhlbSBpbnRvIG9uZSBvci
Btb3JlIHN5c3RlbSBjYWxscy5cbiAgICBGb3Igc2VjdXJpdHkg
YW5kIGZsZXhpYmlsaXR5LCBhbmQgaW50ZXJwcmV0ZXIgbWF5L2
lzIHN1YmplY3QgdG8gY2hhbmdlLiIsImNyZWF0ZWQiOjE3MzQ4
NDg1NjM5MTV9LCI5V0QyNHZkTW1pY0lRNXVwIjp7ImRpc2N1c3
Npb25JZCI6Ilg5Y0pwVDlkSUxWMXF2VGMiLCJzdWIiOiJnbzox
MDUyOTEzMDU1MTM4Mjk5ODkwMDciLCJ0ZXh0IjoiU3lzdGVtIH
Byb2dyYW1zIGNhbiBiZSB0aG91Z2h0IG9mIGFzIGJ1bmRsZXMg
b2YgdXNlZnVsIHN5c3RlbSBjYWxscy4gVGhleSBwcm92aWRlIG
Jhc2ljIGZ1bmN0aW9uYWxpdHkgdG8gdXNlcnMgc28gdGhhdCB1
c2VycyBkbyBub3QgbmVlZCB0byB3cml0ZSB0aGVpciBvd24gcH
JvZ3JhbXMgdG8gc29sdmUgY29tbW9uIHByb2JsZW1zLlxu57O7
57uf56iL5bqP5Y+v5Lul6KKr55yL5L2c5piv5pyJ55So55qE57
O757uf6LCD55So55qE6ZuG5ZCI44CC5a6D5Lus5Li655So5oi3
5o+Q5L6b5Z+65pys5Yqf6IO977yM5L2/55So5oi35peg6ZyA57
yW5YaZ6Ieq5bex55qE56iL5bqP5p2l6Kej5Yaz5bi46KeB6Zeu
6aKY44CCIiwiY3JlYXRlZCI6MTczNDg0ODY3NjMwOH19LCJoaX
N0b3J5IjpbLTE3NTU4MTI5OTksLTE0MzA3NzkzMCwxNzEwNTQ5
NjkxLC0yMDExMjcwMzgwLC0xNTAxNzk1Mzg2LC01NDc3OTg1ND
gsNzQyMzMwMzIzLDY4ODkxMjQzNCwyMDA3OTU4ODYzLC02ODc3
ODk4NDIsNDIwMzExMDc5XX0=
-->