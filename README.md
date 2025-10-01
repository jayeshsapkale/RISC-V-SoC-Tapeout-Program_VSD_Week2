# Week 2 – BabySoC Fundamentals & Functional Modelling

## Objective
To build a solid understanding of **SoC fundamentals** and practice **functional modelling** of the BabySoC using simulation tools:

- **Icarus Verilog (`iverilog`)** for compiling Verilog code  
- **GTKWave** for viewing simulation waveforms  

outcome:

- Explain the theory behind SoC design  
- Demonstrate BabySoC functional modelling with simulation waveforms  

---

## Part 1 – Theory (Conceptual Understanding)

**References:**  
- [Fundamentals of SoC Design](https://github.com/hemanthkumardm/SFAL-VSD-SoCJourney/tree/main/11.%20Fundamentals%20of%20SoC%20Design)  
- [VSDBabySoC Project](https://github.com/hemanthkumardm/SFAL-VSD-SoCJourney/tree/main/12.%20VSDBabySoC%20Project)

### Key Concepts

1. **What is a System-on-Chip (SoC)?**  
   - A SoC integrates **CPU, memory, peripherals, and interconnects** on a single chip.  
   - Enables compact, energy-efficient, and high-performance embedded systems.  

2. **Components of a Typical SoC**  
   - **CPU/Core**: Executes instructions (here, RVMYTH RISC-V core).  
   - **Memory**: Stores instructions and data.  
   - **Peripherals**: I/O modules like DAC, timers, UART, etc.  
   - **Interconnect/Bus**: Transfers data between components.  

3. **Why BabySoC?**  
   - Simplified SoC model for learning purposes.  
   - Focuses on key components without overwhelming complexity.  
   - Enables hands-on understanding of **functional modelling, RTL simulation, and dataflow**.  

4. **Role of Functional Modelling**  
   - Functional modelling is done **before RTL synthesis and physical design**.  
   - Helps verify **module interconnections, clocking, reset behavior, and dataflow**.  
   - Reduces design errors and makes debugging easier before gate-level simulation.

**Deliverable:**  
- 1–2 page write-up summarizing SoC fundamentals and the BabySoC learning journey.

---

## Part 2 – Labs (Hands-on Functional Modelling)

**Reference:**  
- [VSDBabySoC Project Labs](https://github.com/hemanthkumardm/SFAL-VSD-SoCJourney/tree/main/12.%20VSDBabySoC%20Project)


