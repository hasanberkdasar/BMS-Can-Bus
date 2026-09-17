#  Smart BMS (BQ76952 & STM32F103) — 4S Lithium Battery Management System

##  About The Project & Personal Context
This project is an open-source **4S Smart Battery Management System (BMS)** designed around the **Texas Instruments BQ76952** Analog Front-End (AFE) and an **STM32F103C8T6** microcontroller. 

As a **1st-year Electrical and Electronics Engineering student**, this project represents my very first custom PCB design experience. It was built purely as a personal prototype, a learning step, and a hands-on exploration of power electronics and embedded hardware design. Because of my beginner level, the schematic and layout might appear complex, unoptimized, or messy in certain areas—it was developed as a continuous trial-and-error learning path.

---

## ⚠️ Important Engineering Note: Scaling Down from 100A to 5A

* **Original Scope vs. Current Reality:** The initial goal was to build a high-power 100A continuous BMS. However, as the design progressed, I realized that managing thermal dissipation and routing high-current copper paths properly on a standard 2-layer PCB exceeded my current technical expertise. 
* **Current Power Rating:** To keep the design safe and realistic, the continuous current rating has been officially scaled down to **5A continuous (15A peak)** for this version.
* **Why Some Traces Look Unusually Large:** You will notice that certain power paths on the board are disproportionately wide for a 5A system. These are remnants of the original 100A power path layout attempts.
* **Tested Status:** Please note that **this design has NOT been physically fabricated or hardware-tested**. It exists purely as a CAD/EDA design file.
* **Future Outlook:** The project is temporarily put on hold. Once I gain further engineering experience and technical proficiency, I plan to revisit this project to optimize thermal management and push the layout to support 100A peak and 50–60A continuous power on a computer simulation environment.

---

##  Architecture & Component Selection

### 1. Topology Selection (4S System)
A 4-series (4S) Lithium-ion / LiFePO4 configuration was selected as it matches standard low-voltage applications (such as 12V system upgrades, small EVs, or robotics power distribution) while offering a safe voltage range for learning.

### 2. Key Components & Selection Rationale
* **Texas Instruments BQ76952 (AFE):** Chosen for its highly integrated cell monitoring, hardware-level overvoltage/undervoltage protection, and flexible low-side/high-side FET drive capabilities.
* **STM32F103C8T6 (MCU):** Used as the primary host controller to read telemetry data via I2C/SMBus from the BQ76952, execute custom BMS logic, and manage external communications.
* **SN65HVD230 (CAN Transceiver):** Selected to convert the MCU's UART/CAN signals into a robust differential CAN-bus signal, making the BMS compatible with industrial and automotive telemetry networks.
* **NTC Thermistors:** External thermistor headers are added for real-time thermal monitoring of the battery pack and power MOSFETs.

---

##  Circuit Interconnections & Features

* **Power Path:** Utilizes dual-layer 2mm copper traces with a high-side back-to-back MOSFET pair (paralleled discharge/charge FETs) for battery isolation, and a low-side shunt resistor for current sensing.
* **Noise Immunity & Layout:** Decoupling capacitors are placed in immediate proximity to the power pins of both the AFE and MCU. The 8MHz crystal load capacitors are locked close to the oscillator pins.
* **EMC Shielding:** Top and bottom layers are encased with a solid Ground (GND) polygon pour for noise suppression.
* **Communication Interface:** Dedicated CAN-Bus interface pins enable continuous telemetry streaming (cell voltages, pack current, temperatures, and fault flags) to external dashboards or vehicle control units (VCU).

<img width="801" height="871" alt="16" src="https://github.com/user-attachments/assets/634f0757-9060-494e-ad6c-87fc9f4221fb" />
<img width="952" height="450" alt="19" src="https://github.com/user-attachments/assets/7063282a-6f06-4687-8e64-220adbe2d860" />
<img width="735" height="787" alt="15" src="https://github.com/user-attachments/assets/8a2d0022-6a02-4389-b5bb-7d9b51d83f01" />



