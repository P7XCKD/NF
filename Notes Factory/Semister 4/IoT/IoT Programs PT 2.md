***Q.1 Write a Python program to blink an LED connected to GPIO pin 18 of a Raspberry Pi 4 using RPi/GPIOzero method.***  
#answer  

```R Pi method```

```python
import RPi.GPIO as GPIO
import time

GPIO.setmode(GPIO.BCM)   # Use Broadcom pin numbering
GPIO.setup(18, GPIO.OUT) # Set GPIO 18 as an output

while True:
    GPIO.output(18, GPIO.HIGH)  # Turn LED ON
    time.sleep(1)               # Wait 1 second
    GPIO.output(18, GPIO.LOW)   # Turn LED OFF
    time.sleep(1)               # Wait 1 second
```
```GPIO Zero Method```

```python
from gpiozero import LED
from time import sleep

led = LED(18)  # Define LED on GPIO 18

while True:
    led.on()  # Turn LED ON
    sleep(1)  # Wait 1 second
    led.off() # Turn LED OFF
    sleep(1)  # Wait 1 second

```
***

***Q.2 Write a Python program to read and write data from an RFID card sensor using Raspberry Pi 4 (RPi/GPIOzero method).***  
#answer  

```R Pi method```

```python
import RPi.GPIO as GPIO
from mfrc522 import SimpleMFRC522

reader = SimpleMFRC522()

choice = input("Press R to Read, W to Write: ").upper()

if choice == "W":
    text = input("Enter data to write: ")
    print("Place your card near the reader...")
    reader.write(text)
    print("Data written!")
elif choice == "R":
    print("Place your card near the reader...")
    card_id, text = reader.read()
    print("Card ID:", card_id)
    print("Data:", text)

GPIO.cleanup()
```
```GPIO Zero Method```

```python
from gpiozero import DigitalOutputDevice
from mfrc522 import SimpleMFRC522

reader = SimpleMFRC522()
rst_pin = DigitalOutputDevice(22)

choice = input("Press R to Read, W to Write: ").upper()

if choice == "W":
    text = input("Enter data to write: ")
    print("Place your card near the reader...")
    reader.write(text)
    print("Data written!")
elif choice == "R":
    print("Place your card near the reader...")
    card_id, text = reader.read()
    print("Card ID:", card_id)
    print("Data:", text)

rst_pin.off()
```
***
***Q.3 Write a Python program to capture an image using the Raspberry Pi Camera Module and save it as ‘IoT.jpg’.***  
#answer  

```python
from picamera import PiCamera
from time import sleep

camera = PiCamera()

camera.start_preview()
sleep(2)  # Allow camera to adjust to lighting
camera.capture('IoT.jpg')
camera.stop_preview()

print("Image saved as IoT.jpg")
```
***
***Q.4 Write a Python program for Raspberry Pi 4 to control an LED using a push button. The LED should turn ON when the button is pressed and turn OFF when the button is released. Use GPIO pin 18 for the LED and GPIO pin 17 for the button. Ensure the program continuously checks the button state and updates the LED accordingly (RPi method).***  
#answer  


```python
import RPi.GPIO as GPIO
from time import sleep

GPIO.setwarnings(False)
GPIO.setmode(GPIO.BCM)  

GPIO.setup(18, GPIO.OUT, initial=GPIO.LOW)  # LED on GPIO 18
GPIO.setup(17, GPIO.IN, pull_up_down=GPIO.PUD_UP)  # Button on GPIO 17 with pull-up resistor

while True:
    if GPIO.input(17) == GPIO.LOW:  # Button pressed (active low)
        GPIO.output(18, GPIO.HIGH)  # Turn LED ON
    else:
        GPIO.output(18, GPIO.LOW)   # Turn LED OFF
    sleep(1)  #  Delay to avoid rapid state changes
  ```
***

***Q.5 Write a Python script for Raspberry Pi 4 to generate the following LED blinking pattern using GPIO pins:***  
- There are four LEDs connected to GPIO pins 1, 2, 3, and 4.  
- LED 1 and LED 3 should turn ON simultaneously, while LED 2 and LED 4 remain OFF.  
- After 3 seconds, LED 2 and LED 4 should turn ON, while LED 1 and LED 3 turn OFF.  
- This pattern should repeat 5 times.  

#answer  

```python
import RPi.GPIO as GPIO
from time import sleep

GPIO.setwarnings(False)
GPIO.setmode(GPIO.BOARD)  

# Set up GPIO pins as output
GPIO.setup(1, GPIO.OUT, initial=GPIO.LOW)
GPIO.setup(2, GPIO.OUT, initial=GPIO.LOW)
GPIO.setup(3, GPIO.OUT, initial=GPIO.LOW)
GPIO.setup(4, GPIO.OUT, initial=GPIO.LOW)

count = 0

while count < 5:
    GPIO.output(1, GPIO.HIGH)  # Turn ON LED 1
    GPIO.output(3, GPIO.HIGH)  # Turn ON LED 3
    GPIO.output(2, GPIO.LOW)   # Turn OFF LED 2
    GPIO.output(4, GPIO.LOW)   # Turn OFF LED 4
    sleep(3)

    GPIO.output(1, GPIO.LOW)   # Turn OFF LED 1
    GPIO.output(3, GPIO.LOW)   # Turn OFF LED 3
    GPIO.output(2, GPIO.HIGH)  # Turn ON LED 2
    GPIO.output(4, GPIO.HIGH)  # Turn ON LED 4
    sleep(3)

    count += 1

GPIO.cleanup()  # Reset GPIO settings
```
***
***Q.6 Important libraries of Arduino IDE.***  
#answer  

- **DHT Library**:  
  - Used for interfacing **DHT11/DHT22** temperature and humidity sensors.  
  - Provides functions to read **temperature and humidity** easily.  
  - Required for IoT-based weather monitoring applications.  

- **ESP8266WiFi Library**:  
  - Enables **Wi-Fi connectivity** for ESP8266-based boards.  
  - Allows devices to **connect to the internet**, create access points, or communicate with servers.  
  - Essential for **IoT applications** requiring wireless data transmission.  

- **PubSubClient (MQTT) Library**:  
  - Implements the **MQTT (Message Queuing Telemetry Transport) protocol**.  
  - Used for **publishing and subscribing** to topics over the internet.  
  - Commonly used in **IoT applications** to send data between devices and cloud platforms.
***
***Q.7 Write a Python script to detect motion using a PIR sensor connected to a Raspberry Pi 4 and print “Motion Detected” on the console.***  
#answer  

```python
import RPi.GPIO as GPIO
from time import sleep

GPIO.setwarnings(False)
GPIO.setmode(GPIO.BCM)

PIR_PIN = 20  # PIR sensor input pin
LED_PIN = 21  # LED output pin

GPIO.setup(PIR_PIN, GPIO.IN)
GPIO.setup(LED_PIN, GPIO.OUT, initial=GPIO.LOW)

while True:
    if GPIO.input(PIR_PIN):  
        print("Motion Detected")
        GPIO.output(LED_PIN, GPIO.HIGH)  # Turn LED ON
    else:
        print("No Motion")
        GPIO.output(LED_PIN, GPIO.LOW)  # Turn LED OFF
    sleep(1)  # Delay to avoid rapid detection
  ```

***
***Q.8 Write an embedded C code to interface DHT11 sensor with ESP8266 and read temperature & humidity.***  
#answer  

```c
#include <ESP8266WiFi.h>
#include <DHT.h>

#define DHTPIN D4       // Define the pin where DHT11 is connected
#define DHTTYPE DHT11   // Define sensor type (DHT11)

DHT dht(DHTPIN, DHTTYPE);

void setup() {
    Serial.begin(115200);
    dht.begin();
}

void loop() {
    float temperature = dht.readTemperature(); // Read temperature in Celsius
    float humidity = dht.readHumidity();      // Read humidity

    if (isnan(temperature) || isnan(humidity)) {
        Serial.println("Failed to read from DHT sensor!");
    } else {
        Serial.print("Temperature: ");
        Serial.print(temperature);
        Serial.print("°C  |  Humidity: ");
        Serial.print(humidity);
        Serial.println("%");
    }

    delay(5000); // Wait 5 seconds before next reading
}
```
***

***Q.9 Write an embedded C code to connect ESP8266 with the internet.***  
#answer  

```c
#include <ESP8266WiFi.h>

const char* ssid = "YourWiFiSSID";       // Change this to your WiFi SSID
const char* password = "YourWiFiPassword";  // Change this to your WiFi password

void setup() {
    Serial.begin(115200);
    WiFi.begin(ssid, password);
    Serial.print("Connecting to Wi-Fi");

    while (WiFi.status() != WL_CONNECTED) {
        delay(1000);
        Serial.print(".");
    }

    Serial.println("\nConnected to Wi-Fi");
    Serial.print("IP Address: ");
    Serial.println(WiFi.localIP());  // Print the ESP8266 IP Address
}

void loop() {
    // Your main code here
}