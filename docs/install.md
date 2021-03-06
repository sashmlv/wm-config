### Installation:
* Install [stack](https://github.com/commercialhaskell/stack): ```curl -sSL https://get.haskellstack.org/ | sh```
* Add Stack into environment path: ```sudo nano ~/.profile```
```
# stack
export PATH=$PATH":/home/$USER/.local/bin"
```
* Reboot: ```sudo reboot```
* Install GHC: ```stack setup```
* Then:```mkdir ~/.xmonad && cd ~/.xmonad```
* ```git clone https://github.com/xmonad/xmonad```
* ```git clone https://github.com/xmonad/xmonad-contrib```
* ```git clone https://github.com/jaor/xmobar```
* From inside ```~/.xmonad```: ```stack init```
* Edit ```stack.yaml```: ```sudo nano stack.yaml```
```
extra-deps:
- iwlib-0.1.0
- alsa-mixer-0.3.0
- netlink-1.1.1.0
- libmpd-0.9.2.0
flags:
  xmobar:
    all_extensions: true
```
* Install libraries:
```
sudo apt install libiw-dev
sudo apt install libasound2-dev
# for xmonad
sudo apt install libx11-dev libxinerama-dev libxext-dev libxrandr-dev libxss-dev
# for xmonad-contrib
sudo apt install libxft-dev

```
* From inside ```~/.xmonad```: ```stack install```
* Write a build file: ```sudo nano ~/.xmonad/build```
```
#!/bin/sh
exec stack ghc -- \
  --make xmonad.hs \
  -i \
  -ilib \
  -fforce-recomp \
  -main-is main \
  -v0 \
  -o "$1"
```
* Make file executable: ```sudo chmod a+x build```
* Copy config: ```cp -R xwm-config/.xmonad ~/```
* Make file executable: ```sudo chmod +x ~/.xmonad/xmonad-run.sh```
* Overview files and install fonts from it, or replace by your
* Install libraries, for wallpaper support: ```sudo apt install libcurl4-openssl-dev libx11-dev libxt-dev libimlib2-dev libxinerama-dev libjpeg-progs feh```
* Transparency support: [picom](https://github.com/sashmlv/xwm-config/blob/master/docs/picom.md)
* Screenshot utility: ```sudo apt install flameshot```
* If ```xrdb``` utility is not installed, try install X-server utils: ```sudo apt install x11-xserver-utils```
* For volume control, the ```amixer``` and ```pactl``` apps maybe preinstalled, if doesn’t: ```sudo apt install pulseaudio-utils pavucontrol```
* Application launcher: [rofi](https://github.com/davatorium/rofi), [manual](https://github.com/davatorium/rofi/blob/next/INSTALL.md) (prefer) or ```sudo apt install rofi```
* Check ```terminal``` value in ```xmonad.hs``` and set your (for [alacritty](https://github.com/jwilm/alacritty) edit and copy ```alacritty.yml``` into ```~/.config/alacritty/```)
* Maybe you want [fish](https://github.com/fish-shell/fish-shell)
* We want choose xmonad at login page (note the user name at path below): ```sudo nano /usr/share/xsessions/xmonad.desktop```
```
[Desktop Entry]
Encoding=UTF-8
Name=XMonad
Comment=Lightweight tiling window manager
Exec=/home/user/.xmonad/xmonad-run.sh
Icon=xmonad.png
Type=XSession
```
* Fix access rights: ```sudo chmod -R 755 ~/.xmonad/```
* Reboot to ensure: ```sudo reboot```
* Compile: ```xmonad --recompile && xmonad --restart```
* Reboot and choose XMonad session at login page: ```sudo reboot```
* For update everything: ```stack install```
* After change ```stack.yaml```, run stack clean first: ```stack clean```
