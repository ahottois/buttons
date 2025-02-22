# ESP32 Home Assistant Button Controller

A custom ESP32 controller with two physical buttons and an OLED display to trigger Home Assistant scenarios. Each button can trigger two different scenarios depending on whether it is pressed once or twice, and displays customizable text on the OLED screen.

## 📋 Features

- 2 physical buttons with double-click detection
- SH1106 128x64 OLED display for visual feedback
- 4 configurable Home Assistant scenarios
- Customizable texts via Home Assistant
- Secure communication with Home Assistant via ESPHome
- USB or battery powered

## 🛠️ Required Hardware

- ESP32 DevKit
- SH1106 128x64 OLED Display (I2C)
- 2 push buttons
- Connection wires
- Case (optional)

## 📊 Connection Diagram

- **OLED Display (I2C)**
  - SDA → GPIO21
  - SCL → GPIO22
  - VCC → 3.3V
  - GND → GND

- **Buttons**
  - Button 1 → GPIO5 (pull-up)
  - Button 2 → GPIO18 (pull-up)
  - GND → GND

## 🚀 Installation

### 1. ESPHome Configuration

1. Copy the configuration file to your ESPHome folder
2. Modify WiFi settings:
```yaml
wifi:
  ssid: "your_ssid"
  password: "your_password"
```
3. Generate a new API key:
```yaml
api:
  encryption:
    key: "your_new_key"
```
4. Flash your ESP32 with the configuration

### 2. Home Assistant Configuration

1. Create the following input_text entities:
```yaml
input_text:
  scenario1_text:
    name: "Scenario 1 Text"
    initial: "Scenario 1"
  scenario2_text:
    name: "Scenario 2 Text"
    initial: "Scenario 2"
  scenario3_text:
    name: "Scenario 3 Text"
    initial: "Scenario 3"
  scenario4_text:
    name: "Scenario 4 Text"
    initial: "Scenario 4"
  default_text:
    name: "Default Text"
    initial: "Waiting..."
```

2. Create your scenarios:
```yaml
script:
  scenario_1:
    sequence:
      - ... # Your actions for scenario 1
  scenario_2:
    sequence:
      - ... # Your actions for scenario 2
  scenario_3:
    sequence:
      - ... # Your actions for scenario 3
  scenario_4:
    sequence:
      - ... # Your actions for scenario 4
```

## 🎮 Usage

- **Button 1**
  - Single click: Triggers scenario 1
  - Double click: Triggers scenario 2

- **Button 2**
  - Single click: Triggers scenario 3
  - Double click: Triggers scenario 4

The OLED display will show the text corresponding to the activated scenario for a few seconds, then return to the default text.

## ⚙️ Customization

### Modifying texts
1. Go to Home Assistant
2. Navigate to Configuration → Helpers → input_text
3. Modify the texts according to your needs

### Adjusting timings
In the ESPHome configuration file:
```yaml
globals:
  - id: double_click_timeout
    type: uint32_t
    initial_value: '400'  # Double-click timeout in milliseconds
  - id: script_timer
    type: int
    initial_value: '20'   # Text display duration
```

## 🔧 Troubleshooting

### Display doesn't turn on
- Check I2C connections
- Verify I2C address (default 0x3C)
- Run an I2C scan via ESPHome

### Buttons don't respond
- Check connections
- Verify pull-ups are properly configured
- Test buttons with a multimeter

### Scenarios don't trigger
- Check connection between ESP32 and Home Assistant
- Verify scenario names match exactly
- Check ESPHome logs for more information

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🤝 Contributing

Contributions are welcome! Feel free to:
1. Fork the project
2. Create a feature branch
3. Commit your changes
4. Push to the branch
5. Open a Pull Request
