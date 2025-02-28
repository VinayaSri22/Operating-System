# Operating System Generation and System Boot

## Key Topics
1. Operating System designs
2. Operating System Generation (SYSGEN)
3. System Boot
4. Bootstrap program/Bootstrap loader
5. ROM/Firmware

### 1. Operating System Generation
- **Types of OS Design:**
  - Single machine design
  - Multiple machine design
- **SYSGEN Process** determines system requirements:
  - CPU type and specifications
  - Available devices
  - Memory configuration

### 2. System Boot Process
- **Bootstrap Program:**
  - First program executed at computer startup
  - Primary functions:
    - Locates OS kernel
    - Loads kernel into memory
    - Initiates kernel execution

- **Storage Location:**
  - Bootstrap program stored in ROM/Firmware
  - Advantages of ROM storage:
    - No initialization required
    - Protected against viruses (read-only)
  - Operating System stored on disk


> **FIRMWARE**
> 
> Firmware is a specific type of software that provides low-level control for a device's specific hardware.
> 
> Low-level Operations: 
> 
>1.Controls hardware functions directly
>
>2.Provides basic instructions for device operation