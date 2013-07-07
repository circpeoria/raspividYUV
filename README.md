RaspiVidYUV Documentation
======================

This application is intended to output a raw YUV video stream. Nearly all of the options available for RaspiVid are available for this application with the exception of demo mode and the preview window. To build, this application expects https://github.com/raspberrypi/userland.git to be cloned to /opt/vc/userland. After that:

   cmake .
   make

To run:

   cd bin
   ./raspividyuv -o test.yuv

Camera Control Options
======================

    --sharpness,  -sh       | Set image sharpness (-100 to 100)

Set the sharpness of the image, 0 is the default.

    --contrast,  -co        | Set image contrast (-100 to 100)

Set the contrast of the image, 0 is the default

    --brightness,  -br      | Set image brightness (0 to 100)

Set the brightness of the image, 50 is the default. 0 is black, 100 is white.

    --saturation,  -sa      | Set image saturation (-100 to 100)

set the colour saturation of the image. 0 is the default.

    --ISO,  -ISO            | Set capture ISO

Not yet implemented

    --vstab,  -vs           | Turn on video stabilisation

In video mode only, turn on video stabilisation.

    --ev,  -ev              | Set EV compensation

Set the EV compensation of the image. Range is -10 to +10, default is 0.

    --exposure,  -ex        | Set exposure mode 

Possible options are: 

        off          
        auto          Use automatic exposure mode
        night         Select setting for night shooting
        nightpreview 
        backlight     Select setting for back lit subject
        spotlight    
        sports        Select setting for sports (fast shutter etc)
        snow          Select setting optimised for snowy scenery
        beach         Select setting optimised for beach
        verylong      Select setting for long exposures
        fixedfps      Constrain fps to a fixed value
        antishake     Antishake mode
        fireworks     Select settings

Note that not all of these settings may be implemented, depending on camera tuning.

    --awb,  -awb              | Set Automatic White Balance (AWB) mode
    
Possible options are: 

        off           Turn off white balance calculation
        auto          Automatic mode (default)
        sun           Sunny mode
        cloud         Cloudy mode
        shade         Shaded mode
        tungsten      Tungsten lighting mode
        fluorescent   Fluorescent lighting mode
        incandescent  Incandescent lighting mode
        flash         Flash mode
        horizon       Horizon mode

Set an effect to be applied to the image

    --imxfx,     -ifx         | Set image effect

Possible options are: 

        none           NO effect (default)
        negative       Negate the image
        solarise       Solarise the image
        posterize      Posterise the image
        whiteboard     Whiteboard effect
        blackboard     Blackboard effect
        sketch         Sketch style effect
        denoise        Denoise the image
        emboss         Emboss the image
        oilpaint       Apply an oil paint style effect
        hatch          Hatch sketch style
        gpen          
        pastel         A pastel style effect
        watercolour    A watercolour style effect
        film           Film grain style effect
        blur           Blur the image
        saturation     Colour saturate the image
        colourswap     Not fully implemented
        washedout      Not fully implemented
        posterise      Not fully implemented
        colourpoint    Not fully implemented
        colourbalance  Not fully implemented
        cartoon        Not fully implemented

Colour control

    --colfx,  -cfx          | Set colour effect <U:V>

The supplied U and V parameters (range 0 to 255) are applied to the U and Y channels of the image. For example, --colfx 128:128 should result in a monochrome image.

    --metering,  -mm        | Set metering mode

Specify the metering mode used for the preview and capture

        average   Average the whole frame for metering.
        spot      Spot metering
        backlit   Assume a backlit image
        matrix    Matrix metering


Application specific settings
=============================

RaspiVid
--------

    --width,  -w            | Set image width <size>

Width of resulting video. This should be between 64 and 1920.

    --height,  -h           | Set image height <size>

Height of resulting video. This should be between 64 and 1080.

    --bitrate,  -b          | Set bitrate. 

Use bits per second, so 10MBits/s would be -b 10000000. For H264, 1080p a high quality bitrate would be 15Mbits/s or more.

    --output,  -o           | Output filename <filename>.

Specify the output filename. If not specified, no file is saved

    --verbose,  -v          | Output verbose information during run

Outputs debugging/information messages during the program run.

    --timeout,  -t          | Time before takes picture and shuts down.

The program will run for this length of time, then take the capture (if output is specified). If not specified, this is set to 5seconds

    --framerate,  -fps      | Specify the frames per second to record

At present, the minimum frame rate allowed is 2fps, the maximum is 30fps. This is likely to change in the future.



Examples
========

Video Captures
--------------

Image size and preview settings are the same as for stills capture. Default size for video recording is 1080p (1920x1080)

Record a 5s clip with default settings (1080p30)

    ./raspividyuv -t 5000 -o video.yuv

Record a 5s clip at a specified bitrate (3.5MBits/s)

    ./raspividyuv -t 5000 -o video.yuv -b 3500000

Record a 5s clip at a specified framerate (5fps)

    ./raspividyuv -t 5000 -o video.yuv -f 5


