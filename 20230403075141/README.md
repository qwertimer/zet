# Use xvfb for display in CI

When running UI code in CI the system will often fail without a display.
To fix this we can use
[xvfb](https://linuxhint.com/install-xvfb-ubuntu/) to fake a UI for CI
builds. For this to work we need to run 
```bash
export DISPLAY=:99
Xvfb -ac :99 -screen 0 1280x1024x24 > /dev/null 2>&1 &
```
to export the display to a number which is then referenced in the call
to xvfb.


