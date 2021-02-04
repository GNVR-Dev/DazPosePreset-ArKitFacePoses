# DazPosePreset-ArKit
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

Unreal Engine Project Setup:

In your Project Settings make sure the following Plugins are enabled:

DazToUnreal

![Imgur](https://i.imgur.com/ActwpiS.png)

Apple ARKit and Apple ARKit Face Support

![Imgur](https://i.imgur.com/wocd2E9.png)

As well as Live Link

![Imgur](https://i.imgur.com/H2zraCl.png)

Click Restart Now to restart your project.

In Daz Studio load a base character into the scene.

Send the character mesh to Unreal by going to:

File -> Send To -> Daz To Unreal

![Imgur](https://i.imgur.com/EZGnqNw.png)

Set the Asset Type to Skeletal Mesh

Uncheck Enable Morphs

Uncheck Enable Subdivisions

and click Accept

![Imgur](https://i.imgur.com/j9Rv8zI.png)

Using Pose Preset Animation

Download and extract or clone the three files into either:

Daz3DFiles\Presets\Poses

or

My Library\Presets\Poses

Open the ARKitFacePoseNames.txt file 

![Imgur](https://i.imgur.com/qPjFWNb.png)

You will need these names later

In the Content Library tab, navigate to and double click the ARKitFacePoses preset 

![Imgur](https://i.imgur.com/ySewW4U.png)

This will pop up a message asking if you want add frames to the timeline. Click Yes.

![Imgur](https://i.imgur.com/zR1PIRR.png)

All the poses will be added to the timeline.

![Imgur](https://i.imgur.com/yHoqNLy.png)

Again, go to File -> Send To -> DazToUnreal

Change the asset name to something like ARKitFacePoses

Set the Asset Type to Animation

Uncheck Enable Morphs

Uncheck Enable Subdivisions

Click Accept

![Imgur](https://i.imgur.com/mJ9t7rx.png)

Once imported right click on the animation

Go up to Create and click Create PoseAsset

![Imgur](https://i.imgur.com/zLK3Rso.png)

Go back to the ARKitFacePoseNames.txt file and copy all the names of poses

![Imgur](https://i.imgur.com/83D4Lyj.png)

Paste them into the Pose Asset dialog box and click Accept

![Imgur](https://i.imgur.com/4RBpghk.png)

Open the Pose Asset

In the Asset Details Tab under Additive

Check Additive and set the Base Pose to the ARKit_Ref_Pose

Click Convert to Additive Pose

![Imgur](https://i.imgur.com/MQMZmjN.png)

If you have other characters you can change the Preview Mesh for the animation to see what the poses look like on other characters

![Imgur](https://i.imgur.com/uLHoWQM.png)

Setting Up the Animation Blueprint

Right click in the Content Browser

Mouse over Animation and Select Animation Blueprint

![Imgur](https://i.imgur.com/SX3vxc4.png)

In the Animation Blueprint AnimGraph right click and create a Live Link Pose node:

![Imgur](https://i.imgur.com/RIsqPrq.png)

Set the Live Link Subject Name to the device you are using for face capture

![Imgur](https://i.imgur.com/6oclQGS.png)

Pull out from the output pin and create a modify Curve Node

![Imgur](https://i.imgur.com/tuAuzG1.png)

Change the Apply Mode to Weighted Moving Average

![Imgur](https://i.imgur.com/hHL0gka.png)

Pull off from the Alpha input and promote to variable

![Imgur](https://i.imgur.com/Baj0osO.png)

Change the name of the Variable to WMA_Alpha

Compile the Blueprint

and set WMA_Alpha's the default Value to .8

![Imgur](https://i.imgur.com/P2dhcgJ.png)

Pull off from the Modify Curve node and create a node to Evaluate your face poses Pose Asset

![Imgur](https://i.imgur.com/IPnMZ23.png)

Connect this node to the Output Pose and Compile to test that this part is working OK

![Imgur](https://i.imgur.com/CduD8q2.png)

To add head movement pull a pin out and create a Local To Component Node

![Imgur](https://i.imgur.com/apPsfbc.png)

Then create three Transform (Modify) Bone nodes and reconnect to the Output Pose (a Component To Local node will be created automatically)

![Imgur](https://i.imgur.com/asiIbV6.png)

On each of the Transform (Modify) Bone nodes set the Rotation Mode to "Add to Existing" and the Rotation Space the "Bone Space"

On the first Transform (Modify) Bone node set the Bone to Modify as neckLower

On the second Transform (Modify) Bone node set the Bone to Modify as neckUpper

On the third Transform (Modify) Bone node set the Bone to Modify as head

Pull off one of the Rotation pins and Make Rotator

![Imgur](https://i.imgur.com/zGy9zPP.png)

Connect the rest of the rotator pins to the make roTator node

Right click on the graph and create a Get Curve Value node

![Imgur](https://i.imgur.com/RixWuLA.png)

Enter headPitch into the Curve name

add a multiply node and enter -90.0

add a divide node and enter 3.0

![Imgur](https://i.imgur.com/fHXpVPn.png)

Duplicate these nodes twice and connect to the Y(Pitch) and Z(Yaw) of the Make Rotator Node

On the second Get Curve Value node change the Curve Name to headYaw

On the third Get Curve Value node change the Curve Name to headRoll

![Imgur](https://i.imgur.com/ZwIG9x0.png)

Compile and test.

If the head movement isn't working it's probably because the skeleton doesn't have a headPitch, headYaw, or headRoll anim curve set up yet.

In the Skeleton setup of your character go to the Anim Curve tab and search for Head.

If those curves aren't listed Right Click and "Add Curve"

![Imgur](https://i.imgur.com/Ydt6SFO.png)

Add a curve for:
HeadPitch
HeadRoll
HeadYaw

![Imgur](https://i.imgur.com/eQYWmHY.png)

Head movement should now be working



