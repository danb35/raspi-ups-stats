# raspi-ups-stats

Script to show system and UPS statistics on a Raspberry Pi with [UPS Plus](https://wiki.52pi.com/index.php/UPS_Plus_SKU:_EP-0136?spm=a2g0o.detail.1000023.17.4bfb6b35vkFvoW) board and [128x64 OLED display](https://www.amazon.com/dp/B08LYL7QFQ?psc=1&ref=ppx_pop_dt_b_product_details).

## Installation

### Prerequisites

If you're using Raspbian/Raspberry Pi OS, you'll need to enable I2C using `raspi-config`.  You'll then need to install several dependencies with `sudo apt install git i2c-tools python3-pip python3-smbus python3-setuptools python3-pil python3-rpi.gpio libraspberrypi-bin`.

Next, you'll need to download Adafruit's Python library for the OLED display.  `git clone https://github.com/adafruit/Adafruit_Python_SSD1306.git`.  Then `cd Adafruit_Python_SSD1306.git`, `sudo python3 setup.py install`.

Finally, you'll need to download the font files from https://www.dafont.com/pixel-operator.font.  The font file `PixelOperator.ttf` will need to be placed in the same directory as the executable script.

### Download and install

Change to a convenient directory and run `git clone https://github.com/danb35/raspi-ups-stats`.

## Auto start on boot
Create `/opt/stats/`, and copy `PixelOperator.ttf` and `stats.py` there.

Then put the systemd unit file in the correct place: `sudo cp stats.service /etc/systemd/system/`.

Then tell systemd to re-scan the unit files with `sudo systemctl daemon-reload`, and start this unit using `sudo systemctl enable --now stats`.

## Acknowledgements

Original source: https://www.the-diy-life.com/mini-raspberry-pi-server-with-built-in-ups/
Based on: https://github.com/adafruit/Adafruit_Python_SSD1306/blob/master/examples/stats.py
