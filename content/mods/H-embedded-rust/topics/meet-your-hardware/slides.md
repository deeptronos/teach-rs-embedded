---
layout: section
---

# Meet Your Hardware

---
layout: default
---

# The micro:bit
Some of the many components on this board:
- A microcontroller (aka "microcontoller unit", shortened as MCU)
  - The larger of the two black squares sitting on the side of the board with the USB port.
  - The MCU is what *runs your code* - when you are "programming a board", you are actually programming the MCU installed on the board.
- A number of LEDs, most notably the LED matrix on the back.
- Two "user" buttons as well as a "reset" button (the one next to the USB port).
- One USB port.
- A sensor that is both a magnetometer and an accelerometer.

For a more detailed description of the board, visit the [micro:bit website](https://tech.microbit.org/hardware/)
<!--
"Microcontroller" on Wikipedia: [here](https://en.wikipedia.org/wiki/Microcontroller)
"Magnetometer" on Wikipedia: [here](https://en.wikipedia.org/wiki/Magnetometer)
"Accelerometer" on Wikipedia: [here](https://en.wikipedia.org/wiki/Accelerometer)
-->

---

# Nordic nRF52833 (aka the "nRF52", micro:bit v2)
Let's take a closer look at the MCU sitting on our board.

- This MCU has 73 tiny metal *pins* beneath it, which connect to *traces* on the board.
- Traces are like little "roads" that act as the wires connecting components together on the board.
- The MCU dynamically alters the electrical properties (enabling or disabling the flow of electrical current) of the pins to control the components on the board - this works similarly to a light switch, which alters how electrical current flows through a circuit.
- If we inspect the part number on the chip (printed on top of the chip) we can find that it's manufactured by [Nordic Semiconductor](https://www.nordicsemi.com/), who provide a [product page](https://www.nordicsemi.com/products/nrf52833) for the chip as well as a [product specification](https://infocenter.nordicsemi.com/pdf/nRF52833_PS_v1.3.pdf) detailing more useful information about the chip.
- From the specification, we find that the chip is an ARM® Cortex™-M4 32-bit processor.

---
# ARM? Cortex-M4?
If we have a chip made by Nordic, then who is Arm? If our chip is the nRF52833, what is the Corex-M4?
- Arm designs parts of chips, but doesn't make chips themselves. Manufacturers license Arm's designs and then implement the designs (perhaps with some of their own tweaks) in the form of physical hardware which can be sold.
  - This differs from the strategy of companies like Intel, which both designs *and* manufactures their own chips.
- Arm licenses many different designs. The "Cortex-M" family designs are for use in microcontrollers.
  - For example, the Cortext-M4 is designed for low cost and low power usage. The Cortex-M7 is higher cost, but with more features and performance.

You don't need to know too much about different types of processor designs for this course. However, you are hopefully now a bit more knowledgeable about the tech on your micro:bit.
While you are specifically working with an nRF52833, you might find yourself reading documentation and using tools for Cortex-M-based chips, since the nRF52833 is based on a Cortex-M design.

---
# Rust Embedded Terminology
Before we start programming, let's have a look at the libraries and terminology that will be important for the rest of the course.
## Abstraction Layers
The following terms refer to different levels of abstraction:
- **Peripheral Access Crate (PAC)**: Provides a safe(ish) direct interface to the peripherals of the chip. You usually won't need to touch the PAC if the higher-level abstractions don't fulfill your needs. The PAC we are (mostly implicitly) going to use is for the [nRF52](https://crates.io/crates/nrf52833-pac).
- **Hardware Abstraction Layer (HAL)**: Built on top of the chip's PAC to provide an abstraction that is usable for someone who doesn't know about all the special behavior of the chip. Usually, a HAL abstracts entire peripherals away into single structs that can, for example, be used to send data around via the peripheral. We are going to use [nRF52-hal](https://crates.io/crates/nrf52833-hal).
- **Board Support Crate (BSP)**: Abstracts a whole board (such as the micro:bit) away at once. Thus, it provides abstractions to use both the microcontroller as well as the sensors, LEDs etc. that are present on the board.
  - Often (especially when working with custom-made boards) no pre-built BSP will be available, and you must instead work with the HAL and build/find the drivers for the sensors yourself. Luckily, the micro:bit does have a [BSP](https://crates.io/crates/microbit-v2) which we'll use on top of our HAL as well.
  - In non-Rust situations this is usually called the Board Support Package, hence the acronym.

---
# Unifying the Layers
In the Rust Embedded world,
