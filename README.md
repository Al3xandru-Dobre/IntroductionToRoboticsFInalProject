# Introduction

Final project for my lab of Introduction to Robotics. This project creates an interactive audio-visual system that translates sound frequencies into dynamic light patterns using an ESP32 microcontroller, LED matrices, and a piano keyboard. Designed to bridge the gap between digital signal processing and tangible user interaction, the system captures audio inputs—whether from a microphone, a MIDI keyboard, or a user-uploaded file—and processes them in real time to generate immersive visual and auditory outputs.

At its core, the ESP32 acts as the brain of the system, handling signal processing, state management, and wireless communication (via Wi-Fi and Bluetooth) to enable seamless interaction with a mobile app. The LED matrix visualizes sound frequencies as vibrant color patterns, while a speaker outputs the processed audio, creating a multisensory experience. Users can play notes on the keyboard, upload music files, or even sing into the microphone, with the system adapting to each input in real time.

# Table of contents

- [Introduction](#Introduction)
- [Q&A and clarifications](#Q&A-and-clarifications)
- [Bill of Materials(BOM)](#Bill-of-Materials)

# Q&A and clarifications

## What is the system boundary ?

The system consists in an Continous INPUT/OUTPUT stream of data, between the sensors(and user inputs) and the board ESP 32, that outputs to a series of MATRIX LED to visualise the OUTPUT frequency in a more comprihensable way, translating the signal frequency of sounds to colors.

## Where does intelligence live ?

The main point, where orchestration and decision are beeing taken is the main board, ESP 32, where the logic of signal processing will be stored, together with the final state machine and interution in the execution flow. Also, the comunication between the system (it will comprihend a WI-Fi and Bluetooth for the user to comunicate in addition to the hardwear keys) are beeing handled by the main board.

## What is the hardest technical problem ?

There are a few key problems in the implementation, both on the softwear and hardwear side, that will heavily influence the outcome of the project:

### Problem 1

  The logic of the signal processing, especially when multiple succesive inputs (sounds) are beeing delivered, via the microphone or via the keyboard. This is especially difficult, becuase the format of discretisation needs an interval of time, and if the treshold of which the input comes (or is outputed) the sound (information in general) will be lost and artefacts and anomalies can take place.

### Problem 2

  Handling multiple inputs from the user. I plan to input in 3 ways. A file that would be uploaded by the user via their phone using Wi-Fi or Bluetooth, direct sounds beeing picked up via a microphone, or digitally created by prassing a key on the piano keyboard that will come with the hardwear. Each of the input comes with its own unique set of challanges. The microphone aproach, is particular difficult, since it can pick up noise that is not intended. Also, another dificulty consists in transforming the analog signal picked up by the microphone into a digital signal, and further into a signal that can be used and modified acording to the logic of the app.

### Problem 3

  The robustness of the system, the finite state machine on which will be based, can play a critical part in the feel and quality of the result. Interuptions, button debounces, concomitent button presses and longer button presses, the UI and the output (both visual and sound) play an important part on the user experience, thus extensive testing and carefull planing is required.

## What is the minimum demo ?

  The minimum demo consists in a piano midi keyboard, a visualizer made out of multiple Matrixes, and a speaker, coupled with the phone app. The way this demo intends to work, is the user will choose on the HTML page on their phone the mode in which they want to use the system (either upload a file and the system will play and visualise it, either unlock the keyboard and play your own song on the hardwear that will trigger the speakers and visualiser to display the frequency of the notes). The keyboard shall be functional, and features like pressing 2 or more keys at once, longer presses and the audio and visual output fully functional.

## Why is not just a tutorial ?

  The project consists of multiple layers of app, from the input layer of the sensors (converting analog to digital is an entire thing), to the data processing layer, the UI and UX, hardwear handling such as the key presses, communication between the board, user and the devices ,and the handle of the MATRIX display creating a comprehensible visualiser. Thus beeing said, it reaquires combining diffrent developing areas and varied procedure to put everything together.  


# Bill of Materials

## 1.Main Controller Board
  - ESP 32 Development Board (e.g. ESP32-WROOM-32)
  - Purpose: Main processing unit for signal processing, state machine logic, and communication (Wi-Fi/Bluetooth)
  - Quantity: 1

## 2.Input Components
  ### A. Microphone Module (e.g., MAX4466, INMP441 I2S MEMS Microphone, or electret microphone with amplifier)
  - Purpose: Capture analog audio signals for processing
  - Quantity: 1

  ### B. Piano Keyboard (MIDI Input, MIDI Keyboard (e.g., 25-key or 49-key USB/MIDI keyboard))
  - Mechanical keyboard switches (e.g., Cherry MX or tactile switches)
  - Diodes (1N4148) for debouncing
  - PCB or breadboard for wiring
  - Purpose: Digital input for notes/keys.
  - Quantity: 1 (or components for DIY)

  ### C. User Input (Hardwear Buttons): Tactile Push Buttons (e.g., 6mm x 6mm)
  - Purpose: Hardware controls for mode selection, volume, etc.
  - Quantity: 4–6 (depending on features)

## 3.Output Components
  ### A. LED Matrix Display (Addressable RGB LED Matrix (e.g., WS2812B/NeoPixel, 8x8 or 16x16 panels))
  - Purpose: Visualize frequency/color output.
  - Quantity: 4–8 panels (depending on desired size)

  ### B. Speaker/Audio Output Small Speaker (e.g., 8Ω 0.5W speaker)
  - Alternative: I2S Audio DAC Module (e.g., MAX98357A) + speaker
  - Purpose: Play processed audio output.
  - Quantity: 1

## 4.Communication Modules
- Built-in ESP32 Features:
  - Wi-Fi and Bluetooth (no additional modules needed).
  - Purpose: Wireless communication with phone/app.

## 5.Power Supply (5V Power Supply (e.g., USB-C PD adapter or 5V 2A wall adapter))
  - Purpose: Power the ESP32, LED matrix, and other components.
  - Quantity: 1

## 6.Miscellaneous Components
  - Breadboard/PCB (for prototyping/wiring)
      - Quantity: 1–2
  - Jumper Wires (Male-to-Male, Male-to-Female)
      - Quantity: 20–30
  - Resistors (e.g., 220Ω, 1kΩ, 10kΩ for pull-ups/pull-downs)
       - Quantity: 10–20
  - Capacitors (e.g., 100nF, 10µF for noise filtering)
       - Quantity: 5–10
   - Transistors/MOSFETs (e.g., 2N2222 or IRLZ44N for driving high-current loads like LED matrices)
       - Quantity: 2–4
    
## 7.Softwear Dependencies (Not part of BOM but required for functionality)

  - Arduino IDE or PlatformIO (for ESP32 Programming)
  - Libraries :
    - FastLED/NeoPixel (for LED matrix control)
    - ESP32 Wi-Fi/Bluetooth libraries
    - Audio processing libraries (e.g., ArduinoFFT for frequency analysis)
    - MIDI library

    
 

    


  
