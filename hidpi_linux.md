### check current X settings
> $ xdpyinfo | grep -B 2 resolution

### force dpi using xrandr
> $ xrandr --dpi 150

### put configuration in XResource
```
Xft.dpi: 180
Xft.autohint: 0
Xft.lcdfilter:  lcddefault
Xft.hintstyle:  hintfull
Xft.hinting: 1
Xft.antialias: 1
Xft.rgba: rgb
```

### scale up chromium application
> $ <app-name> --force-device-scale-factor=X.X

### make firefox great again
> set layout.css.devPixelsPerPx to 2 in `about:config`  
create a `userChrome.css` file under `~/.mozilla/firefox/9roo6reo.default/chrome/`  
with the following in it:
```
@namespace url("http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul"); /* set default namespace to XUL */
* { font-size: 12px !important; }
```
