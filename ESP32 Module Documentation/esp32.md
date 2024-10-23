# ESP32 Module Documentation

#### Overview

The ESP32 is a versatile Wi-Fi and Bluetooth-enabled microcontroller module developed by Espressif Systems. It is highly popular for embedded systems projects due to its rich feature set, low power consumption, and support for various protocols, making it a go-to choice for IoT applications, robotics, home automation, and more.

### Key Features

- **Dual-core Xtensa LX6 processors** running at up to 240 MHz.
- **Wi-Fi** (802.11 b/g/n) and **Bluetooth 4.2** (Classic and BLE).
- **Integrated Flash** (typically 4MB).
- **SRAM**: 520 KB on-chip SRAM.
- **GPIO Pins**: 34 programmable GPIOs.
- **DACs**: 2 × 8-bit DACs.
- **ADCs**: 18-channel 12-bit ADCs.
- **SPI, I2C, I2S, UART** communication protocols.
- **PWM (Pulse Width Modulation)**: 16 channels.
- **Timers**: Multiple hardware timers for scheduling tasks.
- **RTC** (Real-Time Clock) for low-power operations.
- **Ultra-low-power (ULP) co-processor** for handling deep sleep modes.
- **Integrated capacitive touch sensors**: 10 channels.
- **Security features**: Secure boot, flash encryption, cryptographic hardware acceleration.

### Block Diagram

1. **Processor**: Dual-core Xtensa LX6
2. **RAM**: 520 KB of internal SRAM (split into Data and Instruction memory)
3. **Flash Memory**: 4 MB (depends on variant)
4. **Wi-Fi**: Integrated 802.11 b/g/n module
5. **Bluetooth**: Dual-mode Bluetooth (Classic + BLE)
6. **GPIO**: 34 GPIO pins, many of which are multiplexed with other features like UART, SPI, I2C, etc.
7. **Peripheral Interfaces**:
   - **UART**: Up to 3 UARTs
   - **SPI**: Up to 4 SPI interfaces
   - **I2C**: Up to 2 I2C interfaces
   - **PWM**: 16 independent PWM channels
   - **ADC**: 18-channel 12-bit ADCs

### Power Modes

1. **Active Mode**: ESP32 is fully powered and running at up to 240 MHz. Both cores can be used, Wi-Fi and Bluetooth are active, and peripherals are available.
2. **Modem-sleep Mode**: The CPU is active, but the Wi-Fi or Bluetooth modules are turned off to save power.
3. **Light-sleep Mode**: The CPU is paused, and only peripheral interrupts or RTC can wake it up. Wi-Fi and Bluetooth radios are also powered down.
4. **Deep-sleep Mode**: Only the RTC and ULP coprocessor are running to handle low-power tasks. The main CPU is powered down, allowing significant power savings.
5. **Hibernation Mode**: Everything except a small part of the RTC is powered down. This mode consumes the least amount of power.

### GPIO Pin Capabilities

Each GPIO on the ESP32 can be configured for multiple purposes, such as:

- **Digital Input/Output**: All pins can be used as digital inputs or outputs.
- **Analog Inputs**: Pins that support ADC functionality can be used for analog inputs.
- **PWM Output**: Pulse Width Modulation is available on most GPIO pins.
- **Touch Sensing**: Some GPIO pins can also function as capacitive touch sensors.
- **Interrupts**: GPIOs can be configured to trigger interrupts on changes in state (rising edge, falling edge, etc.).

### Important Pins

- **GPIO 0**: Used for entering programming mode (must be low during boot for flashing).
- **GPIO 2**: Used for boot status and can output an onboard LED signal in some modules.
- **GPIO 4, 16, 17, 27**: Commonly used for sensor arrays (like in your line-following robot project).
- **GPIO 21, 22**: Standard I2C pins (SDA and SCL).
- **GPIO 12–15, 18–19**: Typically used for SPI communication.
- **GPIO 34–39**: Input-only pins that cannot be used for output.

### Communication Protocols

1. **Wi-Fi**:
   - Supports 802.11 b/g/n at 2.4 GHz.
   - Can operate in Access Point (AP), Station (STA), or AP+STA modes.
   - Up to 150 Mbps bandwidth.

2. **Bluetooth**:
   - Supports both Bluetooth Classic (for connecting to legacy devices) and BLE (Bluetooth Low Energy).
   - BLE is useful for low-power communication and IoT devices.
  
3. **UART**:
   - Up to three UART interfaces for serial communication with other devices like sensors or peripherals.
   - Can use both hardware and software flow control.
  
4. **SPI**:
   - Four SPI interfaces, often used for high-speed communication with devices like sensors, SD cards, or displays.
  
5. **I2C**:
   - Two I2C interfaces for communication with devices such as EEPROMs, displays, and sensors.
   - Supports master and slave modes.

6. **I2S**:
   - The I2S protocol is mainly used for audio data transmission.
   - Can function in master or slave mode, and supports half- and full-duplex communication.

### Power Management

1. **Operating Voltage**: 3.3V
   - The ESP32 operates on a 3.3V power supply, although the input voltage to the module (through the VIN pin) can range from 5V to 12V.
   
2. **Current Consumption**:
   - In active mode with Wi-Fi: around 160–260 mA.
   - Light-sleep mode: 0.8–1.1 mA.
   - Deep-sleep mode: 10–150 μA.
   - Hibernation mode: as low as 5 μA.

### Memory

- **RAM**: 520 KB on-chip SRAM.
- **Flash**: Typically 4 MB SPI Flash, but the amount can vary depending on the ESP32 module variant.
- **EEPROM Emulation**: The ESP32 does not have built-in EEPROM, but you can emulate EEPROM using the flash memory.

### Peripherals

1. **Timers**: 
   - ESP32 has multiple hardware timers, which can be used for scheduling tasks and generating delays with microsecond precision.

2. **RTC (Real-Time Clock)**:
   - The built-in RTC enables the ESP32 to keep track of time while in deep-sleep or hibernation modes.
   - It also supports alarms and periodic wake-ups in low-power modes.

3. **Touch Sensors**:
   - The ESP32 features 10 capacitive touch-sensitive GPIOs, which can be used to detect touch inputs.
   
4. **PWM**:
   - 16 channels for controlling devices like LEDs, motors, or servos. You can set the duty cycle and frequency for precise control.

5. **Analog-to-Digital Converter (ADC)**:
   - The ESP32 features up to 18 channels of 12-bit ADC with a resolution of 4096.
   - It can read voltages in the range of 0–3.3V (limited by the reference voltage).

6. **Digital-to-Analog Converter (DAC)**:
   - The module provides two 8-bit DAC channels, which can be used to generate analog signals like sound waves or voltage levels.

### Programming the ESP32

#### Common Development Environments

1. **Arduino IDE**:
   - The ESP32 can be programmed using the familiar Arduino IDE with an added ESP32 board package. This allows for simple integration of libraries and easy-to-understand syntax.
   
2. **ESP-IDF (Espressif IoT Development Framework)**:
   - The official development framework provided by Espressif for advanced projects. It offers deeper control over ESP32 features and is ideal for larger, performance-critical applications.
   
3. **PlatformIO**:
   - Another versatile and professional development environment for embedded systems that supports the ESP32.

### Flashing the ESP32

To program the ESP32, the module must be put into **bootloader mode**. This can be done either manually or automatically (through an auto-reset circuit). Here's a typical procedure:

1. **Connect ESP32 to your computer** using a USB cable.
2. **Press and hold the BOOT button** while clicking the RESET button.
3. **Release the BOOT button** after a couple of seconds. The ESP32 will enter bootloader mode.
4. **Upload your code** from the IDE.

### Example Code (Arduino IDE)

```cpp
void setup() {
  // Initialize Serial communication
  Serial.begin(115200);

  // Initialize GPIO pin
  pinMode(2, OUTPUT);  // LED pin

  // Connect to Wi-Fi
  WiFi.begin("SSID", "PASSWORD");

  while (WiFi.status() != WL_CONNECTED) {
    delay(1000);
    Serial.println("Connecting to Wi-Fi...");
  }
  
  Serial.println("Connected to Wi-Fi");
}

void loop() {
  digitalWrite(2, HIGH);  // Turn on LED
  delay(1000);            // Wait for a second
  digitalWrite(2, LOW);   // Turn off LED
  delay(1000);            // Wait for a second
}
```

### Conclusion

The ESP32 module is a powerful and flexible microcontroller, well-suited for a wide range of applications

, including IoT, robotics, and home automation. Its rich set of features like dual-core processors, Wi-Fi, Bluetooth, GPIOs, and low-power modes make it an ideal choice for developers. The wide support in different development environments like Arduino, ESP-IDF, and PlatformIO makes it accessible for beginners and professionals alike.