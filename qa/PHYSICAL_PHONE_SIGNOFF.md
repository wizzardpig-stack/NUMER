# NUMER Physical Phone Sign-Off

Run this on the exact V12.10-or-later QA URL. Record device, OS, browser version and screen recording if anything fails.

## iPhone Safari

- Open Resolve and create a reading.
- Perform 20 fast vertical flicks across buttons and the bottom dock. Expected: zero accidental activations.
- Perform 10 scroll-then-tap actions immediately after momentum stops. Expected: all deliberate taps register.
- Pinch to approximately 150% and 200%, pan sideways, then operate the bottom dock.
- Rotate portrait → landscape → portrait while in Deep Reading and Compare.
- Open the keyboard in Resolve and both Name Lab fields. Switch sections with keyboard visible, dismiss, and return.
- Test José, O'Brien, Astra2, 李小龍, and José 李.
- Save two plates, compare them, delete one, and return to Compare.
- Confirm validation/toast text is not hidden behind the keyboard or dock.

## Android Chrome

Repeat the same sequence:

- 20 fast flicks across controls
- 10 immediate scroll-then-tap actions
- pinch 150% / 200% and pan
- portrait / landscape / portrait
- keyboard-open navigation
- José, O'Brien, Astra2, 李小龍, José 李
- save / duplicate save / Compare / delete

## Pass criteria

Both devices must record:

- 0 accidental control activations during flick tests
- 0 wrong-view dock activations
- deliberate taps register normally after scrolling
- pinch zoom and sideways pan remain usable
- keyboard never traps navigation or permanently covers required feedback
- landscape navigation remains available
- Name Lab never silently calculates unsupported scripts
- no crash or unrecoverable state
- no open P0/P1 defect

## Sign-off record

| Device | OS | Browser | Flicks | Tap-after-scroll | Pinch/pan | Keyboard | Rotation | Result |
|---|---|---|---:|---:|---|---|---|---|
| iPhone | | Safari | /20 | /10 | | | | |
| Android | | Chrome | /20 | /10 | | | | |
