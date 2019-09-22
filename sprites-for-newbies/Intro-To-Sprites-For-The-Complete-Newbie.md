# Intro to Sprites for the Complete Newbie #
For VERA 0.8

You might've heard of the Commander 16 Project where a bunch of people are trying to build a modern retro computer in the style of the Commodore 64 of the 80's. They are porting over some of the C64's components like its BASIC language, while adding new ones like the new VERA video component.

**VERA** stands for **V**ideo **E**nhanced **R**etro **A**dapter, and being "Enhanced" is a good thing because an early 80's video chip is not going to cut it in 2019. Let's take a look look at the sprites functionality of VERA today.

The Commander 16 project is still being worked on, and it's the same thing for VERA. Right now, VERA is at version 0.8, so you know it's close to being complete, but not quite there.

To follow along with this article, you'll need to run the Commander 16 Emulator. For instructions how, see here.

## What is a sprite? ##

A sprite is a piece of graphic that you can move anywhere on the screen, and it can be placed in front of, or behind other graphics, such as a screen of text, or some other backgrounds.

Here's a sprite of a balloon floating across the X16 screen.

![Sprite demo](./assets/baloon.gif)

## Awesome! Let's do some sprites! ##

If you look at the [VERA Programmer's Reference](https://github.com/commanderx16/x16-docs/blob/master/VERA%20Programmer's%20Reference.md), under the  [Internal Address Space](https://github.com/commanderx16/x16-docs/blob/master/VERA%20Programmer's%20Reference.md#internal-address-space) section, you might notice that these address ranges have something to do with sprites:

| Address Range   | Description       |
|-----------------|-------------------|
| $F4000 - $F400F | Sprite Registers  |
| $F5000 - $F53FF | Sprite Attributes |

### Dollar-F-4-thousand? ###

Close! It's actually pronounced Hex-F-4-thousand. Hexadecimal is another way to write the numbers you've known all these years. Instead of counting with 10 digits, hexadecimal counts with 16 digits. So, it's 0-1-2-3-4-5-6-7-8-9-A-B-C-D-E-F. It's a bit closer to how computers store data, so programmers like this system.

Let's break down $F4000 to see what it's all about:

|Base   |Digit 4|Digit 3|Digit 2|Digit 1|Digit 0|
|:-----:|:-----:|:-----:|:-----:|:-----:|:-----:|
|$      |F      |4      |0      |0      |0      |

The "$" tells you that the number is a hex. If you have a programmer's calculator on your computer, you can easily find out that $F4000 is the same as 999,424. You might agree that $F4000 is easier to remember than 999,424.

<img src="./assets/calc.png" width="50%">

### Sprite Registers ###
<table>
    <thead>
        <tr>
            <th>Register</th>
            <th>Name</th>
            <th>Bit 7</th>
            <th>Bit 6</th>
            <th>Bit 5</th>
            <th>Bit 4</th>
            <th>Bit 3</th>
            <th>Bit 2</th>
            <th>Bit 1</th>
            <th>Bit 0</th>
        </tr>
    </thead>
    <tbod>
        <tr>
            <td>0</td>
            <td>SPR_CTRL</td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td>EN</td>
        </tr>
        <tr>
            <td>1</td>
            <td>SPR_COLLISION</td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td colspan="4" align="center">Collision Mask</td>
        </tr>
    </tbody>
</table>

## How to store numbers in bits & bytes ##
