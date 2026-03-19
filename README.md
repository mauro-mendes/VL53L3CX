# VL53LX Time-of-Flight Sensor Example (Raspberry Pi 5 Compatible)

![Raspberry Pi 5](https://img.shields.io/badge/RPi-5-green)

This project demonstrates how to use the STMicroelectronics VL53L3CX Time-of-Flight sensor with a Raspberry Pi.

This repository is based on the original implementation and has been adapted to work reliably on **Raspberry Pi 5**.

---

## 📌 Changes from Upstream

This fork includes the following fixes and improvements:

* Fixed I2C addressing mode (**7-bit instead of 10-bit**)
* Added reliable sensor reset using **XSHUT via GPIO26**
* Replaced legacy GPIO handling with `pinctrl` (Raspberry Pi 5 compatible)
* Adjusted reset timing for stable initialization
* Updated build and run instructions (`vl53lx_pi`)
* Tested and validated on Raspberry Pi 5

---

## 📦 Requirements

```bash
sudo apt update
sudo apt install build-essential make i2c-tools libczmq-dev
```

Enable I2C:

```bash
sudo raspi-config
# Interface Options → I2C → Enable
```

---

## 🔌 Wiring

| VL53L3CX Pin | Raspberry Pi  |
| ------------ | ------------- |
| VIN          | 3.3V          |
| GND          | GND           |
| SDA          | GPIO2 (Pin 3) |
| SCL          | GPIO3 (Pin 5) |
| XSHUT        | GPIO26        |
| INT          | Not used      |

### Notes

* XSHUT is controlled via GPIO26 for reliable reset
* Direct 3.3V on XSHUT may work, but is not recommended for repeated runs

---

## ⚙️ Build

```bash
git clone https://github.com/mauro-mendes/VL53L3CX.git
cd VL53L3CX
make
make vl53lx_pi
```

---

## ▶️ Run

```bash
sudo ./bin/vl53lx_pi
```

---

## ⚠️ Troubleshooting

### Remote I/O error

```text
errno=121 (Remote I/O error)
ERROR: CONTROL INTERFACE
```

#### Causes:

* Long cables on I2C
* Poor connections
* Signal noise

#### Solution:

* Use **short jumper wires**
* Avoid Ethernet cables for I2C
* Ensure solid grounding

---

## ⚡ Known Issues

* I2C may become unstable with long wires
* Proper XSHUT reset is required between runs

---

## 📷 Example Output

*(original image preserved)*

C program:
![Wiring diagram](screenshot.png)
Python subscriber:
![Wiring diagram](screenshot2.png)

---

## 📚 Original Project

https://github.com/74ls04/vl53lx-pi

---

## 👨‍💻 Author

Adapted for Raspberry Pi 5 by Mauro Mendes

---

## 📄 License

Same as upstream repository
