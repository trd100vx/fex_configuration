fex_configuration
=================

How to use:
-----------------
Choose the configuration file you want, and rename it to script.bin. Then replace the new script.bin file with the old one you used in the OS images. Gernerally the script.bin file is in the first partition of the system.  
<br />
Files instruction:
------------------
bin directory: this directory contains the compiled bin file, you can use it directly.<br />
banana_pro_35lcd.bin is the configuration file for LeMaker 3.5 inch RGB LCD to make it work on Banana Pro. <br />
banana_pro_5lcd.bin is the configuration file for LeMaker 5.0 inch RGB LCD to make it work on Banana Pro. <br />
banana_pro_7lcd.bin is the configuration file for LeMaker 7.0 inch LVDS LCD to make it work on Banana Pro. <br />
banana_pro_10.1lcd.bin is the configuration file for LeMaker 10.1 inch LVDS LCD to make it work on Banana Pro. <br />
banana_pi_35lcd.bin is the configuration file for LeMaker 3.5 inch RGB LCD to make it work on Banana Pi. <br />
banana_pi_5lcd.bin is the configuration file for LeMaker 5.0 inch RGB LCD to make it work on Banana Pi. <br />
banana_pi_7lcd.bin is the configuration file for LeMaker 7.0 inch LVDS LCD to make it work on Banana Pi. <br />

<br />

fex directory:this directory contains the fex files specified to the bin files.



LeMaker team has designed three different size LCD modules, inlcude 3.5 inch, 5.0 inch, 7.0 inch and 10.1 inch:<br />
3.5 inch LCD module is RGB interface with 320*240 resolution (with ft5x_ts).<br />
5.0 inch LCD module is RGB interface with 800*480 resolution (with ft5x_ts).<br />
7.0 inch LCD module is LVDS interface with 1024*600 resolution (with ft5x_ts).<br />
10.1 inch LCD module is LVDS interface with 1280*800 resolution (with gt9xx_ts).<br />

Implementation<br />
For Linux<br />
Step 1:Replace the configuration file<br />
In order to use the LCD module, you need modify the script.bin file in your OS. You can donwload the modified file for each size LCD module from LeMaker github:
https://github.com/LeMaker/fex_configuration<br />
 sudo git clone https://github.com/LeMaker/fex_configuration.git<br />
Enter into the fex_configuration:<br />

 cd fex_configuration<br />
You will find two directories, bin and fex. In the bin directories there are compiled bin files that you can use it directly.<br />
Enter the bin directory:<br />

 cd bin<br />
You will see 7 bin files, 4 for Banana Pro and 3 for Banana Pi. On Banana Pro, you need use the files named banana_pro_Xlcd.bin. On Banana Pi, you need use the files named banana_pi_Xlcd.bin.(X should be 35, 5, 7 or 10.1 choose the right file according to what size LCD you use) Rename the corresponded bin file that you use to script.bin, and replace the new script.bin file with the old on in your OS.<br />
The script.bin file is located at the first partition of your SD card with OS.<br />

You also can download the script.bin files from http://mirror.lemaker.org/pro_script.bin.zip<br />
Then replace the script.bin file with the one for X inch lcd:<br />

 sudo mount /dev/mmcblk0p1 /mnt<br />
 sudo cp banana_pro_Xlcd.bin /mnt/script.bin<br />
 sync<br />
 sudo umount /mnt<br />
note this commond:sudo cp banana_pro_Xld.bin /mnt/script.bin<br />

Then reboot the system.<br />

Step 2:Enable the touche screen<br />
To use the touche screen, we need load the touch screen driver:<br />

For 3.5, 5.0, 7.0 inch LCD screen:<br />
 sudo modprobe ft5x_ts<br />
So you should edit the /etc/modules file,and add the content below into the file:<br />

 ft5x_ts<br />
