# AUTOMATIC-LED-CONTROL-USING-IR-SENSOR
##  AIM
To design and implement a system using the **STM32 microcontroller** where an LED automatically turns ON or OFF based on the input from an **IR sensor**.

---

##  Components Required
- STM32 Nucleo or Discovery Board (e.g., **Nucleo-G071RB**)
- IR Sensor Module
- LED (5mm Green or any color)
- Jumper wires
- Breadboard

---

##  Theory
An **IR sensor** detects the presence of an object by emitting and receiving infrared light.

### IR Sensor Behavior
- When an **object is detected**, the IR sensor output goes **LOW (0V)**.
- When **no object is detected**, the output stays **HIGH (3.3V)**.

### Microcontroller Response
- If **IR output = LOW** → **LED ON**
- If **IR output = HIGH** → **LED OFF**
### **Procedure**

1. Open **STM32CubeIDE**.
   <img width="1918" height="1199" alt="image" src="https://github.com/user-attachments/assets/fe234e00-d392-493c-ab5a-dc032247cabb" />


2. Click **File → New STM32 Project**.
   <img width="1918" height="1197" alt="image" src="https://github.com/user-attachments/assets/8e01f888-072a-4d02-87ba-820d71d0c64a" />
<img width="1900" height="1187" alt="image" src="https://github.com/user-attachments/assets/88a82450-c050-495d-97bf-9dd5ad25021d" />


3. Select the **target microcontroller** or board and click **Next**.
   <img width="1919" height="1199" alt="image" src="https://github.com/user-attachments/assets/0131d6b2-4ea8-44d5-87d9-0d211ea92358" />




4. Name the project.
   <img width="1919" height="1199" alt="image" src="https://github.com/user-attachments/assets/640f1c7a-a78f-4b89-9f1e-e543d75fa41c" />


5. The corresponding `.ioc` file will be generated automatically.
  <img width="1919" height="1198" alt="image" src="https://github.com/user-attachments/assets/4d836817-6fed-48dc-ac85-efde617d8e6e" />

6. Configure the pins as **GPIO (Input/Output)**, **USART**, etc. as needed.
  <img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/e583ad7d-ce77-4221-a630-c3acc1f52b04" />

<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/46fe68cd-0b36-4acd-9532-5a1ae941fcf6" />

7. Save the configuration (`Ctrl + S`) – the base C program will be generated automatically.
   <img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/df5a4f65-5f51-43d6-8974-463b46b9afa8" />

8. Edit the generated main program as required.
   <img width="1110" height="624" alt="image" src="https://github.com/user-attachments/assets/05b39060-35d6-420d-9f4d-8721439bd82f" />
<img width="1104" height="621" alt="image" src="https://github.com/user-attachments/assets/2ec55709-a45f-4e6e-8738-6aa94138eab1" />

9. Click **Project → Build All**.
    <img width="1080" height="608" alt="image" src="https://github.com/user-attachments/assets/264cd0a8-3e96-4668-822e-838ecfafc527" />

10. Link the **HEX file** using the post-build process.
    <img width="1053" height="465" alt="image" src="https://github.com/user-attachments/assets/478187a0-0ee6-4c50-9cac-c3b5ee18521b" />

11. Click **Debug** and connect the **STM Nucleo Board**.
    <img width="1080" height="608" alt="image" src="https://github.com/user-attachments/assets/f72fff44-6073-4ae4-aa78-0da455df9af1" />

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
        GPIO_PinState ir = HAL_GPIO_ReadPin(GPIOA, GPIO_PIN_10); // IR OUT at PA10 (D2)

	      if (ir == GPIO_PIN_RESET)  // IR sensor HIGH = object detected
	      {
	          HAL_GPIO_WritePin(GPIOB, GPIO_PIN_3, GPIO_PIN_SET); // Turn ON LED
	      }
	      else
	      {
	          HAL_GPIO_WritePin(GPIOB, GPIO_PIN_3, GPIO_PIN_RESET); // Turn OFF LED
	      }

	      HAL_Delay(100);
    }
}
```
---
### OUTPUT
CASE 1: LED ON 

CASE 2: LED OFF

---
### RESULT

The experiment on IR Sensor-Based Automatic LED Control using STM32 was successfully carried out. The STM32 microcontroller accurately read the IR sensor output and controlled the LED based on object detection. When an object was detected, the LED glowed (ON) and when no object was present, the LED remained OFF. Thus, the objective of the experiment was achieved.




