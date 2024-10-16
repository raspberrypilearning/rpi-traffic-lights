<html>
  <div style="position: relative; overflow: hidden; padding-top: 56.25%;">
    <iframe style="position: absolute; top: 0; left: 0; right: 0; width: 100%; height: 100%; border: none;" src="https://www.youtube.com/embed/-YZ6Rrho85I?rel=0&cc_load_policy=1" allowfullscreen allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share">
    </iframe>
  </div><br>
</html>

### Code the traffic lights

--- task ---

Create a new file by clicking **New**. 

--- /task ---

--- task ---

Save the new file straight away by clicking **Save**; name the file `trafficlights.py`.

--- /task ---

You have three LEDs: red, amber, and green. Perfect for traffic lights! There's even a built-in interface for traffic lights in GPIO Zero.

--- task ---

Import `Button` and `TrafficLights` by entering the following code:

```python
from gpiozero import Button, TrafficLights
```

--- /task ---

--- task ---

Set up your traffic lights using the GPIO Zero interface:

```python
lights = TrafficLights(25, 8, 7)
```

The `TrafficLights` interface takes three GPIO pin numbers, one for each pin: red, amber, and green (in that order).

--- /task ---

--- task ---

Set up your button using the pin number it is connected to on the Raspberry Pi:

```python
button = Button(21)
```

--- /task ---

--- task ---

Now add a `while` loop to control the `TrafficLights` object:

```python
while True:
    button.wait_for_press()
    lights.on()
    button.wait_for_release()
    lights.off()
```

--- /task ---

--- task ---

Press **Run** in Thonny, then press the button to watch your lights come on!

--- /task ---

The `TrafficLights` interface is very similar to that of an individual LED: you can use `on`, `off`, and `blink`, all of which control all three lights at once.

--- task ---

Try the `blink` example:

```python
while True:
    lights.blink()
    button.wait_for_press()
    lights.off()
    button.wait_for_release()
```

--- /task ---

--- task ---

Press **Run** in Thonny, then press the button to watch your lights blink!

--- /task ---


### Add a buzzer

Now you'll add your buzzer to make some noise.

--- task ---

Add `Buzzer` to the `from gpiozero import...` line:

```python
from gpiozero import Button, TrafficLights, Buzzer
```

--- /task ---

--- task ---

Add a line below your creation of `button` and `lights` to add a `Buzzer` object:

```python
buzzer = Buzzer(15)
```

--- /task ---

--- task ---

`Buzzer` works exactly like `LED`, so try adding a `buzzer.on()` and `buzzer.off()` into your loop:

```python
while True:
    lights.on()
    buzzer.off()
    button.wait_for_press()
    lights.off()
    buzzer.on()
    button.wait_for_release()
```

--- /task ---

--- task ---

`Buzzer` has a `beep()` method which works like `LED`'s `blink`. 

Try it out:

```python
while True:
    lights.blink()
    buzzer.beep()
    button.wait_for_press()
    lights.off()
    buzzer.off()
    button.wait_for_release()
```

--- /task ---


### Traffic lights sequence

As well as controlling the whole set of lights together, you can also control each LED individually. With traffic light LEDs, a button and a buzzer, you can create your own traffic lights sequence, complete with pedestrian crossing!

--- task ---

At the top of your file, below `from gpiozero import...`, add a line to import the `sleep` function:

```python
from time import sleep
```

--- /task ---


--- task ---

Modify your loop to perform an automated sequence of LEDs being lit:

```python
while True:
    lights.green.on()
    sleep(1)
    lights.amber.on()
    sleep(1)
    lights.red.on()
    sleep(1)
    lights.off()
```

--- /task ---

--- task ---

Add a `wait_for_press` so that pressing the button initiates the sequence:

```python
while True:
    button.wait_for_press()
    lights.green.on()
    sleep(1)
    lights.amber.on()
    sleep(1)
    lights.red.on()
    sleep(1)
    lights.off()
```

--- /task ---

--- task ---

Try some more sequences of your own.

--- /task ---

