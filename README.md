# SWHR RTMP Camera Streaming

This application is designed to stream the RTSP output of a FOSCAM camera to our streaming server.

## Installation

You'll need to install dependencies with:

```
sudo apt install ffmpeg git curl
sudo ufw allow 10000/udp
```

Then download this repository to the Raspberry Pi and install the system service:

```
git clone https://github.com/philcrump/swhr-rtmp-camera
cd swhr-rtmp-camera/
./install
```

The software will not be running at this point. You need to configure it first:

## Scan for camera

You can scan for FOSCAM camera IP addresses on the local network with this tool, press Ctrl+C to exit.

`./foscam-scan`

## Configuration

Copy _camera-credentials.template_ to _camera-credentials_

Edit _camera-credentials_ with the following information:

 * `CAMERA_IP_ADDRESS`
 * `CAMERA_USERNAME`
 * `CAMERA_PASSWORD`
 * `CAMERA_STREAMNAME` - This'll either be "videoMain" or "videoSub" for the Main or Sub encoder streams.

 * `RTMP_STREAM_KEY` - This is the secret upload key for the video stream, contact Phil M0DNY if you don't have it.
 * `RTMP_STREAM_NAME` - This is the public name of the video stream, needs to match the secret upload key, contact Phil M0DNY if you don't have it.

## Run

Start the services with:

`./start`

Watch for the camera to appear on the public webpage, which may take 30 seconds or so.

If all goes well, the SSH console to the Raspberry Pi can now be closed and the application will continue to run. It will automatically start again if the Raspberry Pi is rebooted.

## Watch

You can watch the debug output of the commands with:

`./watch`

Press Ctrl+c to exit.
