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
