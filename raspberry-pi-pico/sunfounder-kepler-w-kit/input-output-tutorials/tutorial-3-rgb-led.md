# 🐨 Tutorial 3 - RGB LED

In this tutorial, we will learn how to control an RGB LED with a Raspberry Pi Pico using MicroPython. RGB LEDs can produce any color in the spectrum by mixing red, green, and blue lights, and are commonly used in a variety of projects such as mood lighting, visual effects, and indicators.

In this tutorial, we will use PWM (Pulse Width Modulation) to control the intensity of the red, green, and blue components of the LED, and create different colors by mixing these components in various proportions. We will also introduce the concept of mapping, which allows us to convert a range of values to another range, and use it to map a color value between 0 and 255 to a duty cycle value between 0 and 65535 that is suitable for PWM control.

By the end of this tutorial, you will have a basic understanding of how to use PWM and mapping to control RGB LEDs with a Raspberry Pi Pico, and will be able to apply this knowledge to create your own colorful projects!

### Components Needed

| Component           | Quantity |
| ------------------- | -------- |
| Raspberry Pi Pico W | 1        |
| Micro USB Cable     | 1        |
| Breadboard          | 1        |
| Wires               | Several  |
| Resistor            | 3 - 220Ω |
| RGB LED             | 1        |

### Fritzing Diagram

<figure><img src="../../../.gitbook/assets/RGB LED.png" alt=""><figcaption></figcaption></figure>

### Code

```python
from machine import Pin, PWM

pins = [13, 14, 15]
colors = ['red', 'green', 'blue']
pwms = [PWM(Pin(pin)) for pin in pins]
for pwm in pwms:
    pwm.freq(1000)

def map_color(color):
    return int(color * 65535 / 255)

def set_color(red, green, blue):
    pwms[0].duty_u16(map_color(red))
    pwms[1].duty_u16(map_color(green))
    pwms[2].duty_u16(map_color(blue))

set_color(255, 128, 0)
```

### Code Explanation

```python
from machine import Pin, PWM
```

This line imports the `Pin` and `PWM` classes from the `machine` module. These classes allow us to interact with the pins and generate PWM signals, respectively.

```python
pins = [13, 14, 15]
colors = ['red', 'green', 'blue']
pwms = [PWM(Pin(pin)) for pin in pins]
for pwm in pwms:
    pwm.freq(1000)
```

These lines define three variables: `pins`, which is a list of the pin numbers we will use to control the RGB LED; `colors`, which is a list of the corresponding color names; and `pwms`, which is a list of `PWM` objects that we will use to generate signals on the corresponding pins.

The `PWM` objects are created using list comprehension, which allows us to create a list of objects in a single line of code. We iterate over the `pins` list, creating a `Pin` object for each pin number and passing it as an argument to the `PWM` constructor. The resulting `PWM` object is added to the `pwms` list.

We then loop over each `PWM` object in the `pwms` list and set its frequency to 1000Hz using the `freq()` method. This sets the frequency of the PWM signal that will be generated on each pin.

```python
def map_color(color):
    return int(color * 65535 / 255)

def set_color(red, green, blue):
    pwms[0].duty_u16(map_color(red))
    pwms[1].duty_u16(map_color(green))
    pwms[2].duty_u16(map_color(blue))
```

These lines define two functions: `map_color()` and `set_color()`.

The `map_color()` function takes a single argument `color`, which is an integer in the range of 0-255 representing the intensity of a particular color (red, green, or blue). The function then performs a mathematical operation to map this input value to a 16-bit PWM duty cycle value in the range of 0-65535.

The `set_color()` function takes three arguments: `red`, `green`, and `blue`, which are the intensities of the corresponding color components. The function calls the `map_color()` function to map each color value to a PWM duty cycle value, and then sets the duty cycle of the corresponding `PWM` object using the `duty_u16()` method.

```
set_color(255, 128, 0)
```

This line calls the `set_color()` function with three arguments: 255 for full intensity red, 128 for half intensity green, and 0 for no blue. This sets the RGB LED to a yellow color.
