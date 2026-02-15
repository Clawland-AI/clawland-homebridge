# clawland-homebridge

Smart home bridge for the Clawland edge AI ecosystem.

---

## Overview

`clawland-homebridge` connects Claw agents and their sensor data to smart home platforms, enabling voice control and home automation integration.

## Supported Platforms

| Platform | Protocol | Status |
|----------|----------|--------|
| **Apple HomeKit** | HAP | Planned |
| **Home Assistant** | REST + MQTT | Planned |
| **Google Home** | Matter | Planned |
| **Amazon Alexa** | Smart Home Skill | Planned |

## Use Cases

- "Hey Siri, what's the server room temperature?" → picclaw reads sensor, returns via HomeKit
- Home Assistant dashboard showing all Claw sensor data alongside other smart home devices
- Automated scenes: IF greenhouse temp > 35°C THEN open vent (via Claw relay) AND turn on fan (via HomeKit)

## Architecture

```
┌────────────┐     ┌───────────────────┐     ┌────────────────┐
│ Smart Home │────→│ clawland-homebridge│────→│ picclaw / Claw │
│ Platform   │←────│                   │←────│ Agent Fleet    │
│            │     │ • HAP Server      │     │                │
│ HomeKit    │     │ • HA Integration  │     │ • Sensors      │
│ Home Asst  │     │ • Device Registry │     │ • Actuators    │
│ Google     │     │ • State Sync      │     │ • Status       │
└────────────┘     └───────────────────┘     └────────────────┘
```

## Exposed Accessories

| Claw Sensor | HomeKit Accessory | Home Assistant Entity |
|-------------|-------------------|----------------------|
| Temperature | TemperatureSensor | sensor.temperature |
| Humidity | HumiditySensor | sensor.humidity |
| Motion (PIR) | MotionSensor | binary_sensor.motion |
| Smoke (MQ-2) | SmokeSensor | binary_sensor.smoke |
| Relay | Switch | switch.relay |
| Door Contact | ContactSensor | binary_sensor.door |

## Quick Start

```bash
git clone https://github.com/Clawland-AI/clawland-homebridge.git
cd clawland-homebridge
npm install
npm run dev
```

## Contributing

See [CONTRIBUTING.md](https://github.com/Clawland-AI/.github/blob/main/CONTRIBUTING.md). Smart home integrations earn contribution points toward the quarterly [Revenue Pool](https://github.com/Clawland-AI/.github/blob/main/CONTRIBUTOR-REVENUE-SHARE.md).

## License

MIT — See [LICENSE](LICENSE)
