# Embedded Systems Engineering Portfolio

**Live Demo:** [ahmedmar710.github.io/embedded-portfolio/embedded_portfolio.html](https://ahmedmar710.github.io/embedded-portfolio/embedded_portfolio.html)

An interactive, browser-based portfolio demonstrating core embedded and systems engineering skills aligned with industry requirements. Built as a single-file application showcasing real C/C++ implementations, Linux tooling, RTOS concepts, hardware timing, and software testing practices.

---

## Skills Demonstrated

| Area | Technologies |
|---|---|
| Systems Programming | C99, C++17, ISR design, MMIO, volatile |
| Concurrency & Safety | `std::atomic`, lock-free data structures, memory ordering |
| Linux Development | Bash scripting, `strace`, `valgrind`, `/proc`, OpenOCD |
| Real-Time Systems | Priority-based preemptive scheduler, task states, context switching |
| Hardware Interfaces | SPI bit-bang driver, UART ISR, datasheet timing constraints |
| Testing | Google Test (GTest), PyTest, CTest, `cppcheck` static analysis |
| DevOps | Git, Conventional Commits, GitHub Actions CI/CD pipeline |

---

## Project Sections

### 01 — C/C++ Core
- **Lock-free ring buffer** (`ring_buffer.h`) — C++17 template using `std::atomic` with explicit `memory_order` annotations and `alignas(64)` cache-line separation to prevent false sharing
- **UART ISR driver** (`uart_driver.c`) — C99 interrupt service routine with `__attribute__((interrupt))`, memory-mapped I/O macros, and overflow-safe circular buffer

### 02 — Linux & Shell
- Production Bash build/flash script with `set -euo pipefail`, CLI argument parsing, ARM cross-compiler toolchain validation, CMake/Ninja build, and OpenOCD flashing
- Linux diagnostic workflow: `strace` for syscall tracing, `/proc/interrupts` for IRQ monitoring, `valgrind` for heap leak detection

### 03 — RTOS Simulator
- Interactive priority-based preemptive task scheduler simulation
- Spawn up to 8 tasks, step through scheduler ticks manually or in auto mode
- Visualizes CPU register state (PC, SP, LR, XPSR), stack memory writes, and per-task state transitions (RUNNING / SLEEPING / WAITING / STOPPED)

### 04 — Hardware Timing
- SVG timing diagram of a 10 MHz SPI Mode 0 transaction showing CS_N, SCLK, MOSI, MISO with setup/hold time annotations (`tSU`, `tHD`, `tCSS`) derived from a device datasheet
- Paired C driver translating datasheet Table 12 timing values into `#define` constants

### 05 — Test Runner
- 12-test Google Test suite covering ring buffer correctness, UART overflow handling, SPI byte transfer, and RTOS scheduler behaviour — including one intentional failing test exposing a real race condition
- PyTest integration tests for UART protocol: handshake timing, baud rate tolerance, and CRC-8 checksum validation

### 06 — Git Workflow
- Realistic feature branch history following Conventional Commits (`feat:`, `fix:`, `test:`, `chore:`)
- GitHub Actions CI pipeline: ARM toolchain install → CMake build → GTest via CTest → PyTest → `cppcheck` static analysis

---

## Running Locally

No build required — open directly in any modern browser:

```bash
git clone https://github.com/ahmedmar710/embedded-portfolio.git
cd embedded-portfolio
open embedded_portfolio.html   # macOS
start embedded_portfolio.html  # Windows
xdg-open embedded_portfolio.html  # Linux
```

---

## Tech Stack

C · C++17 · Bash · Python · Google Test · PyTest · CMake · Ninja · OpenOCD · Git · GitHub Actions · ARM Cortex-M (simulated)
