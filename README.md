## Getting started with Streamlabs Desktop



## Have updated drivers and software

Always have up-to-date software and drivers of your hardware if you encounter any issues.

Especially make sure your video drivers are up to date to the latest version.



[![](http://img.youtube.com/vi/d--1z_W9IVw/0.jpg)](http://www.youtube.com/watch?v=d--1z_W9IVw "How to Download, Install, and Go Live with Streamlabs Desktop | Streamlabs Desktop Tutorial")


# Streamlabs Desktop Issues and Solutions

- Backups > Always make backups during beta testing! Settings > Scene Collections > Export
- User Data > User data can be found in `%appdata%\slobs-client`


## Install Visual C++ Redistributable

Streamlabs Desktop requires some additional files (Visual C++ 2017 Redistributables) that might not be currently installed on your system. Please download and run **both** of these Microsoft Visual C++ 2017 redistributables. **Restart** your computer after installing this.

- [Visual C++ 2017 Redistributable [64bit]](https://aka.ms/vs/15/release/vc_redist.x64.exe)
- [Visual C++ 2017 Redistributable [32bit]](https://aka.ms/vs/15/release/vc_redist.x86.exe)

*Both the 32 bit and 64 bit versions should be installed, even if you have a 64 bit version of Windows.*


## Cannot maximize/open Streamlabs Desktop from taskbar*

If your Streamlabs Desktop is open but you are unable to see the window, but it is on the taskbar where you see a preview of the window please select the program so it is highlighted on the taskbar. Then you press `left alt`+`spacebar`. This should open a context menu on the top-left of your screen, where you select `Maximize`.

If that did not work you could try selecting Streamlabs OBS in the task bar and use `winlogo`+`shift` and use the `left/right arrow key` to try moving the window to another screen.

## Streamlabs Desktop is stuck maximized*

Close Streamlabs Desktop and navigate to `%appdata%\slobs-client` in Windows (by Search, winlogo+r, or in Explorer address bar) and in here delete the file `window-state.json` and start Streamlabs OBS again.

If you are having issues navigating to the folder, in Streamlabs Desktop settings, click `Show Cache Directory` and open the `slobs-client` folder found in the folder that opens.

## Game optimized encoder settings

The game-aware optimized encoder settings can be enabled before you go live when you have "Confirm stream title and game before going live" enabled. When available you can then enable the "Use optimized encoder settings" which then applies the optimized game-specific encoding settings when you go live.

*Using this, will override the set preset and any custom x264 flags you have set, with the machine learned values.*

A list of optimized games can be [found here](https://github.com/StreamlabsSupport/Streamlabs-OBS/wiki/List-of-Games-for-the-Video-Encoding-Optimization) and if the game is not on the list, generic optimization settings will be applied specific for gameplay footage so you will always get better results.

## Streamlabs Desktop crashes during startup

> Do not try to run Streamlabs Desktop on a Mac(book) with bootcamp or on macOS with Wine. These are currently not supported and we cannot provide any assistance with this. Most likely the cause for Bootcamp users is the lack of proper updated video drivers, and for Wine it would be vital required components.

- Reboot your computer.
- Try starting Streamlabs Desktop as administrator.
- Update your video drivers and other hardware drivers/software (reboot after updating).
- Install [Windows C++ Redistributable](#install-visual-c-redistributable)
- [Download](http://streamlabs.com/slobs) latest installer and run this as administrator while any AV is disabled temorarily.
- Add `%appdata%\slobs-client` directory to your Anti-Virus whitelist to not scan/block there.

> If you are still having the issue you could try to clear the user data of Streamlabs Desktop and see if that could resolve the issue with starting up. Do keep in mind by doing so you are deleting user data and you need to login, redo your settings and potentially re-adjust your scenes and scene collections depending on the cloud recovery.

- Make sure Streamlabs Desktop is closed and not running in the background in task manager.
- Navigate to `%appdata%` in Windows (winlogo+r or search).
- Delete or rename (to keep a backup) `slobs-client` that is found here.
- Try starting Streamlabs Desktop again (as administrator)

## If you are on Windows 7 please do the following if experiencing crashing issues when launching Streamlabs Desktop

Please enable Aero on Windows 7:
1. Close Streamlabs Desktop and then select an Aero Theme
        Note: pick this default theme if you do not know which one to pick: https://prnt.sc/nhhh9s
2. If Aero is ON (check this screenshot to verify: https://prnt.sc/nhhhdp) then simply run Streamlabs OBS but if not please continue to the next step
3. Make sure Streamlabs Desktop is closed and that an Aero Theme is selected then search for cmd in windows search bar & run it as admin. 
4. Enter two lines of command, first type net stop uxsms hit enter and let it process (few secs) then type net start uxsms and hit enter again. 
4. Aero should now be on and you can open Streamlabs OBS again. Refer to this screenshot to ensure that it is on: https://prnt.sc/nhhhdp

## Streamlabs Desktop randomly crashes during streaming

1. Update your video drivers and other hardware drivers/software.
2. Install [Windows C++ Redistributable](#install-visual-c-redistributable)
3. Try running Streamlabs Desktop as administrator.
4. [Disable 3rd party in-game overlays](#game-crashes-or-drops-fps-while-trying-to-capture-with-streamlabs-obs)

## Streamlabs Desktop crashes when switching scene collections when using a stinger transition

This is due to Streamlabs Desktop trying to fire a stinger transition when switching scene collections. This happens if the scene collections were originally duplicated at some point. We have two solutions here until it is fixed. 
 
1) Delete the scene collection that was duplicated and set it up fresh. You can copy and paste your sources just make sure you do not use the duplicate scene collection option. 
2) If you do not want to do the first option you can disable the stinger transition in the meantime which will stop the crash occuring. 

## Stream goes offline when switching scenes (0kbps bug)

If you are still experiencing the issue where the encoder fails when switching scenes you will need to open the transition menu and add a new transition of any type. Once you have done this simply deleting the previous transition should resolve the issue.
Gif of how to do this:
[![Gif of how to do this](https://i.gyazo.com/14ccc8352f365ab4ba6915578f8fc3be.gif)](https://gyazo.com/14ccc8352f365ab4ba6915578f8fc3be)


## Game crashes or drops FPS while trying to capture with Streamlabs Desktop

In some cases using 3rd party in-game overlays could cause additional FPS drop or instabilities, especially when you have multiple. If you ever encounter any issues, try disabling them and see if that would increase your performance or stability. A few examples of 3rd party software providing in-game overlays that you can disable if needed;
- Nvidia GeForce Experience In-Game Overlay
    - Settings (top-right gear icon) -> General -> In-Game Overlay switch.
- Discord In-Game Overlay
    - User Settings (bottom-left gear icon) -> Overlay -> Enable in-game overlay switch.
- Steam/UPlay/Origin In-Game Overlay

If you are using Windows 10, make sure that in Windows Settings you have disabled at least the `Game DVR` feature, and you can also try to disable the `Game Bar` features but this can cause issues with certain Windows Store games and applications if they are using this. You can find these options via the Windows 10 new settings panel -> Gaming.

Furthermore, try to limit the frames output by the GPU with the likes of V-Sync, G-Sync or Free-sync to the monitors refresh rate, as rendering more frames is a waste of resources if this is causing issues while capturing the game. You could even play and limit the games to 120FPS by using 120Hz as monitor refresh rate, as this is a nice number to be divided to 30 and 60fps for streaming!

If you do encounter issues while having G-Sync enabled, try disabling G-Sync first to see if that helps and keep it disabled for further troubleshooting the issue.


## Capture Not Working (Black Screen)

* Delete the capture source, restart Streamlabs Desktop as administrator, and re-add source.
    - Right click the shortcut on your desktop and select `Run as Administrator`.
* Have Streamlabs Desktop installed in Program Files (default install location).
    - Some games and Windows Store games, like Sea of Thieves, need this due to given additional permissions.
* Use `Capture Specific Window` or `Capture foreground window with hotkey` to force the capture to the game.
* Try toggling the Anti-cheat hook on or off.

* [Disable 3rd party in-game overlays](#game-crashes-or-drops-fps-while-trying-to-capture-with-streamlabs-obs)
* [Install Visual C++ Redistributable](#install-visual-c-redistributable)
* [Have updated drivers and software](#have-updated-drivers-and-software)

* If that did not help, adjust in-game settings to borderless fullscreen instead of (exclusive) fullscreen if used or try a window capture then instead (while using borderless fullscreen). Some games are also impossible to capture with a game capture.

### Display capture not working for Nvidia notebook users

First disable **Force GPU as render device** in `Settings > Advanced (Video section)` https://prnt.sc/mzzm1s and restart Streamlabs Desktop. If that does not resolve the display capture issue then also do the following;

1.   Have Streamlabs Desktop shortcut on your desktop, if not add it.
2.   Right-click the `Streamlabs Desktop` shortcut and select `Run with graphics processor -> Integrated graphics`.
        - https://prnt.sc/kwyv9x

> If you cannot find the option Run with graphics processor in the context menu then follow the following extra steps.

1. Open up the `Nvidia Control Panel`.
      - Normally found by right-clicking on the desktop if added to the context menu.
      - Can be found in the system `Control Panel -> Appearance and Personalization`.
2. Select `Desktop` in the menu bar.
3. Enable `Add "Run with graphics processor" to Context Menu` option.

> If you receive an error saying you do not have the privilege to select the graphics processor in this menu: Right click Streamlabs Desktop > Properties > Compatability > Untick "Always run as admin" > http://prntscr.com/kzh8as

### AMD/ATI Notebeook users with latest Windows 10 April 2018 (1803) update

First disable **Force GPU as render device** in `Settings > Advanced (Video section)` https://prnt.sc/mzzm1s and restart Streamlabs OBS. If that does not resolve the display capture issue then also do the following;

1. Open Windows 10 settings
2. Select `System`
3. Select `Graphic settings` (found at the bottom of the Display settings page).
    - This is in the `Display` settings that should be selected by default.
4. Select `Classic app` and browse to the Streamlabs OBS executable.
    - Default location: `C:\Program Files\Streamlabs OBS\` > `Streamlabs OBS.exe`
5. Select the newly created Streamlabs Desktop and hit options.
6. Select `Power Saving Mode` and Save.

### Force Streamlabs Desktop To Use AMD Graphics Card

Open the AMD Catalyst Control Center app by right-clicking on an empty area on your desktop. Select ‘Catalyst Control Center’ from the context menu. From the list of panels on the left, select ‘Power’. Under ‘Power’, select ‘Switchable application graphics settings’.

Here you will see a list of apps that AMD already recognizes as needing better GPU support. On this panel is an ‘Add Application’ button. Click it and select the EXE of the app you want to force to use the AMD graphics card.

After you add the application, open the dropdown next to it for setting graphics options. Select ‘High performance’ and you’re done. The app will always use AMD graphics card.

We should mention that some options may differ depending on your driver version and the GPU model you have. These solutions will still work but the options may be found under a different menu.


## Not capturing desktop audio

1) Make sure the audio source is not muted in the mixer on Streamlabs Desktop.

2) Some audio management software, like `Nahimic 2`, `Sonic studio sound` or motherboard audio software like `Realtek HD Audio Manager` or `Sound Blaster Recon` are known to cause issues. Try closing that kind of software, and also check Windows taskmanager if any processes with a similar name are running to be closed. If this doesn't work, try going in to your Windows Playback Devices in your Windows Audio Settings, right click on the sound device you are using and click on Properties, then go to the Advanced Tab and uncheck the box that says "Give exclusive mode applications priority" and that should resolve it.

3) Select manually the desktop audio device (audio settings), you use as default device in Windows Sound, not setting it to default. Alternatively you can set it to disabled and add in the scene you want desktop audio an `Audio Output Capture` and select the device that is set as default device in Windows Sound. 

4) Install [Windows C++ Redistributable](#install-visual-c-redistributable)

5) As last resort, you can temporary use an alternative program to capture audio like `VoiceMeeter Banana`. This program allows you to set it as default device, and then use a *virtual audio cable* into Streamlabs Desktop to capture the desktop audio. You can find various guides on the internet and YouTube. 


## Not going live on the service

1. Log out from Streamlabs Desktop, restart the application as administrator and log back in. If using Twitch ensure your not running a rerun of a previous stream as this will prevent you going live. If you are simply end it and hit go live again.  
2. Double check your stream key if this is still correct.
3. If using Advanced Output Mode and using NVENC/AMD make sure GPU is set to `0`.
4. Install [Windows C++ Redistributable](#install-visual-c-redistributable)
5. If signed into Streamlabs Desktop with Twitch you can run the auto-optimizer found in General Settings.  

If this did not work either or get the following error;
> Invalid Path or Connection URL. Please check your settings to confirm that they are valid.

1. Go to `Stream` in Settings and select a **different** service than you want to use.
2. Select the streaming service you want to use again, this reloads the available servers.
3. Select the server you want to use (**do not use auto**)
5. Try going live again.

If this did not work either or get the following error;
> Failed to connect to the streaming server. Please check your internet connection.

1. Go to Settings > Advanced and scroll down to the Bind to IP option. Change it from Default to your local machines.
    - Default local IP address begin with 192.168.x.x or 10.0.x.x
    - You can use `ipconfig /all` in command prompt (cmd.exe) to see to PC's local IP address.
2. Try going live again.

If none of these steps work, reach out to our support team in our discord discord.gg/stream     


## Recording is not working or saved

> No errors, but no recording file created.

- Install [Windows C++ Redistributable](#install-visual-c-redistributable)
- Have up-to-date video drivers of your graphics card

> Error; An unexpected error occured:

- Install [Windows C++ Redistributable](#install-visual-c-redistributable)

> Error; An unexpected error occurred: Unable to write to. Make sure you're using a recording path which your user account is allowed and that there is sufficient disk space.


## Recording + Streaming Performance Issues

If you have performance issues while streaming and recording, check if you are not using twice of the same encoder, like x264 or NVENC for both streaming and recording. For best performance use either x264 or NVENC/AMD for streaming and then record 'same as stream' (only available in simple output mode at the moment). For better quality recordings and having enough system resources, use x264 as stream encoder and NVENC/AMD as recording encoder.


## Modifier Keys and Mouse Buttons as Hotkey

Mouse bindings and certain modifier keys are not yet supported to be used as hotkey.


## Razer Ripsaw & Avermedia LGP

For the Razer Ripsaw, try to select `HDMI + Aux` as audio input for the HDMI video input which you can find via configure device. If this does not work, try the following down below;


## High CPU usage in Idle

> Ensure that you have updated Windows 10 to it's latest patch.

- Make sure all drivers are up-to-date and are matching 64-bit versions of your system.
- Almost every source you use, uses CPU to be functioning properly. The more you have the higher the total CPU usage would be.
- Downloaded animated overlays can cause high CPU usage due to the webm video files used as overlays.
- Using many different browser sources can cause high CPU usage, try limiting them or create references.
- You can delete Streamlabs Desktop browser source cache that can cause high CPU usage;
    1. Navigate (or winlogo + r) in Windows to `%appdata%\slobs-client\plugin_config\obs-browser`
    2. Delete `Cache`
    3. Start Streamlabs Desktop again

> Enabling Performance mode in Streamlabs Desktop will help reduce load on the GPU/CPU slightly. This can be done by right clicking on the preview and selecting "Performance Mode"


## I cannot find the side-dock with chat

The side-dock with chat can only be shown when the total width of Streamlabs Desktop is 1100px or greater. So monitors that have a horizontal resolution less than that (or you are using portrait, causing this) chat is currently unavailable. If the total width of Streamlabs OBS does meet this criteria you'll see a thin bar either on the left or right (depending on your appearance settings) to slide open the dock.


## Set side-dock with the chat to left side

In Settings > Appearance you can checkmark `Show the live dock (chat) on the left side`.




## Stream is losing frames

These issues are most likely caused by overloading either the GPU and CPU. At all times keep and eye out for both the total CPU and GPU usage in Windows task manager (if you do not have GPU in Windows 10, update to the latest major update). Some games are known to be broken and like to use all available CPU or GPU resources and cause issues for streaming software.

- Lagged Frames; Compositor overloaded, commonly high GPU usage.
- Skipped Frames; Encoder overloaded, commonly high CPU usage on x264.
- Dropped Frames; Network issues, try other servers or restart equipment.

> By default 'Detect lagged frames' notification is disabled by Streamlabs OBS. For troubleshooting please enable this via `Settings -> Notifications` and set the thresholds of the three to 10%.

[![](http://img.youtube.com/vi/WnRhaZaQ2ns/0.jpg)](http://www.youtube.com/watch?v=WnRhaZaQ2ns "A Streamers' Quick Guide To Frame Management")


### Lagged frames

IF you are getting **lagged frames** or the game is having slow FPS then  your GPU is being overloaded. Lower the graphics quality in-game so streaming software gets more breathing room to compose the frames for the encoder. You can also limit the FPS or use v-sync. One could even consider locking to 120FPS as this is a nice /2 division for 60FPS and /4 division for 30FPS streaming. You can also enable V-sync to lock the FPS if availble. If you are using G-Sync you can try disabling this and see if that would help.

In addition you can try the [following few steps](https://github.com/StreamlabsSupport/Streamlabs-OBS#game-crashes-or-drops-fps-while-trying-to-capture-with-streamlabs-obs)  as well to further optimize your system for streaming.

Regardless of software or hardware encoding selection, streaming software requires shared GPU to compose the frames (combine sources) for the encoder to encode.


### Skipped frames

If you are using software (x264) encoding and are running into high CPU usage issues, causing **skipped frames**, consider using a faster preset or start using hardware encoding (NVENC/AMD) as that wont load the CPU extra to encode the stream.


### Dropped frames

If you are having **dropped frames** this is most likely the network/internet connection to the selected server. Try selecting the closest Twitch server manually (not auto), and if already done so, try another (like 2nd closest) server. You can also try to restart your local network gear (modem, router, and switches) and see if that helps.

In addition to the **dropped frames**, make also sure the video + audio bitrate is not exceeding or is getting close to your internet upload speed. Having other users on same network using upload (like cloud storage) will lower the throughput of the upload.

If you are using Twitch you can test various Twitch servers with this with [this tool](https://r1ch.net/projects/twitchtest), as your ISP routing can be messed up as well. 
