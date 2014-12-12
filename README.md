Oculus-Unity-MAX
================

The contents of this repository provides a bridge to send head movement data between the Oculus Rift, Unity and MAX/MSP.

There are two parts to this repository:

1) A simple Unity package that interfaces with the Oculus Rift DK1/DK2 and, at game run-time, forwards the head movement data from the Oculus Rift and the global position of the virtual character using the UDP protocol as an OSC message. The OSC messaging is perfromed using the jorgegarcia/UnityOSC v1.2 C# classes interface for the Unity3d game engine.

2) A MAX/MSP patch (authored using MAX 6.1) is included and receives the OSC head movement messages and displays the head movement as a 3D visualisation. The patch is intended to be used as a bpatcher object around which new patches can be created.  

Documention
================
