# CamBot 6D for Star Citizen

**Six degrees of freedom spline interpolation with opentrack UDP-over-network output.**

CamBot 6D can remotely control the in-game camera position and orientation in all six degrees of freedom. Simply set individual waypoints and the software will move the in-game camera along a smooth path at a predefined speed.

You can also use CamBot 6D to split the advanced camera controls of Star Citizen between two real-time operators. One operator will control the camera angle around its pivot directly at the gaming PC (or control a character with fixed camera settings) while the other operator controls the relative camera position and orientation offsets remotely from a second computer.

# Features

![image_1](https://github.com//gulbrillo/CamBot-6D/blob/main/doc/cambot6d1.png?raw=true)

- Define an arbitrary camera path by setting waypoints.
- Set duration, ease and interpolation option for the spline path.  
  Spatial: `Linear` (hard corners) | `Quadratic` (smooth) | `Cubic` (relaxed)  
 Temporal: `Auto` (smooth) | `Isochronous` (equal time to travel between pair of waypoints) | `Manual` (define times for each individual segmet)
- Delete or edit individual waypoints.
- Skip between points on demand to create individual timings that fit your scene.

![image_1](https://github.com//gulbrillo/CamBot-6D/blob/main/doc/cambot6d2.png?raw=true)

- Compatible with keyboard/mouse, 6-axis SpaceMouse, and Xbox Controller.
- Save individual inversion and motion settings per input device.
- X/Y translation options:  
  `Absolute` WASD navigates along coordinates set by initial camera orientation | `Relative` WASD navigates relative to current camera orientation

![image_1](https://github.com//gulbrillo/CamBot-6D/blob/main/doc/cambot6d3.png?raw=true)

- Hot key to bring CamBot 6D GUI to the foreground
- Voice output for audio feedback when waypoints are set or deleted, countdowns, and error messages
- MQTT client to connect GUI features to a Stream Deck or other smart home devices
- Dual PC option: use a second Windows PC in the same network to control the Star Citizen camera remotely

# Limitations

- **Camera offset limited to ±2 meters in X,Y,Z directions**  
  This is a limitation of 3rd person camera head tracking controls in Star Citizen and cannot be circumvented.

# Dokumentation

A full walkthough of how to use CamBot 6D is on my website:

https://www.lordskippy.com/software/virtual-camera-robot

# Dependencies

### Requirements:

- **Star Citizen**: https://robertsspaceindustries.com/enlist?referral=STAR-F3GJ-MFBD
- If you use TrackIR head tracking, terminate the TrackIR v5 Windows app before using CamBot 6D

### Optional:

- **3Dconnexion SpaceMouse** (Enterprise, Pro, or Compact) for full analog 6 axis control
- **Microsoft Xbox Controller** (Series X, Series S, or One) for analog 5 axis control (digital control for roll)  
  if you use CamBot 6D on your gaming PC, 
- **Elgato Stream Deck** with [MQTT plugin](https://apps.elgato.com/plugins/com.bi0s.mqtt)  
  requires an MQTT message broker such as [Eclipse Mosquitto](https://mosquitto.org/) to communicate

# Changelog

Initial pre-release.

# Builds

We are in early testing. Alpha builds for Windows are available here:  

https://github.com/gulbrillo/CamBot-6D/releases

# Run

Requires Python 3.10 or higher.

> python3.10.exe .\CamBot6D.py

# Compile

Spec file is provided. This will create a one file executable `CamBot6D.exe` in `./dist`. 
> python3.10.exe -m PyInstaller CamBot6D.spec

The spec file can be created with
> python3.10.exe -m PyInstaller --noconsole --onefile --windowed --icon=icon.ico --add-data "./images;images" CamBot6D.py

But you need to replace the `datas` line in `CamBot6D.spec` with this:
> datas=[('./images', 'images'),('./icons', 'icons'),('./fonts', 'fonts')],

# Acknowledgements

This is an unofficial Star Citizen fansite, not affiliated with the Cloud Imperium group of companies. All content on this site not authored by its host or users are property of their respective owners.

User interface based on [Simple_PySide_Base](https://github.com/Wanderson-Magalhaes/Simple_PySide_Base) and [Render_Time_Calculator](https://github.com/Wanderson-Magalhaes/Render_Time_Calculator) by Wanderson M. Pimenta.

TrackIR communication based on [opentrack's](https://github.com/opentrack/opentrack) implementation of the [FreeTrack protocol](https://github.com/opentrack/opentrack/tree/master/proto-ft).
