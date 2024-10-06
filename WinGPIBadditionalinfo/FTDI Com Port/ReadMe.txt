So I was playing around with a new USB to RS232 (TTL) device, the Waveshare USB TO RS232/485/TTL. I chose this model because it has an isolated USB port meaning that the any mains born noise on the earth will not make it's way to the PDVS2mini when connected using WinGPIB.
However, I came across an issue and thought I'd post here concerning common issues of getting an FTDI based USB-Serial (TTL) adaptor and how to get it working (Win10).

If you are lucky, you plug in your cheap FTDI based adaptor, drivers automatically load, and it just works! If not, then you sometimes have to jump through hoops, the symptoms being, you can see a COM Port in Device Manager but it doesn't work properly with your Comms app, i.e. WinGPIB or any other serial app.

The quick fix is to dump the FTDI based adaptor and buy a CH340G or CP2102 based adaptor as they 'just work'. But, if you are stuck with FTDI, then here's some tips based on my experience:

If you install the FTDI driver software then it may appear in Device Manager under PORTS as "FTDI......", but this may not work properly.
It has to appear in Device Manager as "USB Serial Port (ComX)" where X is your port number.

Zadig is a great wee app ( https://zadig.akeo.ie ) that allows you to change drivers for a device on the fly, quickly and easily, however, I found that Zadig doesn't support changing to the FTDI driver.
If it could, you'd want Zadig to change out the driver for one listed as "FTDIBUS (v2.12.6.0)" but the selection available to do so is not listed and none of the ones that are will work.

So, going back to Device Manager the answer lies there.

First, download the FTDI VCP driver from https://ftdichip.com/drivers/vcp-drivers/
(At time of writing I installed CDM-v2.12.36.4-WHQL-Certified)
Unzip and right click on both the .INF files and select INSTALL. You should get confirmation each time that the driver is installed......but of course it won't actually be active!

Next, open Device Manager, right click on the COM Port and select UPDATE DRIVER and select BROWSE FOR DRIVERS ON MY COMPUTER
Then at the bottom select LET ME PICK FROM A LIST OF AVAILABLE DRIVERS ON MY COMPUTER, and select "USB Serial Port Version........".
PS. HAVE DISK is an option but I didn't need to do that.

Once you do this (you may need to re-boot), Device Manager should now list your COM Port as "USB Serial Port (ComX)", and if you did open Zadig just for a look then it should list as "FTDIBUS (v2.12.6.0)"

Hope that helps somebody!

Ian.