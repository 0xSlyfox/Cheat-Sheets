# Protocol Data Rates

## Common Baud Rates

- 300
- 1200
- 2400
- 4800
- 9600
- 14400
- 19200
- 38400
- 57600
- 115200
- 230400
- 460800
- 921600

## Other Protocols

### I2C

- Standard mode: 100 kbps
- Fast mode: 400 kbps
- Fast mode plus: 1 Mbps
- High-speed mode: 3.4 Mbps

### SPI

- Typically up to 10 Mbps, can go higher depending on hardware

### CAN

- Low-speed: Up to 125 kbps
- High-speed: Up to 1 Mbps

### USB

- USB 1.1: 12 Mbps (Full-speed)
- USB 2.0: 480 Mbps (High-speed)
- USB 3.0: 5 Gbps (Super-speed)

### Ethernet

- 10BASE-T: 10 Mbps
- 100BASE-TX: 100 Mbps
- 1000BASE-T: 1 Gbps

# Minimum Pins for Common Protocols

## I2C

- SDA (Data Line)
- SCL (Clock Line)

## SPI

- MOSI (Master Out Slave In)
- MISO (Master In Slave Out)
- SCLK (Serial Clock)
- SS (Slave Select)

## UART

- TX (Transmit)
- RX (Receive)
- GND (Ground)

## JTAG

- TDI (Test Data In)
- TDO (Test Data Out)
- TCK (Test Clock)
- TMS (Test Mode Select)
- TRST (Test Reset, optional)
- GND (Ground)
## CAN

- CAN_H (CAN High)
- CAN_L (CAN Low)
- GND (Ground)

## USB

- VBUS (Power)
- D+ (Data Plus)
- D- (Data Minus)
- GND (Ground)

## Ethernet (RJ45)

- TX+ (Transmit Plus)
- TX- (Transmit Minus)
- RX+ (Receive Plus)
- RX- (Receive Minus)
- GND (Ground)

# Common Voltage Levels

## Logic Levels

- **1.8V**: Used in modern low-power ICs
- **3.3V**: Common in many microcontrollers and digital circuits
- **5V**: Standard for older and some current digital circuits

## Power Supply Levels

- **1.2V, 1.8V, 2.5V, 3.3V, 5V, 12V**
- **-12V**: Often used in dual rail power supplies for analog circuits
- **24V**: Common in industrial applications
- **48V**: Used in telecom applications

# Important Interfaces and Connectors

- **GPIO (General Purpose Input/Output)**: Varies by microcontroller, often 1.8V, 3.3V, or 5V logic levels
- **ADC (Analog-to-Digital Converter)**: Typically 10-bit, 12-bit, 16-bit resolution
- **DAC (Digital-to-Analog Converter)**: Similar to ADC in bit resolution
- **PWM (Pulse Width Modulation)**: Used for motor control, LEDs, and other applications

# Debugging Tools and Techniques

- **Multimeter**: Measure voltage, current, resistance
- **Oscilloscope**: Visualize electrical signals
- **Logic Analyzer**: Capture and analyze digital signals
- **Protocol Analyzers**: Specific to protocols like I2C, SPI, UART, etc.
- **JTAG Debugger**: Interface for debugging microcontrollers and FPGAs

# Common Connectors and Their Pin Counts

- **Dupont (Female and Male headers)**: Typically used with 0.1-inch pitch headers (think jumper wires connectors)
- **IDC (Insulation-Displacement Connector)**: Often used for flat ribbon cables, e.g., 10, 16, 20, 26 pins
- **Molex**: Variety of connectors with different pin counts, often used in power supply connections
- **Barrel Jack**: Common for power supply, typically 2 pins
- **Banana Plug**: Often used in test equipment, typically 2 pins (positive and ground)

# Miscellaneous Tips

- **Pull-up/Pull-down Resistors**: Ensure defined logic levels on inputs
- **Bypass Capacitors**: Placed near power pins of ICs to filter noise
- **Decoupling Capacitors**: Used to stabilize power supply voltage
- **PCB Layout Tips**: Keep high-speed signals short, avoid running traces under high-current paths, use ground planes.

# Common Pin Out Diagrams

![[JTAG Connector PinOut Diagram 1.png]]

# Bypassing a Pull-Down Resistor on a UART Pin

Bypassing a pulldown resistor on a UART pin typically involves ensuring that the pin is driven to a high level (logic high) when needed, even though there is a pulldown resistor attempting to pull it to a low level (logic low). Here are the steps to bypass or override a pulldown resistor on a UART pin:

## Method 1: Using an External Pull-Up Resistor

1. **Calculate the Appropriate Pull-Up Resistor Value**:
    - Choose a pull-up resistor value low enough to override the pulldown but high enough to limit current flow.
    - Common pull-up resistor values range from 1kΩ to 10kΩ, depending on the value of the pulldown resistor.
2. **Connect the Pull-Up Resistor**:
    - Connect one end of the pull-up resistor to the UART pin.
    - Connect the other end to the VCC (logic high voltage, typically 3.3V or 5V).

Example:

lua

Copy code

`| VCC | | ----> Pull-Up Resistor (eg. 4.7kΩ) | | ----------> UART Pin | | ----> Pull-Down Resistor (eg. 10kΩ) | | GND`

## Method 2: Directly Driving the Pin

1. **Set the Pin High**:
    - Configure the UART pin as an output on your microcontroller.
    - Set the output level of the pin to high (logic high).

python

Copy code

`# Example for setting a GPIO pin high on a Raspberry Pi import RPi.GPIO as GPIO  def setUartPinHigh():     # Assume the UART pin is connected to GPIO pin 17 (BCM numbering)     uartPin = 17          # Set up the GPIO pin     GPIO.setmode(GPIO.BCM)  # Use BCM pin numbering     GPIO.setup(uartPin, GPIO.OUT)          # Set the pin high     GPIO.output(uartPin, GPIO.HIGH)  # Call the function to set the pin high setUartPinHigh()`

# Linux Tools for Hardware Hacking

## General Tools

1. **GDB** - GNU Debugger for debugging programs.
2. **OpenOCD** - Open On-Chip Debugger for debugging and flashing ARM devices.
3. **Radare2** - Advanced command line-based reverse engineering framework.
4. **Ghidra** - Software reverse engineering (SRE) framework.
5. **Frida** - Dynamic instrumentation toolkit for developers, reverse-engineers, and security researchers.

## Firmware

1. **Binwalk** - Analyze, reverse engineer, and extract firmware images.
2. [**Firmwalker**](https://github.com/craigz28/firmwalker) - Walks through extracted firmware file systems looking for interesting files.
3. [**E-M-B-A**](https://github.com/e-m-b-a/emba?tab=readme-ov-file) - Automated Firmware extraction suite
4. [**Firmadyne**](https://github.com/firmadyne/firmadyne) - Firmware emulation platform for various architectures
5. [**Firmware-Mod-Kit**](https://github.com/rampageX/firmware-mod-kit) - Firmware modification suite for recompiling extracted firmware with your changes

## JTAG and Debugging

1. **OpenOCD** - Open On-Chip Debugger for JTAG and SWD debugging.
2. **UrJTAG** - JTAG interface tool.
3. **PyOCD** - Python library for programming and debugging Arm Cortex-M microcontrollers.

## Protocol Analysis

1. **Wireshark** - Network protocol analyzer.
2. **Saleae Logic** - Logic analyzer software (works with Saleae hardware).
3. **sigrok** - Cross-platform signal analysis software suite.

## Serial Communication

1. **Minicom** - Terminal emulator for serial communication.
2. **Screen** - Terminal multiplexer with support for serial communication.
3. **Picocom** - Minimal terminal emulator for serial communication.

## USB Analysis

1. **usbmon** - USB monitoring framework included in the Linux kernel.
2. **usbtop** - USB monitoring tool.
3. **Wireshark** - With USBPcap for capturing USB traffic on Windows, and directly on Linux.

## I2C/SPI Tools

1. **i2c-tools** - A heterogeneous set of I²C tools for Linux.
2. **spidev** - Userspace interface to SPI devices.

## CAN Bus Tools

1. **can-utils** - Linux-CAN / SocketCAN user space applications.

## Flash and EEPROM Programming

1. **flashrom** - Identify, read, write, verify, and erase flash chips.
2. **avrdude** - Software for programming Atmel AVR Microcontrollers.
3. **pyspiflash** - A utility for programming SPI flash memory chips.

## Logic Analyzers

1. **sigrok-cli** - Command-line tool for controlling logic analyzers and analyzing signals.
2. **PulseView** - Graphical user interface for sigrok.

## FPGA Tools

1. **Vivado** - Xilinx FPGA development tool (requires license).
2. **Quartus** - Intel/Altera FPGA development tool (requires license).
3. **yosys** - Open source Verilog synthesis tool.

## Miscellaneous Tools

1. **fwup** - Firmware update tool.
2. **openFPGALoader** - Universal utility for programming FPGAs.
3. **dfu-util** - Device Firmware Upgrade (DFU) USB programmer.
4. [picopwner](https://github.com/CTXz/stm32f1-picopwner)- Dump read-out protected STM32F1's

## Precompiled Binaries

1. [Precompiled MIPS Binaries](https://github.com/darkerego/mips-binaries)

# Basic Command Cheatsheet

## Flashrom

Read and save the firmware from a flash chip to a file using flashrom.
```shell
flashrom -r backup.bin -p <name of your programmer eg. ch341_a>
```

## Binwalk

Extract nested filesystems recursively
```shell
binwalk -Mer firmware.bin
```

Hexdump the file

```shell
binwalk -X firmware.bin
```

Analyze a file for embedded file systems

```shell
binwalk -E firmware.bin
```

Detect the entropy for a file and output a graph

```shell
binwalk -E firmware.bin
```

**Save Entropy Graph as PNG**
```shell
binwalk -E -J firmware.bin
```

If `-E` is giving you errors use
```shell
binwalk --entropy firmware.bin
```

Enable gzip extract

```shell
binwalk -z firmware.bin
```

Keep extracted files after analysis

```shell
binwalk -K firmware.bin
```

Whitelist Extraction Rules

```shell
binwalk -W <whitelist> firmware.bin
```

Ignore Extraction Rules

```shell
binwalk -I <blacklist> <file>
```

Only display specified file types

```shell
binwalk -y <signature> <file>
```
Example
```shell
binwalk -y 'jpeg png' <file>
```

Terminate after first result, usually used with `-I`, This is useful when regular binwalk commands aren't yielding a lot of info

```shell
binwalk -I --term firmware.bin
```


## Strings

Detect all strings

```shell
strings firmware.bin
```

Specify the minimum string length. The default is 4 characters.

```shell
strings -n 10 firmware.bin
```

Select the character encoding of the strings to be found:

- s: single 7-bit ASCII (default)
- S: single 8-bit ISO-8859-1 characters
- b: 16-bit big-endian
- l: 16-bit little-endian
- B: 32-bit big-endian
- L: 32-bit little-endian

```shell
strings -e l firmware.bin
```

## Readelf

Basic Usage
```shell
readelf -a file.elf
```

### Specific Sections and Headers

File Header

```shell
readelf -h <file>
```

Program Headers

```shell
readelf -l <file>
```

Section Headers

```shell
readelf -S <file>
```

String Tables

```shell
readelf -x .strtab <file>
```

Symbol Tables

```shell
readelf -s <file>
```

Dynamic Section

```shell
readelf -d <file>
```

Notes

```shell
readelf -n <file>
```

Relocation Information

```shell
readelf -r <file>
```

### Detailed and Debugging Information

Section Details
```shell
readelf -p <section> <file>
```

Unwind Information
```shell
readelf -u <file>
```

Version Information
```shell
readelf -V <file>
```

Wide Format Output
```shell
readelf -W <file>
```

### ELF Header and Section Information

Display ELF Header
```shell
readelf -e <file>
```

Display Section Groups
```shell
readelf --section-groups <file>
```

Display all Information from Specific Sections
```shell
readelf -x .text <file>
```

### Dynamic Linking Information
Dynamic Linking Information
```shell
readelf --dynamic-syms <file>
```

Display Library Dependencies
```shell
readelf -d <file>
```

### Hexadecimal Dump
Hex Dump of Sections
```shell
readelf -x <section> <file>
```

### Other Useful Flags
Version Information
```shell
readelf -v
```

Help
```shell
readelf -h
```

## DD

Using dd to carve out section of a binary such as an AES private key

### Step 1: Analyze the Binary with Binwalk

First, you need to identify the sections of the binary file you are interested in. Use `binwalk` to scan the file and get the offset and size information.

```shell
binwalk firmware.bin
```

### Step 2: Identify the Offset and Size

From the `binwalk` output, identify the offset (in decimal or hexadecimal) and size of the section you want to carve out. The output will look something like this:

```shell
DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
4627          0x1213          Some data description
7537          0x1D71          Another data description
```
### Step 3: Carve Out the Section Using `dd`

Use the `dd` command to extract the specific section from the binary file. You need to specify the input file, the starting offset (skip), and the number of bytes to extract (count).

**Syntax:**

```shell
dd if=<file> of=carved_section.bin bs=1 skip=4627 count=2000
```

- `if=<input_file>`: The input file (binary file).
- `of=<output_file>`: The output file where the carved section will be saved.
- `bs=1`: Set the block size to 1 byte.
- `skip=<offset>`: The starting offset to begin carving out data (in bytes).
- `count=<size>`: The number of bytes to extract from the offset.

### Example

Suppose you want to extract the section starting at offset `4627` (decimal) with a size of `2000` bytes.

1. Identify the offset and size using `binwalk`:
    
```shell
binwalk <file>

```
    
    Output:
```shell
DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
4627          0x1213          Some data description
7537          0x1D71          Another data description

```
2. Use `dd` to carve out the section:
```shell
dd if=<file> of=carved_section.bin bs=1 skip=4627 count=2000
```

### Notes

- If the offset is in hexadecimal, you can convert it to decimal using `printf` or `bc`:

```shell
offset_hex="0x1213"
offset_decimal=$(printf "%d" $offset_hex)
```

- Adjust the `count` parameter based on the actual size of the section you need to extract.
