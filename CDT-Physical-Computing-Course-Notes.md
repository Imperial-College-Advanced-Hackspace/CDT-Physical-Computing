# CDT-Physical-Computing

## Find me at http://bit.ly/2FHvwRo

<p align="center">
    <img src="images/ICAHLOGO.jpg" alt="ICAHLOGO" width="800">
</p>

# Introduction

Welcome to this tutorial about the Raspberry Pi microcomputer and its amazing capabilities. This tutorial intends to offer you:

1. An overview of Raspberry Pi – one of the most popular microcomputers in use today.
2. A brief introduction to the Python programming language.
3. An understanding of Raspberry Pi's physical pins, which we can use to make it talk to all sorts of electronics – from within our Python programs!

It may also be useful as a reference during our hackathon.

**One plea**: If you are done earlier than your neighbour, please help us out by offering your help to them. Explaining something is a sure-fire way to really understand it yourself!

# An Overview of the Raspberry Pi (RPi)

## What is the Raspberry Pi?

Raspberry Pi is a small computer the size of a credit card that you can plug into a monitor, keyboard and mouse. You can use it in the same way as you would use your desktop PC or laptop. You can generate spreadsheets, do word processing, browse the internet, and play games. It also plays high-definition video.

However, what will make it interesting for us is its capability for use in electronics projects! The main aim of the Raspberry Pi is to teach anyone how to use programming and electronics to realise their ideas. Raspberry Pi comes with a free Linux operating system that runs from an SD card, and it is powered by a USB phone charger.

<p align="center">
    <img src="images/pi3card.png" alt="The Raspberry Pi (version 3)" width="400">
    <figcaption align="center">The Raspberry Pi (version 3)</figcaption>
</p>

## Models of Raspberry Pi

Since its original launch in 2012 there have been a number of different models with the most recent model having a quad core processor runnning at 1.4GHz and with 1GB of RAM.

<p align="center">
    <img src="images/rpimodels.PNG" alt="The Raspberry Pi (version 3)" width="800">
</p>
<p align="center">
    <img src="images/rpimodelscompute.PNG" alt="The Raspberry Pi (version 3)" width="800">
    <figcaption align="center">Different Raspberry Pi models through the years</figcaption>
</p>

We will be working with the RPi 3 Model B which is based around a 1.2 GHz 64-bit quad-core ARM Cortex-A53 processor, has 1GB of RAM, while the smaller and cheaper Zero W is based on a 1 GHz single-core ARM1176JZF-S processor with 512GB RAM. Both have 802.11n Wireless and Bluetooth 4.1 included on the chip. Look at them – all of this is included in those black chips soldered onto the boards! That's also why we call these little wonders "System on a Chip" – the entire computer system resides in silicon.

## Physical layout of Raspberry Pi

<p align="center">
    <img src="images/RPI3Blayout.jpeg" alt="The Raspberry Pi (version 3)" width="600">
    <figcaption align="center">Raspberry Pi Layout</figcaption>
</p>

The above picture shows a Raspberry Pi 3. On the right-hand side, you have four **USB ports** and one **Ethernet** port. Next to the USB ports, there is a **USB/Ethernet Controller**, which translates data between the ports and the main processor, because the processor itself doesn't understand the USB or Ethernet protocol. At the top, you can find the **General Purpose Input/Output (GPIO) pins** (40 of them to be precise). Down the bottom middle is the **CSI (Camera Serial Interface) connector**, which allows you to connect mobile-phone-style cameras directly to the Pi. Of course, you also have the option to connect a webcam via USB. At the right-hand side, you can find a **DSI (Display Serial Interface) connector** that you can use to connect an LCD screen. At the bottom, you can find the **HDMI port**, which allows you to connect the Pi straight into a monitor. Next to this port, you can see the **USB power connector** and also an **audio port**. The back side of the Pi houses a micro SD card slot for the SD card containing the operating system and user data – just like a classical hard disk.

## Important Note

Before we continue, please be aware of the following limitations when using your Raspberry Pi.

* Always make sure you supply only 5V to the RPi.
* Unlike Arduino, RPi does not have over-voltage protection on the board (yet), so be careful when making GPIO connections.
* Never connect more than a potential difference of 3.3V to the GPIO pins (for example, when using sensors to feed data into the Pi).
* Never demand that any GPIO pin source or sink more than 16mA.
* Pins can only supply a maximum current of 50mA.

During this workshop, if you are unsure about connecting something new to your Raspberry Pi (particularly anything feeding a voltage or a current into it), do come and ask one of us mentors first – it might prevent your board from frying! Let us now consider what we _can_ do with those pins!

## General Purpose I/O Pins (GPIO)

Your Raspberry Pi is more than just a small computer; it is a hardware prototyping tool! The RPi has **bi-directional I/O pins**, which you can use to drive LEDs, spin motors, or read button presses. Using these pins requires a bit or programming. While you can use a [variety of programming languages](http://elinux.org/RPi_Low-level_peripherals#GPIO_Code_examples) to \"do\" GPIO, we will use a reliable, easy-to-use language throughout this hackathon: **Python**.

###  GPIO Pinout

As we saw above, the GPIO is arranged as a header of 40 electrical pins, which makes it easy to connect it with an external circuit, using jumper wires.

<p align="center">
    <img src="images/rpi_new_pin.jpg" alt="The Raspberry Pi (version 3)" width="300">
    <figcaption align="center">Raspberry Pi GPIO Orientation</figcaption>
</p>

<p align="center">
    <img src="images/RPi_pin_layout.svg" alt="The Raspberry Pi (version 3)" width="200">
    <figcaption align="center">Raspberry Pi GPIO Layout</figcaption>
</p>

The image also shows the additional data protocols that can be accessed through some of the GPIO pins: [Serial (UART)](https://learn.sparkfun.com/tutorials/serial-communication), [I2C](https://learn.sparkfun.com/tutorials/i2c), [SPI](https://learn.sparkfun.com/tutorials/serial-peripheral-interface-spi), Pulse width modulation ([PWM](https://learn.sparkfun.com/tutorials/pulse-width-modulation). We will actually use the I2C protocol to control an external circuit board for DC motors later.

# The tools of the trade - the Linux terminal, a code editor and SSH

But how about (a) writing, and (b) executing Python programs on the Rasberry Pi?

For writing programs, we suggest using **Geany**, which is one of the pre-installed code editors on your Raspberry Pi. It has the handy feature that it highlights (i.e., colour-annotates) our programs as we write them, which helps a lot with their readability.

You find Geany in the Programming menu, as shown in the following picture.

<p align="center">
    <img src="images/Geany_menu_item.png" alt="Geany menue item" width="800">
    <figcaption align="center">Opening the Geany script editor</figcaption>
</p>

The user interface is rather self-explanatory, with commands like CTRL+S (save), CTRL+O (open a file) etc. working as expected. It looks like shown below. Note that the program text has been coloured automatically.

<p align="center">
    <img src="images/Geany_window.png" alt="Geany window" width="800">
    <figcaption align="center">The Geany user interface</figcaption>
</p>

Alternatively you can create the programs on your own laptop and copy them over to the raspberry pi over SSH (Secure Socket Shell). For our sessions we will use repl.it which is an online IDE that can interpret and compile your code. Using this we do not have to worry about what operating system we are on and installing any new software. Simply write the code online, download it and copy it across as shown below.

But how to actually run the program, so the computer can do what we ask it to do? That's where the Linux terminal comes in handy. Look again at the main menu bar in the Figure above. The terminal is the black symbol with <kbd>**>\_**</kbd> in it, at the top of the screen. Once you've clicked on it, the below window appears.

<p align="center">
    <img src="images/Terminal_window.png" alt="The Linux terminal" width="600">
    <figcaption align="center">The Linux terminal</figcaption>
</p>

We will show you how you can run a program from within the Terminal. The most important Terminal commands are listed in the table below.

| Command       | Effect     | 
| ------------- |:-------------| 
| ```ls``` | List the contents of the current folder |
| ```cd``` _folder_ | **C**hange **d**irectory into _folder_ |
| ```cd ..``` | Change into the parent folder of the current folder |
| ```cd``` | ```cd``` without argument changes back to the user's home folder (/home/pi) |
| ```pwd``` | **P**resent **w**orking **d**irectory. This prints out the location of the current folder. |
| ```python3``` _program.py_ | Run the program called _program.py_ in Python 3 |

Hint: You can use tab completion. For example, when typing ```cd```+<kbd>Tab</kbd>, the Terminal automatically lists all possible folders that are available for changing into.

Long story short - the Terminal is much like a text-based file explorer, bolted together with a powerful general "command centre" for your computer. You can also start the usual programs from within the terminal. Just type ```chromium```+<kbd>Enter</kbd>.

## SSH: Secure Socket Shell

Raspberry Pis are great for electronics projects - they're quick and easy to use and can be set up to work headless i.e. they can work without a screen. Although this is a little more difficult to work with it makes it great when we want to update code on the Raspberry Pi while it is buried in the middle of our projects. To access our pi without a screen we can use SSH, which forms a secure connection between your device and the pi and provides you access to the command line on the Raspberry Pi.

Normally you can connect to a pi over SSH that is on the same network, for example at home if your pi is connected to your wifi and so is your laptop, you can connect to it over SSH by simply typing ssh pi@PI_IP_ADDRESS in a terminal (Linux/Mac) or using a program like PuTTy (windows).

In our case there are some further difficulties as we do not know the IP address of the pi on the Imperial-WPA network hence we are using the Raspberry Pi as a Wireless Access Point (WAP). This allows us to connect directly to the raspberry pi like we connect to a wifi network. Each of you will be given a pi with a number on top, dictating the wifi SSID to connect to.

Now connect up the 5V power adapter to the pi and turn it on. A red light should come on and a flashing green light. After roughly 20 seconds the Raspberry pi will have completed booting. Now see on your laptops wifi connection - has the raspberry pi SSID shown up? For example for the Raspberry Pi labelled 01 there should be a wifi connection called ```H2Pi01``` that you can connect to. Try connecting to this connection. The password is ```Horizons2```.

If you can connect to it you should be able to also SSH into the raspberry pi now. Try the following instructions:

### Linux/Mac:

Open a terminal and type in ```SSH pi@192.168.4.1```. If it asks you if you want to continue connecting then please type ```yes```+<kbd>Enter</kbd>. If it asks you for a password then try the default rapsberry pi password ```raspberry```.

### Windows:

Download PuTTy, an SSH and telnet client [here](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html). After you have downloaded and installed PuTTy, try running it and you should be met with a screen as below:

<p align="center">
    <img src="images/PuTTy.png" alt="PuTTy: an SSH and telnet client" width="600">
    <figcaption align="center">PuTTy: an SSH and telnet client</figcaption>
</p>

On the left hand bar select Session and fill in the details as follows: 

```
Hostname (or ip address):192.168.4.1
Port:22
Connection Type:SSH
```

You can even save this configuration so you can pull it up next time instead of typing it all out again. Now click ```Open``` and you should be met with a black terminal screen and you may get a popup asking if you are sure to connect. Click Yes. On the black terminal screen you will get a prompt for the login details:

```
login as: pi
password: raspberry
```

If all goes well you should be met with the screen below:

<p align="center">
    <img src="images/successful_connection.png" alt="Successfully SSH raspberry pi" width="600">
    <figcaption align="center">Successfully SSH raspberry pi</figcaption>
</p>

## Working with files on the Pi

As you know we do not have a screen connected to the Raspberry Pi right now, which may confuse some of you for the next bit. Lets say we wanted to write some code and run it on the Pi. How would we do this? There are two ways we can use here, either we write the file on our own laptops in a text editor and copy it over, or we write it directly on the pi in the terminal. 

### Copying a file over to the Raspberry Pi

As some of you may find it is nicer to work within a known code editor that you are comfortable with. Once you have made this file on your laptop you can then copy this over to the Raspberry Pi and run it. So lets try this, create a simple text file called test_file.txt on the Desktop on your laptop.

Now lets copy your file over to the Raspberry Pi. We can do this using SCP (Secure File Copy). Don't forget to connet to your RPi network again before trying the next steps.

If you are using Mac/Linux then you do not require any extra software. Simply open a terminal and change directory to the Desktop and type:

```scp test_file.txt pi@192.168.4.1:/home/pi/Desktop```

If you are using Windows then you will need the program PuTTy which we mentioned in the previous lesson. You can download it [here](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html). Download the MSI('Windows Installer') and install it.

Once you have installed PuTTy you can open the command prompt in Windows and change directory to the Desktop. Now use the pscp command to transfer the file.

```pscp -scp test_file.txt pi@192.168.4.1:/home/pi/Desktop```

Now if you ssh into your Raspberry Pi and list the files in the Desktop folder you will see your text file has been copied across!

### Using a file editor on the Raspberry Pi

If you wanted you could also create and edit a file directly on the RPi. Lets try this. First SSH into the RPi:

```ssh pi@192.168.4.1```

Then change directory to the Desktop folder. Now we are going to use one of the built in file editors for Linux systems called Nano. It is a very nice and easy terminal text editor. So to run it type:

```nano test_file.txt```

This will open a text editor in your terminal as shown below:

<p align="center">
    <img src="images/nano_terminal.PNG" alt="Nano in the terminal" width="800">
    <figcaption align="center">Nano in the terminal</figcaption>
</p>

Note that within this text editor you cannot just click where you want to go but have to move there using the keypad on your keyboard. Then you can type whatever you need so lets try typing ```Hello World!``` at the top of the file and to exit you click <kbd>CTRL</kbd>+<kbd>X</kbd> on your keyboard. Click <kbd>y</kbd> and <kbd>Enter</kbd> to save it under the same file name.

Now we know what a Raspberry Pi is and how to copy files to it but how do we run code on it? And how do we write this code? For our programming we will use a nice, easy to use language called Python!

# Basic Python: Variables, Operators, Data Types

Programming languages hold data in variables. Just like in maths, variables in Python are a convenient way to refer to a quantity through a memorable name.

```Python
number_of_hands = 2 # Hold the value 2 in a variable called "number_of_hands"
fingers_per_hand = 5 # Hold the value 3 in a variable called "fingers_per_hand"
number_of_fingers = number_of_hands * fingers_per_hand # What value will this be?
```

Variable names must start with a letter and should only contain letters, numbers and underscores.

In this example, we used hashtags to mark everything behind them as **comments**, which are not executed.

Programming languages use different **data types** for different types of data. It's horses for courses with this, and unsurprisingly Python supports text, integers, floating point and Boolean data, to name a few.

For example:

```python
x  = 1
some_text = "Hello World!"
some_boolean = False
```

We can perform mathematical calculations in Python using the basic operators `+`, `-`, `*`, `/`, `**`, `%`.

```python
4 + 5
4 - 3
2 * 3
3 / 4
2 ** 3 # Returns 2 to the power of 3
10 % 7 # Returns the remainder of a division
```

In Python, the [standard order of operations](https://en.wikibooks.org/wiki/Python_Programming/Basic_Math) is from left to right, and respects the mathematical precedence of operations (memorised by many as PEMDAS):

| Name        | Syntax     | Description  |
| ------------- |:-------------:| :-----|
| **P**arentheses     | ( ... ) | Happening before operating on anything else.|
| **E**xponents     | **  |  Exponents are evaluated before multiplication and division. |
| **M**ultiplication and **D**ivision | * / | |
| **A**ddition and **S**ubtraction | + -  | |

Let's try it:

```python
3 / 4 * 5  # First division and then multiplication
6 + 7 * 9
2 ** 8
10 % 7 # Remainder of a division
```

The following table lists Python's comparison operators. Operations involving these return the Boolean values `True` or `False`, depending on whether the statement is true or not.

| Name        | Syntax     |
| :-------------: |:-------------|
| < | Less than|
| > | Greater than|
| <=| Less than or equal to|
|>=	| Greater than or equal to|
|==	| Equal to|
|!=	| Not equal to|

You can combine logic statements using the keywords `and`, `or` and `not`. What will the following statements return?

```python
2 == 3
3 == 3
2 < 3
True == (False != True)
"Asterix" == "Obelix" or not("Idefix" == "Idefix")
```

There are more operators, which you can read about [here](https://www.tutorialspoint.com/python/python_basic_operators.htm).

## Strings, Lists and Indexing

The data stored in memory can be of different types; Python has five basic ones: **Numbers** and **Strings**, which we have encountered above, and also **List**, which we will touch upon below. (We won't have time to cover the [**Tuple**](https://www.tutorialspoint.com/python/python_tuples.htm) and [**Dictionary**](https://www.tutorialspoint.com/python/python_dictionary.htm) types.)

Re-using the above:

```python
type(number_of_hands) # Number
type(fingers_per_hand)
type(some_text) # String
```

**Strings** in Python are a set of characters grouped together in quotation marks. Python allows either a pair of single or double quotes.

**Lists** are the most versatile data types in Python. A list contains items separated by commas and enclosed in square brackets `[ ... ]`. In Python, all the items belonging to a list can be of different data type.

The values stored in a list can be accessed using the slice operator (`[]` and `[:]`) with indexes **starting at 0 at the beginning of the list**. That's a popular stumbling block, so beware!

The plus sign is the list concatenation operator, and the asterisk (`*`) is the repetition operator.

```python
examplelist = [ 'abc', 12 , 2.23, 'john', 70.2 ]
tinylist = [123, 'john']

my_name = "John Doe"
my_job = "technician"

print(examplelist)            # Prints complete list
print(examplelist[0])         # Prints first element of the list
print(examplelist[1:3])       # Prints elements starting from 2nd till 3rd
print(examplelist[2:])        # Prints elements starting from 3rd element
print(examplelist[-1])        # Negative indexing: Prints the last element of the list
print(tinylist * 2)    # Prints list two times
print(examplelist + tinylist) # Prints concatenated lists

print(my_name[0])      # Strings behave very similarly to lists
print(my_name + my_job)# String concatenation
```

Finally, you can use the `len(...)` function to find the length of a list or string.

## Control flow

We have so far seen many small bits of software that fulfil one specific task at a time (like assigning a value to a variable, or accepting user input). In order to tackle more complex tasks, we need to combine many of these items into one larger computer program. Think of programs as cooking recipes: They are a sequence of statements (i.e., lines of code), to be executed by a very quick and accurate, but also adhere-to-the-letter type of cook (your Raspberry Pi).

As programmers, we set up “paths” for the program to follow. Can you tell the output of the program?

<p align="center">
<img src="images/Flow1.png" alt="pin" width="90">
</p>

## Repeating code: Loops

Often, we need an action to be repeated. One way to achieve this is to use a `while` loop:

```python
count = 0
while (count < 9):
    print 'The count is:', count
    count = count + 1
print "Goodbye!"
```

Two important points to remember:
1. **Code blocks that are executed inside an `if`/`elif`/`else` statement are indented with a tab. This is Python's way to group code into blocks.**
2. **These code blocks start after a colon and end when the indentation stops.**

To run through a list of things, we can use a `for` loop:

```python
my_numbers = [1,2,3,4,5]
for number in my_numbers:
    print(number ** 2)
```

# Physical Computing and the gpiozero library

Ultimately, we want you to control a physical contraption with your Raspberry Pi. For this, we'll use the General Purpose Input/Output (GPIO) pins on the side of your Pi. Their layout is shown below. Don't worry too much about it all for now, we will show you how to connect things up. Just one thing to remember: **Never connect a 5V pin directly to any other pin of the Raspberry Pi, particularly the Ground pin!**

<p align="center">
    <img src="images/RPi_pin_layout.svg" alt="pin" width="200">
    <figcaption align="center">Raspberry Pi pin layout</figcaption>
</p>

## Working with libraries

You've seen the `import` statement in the last session, where we used `import numpy as np` and later `np.pi` to access the value of the mathematical constant &pi;.

The whole point is to avoid "re-inventing the wheel" by using existing software inside our programs. We do this by importing **software libraries**.

Here's an example for how powerful this idea is. Imagine you want to retrieve the raw HTML content from a website. Instead of manually coding everything up from scratch, we can do the following:

```python
import requests
r = requests.get('http://example.com') # Using everyone's favourite test domain!
print(r.content)
```

A whopping 3 lines of code to traverse the network stack, perform a HTTP GET request, await a response, save it in a variable called `r` and display it!

Things contained in libraries can be retrieved by using the dot operator `.`, such as in `requests.get`.

## Using a breadboard

An electronics breadboard are great units for prototyping or making quick temporary circuits and they generally require no soldering. If you are not sure how a certain circuit will react, its best to prototype it out and usually this is done using a breadboard.

Some of you who have previously worked with electronics may have already seen a breadboard. They come in different sizes and configurations but generally are very similar. A breadboard will always have a DIP ravine in the centre of the breadboard. This is so that you can place IC chips in the middle with pins on either side. Also your breadboard may have a set of rails running along the top and bottom. Lets have a look at a small breadboard:

<p align="center">
    <img src="images/medium_breadboard.jpg" alt="Medium Breadboard" width="400">
    <figcaption align="center">Medium sized breadboard with exposed pins</figcaption>
</p>

So on the left is the top side of the board where you would place your components and on the right is the bottom side of the board. Usually a breadboard has some backing on it so you cannot see the exposed metal components but we have peeled it off here so you can see the inner workings of the breadboard. Now the metal lines you can see are actually rows of pins as shown in the image below and each of these metal rows have clips at the top that are just under the plastic surface of the breadboard. When you plug in a wire or a leg of a component it is held in place by these metal clips.

<p align="center">
    <img src="images/breadboard_pins.JPG" alt="Breadboard metal pins" width="300">
    <figcaption align="center">Metal pins inside the breadboard</figcaption>
</p>

As you can see you have vertical rows and horizontal rows of these metal clips. The vertical rows are used for common rails such as 5V and GND. Note that the vertical rows running on both sides are not connected, traditionally on simple circuits you would run a wire from each side bridging these to allow for rails on either side of the breadboard making it easier when building your circuits. The horizontal rows are for placing your components and allowing for multiple connections off one pin. Note the horizontal rows are not connected in the middle. This is so that you can place IC chips in the middle allowing for half the pins to be on either side and not be bridged across.

<p align="center">
    <img src="images/breadboard_bridge.jpg" alt="Bridged rails" width="500">
</p>
<p align="center">
    <img src="images/breadboard_ravine.jpg" alt="Breadboard DIP ravine" width="500"
</p>
<p align="center">
  <figcaption align="center">Top: Bridging rails on either side of breadboard. Bottom: DIP ravine to place IC</figcaption>
</p>

## Using the gpiozero library

The [gpiozero library](https://gpiozero.readthedocs.io/en/stable/) enables us to control the GPIO pins on our Pi. We start off with `import gpiozero`. The gpiozero library provides us with a lot functionality to interface with the GPIO pins and provides us with ready to use objects for LEDs, sensors and actuators.

### Blinking an LED

Connect an LED via a resistor to the Ground (GND) and GPIO pin 17 (GP17). Note that the shorter wire of the LED needs to connect to ground.

<p align="center">
    <img src="images/gpiozero_led.png" alt="Connecting an LED" width="800">
    <figcaption align="center">Connecting an LED to the Pi</figcaption>
</p>

To keep everything a little organised lets create a directory where we can keep all our code:

```
cd /home/pi/
mkdir Horizons
cd Horizons
```

Run:

```python
import gpiozero
import time

red = gpiozero.LED(17)

while True:
    red.on()
    time.sleep(1)
    red.off()
    time.sleep(1)
```

Note how we also imported the `time` library to allow the program to sleep for one second.

## Conditional statements

Conditional statements allow the program to react to new information _whilst it is running_ ("at runtime").

We use the `if (...):`-`elif (...):`-`else:` construct for this scenario. For example &ndash;

```python
weight = input("Please input your weight in kg: ")
height = input("Please input your height in m: ")
# Need to convert strings to actual number types, using the float(...) function
bmi = float(weight) / float(height) ** 2
if (bmi >=16 and bmi < 18.5):
    print("Your BMI looks a bit low (underweight).")
elif (bmi >= 18.5 and bmi < 25):
    print("Your BMI is considered healthy.")
elif (bmi >= 25 and bmi < 30):
    print("Your BMI looks a bit large (overweight).")
else:
    print("According to your BMI, you are severely over- or underweight.")
```

## Functions

Functions enable you to "recycle" blocks of related code at different places in your program.

A function is a block of organised, reusable code that is used to perform a single, related action. Functions provide better modularity for your application and a high degree of code reusing.

```python
# Import a maths library for accessing the value of pi
import numpy as np

# Function that calculates the area of a circle from its radius
def get_area(radius):
    area = np.pi * radius ** 2
    return area

radii = [1, 2, 3, 4, 5, 6]

for radius in radii:
    area = get_area(radius)
    print("The area of a circle of radius " + radius +
          " cm is " + area + " cm^2.")
print "Done."
```

Functions are _defined_ using the `def` keyword, followed by the function name, and any arguments in brackets. Functions return a value using the `return` keyword.

## User input

The following python code accepts user input and stores it in the variable `my_number`.

```python
my_number = ''
my_number = input('Please tell me a number! ')
if (my_number == '42'):
    print('Amazing. You\'re on to something!')
else:
    print('That\'s a lovely number.')
```

**The output of the `input()` function is always a string, even if you input `'42'`. You need to change the type of this variable to `number` first if you want to "do maths" with it later. For this, use the `int()` or `float()` function, for example by calling `my_number = int(my_number)`.**

## When things don't go to plan

When your program has run down a dead end, Python does its best to help you out of it, by printing out a help message into the Terminal.

Consider the following program:

```python
my_number = input("Please input a number: ")
output = my_number / 2
print(output)
```

Saving it as `test.py` and executing (inside the same folder where you saved it!) `python3 test.py`, the following will happen, assuming the user inputs "25" and presses <kbd>Enter</kbd>:

```bash
pi@raspberrypi ~ $ python3 test.py
Please input a number: 25
Traceback (most recent call last):
  File "test.py", line 2, in <module>
    output = my_number / 2
TypeError: unsupported operand type(s) for /: 'str' and 'int'
```

Can someone explain what this "Traceback" is complaining about, and how to correct it?

### Dimming an LED

Keep the same connection, and run the below code. Note how we use the PWMLED object to control the LED. PWM stands for [**P**ulse **W**idth **M**odulation](https://www.arduino.cc/en/Tutorial/PWM), which rapidly blinks the LED and controls its brightness by switching it on and off for different amounts of times.

```python
from gpiozero import PWMLED
from time import sleep

led = PWMLED(17)

while True:
    led.value = 0  # off
    sleep(1)
    led.value = 0.5  # half brightness
    sleep(1)
    led.value = 1  # full brightness
    sleep(1)
```

Note how in this case we have used the syntax `from <library> import <thing>` to import the `PWMLED` and `sleep` functions directly. This allowed us to skip repeatedly writing `time.sleep()` etc.

## Blink 10 times

Write a program that blinks the LED 10 times. Hint: Don't try to write it out 10 times.

## Connecting and setting up the Motor HAT

First of all shutdown the Raspberry Pi safely. To do this SSH into the raspberry pi and in the terminal type:

```
sudo shutdown now
```

Eventually the RPi will shutdown and then you can add the motor hat to the RPi. As you may have noticed the hat has connectors soldered on to it that have very long pins. This is so you can use jumper wires with the hat still connected. In fact if you wanted you could put multiple motor hats on top of each other. Now plug in the RPi and motor hat into the connector on the breadboard.

Now connect the motor wires, one motor to the M1 terminals and one motor to the M2 temrinals. Finally we need to connect the power for the motors. This is on the top left corner of the shield. Connect one black wire from the negative terminal to the GND rail on the breadboard and one red wire from the positive terminal on the shield to the 5V rail on the breadboard. This can all be seen in the image below. Now turn your pi on.

<p align="center"><img src="images/pi_motorshield_wiring.jpg" alt="Motor Shield Wiring" width="800"><figcaption align="center">how to wire up the motor shield</figcaption></p>

To use this HAT you will need to [install the software](https://learn.adafruit.com/adafruit-dc-and-stepper-motor-hat-for-raspberry-pi/installing-software) with it. To do this you will need a usb wifi adapter. Note that the RPi already has wifi but as we have that setup as a Wireless Access Point we have to also use this wifi adapter for access to the internet. To install the software first SSH into the RPi and download the relevant files:

```
cd Horizons
git clone https://github.com/adafruit/Adafruit-Motor-HAT-Python-Library.git
cd Adafruit-Motor-HAT-Python-Library
```
Now we have downloaded the files we can install it easily using the setup command:

```
sudo python setup.py install
```

And thats it! Its installed now and we can start using the library. Try going to the examples folder and runnning the RobotTest.py example. **NOTE: This will move the robot so make sure you hold it up or ensure the robot does not run away from you!**

```
cd examples
python DCTest.py
```

To close the program type <kbd>CTRL</kbd>+<kbd>C</kbd>.

Find out more about the motorHAT and how to use stepper motors go [here](https://learn.adafruit.com/adafruit-dc-and-stepper-motor-hat-for-raspberry-pi/overview).
