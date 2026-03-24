# VL53LX Time-of-Flight Sensor Example (Raspberry Pi 5 Compatible)

![Raspberry Pi 5](https://img.shields.io/badge/RPi-5-green)

This project demonstrates how to use the STMicroelectronics VL53L3CX Time-of-Flight sensor with a Raspberry Pi, including a ready-to-use Python subscriber for real-time data processing.

---

## 📌 Changes from Upstream

- Fixed I2C addressing mode (7-bit instead of 10-bit)
- Added reliable sensor reset using XSHUT via GPIO26
- Replaced legacy GPIO handling with pinctrl (Raspberry Pi 5 compatible)
- Adjusted reset timing for stable initialization
- Updated build and run instructions
- Tested on Raspberry Pi 5

---

## 📦 Requirements

sudo apt update  
sudo apt install build-essential make i2c-tools libczmq-dev python3-zmq  

Enable I2C:

sudo raspi-config

---

## 🔌 Wiring

VIN → 3.3V  
GND → GND  
SDA → GPIO2 (Pin 3)  
SCL → GPIO3 (Pin 5)  
XSHUT → GPIO26  

---

## ⚙️ Build

git clone https://github.com/mauro-mendes/VL53L3CX.git  
cd VL53L3CX  
make  
make vl53lx_pi  

---

## ▶️ Run

sudo ./bin/vl53lx_pi  

---

## 🐍 Python Subscriber (Recommended)

Location:

python/subscriber.py

Install:

sudo apt install python3-zmq

Run:

Terminal 1:
sudo ./bin/vl53lx_pi

Terminal 2:
cd python  
python3 subscriber.py

---

## ⚠️ Troubleshooting

Remote I/O error:
- Check wiring
- Avoid long cables
- Use proper pull-ups

---

## 📷 Example Output

![Wiring diagram](screenshot.png)
![Wiring diagram](screenshot2.png)

---

## 📚 Original Project

https://github.com/74ls04/vl53lx-pi

---

## 👨‍💻 Author

Mauro Mendes

---

## 📄 License

Same as upstream