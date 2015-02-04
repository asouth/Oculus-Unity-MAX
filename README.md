Oculus-Unity-MAX
================

The contents of this repository provides a bridge to send head movement data between the Oculus Rift, Unity and MAX/MSP. These tools have been created as product of a Royal Society Industry Research Fellowship Scheme between AECOM Ltd and AudioLab, Department of Electronics, University of York, UK.   

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

Next, to export the OCulus HMD movement and the character movement using UDP, in the project hierarchy navigate to Assets -> Scripts -> OSC -> ExportRotations and drag the ExportRotations.cs onto the MovementExporter object.

Then expand the OVRPlayerController but keep the MovementExporter highlighted in the Object Hierarchy and drag the OVRPlayerController object onto the OVRPC attribute in the object object inspector. Repat the process but placing the OVRCameraRig into the OVRCR attribute.

Now build your virtual environment as you wish, when you run the game your headmovments and WASD key press movements will be exported over UDP and can read using the corresponding MAX/MSP patch.
