# 🎬 Cinema Ticket Booking System

A lightweight, interactive Command Line Interface (CLI) application built using **x86 Assembly Language (16-bit)** for the **8086 architecture**. The application simulates a movie theater ticketing hub, allowing users to browse available theater details, view multi-tier ticket pricing tiers, and dynamically calculate the total bill for group bookings using integrated decimal I/O procedures.

---

## 🌟 Key Features

- **Interactive Main Menu:** An easy-to-use routing interface with 3 main operations: Viewing details, Booking tickets, or Terminating the program safely.
- **Detailed Information Desk:** Displays comprehensive records of registered movie theaters, matching locations, direct phone lines, and operating shifts.
- **Dynamic Multi-Tier Pricing:** Supports distinct price schemas tailored for two specific theaters (Film Theater & Action Theater) across multiple age variations:
  - **Film Theater:** Under 6 (Child), Adults, and Seniors.
  - **Action Theater:** Under 6 (Child), Adults, and Seniors.
- **Dynamic Bill Processing:** Accepts a multi-digit numerical ticket quantity from the user, multiplies it by the selected package value, and flashes the real-time sum total instantly.
- **Bulletproof Decimal Procedures:** Houses isolated subroutines (`INDEC` & `OUTDEC`) that manage string-to-integer parsing and multi-digit output display directly over DOS registers.

---

## 🛠️ Technical Profile & Architecture

- **Platform/Architecture:** Intel 8086 (16-bit Real Mode).
- **Execution Model:** `.MODEL SMALL` configuration with an isolated 256-byte stack pipeline (`.STACK 100h`).
- **Interface Protocol:** DOS Interrupt vectors (`INT 21h`) utilizing standard sub-functions:
  - `AH = 01h` (Buffered Character Input)
  - `AH = 02h` (Single Character Console Writing)
  - `AH = 09h` (Complete String Stream Parsing up to the `$` terminal marker)
  - `AH = 4Ch` (Clean Program Termination returning control to OS)

---

## 📂 Application Code Architecture

The runtime process logic flows across the following assembly sub-blocks:

- **`start` / `get_choice`:** Renders the landing directory block and holds execution until a valid input code (`1`, `2`, or `3`) is detected.
- **`FIRST_CHOICE`:** References the `theaters_info` data offset to dump theater details to screen before looping back to main.
- **`SECOND_CHOICE`:** The booking core. It processes inputs sequentially: Theater Type $\rightarrow$ Ticket Class Type $\rightarrow$ Ticket Quantity.
- **`film_cinema` & `action_cinema`:** Evaluation blocks that filter chosen variables and load the correct price scalar into memory registers.
- **`calculate`:** Invokes a 16-bit signed multiplication (`MUL`) pipeline combining total seats against the mapped scalar, then forwards variables to the output engine.
- **`INDEC` / `OUTDEC`:** Assembly utility routines using custom radices to convert numeric characters from console buffers to executable binary metrics, handling safety signs (`-`/`+`) gracefully.

---

## 📋 Cinema Pricing Matrix

The application references the following embedded cost structure:

| Theater Name | Location / Address | Ticket Category | Price (USD) |
| :--- | :--- | :--- | :--- |
| **Film Theater** | North, 27 Garden Street | Under 6 Years Old / Child | \$15 |
| | | Adults | \$45 |
| | | Seniors | \$25 |
| **Action Theater** | South, Exit 9, 23 Rose Road | Under 6 Years Old / Child | \$5 |
| | | Adults | \$35 |
| | | Seniors | \$15 |

---

## 🚀 How to Run the Application

To execute and run this assembly program, you will need an **8086 Emulator** such as **EMU8086** 

### Using EMU8086 (Recommended)
1. Download and open the **EMU8086** IDE.
2. Create a new file and paste the complete assembly source code (`.asm`) into the editor workspace.
3. Click the **Compile** button to generate the `.exe` or `.com` executable.
4. Click **Run** to launch the interactive emulation terminal window.


## 👥 Contribution & Development

This project is built as a baseline application for low-level systems assembly analysis. Feel free to fork this project or introduce pull requests to embed modern upgrades such as interactive array tracking, database logging, or advanced error bounds checking routines.
