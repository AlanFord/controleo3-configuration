# controleo3-configuration
Configuration information and profiles for a Controleo3 Toaster Oven Reflow Controller

I've finally gotten a enthusiast-grade reflow oven to work.  After trying several options,
none achieved both the ability to accurately follow a reflow profile while at the same time 
avoiding cold spots in the oven.  However, a toaster oven retrofitted with a Controleo3 oven
controller has been up to the task!

It's important to note that a successful build required using both a Controleo3 oven controller and a fair-bit of insulation inside the toaster oven.  The insulation makes it 
easier for temperature changes to keep up with the required reflow profile, while the Controleo3 oven controller permits independent control of up to three separate heating elements (permitting the elimination of cold spots).

## The Oven
I started with a Black+Decker Toaster Oven, Model TO1303SB.  This was an intentional choice as it aligned nicely with the oven retrofit kit that can
be ordered with the Controleo3 controller.  The kit was nice because there
are very good build guide for installing and testing 
everything ( https://www.whizoo.com/reflowoven ).

## The Build
The build guide was fairly complete, but I did generate a few "lessons learned".
* Read the guide from beginning to end before starting.  Several of the later steps rely on choices made in earlier steps.
* Red RTV gets all over everything.  Use it in an area prepped for a mess and have a lot of paper towels available within arms reach.
* When preparing to mount the SSR's on the aluminum plate, realize that you will be running wiring between them (see Step 13 of the build guide).  A crimp connector should fit between the left and center SSR, so space them 
appropriately.
* A good crimping tool can make all the difference!  A better/best from the
hardware store is all that's needed.
* Don't cut the braided sleeving unless absolutely necessary - and have a flame ready to seal the ends.  Otherwise it will unravel badly (yeah, I know - a newbie mistake).
* The recommended diameter of holes in the top right of the toaster oven shell were too small for the screws.  I stepped up to a #42 drill (0.093") and everything worked well.
* Heed the advice to make sure the oven controller is far enough away from the door handle to avoid interference when opening and closing the oven door.  In hind sight it might help to test assemble the controller box, servo, and servo arm to see just how far from the door it should be mounted.
* In Step 7 of the build guide, note that the second photo states the holes should have been closer to the edge.  Heed that advice! drilling closer to the edge will allow the bracket to be mounted to a flat surface on the oven
shell, giving a much more stable mount.
* When putting insulation on the bottom of the oven, turn the oven over before inserting the insulation.  This will ensure the insulation stays away from the metal surface until you are ready to press it down (or up, in this 
configuration).
* Have spare zip ties available.  I ended up installing and then removing
several as I figured out how I finally wanted all the wiring controlled.

## Calibrating the Reflow Oven
The "learning cycle" is pretty cool and works very well.  I was able then to immediately reflow a small test PCB in the center of the oven.  However, I was still worried about the likelihood of cold spots at the edges of the oven.  Possibly not a problem if you do a single PCB at a time, but a full tray of boards could have problems.

I used the adhesive temperature strips that came with the build kit to check for cold spots.  I put five home-etched PCBs in the oven (in an X configuration), each with a temperature strip to monitor the peak temperature reached.  The stock 225C reflow curve showed the center of the oven to be perfect, the back of the over to be 9C too cool, and the front to be 15C too cool.  There was no left-right variation, which was very helpful.

With more Type E temperature strips (somewhat hard to find - try https://www.tiptemp.com/Products/Eight-Temperature-Labels/TLCSEN033-Temperature-Label-8-Level-Strip-E.html )  I was able to get the front of the oven up to 225C, while the center and back of the oven reached 232C - not too bad.  This required changing the duty cycle of the extra (third) heating element to 75% and changing the peak temperature of the reflow
profile from 225C to 230C.  The intermediate temperatures where changed
proportionally (assuming no bias at 20C), so140C, 165C, 220C, and 225C were
changed to 143C, 169C, 225C, and 230C.  The hope is that everything stays below the liquidus temperature until the reflow portion of the profile begins.

Finally, I compared the temperatures reached with a home-etched singled-sided
PCB and a purple PCB from OSH Park.  There was a possibility that the dark purple board would reach a higher temperature than the lighter-colored boards I
had sued for calibration.  However, my concerns were unfounded.  Both
boards reached the same temperature - and the oven is calibrated!

