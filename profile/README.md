# MicaNT: Sovereign Operating System Executive

<p align="center">
  <a href="https://micant.barrersoftware.com">
    <img src="https://img.shields.io/badge/Official_Website-micant.barrersoftware.com-4CAF50?style=for-the-badge&logo=googlechrome&logoColor=white" alt="Official Website" />
  </a>
  <a href="https://github.com/MicaNT-Kernel/MicaNT">
    <img src="https://img.shields.io/badge/Core_Repository-MicaNT--Kernel%2FMicaNT-0078D7?style=for-the-badge&logo=github&logoColor=white" alt="MicaNT Repo" />
  </a>
  <a href="https://ko-fi.com/ssfdre38">
    <img src="https://img.shields.io/badge/Support_on_Ko--fi-ssfdre38-FF5E5B?style=for-the-badge&logo=kofi&logoColor=white" alt="Support on Ko-fi" />
  </a>
  <img src="https://img.shields.io/badge/Language-ISO_C%2B%2B23-blue?style=for-the-badge&logo=c%2B%2B" alt="C++23" />
  <img src="https://img.shields.io/badge/Footprint-Sub--32MB-success?style=for-the-badge" alt="Sub-32MB Footprint" />
  <img src="https://img.shields.io/badge/Telemetry-Zero-brightgreen?style=for-the-badge" alt="Zero Telemetry" />
</p>

---

> *"The goal was to design an operating system that would stand the test of time — portable, modular, extensible, and robust."*  
> — **Dave Cutler & Helen Custer**, *Inside Windows NT* (1993)

**MicaNT** is a modern, clean-room, sovereign operating system executive inspired by Dave Cutler's legendary MICA and PRISM architectures. Engineered from first principles in ISO C++23, MicaNT implements a fully compatible NT kernel executive with **sub-32MB memory footprint**, **zero telemetry**, and **hardened determinism**.

---

## 🏛️ Architectural Pillars

```
+--------------------------------------------------------------------------+
|                        USER MODE (Ring 3)                                |
|  +------------------------+  +-------------------+  +------------------+ |
|  | Native Win32 Subsystem |  | Win32k/GDI/USER   |  | PrismX / Prism3D | |
|  | Subsystem Servers      |  | Window Surfaces   |  | Direct3D Engine  | |
|  +------------------------+  +-------------------+  +------------------+ |
|  +---------------------------------------------------------------------+ |
|  |                  NTDLL.DLL / Native System Call Stubs               | |
+--+---------------------------------------------------------------------+--+
                                |  Syscall / Fast System Call (sysenter)
+-------------------------------v------------------------------------------+
|                        KERNEL MODE (Ring 0)                              |
|  +---------------------+  +--------------------+  +--------------------+ |
|  | Process & Thread    |  | Virtual Memory     |  | Object Manager &   | |
|  | Executive (Ps)      |  | Manager (Mm)       |  | Security (Ob / Se) | |
|  +---------------------+  +--------------------+  +--------------------+ |
|  +---------------------+  +--------------------+  +--------------------+ |
|  | I/O System & WDDM   |  | Hardware           |  | HAL & Architecture | |
|  | Executive (Io/Dxg)  |  | Virtualization     |  | Abstraction        | |
|  +---------------------+  +--------------------+  +--------------------+ |
+--------------------------------------------------------------------------+
```

### 1. 100% Clean-Room Pedigree
- Zero proprietary Microsoft source code.
- Authored exclusively from open architecture documentation (*Inside Windows NT*, *Windows Internals* by Russinovich et al., Microsoft Open Specifications, and POSIX/ISO standards).
- Guarded by continuous automated **Clean-Room Sentinel CI** regression auditing.

### 2. Modern ISO C++23 Core
- Strongly-typed handles, RAII kernel object management, compile-time Bitmask enums, concepts, and zero-overhead abstractions.
- 45+ comprehensive test suites passing across memory management, scheduling, APC/DPC delivery, WDDM thunking, and 3D rasterization.

### 3. PrismX & Prism3D Graphics Executive
- Named in homage to Dave Cutler’s 1988 PRISM RISC project.
- **PrismX**: Presentation pipeline, DXGI swapchains (`IDXGISwapChain`, `IDXGIFactory1`), WDDM kernel thunking (`dxgkrnl.sys`), and flip-model backbuffering.
- **Prism3D**: Shading pipeline, pipeline state objects, sub-pixel Gouraud RGB color interpolation, floating-point Z-buffer depth testing, and software reference rasterizer.
- Built using clean-room integration referencing Microsoft's MIT-licensed open-source `DirectX-Headers` and `DirectXTK`.

### 4. Zero Telemetry & Extreme Lightweight Footprint
- Cold-boots in milliseconds into a native command console or high-resolution UEFI GOP graphical desktop.
- Requires less than 32 megabytes of RAM.
- Absolutely zero outbound telemetry, profiling, or cloud tethering.

---

## 🌐 Official Showcase & Links

- **Showcase Website:** [https://micant.barrersoftware.com](https://micant.barrersoftware.com)
- **Core Repository:** [https://github.com/MicaNT-Kernel/MicaNT](https://github.com/MicaNT-Kernel/MicaNT)
- **Ko-fi Support:** If you appreciate independent systems programming and sovereign OS development, consider supporting the author:  
  👉 **[Support ssfdre38 on Ko-fi](https://ko-fi.com/ssfdre38)**

---

## 📜 Legal & Fair Use Notice

*MicaNT is an independent clean-room operating system implementation. "Windows", "DirectX", and "Direct3D" are registered trademarks of Microsoft Corporation. MicaNT, PrismX, and Prism3D are not affiliated with, endorsed by, or sponsored by Microsoft Corporation. Compatibility interfaces are implemented under nominative fair use and interoperability standards (Google LLC v. Oracle America, Inc., 2021) using publicly available specifications and MIT-licensed headers.*
