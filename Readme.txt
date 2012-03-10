This build of Puppy Linux 5.2.8 contains a set of open source software sufficient to design 3D objects, 
convert them to 3D printer command files and operate a Reprap 3D printer. 
It is intended to be a complete turnkey operating system which can be run standalone on many PC
and laptop platforms. Neither Microsoft Windows nor any other version of Linux is required.

Desktop icons have been set up to start the programmes. If you are familiar with the Linux
command line environment, programmes may also be started by moving to the appropriate directory
(e.g. cd /root/my-applications/reprap-mendel-20111115/) then starting the programme in the usual way
(e.g ./reprap).


To get started download the .iso file from this repository and write it to a CD.
This must be done as an image write, not simply a file copy.
Look carefully at your CD writer programme and you should find an image writing,
or .iso burning, option. (In Puppy Linux use Burnisotocd found under the Multimedia menu.)
Shut down your computer and reboot with the CD inserted in a suitable drive. Puppy Linux
may start automatically. If the computer instead starts its normal operating system from
the hard drive, change the boot options in the BIOS setup to raise the
boot priority of the CD drive above that of the hard drive. 

The system can subsequently be booted from the CD or copied onto a bootable USB
memory stick  using the Bootflash programme included in the system (look in the main
menu under Setup). Unless you are familiar with Puppy Linux I recommend that you choose
the Don’t Save option when closing down a system booted from CD. Design and gcode files
can be saved onto the computer’s hard drive or a memory stick.

The software comprises:

Java (TM) SE Runtime Environment version 1.6.0_22
The other software requires JRE.

Production firmware issued by Adrian Bowyer Reprap Ltd. Several different firmware options are included.
The firmware resides in the Atmel microcontroller board on the Reprap printer, and controls
the printer's functions.

Arduino Integrated Development Environment version 0023, with extension to Sanguino boards
Used to edit Atmel microcontroller firmware and upload it to the Reprap.

Art of Illusion
A 3D design package with the ability to export the designs in .stl (stereolithography) format. 

Reprap Host (if this software fails to start correctly see the notes below)
Software which combines two functions within one user interface. Firstly conversion of
3D design files into ‘G-code’ 3D printer instruction files, and secondly printing the files
on a Reprap printer. (NB Do not try and control a Reprap printer whilst converting design
files to gcodes. This will insert control codes at random into the G-codes file - with
disastrous effects when you come to print the G-codes file!)

If you are unfamiliar with Linux, Puppy Linux, or any of the 3D printing software you
can learn how to operate them from the appropriate websites. The folder titles and structures
in Linux differ greatly from Microsoft Windows and can be very confusing until you get used to them.

Once your 3D printer is working, the essential steps in printing a new object are as follows.

1. Design your object using Art of Illusion (AoI. The axis designations (x,y,z) correspond between
AoI and the Reprap printers.
2. Export the file from AoI in .stl format.
3. Load the .stl file into Reprap Host and 'slice' (convert) it to a G-code file.
4. Load the G-code file into Reprap Host and print it. 



Notes:
Two significant problems were encountered in putting together this package. Firstly the Java package
provided for Puppy Linux loads by default into /mnt/home. Although it can be used from this location
it is not incorporated into a Puppy remaster. Java was therefore moved to /root/my-applications and
all of the Java links in /usr/bin redirected to the new location. Secondly Puppy 5.2.8 lacks some libraries
necessary to provide 3D graphics capabilities needed by Reprap Host. These libraries (used by glx and dri)
were added until the test programme glxgears worked.

If Reprap host fails to start correctly and/or Java reports errors naming glx, run the Xorg Video
Wizard (reached via the Setup menu) and choose the highest available resolution vesa video driver
which will work with your hardware. In my Samsung N130 laptop the vesa driver 1024x600x16 fails,
but 1024x600x24 works.
