#include <stdio.h>

int main() {
    printf("Hello\n");
    return 0;
}
-----------
#include <stdio.h>
#include <unistd.h>  // مكتبة fork()

int main() {
    printf("قبل fork\n");
    fork();  // إنشاء عملية ابن
    printf("بعد fork\n");
    return 0;
}
