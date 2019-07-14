
Operating System Assignment 2 (18L-1860)

Installation Steps:

sudo apt-get update
sudo apt-get install qemu
git clone git://github.com/mit-pdos/xv6-public.git 6.826
cd 6.826/xv6-public
make
make qemu

Running Xv6 Shell:

make qemu

Part One: System Call tracing 

In syscall.c I declare a new array syscallnames same as syscalls. That store name of each system call. Inside function syscall when a new call comes, I fetch its name from syscallnames array. And when system call completed, return value of system call is in eax register. I simply print it using prinf statement.
 

Part Two: Date system call

1- syscall.h

In syscall.h a number is assigned to each system call. Already numbers from 1 to 21 are used. And for SYS_data I use the number 22.
  
2- syscall.c 

An entry for sys_date is added in both syscalls array and syscallname array. syscalls array use system call number as index and contain a pointer to implementation of that system call. In this file only the prototype for date system call added. And implementation in other file described in below section. 

3- sysproc.c 

Implementation of date system call is in this file. This implementation simply uses cmostime function that returns current time and date and return an rtcdate time object that is pushed on to stack. So, we can access it inside calling function later. 

4- Defs.h

prototype of date system call added in this file. 

5- User.h

In this file prototype of user function is added that user will use to invoke date system call. 

6- date.c 

New file added that contain the code given in the assignment question. And an print statement is added to print the current date. 

7- Usys.S

To make date identifier as public an entry is added for date system call in this file. This actually makes able to access date as label instead of date function.

8- Makefile

To make new date program available on xv6 shell, _date is added in UPROGS. 




