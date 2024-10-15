# [Comparing Communication Protocols: I2C vs. SPI vs. CAN Bus](https://coreedges.com/comparing-communication-protocols-i2c-vs-spi-vs-can-bus)
#通信/协议/I2C #通信/协议/SPI #通信/协议/CAN

|Aspect|I2C|SPI|CAN Bus|
|---|---|---|---|
|Clocking|Synchronous (Master generates CLK)|Synchronous (Master generates CLK)|Asynchronous (No global clock)|
|Data Rate|Moderate (100 kbps - 5 Mbps)|High (Up to 65 Mbps)|Low to High (Up to 1 Mbps)|
|Distance|Short (Within PCB or few meters)|Short to Moderate (Within PCB)|Moderate to Long (Up to 1 km)|
|Electrical Standard|Voltage levels vary|Voltage levels vary|Differential (TTL, RS-485, etc.)|
|Error Handling|Basic (ACK/NACK)|Limited (No built-in error checking)|Advanced (Checksums, Error Frames)|
|Master-Slave Configuration|Yes|Yes|Yes|
|Maximum Devices|Typically limited by address space|Typically limited by CS/SS lines|Hundreds to Thousands|
|Multiple Masters|Supported (Multi-Master)|Supported (Multi-Master)|Supported (Multi-Master)|
|Number of Wires|2 (SDA, SCL)|4-5 (SCK, MOSI, MISO, CS/SS)|2 (CANH, CANL)|
|Topology|Bus|Bus|Bus|
|Use Cases|Sensors, Displays, EEPROMs|Flash Memory, LCDs, Real-time apps|Automotive, Industrial Automation|
[[I2C]] greatly saves IO space and is flexible, but due to the short distance, it is mostly ideally used in PCBs or an integrated device

[[SPI]], due to the high data rate, is commonly used for high-speed communication within PCBs

CAN is designed for robust(advanced error handling), long-distance communication, making it suitable for automotive and industrial applications.