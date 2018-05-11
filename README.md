# Streamlabs OBS Issues and Solutions

- Roadmap > [found on Trello](https://trello.com/b/oTl4KiBW/streamlabs-obs-roadmap)
- Backups > Always make backups during beta testing! Settings > Overlays > Export
- User Data > User data can be found in `%appdata%\slobs-client`
- New Issues > Please report any issues on our [tracker](http://tracker.streamlabs.com)

## How do I report any issues

You can submit issue you have our [Streamlabs OBS Tracker](http://tracker.streamlabs.com/) Also please `Upload cache to Developers` found in General Settings and include the filename of the cache, that got copied to your clipboard by doing so, in the issue.

## Have updated drivers and software

Always have up-to-date software and drivers of your hardware if you encounter any issues. Especially make sure your video drivers are up to date to the latest version.

## Install Visual C++ Redistributable

Please install [Visual C++ 2015](https://www.microsoft.com/en-us/download/details.aspx?id=52685) and [Visual C++ 2017](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads) redistributable (both x86 and x64) on your system that might solve some of the issues you are having.

## Streamlabs OBS crashes when using projector mode

This is a known issue with the latest GeForce Nvidia `397.31` driver. Developers are working to resolve it as soon as possible.

## Cannot maximize/open Streamlabs OBS from taskbar

If your Streamlabs OBS is open but you are unable to see the window, but it is on the taskbar where you see a preview of the window please select the program so it is highlighted on the taskbar. Then you press `left alt` and `spacebar`. This should open a context menu on the top-left of your screen, where you select `Maximize`.

## Update is stuck at 100%

Redownload Streamlabs OBS from [https://streamlabs.com/slobs](https://streamlabs.com/slobs) and run the installer as administrator. There should be no need to uninstall or delete any data prior doing so.

## Game optimized encoder settings

The game optimized encoder settings is currently only available when using **software (x264)** encoding and using **Twitch** as streaming service. If you use both, you can then enable the **use optimized encoder settings** found in the *Go Live* pop-up, where you set your Game and Title. The profile selection is only in effect when **Use optimized encoder settings** is enabled.

*Using this, will override the set preset and any custom x264 flags you have set, with the machine learned values.*

- **Medium profile**; CPU usage is equivalent to x264 profile **veryfast** but optimized for gameplay.
- **Low profile**; CPU usage is equivalent to x264 profile **ultrafast** but optimized for gameplay.

If you use a dedicated stream PC to encode or you have a powerful single PC that manages to go slower than veryfast, for example medium, it would not be best to use the optimized encoder settings, as no higher profile exists at this moment.

If you do not see the pop-up to set the game or title, make sure that **Confirm stream title and game before going live** is set found in the General Settings.

## Streamlabs OBS crashes during startup

> Do not try to run Streamlabs OBS on a Mac(book) with bootcamp or on macOS with Wine. These are currently not supported and we cannot provide any assistance with this. Most likely the cause for Bootcamp users is the lack of proper updated video drivers, and for Wine it would be vital required components.

- Reboot your computer.
- Try starting Streamlabs OBS as administrator.
- Update your video drivers and other hardware drivers/software (reboot after updating).
- Install [Windows C++ Redistributable](https://github.com/ocgineer/Streamlabs-OBS-Solutions#install-visual-c-redistributable)
- [Download](http://streamlabs.com/slobs) latest installer and run this as administrator while any AV is disabled temorarily.
- Add `%appdata%\slobs-client` directory to your Anti-Virus whitelist to not scan/block there.

> If you are still having the issue you could try to clear the user data of Streamlabs OBS and see if that could resolve the issue with starting up. Do keep in mind by doing so you are deleting user data and you need to login, redo your settings and potentially re-adjust your scenes and scene collections depending on the cloud recovery. **Not recommended but only used as last resort.**

- Make sure Streamlabs OBS is closed and not running in the background in task manager.
- Navigate to `%appdata%` in Windows explorer.
- Rename `slobs-client` to `_slobs-client` found here.
- Start Streamlabs OBS and close it again (without logging in).
- Copy the folders `Overlays` and `SceneCollections` from `_slobs-client` to `slobs-client`.
- Start Streamlabs OBS again and log in.
- Redo the settings as these are not recovered.

> If this renaming of slobs-client in %appdata% has solved your issue could you please zip up `_slobs-client` and host it on Dropbox or something alike, and DM the link on Discord to `Ocgineer#0042` with the initial issue for further investigation.

## Streamlabs OBS randomly crashes during streaming

1. Update your video drivers and other hardware drivers/software.
2. Install [Windows C++ Redistributable](https://github.com/ocgineer/Streamlabs-OBS-Solutions#install-visual-c-redistributable)
3. Try running Streamlabs OBS as administrator.
4. [Disable or uninstall GeForce Experience](#game-crashes-or-drops-fps-while-trying-to-capture-with-streamlabs-obs)

## Game crashes or drops FPS while trying to capture with Streamlabs OBS

If you are using GeForce Experience please disable the `IN-GAME OVERLAY` and `Instant Replay` feature or uninstall Experience completely. Some games can crash or have lower FPS when Streamlabs OBS as trying to capture game footage when GeForece Experience features are enabled and disabling or uninstalling might solve your issue.

If you are using Windows 10, make sure that in Windows Settings you have disabled at least the `Game DVR` feature, and you can also try to disable the `Game Bar` features but this can cause issues with certain Windows Store games and applications if they are using this. You can find these options via the Windows 10 new settings panel -> Gaming.

Furthermore, try to limit the frames output by the GPU with the likes of V-Sync, G-Sync or Free-sync to the monitors refresh rate, as rendering more frames is a waste of resources if this is causing issues while capturing the game. You could even play and limit the games to 120FPS by using 120Hz as monitor refresh rate, as this is a nice number to be divided to 30 and 60fps for streaming!

If you have sudden FPS issues capturing a DirectX 9 game after the latest major Windows 10 update then you could try to use the [temporary fix for D3D9 games](#directx-9-d3d9-games-on-latest-windows-10-april-2018-1803-update).

## Capture Not Working (Black Screen)

* Run Streamlabs OBS as Administrator.
* Run both Streamlabs OBS and the game as Administrator.
* Havve Streamlabs OBS installed in Program Files (default install location).
    - Some games and Windows Store games, like Sea of Thieves, need this due to given additional permissions.
* Use `Capture Specific Window` mode if using Game Capture and/or toggle anti-cheat hook.

* [Disable or uninstall GeForce Experience](#game-crashes-or-drops-fps-while-trying-to-capture-with-streamlabs-obs)
* [Install Visual C++ Redistributable](#install-visual-c-redistributable)
* [Have updated drivers and software](#have-updated-drivers-and-software)

### DirectX 9 (D3D9) Games on latest Windows 10 April 2018 (1803) update

There is a current known issue due to the latest Windows 10 update that might prevent you from properly capturing DirectX 9 games and the following solution is a temporary solution untill a permament fix has been build in.

1. Close Streamlabs OBS
2. Download [get-graphics-offsets-win10-1803-signed](https://obsproject.com/temp/get-graphics-offsets-win10-1803-signed.zip).
3. Extract the contents (both files) to `C:\Program Files\Streamlabs OBS\resources\app.asar.unpacked\node_modules\obs-studio-node\libobs\data\obs-plugins\win-capture`
    - If done correct, it should ask you to overwrite two files and might need administrative permissions.
    - This is the path of the default installed location, adjust accordingly if needed.
4. Start Streamlabs OBS

### Notebook users on latest Windows 10 April 2018 (1803) update

1. Open Windows 10 settings
2. Select `System`
3. Select `Graphic settings` (found at the bottom of the settings page)
    - This is in the `Display` settings that should be selected by default.
4. Select `Classic app` and browse to the Streamlabs OBS executable.
    - Default location: `C:\Program Files\Streamlabs OBS\` > `Streamlabs OBS.exe`
5. Select the newly created Streamlabs OBS and hit options.
6. Select `High Performance` and Save.

### Notebook users prior Windows 10 April 2018 (1803) update and Windows 7/8

1. Open up the **Nvidia Control Panel**.
    - Normally found by right-clicking on the desktop.
    - Can be found in the system Control Panel -> Appearance and Personalization.
2. Select **Desktop** in the menu bar.
3. Enable **Add Desktop Context Menu** option.
4. Right click **Streamlabs OBS shortcut** -> Run with graphics processor -> High Performance NVIDIA Processor .

## Not capturing desktop audio

1) Some audio management software, like `Nahimic 2`, `Sonic studio sound` or motherboard audio software like `Realtek HD Audio Manager` or `Sound Blaster Recon` are known to cause issues. Try closing that kind of software, and also check Windows taskmanager if any processes with a similar name are running to be closed. If this doesn't work, try going in to your Windows Playback Devices in your Windows Audio Settings, right click on the sound device you are using and click on Properties, then go to the Advanced Tab and uncheck the box that says "Give exclusive mode applications priority" and that should resolve it.

2) Select manually the desktop audio device (audio settings), you use as default device in Windows Sound, not setting it to default. Alternatively you can set it to disabled and add in the scene you want desktop audio an `Audio Output Capture` and select the device that is set as default device in Windows Sound. 

3) Install [Windows C++ Redistributable](https://github.com/ocgineer/Streamlabs-OBS-Solutions#install-visual-c-redistributable)

4) Rename the executable name of Streamlabs OBS from `Streamlabs OBS.exe` to `obs64.exe`. You can find the executable on the installed location, which by default is `c:\program files\streamlabs obs\`.

5) As last resort, you can temporary use an alternative program to capture audio like `VoiceMeeter Banana`. This program allows you to set it as default device, and then use a *virtual audio cable* into Streamlabs OBS to capture the desktop audio. You can find various guides on the internet (like [this one](http://www.ocgineer.com/audio.html)) or Youtube. 

## Not going live on the service

1. Log out from SLOBS, restart the application as administrator and log back in.
2. You can also double check your stream key if this is still correct.
3. Install [Windows C++ Redistributable](https://github.com/ocgineer/Streamlabs-OBS-Solutions#install-visual-c-redistributable)

If you are using NVENC/AMD encoding;

1. Go to `Settings > Output` and set output mode to advanced.
2. Check if GPU is properly set to 0.
3. Go back to simple output mode.

If this did not work either try the following;

1. Go to `Stream` in settings and select a **different** service than you want to use.
2. Go to `Stream` in settings and select the service again you want to use.
3. Select a different server, and then the server you want to use (**do not use auto**)
4. Restart Streamlabs OBS.
5. Try going live.

If all the steps above did not work please [report the issue on our tracker](https://github.com/ocgineer/Streamlabs-OBS-Solutions#how-do-i-report-any-issues) (**please do so for bug fixing**) so the developers can investigate this issue and create a possible fix for this to prevent this from happening in the future.

After you have done so, make a backup of your overlay scene collection (Settings > Overlays > Export) even though cloud recovery should record your scene, it never hurts to have a backup if that also failed for some reason. Then `Clear Cache and Restart` found in Settings. This will **wipe** all user data, including scenes and settings, but after logging in the cloud recovery should recover your scenes. You need to redo your settings but this could fix the not going live issue.

## Recording is not working or saved

> Not Saving any files

- Install [Windows C++ Redistributable](https://github.com/ocgineer/Streamlabs-OBS-Solutions#install-visual-c-redistributable)
- Use anything else except lossless quality
    - If used this, set to another quality and then restart the application

> Failed to connect to the streaming server. Please check your internet connection.

- Do not use custom FFMPEG
    - Advanced Output Settings -> Recording -> Type

> An unexpected error occurred: Unable to write to. Make sure you're using a recording path which your user account is allowed and that there is sufficient disk space.

- Do not use Replay buffer (not functional anyway)
    - Simple Output settings -> Recording (at the bottom)

> Performance Issues while streaming and recording.

If you have performance issues while streaming and recording, check if you are not using twice of the same encoder, like x264 or NVENC for both streaming and recording. For best performance use either x264 or NVENC/AMD for streaming and then record 'same as stream' (only available in simple output mode at the moment). For better quality recordings and having enough system resources, use x264 as stream encoder and NVENC/AMD as recording encoder.

## Modifier Keys and Mouse Buttons as Hotkey

Mouse bindings and certain modifier keys are not yet supported to be used as hotkey.

## Elgato HD60

### HD60 and HD60s

As of this moment when you are using `Elgato Game Capture HD` as video device the configure window will not correctly stay visible when trying to adjust some settings for these devices. If you are in need to adjust these settings, to for example, setup the analog audio inputs then you could try the e following;

Close Streamlabs OBS and open OBS Studio. Add a new capture device and select the `Elgato Game Capture HD` as device and select configure. Setup the settings you want for your stream. Then close the config, properties and OBS Studio. Now if you open Streamlabs OBS the settings should be still set, unless you unplugged the USB device or rebooted your computer.

### HD60 Pro and HD60 4K Pro

If you are using the `Elgato Game Capture HD` as video device, which is a software device installed when installing the Elgato Game Capture HD software. As of this moment the configure window does not work with this device in Streamlabs OBS, but this device is able to output the captured audio normally to the desktop audio. The downside is that you cannot control the captured audio level as the configure panel does not work at the moment, and the audio is routed outside Streamlabs OBS directly onto your Desktop Audio.

If you need to use the configure window make sure your Video Capture Device is set to `Game Capture HD60 (Video) (#01)` as this is the native video device [drivers of the capture card](https://help.elgato.com/customer/portal/articles/2405414-elgato-gaming-hardware-drivers) but are also included when installing the Elgato Game Capture HD software.

*This device driver is only available when you use the internal PCIe capture card and is unable to output the captured audio to the desktop audio for you to hear yourself, unless you use monitoring.*

If you also need **to control the volume** and/or **have the need to listen to the audio**, then you can monitor the audio via the selected monitoring device. To enable this you click the gear icon above the mixer and set the Audio Monitoring to `Monitor and Output`. The monitor device used can be found in Settings -> Advanced.

## Razer Ripsaw & Avermedia LGP

For the Razer Ripsaw, try to select `HDMI + Aux` as audio input for the HDMI video input which you can find via configure device. If this does not work, try the following down below;

As of this moment users are able to successfully capture audio from the Razer Ripsaw by renaming the Streamlabs OBS executable to that of OBS Studio. Rename the executable name of Streamlabs OBS from `Streamlabs OBS.exe` to `obs64.exe`, found in installed location, which by default is `c:\program files\streamlabs obs\`.

## High CPU usage in Idle

> Ensure that you have updated Windows 10 to it's latest patch.

- Make sure all drivers are up-to-date and are matching 64-bit versions of your system.
- Almost every source you use, uses CPU to be functioning properly. The more you have the higher the total CPU usage would be.
- Downloaded animated overlays can cause high CPU usage due to the webm video files used as overlays.
- Using many different browser sources can cause high CPU usage, try limiting them or create references.
- You can delete Streamlabs OBS browser source cache that can cause high CPU usage;
    1. Navigate (or winlogo + r) in Windows to `%appdata%\slobs-client\plugin_config\obs-browser`
    2. Delete `Cache`
    3. Start Streamlabs OBS again

> Enabling Performance mode in Streamlabs OBS will help reduce load on the GPU/CPU slightly. This can be done by right clicking on the preview and selecting "Performance Mode"

## I cannot find the side-dock with chat

The side-dock with chat can only be shown when the total width of Streamlabs OBS is 1100px or greater. So monitors that have a horizontal resolution less than that (or you are using landscape, causing this) chat is currently unavailable. If the total width of Streamlabs OBS does meet this criteria you'll see a thin bar either on the left or right (depending on your appearance settings) to slide open the dock.

## Set side-dock with the chat to left side

In Settings > Appearance you can checkmark `Show the live dock (chat) on the left side`.

## Unable to connect Streamlabs Mobile App Remote Control to Streamlabs OBS

1. Install the latest Streamlabs Mobile App from the [Google Play Store](https://play.google.com/store/apps/details?id=com.streamlabs)
2. Connect your device to the same local network Streamlabs OBS is on.
3. Allow Streamlabs OBS through firewall.
    - See [this FAQ; Allow streaming software through the Firewall](https://support.streamlabs.com/hc/en-us/articles/115000090014-Fix-broken-alerts)
4. Open Streamlabs OBS `Settings > Remote Control` and click to show the QR code
5. Ensure that the QR code is not cropped or obstructed (expand the popup window horizontally if needed) 
6. Scan the QR code with the QR scanner in the Streamlabs Mobile App (under Remote Control in the sidebar).

> If your camera is freezing when you try to scan the QR code try enabling `Use pre-L Camera API` found under `Settings -> Broadcast`.

## Mobile Device Having No or Broken Camera

> If you have a mobile Android device with a broken or no camera and would like to use it for the Streamlabs OBS Remote Control you can do the following few steps to connect your the Streamlabs: Livestreaming app to Streamlabs OBS.

1. Take a snapshot of the QR code and save this locally on your computer.
    - Windows 10 has build in `Snipping Tool` to snip a region and save.
    - You can use `winlogo`+`shift`+`s` to  take a snip of a region.
    - Other third party apps around can do the same.
2. Decode the saved QR code with a decoder like [this website](https://zxing.org/w/decode.jspx).
3. Copy the raw or parsed text and email the link to yourself.
4. Open the email on your mobile device and open the emailed link with Streamlabs application.

## Stream is losing frames

These issues are most likely caused by overloading either the GPU and CPU. At all times keep and eye out for both the total CPU and GPU usage in Windows task manager (if you do not have GPU in Windows 10, update to the latest major update). Some games are known to be broken and like to use all available CPU or GPU resources and cause issues for streaming software.

- Lagged Frames; Compositor overloaded, commonly high GPU usage.
- Skipped Frames; Encoder overloaded, commonly high CPU usage on x264.
- Dropped Frames; Network issues, try other servers or restart equipment.

If Streamlabs OBS does not give you any warnings but the game is still lagging, the CPU or GPU is still being overloaded for the game to run properly.

### Lagged frames

IF you are getting **lagged frames** or the game is having slow FPS then  your GPU is being overloaded. Lower the graphics quality in game so streaming software gets more breathing room to compose the frames for the encoder. You can also limit the FPS or use v-sync. One could even consider locking to 120FPS (and 120Hz) as this is a nice /2 division for 60FPS and /4 division for 30FPS streaming.

Regardless of software or hardware encoding selection, streaming software requires shared GPU to compose the frames (combine sources) for the encoder to encode.

> Ensure that you in game FPS is not exceeding your monitors refresh rate. Enabling V-Sync in game will help resolve this issue

### Skipped frames

If you are using software (x264) encoding and are running into high CPU usage issues, causing **skipped frames**, consider using a faster preset or start using hardware encoding (NVENC/AMD) as that wont load the CPU extra to encode the stream.

### Dropped frames

If you are having **dropped frames** this is most likely the network/internet connection to the selected server. Try selecting the closest Twitch server manually (not auto), and if already done so, try another (like 2nd closest) server. You can also try to restart your local network gear (modem, router, and switches) and see if that helps.

In addition to the **dropped frames**, make also sure the video + audio bitrate is not exceeding or is getting close to your internet upload speed. Having other users on same network using upload (like cloud storage) will lower the throughput of the upload.

If you are using Twitch you can test various Twitch servers with this with [this tool](https://r1ch.net/projects/twitchtest), as your ISP routing can be messed up as well. 

