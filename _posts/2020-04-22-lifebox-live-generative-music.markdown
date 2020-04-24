---
layout: post
title:  "lifebox live generative music"
date:   2020-04-22 20:14:26 +0200
categories: lifebox
---
Lifebox project have a `new feature`: a generative MIDI music. Now, the Lifebox script generates a MIDI output based on real-time simulation data. Those `MIDI signals` can be played through a synth or other musical software, allowing to create an immersive soundscape.

This code is only a preview demo release and must be improved.

{% highlight python %}
import rtmidi # midi library
# midi thread functions

# midi chords
def majorChordGenerator():
    startValue = random.randint(50,60)
    return ([startValue,startValue+4,startValue+7])

def minorChordGenerator():
    startValue = random.randint(50,60)
    return ([startValue,startValue+3,startValue+7])

def augmentedChordGenerator():
    startValue = random.randint(50,60)
    return ([startValue,startValue+4,startValue+8])

def reducedChordGenerator():
    startValue = random.randint(50,60)
    return ([startValue,startValue+3,startValue+6])

# midi output function
def generativeSound(midiStop):
    midiout = rtmidi.MidiOut()
    available_ports = midiout.get_ports()
    #print (available_ports)
    #print (midiout.get_port_count())
    midiout.open_port(1)

    # nasty way to stop all sounds
    for iter in range(0,10):
        for i in range(50,70):
            midiout.send_message([0x80,i,0])
    while not midiStop:
        chordType = random.randint(0,3)
        if specie1_individuals > specie2_individuals:
            chord = majorChordGenerator()
        else:
            chord = minorChordGenerator()
        midiout.send_message([0x90,chord[0],30])
        midiout.send_message([0x90,chord[1],30])
        midiout.send_message([0x90,chord[2],30])
        time.sleep(float(random.randint(3000,5000)/1000))
        midiout.send_message([0x80,chord[0],0])
        midiout.send_message([0x80,chord[1],0])
        midiout.send_message([0x80,chord[2],0])
    for iter in range(0,10):
        for i in range(50,70):
            midiout.send_message([0x80,i,0])
    del midiout
{% endhighlight %}

Check out the [Lifebox project repo](https://github.com/ferrithemaker/lifebox) for more information.

