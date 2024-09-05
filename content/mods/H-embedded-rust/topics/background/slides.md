---
layout: cover
---

# Embedded Rust - Background

---
layout: default
---

# What's a microcontroller?
- A system on a chip.
- Contains all the discrete parts of a computer (processor, RAM, etc.) in a single "package"/chip.
- Allows systems to be built with fewer individual parts.

---

# What can you do with a microcontroller?
- Microcontrollers are the central control of what are known as *"embedded systems"*.
  - Everywhere, even if you don't notice them - washing machines, microwaves, printers, temperature control, vehicle controls, etc.
- Operate with little user input.
  - Even if a system exposes a user interface (like a washing machine does) most of their operation is done on their own
- Often, embedded systems are used to *control* a physical process.
  - This is done by taking inputs to learn about the state of the world ("sensors") and changing things using devices ("actuators".)
  - For example, a building climate control system could be...
    - Sensors which measure temperature/humidity in various locations.
    - Actuators which control the speed of fans.
    - Actuators which cause heat to be added/removed from the building.

---

# When should I use a microcontroller?
You can imagine that many embedded systems could be operated by a computer running Linux (for example a "Raspberry Pi"). Why would anyone use a microcontroller instead?
Some reasons may include:
- **Cost.** A microcontroller is much cheaper than any general purpose computer. It also requires fewer external electrical components to operate.
- **Power consumption.** Most microcontrollers consume a fraction of the power of a full blown computer processor. This makes a big difference for applications that run on batteries!
- **Responsiveness.** Many embedded systems must react quickly (e.g. the "anti-lock" braking system of a car) or risk catastrophic failure. This deadline is called a "hard real time" requirement, and a system designed with such a deadline is a *"hard real time system"*. A general purpose computer usually runs multiple software components which share the computer's resources. This makes it harder to guarantee execution of a program within tight time constraints.
- **Reliability.** With fewer components (both hardware and software), there is less to go wrong!

---

# When should I *not* use a microcontroller?
- For heavy computational work - low cost/power consumption comes at the cost of limited computational resources.
- Typically, microcontrollers are not capable of executing instructions as quickly as a "big" processor.
  - The amount of work per instruction is usually lower.
  - Instruction size constraints - microcontrollers are typically 32 bit, but 16 bit is not uncommon.
  - Little or no "cache" - instructions can only be run as fast as main memory can be accessed.
- Some microcontrollers don't have hardware support for floating point ops.
  - On these, performing addition of single precision numbers could take hundreds of CPU cycles!
- Limited memory
  - With sizes as small as 16KB for instructions and 4KB for data, programming for these systems can be quite challenging.
  - The controller we will work with has "only" 512KB for instructions and 256KB for data - far less than that of a "real computer".

---

# Why use Rust instead of C?
This question is largely beyond the scope of this course, but the most useful advantage of Rust over C for our work is Cargo for package management.
- Makes development much easier!
- Easy package management encourages code reuse, which leads libraries to get more "battle testing" and improve with time.

---

# Why should I not use Rust? Why should I prefer C over Rust?

- C ecosystem is more mature.
- Off-the-shelf solutions for several problems already exist.
  - Commercial Real Time Operating Systems (RTOS) are available in C.
  - There aren't any commercial, production-grafde RTOSes in Rust (as of this writing) so you have to either make one yourself or try the ones that are in development. These can be found in the [Awesome Embedded Rust](https://github.com/rust-embedded/awesome-embedded-rust#real-time-operating-system-rtos) repository.
