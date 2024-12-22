

## introduction
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

- bootstrap program



<!--stackedit_data:
eyJwcm9wZXJ0aWVzIjoidGl0bGU6IHBpY1xuYXV0aG9yOiBmZW
lcbiIsImRpc2N1c3Npb25zIjp7IjFDOFAxTWFuekFvSkZVTjki
Onsic3RhcnQiOjMyNjksImVuZCI6MzM2MCwidGV4dCI6IldoYX
QgaXMgdGhlIHB1cnBvc2Ugb2YgdGhlIGNvbW1hbmQgaW50ZXJw
cmV0ZXI/IFdoeSBpcyBpdCB1c3VhbGx5IHNlcGFyYXRlIGZyb2
3igKYifSwiWDljSnBUOWRJTFYxcXZUYyI6eyJzdGFydCI6NDI5
MywiZW5kIjo0MzM4LCJ0ZXh0IjoiYFdoYXQgaXMgdGhlIHByb3
Bvc2Ugb2YgdGhlIHN5c3RlbSBwcm9ncmFtcz9gIn0sImhpYUU0
ZVdTTW9hUUpqM0wiOnsic3RhcnQiOjUxNDUsImVuZCI6NTI2NS
widGV4dCI6IldoYXQgaXMgdGhlIG1haW4gYWR2YW50YWdlIG9m
IHRoZSBsYXllcmVkIGFwcHJvYWNoIHRvIHN5c3RlbSBkZXNpZ2
4/IFdoYXQgYXJlIHTigKYifSwiQnlpbE5KUmswaGc2aGlVaiI6
eyJzdGFydCI6NDAzLCJlbmQiOjYxNywidGV4dCI6ImBMaXN0IG
ZpdmUgc2VydmljZXMgcHJvdmlkZWQgYnkgYW4gb3BlcmF0aW5n
IHN5c3RlbSwgYW5kIGV4cGxhaW4gaG93IGVhY2ggY3JlYXTigK
YifX0sImNvbW1lbnRzIjp7Im5sMzd3ZjhSR1NmVlUwejkiOnsi
ZGlzY3Vzc2lvbklkIjoiMUM4UDFNYW56QW9KRlVOOSIsInN1Yi
I6ImdvOjEwNTI5MTMwNTUxMzgyOTk4OTAwNyIsInRleHQiOiJJ
dCByZWFkcyBjb21tYW5kcyBmcm9tIHRoZSB1c2VyIG9yIGEgZm
lsZSBhbmQgZXhlY3V0ZXMgdGhlbSwgdHVybmluZyB0aGVtIGlu
dG8gb25lIG9yIG1vcmUgc3lzdGVtIGNhbGxzLlxuICAgIEZvci
BzZWN1cml0eSBhbmQgZmxleGliaWxpdHksIGFuZCBpbnRlcnBy
ZXRlciBtYXkvaXMgc3ViamVjdCB0byBjaGFuZ2UuIiwiY3JlYX
RlZCI6MTczNDg0ODU2MzkxNX0sIjlXRDI0dmRNbWljSVE1dXAi
OnsiZGlzY3Vzc2lvbklkIjoiWDljSnBUOWRJTFYxcXZUYyIsIn
N1YiI6ImdvOjEwNTI5MTMwNTUxMzgyOTk4OTAwNyIsInRleHQi
OiJTeXN0ZW0gcHJvZ3JhbXMgY2FuIGJlIHRob3VnaHQgb2YgYX
MgYnVuZGxlcyBvZiB1c2VmdWwgc3lzdGVtIGNhbGxzLiBUaGV5
IHByb3ZpZGUgYmFzaWMgZnVuY3Rpb25hbGl0eSB0byB1c2Vycy
BzbyB0aGF0IHVzZXJzIGRvIG5vdCBuZWVkIHRvIHdyaXRlIHRo
ZWlyIG93biBwcm9ncmFtcyB0byBzb2x2ZSBjb21tb24gcHJvYm
xlbXMuXG7ns7vnu5/nqIvluo/lj6/ku6XooqvnnIvkvZzmmK/m
nInnlKjnmoTns7vnu5/osIPnlKjnmoTpm4blkIjjgILlroPku6
zkuLrnlKjmiLfmj5Dkvpvln7rmnKzlip/og73vvIzkvb/nlKjm
iLfml6DpnIDnvJblhpnoh6rlt7HnmoTnqIvluo/mnaXop6Plhr
PluLjop4Hpl67popjjgIIiLCJjcmVhdGVkIjoxNzM0ODQ4Njc2
MzA4fSwiMjR5SFAzZmtTVndLUFBtNCI6eyJkaXNjdXNzaW9uSW
QiOiJoaWFFNGVXU01vYVFKajNMIiwic3ViIjoiZ286MTA1Mjkx
MzA1NTEzODI5OTg5MDA3IiwidGV4dCI6IlRoZSBzeXN0ZW0gaX
MgZWFzaWVyIHRvIGRlYnVnIGFuZCBtb2RpZnkgYmVjYXVzZSBj
aGFuZ2VzIGFmZmVjdCBvbmx5IGxpbWl0ZWQgc2VjdGlvbnMgb2
YgdGhlIHN5c3RlbS5cbmRpc2FkdmFudGFnZSB0byB0aGUgbGF5
ZXJlZCBhcHByb2FjaCBpcyB0aGUgYXBvb3IgcGVyZm9ybWFuY2
UuIiwiY3JlYXRlZCI6MTczNDg1MDA1MDQ2OH0sImo4MVF0WVdx
VHdkb3k2TXYiOnsiZGlzY3Vzc2lvbklkIjoiaGlhRTRlV1NNb2
FRSmozTCIsInN1YiI6ImdvOjEwNTI5MTMwNTUxMzgyOTk4OTAw
NyIsInRleHQiOiJpdCBzZW5kcyBhIHJlcXVlc3QgdGhhdCBoYX
MgdG8gdHJhdmVsIHRocm91Z2ggYWxsIHRoZSBsYXllcnMgcHJl
c2VudCBpbiBiZXR3ZWVuIHRoZSB0d28gaW50ZXJhY3RpbmcgbG
F5ZXJzLiIsImNyZWF0ZWQiOjE3MzQ4NTAxOTIzNDB9LCI1cnhn
M3ZhSm9qTGwzeEFtIjp7ImRpc2N1c3Npb25JZCI6IkJ5aWxOSl
JrMGhnNmhpVWoiLCJzdWIiOiJnbzoxMDUyOTEzMDU1MTM4Mjk5
ODkwMDciLCJ0ZXh0IjoiUHJvZ3JhbSBleGVjdXRpb24uIFRoZS
BvcGVyYXRpbmcgc3lzdGVtIGxvYWRzIHRoZSBjb250ZW50cyAo
b3Igc2VjdGlvbnMpIG9mIGEgZmlsZSBpbnRvIG1lbW9yeSBhbm
QgYmVnaW5zIGl0cyBleGVjdXRpb24uIEEgdXNlci0gbGV2ZWwg
cHJvZ3JhbSBjb3VsZCBub3QgYmUgdHJ1c3RlZCB0byBwcm9wZX
JseSBhbGxvY2F0ZSBDUFUgdGltZS4gSS9PIG9wZXJhdGlvbnMu
IENvbW11bmljYXRpb25zLlxuRXJyb3IgZGV0ZWN0aW9uXG5GaW
xlLXN5c3RlbSBtYW5pcHVsYXRpb24iLCJjcmVhdGVkIjoxNzM0
ODUyNTM2Mjg0fSwiVTE3VjJHaldJOExkQW9pMiI6eyJkaXNjdX
NzaW9uSWQiOiJCeWlsTkpSazBoZzZoaVVqIiwic3ViIjoiZ286
MTA1MjkxMzA1NTEzODI5OTg5MDA3IiwidGV4dCI6IuaTjeS9nO
ezu+e7n+i0n+i0o+eoi+W6j+eahOWKoOi9veWSjOi/kOihjO+8
jOeUqOaIt+eoi+W6j+aXoOazleWPr+mdoOWcsOeuoeeQhiBDUF
Ug5pe26Ze044CC5a6D5aSE55CGIEkvTyDmk43kvZzvvIznlKjm
iLflj6rpnIDmjIflrprmk43kvZzvvIzns7vnu5/kvJrovazmja
LkuLrnoazku7bmjIfku6TvvIzpgb/lhY3nlKjmiLfnqIvluo/p
lJnor6/orr/pl67orr7lpIfmiJbotYTmupDjgILmlofku7bns7
vnu5/mk43kvZzlpoLliJvlu7rjgIHliKDpmaTlkozmnYPpmZDn
rqHnkIbnlLHmk43kvZzns7vnu5/lrozmiJDvvIznlKjmiLfml6
DpnIDlhbPlv4PlpI3mnYLnmoTnu4boioLjgILpgJrkv6Hml7bv
vIzmk43kvZzns7vnu5/otJ/otKPmlbDmja7miZPljIXjgIHkvK
DovpPlkozph43nu4TvvIznoa7kv53nvZHnu5zorr7lpIfljY/o
sIPkvb/nlKjjgILplJnor6/mo4DmtYvnlLHmk43kvZzns7vnu5
/nu5/kuIDlpITnkIbvvIzkv53miqTmlbDmja7lrozmlbTmgKfl
ubblh4/lsJHnlKjmiLfnqIvluo/nmoTlpI3mnYLmgKfjgIIiLC
JjcmVhdGVkIjoxNzM0ODUyNTQ3NzI1fX0sImhpc3RvcnkiOlst
MTE5NTg2OTc5MiwtMTMxMzQ3OTg4MywxOTQ2MjY0MzA0LC0xOD
c1MzYyMDYsOTY0NjUzNTQwLC0xNzc0NjUwMTg4LC0xNDMwNzc5
MzAsMTcxMDU0OTY5MSwtMjAxMTI3MDM4MCwtMTUwMTc5NTM4Ni
wtNTQ3Nzk4NTQ4LDc0MjMzMDMyMyw2ODg5MTI0MzQsMjAwNzk1
ODg2MywtNjg3Nzg5ODQyLDQyMDMxMTA3OV19
-->