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

