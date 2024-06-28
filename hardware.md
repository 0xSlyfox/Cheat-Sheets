# Common Baud Rates

300
1200
2400
4800
9600
14400
19200
38400
57600
115200
230400
460800
921600

# Minimum Pins for Common Protocols
## I2C

SDA (Data Line)
SCL (Clock Line)

## SPI

MOSI (Master Out Slave In)
MISO (Master In Slave Out)
SCLK (Serial Clock)
SS (Slave Select)

## UART

TX (Transmit)
RX (Receive)
GND (Ground)

## JTAG

TDI (Test Data In)
TDO (Test Data Out)
TCK (Test Clock)
TMS (Test Mode Select)
TRST (Test Reset, optional)
GND (Ground)

## CAN

CAN_H (CAN High)
CAN_L (CAN Low)
GND (Ground)

## USB

VBUS (Power)
D+ (Data Plus)
D- (Data Minus)
GND (Ground)

## Ethernet (RJ45):

TX+ (Transmit Plus)
TX- (Transmit Minus)
RX+ (Receive Plus)
RX- (Receive Minus)
GND (Ground)

# Common Voltage Levels

## Logic Levels:

__1.8V__: Used in modern low-power ICs
__3.3V__: Common in many microcontrollers and digital circuits
__5V__: Standard for older and some current digital circuits

## Power Supply Levels:

__1.2V, 1.8V, 2.5V, 3.3V, 5V, 12V__
__-12V__: Often used in dual rail power supplies for analog circuits
__24V__: Common in industrial applications
__48V__: Used in telecom applications

# Important Interfaces and Connectors

GPIO (General Purpose Input/Output): Varies by microcontroller, often 1.8V, 3.3V, or 5V logic levels
ADC (Analog-to-Digital Converter): Typically 10-bit, 12-bit, 16-bit resolution
DAC (Digital-to-Analog Converter): Similar to ADC in bit resolution
PWM (Pulse Width Modulation): Used for motor control, LEDs, and other applications

# Debugging Tools and Techniques

Multimeter: Measure voltage, current, resistance
Oscilloscope: Visualize electrical signals
Logic Analyzer: Capture and analyze digital signals
Protocol Analyzers: Specific to protocols like I2C, SPI, UART, etc.
JTAG Debugger: Interface for debugging microcontrollers and FPGAs

# Common Connectors and Their Pin Counts

Dupont (Female and Male headers): Typically used with 0.1-inch pitch headers (think jumper wires connectors)
IDC (Insulation-Displacement Connector): Often used for flat ribbon cables, e.g., 10, 16, 20, 26 pins
Molex: Variety of connectors with different pin counts, often used in power supply connections
Barrel Jack: Common for power supply, typically 2 pins
Banana Plug: Often used in test equipment, typically 2 pins (positive and ground)

# Miscellaneous Tips

Pull-up/Pull-down Resistors: Ensure defined logic levels on inputs
Bypass Capacitors: Placed near power pins of ICs to filter noise
Decoupling Capacitors: Used to stabilize power supply voltage
PCB Layout Tips: Keep high-speed signals short, avoid running traces under high-current paths, use ground planes.
