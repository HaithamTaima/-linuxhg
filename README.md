#include <stdio.h>

int main() {
    printf("Hello\n");
    return 0;
}
-----------
#include <stdio.h>
#include <unistd.h>

int main() {
    printf("قبل fork\n");
    fork();
    printf("بعد fork\n");
    return 0;
}

--------------------------------------------------
#include <stdio.h>
#include <unistd.h>

int main() {

    int n = fork();

    if (n == 0) {
        printf("I am Child\n");
    } else {
        printf("I am Parent\n");
    }

    return 0;
}
******************88****
#include <stdio.h>
#include <unistd.h>

int main() {

    printf("Before exec\n");

    execl("/bin/ls", "ls", NULL);

    printf("After exec\n"); // لن تنفذ

    return 0;
}
********************************************
#include <stdio.h>
#include <unistd.h>
#include <sys/wait.h>

int main() {

    int n = fork();

    if (n == 0) {
        printf("Child running\n");
    } else {
        wait(NULL);
        printf("Parent after child\n");
    }

    return 0;
}
**************************************************
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <sys/wait.h>

int main() {

    int n = fork();

    if (n == 0) {
        exit(5);
    } else {
        int status;
        wait(&status);
        printf("Child exit value = %d\n", WEXITSTATUS(status));
    }

    return 0;
}
