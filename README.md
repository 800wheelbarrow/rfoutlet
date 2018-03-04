#### 433MHz RF power outlet control

Slightly modified from the original version:

* Can be used offline (Bootstrap and jQuery files are stored locally)
* Dark theme for web page
* Web app compatible (adds a shortcut to your home screen, removes browser controls)

**Some setup steps:** 

Connect the transmitter module/breadboard to the Pi like this:
* GND (left pin near coil) = Ground
* GPIO (center pin) -> GPIO #17 (also known as GPIO #0)
* VCC (right pin) -> 5 volts

Connect the receiver module (only necessary to capture the RF codes from the remote):

* VCC (left pin) -> +5VDC
* DATA (2nd pin from left) -> GPIO 21/27
* GND (far right pin) -> Ground

To set up the software on the Pi:

```
sudo apt-get install apache2 php5 libapache2-mod-php5 -y
git clone https://github.com/800wheelbarrow/rfoutlet.git /var/www/html/rfoutlet
sudo chown root.root /var/www/html/rfoutlet/codesend
sudo chmod 4755 /var/www/html/rfoutlet/codesend
```

To capture the RF codes, run the following program and press the remote buttons:
```
sudo /var/www/html/rfoutlet/RFSniffer
```

Edit /var/www/html/rfoutlet/toggle.php with the codes displayed from the last step.

To manually send codes (for testing purposes), run:

```
sudo /var/www/html/rfoutlet/codesend 5575987
```