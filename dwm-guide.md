# DWM Guide
#### DWM: http://dwm.suckless.org/
![](http://dwm.suckless.org/screenshots/dwm-20100318.png)
Start DWM: `exec dwm`
```
DWM Structure:
     +------+----------------------------------+--------+
     | tags | title                            | status +
     +------+---------------------+------------+--------+
     |                            |                     |
     |                            |                     |
     |                            |                     |
     |                            |                     |
     |          master            |        stack        |
     |                            |                     |
     |                            |                     |
     |                            |                     |
     |                            |                     |
     +----------------------------+---------------------+
[Shift]+[Alt]+[Enter] - launch terminal
[Alt]+[p] - dmenu for running programs like the x-www-browser
[Alt]+[Enter] toggles windows between master and stack.

[Alt]+[j] or [Alt]+[k] - move to another terminal
[Shift]+[Alt]+[2] - move a terminal to another tag
[Alt]+[tag number] - focus another tag or LEFT CLICK
[Alt]+[d] or [Alt]+[i] - move from master to stack
[Shift]+[Alt]+[c] - close
[Shift]+[Alt]+[q] - quit DWM

[Alt]+[t] - tile
[Alt]+[f] - floating
	[Alt]+[right mouse button] - resize
	[Alt]+[left mouse button] - move
	[Alt]+[Shift]+[space] - float active window
	[Alt]+[middle mouse button] - to toggle float
[Alt]+[m] - monocle
