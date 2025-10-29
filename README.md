# LED-BLINK
# 💡 Experiment 01 – Interfacing a Digital Output (LED) with ARM Development Board

### 🎯 **Aim**
To interface a digital output (LED) to an ARM development board and write a blink code.

---

### ⚙️ **Components Required**
- STM32CubeIDE  
- NUCLEO ARM Development Board  

---

### 🧠 **Theory**

**ARM (Advanced RISC Machine)** is a 32-bit processor architecture developed by ARM Holdings. It is widely used in embedded systems and SoC (System-on-Chip) products. Many semiconductor companies like Samsung, Atmel, and Texas Instruments license ARM architecture to design their own SoCs.
### 🧩 **What is an ARM7 Processor?**
The **ARM7 processor** is commonly used in embedded system applications. It provides a balance between the classic ARM architecture and the newer Cortex series, offering an excellent platform for both hardware and software development.
### 🔍 **LPC2148 Microcontroller**
The **LPC2148**, developed by NXP Semiconductors (Philips), is a 16/32-bit ARM7-based microcontroller featuring a wide range of peripherals.
#### **Key Features**
- 16/32-bit ARM7TDMI-S core in LQFP64 package  
- On-chip **Flash memory**: 32 KB – 512 KB  
- On-chip **SRAM**: 8 KB – 40 KB  
- **ISP/IAP** via on-chip bootloader  
- **Embedded ICE-RT** and **Real Monitor** for real-time debugging  
- **USB 2.0** full-speed device controller with 2 KB endpoint RAM  
- **10-bit ADC** (6 or 14 channels, 2.44 μs conversion time)  
- **10-bit DAC** for analog output  
- **Timers:** Two 32-bit timers, watchdog, and PWM unit  
- **RTC** with 32 kHz clock input  
- **UARTs (2x), I²C (2x)** up to 400 kbit/s  
- **5V-tolerant GPIOs**, 21 external interrupt pins  
- **Max CPU Clock:** 60 MHz using on-chip PLL (lock time 100 µs)  
- **Crystal Frequency:** 1 MHz – 25 MHz  
- **Power modes:** Idle and Power-down with peripheral clock scaling  

---

### 🧭 **Procedure**

1. Open **STM32CubeIDE**.
  
![WhatsApp Image 2025-10-29 at 07 38 27_ad6bc608](https://github.com/user-attachments/assets/b751dedb-58f1-4fe4-a4cd-47b2da56f7f6)

2. Click **File → New STM32 Project**.
   ![WhatsApp Image 2025-10-29 at 07 53 27_2f737740](https://github.com/user-attachments/assets/875b8072-431e-4bdb-88b8-b7680fb0f1aa)

   ![WhatsApp Image 2025-10-29 at 07 53 46_8344de17](https://github.com/user-attachments/assets/9f08faff-4a8b-4d82-ad29-aff1e2319393)


4. Select the **target microcontroller** or board and click **Next**.
  ![WhatsApp Image 2025-10-29 at 07 54 02_e2528955](https://github.com/user-attachments/assets/af8558b0-4a01-4e89-9ea2-97ccd8dc7f81)

5. Name the project.
   <img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/2c5c31dc-4c9e-48da-a7bf-30c30835b787" />


6. The corresponding `.ioc` file will be generated automatically.
 ![WhatsApp Image 2025-10-29 at 07 54 35_6ac2a168](https://github.com/user-attachments/assets/71a2fe71-3061-45a2-9d2a-6cb4fe19d394)


7. Configure the pins as **GPIO (Input/Output)**, **USART**, etc. as needed.
  ![WhatsApp Image 2025-10-29 at 07 54 54_cb359a39](https://github.com/user-attachments/assets/7e30e2eb-fa9d-4ae1-b054-b94a4efa63de)
![WhatsApp Image 2025-10-29 at 07 55 22_3bb6a85f](https://github.com/user-attachments/assets/c0d4051e-c6f8-419f-80ac-5d2a3d790ed0)


8. Save the configuration (`Ctrl + S`) – the base C program will be generated automatically.
  ![WhatsApp Image 2025-10-29 at 07 55 52_34723193](https://github.com/user-attachments/assets/fef77f02-3391-4fe5-a817-1260ad942d22)

 
9. Edit the generated main program as required.
  <img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/1707b147-19bf-418a-a145-5eebb28e4a16" />

10. Click **Project → Build All**.
  <img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/03fbfd02-b308-4fa1-b252-000109def26b" />


11. Link the **HEX file** using the post-build process.
  <img width="1912" height="1079" alt="image" src="https://github.com/user-attachments/assets/c4e4ad28-10c1-4a10-a041-7f1414a4f13c" />


12. Click **Debug** and connect the **STM Nucleo Board**.
   <img width="966" height="588" alt="image" src="https://github.com/user-attachments/assets/d1fca878-6288-4a7a-91b1-d7e14713a00f" />

13. Click **Run** to execute the program.
    
---

### 💻 **Program**


```c
#include "main.h"

void SystemClock_Config(void);
static void MX_GPIO_Init(void);

int main(void)
{
    HAL_Init();
    SystemClock_Config();
    MX_GPIO_Init();

    while (1)
    {
        HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_RESET);
        HAL_Delay(1000);
        HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_SET);
        HAL_Delay(1000);
    }
}
```
---
### OUTPUT
CASE 1: LED ON 
![WhatsApp Image 2025-10-29 at 08 08 15_71904d33](https://github.com/user-attachments/assets/0535c63b-a017-43a3-9ffe-05c44a8580f1)


CASE 2: LED OFF
![WhatsApp Image 2025-10-29 at 08 08 17_73fd5432](https://github.com/user-attachments/assets/79c37e3d-85c7-4c95-9300-495f283c2bca)

---
### RESULT
Interfacing a digital output with ARM microcontroller is executed and the results are verified.
