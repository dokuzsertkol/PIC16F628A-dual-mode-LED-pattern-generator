# PIC16F628A-dual-mode-LED-pattern-generator

---

## Project Description
This project implements a dual-mode LED pattern generator using a PIC16F628A microcontroller. It features two distinct LED animation modes that can be switched using a push button connected to PORTA, bit 0.

---
## Features
Mode 1 - Shift Left Pattern: LEDs rotate left in a continuous loop

Mode 2 - Chaos Pattern: LEDs rotate right with inversion for a "chaotic" alternating effect

Button Control: Toggle between modes using a single push button

Debounce Handling: Software-based button debouncing

Visual Feedback: Carry bit is displayed on the first LED for continuous visual tracking

---

##  Hardware Requirements
- PIC16F628A microcontroller

- 8 LEDs connected to PORTB (RB0-RB7)

- 8 current-limiting resistors (typically 220Ω-330Ω)

- 1 push button connected to RA0

- 1 pull-up resistor for the button (10kΩ typical)

- Power supply (5V DC)

---

### Pin Connections
| Pin	| Connection
|----------|-------------|
| RB0-RB7	| LEDs (through current-limiting resistors) |
| RA0	| Push button (active low, with pull-up resistor) |

## Operating Instructions
1. Power On: The system starts in Mode 1 (Shift Left pattern)

2. Mode Switching: Press and release the button to switch between modes

3. Mode 1 (Shift Left):
    * LEDs rotate from RB0 to RB7
    * The carry bit is displayed on RB0 for continuous visualization

4. Mode 2 (Chaos):
    * LEDs rotate right with inversion
    * Creates an alternating "chaotic" pattern
    * Multiple delays for better visual tracking

---

## Main Sections
1. Initialization: Sets up I/O ports and clears the carry flag

2. Mode 1 Handler: Implements the left shift pattern

3. Mode 2 Handler: Implements the chaotic pattern

4. Delay Routines: Provides timing for human-visible patterns

5. Button Handling: Debounces and processes button inputs

---

## Program Flow
```text
                    ┌─────────────┐
                    │    START    │
                    │ Init Ports  │
                    └──────┬──────┘
                           │
                           ▼
                    ┌─────────────┐
              ┌───▶│  MODE 1     │
              │     │ (Shift Left)│
              │     └──────┬──────┘
              │            │
              │            ▼
              │     ┌─────────────┐
              │     │ Button      │        
              │     │ Pressed?    │
              │     └──────┬──────┘        
              │            │YES            
              │            ▼               
              │     ┌─────────────┐        
              │     │ Wait for    │        
              │     │ Release     │        
              │     └──────┬──────┘        
              │            │               
              │            ▼               
              │     ┌─────────────┐        
              │     │  MODE 2     │        
              │     │  (Chaos)    │       
              │     └──────┬──────┘        
              │            │               
              │            ▼              
              │     ┌─────────────┐        
              │     │ Button      │        
              │     │ Pressed?    │
              │     └──────┬──────┘
              │            │YES
              │            ▼
              │     ┌─────────────┐
              │     │ Wait for    │
              └─────│ Release     │
                    └─────────────┘
```

---
                           
## Important Notes
1. Pull-up Resistor: The button at RA0 requires an external pull-up resistor (or enable the internal weak pull-up)

2. Current Limiting: Always use current-limiting resistors with LEDs to prevent damage

3. Power Supply: Ensure stable 5V power supply

4. Button Debouncing: Software debouncing is implemented in the code

5. Carry Bit Handling: The code explicitly handles the carry bit to maintain visual continuity

---

## Circuit Design
![alt text](https://i.imgur.com/Bd9Tkh2.png)
