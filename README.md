<h3>Note:</h3>
You'll need to set your Station ID, Latitude, and Longitude in the `run.sh` file.

<h4>Change Log</h4>

* Added expanded XML format which can transmit location and heading data if supplied by the user. Added location and heading to run.sh.
  * This new format does not break app compatibility

<h4>Ubuntu 20.04 Users NOTE:</h4>

Note that on Ubuntu 20.04 or newer PyQt4 is no longer available. A contributor has created his own modification to the code which uses PyQt5. You can try it at this link https://github.com/rfjohnso/kerberossdr

**This branch is not available PyQt5 currently**

<h3>Please see the software tutorial at www.rtl-sdr.com/ksdr</h3>

<h2>KerberosSDR Demo Software</h2>

<h3>Installing the software</h3>

1. <h4>Install Dependencies via apt:</h4>

  `sudo apt update`<br>
  `sudo apt install python3-pip python3-pyqt4 pyqt4-dev-tools build-essential gfortran libatlas3-base libatlas-base-dev python3-dev python3-setuptools libffi6 libffi-dev python3-tk pkg-config libfreetype6-dev php7.2-cli`

2. <h4>Uninstall any preinstalled numpy packages as we want to install with pip3 to get optimized BLAS.</h4>

  `sudo apt remove python3-numpy`

3. <h4>Install Dependencies via pip3:</h4>

  `pip3 install numpy`<br>
  `pip3 install matplotlib`<br>
  `pip3 install scipy`<br>
  `pip3 install cairocffi`<br>
  `pip3 install pyapril`<br>
  `pip3 install pyargus`<br>
  `pip3 install pyqtgraph`<br>
  `pip3 install peakutils`<br>
  `pip3 install bottle`<br>
  `pip3 install paste`<br>

4. <h4>Install RTL-SDR-Kerberos Drivers</h4>

  Our Kerberos RTL-SDR driver branch contains code for slightly modified Osmocom RTL-SDR drivers that enable GPIO, disable dithering, and disable zerocopy buffers which seems to cause trouble on some ARM devices.

  `sudo apt-get install libusb-1.0-0-dev git cmake`<br>

  `git clone https://github.com/rtlsdrblog/rtl-sdr-kerberos`<br>

  `cd rtl-sdr-kerberos`<br>
  `mkdir build`<br>
  `cd build`<br>
  `cmake ../ -DINSTALL_UDEV_RULES=ON`<br>
  `make`<br>
  `sudo make install`<br>
  `sudo cp ../rtl-sdr.rules /etc/udev/rules.d/`<br>
  `sudo ldconfig`<br>

  `echo 'blacklist dvb_usb_rtl28xxu' | sudo tee --append /etc/modprobe.d/blacklist-dvb_usb_rtl28xxu.conf`

5. <h4>Reboot the Pi.</h4>

6. <h4>Test 4x Tuners</h4>

  At this stage we recommend first testing your four tuners with rtl_test. Open four terminal windows, or tabs, and in each window run "rtl_test -d 0", "rtl_test -d 1", "rtl_test -d 2" and "rtl_test -d 3". Ensure that each unit connects and displays no errors.
Install KerberosSDR Demo Software

7. <h4>Clone or unzip the software</h4>

  `git clone https://github.com/rtlsdrblog/kerberossdr`<br>
  `cd kerberossdr`<br>
  `sh setup_init.sh`

8. <h4>Now you can run the software by typing</h4>

  `./run.sh`

Full software tutorial at www.rtl-sdr.com/ksdr

TROUBLESHOOTING:

Edit the run.sh file and comment out the >&/dev/null parts on the last line to show any errors to the terminal.


This software was 95% developed by Tamas Peto, and makes use of his pyAPRIL and pyARGUS libraries. See his website at www.tamaspeto.com
