---
title: global
category: 'inner'
tags: [global]
---

<!--50--> 

### HIGH

::i-chinese{sha="eb8425ce4ba48a4bd45fd68a6c970c7fa9d911fdad6a9ce5aa31d8ccd4626d53"}
::
Logic 1 for Arduino compatibility - this is the same as just typing `1`

### Infinity

::i-chinese{sha="4d3108d319014443055eafcb5e64e357b3ef187538e1d7ce400a43f57761d7a4"}
::
Positive Infinity (1/0)

### LOW

::i-chinese{sha="4249523a6f255496fb525febe122ad02fd4a47640e8e5ca00517c8bb7d1e3e90"}
::
Logic 0 for Arduino compatibility - this is the same as just typing `0`

### NaN

::i-chinese{sha="4a89d6f81417c7ae39dccc79b78127cd3d1847784da346190a211ad3480ee9b0"}
::
Not a  Number

### analogRead(pin)

::i-chinese{sha="8ce5596f74fd9b4ecdca63b3a5705efc4966d555b4ad44953053d9e41b4e5308"}
::
Get the analog value of the given pin.
This is different to Arduino which only returns an integer between 0 and 1023.
However only pins connected to an ADC will work (see the datasheet)

> **Note:** if you didn't call `pinMode` beforehand then this function will also reset pin's state to `"analog"`

### analogWrite(pin,value,options)

::i-chinese{sha="e23bd7a05b62a72f7a3912491e8c0c4067158ffbc6902df659517ec574b8c149"}
::
Set the analog Value of a pin. It will be output using PWM.
Objects can contain:

* `freq` - pulse frequency in Hz, eg. `analogWrite(A0,0.5,{ freq : 10 });` - specifying a frequency will force PWM output, even if the pin has a DAC
* `soft` - boolean, If true software PWM is used if hardware is not available.
* `forceSoft` - boolean, If true software PWM is used even if hardware PWM or a
  DAC is available

> **Note:** if you didn't call `pinMode` beforehand then this function will also reset pin's state to `"analog_output"`

### arguments

::i-chinese{sha="66873740eb3b8a285d2feb2ff783c3e603ad8e92463b9e1dd5fec8131a751e41"}
::
A variable containing the arguments given to the function:

```javascript
function hello() {
  console.log(arguments.length, JSON.stringify(arguments));
}
hello()        // 0 []
hello("Test")  // 1 ["Test"]
hello(1,2,3)   // 3 [1,2,3]
```

> **Note:** Due to the way Espruino works this is doesn't behave exactly
the same as in normal JavaScript. The length of the arguments array
will never be less than the number of arguments specified in the 
function declaration: `(function(a){ return arguments.length; })() == 1`.
Normal JavaScript interpreters would return `0` in the above case.

### atob(base64Data)

::i-chinese{sha="4851f6450e809a8be279cc37ac1c773743f4f2bd172a785d04e1d48c957aba23"}
::
Decode the supplied base64 string into a normal string

### btoa(binaryData)

::i-chinese{sha="767484b9ac5fe148e1cd849d3ae7a03b2094d14852381243bbcd96fc20852667"}
::
Encode the supplied string (or array) into a base64 string

### changeInterval(id,time)

::i-chinese{sha="f6e31f464f7f6fb67ea2fb8d58f242a9089490e197dc7521fcc3412891d89c33"}
::
Change the Interval on a callback created with `setInterval`, for example:

```javascript
var id = setInterval(function () { print('foo'); }, 1000); // every second
changeInterval(id, 1500); // now runs every 1.5 seconds
```

This takes effect immediately and resets the timeout, so in the example above,
regardless of when you call `changeInterval`, the next interval will occur
1500ms after it.

### clearInterval(id)

::i-chinese{sha="275e94f50eddffeb6a79386f5c9ad60ec7648c51e271d9214d67fcd743b91a1e"}
::
Clear the Interval that was created with `setInterval`, for example:

```javascript
var id = setInterval(function () { print('foo'); }, 1000);
clearInterval(id);
```

If no argument is supplied, all timeouts and intervals are stopped.
To avoid accidentally deleting all Intervals, if a parameter is supplied but is `undefined` then an Exception will be thrown.

### clearTimeout(id)

::i-chinese{sha="ae1183ab994e9e20ab16328d0b862d3bec720cddaf1cbb239507c1254f19e2d1"}
::
Clear the Timeout that was created with `setTimeout`, for example:

```javascript
var id = setTimeout(function () { print('foo'); }, 1000);
clearTimeout(id);
```

If no argument is supplied, all timeouts and intervals are stopped.
To avoid accidentally deleting all Timeouts, if a parameter is supplied but is `undefined` then an Exception will be thrown.

### clearWatch(id)

::i-chinese{sha="a196b280a039f6a29cc84abe1ad511da7b08cbaf93d2c89fe789bb6de2a017de"}
::
Clear the Watch that was created with setWatch. If no parameter is supplied, all watches will be removed.
To avoid accidentally deleting all Watches, if a parameter is supplied but is `undefined` then an Exception will be thrown.

### decodeURIComponent(str)

::i-chinese{sha="837fd2158fb14a26104a2e4ab68b6449cafa5150e8ed45785305c7f44f24f11c"}
::
Convert any groups of characters of the form '%ZZ', into characters with hex
code '0xZZ'

### digitalPulse(pin,value,time)

::i-chinese{sha="e407ef2c0ae64e540cb3df813fd07ec35b1a0222e42b1b74b3264bb56d62ffe1"}
::
Pulse the pin with the value for the given time in milliseconds. It uses a
hardware timer to produce accurate pulses, and returns immediately (before the
pulse has finished). Use `digitalPulse(A0,1,0)` to wait until a previous pulse
has finished.

e.g. `digitalPulse(A0,1,5);` pulses A0 high for 5ms.
`digitalPulse(A0,1,[5,2,4]);` pulses A0 high for 5ms, low for 2ms, and high for
4ms

> **Note:** if you didn't call `pinMode` beforehand then this function will also reset pin's state to `"output"`

digitalPulse is for SHORT pulses that need to be very accurate. If you're doing
anything over a few milliseconds, use setTimeout instead.

### digitalRead(pin)

::i-chinese{sha="d4d42c237ff3a7e7a4ece6a0132d6faeefef0e38f8256ac4e2c9b8f556391245"}
::
Get the digital value of the given pin.

> **Note:** if you didn't call `pinMode` beforehand then this function will also reset pin's state to `"input"`

If the pin argument is an array of pins (e.g. `[A2,A1,A0]`) the value returned
will be an number where the last array element is the least significant bit, for
example if `A0=A1=1` and `A2=0`, `digitalRead([A2,A1,A0]) == 0b011`

If the pin argument is an object with a `read` method, the `read` method will be
called and the integer value it returns passed back.

### digitalWrite(pin,value)

::i-chinese{sha="72a33405a0186130e63d397e18f96203a3a14a6406785df9dfc69bcf2fb99a01"}
::
Set the digital value of the given pin.

> **Note:** if you didn't call `pinMode` beforehand then this function will also reset pin's state to `"output"`

If pin argument is an array of pins (e.g. `[A2,A1,A0]`) the value argument will
be treated as an array of bits where the last array element is the least
significant bit.

In this case, pin values are set least significant bit first (from the
right-hand side of the array of pins). This means you can use the same pin
multiple times, for example `digitalWrite([A1,A1,A0,A0],0b0101)` would pulse A0
followed by A1.

If the pin argument is an object with a `write` method, the `write` method will
be called with the value passed through.

### dump()

::i-chinese{sha="9fc06d0db9f62bd9d7bcfab95449c13c87ecab11994f098d890ccde2f161cf0b"}
::
Output current interpreter state in a text form such that it can be copied to a
new device

Espruino keeps its current state in RAM (even if the function code is stored in
Flash). When you type `dump()` it dumps the current state of code in RAM plus
the hardware state, then if there's code saved in flash it writes "// Code saved
with E.setBootCode" and dumps that too.

> **Note:** 'Internal' functions are currently not handled correctly. You will
need to recreate these in the `onInit` function.

### echo(echoOn)

::i-chinese{sha="fc2db6bc21614ff9964cee980a17ca70d42e9440fbbad82e7bd4e2be28d07dfe"}
::
Should Espruino echo what you type back to you? true = yes (Default), false = no. When echo is off, the result of executing a command is not returned. Instead, you must use `print` to send output.

### edit(funcName)

::i-chinese{sha="661d4a785b2bd1c3baab1bf8778b80af1ace4269279de877582242c57fb2b8c4"}
::
Fill the console with the contents of the given function, so you can edit it.

> **NOTE:** This is a convenience function - it will not edit 'inner functions'. For that, you must edit the 'outer function' and re-execute it.

### encodeURIComponent(str)

::i-chinese{sha="4ed0022e464531bfac402583a793334cf30f6992859c360c2b8e0aa8280f40a7"}
::
Convert a string with any character not alphanumeric or `- _ . ! ~ * ' ( )`
converted to the form `%XY` where `XY` is its hexadecimal representation

### eval(code)

::i-chinese{sha="ca7e67c4d4cc75745604dd19a4878b658d457ab9d8fa98b3ac72093b2f4364cc"}
::
Evaluate a string containing JavaScript code

### getPinMode(pin)

::i-chinese{sha="55e876f9fe8a76d996fc90143d392cf647ebecf47eeb5d8dccfaa86e2300c409"}
::
Return the current mode of the given pin. See `pinMode` for more information on
returned values.

### getSerial()

::i-chinese{sha="aa6bf4f4388b95ef7379230d98f10d96da7d607cffd7998904eedd38236e243c"}
::
Get the serial number of this board

### getTime()

::i-chinese{sha="ad192617fde0443a4491ef4b175194aae13694f05502d8db1222e9d79a2b6e8c"}
::
Return the current system time in Seconds (as a floating point number)

### global

::i-chinese{sha="5d277c964fd850efd8027eccf1628d61b053f29128a07948f717b42fff473f72"}
::
A reference to the global scope, where everything is defined.

### isFinite(x)

::i-chinese{sha="a93d919388b9e814fcf55c2959a5e411156e3677b23447e93cf9c7d6a7c4d774"}
::
Is the parameter a finite number or not? If needed, the parameter is first
converted to a number.

### isNaN(x)

::i-chinese{sha="8723760f82d7e040d6c3cb0a186c32a6f05b6c7eff3e1064d0214439682d3476"}
::
Whether the x is NaN (Not a Number) or not

### load(filename)

::i-chinese{sha="9c066291edf0ce29e0b22c5ff7e0b95d715fdf805037b6e49ba9978d89e47a90"}
::
Restart and load the program out of flash - this has an effect similar to
completely rebooting Espruino (power off/power on), but without actually
performing a full reset of the hardware.

This command only executes when the Interpreter returns to the Idle state - for
instance `a=1;load();a=2;` will still leave `a` as undefined (or what it was
set to in the saved program).

Espruino will resume from where it was when you last typed `save()`. If you want
code to be executed right after loading (for instance to initialise devices
connected to Espruino), add an `init` event handler to `E` with `E.on('init',
function() { ... your_code ... });`. This will then be automatically executed by
Espruino every time it starts.

**If you specify a filename in the argument then that file will be loaded from
Storage after reset** in much the same way as calling `reset()` then
`eval(require("Storage").read(filename))`

### parseFloat(string)

::i-chinese{sha="b714b94c56b44624617a4773e7b010207c47c9a8dff2dd24ac84242063a8faee"}
::
Convert a string representing a number into an float

### parseInt(string,radix)

::i-chinese{sha="fb49bcaa2d50251bfe8013303f4c834709239a5e9a5dfab2a19c8fae9fd1487b"}
::
Convert a string representing a number into an integer

### peek16(addr,count)

::i-chinese{sha="08852a1643ee50af0f81c7580ddc4c1192739ebe306af8a09d74564bc6055073"}
::
Read 16 bits of memory at the given location - DANGEROUS!

### peek32(addr,count)

::i-chinese{sha="a07c464b133da4aeaa160f67e904d5b531d04ecaba23d9333fe78fc8e5d23667"}
::
Read 32 bits of memory at the given location - DANGEROUS!

### peek8(addr,count)

::i-chinese{sha="30fc508f2d1d35e84a02a6a7228dc4ea2225b8eea5ea3b4ee80c3ff396ef3c1b"}
::
Read 8 bits of memory at the given location - DANGEROUS!

### pinMode(pin,mode)

::i-chinese{sha="69fd16bb12300820792eca89b925aa40e2ed858ca535942f20043d312f21c53e"}
::
Set the mode of the given pin.

 * `analog_output` - Analog output
 * `analog` - Analog input
 * `input` - Digital input
 * `input_pullup` - Digital input with internal pull-up resistor (If there is an internal resistor )
 * `input_pulldown` - Digital input with internal pull-down resistor (If there is an internal resistor )
 * `output` - Digital output
 * `opendrain` - Digital output that only ever pulls down to 0v. Sending a logical `1` leaves the pin open circuit
 * `opendrain_pullup` - Digital output that pulls down to 0v. Sending a logical `1` enables internal pull-up resistor (If there is an internal resistor )

### poke16(addr,value)

::i-chinese{sha="616727a789c3b3718f56136af08baebd531bb246c159d3d6d86e5f70cb57aa63"}
::
Write 16 bits of memory at the given location - VERY DANGEROUS!

### poke32(addr,value)

::i-chinese{sha="6179b2acaa5d3a51074070e7fb3bc92d670fb2559975370a229bd4b900c4fdcb"}
::
Write 32 bits of memory at the given location - VERY DANGEROUS!

### poke8(addr,value)

::i-chinese{sha="37e175eeb5aaa1a052d1790194a7511ffc8609d79bb95ca6884d546d26c0e781"}
::
Write 8 bits of memory at the given location - VERY DANGEROUS!

### print(text)

::i-chinese{sha="1ad6ec8b41bc1a4f33fc6d2b56b2aeb53ac592b8aaf5063437081bbb39045877"}
::
Print the supplied string(s) to the console

> **Note:** If you're connected to a computer (not a wall adaptor) via USB but **you are not running a terminal app** then when you print data Espruino may pause execution and wait until the computer requests the data it is trying to print.

### require(moduleName)

::i-chinese{sha="5aeddf59b8f36b365f7855b8a602706445c4924cf838149a34b6e80d8c1ed27a"}
::
Load the given module, and return the exported functions and variables.
For example:

```javascript
var s = require("Storage");
s.write("test", "hello world");
print(s.read("test"));
// prints "hello world"
```

Check out [the page on Modules](/modules) for an explanation
of what modules are and how you can use them.

### reset(clearFlash)

::i-chinese{sha="1f811e361dfe765171045c409ea5dfbc2ce09183eb25ff391170466285ba098b"}
::
Reset the interpreter - clear program memory in RAM, and do not load a saved
program from flash. This does NOT reset the underlying hardware (which allows
you to reset the device without it disconnecting from USB).

This command only executes when the Interpreter returns to the Idle state - for instance `a=1;reset();a=2;` will still leave `a` as undefined.

The safest way to do a full reset is to hit the reset button.

If `reset()` is called with no arguments, it will reset the board's state in RAM
but will not reset the state in flash. When next powered on (or when `load()` is
called) the board will load the previously saved code.

Calling `reset(true)` will cause *all saved code in flash memory to be cleared
as well*.

### save()

::i-chinese{sha="a46a97fc048a90c72af3960541c1b83295838e79b441602825651902a58ccf6e"}
::
Save the state of the interpreter into flash (including the results of calling
`setWatch`, `setInterval`, `pinMode`, and any listeners). The state will then be
loaded automatically every time Espruino powers on or is hard-reset. To see what
will get saved you can call `dump()`.

> **Note:** If you set up intervals/etc in `onInit()` and you have already called
`onInit` before running `save()`, when Espruino resumes there will be two copies
of your intervals - the ones from before the save, and the ones from after -
which may cause you problems.

For more information about this and other options for saving, please see the
[Saving code on Espruino](https://www.espruino.com/Saving) page.

This command only executes when the Interpreter returns to the Idle state - for
instance `a=1;save();a=2;` will save `a` as 2.

When Espruino powers on, it will resume from where it was when you typed
`save()`. If you want code to be executed right after loading (for instance to
initialise devices connected to Espruino), add a function called `onInit`, or
add a `init` event handler to `E` with `E.on('init', function() { ... your_code
... });`. This will then be automatically executed by Espruino every time it
starts.

In order to stop the program saved with this command being loaded automatically,
check out [the Troubleshooting
guide](https://www.espruino.com/Troubleshooting#espruino-stopped-working-after-i-typed-save-)

### setBusyIndicator(pin)

::i-chinese{sha="db79938258177b4bf5f7ea41e730556cb409fce62e6e46a27d6fc87a43cb3077"}
::
When Espruino is busy, set the pin specified here high. Set this to undefined to
disable the feature.

### setInterval(function,timeout,args)

::i-chinese{sha="edcdabf06748ce822290c3e5ca224d2602198c03708c979f9c06553312ac3b59"}
::
Call the function (or evaluate the string) specified REPEATEDLY after the timeout in milliseconds.
For instance:

```javascript
setInterval(function () {
  console.log("Hello World");
}, 1000);
// or
setInterval('console.log("Hello World");', 1000);
// both print 'Hello World' every second
```

You can also specify extra arguments that will be sent to the function when it
is executed. For example:

```javascript
setInterval(function (a,b) {
  console.log(a+" "+b);
}, 1000, "Hello", "World");
// prints 'Hello World' every second
```

If you want to stop your function from being called, pass the number that was
returned by `setInterval` into the `clearInterval` function.

> **Note:** If `setDeepSleep(true)` has been called and the interval is greater than 5 seconds, Espruino may execute the interval up to 1 second late. This is because Espruino can only wake from deep sleep every second - and waking early would cause Espruino to waste power while it waited for the correct time.

### setSleepIndicator(pin)

::i-chinese{sha="8f23f29fd4718843ed59c1e64106ef23537d06f9fdbc0177077c8ed8d1eb9903"}
::
When Espruino is asleep, set the pin specified here low (when it's awake, set it
high). Set this to undefined to disable the feature.

### setTime(time)

::i-chinese{sha="6222e321586565cdcdb815aa8540c8aee4130bf30d2200ed65648da4ef7e7b1c"}
::
Set the current system time in seconds (`time` can be a floating point value).

This is used with `getTime`, the time reported from `setWatch`, as well as when
using `new Date()`.

`Date.prototype.getTime()` reports the time in milliseconds, so you can set the
time to a `Date` object using:

```javascript
setTime((new Date("Tue, 19 Feb 2019 10:57")).getTime()/1000)
```

To set the timezone for all new Dates, use `E.setTimeZone(hours)`.

### setTimeout(function,timeout,args)

::i-chinese{sha="d372610c1496c978a11d39252b7c25230491cf935c8678ffba6e036b48e58c51"}
::
Call the function (or evaluate the string) specified ONCE after the timeout in milliseconds.
For instance:

```javascript
setTimeout(function () {
  console.log("Hello World");
}, 1000);
// or
setTimeout('console.log("Hello World");', 1000);
// both print 'Hello World' after a second
```

You can also specify extra arguments that will be sent to the function when it
is executed. For example:

```javascript
setTimeout(function (a,b) {
  console.log(a+" "+b);
}, 1000, "Hello", "World");
// prints 'Hello World' after 1 second
```

If you want to stop the function from being called, pass the number that was
returned by `setTimeout` into the `clearTimeout` function.

> **Note:** If `setDeepSleep(true)` has been called and the interval is greater than 5 seconds, Espruino may execute the interval up to 1 second late. This is because Espruino can only wake from deep sleep every second - and waking early would cause Espruino to waste power while it waited for the correct time.

### setWatch(function,pin,options)

::i-chinese{sha="b707c33beb4e87b60515827f9745114be0db1864260b398efc39eb148bee69f1"}
::
Call the function specified when the pin changes. Watches set with `setWatch`
can be removed using `clearWatch`.

If the `options` parameter is an object, it can contain the following
information (all optional):

```javascript
var option = {
   // Whether to keep producing callbacks, or remove the watch after the first callback
   repeat: true/false(default),
   // Trigger on the rising or falling edge of the signal. Can be a string, or 1='rising', -1='falling', 0='both'
   edge:'rising'(default for built-in buttons)/'falling'/'both'(default for pins),
   // Use software-debouncing to stop multiple calls if a switch bounces
   // This is the time in milliseconds to wait for bounces to subside, or 0 to disable
   debounce:10 (0 is default for pins, 25 is default for built-in buttons),
   // Advanced: If the function supplied is a 'native' function (compiled or assembly)
   // setting irq:true will call that function in the interrupt itself
   irq : false(default)
   // Advanced: If specified, the given pin will be read whenever the watch is called
   // and the state will be included as a 'data' field in the callback
   data : pin
   // Advanced: On Nordic devices, a watch may be 'high' or 'low' accuracy. By default low
   // accuracy is used (which is better for power consumption), but this means that
   // high speed pulses (less than 25us) may not be reliably received. Setting hispeed=true
   // allows for detecting high speed pulses at the expense of higher idle power consumption
   hispeed : true
}
```

The `function` callback is called with an argument, which is an object of type
`{state:bool, time:float, lastTime:float}`.

 * `state` is whether the pin is currently a `1` or a `0`
 * `time` is the time in seconds at which the pin changed state
 * `lastTime` is the time in seconds at which the **pin last changed state**.
   When using `edge:'rising'` or `edge:'falling'`, this is not the same as when
   the function was last called.
 * `data` is included if `data:pin` was specified in the options, and can be
   used for reading in clocked data

For instance, if you want to measure the length of a positive pulse you could
use `setWatch(function(e) { console.log(e.time-e.lastTime); }, BTN, {
repeat:true, edge:'falling' });`. This will only be called on the falling edge
of the pulse, but will be able to measure the width of the pulse because
`e.lastTime` is the time of the rising edge.

Internally, an interrupt writes the time of the pin's state change into a queue
with the exact time that it happened, and the function supplied to `setWatch` is
executed only from the main message loop. However, if the callback is a native
function `void (bool state)` then you can add `irq:true` to options, which will
cause the function to be called from within the IRQ. When doing this, interrupts
will happen on both edges and there will be no debouncing.

> **Note:** if you didn't call `pinMode` beforehand then this function will reset pin's state to `"input"`

> **Note:** The STM32 chip cannot watch two pins with the same number - eg `A0` and `B0`.

> **Note:** On nRF52 chips `setWatch` disables the GPIO output on that pin. In order to be able to write to the pin again you need to disable
the watch with `clearWatch`.

### shiftOut(pins,options,data)

::i-chinese{sha="373936d5837fb5c28ba4671954cd6514e8248e8bf1ad726dac43788754ed0006"}
::
Shift an array of data out using the pins supplied *least significant bit
first*, for example:

```javascript
// shift out to single clk+data
shiftOut(A0, { clk : A1 }, [1,0,1,0]);
```

```javascript
// shift out a whole byte (like software SPI)
shiftOut(A0, { clk : A1, repeat: 8 }, [1,2,3,4]);
```

```javascript
// shift out via 4 data pins
shiftOut([A3,A2,A1,A0], { clk : A4 }, [1,2,3,4]);
```

`options` is an object of the form:

```javascript
var option = {
  clk : pin, // a pin to use as the clock (undefined = no pin)
  clkPol : bool, // clock polarity - default is 0 (so 1 normally, pulsing to 0 to clock data in)
  repeat : int, // number of clocks per array item
}
```

Each item in the `data` array will be output to the pins, with the first pin in
the array being the MSB and the last the LSB, then the clock will be pulsed in
the polarity given.

`repeat` is the amount of times shift data out for each array item. For instance
we may want to shift 8 bits out through 2 pins - in which case we need to set
repeat to 4.

### trace(root)

::i-chinese{sha="8f0e2fc99fba0f3f1741814d7aeb5d197f5ff12292e58c7425f8bc1cf4132486"}
::
Output debugging information

> **Note:** This is not included on boards with low amounts of flash memory, or the Espruino board.
