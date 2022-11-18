# Operating systems

## Introduction

An operating system is a system software that manages computer hardware,
software resources, and provides common services for computer programs.

Without an OS, only one software would run and would be in charge of
everything on the computer, including the hardware.

## System & application softwares

**System softwares** are in charge of:

- managing **memory**;
- managing **programs execution**;
- allowing several programs to **exchange data between them**;
- managing all **computer's peripherals**;
- managing **files**, **network**, **sound** & **display**.

Then, **application** software let the **user** do **tasks** that may involve
calls to some system softwares.

But depending on the hardware, an OS can't manage all devices or peripherals.
That's why the computer needs **drivers**, which is a system software, often
provided by the manufacturer of the device.

## System calls

When an application software executes a system software, it makes a **system**
**call**. In order to make one, softwares will use a processor functionality,
called **interrupt**.

### Interrupts

An interrupt is a request for the processor to **stop currently executing**
**program in order to execute another one**. After this last program is done,
it **resumes the stopped program**. It is **stored in the processor**.

When the interrupt is requested, it runs an **Interrupt Service Routine**
(or **ISR**).

Since there is a lot of different devices & peripherals, there is multiple ISR.
That's why we use an **interrupt vector table**.

### Interrupt vectors

An interrupt vector is a pointer that stores the **address of an interrupt**
**handler**.

First, it is **initialized by the BIOS** during the booting process. Then, the
**OS will replace this interrupt handler** by its own one.

Since there is multiple interrupt vector in a system, those are stored in an
**interrupt vector table**, that associate a list of interrupt handlers with a
list of interrupt requests. It is **stored in the memory**.

### Interrupt requests

On x86 processors, `INT` is the assembly language instruction (or machine
instruction) that generates an interrupt.

This instruction needs some **parameters** in order to work, such as the number
or the address of an interrupt, ... For example, an ISR for printing a letter
on the screen will need the letter to display as a parameter.

Those parameters are copied in ultra-fast memory in the processor, called
**registers**.

## Kernel

## Booting

### Linux

1. Power on
2. POST
3. BIOS
4. MBR
5. GRUB
6. Kernel
7. Systemd (Init)
