# ESP32-CAM Image Stream Server

This project implements a simple MJPEG image streaming server for the ESP32-CAM module. It allows you to view a live video stream from the camera over your local WiFi network.

## Features

*   **MJPEG Streaming**: Low-latency video streaming.
*   **Static IP Configuration**: Ensure the camera is always available at the same address.
*   **PlatformIO & Arduino IDE Support**: Ready to build with your preferred tool.

## Hardware Required

*   ESP32-CAM Module (AI-Thinker Model recommended)
*   FTDI Programmer (for uploading code)
*   5V Power Supply

## Configuration

Before uploading, you **MUST** configure your network settings in `ESP32_CAM_Server/ESP32_CAM_Server.ino`:

1.  **WiFi Credentials**:
    ```cpp
    const char* ssid = "YOUR_WIFI_SSID";
    const char* password = "YOUR_WIFI_PASSWORD";
    ```
2.  **Static IP Settings** (Optional but recommended):
    ```cpp
    IPAddress local_IP(192, 168, 1, 200); // The IP you want for the camera
    IPAddress gateway(192, 168, 1, 1);    // Your router's IP
    ```

---

## How to Run with Arduino IDE

1.  **Install ESP32 Board Support**:
    *   Open Arduino IDE > File > Preferences.
    *   Add this URL to "Additional Boards Manager URLs":
        `https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_index.json`
    *   Go to Tools > Board > Boards Manager, search for `esp32`, and install `esp32 by Espressif Systems`.

2.  **Select Board**:
    *   Go to Tools > Board > ESP32 Arduino > **AI Thinker ESP32-CAM**.

3.  **Open Project**:
    *   Open `ESP32_CAM_Server/ESP32_CAM_Server.ino`.

4.  **Connect & Upload**:
    *   Connect GPIO 0 to GND on the ESP32-CAM (this puts it in flash mode).
    *   Connect the module to your computer via the FTDI programmer.
    *   Click **Upload**.
    *   Once done, **disconnect GPIO 0 from GND** and press the RESET button on the module.

5.  **Monitor**:
    *   Open Serial Monitor (Tools > Serial Monitor) and set baud rate to `115200`.
    *   You should see the "WiFi connected" message.

---

## How to Run with PlatformIO (VS Code)

1.  **Prerequisites**:
    *   Install **Visual Studio Code**.
    *   Install the **PlatformIO IDE** extension.

2.  **Open Project**:
    *   Open the root folder of this repository in VS Code.

3.  **Build & Upload**:
    *   Connect GPIO 0 to GND on the ESP32-CAM.
    *   Click the **PlatformIO: Upload** button (arrow icon) in the bottom status bar.
    *   PlatformIO will automatically download the necessary dependencies and toolchains.

4.  **Monitor**:
    *   Click the **PlatformIO: Serial Monitor** button (plug icon) to view the output.

---

## Usage

1.  Ensure the ESP32-CAM remains powered.
2.  Open a web browser on a device connected to the same WiFi network.
3.  Navigate to `http://192.168.1.200` (or the Static IP you configured).
4.  You should see the live video stream!
