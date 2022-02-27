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

## Others Installed Programs

### `fzf`

### `starshipt`

### `foliate`

### `okular`

### `btop`

### `flameshot`

## Audio Adjustments
### Pulse
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

### Problems with Microphone
- [Headset microphone not working](https://askubuntu.com/questions/1230016/headset-microphone-not-working-on-ubuntu-20-04)
- [Microphone from headset not working](https://forums.linuxmint.com/viewtopic.php?t=299427)


## Terminal Theme
### Gnome
- [Color Schema Gogh](https://mayccoll.github.io/Gogh/)
- [Dracula Gnome Terminal](https://github.com/dracula/gnome-terminal)

## Questions 
- What is swappiness?

```
cat /proc/sys/vm/swappiness
// 60

sudo xed /etc/sysctl.conf

// last line insert: 
// vm.swappiness=10 

// save file & reboot
```

- What is timestamp write and why do we disable them when using SSD?
    - [system performance with noatime](https://opensource.com/article/20/6/linux-noatime)

- What is the package mannager `cargo`?
    - `cargo install exa`

- What is `exa`?
    - A replacement for the comand `ls`? 


## Terminal file manager for the console
### `ranger`
```
sudo apt install ranger

``` 

## Application Launcher
### `rofi`
[Rofi](https://github.com/davatorium/rofi) is a window switcher, Application launcher and dmenu replacement.
```
sudo apt install rofi
```

## Command-line System Information Tool
### `neofetch`
[Neofetch](https://github.com/dylanaraps/neofetch) is a command-line system information tool written in bash 3.2+. Neofetch displays information about the operating system, software and hardware in an aesthetic and visually pleasing way.

### `inxi`
- Fetching System Information using Inxi: `inxi -Fxz`


## Things to Figure out How to use Through the Terminal
- Driver Manager
- Change location Mirrors
  ![image](https://user-images.githubusercontent.com/17462762/154803226-8b99716c-1cc9-4d1e-933f-9b00fb45a83c.png)
- Install codecs (multimedia)
    - What is codecs?
- Install microsoft fonts
    - I installed through Synaptic Package Manager (Synaptic Package Manager)
- Custom Shortcuts

https://draculatheme.com/gnome-terminal
