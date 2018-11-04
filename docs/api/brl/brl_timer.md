---
id: brl.timer
title: BRL.Timer
sidebar_label: BRL.Timer
---


## Functions

### `Function CreateTimer:TTimer( hertz#,event:TEvent=Null )`

Create a timer


[CreateTimer](../../brl/brl.timer/#function-createtimer-ttimer-hertz-event-tevent-null) creates a timer object that 'ticks' <b>hertz</b> times per second.

Each time the timer ticks, <b>event</b> will be emitted using [EmitEvent](../../brl/brl.event/#function-emitevent-event-tevent).

If <b>event</b> is Null, an event with an <b>id</b> equal to EVENT_TIMERTICK and
<b>source</b> equal to the timer object will be emitted instead.


#### Returns
A new timer object



### `Function TimerTicks:Int( timer:TTimer )`

Get timer tick counter

#### Returns
The number of times <b>timer</b> has ticked over



### `Function WaitTimer:Int( timer:TTimer )`

Wait until a timer ticks

#### Returns
The number of ticks since the last call to [WaitTimer](../../brl/brl.timer/#function-waittimer-int-timer-ttimer)


#### Example
```blitzmax
timer=CreateTimer( 10 )

Repeat
	Print "Ticks="+WaitTimer( timer )
Forever
```

### `Function StopTimer( timer:TTimer )`

Stop a timer

Once stopped, a timer can no longer be used.


