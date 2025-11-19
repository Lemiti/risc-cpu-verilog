# RISC CPU Design in Verilog

A custom 16-bit RISC processor implementation in Verilog, designed from the ground up as part of a Computer Architecture and Organization course project.

## 📋 Project Overview

This project implements a fully functional 16-bit Reduced Instruction Set Computer (RISC) processor in Verilog. The CPU features a custom instruction set architecture, modular design, and demonstrates fundamental computer architecture concepts including datapath design, control unit implementation, and memory hierarchy.

## 🏗️ Architecture Specifications

### Processor Features
- **Architecture**: 16-bit RISC
- **Instruction Set**: Custom 16-bit instruction format
- **Registers**: 8 general-purpose 16-bit registers
- **Memory**: Harvard architecture (separate instruction and data memory)
- **Clock**: Single-cycle implementation
- **Technology**: Synthesizable Verilog

### Instruction Set Architecture
| Instruction | Opcode | Format | Description |
|-------------|--------|--------|-------------|
| ADD | 4'b0000 | R-type | Register addition |
| SUB | 4'b0001 | R-type | Register subtraction |
| AND | 4'b0010 | R-type | Bitwise AND |
| OR | 4'b0011 | R-type | Bitwise OR |
| LOAD | 4'b0100 | I-type | Load from memory |
| STORE | 4'b0101 | I-type | Store to memory |
| BEQ | 4'b0110 | I-type | Branch if equal |
| JMP | 4'b0111 | J-type | Unconditional jump |

## 📁 Project Structure
```text
risc-cpu-verilog/
├── rtl/ # Verilog source files
│ ├── cpu.v # Top-level CPU module
│ ├── alu.v # Arithmetic Logic Unit
│ ├── control_unit.v # Instruction decoder & control
│ ├── reg_file.v # Register file (8 registers)
│ ├── pc.v # Program Counter
│ ├── imem.v # Instruction Memory
│ └── dmem.v # Data Memory
├── tb/ # Testbench files
│ ├── testbench.v # Main testbench
│ ├── test_*.v # Individual module testbenches
│ └── test_programs/ # Assembly test programs
├── scripts/ # Utility scripts
│ ├── compile.sh # Compilation script
│ ├── run_sim.sh # Simulation script
│ └── assembler.py # Custom assembler
├── docs/ # Documentation
│ ├── ISA.md # Instruction Set Documentation
│ ├── datapath.pdf # Datapath diagram
│ └── timing_diagrams/
└── results/ # Simulation results & waveforms
```

## 🚀 Getting Started

### Prerequisites
- Icarus Verilog (iverilog)
- GTKWave for waveform viewing
- Python 3.x (for assembler script)

### Installation on Ubuntu
```bash
sudo apt update
sudo apt install iverilog gtkwave python3
```

# Simulation
1. Clone the repository:
```bash
git clone https://github.com/Lemiti/risc-cpu-verilog.git
cd risc-cpu-verilog
```
2. Compile and run simulation:
```bash
cd scripts
chmod +x compile.sh run_sim.sh
./compile.sh
./run_sim.sh
```
3. View waveforms:
```bash
gtkwave results/cpu_waves.vcd
```
# Running Test Programs
```bash
# Assemble test program
python3 scripts/assembler.py tb/test_programs/fibonacci.asm

# Run specific test
./scripts/run_sim.sh tb/test_programs/fibonacci.mem
```
# 🧪 Testing Strategy
The project includes comprehensive testing at multiple levels:
- Unit Testing: Individual module verification
- Integration Testing: Complete CPU functionality
- Program Testing: Real assembly programs execution
# Example Test Program
```assembly
// Calculate Fibonacci sequence
LOAD R1, 0        // Initialize first number
LOAD R2, 1        // Initialize second number
LOAD R3, 10       // Number of iterations
LOOP:
ADD R4, R1, R2    // Calculate next Fibonacci number
MOV R1, R2        // Shift numbers
MOV R2, R4
SUB R3, R3, 1     // Decrement counter
BNE R3, LOOP      // Continue if not zero
HALT
```
# 📊 Performance Characteristics

| Metric                  | Value                 |
| ----------------------- | --------------------- |
| Maximum Clock Frequency | XX MHz                |
| Instructions per Cycle  | 1 (single-cycle)      |
| Gate Count              | ~XXXX gates           |
| Critical Path           | ALU -> Register Write |

# 🛠️ Design Methodology
### Modular Design

The CPU follows a modular design approach with clearly defined interfaces between components:
1. **ALU**: Handles all arithmetic and logical operations
2. **Control Unit**: Implements finite state machine for instruction decoding
3. **Register File**: Manages 8 general-purpose registers
4. **Memory Units**: Separate instruction and data memory

### Verification Strategy
- Waveform analysis for timing verification
- Self-checking testbenches with automatic pass/fail reporting
- Coverage-driven testing methodology

---
**Course**: Computer Architecture and Organization  
**University**: Addis Ababa University  
**Semester**: 1st/4rth year  
**Instructor**: Dr.Getachew