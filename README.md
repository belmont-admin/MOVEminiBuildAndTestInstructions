```package
neopixel=github:microsoft/pxt-neopixel#v0.6.12
```

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

Use a small Phillips screwdriver to screw the five M3 machine screws through the micro:bit and spacer, into the nuts mounted on the PCB.

![Boards connected](https://github.com/belmont-admin/MOVEminiBuildAndTestInstructions/raw/master/docs/images/2-Boards.png)

### ~hint

#### Don't forget the spacer
Make sure you put the spacer between the two boards otherwise they won't connect nicely.

### ~

## Step 2 - Add the batteries

Make sure the switch on the Servo:Lite board is in the **OFF** position and then install the three batteries.

## Step 3 - Test the lights

Use a ``||variables:set strip to||`` ``||neopixel:Nexopixel at Pin||`` block to create a variable ``||variables:strip||`` which tells the @boardname@ that you have have a strip of 5 neopixels connected to Pin 0.

```blocks
let strip: neopixel.Strip = null
strip = neopixel.create(DigitalPin.P0, 5, NeoPixelMode.RGB)
```

### ~hint

#### Look in the **Neopixel** section
Although you are creating a variable you will find the block you need in the **Neopixel** section and not in the *Variables* section
### ~

Add a Neopixel ``||neopixel:show colour||`` block to set the strip LEDs to red when button ``||A||`` is pressed

```blocks
input.onButtonPressed(Button.A, function () {
    strip.showColor(neopixel.colors(NeoPixelColors.Red))
})
let strip: neopixel.Strip = null
strip = neopixel.create(DigitalPin.P0, 5, NeoPixelMode.RGB)
```

Now add a Neopixel ``||neopixel:clear||`` and ``||neopixel:show||`` blocks to turn the LEDs off when button ``||B||`` is pressed.

```blocks
input.onButtonPressed(Button.A, function () {
    strip.showColor(neopixel.colors(NeoPixelColors.Red))
})
input.onButtonPressed(Button.B, function () {
    strip.clear()
    strip.show()
})
let strip: neopixel.Strip = null
strip = neopixel.create(DigitalPin.P0, 5, NeoPixelMode.RGB)

```

Download your code to the @boardname@, turn the switch on the Servo:Lite board to the **On** position and test that your LEDs work.

## Step 4 - Connect the wheels to the servos

For this step you need to push the wheels onto the servos so you can test them. You'll then need to connect the servos to the Servo:Lite board. Be careful and don't force anything too hard.

![wheels](https://github.com/belmont-admin/MOVEminiBuildAndTestInstructions/raw/master/docs/images/4-PartsWheels.png)

Once the wheels are on the spindle of the servos you can connect them to the Servo:Lite board.

### ~hint

#### Connect the cable the right way round
The 3-pin connector on the end of the wire from the servo can fit both ways onto the pins on the Servo:Lite board. You must connect the cable the correct way round which is with the brown wire nearest the neopixels at the top of the Servo:Lite board.

![wheels connect](https://github.com/belmont-admin/MOVEminiBuildAndTestInstructions/raw/master/docs/images/6-ServoConnecting.png)

### ~

Congratulations you should now have assembled the core parts of your robot buggy!

![buggy assembled](https://github.com/belmont-admin/MOVEminiBuildAndTestInstructions/raw/master/docs/images/7-FinalAssembled.png)

## Step 5 - Testing the servo motors

The motors are controlled using the ``||Pins:servo write pin PIN to NUMBER||`` block

The number you write to the pin determines the speed of the motor.

![speeds](https://github.com/belmont-admin/MOVEminiBuildAndTestInstructions/raw/master/docs/images/5-SpeedControl.png)

-
* **180** means full speed anticlockwise
* **0** means full speed clockwise
* **90** means stop

Change your code so that when you press button ``||A||`` both motors spin full speed anticlockwise

Remember which pins control what.

![Pin Outs](https://github.com/belmont-admin/MOVEminiBuildAndTestInstructions/raw/master/docs/images/0-PinOuts.png)

```blocks
input.onButtonPressed(Button.A, function () {
    pins.servoWritePin(AnalogPin.P1, 180)
    pins.servoWritePin(AnalogPin.P2, 180)
})
```
Now add code so that when you press the ``||B||`` button the motors stop.

You will probably find that the motors do not stop completely. If this happens then the servos need to be **trimmed**. This means adjusting a small screw on the servo. Ask Alice or Elise to give you a small screwdriver and help you with this

Congratulations! You have now assembled and tested the key parts of your robot buggy.

## Step 6 - Try some other things

Add code so that when you press the ``||A+B||`` buttons the wheels spin the other way.

See if you can change the the colour of each neopixel separately. This picture shows you the number of each neopixel that you will need to use:

![leds](https://github.com/belmont-admin/MOVEminiBuildAndTestInstructions/raw/master/docs/images/3-PixelArrayAddressing.png)

### ~hint

#### Note the numbering
The five neopixels are number 0,1,2,3 and 4. It's not unusual in computing for numbering to start at 0 rather than 1.

### ~

```blocks
let strip = neopixel.create(DigitalPin.P0, 5, NeoPixelMode.RGB)
basic.forever(function () {
    strip.setPixelColor(0, neopixel.colors(NeoPixelColors.Red))
    strip.setPixelColor(1, neopixel.colors(NeoPixelColors.Green))
    strip.setPixelColor(2, neopixel.colors(NeoPixelColors.Purple))
    strip.setPixelColor(3, neopixel.colors(NeoPixelColors.Blue))
    strip.setPixelColor(4, neopixel.colors(NeoPixelColors.Orange))
    strip.show()
    basic.pause(2000)
    strip.clear()
    strip.show()
    basic.pause(2000)
})

```

