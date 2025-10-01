# Week 2 – Part 2: BabySoC Functional Modelling (Lab)

## Objective
To build a solid understanding of **SoC fundamentals** and practice **functional modelling** of the BabySoC using simulation tools:

- **Icarus Verilog (`iverilog`)** for compiling Verilog code  
- **GTKWave** for viewing simulation waveforms  

By the end of this lab, outcome:

- Simulate BabySoC modules  
- Analyze reset, clock, and dataflow behavior  
- Verify functional correctness using waveforms  

---

## Lab Reference
[VSDBabySoC Project Labs](https://github.com/hemanthkumardm/SFAL-VSD-SoCJourney/tree/main/12.%20VSDBabySoC%20Project)

---

## Tools Required
- **Icarus Verilog (`iverilog`)** – Compilation and simulation  
- **GTKWave** – Waveform viewing  

---

## Steps

### 1.Environment Setup and Repository Cloning
To start, prepare the workspace and clone the project:
```
mkdir VLSI
cd ~/VLSI
git clone https://github.com/manili/VSDBabySoC.git
cd VSDBabySoC
ls src/module/
```


## 2.TLV-to-Verilog Conversion for RVMYTH

Convert TL-Verilog to Verilog for simulation as follows:

```bash
# Step 1: Install python3-venv (if not already installed)
sudo apt update
sudo apt install python3-venv python3-pip

# Step 2: Create and activate a virtual environment
cd ~/VLSI/VSDBabySoC/
python3 -m venv sp_env
source sp_env/bin/activate

# Step 3: Install SandPiper-SaaS inside the virtual environment
pip install pyyaml click sandpiper-saas

# Step 4: Convert rvmyth.tlv to Verilog
sandpiper-saas -i ./src/module/*.tlv -o rvmyth.v --bestsv --noline -p verilog --outdir ./src/module/

# Step 5: Deactivate the environment
deactivate
```
snapshot:
<img width="940" height="597" alt="image" src="https://github.com/user-attachments/assets/16dba860-afb6-465e-abe5-ab3999b3e81c" />


### 3. Compile BabySoC Verilog Modules

Pre-synthesis Simulation:
```
iverilog -DPRE_SYNTH_SIM \
  -I /home/vboxuser/VLSI/VSDBabySoC/src/include \
  -I /home/vboxuser/VLSI/VSDBabySoC/src/module \
  /home/vboxuser/VLSI/VSDBabySoC/src/module/testbench.v \
  -o sim.out

vvp sim.out
```

<img width="940" height="581" alt="image" src="https://github.com/user-attachments/assets/3785bc28-0d26-4c64-923d-aba530b2e824" />


### 4. Open .vcd File in GTKWave
### Waveform Viewing
```bash
gtkwave pre_synth_sim.vcd
```
waveform :
<img width="940" height="595" alt="image" src="https://github.com/user-attachments/assets/e311d301-609a-4c6c-9cf1-02996ebaffe5" />

## Signals to Observe

| Signal         | Purpose                                  |
|----------------|------------------------------------------|
| `CLK`          | Clock input to RVMYTH core              |
| `reset`        | Reset signal for initialization         |
| `RV_TO_DAC[9:0]` | 10-bit digital output from RVMYTH    |
| `OUT`          | DAC digital output                      |
| `OUT (real)`   | DAC analog output (optional, step mode)|

## 5. Analyze Waveforms

### Reset Operation
- Observe that outputs remain stable when `reset` is asserted.  
- Outputs start updating after `reset` is de-asserted.  

**Explanation:** Reset holds all outputs stable until initialization is complete.

### Clocking
- Verify that the `CLK` signal toggles periodically.  
- Check that sequential logic updates on the rising edge of the clock.  

**Explanation:** Shows proper synchronous operation of RVMYTH core and other modules.

### Dataflow Between Modules
- Observe `RV_TO_DAC[9:0]` changes propagate to `OUT`.  
- Confirm functional interaction between CPU, memory, and DAC.  

**Explanation:** Demonstrates correct dataflow and module interaction.

