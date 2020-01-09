# SWHR RTMP Camera Streaming

This application is designed to stream the RTSP output of a FOSCAM camera to our streaming server.

## Installation

You'll need to install ffmpeg with:

`sudo apt install ffmpeg`

Then download this repository to the RPi, you can either use the `git` command as below, or download a TAR from here: [master.tar.gz](https://github.com/philcrump/swhr-rtmp-camera/archive/master.tar.gz)

`git clone https://github.com/philcrump/swhr-rtmp-camera`

Change directory into the repository, and install the service scripts (this will set them to start on next boot)

```
cd swhr-rtmp-camera/
./install
```

The scripts will not be running at this point. You need to configure them first.

## Configuration

There are several parameters in the top of each file that need configuring before use:

### _camera-rtmp_

 * `CAMERA_IP` - If unknown this can be found by scanning with the command `./foscan-scan`, press Ctrl+c to exit.
 * `CAMERA_USERNAME`
 * `CAMERA_PASSWORD`
 * `CAMERA_STREAMNAME` - This'll either be "videoMain" or "videoSub" for the Main or Sub encoder streams.

 * `SERVER_STREAM_KEY` - This is the secret upload key for the video stream, contact Phil M0DNY if you don't have it.

### _rtmp-watchdog_

 * `SERVER_STREAM_NAME` - This is the public name of the video stream, needs to match the secret upload key, contact Phil M0DNY if you don't have it.

## Run

Start the services with:

`./start`

If all goes well, the SSH console to the RPi can now be closed and the application will continue to run. It will also automatically start if the RPi is rebooted.

## Watch

You can watch the debug output of the commands with:

`./watch`

Press Ctrl+c to exit.