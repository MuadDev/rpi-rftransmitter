rpi-rftransmitter
=================
Tools for scanning, recording and playing RF signals. Made mostly for 433 mhz outlet switches.

Requires [wiringPi](http://wiringpi.com) to compile and run.

Run `make` build and `make install` to install to `/usr/local/bin`.

### rfscanner
Simply outputs all received signals:
```
Usage: rfscanner [options]
Options:
  -p <number>, --pin <number>   The input (wiringPi) pin number (see http://pinout.xyz
                                for details, default: 2)
```

### rfrecorder
Looks for a pattern in received signals and stores it in a file.
```
Usage: rfrecorder [options]
Options:
  -o <path>, --output <path>    Specifies the output file path
  -p <number>, --pin <number>   The input (wiringPi) pin number (see http://pinout.xyz
                                for details, default: 0)
  --buffer-size <size>          The size of the input buffer (default: 250)
  --record-samples <samples>    The number of samples recorded (default: 5)
  --record-failures <count>     The number of samples not matching previous samples
                                before discarding all previous samples (default: 2)
```

### rfplayer
Plays a file created by rfrecorder
```
Usage: rfplayer <filename> [options]
Options:
  -p <number>, --pin <number>   The input (wiringPi) pin number (see http://pinout.xyz
                                for details, default: 0)
  -t <ms>, --playtime <ms>      The total playtime in milliseconds (default: 500)
  ```
  
## requirements
WiringPi: http://wiringpi.com/download-and-install/

If this requirement has not been met the following error will show:
```
 #include <wiringPi.h>
                      ^
compilation terminated.
Makefile:25: recipe for target 'rfrecorder' failed
make: *** [rfrecorder] Error 1
```

## remotes
Currently the codes for the following remotes are added:
- A (KlikAanKlikUit)
- B (Flamingo)

These are recorded using the command `rfrecord` and the following hints:
- Use data wiring pi pin 3 instead of 2
- Turn off the wireless keyboard & mouse
- Put the Pi in the bedroom
- Keep the controller almost against the receiver
- Remove the RF transmitter
- When recording pay attention to the mentioned command size, this should be (around) 132 and not (around) 4. The former is an actual signal, the latter means only noise is captured.
