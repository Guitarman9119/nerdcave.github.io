# 🐶 Tutorial 2 - LED Bar Graph

A project using an LED bar graph can be a fun and useful way to display information or create visual effects. An LED bar graph is a series of LEDs arranged in a row or column, where each LED represents a different level of intensity or value.

For example, an LED bar graph can be used to display the level of volume on a stereo system or the strength of a Wi-Fi signal. In this case, each LED would represent a different level of volume or signal strength, and the number of lit LEDs would correspond to the current value.

In other cases, an LED bar graph can be used to create visual effects, such as a scrolling marquee or a pattern of flashing lights. This can be a great way to add some visual interest to a project or create an eye-catching display for an art installation.



### Components Needed

| Component           | Quantity  |
| ------------------- | --------- |
| Raspberry Pi Pico W | 1         |
| Micro USB Cable     | 1         |
| Breadboard          | 1         |
| Wires               | Several   |
| Resistor            | 10 (220Ω) |
| LED Bar Graph       | 1         |

### Fritzing Diagram

<figure><img src="../../../.gitbook/assets/Project 2 - LED BAR.png" alt=""><figcaption><p>Fritzing Breadboard View</p></figcaption></figure>

### Code

```python
import machine
import utime

pin = [6,7,8,9,10,11,12,13,14,15]
led= []
for i in range(10):
    led.append(None)
    led[i] = machine.Pin(pin[i], machine.Pin.OUT)

while True:
    for i in range(10):
        led[i].toggle()
        utime.sleep(0.2)
```

### Code Explanation

```python
import machine
import utime
```

These lines import the necessary modules. `Pin` is a class from the `machine` module that allows us to control digital pins on the Raspberry Pi Pico board. `utime` is a module that provides time-related functions, such as `sleep`, which we'll use later to pause the program for a specified amount of time.

```python
pin = [6,7,8,9,10,11,12,13,14,15]
led= []
```

These lines define two variables. `pin` is a list that contains the pin numbers that are connected to the 10 LEDs. `led` is an empty list that will be used to store the `Pin` objects that represent the LED pins.

```python
for i in range(10):
    led.append(None)
    led[i] = Pin(pin[i], Pin.OUT)
```

These lines initialize the `led` list. We start by appending `None` to the list 10 times, to create 10 empty slots. We then use a `for` loop to iterate over the `led` list and assign a `Pin` object to each slot. We use the `Pin` constructor to create a new `Pin` object, passing in the pin number (`pin[i]`) and the mode (`Pin.OUT`), which sets the pin as an output.

```python
while True:
    for i in range(10):
        led[i].toggle()
        utime.sleep(0.2)
```

These lines define the main loop of the program. The loop runs indefinitely (`while True:`), and each iteration of the loop toggles the state of each LED in the `led` list using the `toggle()` method of the `Pin` class. This causes each LED to turn on and off in sequence, creating a visual effect similar to a progress bar or scrolling marquee. We also use `utime.sleep(0.2)` to pause the program for 200 milliseconds (0.2 seconds) between each LED toggle, which controls the speed of the animation.
