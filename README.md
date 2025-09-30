# Linux-Process-API-fork-wait-exec-
Ex02-Linux Process API-fork(), wait(), exec()
# Ex02-OS-Linux-Process API - fork(), wait(), exec()
Operating systems Lab exercise


# AIM:
To write C Program that uses Linux Process API - fork(), wait(), exec()

# DESIGN STEPS:

### Step 1:

Navigate to any Linux environment installed on the system or installed inside a virtual environment like virtual box/vmware or online linux JSLinux (https://bellard.org/jslinux/vm.html?url=alpine-x86.cfg&mem=192) or docker.

### Step 2:

Write the C Program using Linux Process API - fork(), wait(), exec()

### Step 3:

Test the C Program for the desired output. 

# PROGRAM:

## C Program to print process ID and parent Process ID using Linux API system calls
```
#include <stdio.h>
#include <sys/types.h>
#include <unistd.h>
int main(void)
{	//variable to store calling function's process id
	pid_t process_id;
	//variable to store parent function's process id
	pid_t p_process_id;
	//getpid() - will return process id of calling function
	process_id = getpid();
	//getppid() - will return process id of parent function
	p_process_id = getppid();
	//printing the process ids

//printing the process ids
	printf("The process id: %d\n",process_id);
	printf("The process id of parent function: %d\n",p_process_id);
	return 0;
}
```
## OUTPUT
<img width="871" height="682" alt="Screenshot from 2025-09-30 11-37-47" src="https://github.com/user-attachments/assets/93152fe8-8160-4bd8-9694-c17eefaa0f55" />








## C Program to create new process using Linux API system calls fork() and exit()
```
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>  // Needed for fork(), getpid(), getppid(), sleep()

int main() {
    int pid;
    pid = fork();  // Create a new process

    if (pid == 0) {
        // Child process
        printf("I am the child, my PID is %d\n", getpid());
        printf("My parent PID is: %d\n", getppid());
        exit(0);
    } else if (pid > 0) {
        // Parent process
        printf("I am the parent, my PID is %d\n", getpid());
        sleep(100);  // Let the parent sleep so child becomes orphan after it exits
        exit(0);
    } else {
        // fork failed
        perror("fork");
        exit(1);
    }
}
```







## OUTPUT
<img width="1052" height="829" alt="Screenshot from 2025-09-30 11-40-18" src="https://github.com/user-attachments/assets/10f88bc6-99d3-4f70-8caa-e2f95755eaaf" />




## C Program to execute Linux system commands using Linux API system calls exec() family
```
#include <unistd.h>
#include <stdio.h>
#include <stdlib.h>
int main()
{
	printf("Running ps with execlp\n");
	execlp("ps", "ps", "ax", NULL);
	printf("Done.\n");
	exit(0);
}
```

## OUTPUT
<img width="1052" height="1007" alt="Screenshot from 2025-09-30 11-44-51" src="https://github.com/user-attachments/assets/daf76ce6-15f0-46b4-a3ab-29f5f57853d6" />












# RESULT:
The programs are executed successfully.
