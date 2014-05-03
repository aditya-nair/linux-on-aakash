================================
Steps to set up on software side
================================

#. Get an Ubuntu 12.04+ machine (any other modern distro will do, but we have tested on Ubuntu 12.04 and 14.04)

#. Download and install free ``Codesourcery cross-compiler`` from this `page <http://www.mentor.com/embedded-software/sourcery-tools/sourcery-codebench/editions/lite-edition/>`_ , find *Download the GNU/Linux Release* in **ARM processor** section, click on link and fill up the form, from link in your email choose the most recent version of toolchain, download the ``IA32 GNU/Linux Installer`` version. 

#. Download the the *.bin* file make it executable and run it from terminal, follow the instructions given on the prompt(dash related) and allow GUI installer to copy toolchain to your preferred location. Update the Codesourcery bin directory in your ``$PATH`` so that bash can find the binaries. 


#. You can alternatively install *gcc-arm-linux-gnueabihf* instead of *Codesourcery cross-compiler*, but we will use Codesourcery toolchain in rest of this documentation ::

	sudo apt-get install gcc-arm-linux-gnueabihf cpp-arm-linux-gnueabihf
   **Note:** I you are on 64-bit Ubuntu, then *gcc-arm-linux-gnueabihf* won't work. You have to install *Codesourcery cross-compiler*
   
#. Install dependencies for kernel compilation ::

	apt-get install build-essential dpkg-dev kernel-wedge make automake checkinstall git u-boot-tools

#. You may also need *adb* and *qemu-user-static* for getting ``script.bin``
   from android and to install packages in chrooted Linux. We will get back to  
   this later. To install *adb* you can either install entire android-sdk or 
   can you may download binary directly from this `link <https://raw.github.com/androportal/aakash-apps-installer/master/adb>`_.  
   Please make the *adb* binary executable. And to install *qemu-user-static*
   just issue ::

	sudo apt-get install qemu-user-static

#. If you are using x86_64 bit ubuntu then to run *adb* you must install ::

	sudo apt-get install ia32-libs-multiarch
	
(OPTIONAL) For setting up serial console
-----------------

#. If you have serial console (Rx, Tx) lines from the board/tablet, then to  
   view console output install *minicom*  ::

	sudo apt-get install minicom

#. To setup ``minicom``, connect Aakash's serial port(one which you have
   soldered out from the board) to your linux machine using suitable level 
   shifter ::

	sudo minicom -s

   Set the right serial device(eg: /dev/ttyUSBx), set BPS to 115200 8N1,
   Hardware flow control : ``NO``, and also Software flow control : ``NO``.  
   Save the setting as default and exit. From next time when you connect
   serial console device from Aakash to your ubuntu machine just run ::

	sudo minicom 

`Back to main page </README.rst>`_ 

 Next topic: `Compiling u-boot </compiling_uboot.rst>`_
