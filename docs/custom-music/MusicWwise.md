---
sidebar_position: 2
---

# Custom Music via Wwise

## Prerequisites
:::note
This version will require Unreal Engine and Wwise for Music Replacements.
:::
 - Wwise 2021.1.13.8036 **or** Wwise 2021.1.14.8108
 - A program that can view UE4 PAK files (FModel, UModel)
 - A program that can pack UE4 PAK files (repak, UnrealPak)
 
## Setting up your sound files
In order for Wwise and wwise_pd3 to work properly, your files must be
in the WAV format with PCM encoding. The best way to do this is to use
a tool like ffmpeg to encode your audio to little endian 16-bit.

An example command for this is `ffmpeg -i input.wav/mp3 -c:a pcm_s16le output.wav` 

## Setting your Wwise for PAYDAY 3

### Using Wwise
1. Make sure you have a Wwise project ready for setting up and converting audio for your purpose.

:::
Note
Your Wwise project will have its Conversion Settings set to `Default Conversion Settings` which will export your audio in PCM format as you imported it into wwise.
Although fine by itself, your final size will be likely to be huge due to it being unconverted.
You can avoid high file sizes via `Audio Conversion`
You can set this by opening the project settings (Project->Project Settings),
going to the Source Settings tab. Pressing the 3 dots next to the
currently set conversion setting and selecting
`Factory Conversion Settings` to which ever format you prefer.
:::

### Creating the Audio Bus
First, you will need to create a audio bus called `Music` for your project. This will be associated to your music so it's volume can be adjusted ingame via the Music slider.

1. Navigate to your Master-Mixer Hierarchy located in the Audio tab via your Project Explorer.
2. Right-Click on the Master Audio Bus (located in your Default Work Unit) and create a new child folder.
3. Rename the child folder to `Main`.
4. Create a new Audio Bus child for your folder named `Music`.

### Creating the Music Switch
Think of this as a instruction the game asks for in order to play the correct music depending on the state of the level.

1. Navigate to the Game Syncs tab in your Project Explorer.
2. Create a new child switch group named `music_switch`.
3. Create 9 child switches exactly as shown below.
- anticipation
- assault
- control
- stealth
- suspense 1
- suspense 2
- suspense 3
- suspense 4
- suspense 5

### Making the Music Switch Container
This will be what you'll use to make your heist track so it can react accordingly depending on what switches the game calls for!

1. Navigate to the Audio tab via the Project Explorer.
2. Under the Interactive Music Hierarchy, Create a new Child Music Switch Container under the Default Work Unit or a Work Unit you made.
3. Create as many containers as needed for your heist track. (I.E If have 4 phases (Stealth, Control, Anticipation, Assault) then create 4 containers named accordingly.

You now have a template that you can freely copy and paste for whenever a heist track will be made!


### Setting up the Music Switch Container
1. After copying your template, import your audio to the container via drag and drop or by clicking on import audio.
2. Drag and drop the audio files to their respective containers, then crea