# -Automated-Toll-Gate-Security-System-using-OpenCV-and-ESP8266
This project uses Python and OpenCV to detect and read vehicle number plates. An ESP8266 module checks each plate against a stored database, sends SMS notifications to owners, and triggers alerts for blacklisted or stolen vehicles.

## Files

- `ANPR.py` —  Python Script for Number Plate recognition.
- `backend.c` —  C code for enabling real-time SMS alerts and verifyig number plates in the Supabase database.
- `README.md` — This file.


## Folder Access
- TO ACCESS THE FOLDER CLICK ON THIS LINK:
  https://drive.google.com/drive/folders/1Zh__nBS50MH7-o3vS-tiKpl4PzcJP2gg?usp=drive_link

---
## Overview
### This project consists of two main components working in tandem:

-Computer Vision Module : Captures video, detects license plates using EasyOCR, and sends the data to the microcontroller.

-IoT Controller (ESP8266): Receives plate data, verifies it against a synchronized cloud database (Supabase), and triggers SMS alerts (Twilio) based on the vehicle's status                             (Normal vs. Blacklisted).


---
## Features
- Uses OpenCV and EasyOCR to extract text from vehicle license plates.

- Normal Vehicles: Sends a welcome/detection SMS to the registered owner.

- Blacklisted Vehicles: Immediately alerts the Control Room with the vehicle details.

- Cloud Synchronization: Periodically fetches vehicle data from Supabase to ensure the local database is up-to-date.

---
## Requirements

### Hardware

-ESP32 Development Board (WiFi Module)

-Webcam (USB or Integrated)

-PC/Laptop (To run the Python processing script)

### Software & Services

- Python 3.x

- OpenCV, EasyOCR, Imutils, Requests

- Arduino IDE (C/C++)

- Libraries: WiFi, HTTPClient, ArduinoJson, Preferences

- Supabase (PostgreSQL Database)

- Twilio (SMS Gateway)
---

## Installation and Setup
### Database Setup (Supabase)

  - Create a Supabase project.

  - Create a table named vehicles.

  - Add the following columns: Number Plate (text), Owner Name (text), Phone Number (text), Blacklisted (text/boolean).

  - Copy your Project URL and API Key.

### Microcontroller Setup (ESP8266/ESP32)

  -Open backend.c in Arduino IDE.

  -Install the required libraries via Library Manager:

  - ArduinoJson

  - Preferences

  - WiFiClientSecure

### Configuration:
Update the following variables in the code with your credentials:

- const char* ssid = "YOUR_WIFI_SSID";
- const char* password = "YOUR_WIFI_PASSWORD";
- const char* supabase_url = "YOUR_SUPABASE_URL/rest/v1/vehicles";
- const char* supabase_api_key = "YOUR_SUPABASE_KEY";
- const char* twilio_sid = "YOUR_TWILIO_SID";
- const char* twilio_token = "YOUR_TWILIO_TOKEN";


### Upload the code to your ESP32.

  - Open the Serial Monitor (Baud Rate: 115200) to find the ESP32 IP Address.

### Computer Vision Setup (Python)

  - Install Python dependencies: pip install -r requirements.txt


  - Open ANPR.py.

  - Update the IP address to match your ESP8266/ESP32: esp32_ip = 'http://<YOUR_ESP32_IP>/receivePlate'

  - Run the python script:










