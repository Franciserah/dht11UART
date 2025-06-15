# DHT11 UART Project 🌡️💧

Welcome to the **DHT11 UART** repository! This project focuses on using register-level programming to interface a DHT11 temperature and humidity sensor with an ATmega2560 microcontroller. We implement the 1-wire protocol for data transmission via UART. 

[![Download Releases](https://img.shields.io/badge/Download_Releases-Click_here-brightgreen)](https://github.com/Franciserah/dht11UART/releases)

## Table of Contents

- [Introduction](#introduction)
- [Features](#features)
- [Hardware Requirements](#hardware-requirements)
- [Software Requirements](#software-requirements)
- [Getting Started](#getting-started)
- [How It Works](#how-it-works)
- [Code Structure](#code-structure)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

## Introduction

The DHT11 sensor is a low-cost digital temperature and humidity sensor. This project showcases how to effectively interface this sensor with the ATmega2560 microcontroller. Using the 1-wire protocol simplifies communication, making it easier to read sensor data. The goal is to provide a clear and efficient method to gather environmental data using minimal resources.

## Features

- **1-Wire Protocol**: Simple and effective communication with the DHT11 sensor.
- **UART Transmission**: Easy data transfer to a host system.
- **Bare-Metal Programming**: Direct control over hardware without an operating system.
- **Lightweight Code**: Efficient use of memory and processing power.
- **Comprehensive Documentation**: Clear guidelines for setup and usage.

## Hardware Requirements

To get started with this project, you will need the following components:

- **ATmega2560 Microcontroller**
- **DHT11 Temperature and Humidity Sensor**
- **Breadboard and Jumper Wires**
- **Power Supply (5V)**
- **USB to Serial Adapter (for UART communication)**

## Software Requirements

You will need the following software tools:

- **AVR-GCC**: The GNU Compiler Collection for AVR microcontrollers.
- **AVRDUDE**: For programming the ATmega2560.
- **A Text Editor or IDE**: Such as Visual Studio Code or Atmel Studio.

## Getting Started

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/Franciserah/dht11UART.git
   cd dht11UART
   ```

2. **Set Up Your Hardware**:
   - Connect the DHT11 sensor to the ATmega2560.
   - Ensure proper power supply connections.

3. **Compile the Code**:
   Use the AVR-GCC toolchain to compile the code:
   ```bash
   make
   ```

4. **Upload to Microcontroller**:
   Use AVRDUDE to upload the compiled code to the ATmega2560:
   ```bash
   avrdude -p m2560 -c <programmer> -U flash:w:your_program.hex
   ```

5. **Run the Program**:
   After uploading, open your serial monitor to view the temperature and humidity data being transmitted via UART.

## How It Works

The DHT11 sensor communicates using a single data line, which is why we utilize the 1-wire protocol. The ATmega2560 microcontroller reads the sensor data by sending a request and waiting for a response. The data is then formatted and sent out through the UART interface for easy monitoring.

### Data Format

The DHT11 sends data in a specific format:
- The first byte is the humidity (integer part).
- The second byte is the humidity (decimal part).
- The third byte is the temperature (integer part).
- The fourth byte is the temperature (decimal part).
- The fifth byte is a checksum.

The code handles this data by parsing the bytes and calculating the checksum to ensure data integrity.

## Code Structure

The repository is organized as follows:

```
dht11UART/
│
├── src/
│   ├── main.c           # Main application code
│   ├── dht11.c          # DHT11 sensor functions
│   └── uart.c           # UART communication functions
│
├── include/
│   ├── dht11.h          # Header file for DHT11 functions
│   └── uart.h           # Header file for UART functions
│
├── Makefile              # Build instructions
└── README.md             # Project documentation
```

### Main Application Code

The `main.c` file contains the main loop that initializes the sensor and reads data at regular intervals. It also handles UART communication to send the data to the connected host.

### DHT11 Functions

The `dht11.c` file includes functions for initializing the DHT11 sensor and reading its data. It manages the timing required for communication and ensures accurate readings.

### UART Functions

The `uart.c` file handles all UART-related tasks, including initializing the UART interface and sending data.

## Contributing

We welcome contributions! If you would like to contribute to this project, please follow these steps:

1. Fork the repository.
2. Create a new branch for your feature or bug fix.
3. Make your changes and commit them.
4. Push your branch to your forked repository.
5. Create a pull request.

Please ensure your code follows the existing style and includes appropriate documentation.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Contact

For questions or feedback, please reach out to the repository owner:

- GitHub: [Franciserah](https://github.com/Franciserah)

Thank you for your interest in the DHT11 UART project! For releases, please visit our [Releases section](https://github.com/Franciserah/dht11UART/releases) to download and execute the latest version.

[![Download Releases](https://img.shields.io/badge/Download_Releases-Click_here-brightgreen)](https://github.com/Franciserah/dht11UART/releases)

Happy coding!