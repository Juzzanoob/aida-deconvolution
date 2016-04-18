# Introduction #

A brief tutorial on using AIDA with Priithon by F. Marchis.


# Details #

**1. Test if you have Python 2.5 on your machine**

Open an Xterm or Terminal window on your Mac, type "Python". You should see something like this:

_la-fournaise.localin programs> python_

_Python 2.5 ([r25](https://code.google.com/p/aida-deconvolution/source/detail?r=25):51918, Sep 19 2006, 08:49:130_

_[4.0.1 (Apple Computer, Inc. build 5341)](GCC.md) on darwin_
_Type "help", "copyright", "credits" or "license" for more information._
_>>>_
_type "exit()" in Python to get out_

if the first line is "Python 2.5" then go to step 3, else continue to step 2

**2. Python 2.5 Installation and Test**

Install Python 2.5 for Mac OS X (if you don't have it already): http://www.python.org/download/releases/2.5.4/

Make sure that this is the default Python on your machine by typing
"python" in a xterm window.  You should see:

_"Python 2.5 ([r25](https://code.google.com/p/aida-deconvolution/source/detail?r=25):51918, Sep 19 2006, 08:49:13) "_

Type "exit()" to quit

**3. Priithon installation and test**

install Priithon for Python 2.5 for Mac from http://code.google.com/p/priithon/

Put the Priithon directory (called Priithon\_25\_mac) on my home directory ~/Priithon\_25\_mac

After installing priithon, test it typing in an xterm window " ~/Priithon\_25\_mac/priithon\_script"

A new window should open with the following text:

_" !!! Welcome to Priithon !!!_
_(Python 2.5 ([r25](https://code.google.com/p/aida-deconvolution/source/detail?r=25):51918, Sep 19 2006, 08:49:13)  [4.0.1 (Apple Computer, Inc. build 5341)](GCC.md) on darwin)"_

**4. Install AIDA**

Unzip the AIDA1.2.2i archive available in the download and copy the directory  AIDA\_1.2.2i on your home directory

**5. Test AIDA**

An archive containing a Titan test image can be found in the Download section

unzip this archive in your directory (directory ~/Test\_AIDA)

open an xterm window and cd ~/Test\_AIDA/Titan\_testimage

You will run AIDA typing the following command

~/Priithon\_25\_mac/priithon\_script ~/AIDA\_1.2.2i/AIDA.py -S AIDA\_Settings.py

AIDA will run for about 6-9 min (depending of the machine)

if everything goes well you should see a new directory called Results/myopic**containing three files in it called Robj Rpsf and**.log

The file called comparison.jpg in the Titan\_testimage show what Titan should look like after deconvolution. You can compare it with Robj\*fits.