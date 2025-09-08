# Feedback-Guitar-Pedal

![thumbnail](https://github.com/user-attachments/assets/15f0e10a-a074-4aeb-89d2-42c260b15fe8)

# About Us
This pedal was created and designed by Cody Carter (Computer Engineering), Rylie Fontenot (Electrical Engineering), and Cecilia [Last Name] (Electrical Engineering). Together we created a custom feedback looper pedal that open up so many tone possibilities to a guitar player's arsenal. Development responsibilities were split between us, with each contributing their expertise in analog circuit design, PCB design, and hardware integration.

<div align="center">
  <h3>Cody Carter</h3>
  <img src="https://github.com/user-attachments/assets/2808f0ad-6c56-464c-abdd-6ece9a4be026" alt="Cody Carter Profile" width="100" style="border-radius:50%">
  <p>
    <a href="https://github.com/codycarter1763">
      <img src="https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white" alt="GitHub">
    </a>
    <a href="https://www.linkedin.com/in/cody-carter-a8a747293/">
      <img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn">
    </a>
  </p>

<div align="center">
  <h3>Rylie Fontenot</h3>
  <img src="https://media.licdn.com/dms/image/v2/D5603AQFKTee4mqEFRQ/profile-displayphoto-shrink_400_400/B56Zd2r2jqHEAg-/0/1750042897225?e=1759968000&v=beta&t=cUhbHVjkiVxpLuMKNt5Zb8UxYemX87PC8ysEgMbyvS0" width="100" style="border-radius:50%">
  <p>
    <a href="https://www.linkedin.com/in/rylie-fontenot-979aa1330/">
      <img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn">
    </a>
  </p>

  <div align="center">
  <h3>Cecilia (insert last name)</h3>
  <img src="" alt="" width="100" style="border-radius:50%">
  <p>
    <a href="">
      <img src="https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white" alt="GitHub">
    </a>
    <a href="">
      <img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn">
    </a>
  </p>
  
# About
All you do is plug in a guitar into the input, route a pedal through the effects loop, and run the output to your signal chain or amp. Depending on the pedals put in the effects loop, like delay, fuzz, chorus, distortion, etc, you will have infinite delay, chasmic reverb, snarling fuzz tones, and so much more. Each pedal has a truly unique effect when placed in the looper that brings new life and inspiration to your guitar pedals.

Convinced yet? The possibilities with a feedback looper are endless, give it a shot and see what you've been missing!

# Parts List
All of these parts can be easily picked up online for under 15-20 bucks.

This build can be made without the LED and DC jack, but I prefer having an indicator for whether the pedal is on.

- 1590BB Enclosure (I used a bigger enclosure for the graphics)
- 4x 1/4" Guitar Jacks
- 1x DC Power Connector
- 1x Latching or Momentary 3PDT Footswitch
- 1x LED
- 1x 4.7k resistor

For Boost and Phase Circuit
- 6x 1Meg Resistors
- 3x 10u Bipolar Capacitors
- 1x 47u Electrolytic Capacitor
- 1x 47p Capacitor
- 1x 2.7k Resistor
- 1x 4.7u Capacitor
- 1x TL072 OP Amp
- 3x 10k Resistors
- 1x C100k Potentiometer
- 1x A100k Potentiometer
- 1x Dual Gang Toggle Switch
- 1x Single Gang Toggle Switch
  
# Schematic
This is the schematic for the feedback looper pedal. The way this design works is by looping the effects loop back onto itself. Using a distortion pedal, feedback similar to amplifier feedback is observed. Whereas if you put a delay pedal in the loop, you can get infinite delay or a stacked delay effect. Every pedal will react differently in this setup, making for a truly unique pedal that brings new life to your pedals. As well as, with the volume potentiometer you can control how much feedback is being heard in the signal chain. 
<br>
![Feedback Looper Diagram](https://github.com/user-attachments/assets/8009a770-fe0a-44e6-8ca3-40d68abfe497)
<br>

## Boost and Phase Circuit
![BoostV1-min](https://github.com/user-attachments/assets/76d73c05-668e-442a-a62f-e9742ba107b0)
<br>
My two classmates, Rylie and Cecilia, and I designed the schematic and circuit board for use with this pedal using LTSpice and Fusion 360. The design includes an adjustable clean boost, phase reversal, and adjustable feedback volume for more sonic versitility with pedals in the feedback loop.
### Analysis
#### Clean Boost Stage
![image](https://github.com/user-attachments/assets/ffff4b2a-9eae-4d1a-be30-3aacc9880a1a)
##### Cutoff Frequency Input 
With a goal being a clean boost that will boost the feedback loop volume with a flat response, we used these components to get the cutoff frequency low. <br>
f = 2pi(10uF)(1Meg) = 0.02Hz <br>

##### Cutoff Frequency Feedback Loop
f = 2pi(4.7uF)(2.7k) = 12.54Hz <br>
![Frequency Response BoostV1](https://github.com/user-attachments/assets/7b27e127-77a5-4945-9457-f5ebef95aab5)

##### Gain
Since there will already be a considerable amount of feedback, we opted for a low gain boost <br>
Gain = 1 + 10k / 2.7k = 4.7
Gain in dB = 20log(4.7) = 13.44dB
![Output Waveform BoostV1](https://github.com/user-attachments/assets/f11ba0d6-66c1-4e51-97d2-c973e15da99b)
<br>

#### Phase Reverse and Buffer
To reverse the phase, we connected a toggle switch to the non-inverting input of the TL072 where the input is switched between positive boost output and ground. When switched to ground, the phase will be reversed 180 degrees and have a significant effect on the tone. Since the signal was boosted in the first stage, we used two 10k resistors for unitary gain.
<br>
![image](https://github.com/user-attachments/assets/7a5e876e-abd9-448b-9412-33c87ac3f07c)
![image](https://github.com/user-attachments/assets/3ca4b758-cc5e-4d9e-8a53-d1a29edff9fa)

# Artwork
I used Hayes white background waterslide decals to transfer the artwork to the enclosure. Waterslide decals are super cheap and easy to use, so it was perfect for my guitar pedal builds without having to outsource for graphics. Using inkscape, you can easily add in additional information such as what certain knobs do on your pedal. 

# Closing
I hope you got some useful information about how to build a feedback pedel for yourself to try out. Especially for beginner pedal builders, this is the perfect way to start learning how to build guitar pedals. This pedal is always suprising me every time I use it, it opened up a whole new universe of tone at my fingertips without having to use a cranked amplifier.
