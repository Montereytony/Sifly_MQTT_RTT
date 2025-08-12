# 🚁 SiFly MQTT Drone RTT Tester

This project simulates **round-trip time (RTT)** measurement between a ground station (controller) and a drone over MQTT.
It uses two separate Python programs:

- **controller.py** — The *ground station* script that sends commands and measures RTT.
- **drone.py** — The *drone simulator* that listens for commands and sends responses.

By running these scripts on separate machines (or the same one with a network broker),
you can measure **real-world network latency** for drone command/response cycles.

---

## 📌 Features
- MQTT communication over **TLS (port 8883)** for security.
- Unique `command_id` for accurate RTT tracking.
- Separate topics for commands and responses.
- Simulated drone processing delay.
- Can run across LAN or the internet using any MQTT broker.

---

## 🛠 Requirements

- Python 3.7+
- `paho-mqtt` library
  Install using:

pip install paho-mqtt

- Access to an MQTT broker with:
- Hostname / port
- Username & password
- TLS enabled (for port 8883)

---

## 📡 MQTT Topics
- **`drone/rtt/command`** — Commands from controller → drone
- **`drone/rtt/response`** — Responses from drone → controller

---
(base) tony@MacBook-Pro-5 ~/Projects/Sifly_MQTT_Test % clear
(base) tony@MacBook-Pro-5 ~/Projects/Sifly_MQTT_Test % cat README.md
# 🚁 MQTT Drone RTT Tester

This project simulates **round-trip time (RTT)** measurement between a ground station (controller) and a drone over MQTT.
It uses two separate Python programs:

- **controller.py** — The *ground station* script that sends commands and measures RTT.
- **drone.py** — The *drone simulator* that listens for commands and sends responses.

By running these scripts on separate machines (or the same one with a network broker),
you can measure **real-world network latency** for drone command/response cycles.

---

## 📌 Features
- MQTT communication over **TLS (port 8883)** for security.
- Unique `command_id` for accurate RTT tracking.
- Separate topics for commands and responses.
- Simulated drone processing delay.
- Can run across LAN or the internet using any MQTT broker.

---

## 🛠 Requirements

- Python 3.7+
- `paho-mqtt` library
  Install using:

pip install paho-mqtt

- Access to an MQTT broker with:
- Hostname / port
- Username & password
- TLS enabled (for port 8883)

---

## 📡 MQTT Topics
- **`drone/rtt/command`** — Commands from controller → drone
- **`drone/rtt/response`** — Responses from drone → controller

---

## ⚙️ Configuration
Edit the following constants in both `controller.py` and `drone.py`:

MQTT_HOST = "your_broker_url"
MQTT_PORT = 8883
USERNAME = "drone_user"
PASSWORD = "drone_password_123"


---

## 🚀 Usage

### 1. Start the Drone Simulator
On one machine (or terminal), run:

python drone.py

This will:
- Connect to the broker
- Subscribe to `drone/rtt/command`
- Send back responses on `drone/rtt/response`

---

### 2. Start the Controller (Ground Station)
On another machine (or same machine), run:

python controller.py

This will:
- Send commands
- Measure RTT once the response is received
- Print latency in milliseconds

---

## 📊 Example Output
Connected
Sent Command: cmd_1723429031204991
RTT: 48.62ms (hover)
Sent Command: cmd_1723429033205781
RTT: 51.01ms (hover)


---

## 🖼 Architecture Diagram


<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/36d34a7e-4bbe-461d-8916-729d60effac3" />



---

## 🔮 Next Steps
- Replace `drone.py` with your actual drone’s MQTT interface.
- Log measurements for performance analysis.
- Add more command types beyond `"hover"`.

---

## 📝 License
MIT License – feel free to use and adapt.

