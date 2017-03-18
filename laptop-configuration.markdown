---
layout: page
title: "i3wm config"
subtitle: "My laptop configuration with i3wm"
permalink: my-laptop-configuration-with-i3wm.html
---


## Introduction

I'm a huge fan of tiling window manager, and I've been using [i3wm](http://i3wm.org) for several years now, and I can't see myself going back to classic window management… It would be a huge step back in term of efficiency for me… 

But by using this kind of window manager (also like awesome, xmonad or other), you "loose" things that usually the desktop environment (gnome, kde, unity, …) does for you. And for a lot of people this is a big issue… Whereas for me this is an opportunity to only configure what I want my system to do and not let the DM do its stuff on its own...

So this simple page is supposed to be an up to date page of my laptop setup. It might evolve with time when adding new configuration (eg: at the moment, there is a todo for the multiscreen auto management as I'm not 100% happy of my current setup).

**PS**: The goal is not to copy / paste my i3wm config and add comments, if you want details on i3wm configuration, look at the documentation or find config files on github (mine can also be found there).


## Brightness

I use ```xbacklight``` to manage the brightness on my laptop.

### Manual

My i3wm shortcuts:

```
bindsym XF86MonBrightnessUp exec xbacklight -inc 5
bindsym XF86MonBrightnessDown exec xbacklight -dec 5
```

### On power (un)plug

Manual changing is good, but I also like to automate that when I (un)plug my power supply to my laptop. To do so create a udev rule ```/etc/udev/rules.d/98-power_supply.rules``` with the following:


```
ACTION=="change", SUBSYSTEM=="power_supply", ATTR{type}=="Mains", ATTR{online}=="0", ENV{DISPLAY}=":0", ENV{XAUTHORITY}="/home/bacardi55/.Xauthority", RUN+="/usr/bin/xbacklight -set 33"
ACTION=="change", SUBSYSTEM=="power_supply", ATTR{type}=="Mains", ATTR{online}=="1", ENV{DISPLAY}=":0", ENV{XAUTHORITY}="/home/bacardi55/.Xauthority", RUN+="/usr/bin/xbacklight -set 75"
```

## Keyboard shortcuts

### session and screenlock

I'm using a [i3wm mode](https://i3wm.org/docs/userguide.html#binding_modes) to manage the different choices (like when you click on the shutdown button in a Desktop manager)

```
set $mode_system System (l) lock, (e) logout, (s) suspend, (h) hibernate, (r) reboot, (Shift+s) shutdown
mode "$mode_system" {
    bindsym l exec --no-startup-id i3exit lock, mode "default"
    bindsym e exec --no-startup-id i3exit logout, mode "default"
    bindsym s exec --no-startup-id i3exit suspend, mode "default"
    bindsym h exec --no-startup-id i3exit hibernate, mode "default"
    bindsym r exec --no-startup-id i3exit reboot, mode "default"
    bindsym Shift+s exec --no-startup-id i3exit shutdown, mode "default"

    # back to normal: Enter or Escape
    bindsym Return mode "default"
    bindsym Escape mode "default"
}
bindsym $mod+Delete mode "$mode_system"
```
For example, ```window + Delete, then l ``` will lock my sreen using [i3lock](https://i3wm.org/i3lock/)


### Media

#### Volume

My shortcuts to manage sound changes (via pulseaudio):

```
bindsym XF86AudioRaiseVolume exec --no-startup-id pactl set-sink-volume 0 +5% #increase sound volume
bindsym XF86AudioLowerVolume exec --no-startup-id pactl set-sink-volume 0 -5% #decrease sound volume
bindsym XF86AudioMute exec --no-startup-id pactl set-sink-mute 0 toggle # mute sound
```

#### Media player

And to mangae media key for [MPD](https://www.musicpd.org/) (my local audio player)

```
bindsym XF86AudioPlay exec mpc --host "password@localhost" --port 1234 toggle
bindsym XF86AudioPause exec mpc --host "password@localhost" --port 1234 toggle
bindsym XF86AudioNext exec mpc --host "password@localhost" --port 1234 next
bindsym XF86AudioPrev exec mpc --host "password@localhost" --port 1234 prev
```

Don't forget to change the password and port !


#### screenshot

Using the simple ```import``` software to do so:

```
bindsym --release $mod+x exec --no-startup-id import ~/latest-screenshot.png
```


## Opening / closing Lid

Suspend to RAM when closing the lid, via systemd:

Create a file ```/etc/acpi/lid.sh```, and add the following:

```
##!/bin/sh

grep -q closed /proc/acpi/button/lid/*/state

if [ $? = 0 ] ; then
	/bin/systemctl suspend
fi
```

## Multi screen switch

### Manual script

```
xrandr --output eDP1 --primary --mode 3200x1800 --pos 3840x192 --rotate normal --output DP1-1 --mode 1920x1080 --pos 0x0 --rotate normal --scale 2x2
```

### Automate when plugging screen

TODO (not fully happy with this part yet)!

