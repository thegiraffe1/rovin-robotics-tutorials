# Bop It 

## {Introduction @unplugged}

Let's code a Bop-It like game!
![Bop It GIF](https://raw.githubusercontent.com/thegiraffe1/rovin-robotics-tutorials/main/bop-it.gif)

## {Step 1}

Let's create a variable to keep track of which button we should press! Go to ``||variables:Variables||`` and Make a Variable and name it **state**. 
Now, add the ``||variables:set state to 0||`` block into ``||basic:on start||``.

## {Step 2}

Instead of using the icons inside the loop right now, we want displays that correspond to an action. For example, you could use ⇽ for button A, ⇾ for button B, "S" for shake, and "F" for flip! 

Whatever you decide, switch out each code block within the ``|basic:if then|`` with your own. Remember, you can use an existing ``||basic:show icon||``, show a letter with ``||basic:show string||``, or draw out your own with ``||basic:show leds||``.

## {Step 3}

Instead of responding to buttons, the micro:bit should decide itself which image to show! We can use the variable ``|variable:state|`` to check which part of the ``|basic:if then||`` should be run. 

There are 4 show LED options and 4 actions, so let's say ``|variable:state|`` will be between 1 and 4. For the first if block, we can check if ``|variable:state|`` is equal to 0. 

Grab the ``||logic:equals||`` block and replace the ``|logic:button A is pressed|`` in the ``|basic:if then|`` block. Now, drag a ``||variable:state||`` into the first slot of ``||logic:equals||``. Now it asks each time: does ``|variable:state|`` equal 0?

## {Step 4}

Let's fill the other cases! Create three more ``||logic:equals||`` blocks and put ``|variable:state|``s into it. What do we want to compare it to? Remember, ``|variable:state|`` will be between 1 and 4. 

## {Step 5}

Let's check if everything works! We can manually go through the cases. In each body of the ``|basic:if then|`` block, add a ``||logic:set state to||`` block that goes to the next state. For example, when ``|variable:state|`` is 1, set it to 2. When it is 2, set it to 3. When it is 5 though, set it back to 1. 

Once you've done this, hit ``||Download||`` and run!


```template
basic.showIcon(IconNames.Happy)

basic.forever(function () {
    if (input.buttonIsPressed(Button.A)) {
        basic.showIcon(IconNames.Heart)
    } else if (input.buttonIsPressed(Button.B)) {
        basic.showIcon(IconNames.SmallHeart)
    } else if (input.isGesture(Gesture.Shake)) {
        basic.showIcon(IconNames.Yes)
    } else if (input.isGesture(Gesture.LogoDown)) {
        basic.showIcon(IconNames.No)
    } else {
        basic.clearScreen()
    }
})
```

```ghost
function checkAction (num: number) {
    music.play(music.stringPlayable("F A C5 C5 - A C5 C5 ", 300), music.PlaybackMode.UntilDone)
}

let state = 0
```