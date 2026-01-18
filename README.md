# Introduction

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
