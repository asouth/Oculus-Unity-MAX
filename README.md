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
