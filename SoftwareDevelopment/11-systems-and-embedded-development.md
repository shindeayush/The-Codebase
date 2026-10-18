# Systems and Embedded Development

*Control how programs use memory, operating systems and physical hardware.*

## What this field is

Systems development builds low-level software that manages computer resources or supports other programs, including operating systems, drivers and runtimes. Embedded development builds software inside dedicated devices such as sensors, appliances and industrial controllers. Both require close attention to hardware, memory and timing; embedded work often adds strict power, storage or real-time constraints.

**Learning sequence** 1. C and memory → 2. Build, debug and profile → 3. OS or device programming → 4. Concurrency and reliability

**Languages** C first; C++ or Rust next. Python for automation and basic assembly for your target architecture.

## Learn the essentials

**Systems foundations** Pointers, memory layout, stack/heap, allocation, binary representation, compilation, linking and system calls.

**Concurrency** Threads, synchronization, races, deadlocks and safe resource management.

**Embedded foundations** Digital logic, microcontrollers, interrupts, timers, memory-mapped I/O, UART, SPI, I2C and real-time constraints.

## Use these tools

Linux, GCC or Clang, GDB or LLDB, Make, CMake, sanitizers and a profiler. For embedded work, choose an STM32 or ESP32 board, its SDK, a debugger and serial monitor; add a logic analyzer later.

## Choose a specialization

| Path | Language and tools |
|---|---|
| Systems programming | C, then C++ or Rust; Linux, GCC or Clang, GDB, sanitizers and a profiler. Build a shell or server. |
| Embedded firmware | C; an STM32 or ESP32 board, its SDK, a debugger and serial monitor. Add an RTOS later. |

## Add later

Drivers, RTOS concepts, bootloaders, networking stacks, power management and hardware security.

## Project milestone

Systems: build a small shell or multithreaded server. Embedded: build a sensor logger with interrupt-driven input, persistent storage and error recovery.

## Starting resources

- [The Rust Programming Language](https://doc.rust-lang.org/book/)

---

Learning sequences and stack choices are recommendations; alternatives are separate paths, not extra requirements. Start with [Shared foundations](00-shared-foundations.md) and see the [README](README.md) to compare fields.
