# Moved to bCourses - all of the content in this page has been moved to bCourses, and as of April 15, 2022, is no longer being updated.  Please use bCourses for the most recent, up to date version. This repo will be deleted once we are sure we have moved everything to bCourses correctly.

# How to Guide: Linux - Convert the Private Key from pem format to PuTTY Key Format for Windows

Video: https://kevincrook.com/ucb/mids/w205/how_to_guides/linux/03_linux_windows_convert_key_putty.mp4

PuTTY (and also WinSCP) store private keys in a different file format than pem.  The pem file create for your private key by AWS will need to be converted.  This guide walks you through the conversion.

The PuTTYgen app will be used for the conversion, start it:

**Windows system menu (lower left) => PuTTY (64-bit) => PuTTYgen**

Click the Load button (lower right)

Change dropdown in the lower right from "PuTTY Private Key Files (\*.ppk) to All Files (*.*)

Your pem file should now show up.  Click on the pem file.  Click the Open button.

You get a popup saying that the key loaded correctly (hopefully!).  Click OK to confirm.

Click on the "Save private key" button in the lower right.   It will ask you if you are sure, click Yes.

I usually use the same name as the pem file name as it will have the ppk extension and not overwrite the pem file.

Now you have a ppk file you can use for PuTTY and WinSCP.

Close out PuTTYgen. 
