# OS Design & Implementation

### 1. Design Goals

Operating system design aims to satisfy both user and system requirements:

*   **User Goals**: The OS should be user-friendly, reliable, safe, and efficient.
*   **System Goals**: The OS should be easy to design, implement, and maintain, while also being flexible and error-free.

### 2. Mechanisms and Policies

The separation of mechanisms and policies is a fundamental principle in OS design.

*   **Mechanisms**: These are the low-level components that provide specific functionalities (e.g., memory protection, process scheduling).
*   **Policies**: These are the high-level decisions that determine how mechanisms are used (e.g., which process to schedule, how to allocate memory).

**Why Separate?** Separating mechanisms and policies enhances flexibility. The same mechanism can support different policies, allowing the OS to adapt to various environments and user needs. This separation also improves modularity and maintainability.

### 3. Implementation

OS implementation involves several key considerations:

*   **Programming Language**: Modern OSes are typically written in C or C++ for portability and maintainability.
*   **Code Structure**: Common architectures include monolithic kernels, layered systems, and microkernels.
*   **Debugging**: Debugging OS kernels requires specialized tools and techniques.

### Key Concepts

*   Balancing user and system goals is a central challenge in OS design.
*   The separation of mechanisms and policies promotes flexibility and adaptability.
*   Implementation choices significantly impact the OS's performance and maintainability.