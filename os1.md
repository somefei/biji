

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
    It reads commands from the user or a file and executes them, turning them into one or more system calls.
    For security and flexibility, and interpreter may/is subject to change.
- To start a new process, the shell executes a fork() system call. Then, the selected program is loaded into memory via an exec() system call, and the program is executed.
通常，`fork()` 和 `exec()` 是配合使用的。典型的操作流程是：

1.  父进程调用 `fork()` 创建一个子进程。
2.  子进程调用 `exec()` 来加载并执行新的程序。

` What system calls have to be executed by a command interpreter or shell in order to start a new process on a UNIX system? `
`1. The parent process calls 'fork()' to create a child process.
2. The child process calls 'exec()' to load and execute the new program.`

- **system programs**

## QUIT	
 1. We have stressed the need for an operating system to make efficient use of the computing hardware. When is it appropriate for the operating system to forsake this principle and to “waste” resources? Why is such a system not really wasteful?
> Single-user systems should maximize use of the system for the user. A GUI might “waste” CPU cycles, but it optimizes the user’s interaction with the system.
> `GUI虽然比CLI消耗更多资源，但它的价值体现在提升了用户的操作效率和舒适感上。`
> Command-Line  (CLI), Graphics  User  Interface  (GUI)
 2. What is the main difficulty that a programmer must overcome in writing an operating system for a real-time environment?
 >The main difculty is keeping the operating system within the fixed time constraints of a real-time system. If the system does not complete a task in a certain time frame, it may cause a breakdown of the entire system.



<!--stackedit_data:
eyJwcm9wZXJ0aWVzIjoidGl0bGU6IHBpY1xuYXV0aG9yOiBmZW
lcbiIsImhpc3RvcnkiOlsyMDQ3MzE4MDU2LDE3MTA1NDk2OTEs
LTIwMTEyNzAzODAsLTE1MDE3OTUzODYsLTU0Nzc5ODU0OCw3ND
IzMzAzMjMsNjg4OTEyNDM0LDIwMDc5NTg4NjMsLTY4Nzc4OTg0
Miw0MjAzMTEwNzldfQ==
-->