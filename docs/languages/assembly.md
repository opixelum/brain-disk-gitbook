# Assembly

## Introduction

Assembly is the lowest level of language (just above binary).

It is platform specific (different for each CPU architecture: x86, x86-64, ARM,
...).

It was used to write code close to the hardware, but is now mostly used for
reverse engineering (understanding how malwares work).

It is one of fastest language, with C, but also the most difficult to write &
maintain. Today, some C compilers can compile C code directly to binary,
without using assembly. That's why assembly is less used than before.

## Types

| Type | Declaration | Size |
| ---- | ----------- | ---- |
| **Byte** | `db` | 1 byte |
| **Word** | `dw` | 2 bytes |
| **Double word** | `dd` | 4 bytes |
| **Quadruple word** | `dq` | 8 bytes |
| **Ten bytes** | `dt` | 10 bytes |

*Example:*

```asm
choice      DB    'y'
number      DW    65535
negative    DD    -2147483648
big         DQ    9223372036854775807
very_big    DT    18446744073709551615
```

**Note:**

- **Characters** are stored as its **ASCII** value in **hexadecimal**;
- There is no **signed & unsigned types differentiation**;
- **Negative values** are **automatically** converted to its **2's complement
representation**;
- There is **no floating point & integer types differentiation**;
- **float** & **double** are represented using **32 bits** & **64 bits**
respectively.

## Conditions

`cmp` is used to **compare two values**. It subtracts the second value from the
first one and sets the flags `ZF`, `SF`, `CF` & `OF`. Then we can use `j`
instructions to **jump** to a label if a condition is **true**.

| Condition | Instruction | Sign |
| --------- | ----------- | ---- |
| **Equal** | `je` | signed or unsigned |
| **Not equal** | `jne` | signed or unsigned |
| **Above** | `ja` | unsigned |
| **Above or equal** | `jae` | unsigned |
| **Below** | `jb` | unsigned |
| **Below or equal** | `jbe` | unsigned |
| **Greater** | `jg` | signed |
| **Greater or equal** | `jge` | signed |
| **Lower** | `jl` | signed |
| **Lower or equal** | `jle` | signed |

```asm
greater:
    mov     eax, 1

main:
    cmp     eax, ebx
    jg      greater
```

## Notes

- If `[rax]` is used but no valid memory address is stored in `rax`, there is a
segmentation fault.

- `[rax + 5]` means that we take the value stored 5 bytes after the address
stored in `rax`. If `rax` is `0x1000`, then `[rax + 5]` is the value stored at
`0x1005`. Same for `-`.

## References

- [Tutorials point](https://www.tutorialspoint.com/assembly_programming)
