================================
Steps to set up on software side
================================

#. Get an ubuntu 12.04 machine (any other distro will do, but we have tested on this version of ubuntu)

#. You can alternatively install *gcc-arm-linux-gnueabihf* instead of *Codesourcery cross-compiler*, we will use Codesourcery toolchain in rest of this documentation ::

	sudo apt-get install gcc-arm-linux-gnueabihf cpp-arm-linux-gnueabihf

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

#. If you have serial console (Rx, Tx) lines from the board/tablet, then to  
   view console output install *minicom* (optional) ::

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

   N.B: The above serial port setup and minicom are totally optional and will
   not be discussed later. Please search in web for more details. 

`Back to main page <https://github.com/androportal/linux-on-aakash/blob/master/README.rst>`_ 

 Next topic: `Compiling u-boot <https://github.com/androportal/linux-on-aakash/blob/master/compiling_uboot.rst>`_
