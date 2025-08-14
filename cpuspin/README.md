# Introduction to Operating Systems

Compiled using `gcc -o cpu cpu.c -Wall`
Invoked with syntax `./cpu "char"`

The example involves running multiple instances and observing the returned patterns, i.e.:
`./cpu A & ./cpu B & ./cpu C & ./cpu D &`
To observe the results of multiple processes running on a single physical CPU.

This program will continuously loop and should be exited with "Control-c" or terminating the PID. 

The code in `cpu.c` has been altered slightly to compile on x86_64 by replacing the following:
1. replace `#include "common.h"` with `#include <unistd.h>`
2. the above swap means we switch out `Spin(1)` for `sleep(1)` 
