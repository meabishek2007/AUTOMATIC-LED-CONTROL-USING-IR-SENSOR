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
  <img width="1557" height="936" alt="image" src="https://github.com/user-attachments/assets/b5ab9b5e-810b-4993-a108-d553b88bd749" />


6. Configure the pins as **GPIO (Input/Output)**, **USART**, etc. as needed.
 <img width="1560" height="945" alt="image" src="https://github.com/user-attachments/assets/cd3f855e-9f51-4d38-b9a3-fc40ebd8c8c4" />

<img width="1561" height="942" alt="image" src="https://github.com/user-attachments/assets/49855f80-298b-4d4c-ac6e-c7ea9a1dca5f" />

7. Save the configuration (`Ctrl + S`) – the base C program will be generated automatically.
   <img width="1558" height="944" alt="image" src="https://github.com/user-attachments/assets/747781df-e8ca-42cb-af7e-1df28383d7cc" />

8. Edit the generated main program as required.
   <img width="1110" height="624" alt="image" src="https://github.com/user-attachments/assets/b3f544b1-32b2-4ace-958b-73241d6db562" />
<img width="1104" height="621" alt="image" src="https://github.com/user-attachments/assets/7828bb5b-a63e-44a9-af8b-78669cf15ede" />

9. Click **Project → Build All**.
    <img width="1080" height="608" alt="image" src="https://github.com/user-attachments/assets/0352ce8b-faf6-4f20-93a8-242c95633156" />

10. Link the **HEX file** using the post-build process.
    <img width="1053" height="465" alt="image" src="https://github.com/user-attachments/assets/ad8a7ccd-d6d0-43dd-be44-c473405a4950" />

11. Click **Debug** and connect the **STM Nucleo Board**.
   <img width="1080" height="608" alt="image" src="https://github.com/user-attachments/assets/98c69ee6-46e8-4b7a-8f81-cf10c562ed3f" />

12. Click **Run** to execute the program.
    
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

![WhatsApp Image 2025-11-10 at 14 08 29_1c553d15](https://github.com/user-attachments/assets/b2d13136-db3b-4a6c-ba93-d4b2dea9fb17)
CASE 2: LED OFF

![WhatsApp Image 2025-11-10 at 14 08 19_fb58f2b7](https://github.com/user-attachments/assets/4b86822f-98f3-4908-a8f9-be2f33c06c92)

---
### RESULT

The experiment on IR Sensor-Based Automatic LED Control using STM32 was successfully carried out. The STM32 microcontroller accurately read the IR sensor output and controlled the LED based on object detection. When an object was detected, the LED glowed (ON) and when no object was present, the LED remained OFF. Thus, the objective of the experiment was achieved.




