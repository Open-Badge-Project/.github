# Open Badge Project

![](<../images/badge.gif>)

This is the Open Badge Project. The idea behind this is to have a very low cost, low power electronic badge. These could be built just for fun, or if you're throwing a conference, feel free to use the PCB as the badge, maybe build some, maybe let the folks at the conference build them.

Electronic badges have gotten pretty hip, but they seem to suffer from two primary problems.
1) They are very expensive
1) They need a lot of batteries

The goal of the Open Badge Project was to build a badge that costs $5 or less and can run for a day or more on one 2032 battery.

The badge as it stands right now will only cost $5 if you build A LOT (1000 or more). The cost is closer to $6 or $7 for smaller batches at the moment, but that's still pretty reasonable.

### Types
There are two versions of the badge. One is a through hole badge that's very easy to solder. It was designed with human fabricators in mind. The kicad files in the main branch are for the through hole model.

There is also a surface mount version. This version of the badge can be sent off to a fabricator to be mass produced.

Both badge versions use the same code. The KiCad design files for the badges can be found in the [badge-hardware](https://github.com/OpenBadgeProject/badge-hardware) repo.

## How does it work?
The badge itself runs on a microprocessor called an ATTINY85. It has 8K of program space, 512 bytes (yes, bytes) of memory. That microprocessor then drives 3 shift registers. One for the button input, and two for the display output. Shift registers shouldn't be used to drive LEDs, but it works, and doing it this way keeps the cost down.

The PCB was designed using KiCad.


## How to change the logo
KiCad has a tool called "Image Converter". This application lets you turn an image into a footprint that can be added to the PCB layout.

When you run the tool, there is a button on the left called "Load Source Image". If you have a black and white image to start with that's the best. You can use any image but things get weird.

Once you load an image you will need to watch the size. The "Output Size" field is what matters here. It will take a few tries to get it right. There's about 3 inches by 1.7 inches of space to work with on the front.

Use the "Front Solder Mask" layer. Make sure you use Footprint for the output layer.

Click Export to file. Save the file in the badge-footprints.pretty directory.

Now open the "PCB Editor" application. Make sure the "F. Silkscreen" layer is selected on the right.

You will have to click on and delete the existing logo. Now from the menu Place -> Add Footprint

If you search for "badge" in the text box you should see your logo show up in the list. Double click it, then place it where it fits. If the logo isn't sized right, go back to the Image Converter and try again.

## How to order PCBs
If you want to have PCBs made, you need to export the Gerber files from the PCB Editor. The Gerber files are what you send the PCB manufacturer.

Run the PCB Editor, then File -> Fabrication Outputs -> Gerbers

Create a new directory to hold the files (there will be more than one). For example let's call it badge_gerber. Leave the default settings alone, it should do the right thing.

Then click Plot. Then click "Generate Drill Files" and "Generate Drill File" on the window that pops up. Your directory now has the files need to create the PCB in it.

The PCB manufacturer will want that directory turned into a zip file and uploaded. You're on your own to figure that part out.
