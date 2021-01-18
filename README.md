# dbus-ruuvi
Read data from Ruuvi sensor and publish on Venus OS D-Bus

## Dependencies
There are currently two dependencies, and since this is all a bit hacked together as a proof of concept now, I simply took the folders I needed from the repos where I got it from:

- ptyprocess:  copied from this subdir https://github.com/pexpect/ptyprocess/tree/master/ptyprocess
- ruuvitag-sensor: copied from this subdir https://github.com/ttu/ruuvitag-sensor/tree/master/ruuvitag_sensor
- ext/velib_python: anyone familiar with Venus OS will know where that was copied from

## Installation
Clone this repo, and the run more or less these commands on the commandline of the GX Device:
``` 
/opt/victronenergy/swupdate-scripts/resize2fs.sh
/opt/victronenergy/swupdate-scripts/set-feed.sh release
opkg update
opkg install python-terminal
opkg install python-resource
```

And then from your host, run:
```
scp -r -P 4000 ./dbus-ruuvi root@localhost:~/
```

## Things to do
As said, this is merely a proof of concept. Even though it seems to run rather stable on the system where this all began since I needed to monitor a few temperatures.

Roughly what needs doing is:

- Replace ext/velib_python by a proper submodule
- Make it invalidate data if no more updates come in.
- Support configuring a Custom name
- Add publishing of humidity, battery level, motion and possible other data
- Remove all the ruuvitag-sensor code, and replace by something more elegant. This starts hcidump as a process and parses its output.


And more work and outside of the Python scope: find a way to extend the range.
