# **bash** Send POST with JSON data:
```
curl -X POST --data @filename.json -H "Content-Type: application/json" http://localhost:8080/
```
# **bash** Create 7zip archive with 4GB size and password:
```
7z a SOME_NAME.7z -v4000m SOURCE_TO_PACK/ -p=SOME_PASSWORD
```

# **bash** Bash clipboard:
```
Ctrl-u Ctrl-y
```

# **bash** Replace and execute last command:
```
^CHANGE_THIS^TO_THIS
```

# **bash** Other shortcuts:
```
Ctrl + U Delete to beginning of command from current cursor position.
Ctrl + K Delete to end of command from current cursor position.
Ctrl + R Reverse search history
Ctrl + - Incremental undo
```

# **bash** Replacement for arrows, Home and End keys in terminal:
```
  Up Arrow:    Ctrl + p
  Down Arrow:  Ctrl + n
  Left Arrow:  Ctrl + b
  Right Arrow: Ctrl + f
  Home:        Ctrl + a
  End:         Ctrl + e
```

# **bash** Shorthands and Magic variables:
```
!!                          The last command
!$                          The last argument from the last command.
![word]                     The last command starting with [word]
![word]:p                   Print the last command starting with [word] (but do not run)
^[word]^[replacement]       Find last command starting with [word] and re-run it with [replacement].
[command] [argument]{a,b,c} Run [command] with [argument] three times, each time changing the postfix to a, then b, then c. For example, mkdir test{1,2} would make two directories: test1 and test2
set -o vi                   Use vi-like movement to edit commands :)
```

# **bash** Copy all directory:
```
cp -R dirName target/newDirName
```

# **bash** Kill some connection:
```
tcpkill host IPADDRESS
```

# **bash** Add user public ssh key to authorized keys on server:
```
cat ~/.ssh/id_rsa.pub | ssh username@hostname 'cat >> .ssh/authorized_keys'
or
ssh-copy-id root@someAddress
```

# **bash** Some bash oneliner:
```
for f in *.txt; do mv "$f" `echo $f | sed s/old/new/`; done
```

# **bash** Show connection to specific IP:
```
netstat -an IPADDRESS | grep EXAMPLE_IP
```

# **tmux** Go to two-digit window number:
```
CTRL + b + w
```

# **virtualbox** Harddisk uuid error:
```
VBoxManage internalcommands sethduuid disk.vhd
```

# **unix** Check services:
```
netstat -plnt
```

# **bash** Write terminal commands in editor:
```
#must be set EDITOR=vim in .bashrc
Ctrl-x Ctrl-e
```

# **bash** Go to previous localization and go to home localization:
```
cd -
cd
```

# **bash** Change two letters in command:
```
Ctrl + t
```

# **unix** Show which process is running on specific port:
```
lsof -i :15672
```

# **git** Show status of the file before the last 4 commits:
```
git show HEAD~4:src/main.js
```

# **git** Merge two last commits into one commit:
```
git rebase --interactive HEAD~2
```

# **git** Remove .DS_Store files from repository:
```
# remove any existing files from the repo, skipping over ones not in repo
find . -name .DS_Store -print0 | xargs -0 git rm --ignore-unmatch
# specify a global exclusion list
git config --global core.excludesfile ~/.gitignore
# adding .DS_Store to that list
echo .DS_Store >> ~/.gitignore
```

# **git** Autocomplete git commands:
```
brew install bash-completion
and add to .bash_profile:
if [ -f `brew --prefix`/etc/bash_completion ]; then
    . `brew --prefix`/etc/bash_completion
fi
```

# **git** Name of branch in prompt:
```
# add this to .bash_profile
parse_git_branch() {
    git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/ (\1)/'
}

export PS1="\u@\h \w\[\033[32m\]\$(parse_git_branch)\[\033[00m\]$ "
```

# **git** Interactive adding files:
```
git add -i
```

# **git** Remove all feature branches:
```
git branch -D `git branch | grep -E 'feature*'`
```

# **git** Prune branches (dry run):
```
git remote prune origin --dry-run
```

# **git** Show number of commits per author:
```
git shortlog -s -n
```

# **vim** Solve problem with modifiable off message:
```
:autocmd BufWinEnter * setlocal modifiable
```

# **vim** Replace in all files in agrs:
```
:argdo %s/pattern/replace/ge | update
```

# **vim** Run macro in 'a' register for line which match pattern:
```
:g/pattern/norm! @a
```

# **vim** Move text from vim register to tmux pane and execute:
```
call system("tmux load-buffer -", @r)
call system('tmux paste-buffer -t "s01:repl.1"')
```

# **vim** Surrounding word in parentheses:
```
viwxi()<esc>P
```

# **vim** Bind command for example eslint to key:
```
map <f5> :!eslint %<cr>
```

# **vim** Create alias for long text:
```
imap =tlt test long text
```

# **vim** Hex view:
```
Turn on:  :%!xxd
Turn off: :%!xxd -r
```

# **vim** Change size of panes:
```
Width: 10 CTRL + w + > 
Height: 10 CTRL + w + + 
```

# **vim** Replace text in all specified files:
```
:argsadd ./path/*.js //dodaje ścieżkę do zmiennej args
:arg //wyświetla pliki
:argdo %s/pattern/replace/ge | update //podmienia
```

# **vim** Case sensitive replace:
```
:%s/foo/bar/gI
```

# **vim** Replace this word (not when this is a part of other word):
```
:%s/\/bar/g
```

# **vim** Set color column in all panes:
```
set colorcolumn=80
```

# **vim** Open few files one beside another:
```
:args app/views/*.erb | vertical all
```

# **vim** Change mode of explorer:
```
Press: i
```

# **vim** Ignore node_modules directory in vimgrep:
```
set wildignore+=**/node_modules/**python
```

# **vim** Prettify JSON:
```
:%!python -m json.tool
```

# **vim** Change ^M:
```
:%s/^M//g
#to write ^M press Ctrl+V+M
```

# **vim** Change file format from unix to dos:
```
:update
:e ++ff=dos
:w osx
```

# **vim** Save file with sudo:
```
:w !sudo tee %
```

# **vim** Switching between localizations:
```
Previous: Ctrl-O
Next: Ctrl-I
```

# **vim** List of last localizations:
```
:jumps
```

# **vim** Alignment to columns:
```
:!column -t
:%!column -t -s ','
```

# **docker** Clean up
```
docker-compose down
docker rm -f $(docker container ls -aq)
docker-compose rm -v
docker volume prune
docker system prune
```

# **linux** Unknown Linux
```
free -m
netstat -plnt
apt-get purge apache2
ps aux | grep apache
/etc/init.d/sendmail stop
apt-get purge sendmail
dpkg-reconfigure locales
//pl_PL ISO-UTF ISO-8859-2
apt-get update
apt-get install php5 php5-mysql mysql-server mysql-client nginx
top // Shift-m
apt-get purge apache2*
vim /etc/mysql/my.cnf
[mysqld]
skip-innodb
key_buffer = 2M
query_cache_size = 3M
max_connections = 40
/etc/init.d/mysql restart
/etc/init.d/saslauthd stop
dpkg -l | grep sasl
apt-get remove sas;2-bin
/etc/init.d/xinetd stop
apt-get remove xinetd
apt-get install dash //only for scripts
dpkg-reconfigure dash //yes
vim /etc/init.d/mysql
#!/bin/sh
/etc/init.d/mysql restart
/etc/init.d/nginx start
ca /proc/cpuinfo
vim /etc/nginx/nginx.conf
worker_processes 1;//the same as cpu cores
worker_connections 1024
sendfile on;
keepalive_timeout 5;
gzip off;
vim /etc/nginx/sites-available/default
server_name www.mojastrona.pl mojastrona.pl
access_log /var/log/nginx/mojastrona.access.log
location / { root /var/www index index.plh index.html index.htmp}
uncomment fastcgi 
fastcgi_param SCRIPT_FILENAME /var/www$fastcgi_script_name;
php-fastcgi //lighthttp to /etc/init.d/
default/php-fastcgi //lighthttp to /etc/default/
//https://www.dobreprogramy.pl/@djgrzenio/debian-nginx-php-mysql-prosta-instalacja,blog,31212

apt-get isntall proftpd //standalone
apt-get isntall postfix //internet site, mojastrona.pl
```

# **thinkpad** Fan speed
```
echo 'options thinkpad_acpi fan_control=1' | sudo tee -a /etc/modprobe.d/thinkpad_acpi.conf
echo level 2 | sudo tee /proc/acpi/ibm/fan 
```

# **macos** Burning iso image 
```
hdiutil burn ubuntu-19.10-desktop-amd64.iso
```

# **youtube** Download YT video using Docker image
```
docker run --rm -i -e PGID=$(id -g) -e PUID=$(id -u) -v "$(pwd)":/workdir:rw mikenye/youtube-dl https://www.youtube.com/watch?v=fW4BqUNdF4Y
```

# **torrent** Run Transmission in Docker
```
docker run -it -p 9091:9091 -v $(pwd):/downloads mb-ubuntu-transmission
```

# **zsh** Ctrl-x Ctrl-e 
```
# Enable Ctrl-x-e to edit command line
autoload -U edit-command-line
# Emacs style
# zle -N edit-command-line
# bindkey '^xe' edit-command-line
# bindkey '^x^e' edit-command-line
# Vi style:
zle -N edit-command-line
bindkey -M vicmd v edit-command-line
```

# **docker** Docker-compose issue
```
cat /proc/sys/kernel/random/entropy_avail
# around 5

apt install -y haveged
systemctl status haveged.service

cat /proc/sys/kernel/random/entropy_avail
# 2400 or more
```

# **bash** Find file duplications
```
find -not -empty -type f -printf "%s\n" | sort -rn | uniq -d | xargs -I{} -n1 find -type f -size {}c -print0 | xargs -0 md5sum | sort | uniq -w32 --all-repeated=separate
```

# **bash** Find empty directories
```
find . -type d -empty
```

# **gpg** encryption and decription test
```
gpg --full-generate-key
gpg -e -a -r test@email.com test_encryption.txt
gpg --decrypt test_encryption.txt.asc | grep test | pbcopy
cat output.txt | perl -lne 'print $1 if /badum ([ \w]+)/' | pbcopy
```

# **bash** Copy to remote without rsync
```
cat file | ssh user@host 'cat >file'
ssh user@host cat file | cat >file
```

# **ssh** Longer connection
```
.ssh
  Host *
    ControlPath    ~/.ssh/%C.sock
    ControlMaster  auto
    ControlPersist 10m
```

# **youtube** Download music playlist from YouTube
```
youtube-dl --extract-audio --audio-format mp3 -o "%(title)s.%(ext)s" <url to playlist>

youtube-dl -ict --yes-playlist --extract-audio --audio-format mp3 --audio-quality 0 https://www.youtube.com/playlist?list=UUCvVpbYRgYjMN7mG7qQN0Pg

youtube-dl -o '%(uploader)s/%(playlist)s/%(playlist_index)s - %(title)s.%(ext)s' -x --audio-format mp3 https://www.youtube.com/playlist?list=PL1f-DySmhA2osjYJ6hOS1xqCmxe1xoq9-

youtube-dl -o '%(playlist)s/%(playlist_index)s - %(title)s.%(ext)s' https://www.youtube.com/playlist?list=PL1f-DySmhA2pE54BOx6nZ8RYK7pB4vxzN
```

# **youtube** Download only sound from video
```
youtube-dl -i --extract-audio --audio-format mp3 --audio-quality 0 YT_URL
```

# **youtube** Download playlist, --download-archive downloaded.txt add successfully downloaded files into downloaded.txt
```
youtube-dl --download-archive downloaded.txt --no-overwrites -ict --yes-playlist --extract-audio --audio-format mp3 --audio-quality 0 --socket-timeout 5 https://www.youtube.com/playlist?list=UUCvVpbYRgYjMN7mG7qQN0Pg
```

# **youtube** Retry until success, no -i option
```
while ! youtube-dl --download-archive downloaded.txt --no-overwrites -ct --yes-playlist --extract-audio --audio-format mp3 --audio-quality 0 --socket-timeout 5 <YT_PlayList_URL>; do echo DISCONNECTED; sleep 5; done
```

# **youtube** Download playlist (titles only) from YT
```
$ youtube-dl -i --get-filename --skip-download https://www.youtube.com/playlist?list=PL1f-DySmhA2p1cu7HIAq-S_FPNC5d6PLN
```

# **youtube** Download all videos as a podcast from channel
```
youtube-dl --download-archive musisz_wiedziec.txt --extract-audio --audio-format mp3 -o "%(title)s.%(ext)s" https://www.youtube.com/@musiszwiedziec4511
```

# **bash** Check public IP
```
curl ifconfig.me
```

# **bash** Many pictures to one pdf
```
img2pdf *.jp* --output combined.pdf

```

# **gpg** Export and import GPG keys
```
gpg --list-keys
gpg --export -a john > public.key
gpg --export-secret-key -a john > private key
gpg --import public.key
gpg --import private.key
```

# **ssh** How to secure SSH
```
sudo vi /etc/ssh/sshd_config

Protocol 2
PermitRootLogin prohibit-password
MaxAuthTries 3
PasswordAuthentication no
PermitEmptyPasswords no
ClientAliveInterval 300

sudo systemctl restart sshd
```

# **tmux**  tmux.conf
```
set -g mouse on
set -g base-index 1
set -g history-limit 50000
set -g mode-keys vi
bind-key -Tcopy-mode-vi y send-keys -X copy-pipe-and-cancel 'pbcopy'
set -g default-shell $SHELL 
set -g default-command "reattach-to-user-namespace -l ${SHELL}"# Enable mouse support in ~/.tmux.conf
set -g default-terminal "screen-256color"
set-option -ga terminal-overrides ",screen-256color:Tc"
```

# **linux** HDMI sound
```
pactl set-card-profile 0 output:hdmi-stereo
```

# **linux** Autologin XFCE
```
cat /etc/group | grep autologin
sudo groupadd -r autologin
sudo gpasswd -a marek autologin
sudo vi /etc/lightdm/lightdm.conf
autologin-user=marek
```

# **linux** Sudo w Debian
```
apt install sudo
/sbin/adduser username sudo
```

# **linux** Setup Wifi on Raspberry Pi
```
#Edit wpa_supplicant.conf
country=PL
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1

network={
    ssid="SSID_TEST"
    psk="PASSWORD"
    key_mgmt=WPA-PSK
}
```

# **linux** ExFAT
```
sudo add-apt-repository universe
sudo apt install exfat-fuse exfat-utils
sudo mkdir /media/usb_disk
# Test mount
sudo mount -t exfat /dev/sdb2 /media/usb_disk/
# Pernament mount
echo "/dev/sdb2	/media/usb_disk	exfat defaults	0	0" >> /etc/fstab
```

# **linux** rsync photos from iphone
```
rsync -avz --progress /run/user/1000/gvfs/gphoto2\:host\=Apple_Inc._iPhone_00008110000130222EB8801E/DCIM/ /home/marek/photos/
```

# **virtualbox** access to USB devices
```
sudo adduser $USER vboxusers
```

# **vim** Copy current file name
```
:let @" = expand("%")
```

# **vim** Replace in many files
```
#Find the pattern that you want to replace (the last dot is for current dir)
:grep -r 'pattern' .
#Open the quickfix window and check if matches are correct
:copen
#Find and replace the entries of the quickfix list
:cdo s/pattern/replacement/ | update 
```

# **linux** Automatic connect to WiFi on clean Debian
```
vi /etc/netplan/00-installer-config.yaml
# This is the network config written by 'subiquity'
# sudo apt install wpasupplicant
# sudo netplan apply
# sudo netplan generate
network:
  wifis:
    wls3:
      dhcp4: true
      access-points:
        "NAME":
          password: "PASSWORD"
  ethernets:
    ens4:
      optional: true
      dhcp4: true
  version: 2
~

vi /etc/systemd/logind.conf
HandleLidSwitch=ignore
sudo systemctl restart systemd-logind
```

# **qemu** Qemu
```
# Install:
sudo apt install qemu-kvm qemu-system
lsmod | grep kvm
sudo modprobe kvm
sudo modprobe kvm_intel
sudo adduser mb kvm
kvm-ok
qemu-system-x86_64 -enable-kvm -m 2048 -hda debian.img
# Check USB devices:
lsusb
# Check if QEMU has USB support by adding flags: -device usb-host
# Run VM with USB. <bus> and <address> should come from lsusb:
qemu-system-x86_64 -device usb-host,hostbus=<bus>,hostaddr=<address>
# Share Ethernet with VM - Create TAP interface:
sudo ip tuntap add tap0 mode tap
sudo ip link set tap0 up
# Run VM:
qemu-system-x86_64 -netdev tap,id=tapnet,ifname=tap0,script=no,downscript=no -device e1000,netdev=tapnet
```

# **thinkpad** How to setup Thinkpad
```
sudo apt install thinkfan tp-smapi-dkms
sudo modprobe -v tp_smapi force_io=1

# tp-smapi-dkms enables enhanced battery stats and charging control.
# thinkfan allows software fan control. Mine would spend hours pumping out cold air.
# check tp_smapi and thinkpad_acpi in /etc/modules

# edit /etc/default/grub and add acpi_osi=Linux to:
# GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux"
# for fix mute and shutdown

# To make the battery last longer avoid recharging it if it is only a
# little bit discharged and never let the battery fully discharge
echo 50 > /sys/devices/platform/smapi/BAT0/start_charge_thresh
echo 85 > /sys/devices/platform/smapi/BAT0/stop_charge_thresh
cat /sys/devices/platform/smapi/BAT0/*_charge_thresh

# add those lines to /etc/rc.local

# Fan control
echo "options thinkpad_acpi fan_control=1" >> /etc/modprobe.d/thinkpad_acpi.conf
# Then enable thinkfan by changing START=no to START=yes in
# /etc/defaults/thinkfan
# You can edit /etc/thinkfan.conf to tune the fan behaviour if you like.

# source:
# https://hackmemory.wordpress.com/2012/07/19/lenovo-x200-tuning/
# https://www.thinkwiki.org/wiki/Tp_smapi#Battery_charge_control_features 
```

# **linux** rsync via ssh
```
rsync -avh -e 'ssh -p 8888' user@host:/home/test/ /home/marekk/test
```

# **linux** ssh tunnel example
```
ssh -R \*:80:localhost:1080 -N user@hostname
```
