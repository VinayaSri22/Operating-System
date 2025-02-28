# Operating System Structures

## 1. Simple Structure
- Every layer can access the hardware directly
- Characterized by weak security mechanisms
- No clear separation between components

## 2. Monolithic Structure
- All functionalities are integrated into a single kernel level
- **Disadvantages:**
  - Difficult to maintain
  - Challenging to debug
  - Large codebase in single space

## 3. Layered Structure
- Each functionality is implemented as a separate layer
- **Key Characteristic:** 
  - Layer N can only communicate directly with:
    - Layer N+1 (above)
    - Layer N-1 (below)
- Promotes hierarchical design

## 4. Microkernels
- **Core Design:**
  - Only essential functionalities in kernel level
  - Other functionalities moved to system programs
- **Communication:**
  - Uses message passing between programs
  - Improved system modularity
  - Better security isolation

## 5. Module Structure
- **Architecture:**
  - Core kernel at the center
  - Additional functionalities as loadable modules
- **Communication:**
  - All modules connect to core kernel
  - Inter-module communication happens through core kernel
- Allows dynamic loading of components

## Common Usage Today
| Structure Type | Used In |
|---------------|---------|
| Monolithic | Linux Kernel, Unix |
| Microkernel | macOS (XNU kernel), QNX |
| Module | Windows NT, Modern Linux |
| Layered | Some embedded systems |
| Simple | MS-DOS (legacy) |