

## introduction

*> **Turnaround Time**（周转时间）是衡量进程完成效率的重要指标之一，它表示一个进程从提交到完成所需的总时间。
> 
> ### **定义：**
> 
> 周转时间（Turnaround Time, TAT）是进程完成的时间（Finish Time, FT）减去其到达时间（Arrival
> Time, AT）的差值：
> 
> Turnaround Time=Completion Time−Arrival Time\text{Turnaround Time} =
> \text{Completion Time} - \text{Arrival Time}Turnaround Time=Completion
> Time−Arrival Time（跑完的时间-刚到的时间）
> 
> ### **解释：**
> 
> 1.  **到达时间（Arrival Time, AT）**：
>     -   进程到达系统、准备进入就绪队列的时间。
> 2.  **完成时间（Completion Time, CT）**：
>     -   进程完成所有任务并退出系统的时间。
> 3.  **周转时间**：
>     -   包括进程在就绪队列中等待、CPU 上执行，以及可能的 I/O 操作所花费的总时间。*

An operating system is software that acts as an intermediary between the user and computer hardware.
Operating systems provide an environment for execution of programs and services to programs and users

> programs: 进程
> allocate resources to programs 分配资源给进程
 - Computer system :  hardware,  operating system,  application programs,  user
 - Interrupts
 - Real-Time Embedded Systems

`List five services provided by an operating system, and explain how each creates convenience for users. In which cases would it be impossible for user-level programs to provide these services? Explain your answer`
> 
 - [ ] **嵌入式系统**是专门为某一特定功能设计的计算机系统，它通常嵌入在一个更大的设备中，例如  微波炉中的控制系统  汽车中的防抱死制动系统（ABS）
 - [ ] **实时系统**是指必须在规定的时间内完成某些任务的系统。
 - The basic unit of computer storage is the bit, which contain one 0 or 1, and a **byte** is 8 bits; a **kilobyte** or **KB** is 1024 bytes; a **megabyte (MB)** is 1024*1024 bytes; a **gigabyte (GB)** is 1024^3 bytes; a **terabyte (TB)** is 1024^4 bytes.
 - An operating system is software that manages the computer hardware, as well as providing an environment for application programs to run.
  `Why do some systems store the operating system in firmware, while others store it on disk?`

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
层的实现有一些规则，如下所示：
1.  The outermost layer must be the User Interface layer.  
    最外层必须是 User Interface 层。
2.  The innermost layer must be the Hardware layer.  
    最内层必须是 Hardware 层。
3.  A particular layer can access all the layers present below it but it cannot access the layers present above it. That is layer n-1 can access all the layers from n-2 to 0 but it cannot access the nth layer.  
    特定层可以访问其下方的所有层，但无法访问其上方的层。也就是说，第 n-1 层可以访问从 n-2 到 0 的所有层，但它无法访问第 n 层。
     What is the main advantage of the layered approach to system design? What are the disadvantages of the layered approach? 

## QUIT	
 1. We have stressed the need for an operating system to make efficient use of the computing hardware. When is it appropriate for the operating system to forsake this principle and to “waste” resources? Why is such a system not really wasteful?
> Single-user systems should maximize use of the system for the user. A GUI might “waste” CPU cycles, but it optimizes the user’s interaction with the system.
> `GUI虽然比CLI消耗更多资源，但它的价值体现在提升了用户的操作效率和舒适感上。`
> Command-Line  (CLI), Graphics  User  Interface  (GUI)
 2. What is the main difficulty that a programmer must overcome in writing an operating system for a real-time environment?
 >The main difculty is keeping the operating system within the fixed time constraints of a real-time system. If the system does not complete a task in a certain time frame, it may cause a breakdown of the entire system.

- **bootstrap program**引导程序
A bootstrap program is the first code that is executed when the computer system is started. The entire operating system depends on the bootstrap program to work correctly as it loads the operating system.  
引导程序是计算机系统启动时执行的第一个代码。整个操作系统依赖于引导程序在加载操作系统时正常工作。
`## How could a system be designed to allow a choice of operating systems from which to boot? What would the bootstrap program need to do?`



<!--stackedit_data:
eyJwcm9wZXJ0aWVzIjoidGl0bGU6IHBpY1xuYXV0aG9yOiBmZW
lcbiIsImRpc2N1c3Npb25zIjp7IjFDOFAxTWFuekFvSkZVTjki
Onsic3RhcnQiOjM4NDAsImVuZCI6MzkzMSwidGV4dCI6IldoYX
QgaXMgdGhlIHB1cnBvc2Ugb2YgdGhlIGNvbW1hbmQgaW50ZXJw
cmV0ZXI/IFdoeSBpcyBpdCB1c3VhbGx5IHNlcGFyYXRlIGZyb2
3igKYifSwiWDljSnBUOWRJTFYxcXZUYyI6eyJzdGFydCI6NDg2
NCwiZW5kIjo0OTA5LCJ0ZXh0IjoiYFdoYXQgaXMgdGhlIHByb3
Bvc2Ugb2YgdGhlIHN5c3RlbSBwcm9ncmFtcz9gIn0sImhpYUU0
ZVdTTW9hUUpqM0wiOnsic3RhcnQiOjU3MTYsImVuZCI6NTgzNi
widGV4dCI6IldoYXQgaXMgdGhlIG1haW4gYWR2YW50YWdlIG9m
IHRoZSBsYXllcmVkIGFwcHJvYWNoIHRvIHN5c3RlbSBkZXNpZ2
4/IFdoYXQgYXJlIHTigKYifSwiQnlpbE5KUmswaGc2aGlVaiI6
eyJzdGFydCI6OTc0LCJlbmQiOjExODgsInRleHQiOiJgTGlzdC
BmaXZlIHNlcnZpY2VzIHByb3ZpZGVkIGJ5IGFuIG9wZXJhdGlu
ZyBzeXN0ZW0sIGFuZCBleHBsYWluIGhvdyBlYWNoIGNyZWF04o
CmIn0sIm0xeWl2WWdzdU1NUGgxYXMiOnsic3RhcnQiOjE3MDks
ImVuZCI6MTgwMSwidGV4dCI6ImBXaHkgZG8gc29tZSBzeXN0ZW
1zIHN0b3JlIHRoZSBvcGVyYXRpbmcgc3lzdGVtIGluIGZpcm13
YXJlLCB3aGlsZSBvdGhlcnMgc3RvcmXigKYifSwibkxlaU13VV
NjTEsySnNhaCI6eyJzdGFydCI6Njk4MiwiZW5kIjo3MTIwLCJ0
ZXh0IjoiYCMjIEhvdyBjb3VsZCBhIHN5c3RlbSBiZSBkZXNpZ2
5lZCB0byBhbGxvdyBhIGNob2ljZSBvZiBvcGVyYXRpbmcgc3lz
dGVtcyBmcm9t4oCmIn19LCJjb21tZW50cyI6eyJubDM3d2Y4Uk
dTZlZVMHo5Ijp7ImRpc2N1c3Npb25JZCI6IjFDOFAxTWFuekFv
SkZVTjkiLCJzdWIiOiJnbzoxMDUyOTEzMDU1MTM4Mjk5ODkwMD
ciLCJ0ZXh0IjoiSXQgcmVhZHMgY29tbWFuZHMgZnJvbSB0aGUg
dXNlciBvciBhIGZpbGUgYW5kIGV4ZWN1dGVzIHRoZW0sIHR1cm
5pbmcgdGhlbSBpbnRvIG9uZSBvciBtb3JlIHN5c3RlbSBjYWxs
cy5cbiAgICBGb3Igc2VjdXJpdHkgYW5kIGZsZXhpYmlsaXR5LC
BhbmQgaW50ZXJwcmV0ZXIgbWF5L2lzIHN1YmplY3QgdG8gY2hh
bmdlLiIsImNyZWF0ZWQiOjE3MzQ4NDg1NjM5MTV9LCI5V0QyNH
ZkTW1pY0lRNXVwIjp7ImRpc2N1c3Npb25JZCI6Ilg5Y0pwVDlk
SUxWMXF2VGMiLCJzdWIiOiJnbzoxMDUyOTEzMDU1MTM4Mjk5OD
kwMDciLCJ0ZXh0IjoiU3lzdGVtIHByb2dyYW1zIGNhbiBiZSB0
aG91Z2h0IG9mIGFzIGJ1bmRsZXMgb2YgdXNlZnVsIHN5c3RlbS
BjYWxscy4gVGhleSBwcm92aWRlIGJhc2ljIGZ1bmN0aW9uYWxp
dHkgdG8gdXNlcnMgc28gdGhhdCB1c2VycyBkbyBub3QgbmVlZC
B0byB3cml0ZSB0aGVpciBvd24gcHJvZ3JhbXMgdG8gc29sdmUg
Y29tbW9uIHByb2JsZW1zLlxu57O757uf56iL5bqP5Y+v5Lul6K
Kr55yL5L2c5piv5pyJ55So55qE57O757uf6LCD55So55qE6ZuG
5ZCI44CC5a6D5Lus5Li655So5oi35o+Q5L6b5Z+65pys5Yqf6I
O977yM5L2/55So5oi35peg6ZyA57yW5YaZ6Ieq5bex55qE56iL
5bqP5p2l6Kej5Yaz5bi46KeB6Zeu6aKY44CCIiwiY3JlYXRlZC
I6MTczNDg0ODY3NjMwOH0sIjI0eUhQM2ZrU1Z3S1BQbTQiOnsi
ZGlzY3Vzc2lvbklkIjoiaGlhRTRlV1NNb2FRSmozTCIsInN1Yi
I6ImdvOjEwNTI5MTMwNTUxMzgyOTk4OTAwNyIsInRleHQiOiJU
aGUgc3lzdGVtIGlzIGVhc2llciB0byBkZWJ1ZyBhbmQgbW9kaW
Z5IGJlY2F1c2UgY2hhbmdlcyBhZmZlY3Qgb25seSBsaW1pdGVk
IHNlY3Rpb25zIG9mIHRoZSBzeXN0ZW0uXG5kaXNhZHZhbnRhZ2
UgdG8gdGhlIGxheWVyZWQgYXBwcm9hY2ggaXMgdGhlIGFwb29y
IHBlcmZvcm1hbmNlLiIsImNyZWF0ZWQiOjE3MzQ4NTAwNTA0Nj
h9LCJqODFRdFlXcVR3ZG95Nk12Ijp7ImRpc2N1c3Npb25JZCI6
ImhpYUU0ZVdTTW9hUUpqM0wiLCJzdWIiOiJnbzoxMDUyOTEzMD
U1MTM4Mjk5ODkwMDciLCJ0ZXh0IjoiaXQgc2VuZHMgYSByZXF1
ZXN0IHRoYXQgaGFzIHRvIHRyYXZlbCB0aHJvdWdoIGFsbCB0aG
UgbGF5ZXJzIHByZXNlbnQgaW4gYmV0d2VlbiB0aGUgdHdvIGlu
dGVyYWN0aW5nIGxheWVycy4iLCJjcmVhdGVkIjoxNzM0ODUwMT
kyMzQwfSwiNXJ4ZzN2YUpvakxsM3hBbSI6eyJkaXNjdXNzaW9u
SWQiOiJCeWlsTkpSazBoZzZoaVVqIiwic3ViIjoiZ286MTA1Mj
kxMzA1NTEzODI5OTg5MDA3IiwidGV4dCI6IlByb2dyYW0gZXhl
Y3V0aW9uLiBUaGUgb3BlcmF0aW5nIHN5c3RlbSBsb2FkcyB0aG
UgY29udGVudHMgKG9yIHNlY3Rpb25zKSBvZiBhIGZpbGUgaW50
byBtZW1vcnkgYW5kIGJlZ2lucyBpdHMgZXhlY3V0aW9uLiBBIH
VzZXItIGxldmVsIHByb2dyYW0gY291bGQgbm90IGJlIHRydXN0
ZWQgdG8gcHJvcGVybHkgYWxsb2NhdGUgQ1BVIHRpbWUuIEkvTy
BvcGVyYXRpb25zLiBDb21tdW5pY2F0aW9ucy5cbkVycm9yIGRl
dGVjdGlvblxuRmlsZS1zeXN0ZW0gbWFuaXB1bGF0aW9uIiwiY3
JlYXRlZCI6MTczNDg1MjUzNjI4NH0sIlUxN1YyR2pXSThMZEFv
aTIiOnsiZGlzY3Vzc2lvbklkIjoiQnlpbE5KUmswaGc2aGlVai
IsInN1YiI6ImdvOjEwNTI5MTMwNTUxMzgyOTk4OTAwNyIsInRl
eHQiOiLmk43kvZzns7vnu5/otJ/otKPnqIvluo/nmoTliqDovb
3lkozov5DooYzvvIznlKjmiLfnqIvluo/ml6Dms5Xlj6/pnaDl
nLDnrqHnkIYgQ1BVIOaXtumXtOOAguWug+WkhOeQhiBJL08g5p
ON5L2c77yM55So5oi35Y+q6ZyA5oyH5a6a5pON5L2c77yM57O7
57uf5Lya6L2s5o2i5Li656Gs5Lu25oyH5Luk77yM6YG/5YWN55
So5oi356iL5bqP6ZSZ6K+v6K6/6Zeu6K6+5aSH5oiW6LWE5rqQ
44CC5paH5Lu257O757uf5pON5L2c5aaC5Yib5bu644CB5Yig6Z
mk5ZKM5p2D6ZmQ566h55CG55Sx5pON5L2c57O757uf5a6M5oiQ
77yM55So5oi35peg6ZyA5YWz5b+D5aSN5p2C55qE57uG6IqC44
CC6YCa5L+h5pe277yM5pON5L2c57O757uf6LSf6LSj5pWw5o2u
5omT5YyF44CB5Lyg6L6T5ZKM6YeN57uE77yM56Gu5L+d572R57
uc6K6+5aSH5Y2P6LCD5L2/55So44CC6ZSZ6K+v5qOA5rWL55Sx
5pON5L2c57O757uf57uf5LiA5aSE55CG77yM5L+d5oqk5pWw5o
2u5a6M5pW05oCn5bm25YeP5bCR55So5oi356iL5bqP55qE5aSN
5p2C5oCn44CCIiwiY3JlYXRlZCI6MTczNDg1MjU0NzcyNX0sIj
BaQjlhYjlPUmphVk5XY3oiOnsiZGlzY3Vzc2lvbklkIjoibTF5
aXZZZ3N1TU1QaDFhcyIsInN1YiI6ImdvOjEwNTI5MTMwNTUxMz
gyOTk4OTAwNyIsInRleHQiOiJGb3IgY2VydGFpbiBkZXZpY2Vz
LCBzdWNoIGFzIGVtYmVkZGVkIHN5c3RlbXMsIGEgZGlzayB3aX
RoIGEgZmlsZSBzeXN0ZW0gbWF5IGJlIG5vdCBiZSBhdmFpbGFi
bGUgZm9yIHRoZSBkZXZpY2UuIEluIHRoaXMgc2l0dWF0aW9uLC
B0aGUgb3BlcmF0aW5nIHN5c3RlbSBtdXN0IGJlIHN0b3JlZCBp
biBmaXJtd2FyZS4iLCJjcmVhdGVkIjoxNzM0ODUzMDU5MTI0fS
wieWZCbEpGTXNpZ0RvaVdqSiI6eyJkaXNjdXNzaW9uSWQiOiJu
TGVpTXdVU2NMSzJKc2FoIiwic3ViIjoiZ286MTA1MjkxMzA1NT
EzODI5OTg5MDA3IiwidGV4dCI6InJ1biBib3RoIFdpbmRvd3Mg
YW5kIHRocmVlIGRpZmZlcmVudCBkaXN0cmlidXRpb25zIG9mIE
xpbnV4IChmb3IgZXhhbXBsZSwgUmVkSGF0LCBEZWJpYW4sIGFu
ZCBVYnVudHUpLiBFYWNoIG9wZXJhdGluZyBzeXN0ZW0gd2lsbC
BiZSBzdG9yZWQgb24gZGlzay4gRHVyaW5nIHN5c3RlbSBib290
LCBhIHNwZWNpYWwgcHJvZ3JhbSAod2hpY2ggd2Ugd2lsbCBjYW
xsIHRoZSAqKmJvb3QgbWFuYWdlcioqKSB3aWxsIGRldGVybWlu
ZSB3aGljaCBvcGVyYXRpbmcgc3lzdGVtIHRvIGJvb3QgaW50by
4iLCJjcmVhdGVkIjoxNzM0ODUzNDAxNzg4fSwiYjdqSGF3ZEVr
RGQ3Njh0ayI6eyJkaXNjdXNzaW9uSWQiOiJuTGVpTXdVU2NMSz
JKc2FoIiwic3ViIjoiZ286MTA1MjkxMzA1NTEzODI5OTg5MDA3
IiwidGV4dCI6Ikl0IGlzIHRoaXMgYm9vdCBtYW5hZ2VyIHRoYX
QgaXMgcmVzcG9uc2libGUgZm9yIGRldGVybWluaW5nIHdoaWNo
IHN5c3RlbSB0byBib290IGludG8uIiwiY3JlYXRlZCI6MTczND
g1MzQ0NDQyOX19LCJoaXN0b3J5IjpbMjUzODY4NDUxLC0xNzAz
NjkyNTA2LC0zODIxNjAyNjUsNDk1MjU5OTIzLC0xMzEzNDc5OD
gzLDE5NDYyNjQzMDQsLTE4NzUzNjIwNiw5NjQ2NTM1NDAsLTE3
NzQ2NTAxODgsLTE0MzA3NzkzMCwxNzEwNTQ5NjkxLC0yMDExMj
cwMzgwLC0xNTAxNzk1Mzg2LC01NDc3OTg1NDgsNzQyMzMwMzIz
LDY4ODkxMjQzNCwyMDA3OTU4ODYzLC02ODc3ODk4NDIsNDIwMz
ExMDc5XX0=
-->