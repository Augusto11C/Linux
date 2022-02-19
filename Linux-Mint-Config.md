# Linux Mint Configuration

## Resolution Adjustments (`xrandr` and `gtf`)

### Detect resolution automatically
```
sudo xrandr --output HDMI-0 --auto
```

### Selecting an existing resolution

Enumerate the names of all your video outputs, and the possible resolutions for those currently connected to a monitor:

```
xrandr -q
```

Choose the name of the output you wish to change the resolution of, and:

```
xrandr --output <OUTPUT> --mode 1024x768
```

### Creating a Resolution

- First use gtf to create a mode line

```
$ gtf 2560 1080 60


// Output
# 2560x1080 @ 60.00 Hz (GTF) hsync: 67.08 kHz; pclk: 230.76 MHz
  Modeline "2560x1080_60.00"  230.76  2560 2728 3000 3440  1080 1081 1084 1118  -HSync +Vsync

```
- Create a new mode using xrandr and parameters from previous command

```
xrandr --newmode "2560x1080_60" 230.76  2560 2728 3000 3440  1080 1081 1084 1118  -HSync +Vsync
```

- Now you need to add the mode to the desired output, in your case it seems to be HDMI-0

```
xrandr --addmode HDMI-0 2560x1080_60
```

- Applying the new mode

```
xrandr --output HDMI-0 --mode 2560x1080_60
```

- More about resolution adjustment using `xrandr`
    - [Link 1](https://askubuntu.com/questions/1075157/unable-to-set-my-screen-resolution-higher)
    - [Link 2](https://askubuntu.com/questions/281509/how-do-i-change-the-screen-resolution-using-ubuntu-command-line)

### Deleting custom resolution from `xrandr`
```
xrandr --delmode <output> <name>
```

### Find the current display

```
$ xrandr | grep -e " connected [^(]" | sed -e "s/\([A-Z0-9]\+\) connected.*/\1/"
```




## Audio Adjustments (Pulse Audio)
```
$ sudo apt install pulseaudio-equalizer

$ qpaeq

// If it fails like -> "There was an error connection to pulseaudio..."

// Try config bellow

$ sudo nano /etc/pulse/default.pa

// Add the below-given lines at the bottom of the/etc/pulse/default.pa file.
load-module module-equalizer-sink
load-module module-dbus-protocol


$ pulseaudio --kill && pulseaudio --start

```
