# Little tricks

## Initial launch

1. Wire the headset.
2. Run the register.sh file in the SteamVR-OpenHMD directory.
3. Launch steam using the steam command in a terminal.
4. Launch SteamVR using the steam GUI.
  * Be sure the application is sent to the headset.
  * If not, just shut down the SteamVR software et launch it again.
5. At this point you should see the Steam-Home in the headset.
6. Run the **paraview** you just built.
7. Load the OpenVR module with the GUI in **Tools->Manage Plugins**
8. A new window should appear. Then press on the **Send to OpenVR** button.
9. Load a case.
10. Add all you  filters and do all needed modifications.
11. Press again the **Send to OpenVR** button.
12. You should be able te see your paraview case with the headset.

## Known causes of crashs

* Moving the camera mith the mouse. Just don't press you mouse buuton when your cursor is in the view window.

## Adding filters and doing some modifications

You should be able to do some modifications in you filters and add some to.
But still sometimes their it can "crash". (You will just see a black shape).
If so, just do all your modifications before **11.** or try the following : 

* Try to press again on **Send to OpenVR**
* Try to disable the visibility of your components. (By pressing the "eye" button).
* Try to disable the visibility of your components before doing any modifications.
* Try to launch a big calculation (for example by adding lots of streamlines) to force SteamVR to reload the home thing.
