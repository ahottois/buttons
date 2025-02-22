ESP32 Home Assistant Button Controller
A custom ESP32 controller with two physical buttons and an OLED display to trigger Home Assistant scenarios. Each button can trigger two different scenarios depending on whether it is pressed once or twice, and displays customizable text on the OLED screen.
📋 Features

2 physical buttons with double-click detection
SH1106 128x64 OLED display for visual feedback
4 configurable Home Assistant scenarios
Customizable texts via Home Assistant
Secure communication with Home Assistant via ESPHome
USB or battery powered

🛠️ Required Hardware

ESP32 DevKit
SH1106 128x64 OLED Display (I2C)
2 push buttons
Connection wires
Case (optional)

📊 Connection Diagram

OLED Display (I2C)

SDA → GPIO21
SCL → GPIO22
VCC → 3.3V
GND → GND


Buttons

Button 1 → GPIO5 (pull-up)
Button 2 → GPIO18 (pull-up)
GND → GND



🚀 Installation
1. ESPHome Configuration

Copy the configuration file to your ESPHome folder
Modify WiFi settings:

yaml
