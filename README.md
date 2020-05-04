# ImageJ Nuclei Counter for Fluorescent Images

## The modified ImageJ plugin ITCN

This is a modified version of the ImageJ plugin ITCN. The original plugin is developed by the Center for Bio-image Informatics at UC Santa Barbara, and released on the [ImageJ website](https://imagej.nih.gov/ij/plugins/itcn.html). It could also be downloaded from the developer's [web page](https://bioimage.ucsb.edu/docs/automatic-nuclei-counter-plugin-imagej) (This version actually works better).

However, because the plugin is developed many years ago, it is no longer maintained and no detailed instructions could be found on the internet. Here I improved the original plugin a little bit so that it could be recorded by and used in ImageJ macro scripts.

### Installation

Download Itcn.zip from [this Github directory](https://github.com/dorrenasun/CountNuclei.git), unzip, and place it under the ImageJ or Fiji plugins folder, restart ImageJ or Fiji. There will be a new Plugins>Itcn menu path.

* How to find ImageJ plugins folder:  
  * If you are using ImageJ:  
  Open the software and select File>Show Folder>Plugins.
  * If you are using Fiji:  
  Open the software, _CLOSE ALL IMAGES_ and select Image>Show info...  
  ImageJ home information will appear. Go to that folder and there will be a plugins subfolder.

### How to use ITCN

You can also refer to this video on [Youtube](https://youtu.be/PqHFsmS1_JY) for how to use the original version of ITCN. Basic ideas are the same.

1. Open an image before you start the plugin.
2. Convert the image to 8-bit using Image>Type>8-bit.
3. Select Edit>Invert so that you have dark signals on a white background.
4. Select Plugins>Itcn>Itcn, a dialog will appear.
5. Play around to determine the choices and parameters:
    * Select your image in "Image". If you want to use another unopened image, open it using the "Open..." button. If you opened some new images from File>open.. or Drag&Drop, you will have to restart the Itcn plugin to count on them.
    * The "width" parameter stands for the diameter of the nuclei in pixels, and the "Minimum Distance" stands for the distance between two nearby nuclei. These distances could also be measured on the image. Use the line tool to mark distances, and click "Measure Line Length" in the dialog to do so.
    * "Threshold" changes the sensitivity on nuclei detection. With a lower threshold weaker signals could be counted, but the risk of counting background noise as signals also increases. Start with a larger threshold (e.g. 0.2) so the initial trial won't take you too long.
    * Select "Detect Dark Peaks" if you have inverted the image as suggested by step 3.
    * You can choose which part of the image to be counted. This could be done in two ways:
       * Select the region of interest (ROI) using the selection tools (Rectangle, Oval, Polygon or Freehand). Leave the "Mask Image" choice as "Use seleted ROI" if doing so.
       * Use a binary mask. This should be a thresholded binary image, the region of interest in black and background region in white. Choose the image name or open it from the dialog.  
  For the example images, the default parameters were recommended.
6. Click on "Count" and wait for the program to finish. This could take a while, especially when you are using a small threshold. Pay attention to the "Log" window, and it will tell you if the analysis is finished. Counted nuclei will be marked with a small red dot, and the selected region will be indicated with blue borders. If you are not happy with the result, change the parameters and "Count" again. Or you could manually improve the results with Paintbrush (Will be explained later).
7. Don't forget to click on "Exit" after you finished the analysis!

### How to improve the results manually with Paintbrush

Sometimes the algorithm is just not clever enough to accurately cover all the nuclei in your image, leaving a few exceptions. It would be much easier to improve manually.

1. Put your pointer over "Color picker" on the toolbar, the foreground/background colors will be indicated. After running the Itcn plugin, the foreground/background colors will be set to red(255,0,0) and white(255,255,255) respectively. If not so, double-click the "Color picker" to set up these colors. Double-click the foreground or background color block to check RGB values.
2. Double-click the "Paintbrush" tool to set brush width. 5 should be a good value.
3. Use paintbrush to mark the missing nuclei with red dots, and cover the unwanted ones with white. Keep pressing the "alt" key to use background white color.
4. After you finish, remember to save this image for future reference.
5. Run Plugins>Itcn>Count Red Dots to get the revised number.

## Batch Mode of Itcn

1. Before you start, place all your fluorescent images in a folder called "Nuclei". If you wish to generate masks from bright field images, place them in a folder called "BF". Make sure the _sequence_ of corresponding images are identical between two folders.
2. Run Plugins>Itcn>Batch ITCN and follow the instructions. All the images will be processed with the same parameters.
3. If you are not happy with the output, adjust individual images with Itcn in normal mode or use paintbrush to improve manually.
4. After improving the results, red dots on ITCN results images could be counted using Plugins>Itcn>Batch Count.

