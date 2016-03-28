# rpisurv - Raspberry pi surveillance an RPI IP Camera Monitor
Follow us on facebook https://www.facebook.com/rpisurv

## Goal
Rpisurv is designed to be simple to use. The goal is to connect your raspberry pi 2 to a monitor, tell rpisurv which rtsp streams it should display and tell it the max number of "columns" of streams you want. It will then autocalculate the rest, like how many rows are needed etc ...

## Description
You can think of rpisurv as a wrapper for omxplayer with following features. Rpisurv uses omxplayer to fully make use of the GPU of the raspberry pi 2.

- Rpisurv implements a watchdog for every stream displayed, if the process gets killed somehow. It will try to restart the stream/process. This gives you a very robust surveillance screen.
- Autocalculcate coordinates for every stream displayed. The last stream defined will be stretched to make use of the complete screen but only if some pixels are unused.
- RTSP stream up/down detection and autorearrange of the screen layout. So for example if you stop a camera (or just stop the rtsp server on the camera), rpisurv will detects this and will recalculate/redraw the screen with the still available cameras. The same is true if a previous unconnectable rtsp stream becomes connectable. All without any user interaction.

## How to get started

- Get a monitor or a TV
- Get a raspberry pi 2 dedicated for rpisurv, and install raspbian on it. Make sure your monitor is operating at the correct resolution
- If you are going to have multiple streams, add gpu_mem=512 to your /boot/config.txt
- git clone this repository: `git clone git@github.com:SvenVD/rpisurv.git`
- run `install.sh` as the root user
- Get the correct rtsp stream url for your ip camera(s), there are some examples in /etc/rpisurv
- configure your rtsp streams in /etc/rpisurv.
- configure your max number of columns in /etc/rpisurv
- reboot

## Rpisurv in operation

If you used the install.sh script, you can configure your streams in /etc/rpisurv. Do not forget to reboot afterwards.

## Troubleshooting

I advise you to test your rtsp urls in vlc or omxplayer (command line) first. It should work in these applications before attempting to use them in rpisurv

If you used the install.sh script, logs are created at /usr/local/bin/rpisurv/logs/. You can use them for troubleshooting.

To start the screen without rebooting, run `cd /usr/local/bin/rpisurv`; python surveillance.py
