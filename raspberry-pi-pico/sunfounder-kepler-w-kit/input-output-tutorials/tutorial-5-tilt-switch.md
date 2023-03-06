# 🐼 Tutorial 5 - Tilt Switch

A tilt switch is a type of switch that operates by tilting the device on which it is mounted. It is a simple and inexpensive way to detect orientation or inclination and is commonly used in various electronic projects. In this tutorial, we will be using a tilt switch with the Raspberry Pi Pico board to detect when the switch is tilted, and print a message to the console.

### Components Needed

| Component           | Quantity |
| ------------------- | -------- |
| Raspberry Pi Pico W | 1        |
| Micro USB Cable     | 1        |
| Breadboard          | 1        |
| Wires               | Several  |
| Resistor            | 1 - 10KΩ |
| Tilt Switch         | 1        |

### Fritzing Diagram

<figure><img src="../../../.gitbook/assets/Tilt switch.png" alt=""><figcaption><p>Frtizing Breadboard Diagram</p></figcaption></figure>

### Code

```python
from machine import Pin
import utime
button = machine.Pin(15, machine.Pin.IN)
while True:
    if button.value() == 0:
        print("The switch works!")
        utime.sleep(1)
```



### Code Explanation

```python
from machine import Pin
import utime
```

This code imports the `Pin` class from the `machine` module, which allows us to control the input and output pins on the Raspberry Pi Pico. The `utime` module is also imported, which allows us to pause the program for a specified amount of time.

```python
button = Pin(15, Pin.IN)
```

This code sets up pin 15 as an input pin, which will be used to read the state of the tilt switch. The `Pin.IN` argument specifies that the pin should be set up for input.

```python
while True:
    if switch.value() == 0:
        print("The switch works!")
        utime.sleep(1)
```

This code continuously loops while the program is running, checking the state of the button. The `switch.value()` method returns the current state of the button, which is either 0 or 1. If the button is tilted or closed, the value will be 0.

If the value of the button is 0, the program prints a message to the console indicating that the switch is working. It then pauses for one second using the `utime.sleep(1)` function call.

The program will continue to loop and check the state of the button as long as the program is running.
