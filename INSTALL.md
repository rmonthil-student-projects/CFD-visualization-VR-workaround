# Creating an VR CFD Vizualisation environnement on Linux, with the Oculus Rift.

## Installing

### Steam and SteamVR
)
The following instruction just resume the instructions found [here](https://blog.ybalrid.info/2018/03/20/install-and-run-steamvr-on-archlinux-for-using-an-htc-vive-and-do-opengl-openvr-developement/).
Just refer to that website in case of issues. 

* Download the steam official package and install it with its dependencies.
* Do not forget its a 32 bit software, you may need to adapte your system to install 32 bit softwares.
* Then download and install SteamVR using the steam GUI.
* With the steam GUI : enable the Beta Update option of the SteamVR software.

### HIDAPI

As a dependencie of OpenHMD, you will need to install HIDAPI first.
Just download the sources and follow instructions described [here](https://github.com/signal11/hidapi).
Do not forget to install the dependencies suggested in the README.

### SteamVR - OpenHMD

Just download the sources and follow what is described [here](https://github.com/ChristophHaag/SteamVR-OpenHMD).
It should include OpenHMD.

You may need to set Udev Rules as described [here](https://github.com/OpenHMD/OpenHMD/wiki/Udev-rules-list).

Be sure to read ALL the README.md file and to create a $HOME/.ohmd_config.txt file with the correct values.

### OpenVR

As a dependencie for the OpenVR plugin, just download the sources [here](https://github.com/ValveSoftware/openvr.git).

### Building and Installing Paraview with OpenVR

The following instructions were build using the instruction found [here](https://www.paraview.org/Wiki/ParaView:Build_And_Install).

Before begining be sure to have all dependencies described in the [build and instllation page](https://www.paraview.org/Wiki/ParaView:Build_And_Install#Download_ParaView_Source_Code). Especially, be sure to have Qt5.

* Downloading the sources

'''user
git clone https://gitlab.kitware.com/paraview/paraview.git
cd paraview
git checkout release
git submodule update --init --recursive
''' 

* Configure with CMake

'''user
cd ../
mkdir pvbuild
cd pvbuild

ccmake ../paraview
'''

**Note :** ccmake is a tool that let you select options for compilation.

Press [t] to enable advanced options.
Press [c] to configure.
If you have an issue related to xmlpatterns. Be sure you have qt5-xmlpatterns installed.
Then press [c] to configure again. If you have any other issue disable the build of documentation.

You should be able to press generate files using th [g] key but do not do it yet.

We will now enable in the build. Find the **PARAVIEW BUILD PLUGIN OpenVR** parameters and set them to **ON**.
Press [c]. Find and set  the **OPENVR INCLUDE DIR** parameter to ***/path/to/openvr/headers*** and the **OPENVR LIBRARY TEMP** to ***/path/to/openvr/bin/linux64/libopenvr_api.so***. Configure again with the [c] key. Presse [c] until you can generate Makefiles.
Be sure no errors are displayed.

Then you can press [g] to generate Makefiles.

Be sure no error is displayed and run 

'''user
make -j 4
'''

**Note :** The option -j is used to state the number of threads you want to use for the compilation.

## Using

* Wire the headset.
* Run the register.sh file in the SteamVR-OpenHMD directory.
* Launch steam using the steam command in a terminal.
* Launch SteamVR using the steam GUI.
  * Be sure the application is sent to the headset.
  * If not, just shut down the SteamVR software et launch it again.
* At this point you should see the Steam-Home in the headset.
* Run the **paraview** you just built.
* Load the OpenVR module with the GUI in **Tools->Manage Plugins**
* A new window should appear. Then press on the **Send to OpenVR** button.
* Load a case, then press again on the **Send to OpenVR** button.
* Add the filters you want.
* You should be able te see your paraview case with the headset.

## Further work

Different interesting paths for a futur work :

* Upload each software used and try out the new features.
* Try out the HTC Vive or another device.
* Try it out on Windows.

## Conclusion

At the time I write these lines, lots of the tools used here are maybe not mature enough for the experience to be as cosy as wanted. This work was mostly a clearing work to see what was possible now. Hopefully some improvement will be done in a few years.
