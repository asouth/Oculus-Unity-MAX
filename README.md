Oculus-Unity-MAX
================

The contents of this repository provides a bridge to send head movement data (yaw,pitch and roll as well as 3d co-ordinates of the player in the game world) from the Oculus Rift and Unity to MAX/MSP using UDP messaging. These tools have been created as product of a Royal Society Industry Research Fellowship Scheme between AECOM Ltd and AudioLab, Department of Electronics, University of York, UK.   

Disclaimer and License
----------------

This patch/package may not be error free, fully functional, accurate or reliable. In no event will we be liable for any loss or damage of any kind arising out of or in connection with your use of this patch/package.

This work is licensed under a Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License which can be found at http://creativecommons.org/licenses/by-nc-sa/4.0/

Overview
----------------

There are two parts to this repository:

1) Unity Package - A simple Unity package that interfaces with the Oculus Rift DK1/DK2 and, at game run-time, forwards the head movement data from the Oculus Rift and the global position of the virtual character using the UDP protocol as an OSC message. The OSC messaging is perfromed using the jorgegarcia/UnityOSC v1.2 C# classes interface for the Unity3d game engine which can be found at (https://github.com/jorgegarcia/UnityOSC) and is licensed under the The MIT License (MIT) http://opensource.org/licenses/mit-license.php


2) A MAX/MSP patch (authored using MAX 6.1) - This receives the OSC head movement messages and displays the head movement as a 3D visualisation. The patch is intended to be used as a bpatcher object around which new patches can be created.  

Documention
----------------

Start a New Unity Project

Import 2 Custom Packages by selecting Assets -> Import Package -> Custom Package

The first package is the OculusUnity Integration package (filename: OculusUnityIntegration.unitypackage) which is available from the developers pages on the Oculus website.

The second is the OVR_MovementManager.unitypackage.

Next you need to create a character controller.

In the Project Heirarchy select Assets -> OVR -> Prefabs and the drag the OVRPlayerController onto the object Hierarchy window.

Now create an Empty game Object, GameObject-> Create Empty and rename it to something useful like MovementExporter.

Next, to export the OCulus HMD movement and the character movement using UDP, in the project hierarchy navigate to Assets -> Scripts and drag the ExportRotations.cs onto the MovementExporter object.

Then expand the OVRPlayerController but keep the MovementExporter highlighted in the Object Hierarchy and drag the OVRPlayerController object onto the OVRPC attribute in the object inspector. Repeat the process but placing the OVRCameraRig into the OVRCR attribute.

Now build your virtual environment as you wish, when you run the game your headmovments and WASD key press movements will be exported over UDP and can read using the corresponding MAX/MSP patch.

Note that the ExportRate can be used to reduce the rate at which the positional messages are sent over UDP. By default the Export is 1 and corresponds to 1 message every time Update() is called. However if, for example, ExportRate was 4 then the positional message would only be sent every 4th time update is called. The ExportRate can be changed at run-time by holding Ctrl and pressing Up or Down. The unity2max.maxpat patch will display the current UDP frame rate, if it is receiving messages when the keys are pressed.

The IP Address and Port number can now be changed without the need to Build the project again. Simply place a file name ipconfigfile.txt in the same folder as the executable ensure the first line reads i.e. "127.0.0.1 8000" but omitting the quotation marks.


