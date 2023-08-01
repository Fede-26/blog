---
title: "Tps per aprile"
date: 2021-04-24T12:14:21+01:00
categories: Notes
tags:
    - "Sistemi operativi"
    - "School"
    - TPS
draft: true
---
{{< katex >}}


# Virtual memory

_Pagina 69_

> Virtual memory gives the ability to run programs larger than the machine's physical memory by moving pieces back and forth between RAM and disk.

I processi nella swap devono essere spostati in RAM prima di poter essere eseguiti.

> It also enabled the ability to have a program dynamically link in a library at run time instead of having it compiled in.

Questo permette di avere eseguibili più piccoli, con lo svantaggio di dover tenere aggiornate le librerie installate a livello globale.

> The operating systems have two main functions: providing abstractions to user programs and managing the computer's resources.

# System calls

_Pagina 70_

## POSIX

[Wikipedia](https://en.wikipedia.org/wiki/POSIX)



>   The Portable Operating System Interface (POSIX) is a family of standards specified by the IEEE Computer Society for maintaining compatibility between operating systems. POSIX defines the application programming interface (API), along with command line shells and utility interfaces, for software compatibility with variants of Unix and other operating systems.

## read

>   It has three parameters: the first one specifying the file, the second one pointing to the buffer, and the third one giving the number of bytes to read. Like nearly all system calls, it is invoked from C programs by calling a library procedure with the same name as the system call: `read`. 

```c
count = read(fd, buffer, nbytes);
```

La chiamata ritorna il numero di bytes effettivamente letti in `count`. Normalmente la grandezza è uguale a `nbytes`, ma può essere minore se, per esempio, si incontra un _EOF_ durante la lettura.

Se la lettura non può essere effettuata, sia per un parametro invalido, sia per un errore del disco, `count` sarà uguale a _-1_ e il numero di errore verrà messo nella variabile globale `errno`.



![](/img/tps/syscall-read-2021-04-25_12-15.png)

1.  System calls are performed in a series of steps. In preparation for calling the read library procedure, which actually makes the read system call, the calling program first pushes the parameters onto the stack.

    >   C and C++ compilers push the parameters onto the stack in reverse order for historical reasons (having to do with making the first parameter to printf, the format string, appear on top of the stack).

    

    >   The first and third parameters are called by value, but the second parameter is passed by reference, meaning that the address of the buffer (indicated by &) is passed, not the contents of the buffer.

2.  ...

3.  ...

4.  Then comes the actual call to the library procedure (__step 4__). 

5.  This instruction is the normal procedure call instruction used to call all procedures. The library procedure, possibly written in assembly language, typically puts the system call number in a place where the operating system expects it, such as a register (__step 5__).

6.  Then it executes a TRAP instruction to switch from user mode to kernel mode and start execution at a fixed address within the kernel (__step 6__). The TRAP instruction is actually fairly similar to the procedure call instruction in the sense that the instruction following it is taken from a distant location and the return address is saved on the stack for use later. 

7.  The kernel code that starts following the TRAP examines the system call number and then dispatches to the correct system call handler, usually via a table of pointers to system call handlers indexed on system call number (__step 7__).

8.  At that point the system call handler runs (__step 8__).

9.  Once the system call handler has completed its work, control may be returned to the user-space library procedure at the instruction following the TRAP instruction (__step 9__).

10.  This procedure then returns to the user program in the usual way procedure calls return (__step 10__).

11.  To finish the job, the user program has to clean up the stack, as it does after any procedure call (__step 11__).  Assuming the stack grows downward, as it often does, the compiled code increments the stack pointer exactly enough to remove the parameters pushed before the call to read. The program is now free to do whatever it wants to do next.

     


### Differenze tra instruzioni TRAP e procedure call

>   Nevertheless, the TRAP instruction also differs from the procedure call instruction in two fundamental ways. First, as a side effect, it switches into kernel mode. The procedure call instruction does not change the mode. Second, rather than giving a relative or absolute address where the procedure is located, the TRAP instruction cannot jump to an arbitrary address. Depending on the architecture, it either jumps to a single fixed location, there is an 8-bit field in the instruction giving the index into a table in memory containing jump addresses, or equivalent.

## System calls principali su sistemi POSIX

### Process management

| Call                                  | Description                                    |
| ------------------------------------- | ---------------------------------------------- |
| pid = fork( )                         | Create a child process identical to the parent |
| pid = waitpid(pid, &statloc, options) | Wait for a child to terminate                  |
| s = execve(name, argv, environp)      | Replace a process' core image                  |
| exit(status)                          | Terminate process execution and return status  |

### File management

| Call                                 | Description                               |
| ------------------------------------ | ----------------------------------------- |
| fd = open(file, how, ...)            | Open a file for reading, writing, or both |
| s = close(fd)                        | Close an open file                        |
| n = read(fd, buffer, nbytes)         | Read data from a file into a buffer       |
| n = write(fd, buffer, nbytes)        | Write data from a buffer into a file      |
| position = Iseek(fd, offset, whence) | Move the file pointer                     |
| s = stat(name, &buf)                 | Get a file's status information           |

### Directory and file system management

| Call                           | Description                                  |
| ------------------------------ | -------------------------------------------- |
| s = mkdir(name, mode)          | Create a new directory                       |
| s = rmdir(name)                | Remove an empty directory                    |
| s = link(name1, name2)         | Create a new entry, name2, pointing to namel |
| s = unlink(name)               | Remove a directory entry                     |
| s = mount(special, name, flag) | Mount a file system                          |
| s = umount(special)            | Unmount a file system                        |

### Miscellaneous

| Call                     | Description                             |
| :----------------------- | --------------------------------------- |
| s = chdir(dirname)       | Change the working directory            |
| s = chmod(name, mode)    | Change a file's protection bits         |
| s = kill(pid, signal)    | Send a signal to a process              |
| seconds = time(&seconds) | Get the elapsed time since Jan. 1, 1970 |

>   The return code _s_ is _-1_ if an error has occurred. The return codes are as follows: _pid_ is a process id, _fd_ is a file descriptor, _n_ is a byte count, _position_ is an offset within the file, and _seconds_ is the elapsed time. The parameters are explained in the text.

# Differenza tra un sistema a 64 bit e 32 bit

In un sistema a 64 bit i bus hanno una grandezza di 64.
TODO: finire

# Digressioni

_EOF_ è un carattere ascii che rappresenta la fine di un file. In console equivale a _Ctrl+D_