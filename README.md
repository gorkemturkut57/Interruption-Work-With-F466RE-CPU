# STM32 LED Blink and Button Control

This project demonstrates a simple application on an STM32 microcontroller where an LED blinks continuously, and a button press makes the LED stay on for a specified duration.

## Features

- Blinks an LED (LD2) continuously with a delay.
- When a button (BUTTON) is pressed, the LED stays on for 1 second.

## Requirements

- STM32 microcontroller (e.g., STM32F4 series).
- STM32CubeIDE or any other IDE compatible with STM32 development.
- ST-LINK/V2 or any other programmer/debugger compatible with STM32.
- Basic knowledge of embedded C programming.

## Getting Started

### Hardware Setup

1. Connect the LED to the appropriate GPIO pin (configured as LD2 in the code).
2. Connect a push-button to another GPIO pin (configured as BUTTON in the code).

### Software Setup

1. **Clone the Repository**
    ```sh
    git clone https://github.com/your-username/stm32-led-button-control.git
    cd stm32-led-button-control
    ```

2. **Open the Project in STM32CubeIDE**
    - Launch STM32CubeIDE.
    - Open the project directory you cloned.

3. **Build the Project**
    - Click on the "Build" button or go to `Project -> Build All`.

4. **Flash the Firmware**
    - Connect your STM32 microcontroller to your computer using ST-LINK/V2 or another programmer.
    - Click on the "Debug" button or go to `Run -> Debug` to flash the firmware to the microcontroller.

### How It Works

1. **Initialization**
    - The microcontroller and peripherals are initialized using `HAL_Init()`, `SystemClock_Config()`, `MX_GPIO_Init()`, and `MX_USART2_UART_Init()`.

2. **Main Loop**
    - In the main loop, the LED blinks with a delay of 100 ms.
    - If the button is pressed, the `HAL_GPIO_EXTI_Callback` function sets the `tick_timer` to 1000 ms (1 second), and the LED stays on for this duration.

3. **Interrupt Handling**
    - The button press generates an external interrupt.
    - The `HAL_GPIO_EXTI_Callback` function is called to handle the interrupt and update the LED state and `tick_timer`.

### Code Explanation

- **main.c**:
    - Contains the main application code.
    - Initializes the system clock, GPIO, and UART.
    - Implements the main loop to control the LED.
    - Contains the interrupt callback function for button press handling.

### Contributing

Feel free to fork this repository and contribute by submitting pull requests. For major changes, please open an issue first to discuss what you would like to change.

### License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

