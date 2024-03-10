# Arturia_minilab3
Toolling for **Arturia Minilab 3**

## Ardour
The **ardour** directory contains a *midi_map* allowing you to use your **Minilab3** in **Ardour**.

I made this choices:
* Faders are bind to the 4 first track/buses/bank
* *Loop*, *Stop*, *Play* and *Record* pad function are bind to the transport *Loop*,
  *Stop*, *Play* and *Record*
* The Main knob is linked to switch next and previous track. Pushing the knob
  will toggle record on the current track/bus.
* The last 8 knobs are bind to the first plugin of each track. It is configured to
  control the first 8 parameters of this plugin[^1].

**Ardour** documentation about howto make a *midi_map* is available here:
* [Generic MIDI in Ardour](https://manual.ardour.org/using-control-surfaces/generic-midi/midi-binding-maps/)
* [Full Ardour commands](https://manual.ardour.org/appendix/menu-actions-list/)

## Getting MIDI messages
Because it's not so simple to translate incoming midi message to Note or
Control, here is a conveniant way to get those codes:
```
$ amidi -l
Dir Device    Name
IO  hw:2,0,0  Minilab3 Minilab3 MIDI
IO  hw:2,0,1  Minilab3 Minilab3 DIN THRU
IO  hw:2,0,2  Minilab3 Minilab3 MCU/HUI
IO  hw:2,0,3  Minilab3 Minilab3 ALV
$ amidi -d -p hw:2,0,0
# Rotating a knob
B0 72 40
B0 72 41
# Pushing a note
90 43 7F
# Releasing a note
90 43 00
```


[^1]: I would like to find a way to have a better parameter management with
    Arturia Minilab3 knobs, but I didn't find a proper way to do so. Not
    every couple of plugin/instrument support correctly this function, I hope
    finding a trick to correctly assign knobs and parameters.
