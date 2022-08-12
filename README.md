# Shaper LFO

This is a Euro Rack module project for an LFO that can seamlessly change the output
waveform shape between a Triangle wave and Saw wave. The LFO has the following features:

Inputs:
- Linear CV Rate control
- Reset or Hold input (selectable by switch)
- Output waveform offset CV

Controls
- Rate Control
- CV Rate Level
- Triangle Shape/PWM control
- Output waveform offset Control
- Dual Rate switch
- Reser/Hold switch

Outputs:
- Triangle/Sawtooth 
- Square/PWM output
- Sine output
- Output indicator Dual color LED

The project include schematics and PCB design intended for hand soldering.

## Licence

This project is licenced under the "CERN Open Hardware Licence Version 2 -
Strongly Reciprocal" Open Hardware Licence.

The licence permits you to freely Make, Modify and even Sell products based on this 
project, as long as you do so under the same or a compatible Licence. 

In short; all source material, even if modified, _must_ remain Open Hardware and be 
available to everyone. 

Please read the documents in the [LICENCE](./LICENCE) folder for details.

## Principle of operation

The Oscillator core is an Integrator bases Relaxation oscillator. It uses an Op-Amp
integrator that accumulates an input voltage over time. The integrator output is in turn 
fed to an inverting Op-Amp Schmidt trigger, that inverts once the integrator output 
reaches a maximum or minimum level.

The output of the schmidt trigger alternates the input to the intergator from a positive
to a negative control voltage, generating a periodic triangular shaped waveform with a 
frequency determined by the integrator input voltage. The output from the Schmidt Trigger
is used as the Pulse Wave output.

These waveforms are mixed with a controllable offset voltage, to form the final output
signals. In addition a Sine-wave converter converts the triangle wave output to a 
Sine-like waveform, which becomes deformed rather then offset by the Offset control and CV.

The Shape adjustment works by creating both a direct and an inverted Control Voltage.
These voltages are "switched" alternatingly using two op-amps, that combined with some 
diodes. By supplying the alternating control voltage throgh a potentiometer, one can 
adjust the ratio from the positive and negative control voltage to feed to the integrator. 
This in turn controls the rise and fall time of the integrator, so it will seamlessly 
transition from a triangle to a saw waveform in both directions.

This also change the duty-cycle of the Schmidt trigger, and thus results in an adjustable
PWM output. The shape of the Sine-like output will be sqewed accodingly as well.

## Project files

There is a [Schemaitc diagram in PDF format](./ShaperLFO-Rev1.schematic.pdf) in the main folder. 

The Schematic and PCB project is a [Kicad 6 Project](https://www.kicad.org/).

In the simulations folder you can find a simulation of the working principle of the LFO.
The simulations are made in the [Circuit JS simulator](https://www.falstad.com/circuit/circuitjs.html).


