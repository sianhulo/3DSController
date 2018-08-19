3DSController ![](/3DS/cxi/icon48x48.png?raw=true)
===
A 3DS homebrew application which allows you to use your 3DS as a wireless controller for Windows.

### Download
The latest release will always be downloadable from [here](https://github.com/CTurt/3DSController/releases/).

If you are updating to 0.6 from an older version, you will need to make sure you update vJoy to the recommended version.

### Setup and Usage
Firstly, if you want to be able to register the circle pad or touch screen as a joystick you will need to install [vJoy (version 2.0.5-120515 is preferable)](http://sourceforge.net/projects/vjoystick/files/Beta%202.x/2.0.5-120515/vJoy_205_050515.exe/download). However, if you just want to use keyboard buttons, this is not necessary.

Extract the archive and copy the executable in the `3DS` directory with the extension that applies to your loader: `3DSController.3dsx` and `3DSController.smdh` for Ninjhax, `3DSController.3ds` for flashcards, or `3DSController.cia` for CFWs, into your 3DS's SD card or flashcard's micro SD card.

Copy the file `3DS/3DSController.ini` to the root of your 3DS's SD card, and change the line that says `IP: 192.168.0.4` to match your computer's local IP.

If you are unsure of your local IP address, run `3DSController.exe` and it will tell you.

Run `3DSController.exe` on your computer. If you are prompted, make sure to allow it through your firewall.

Start the application on your 3DS, there is no GUI, it will automatically try to connect to the IP address you put in `3DSController.ini`.

If it wasn't able to read the IP from `3DSController.ini`, it will notify you and quit.

Otherwise, you should just see a black screen, this is a good sign. To see if it works, open Notepad and press some buttons on the 3DS, they should show up. You can also test if the joystick works by going to Configure USB Game Controllers in Control Panel, it shows up as vJoy.

If using version 0.4 or above you can press L, R and X to bring up the keyboard. Press L, R and X again to close it.

If using version 0.6 or above, up to 16 joystick buttons are available. If you wish to use more than 8, you need to configure vJoy. Search in your start menu for vJoyConfig and set buttons to 16.

If using Ninjhax press Start and Select to return to the Homebrew Loader, otherwise you can just exit with the Home button.

### Setup and Usage (Linux)
-For keyboard emulation you only need to run `3DSController.py`.

-For Joystick emulation, first, install [python-uinput](https://github.com/tuomasjjrasanen/python-uinput). BEWARE: The latest release of this library as of the writing of this tutorial is 0.10.2 which is broken for most updated systems. Download the master branch directly.

Make sure that uinput module is running. You can do it from cosole like so: 
`sudo modprobe uinput`

Then, run `3DSController_gamepad.py` if you want to run it as a gamepad, and this would be it for most applications, but I've found that some games can't recognize the 3ds as a gamepad, if you encounter that use the following:

* Using a tool like [gamepadtool](http://generalarcade.com/gamepadtool/) map the 3ds to a controller setting
* Export an enviroment variable with what you got with the previous tool, this can be the terminal where you plan to run the game from, or from lutris settings, for example:

`export SDL_GAMECONTROLLERCONFIG="00000000707974686f6e2d75696e7000,python-uinput,a:b1,b:b0,x:b3,y:b2,back:b6,start:b7,leftshoulder:b4,rightshoulder:b5,dpup:b11,dpdown:b12,dpleft:b13,dpright:b14,leftx:a0,lefty:a1,platform:Linux,"`

Where you replace the text after `export SDL_GAMECONTROLLERCONFIG=` with whatever you got from your configuration.
* If you want this setting to every sdl2 game, you could add your `export SDL_GAMECONTROLLERCONFIG=` line to the end of `~/.xprofile` file, that way it'll be applied on boot (so it won't apply until you reboot).

May work on OS X too, but this is not tested.

### Configuration
Find the line `Port: 8889` and change it to your desired port, do this for both the 3DS's `3DSController.ini` and the PC's `3DSController.ini`.

To use custom key bindings, just change the PC's `3DSController.ini` file, it should be straight forward.

### Configuration (Linux)
The configuration for the keyboard emulation is in `3DSController.py`, not the INI.

The configuration for the joystick emulation is in `3DSController_gamepad.py`, not the INI.

### Troubleshooting
- Make sure that you are using the 3DS and PC application from the same release,
- Make sure your 3DS has internet access (turn on the switch on the side of the 3DS so that an orange light shows) and is on the same network as your PC,
- Make sure that the `3DSController.ini` is in the root of your 3DS's SD card (not flashcard micro SD),
- Make sure that the `3DSController.ini` has the local IP of your computer, not your public IP,
- Make sure your firewall isn't blocking the application,
- Try using a different port (change the port for both the 3DS and PC's .ini file),
