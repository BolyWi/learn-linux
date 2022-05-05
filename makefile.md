# makefile使用方法
```makefile
all:program0 program1 program2 ... 

program0:program0.c
        gcc -o program0 program0.c

program1:program1.c head1.h head.c
        gcc -o program1 program1.c head.c

clean:
        rm -f program0 program1

```