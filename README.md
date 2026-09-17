# 4S 5A SMART BMS (BQ76952 & STM32F103)

!!!This project is my first PCB design, developed as a 1st-year Electrical & Electronics Engineering student at Kahramanmaraş Sütçü İmam University to learn hardware design and communication architectures of Battery Management Systems (BMS).

!!!As it was created during the initial phase of my learning process, there may be complexities in the schematics and PCB trace routings. These will be optimized in future revisions.

---

## Component Selection and Circuit Rationale

### 1. Texas Instruments BQ76952 (Analog Front End)
* **Selection Reason:** Industry-standard AFE capable of precise cell voltage, current, and temperature measurements. 3S to 16S Li-Ion / LiFePO4 battery pack protection.
* **Connection Architecture:**
  * Provides a 3.3V regulated rail via the REG1 pin to power the MCU and CAN transceiver.
  * Current measurements are routed from a 1mΩ shunt resistor to SRP and SRN pins through a differential RC filter (100Ω resistors and 100nF capacitors).
  * Two 10kΩ NTC thermistors are connected to TS1 and TS2 for temperature tracking.
  * The BMS_ALERT pin is routed to STM32 PA0 to generate hardware interrupts during faults.

### 2. STM32F103CBT6 (Microcontroller)
* **Selection Reason:** Selected to learn the ARM Cortex-M3 architecture and hardware CAN Bus protocol.
* **Connection Architecture:**
  * VBAT, VDD, and VDDA power pins are connected to the +3V3 rail provided by the BQ76952. 100nF decoupling capacitors are placed in parallel between each power pin and GND to prevent voltage dips.
  * An 8MHz external crystal (HSE) with 22pF load capacitors is connected to PD0 and PD1 for accurate CAN Bus clock timing.
  * The NRST pin is protected with a 100nF capacitor and a 10kΩ pull-up resistor. BOOT0 is pulled to GND via a 10kΩ pull-down resistor to ensure boot execution from internal flash memory.

### 3. SN65HVD230 (CAN Bus Transceiver)
* **Selection Reason:** The 3.3V-native SN65HVD230 was selected because the board lacks a 5V rail and runs directly from the 3.3V LDO output of the BQ76952.
* **Connection Architecture:**
  * D (TX) and R (RX) pins are connected to STM32 PA12 (CAN_TX) and PA11 (CAN_RX).
  * A 120Ω termination resistor is placed across CANH and CANL to suppress signal reflections.
  * The Rs pin is pulled to GND through a 10kΩ resistor for high-speed operation mode.

### 4. I2C Communication Bus
* Since I2C is an open-drain architecture, 4.7kΩ pull-up resistors are connected from the +3V3 rail to both I2C_SDA and I2C_SCL lines to enable proper communication between the BQ76952 and STM32.

---

## PCB Design Status

* **Layer Count:** 2 Layers (FR4).
* **Copper Fills:** Continuous GND copper pours are applied to both F.Cu and B.Cu layers for noise suppression and thermal management.
* **DRC Status:** Verified via KiCad Design Rules Check with 0 Errors, 0 Warnings, and 0 Unconnected Items.

---

## File Structure

* BMS-Can-Bus.kicad_sch - Şematik / Schematic

* BMS-Can-Bus.kicad_pcb - PCB Yerleşimi / PCB Layout

* BMS-Can-Bus.kicad_pro - KiCad Proje Dosyası / Project File

* ksulog2.kicad_mod - KSÜ Logo Footprint

---

## Author Information

* **Hasan Berk Daşar**
* Kahramanmaraş Sütçü İmam University — Electrical & Electronics Engineering
* Open to technical feedback and constructive recommendations.









<img width="1437" height="667" alt="3" src="https://github.com/user-attachments/assets/830ccc1e-99d7-4d42-a82f-e6fdfee5b5d9" />
<img width="735" height="787" alt="15" src="https://github.com/user-attachments/assets/2b878add-5497-4477-b405-68b9fedcfdfa" />
<img width="801" height="871" alt="16" src="https://github.com/user-attachments/assets/b678c631-1360-4ec3-b7f9-9fc9c196e146" />


