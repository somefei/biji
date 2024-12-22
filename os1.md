

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

- **bootstrap program**引导程序
A bootstrap program is the first code that is executed when the computer system is started. The entire operating system depends on the bootstrap program to work correctly as it loads the operating system.  
引导程序是计算机系统启动时执行的第一个代码。整个操作系统依赖于引导程序在加载操作系统时正常工作。
`## How could a system be designed to allow a choice of operating systems from which to boot? What would the bootstrap program need to do?`



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
YifSwibTF5aXZZZ3N1TU1QaDFhcyI6eyJzdGFydCI6MTEzOCwi
ZW5kIjoxMjMwLCJ0ZXh0IjoiYFdoeSBkbyBzb21lIHN5c3RlbX
Mgc3RvcmUgdGhlIG9wZXJhdGluZyBzeXN0ZW0gaW4gZmlybXdh
cmUsIHdoaWxlIG90aGVycyBzdG9yZeKApiJ9LCJuTGVpTXdVU2
NMSzJKc2FoIjp7InN0YXJ0Ijo2NDExLCJlbmQiOjY1NDksInRl
eHQiOiJgIyMgSG93IGNvdWxkIGEgc3lzdGVtIGJlIGRlc2lnbm
VkIHRvIGFsbG93IGEgY2hvaWNlIG9mIG9wZXJhdGluZyBzeXN0
ZW1zIGZyb23igKYifX0sImNvbW1lbnRzIjp7Im5sMzd3ZjhSR1
NmVlUwejkiOnsiZGlzY3Vzc2lvbklkIjoiMUM4UDFNYW56QW9K
RlVOOSIsInN1YiI6ImdvOjEwNTI5MTMwNTUxMzgyOTk4OTAwNy
IsInRleHQiOiJJdCByZWFkcyBjb21tYW5kcyBmcm9tIHRoZSB1
c2VyIG9yIGEgZmlsZSBhbmQgZXhlY3V0ZXMgdGhlbSwgdHVybm
luZyB0aGVtIGludG8gb25lIG9yIG1vcmUgc3lzdGVtIGNhbGxz
LlxuICAgIEZvciBzZWN1cml0eSBhbmQgZmxleGliaWxpdHksIG
FuZCBpbnRlcnByZXRlciBtYXkvaXMgc3ViamVjdCB0byBjaGFu
Z2UuIiwiY3JlYXRlZCI6MTczNDg0ODU2MzkxNX0sIjlXRDI0dm
RNbWljSVE1dXAiOnsiZGlzY3Vzc2lvbklkIjoiWDljSnBUOWRJ
TFYxcXZUYyIsInN1YiI6ImdvOjEwNTI5MTMwNTUxMzgyOTk4OT
AwNyIsInRleHQiOiJTeXN0ZW0gcHJvZ3JhbXMgY2FuIGJlIHRo
b3VnaHQgb2YgYXMgYnVuZGxlcyBvZiB1c2VmdWwgc3lzdGVtIG
NhbGxzLiBUaGV5IHByb3ZpZGUgYmFzaWMgZnVuY3Rpb25hbGl0
eSB0byB1c2VycyBzbyB0aGF0IHVzZXJzIGRvIG5vdCBuZWVkIH
RvIHdyaXRlIHRoZWlyIG93biBwcm9ncmFtcyB0byBzb2x2ZSBj
b21tb24gcHJvYmxlbXMuXG7ns7vnu5/nqIvluo/lj6/ku6Xooq
vnnIvkvZzmmK/mnInnlKjnmoTns7vnu5/osIPnlKjnmoTpm4bl
kIjjgILlroPku6zkuLrnlKjmiLfmj5Dkvpvln7rmnKzlip/og7
3vvIzkvb/nlKjmiLfml6DpnIDnvJblhpnoh6rlt7HnmoTnqIvl
uo/mnaXop6PlhrPluLjop4Hpl67popjjgIIiLCJjcmVhdGVkIj
oxNzM0ODQ4Njc2MzA4fSwiMjR5SFAzZmtTVndLUFBtNCI6eyJk
aXNjdXNzaW9uSWQiOiJoaWFFNGVXU01vYVFKajNMIiwic3ViIj
oiZ286MTA1MjkxMzA1NTEzODI5OTg5MDA3IiwidGV4dCI6IlRo
ZSBzeXN0ZW0gaXMgZWFzaWVyIHRvIGRlYnVnIGFuZCBtb2RpZn
kgYmVjYXVzZSBjaGFuZ2VzIGFmZmVjdCBvbmx5IGxpbWl0ZWQg
c2VjdGlvbnMgb2YgdGhlIHN5c3RlbS5cbmRpc2FkdmFudGFnZS
B0byB0aGUgbGF5ZXJlZCBhcHByb2FjaCBpcyB0aGUgYXBvb3Ig
cGVyZm9ybWFuY2UuIiwiY3JlYXRlZCI6MTczNDg1MDA1MDQ2OH
0sImo4MVF0WVdxVHdkb3k2TXYiOnsiZGlzY3Vzc2lvbklkIjoi
aGlhRTRlV1NNb2FRSmozTCIsInN1YiI6ImdvOjEwNTI5MTMwNT
UxMzgyOTk4OTAwNyIsInRleHQiOiJpdCBzZW5kcyBhIHJlcXVl
c3QgdGhhdCBoYXMgdG8gdHJhdmVsIHRocm91Z2ggYWxsIHRoZS
BsYXllcnMgcHJlc2VudCBpbiBiZXR3ZWVuIHRoZSB0d28gaW50
ZXJhY3RpbmcgbGF5ZXJzLiIsImNyZWF0ZWQiOjE3MzQ4NTAxOT
IzNDB9LCI1cnhnM3ZhSm9qTGwzeEFtIjp7ImRpc2N1c3Npb25J
ZCI6IkJ5aWxOSlJrMGhnNmhpVWoiLCJzdWIiOiJnbzoxMDUyOT
EzMDU1MTM4Mjk5ODkwMDciLCJ0ZXh0IjoiUHJvZ3JhbSBleGVj
dXRpb24uIFRoZSBvcGVyYXRpbmcgc3lzdGVtIGxvYWRzIHRoZS
Bjb250ZW50cyAob3Igc2VjdGlvbnMpIG9mIGEgZmlsZSBpbnRv
IG1lbW9yeSBhbmQgYmVnaW5zIGl0cyBleGVjdXRpb24uIEEgdX
Nlci0gbGV2ZWwgcHJvZ3JhbSBjb3VsZCBub3QgYmUgdHJ1c3Rl
ZCB0byBwcm9wZXJseSBhbGxvY2F0ZSBDUFUgdGltZS4gSS9PIG
9wZXJhdGlvbnMuIENvbW11bmljYXRpb25zLlxuRXJyb3IgZGV0
ZWN0aW9uXG5GaWxlLXN5c3RlbSBtYW5pcHVsYXRpb24iLCJjcm
VhdGVkIjoxNzM0ODUyNTM2Mjg0fSwiVTE3VjJHaldJOExkQW9p
MiI6eyJkaXNjdXNzaW9uSWQiOiJCeWlsTkpSazBoZzZoaVVqIi
wic3ViIjoiZ286MTA1MjkxMzA1NTEzODI5OTg5MDA3IiwidGV4
dCI6IuaTjeS9nOezu+e7n+i0n+i0o+eoi+W6j+eahOWKoOi9ve
WSjOi/kOihjO+8jOeUqOaIt+eoi+W6j+aXoOazleWPr+mdoOWc
sOeuoeeQhiBDUFUg5pe26Ze044CC5a6D5aSE55CGIEkvTyDmk4
3kvZzvvIznlKjmiLflj6rpnIDmjIflrprmk43kvZzvvIzns7vn
u5/kvJrovazmjaLkuLrnoazku7bmjIfku6TvvIzpgb/lhY3nlK
jmiLfnqIvluo/plJnor6/orr/pl67orr7lpIfmiJbotYTmupDj
gILmlofku7bns7vnu5/mk43kvZzlpoLliJvlu7rjgIHliKDpma
TlkozmnYPpmZDnrqHnkIbnlLHmk43kvZzns7vnu5/lrozmiJDv
vIznlKjmiLfml6DpnIDlhbPlv4PlpI3mnYLnmoTnu4boioLjgI
LpgJrkv6Hml7bvvIzmk43kvZzns7vnu5/otJ/otKPmlbDmja7m
iZPljIXjgIHkvKDovpPlkozph43nu4TvvIznoa7kv53nvZHnu5
zorr7lpIfljY/osIPkvb/nlKjjgILplJnor6/mo4DmtYvnlLHm
k43kvZzns7vnu5/nu5/kuIDlpITnkIbvvIzkv53miqTmlbDmja
7lrozmlbTmgKflubblh4/lsJHnlKjmiLfnqIvluo/nmoTlpI3m
nYLmgKfjgIIiLCJjcmVhdGVkIjoxNzM0ODUyNTQ3NzI1fSwiMF
pCOWFiOU9SamFWTldjeiI6eyJkaXNjdXNzaW9uSWQiOiJtMXlp
dllnc3VNTVBoMWFzIiwic3ViIjoiZ286MTA1MjkxMzA1NTEzOD
I5OTg5MDA3IiwidGV4dCI6IkZvciBjZXJ0YWluIGRldmljZXMs
IHN1Y2ggYXMgZW1iZWRkZWQgc3lzdGVtcywgYSBkaXNrIHdpdG
ggYSBmaWxlIHN5c3RlbSBtYXkgYmUgbm90IGJlIGF2YWlsYWJs
ZSBmb3IgdGhlIGRldmljZS4gSW4gdGhpcyBzaXR1YXRpb24sIH
RoZSBvcGVyYXRpbmcgc3lzdGVtIG11c3QgYmUgc3RvcmVkIGlu
IGZpcm13YXJlLiIsImNyZWF0ZWQiOjE3MzQ4NTMwNTkxMjR9LC
J5ZkJsSkZNc2lnRG9pV2pKIjp7ImRpc2N1c3Npb25JZCI6Im5M
ZWlNd1VTY0xLMkpzYWgiLCJzdWIiOiJnbzoxMDUyOTEzMDU1MT
M4Mjk5ODkwMDciLCJ0ZXh0IjoicnVuIGJvdGggV2luZG93cyBh
bmQgdGhyZWUgZGlmZmVyZW50IGRpc3RyaWJ1dGlvbnMgb2YgTG
ludXggKGZvciBleGFtcGxlLCBSZWRIYXQsIERlYmlhbiwgYW5k
IFVidW50dSkuIEVhY2ggb3BlcmF0aW5nIHN5c3RlbSB3aWxsIG
JlIHN0b3JlZCBvbiBkaXNrLiBEdXJpbmcgc3lzdGVtIGJvb3Qs
IGEgc3BlY2lhbCBwcm9ncmFtICh3aGljaCB3ZSB3aWxsIGNhbG
wgdGhlICoqYm9vdCBtYW5hZ2VyKiopIHdpbGwgZGV0ZXJtaW5l
IHdoaWNoIG9wZXJhdGluZyBzeXN0ZW0gdG8gYm9vdCBpbnRvLi
IsImNyZWF0ZWQiOjE3MzQ4NTM0MDE3ODh9fSwiaGlzdG9yeSI6
WzIwMzY4NjI3NDAsNDk1MjU5OTIzLC0xMzEzNDc5ODgzLDE5ND
YyNjQzMDQsLTE4NzUzNjIwNiw5NjQ2NTM1NDAsLTE3NzQ2NTAx
ODgsLTE0MzA3NzkzMCwxNzEwNTQ5NjkxLC0yMDExMjcwMzgwLC
0xNTAxNzk1Mzg2LC01NDc3OTg1NDgsNzQyMzMwMzIzLDY4ODkx
MjQzNCwyMDA3OTU4ODYzLC02ODc3ODk4NDIsNDIwMzExMDc5XX
0=
-->