# DazPosePreset-ArKit
Important Note: Transfer your character skeletal mesh before transferring animations from Daz Studio to Unreal engine

Basic poses for ArKit Face capture.  Made with default Parameter settings. Saved as Daz Pose Preset.

Reference Pose:

![Imgur](https://i.imgur.com/HmxcsXo.png)

Eyes:
![Imgur](https://i.imgur.com/uBRh8Fr.png)

Jaw:
![Imgur](https://i.imgur.com/lbKk2TW.png)

Mouth
![Imgur](https://i.imgur.com/EPX50Z4.png)

Cheek, Nose, Tongue
![Imgur](https://i.imgur.com/pItTu6j.png)

Using Pose Preset Animation

Download and extract or clone the three files into either:

Daz3DFiles\Presets\Poses

or

My Library\Presets\Poses

Open the ARKitFacePoseNames.txt file 

![Imgur](https://i.imgur.com/qPjFWNb.png)

You will need these names later

In Daz Studio load a base character into the scene.
In the Content Library tab, navigate to and double click the ARKitFacePoses preset 

![Imgur](https://i.imgur.com/ySewW4U.png)

This will pop up a message asking if you want add frames to the timeline. Click Yes.

![Imgur](https://i.imgur.com/zR1PIRR.png)

All the poses will be added to the timeline.

![Imgur](https://i.imgur.com/yHoqNLy.png)

TO DO - Getting Unreal Engine ARKit sample project setup

Back in Daz Studio we are ready to Send to - Daz to Unreal 

In the export settings:

Change the asset name to something like ARKitFacePoses

Set the Asset Type to Animation

Uncheck Enable Morphs

Uncheck Enable Subdivisions

Click Accept

![Imgur](https://i.imgur.com/mJ9t7rx.png)

Once imported right click on the animation

Go up to Create and click Create PoseAsset

![Imgur](https://i.imgur.com/OnKQpCW.png)

Go back to the ARKitFacePoseNames.txt file and copy all the names of poses

![Imgur](https://i.imgur.com/83D4Lyj.png)

Paste them into the Pose Asset dialog box and click Accept

![Imgur](https://i.imgur.com/Ef9oh4Y.png)

Open the Pose Asset

In the Asset Details Tab under Additive

Check Additive and set the Base Pose to the ARKit_Ref_Pose

Click Convert to Additive Pose

![Imgur](https://i.imgur.com/MQMZmjN.png)

If you have other characters you can change the Preview Mesh for the animation to see what the poses look like on other characters

![Imgur](https://i.imgur.com/uLHoWQM.png)

TO DO - Adding Pose Asset to Anim Blueprint














