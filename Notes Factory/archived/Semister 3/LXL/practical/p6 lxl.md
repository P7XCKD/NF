command name - command description
- replac all : %s/word1/word2/g 
to replace everything globally
ctrl + r = undo
u = undo
***
work to do today
write a c program using vi editor
***

To run a simple C file on a Linux system, you need to follow these steps: compile the file into an executable and then run the resulting executable. Here’s a straightforward guide on how to do this using common tools available on Linux:

### **1. Install a C Compiler**

First, ensure you have a C compiler installed. The most common compiler is `gcc` (GNU Compiler Collection). You can install it using your package manager if it’s not already installed.

For **Debian-based** distributions (like Ubuntu):
```bash
sudo apt update
sudo apt install gcc
```
password is : ```pass@123```


### **2. Compile the C File**

Assuming you have a C source file named `example.c`, you need to compile it into an executable. Use the following command:

```bash
gcc -o example example.c
```

Here’s what this command does:
- `gcc` invokes the compiler.
- `-o example` specifies the output file name (`example`).
- `example.c` is your C source file.

### **3. Run the Executable**

After compilation, you’ll have an executable file named `example` (or whatever name you specified). Run it using:

```bash
./example
```
