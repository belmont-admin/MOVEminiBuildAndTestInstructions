# Assemble and test a MOVE:mini Mk1

## Introduction @unplugged

In this session you will connect the core parts of the MOVE:mini robot buggy and test them.

This is how the pins on the @boardname@ are used.

![Pin Outs](https://github.com/belmont-admin/MOVEminiBuildAndTestInstructions/raw/master/docs/images/0-PinOuts.png)

The ZIP LED is the set of 5 neopixels which are at the top of the servo board.

## Step 1 - Connect the @boardname@ and the :MOVE Servo:Lite board

Here are the parts you need:

![Parts](https://github.com/belmont-admin/MOVEminiBuildAndTestInstructions/raw/master/docs/images/1-Parts.png)

### ~hint

#### Remember to handle the boards carefully

Handle the boards by their edges. If you damage them they won't work and we don't have spares.

### ~

Use a small Phillips screwdriver to screw the five M3 machine
screws through the micro:bit and spacer, into the nuts mounted on the
PCB.

![Boards connected](https://github.com/belmont-admin/MOVEminiBuildAndTestInstructions/raw/master/docs/images/2-Boards.png)

### ~hint

#### Don't forget the spacer
Make sure you put the spacer between the two boards otherwise they won't connect nicely.

### ~

## Step 2 - Add the batteries

Make sure the switch on the Servo:Lite board is in the **OFF** position and then install the three batteries.

### Step 3 - Test the lights

Use a ``||variables:set strip to||`` block to create a variable ``||variables:strip||`` which tells the @boardname@ that you have have a strip of 5 neopixels connected to Pin 0.

![setPixelArray](https://github.com/belmont-admin/MOVEminiBuildAndTestInstructions/raw/master/docs/images/a-setNeopixel.png)

### ~hint

#### Look in the **Neopixel** section
Although you are creating a variable you will find the block you need in the **Neopixel** section and not in the *Variables* section
### ~

Add a Neopixel ``||show colour||`` block to set the strip LEDs to red when button ``||A||`` is pressed

![Red](https://github.com/belmont-admin/MOVEminiBuildAndTestInstructions/raw/master/docs/images/b-setRed.png)

Now add a Neopixel ``||clear||`` and ``||show||`` blocks to turn the LEDs off when button ``||B||`` is pressed.

![Off](https://github.com/belmont-admin/MOVEminiBuildAndTestInstructions/raw/master/docs/images/c-clearStrip.png)

Download your code to the @boardname@, turn the switch on the Servo:Lite board to the **On** position and test that your LEDs work.
