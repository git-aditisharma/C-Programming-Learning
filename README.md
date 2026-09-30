# Lecture 1: C Compilation Pipeline or Stages

**Date:** September 27, 2026
**Topic:** Understanding 4-Stage C Compilation

Learning the 4-stage GCC compilation pipeline from Programming & Operating Systems class.

## What I Accomplished

I successfully completed all 4 stages of C compilation in Kali Linux:

1. ✅ **Preprocessing** - Expanded headers
2. ✅ **Compilation** - Generated assembly
3. ✅ **Assembly** - Created object file
4. ✅ **Linking** - Created executable


## My Source Code
```
#include<stdio.h>
#include<stdlib.h>
#include<math.h>

int global_var=10;

int main()
{
    printf("this is a test file\n");
    return 0;
}
```

### Stage 1: Preprocessing
- **Command:** `gcc -E aditi.c -o aditi.i`
- **What it does:** Expands header files (#include)
- **Output file:** `.i` (looks like text)
- **Screenshot:** See Stage 1 Preprocess.png

### Stage 2: Compilation
- **Command:** `gcc -S aditi.i -o aditi.s`
- **What it does:** Converts C to assembly language
- **Output file:** `.s` (human-readable CPU instructions)
- **Screenshot:** See Stage 2 Compile.png

### Stage 3: Assembly
- **Command:** `gcc -c aditi.s -o aditi.o`
- **What it does:** Converts assembly to machine code (binary)
- **Output file:** `.o` (binary - object file)
- **Screenshot:** See Stage 3 Assemble.png

### Stage 4: Linking
- **Command:** `gcc aditi.o -o aditi`
- **What it does:** Combines object file with libraries → creates executable
- **Output file:** `aditi` (the runnable program!)
- **Screenshot:** See Stage 4 Link.png

---

## The Flow

aditi.c (source code)
↓ gcc -E
aditi.i (preprocessed)
↓ gcc -S
aditi.s (assembly)
↓ gcc -c
aditi.o (object file)
↓ gcc -o
aditi (EXECUTABLE WHICH RUNS!)

## Key Takeaway

- Each stage **transforms** the code
- I can stop at any stage for debugging
- The final executable needs ALL 4 stages
---
# Lecture 2: Operating System Concepts

**Date:** [Today's Date]  
**Topic:** Control Flow, I/O Streams, Exit Codes, Process IDs, Long-Running Processes

---

## Task 1: Testing Control Flow (if/else statements)

![Testing Control Flow](Testing_Control_Flow.png)

### What It Does
Program asks user for input (1 or 0) and:
- If input is **1** → prints "Continuing..." and returns 0 (success)
- If input is **0** → prints "Exiting..." and returns 1 (failure)

### Code
```c
#include <stdio.h>
#include <unistd.h>

int main() {
    int choice;
    
    // Print PID at start
    printf("Current PID: %d\n", getpid());
    
    printf("Do you want to continue? (1 for Yes, 0 for No): ");
    scanf("%d", &choice);
    
    if (choice == 1) {
        printf("Continuing...\n");
        sleep(5);
        return 0;  // Success
    }
    else {
        printf("Exiting...\n");
        return 1;  // Failure
    }
}
```

### How to Run
```bash
gcc conditional.c -o task5
./task5
```

### Key Concept
**Control flow** = Making decisions in code using if/else statements

---

## Task 2: Standard I/O Streams

![Standard I/O Streams](Standard_I_O_Streams.png)

### What It Does
Program takes user input (name) and displays it:
- Uses `scanf()` to read input from standard input (stdin)
- Uses `printf()` to write output to standard output (stdout)

### Code
```c
#include <stdio.h>

int main() {
    char name[50];
    
    printf("Enter your name: ");
    // Read string from standard input
    scanf("%s", name);
    
    printf("Hello, %s! Welcome to OS Class.\n", name);
    return 0;
}
```

### How to Run
```bash
gcc io_stream.c -o task4
./task4
```

### Input/Output Example
I am starting ...
I am finished.

---
### Key Concept
**Long-running processes** = Programs that take time to complete

---

## Summary of All 5 Tasks

| Task | Program | Learns | Key Command |
|------|---------|--------|-------------|
| 1 | c_source.c | Long-running processes | `./task1 &` (background) |
| 2 | ppid.c | PID & PPID | `getpid()`, `getppid()` |
| 3 | exitcode.c | Exit codes | `echo $?` |
| 4 | io_stream.c | Input/Output | `scanf()`, `printf()` |
| 5 | conditional.c | Control flow | if/else statements |

---

## What I Learned

✅ How programs communicate with Operating System  
✅ What PIDs and PPIDs are  
✅ How input/output works  
✅ How exit codes tell OS if program succeeded  
✅ How to run processes in background  

---

## Commands I Used

```bash
gcc <filename>.c -o <executable>  # Compile
./<executable>                     # Run in foreground
./<executable> &                   # Run in background
ps aux | grep <name>              # See running processes
echo $?                           # Check last exit code
```

---

