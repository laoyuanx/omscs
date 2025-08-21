# CS6200: Operating Systems

## Lecture Notes

### P1L2: Introduction to Operating Systems

#### What is an Operating System?
- A special piece of software that **abstracts** and **arbitrates** the underlying hardware system.
- **Abstract:** simplifies what the hardware looks like to applications.
- **Arbitrate:** manages and controls hardware usage among multiple programs.

#### Analogy: OS as a Toy Shop Manager
- **Direct operational resources:** controls CPU, memory, devices.
- **Enforces policies:** ensures fair access and enforces resource limits.
- **Mitigates complexity:** abstracts hardware details through system calls.

#### Formal Definition
An operating system is a layer of system software that:
- Has privileged access to the hardware.
- Hides hardware complexity.
- Manages hardware on behalf of applications according to predefined policies.
- Ensures applications are isolated and protected from one another.

#### Quiz
- **Question:** Is cache memory an OS component?
- **Answer:** No, cache memory is managed by hardware.

#### Examples
- **Desktop:** Windows, macOS, Linux.
- **Embedded:** Android, iOS.

---

### OS Elements
1. **Abstractions** – hide hardware details (e.g., processes, files).
2. **Mechanisms** – how to implement abstractions.
3. **Policies** – rules for resource allocation (e.g., scheduling).

#### Design Principles
- **Separation of mechanism and policy:** mechanisms should be flexible to support different policies.
- **Optimize for the common case:** design choices depend on target workload.

---

### OS Protection Boundary

| Level  | Mode         | Used by |
|--------|--------------|---------|
| User   | Unprivileged | Apps    |
| Kernel | Privileged   | OS      |

#### User–Kernel Switch
Supported by hardware through:
- **Trap instructions.**
- **System calls:** e.g., `open(file)`, `send(socket)`, `mmap(memory)`.
- **Signals:** OS notifications delivered to applications.

**System Call Flow:**
1. Application prepares arguments.
2. Saves data at well-defined memory locations.
3. Issues a system call instruction.
4. OS executes the request and returns results.

---

### OS Services
- Process management
- File management
- Device management
- Memory management
- Storage management
- Security management

All exposed via **system calls**.

---

### OS Architectures

#### Monolithic OS
- **Pros:**
  - All features included.
  - Compile-time optimizations possible.
- **Cons:**
  - Hard to maintain.
  - Large codebase.
  - Performance overhead due to size.

#### Modular OS (Common Today)
- **Pros:**
  - Easier maintenance.
  - Smaller footprint.
  - Lower resource requirements.
- **Cons:**
  - Some performance overhead (indirection).
  - Still requires careful maintenance.

#### Microkernel OS
- Only minimal primitives at kernel level (e.g., IPC, address spaces, threads).
- Services like DB, filesystem, and drivers run in **user space**.
- **Pros:**
  - Small size.
  - Easier verification.
- **Cons:**
  - Portability challenges.
  - Higher software complexity.
  - Frequent user/kernel boundary crossings (performance cost).
