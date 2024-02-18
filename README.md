# INTRODUCTION
This repository contatins step by step commands to install RISC-V 32-bit toolchain, SPIKE simulator and to run a program on SPIKE simulator.

## INSTALLING RISC-V TOOLCHAIN

First we have to download the RISC-V prebuilt toolchain, which can be downloaded from here [Toolchain](https://github.com/stnolting/riscv-gcc-prebuilt) 

Make a directory where you want to download the tooclchain

```bash
$ sudo mkdir /path/directory
$ cd Downloads
$ sudo tar -xzf TOOLCHAIN.tar.gz -C /path/directory
$ export PATH=$PATH:/path/directory/bin
```
Check wheather toolchain is downloaded or not.
```bash
riscv32-unknown-elf-gcc -v
```
Add the path variable in the end in .bashrc file and save it.
```bash
$ nano ~/.bashrc
$ export PATH=$PATH:/path/directory/bin
```
## INSTALLING SPIKE
SPIKE RISC-V simulator can be downloaded from here [SPIKE](https://github.com/riscv-software-src/riscv-isa-sim) 

Run the following commands, make sure in sixth command the path is correct of toolchain installation path.
```bash
$ apt-get install device-tree-compiler
$ git clone git@github.com:riscv-software-src/riscv-isa-sim.git
$ cd riscv-isa-sim
$ mkdir build
$ cd build
$ ../configure --prefix=/path/directory/bin
$ make
$ sudo make install
$ export PATH="/path/directory/riscv-isa-sim/build:$PATH"
```
Now add the path in .bashrc file
```bash
$ nano ~/.bashrc
$ export PATH="/path/directory/riscv-isa-sim/build:$PATH"
```

Now run to check if the SPIKE simulator is downloaded or not.
```bash
$ spike
```
## ASSEMBLING THE CODE
The GCC compiler would generate an executable file **SAMPLE**, which will execute on spike
```bash
riscv32-unknown-elf-gcc -march=rv32i_zicsr -mabi=ilp32 -o SAMPLE exception_handling.S -nostartfiles -L link.ld
```
## RUNNING ON SPIKE
Now we will run the executable file.
```bash
$ spike SAMPLE
```





