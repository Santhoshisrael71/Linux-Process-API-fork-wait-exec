# Linux-Process-API-fork-wait-exec-
Ex02-Linux Process API-fork(), wait(), exec()
# Ex02-OS-Linux-Process API - fork(), wait(), exec()
Operating systems Lab exercise


# AIM:
To write C Program that uses Linux Process API - fork(), wait(), exec()

```
DEVELOPED BY:
NAME: Santhosh P
REG NO:212224220088
```

# DESIGN STEPS:

### Step 1:

Navigate to any Linux environment installed on the system or installed inside a virtual environment like virtual box/vmware or online linux JSLinux (https://bellard.org/jslinux/vm.html?url=alpine-x86.cfg&mem=192) or docker.

### Step 2:

Write the C Program using Linux Process API - fork(), wait(), exec()

### Step 3:

Test the C Program for the desired output. 

## C Program to print process ID and parent Process ID using Linux API system calls
# PROGRAM:

## CODE :
```
#include <stdio.h>
#include <sys/types.h>
#include <unistd.h>
int main(void)
{	gcc 
	pid_t process_id;
	pid_t p_process_id;
	process_id = getpid();
	p_process_id = getppid();


	printf("The process id: %d\n",process_id);
	printf("The process id of parent function: %d\n",p_process_id);
	return 0;
 }
```
## OUTPUT :
![image](https://github.com/user-attachments/assets/25e03231-53b9-4734-bccb-c2d2150ee183)
clclea

## C Program to create new process using Linux API system calls fork() and exit()
## CODE :
```
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <sys/wait.h>  

int main() {
    pid_t pid = fork();

    if (pid < 0) {
        perror("Fork failed");
        exit(1);
    }

    if (pid == 0) {
        printf("I am child, my PID is %d\n", getpid());
        printf("My parent PID is: %d\n", getppid());
        sleep(2);  
    } else {
        printf("I am parent, my PID is %d\n", getpid());
        wait(NULL);  
    }

    return 0;
}

```

## OUTPUT
![image](https://github.com/user-attachments/assets/90528423-acfa-4785-a77d-263cd26e6f3f)





## C Program to execute Linux system commands using Linux API system calls exec() family
## CODE

```
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <sys/types.h>
#include <sys/wait.h>

int main() {
    int status;
    pid_t pid;
    printf("Running ps with execl (no path)\n");
    pid = fork();
    if (pid == 0) {
        execl("ps", "ps", "ax", NULL);  
        perror("execl failed");
        exit(1);
    } else {
        wait(&status);
        if (WIFEXITED(status))
            printf("Child exited with status of %d\n", WEXITSTATUS(status));
        else
            puts("Child did not exit successfully");
    }

    printf("Running ps with execl (with /bin/ps path)\n");
    pid = fork();
    if (pid == 0) {
        execl("/bin/ps", "ps", "ax", NULL); 
        perror("execl failed");
        exit(1);
    } else {
        wait(&status);
        if (WIFEXITED(status))
            printf("Child exited with status of %d\n", WEXITSTATUS(status));
        else
            puts("Child did not exit successfully");
    }

    printf("Done.\n");
    return 0;
}


```

## OUTPUT
![image](https://github.com/user-attachments/assets/295e5d8e-f965-4251-b6f5-bea5e23e652a)
![image](https://github.com/user-attachments/assets/143e5ec7-142d-476a-a346-127eba00b13b)
![image](https://github.com/user-attachments/assets/9903b163-3b31-49eb-9a64-2e31f53fbce4)

# RESULT:
The programs are executed successfully.
