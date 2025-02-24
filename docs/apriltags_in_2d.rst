Tracking AprilTags
==============================================================

AprilTags are tracked using the "tx", "ty", and "ta" values in NetworkTables, just like standard retroreflective targets! No code changes are required to upgrade a retroreflective tracking robot to apriltags.
"botpose" and "camtran" may also be used for field-space and target-space 3D tracking.

For more advanced usage with multiple tags, the JSON results dump may be used.

Do not feel pressured to use the more advanced features in the "Advanced" pages unless you know you need them. Many of the very best teams in FRC use the simplest techniques available 
to maximize reliability and speed. If you frequent Discord, CD, and regionals with elite teams, you may get the impression that you need the most advanced software possible to win events, but this is simply not true.

Our message to many of the teams we help is "It's ok to do the simple thing."

To configure an AprilTag pipeline, first access the Limelight web interface at <http://IPADDRESS:5801> or http://10.te.am.11:5801 for FRC teams. Use the Limelight Finder tool from our Downloads page to find your Limelight's IP address.



Quick Start for FRC
~~~~~~~~~~~~~~~~~~~~~~
* Input Tab - Change "Pipeline Type" to "Fiducial Markers"
* Standard Tab - Make sure "family" is set to "AprilTag Classic 16h5"
* Input Tab - Set "Black Level" to zero
* Input Tab - Set "Gain" to 20 
* Input Tab - Reduce exposure to reduce motion blur. Stop reducing once tracking reliability decreases.

* Standard Tab - If would like to increase your framerate, increase the "Detector Downscale"
* Input Tab - For increased range and/or accuracy, increase the capture resolution.

* Click the "Gear" Icon, and make sure your team number is set and that a static IP is configured.
* Click "Change Team Number" and "Change IP Settings" if you changed their corresponding settings. Powercycle your robot.
* You're done! Use "tx" and "ty" from networktables. Copy the code sample on the "getting started" page.

* Make sure your tags are as flat as possible.
----------

.. _Input:

Input Tab
~~~~~~~~~~~~~~~~~~~~~~

----------

The Input Tab hosts controls to change the raw camera image before it is passed through the processing pipeline. See the "Building a retroreflective/color pipeline" page for more details.

To track AprilTags:

* Change "Pipeline Type" to "Fiducial Markers"
* Set "Black Level" to zero

At this point, it is a matter of balancing sensor gain and exposure time. You want to be able to see the tags with the smallest exposure possible to minimize motion blur.
This usually calls for a high sensor gain setting. For simple 2D tracking,
it is often advisable to max-out your sensor gain, and then increase your exposure from zero until targets are sufficiently tracked. Make sure the correct family is selected in the "Standard" tab if tracking isn't working.


----------

Standard Tab
~~~~~~~~~~~~~~~~~~~~~~

----------------------

 
Family
--------------------------------------
Selects the fiducial/AprilTag family type. For FRC, you should selection "AprilTag Classic 16h5 (30 tags)"


Marker Size
--------------------------------
Sets the expected size of the tags your robot will encounter in mm. For FRC, this should be set to 203.2

Detector Downscale
--------------------------------
Increasing this number will result in significant performance boosts. This this will sometimes result in reduced range, but the cost is usually minimal.

ID Filters
--------------------------------
ID Filters allow you specify exactly which tags you care about. For most FRC teams, each pipeline should be configured to track exactly one tag ID.
This is a comma-separated list of numbers (eg. "0,1")

(ADVANCED) Localization ID Filters
----------------------------------------------------------------
This is only for advanced users. This filter allows you to specify the tags that should be considered during field-space localization). It is recommended to only consider the tags that you plan on seeing during a match.

Multi-Target Sorting and Grouping
--------------------------------
This allows for the exact grouping functionality seen in standard retroreflective pipelines. In most games, the only feature to modify is the "Area" filter, which will allow you to filter-out small tags.

------------------------------
