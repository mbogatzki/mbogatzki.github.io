### Check public IP
```
curl ifconfig.me
```
### Many pictures to one pdf
```
img2pdf *.jp* --output combined.pdf

```

### GPG Keys
```
gpg --list-keys
gpg --export -a john > public.key
gpg --export-secret-key -a john > private key
gpg --import public.key
gpg --import private.key
```
### Download all video as a podcast from channel
```
youtube-dl --download-archive musisz_wiedziec.txt --extract-audio --audio-format mp3 -o "%(title)s.%(ext)s" https://www.youtube.com/@musiszwiedziec4511
```

### How to secure SSH
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
### tmux.conf
```
set -g mouse on
set -g base-index 1
set -g history-limit 50000
set -g mode-keys vi
bind-key -Tcopy-mode-vi y send-keys -X copy-pipe-and-cancel 'pbcopy'
```

### SASS MAC
```
CXXFLAGS="-mmacosx-version-min=10.9"
LDFLAGS="-mmacosx-version-min=10.9"
```

### HDMI SOUND
```
pactl set-card-profile 0 output:hdmi-stereo
```

### Login AWS Docker
```
AWS CLI V1:
Run $(aws ecr get-login --no-include-email --region eu-west-1) to login

AWS CLI V2:
Run aws ecr get-login-password --region eu-west-1 | docker login --username AWS --password-stdin AWS_REPOSITORY to login. Replace AWS_REPOSITORY with real address.
```

### samba.conf
```
[global]
    map to guest = Bad User
    log file = /var/log/samba/%m
    log level = 10
[smb]
    comment = Samba
    path = /smb
    read only = no
    browsable = yes
    guest ok = yes
```

### Transmission.json
```
{
    "download-dir": "\/downloads",
    "rpc-authentication-required": 0, 
    "rpc-port": 9091, 
    "rpc-whitelist": "192.168.*.* 127.0.0.1",
    "rpc-whitelist-enabled": 0,
    "upload-limit": 0, 
    "upload-limit-enabled": 1,
    "speed-limit-up": 0,
    "speed-limit-up-enabled": 1
}
```

### Autologin w XFCE
```
cat /etc/group | grep autologin
sudo groupadd -r autologin
sudo gpasswd -a marek autologin
sudo vi /etc/lightdm/lightdm.conf
autologin-user=marek
```

### Sudo w debian
```
apt install sudo
/sbin/adduser username sudo
```

### Wifi Raspberry Pi
```
#wpa_supplicant.conf
#country=PL
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1

network={
    ssid="SSID_TEST"
    psk="PASSWORD"
    key_mgmt=WPA-PSK
}
```

### ExFat na linuksie
```
sudo add-apt-repository universe
sudo apt install exfat-fuse exfat-utils
sudo mkdir /media/usb_disk
# Test mount
sudo mount -t exfat /dev/sdb2 /media/usb_disk/
# Pernament mount
echo "/dev/sdb2	/media/usb_disk	exfat defaults	0	0" >> /etc/fstab
```

### Racket na MacOS
```
brew install racket
brew install --cask racket
raco pkg install sicp
```

### Rsync zdjęć z iPhone'a
```
rsync -avz --progress /run/user/1000/gvfs/gphoto2\:host\=Apple_Inc._iPhone_00008110000130222EB8801E/DCIM/ /home/marek/Pobrane/iphone/
```

### Virtualbox dostęp do urządzen USB
```
sudo adduser $USER vboxusers
```

### nie wiem co to robi xD 
```
git checkout `git rev-list -n 1 --before="3 days ago" master`
```

### kopiuj nazwę pliku
```
:let @" = expand("%")
```

### podmiana w wielu plikach
```
- Find the pattern that you want to replace (the last dot is for current dir)
:grep -r 'pattern' .
- Open the quickfix window and check if matches are correct
:copen
- Find and replace the entries of the quickfix list
:cdo s/pattern/replacement/ | update 
```

### automatyczny połączenie z Wifi
```
/etc/netplan/00-installer-config.yaml
# This is the network config written by 'subiquity'
# sudo apt install wpasupplicant
# sudo netplan apply
# sudo netplan generate
network:
  wifis:
    wls3:
      dhcp4: true
      access-points:
        "Tenda_194740_5G":
          password: "occurtalk449"
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

### Backups:
```
rsnapshot https://rsnapshot.org/
TimeShift https://itsfoss.com/backup-restore-linux-timeshift/
https://www.linux.org/threads/timeshift-system-backups.18863/
```

### Regulacja obrotów
```
echo 'options thinkpad_acpi fan_control=1' | sudo tee -a /etc/modprobe.d/thinkpad_acpi.conf
echo level 2 | sudo tee /proc/acpi/ibm/fan 
```

### Podman
```
sudo apt install -y buildah podman
sudo apt install -y runc && sudo systemctl start podman
```

### Open link in tmux on MacOS:
```
https://stackoverflow.com/questions/9458294/open-url-under-cursor-in-vim-with-browser
fn + shift + double click on link
```

### Mouse select in tmux on MacOS:
```
(shift in linux, Option in iTerm, fn in Terminal.app)
fn + mouse
```

### Burning iso image on MacOS
```
hdiutil burn ubuntu-19.10-desktop-amd64.iso
```

### Download YT video using Docker image
```
docker run --rm -i -e PGID=$(id -g) -e PUID=$(id -u) -v "$(pwd)":/workdir:rw mikenye/youtube-dl https://www.youtube.com/watch?v=fW4BqUNdF4Y
```

### Run Transmission in Docker
```
docker run -it -p 9091:9091 -v $(pwd):/downloads mb-ubuntu-transmission
```

### Ctrl-x Ctrl-e in ZSH
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


### Docker-compose issue
```
cat /proc/sys/kernel/random/entropy_avail
# around 5

apt install -y haveged
systemctl status haveged.service

cat /proc/sys/kernel/random/entropy_avail
# 2400 or more
```

### duplikaty plikow:
```
find -not -empty -type f -printf "%s\n" | sort -rn | uniq -d | xargs -I{} -n1 find -type f -size {}c -print0 | xargs -0 md5sum | sort | uniq -w32 --all-repeated=separate
```

### puste foldery:
```
find . -type d -empty
```

### test szyfrowania
```
gpg --full-generate-key
gpg -e -a -r mark.bogatzki@gmail.com test_encryption.txt
gpg --decrypt test_encryption.txt.asc | grep test | pbcopy
cat output.txt | perl -lne 'print $1 if /badum ([ \w]+)/' | pbcopy
```

### Kopiowanie bez SCP
```
cat file | ssh user@host 'cat >file'
ssh user@host cat file | cat >file
```

### Ulepszenie SSH
```
.ssh
  Host *
    ControlPath    ~/.ssh/%C.sock
    ControlMaster  auto
    ControlPersist 10m
```

#Create 7zip archive with 4GB size and password:
```
7z a SOME_NAME.7z -v4000m SOURCE_TO_PACK/ -p=SOME_PASSWORD
```

#Enable possibility to editing system files in El Captian and newer:
```
reboot with CMD+R
csrutil disable
reboot
```

### Create nested directories:
```
mkdir -p /new/new/new
```

### Bash clipboard:
```
Ctrl-u Ctrl-y
```

### Replace and execute last command:
```
^CHANGE_THIS^TO_THIS
```

### Other shortcuts:
```
Ctrl + U Delete to beginning of command from current cursor position.
Ctrl + K Delete to end of command from current cursor position.
Ctrl + R Reverse search history
Ctrl + - Incremental undo
```

### Replacement for arrows, Home and End keys in terminal:
```
  Up Arrow:    Ctrl + p
  Down Arrow:  Ctrl + n
  Left Arrow:  Ctrl + b
  Right Arrow: Ctrl + f
  Home:        Ctrl + a
  End:         Ctrl + e
```

### Shorthands and Magic variables:
```
!!                          The last command
!$                          The last argument from the last command.
![word]                     The last command starting with [word]
![word]:p                   Print the last command starting with [word] (but do not run)
^[word]^[replacement]       Find last command starting with [word] and re-run it with [replacement].
[command] [argument]{a,b,c} Run [command] with [argument] three times, each time changing the postfix to a, then b, then c. For example, mkdir test{1,2} would make two directories: test1 and test2
set -o vi                   Use vi-like movement to edit commands :)
```

### Kill some connection:
```
tcpkill host IPADDRESS
```

### Add user public ssh key to authorized keys on server:
```
cat ~/.ssh/id_rsa.pub | ssh username@hostname 'cat >> .ssh/authorized_keys'
or
ssh-copy-id root@someAddress
```

### Show connection to specific IP:
```
netstat -an IPADDRESS | grep EXAMPLE_IP
```

### Selection in iTerm:
```
OPTION (alt)
```

### VirtualBox - Harddisk uuid error:
```
VBoxManage internalcommands sethduuid disk.vhd
```

### Rotate screen:
```
xrandr --output LVDS1 --rotate right|left|normal
```

### Check services:
```
netstat -plnt
```

### Write terminal commands in editor:
```
(must be set EDITOR=vim in .bashrc)
Ctrl-x Ctrl-e
```

### Copy using rsync
```
rsync -ah --progress source-file destination
```

### Change two letters in command:
```
Ctrl + t
```

### Remove .DS_Store files from repository:
```
# remove any existing files from the repo, skipping over ones not in repo
find . -name .DS_Store -print0 | xargs -0 git rm --ignore-unmatch
# specify a global exclusion list
git config --global core.excludesfile ~/.gitignore
# adding .DS_Store to that list
echo .DS_Store >> ~/.gitignore
```

### Autocomplete git commands:
```
brew install bash-completion
and add to .bash_profile:
if [ -f `brew --prefix`/etc/bash_completion ]; then
    . `brew --prefix`/etc/bash_completion
fi
```

### Name of branch in prompt:
```
(add this to .bash_profile)
parse_git_branch() {
    git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/ (\1)/'
}

export PS1="\u@\h \w\[\033[32m\]\$(parse_git_branch)\[\033[00m\]$ "
```

### Interactive adding files:
```
git add -i
```

### Move text from vim register to tmux pane and execute:
```
call system("tmux load-buffer -", @r)
call system('tmux paste-buffer -t "s01:repl.1"')
```

### Bind command for example eslint to key:
```
map <f5> :!eslint %<cr>
```

### Create alias for long text:
```
imap =tlt test long text
```

### Hex view:
```
Turn on:  :%!xxd
Turn off: :%!xxd -r
```

### Change size of panes:
```
Width: 10 CTRL + w + > 
Height: 10 CTRL + w + + 
```

### Replace text in all specified files:
```
:argsadd ./path/*.js //dodaje ścieżkę do zmiennej args
:arg //wyświetla pliki
:argdo %s/pattern/replace/ge | update //podmienia
```

### Change two vertically split windows to horizontally split and horizontally split to vertically:
```
Ctrl-w t Ctrl-w K
Ctrl-w t Ctrl-w H
```
### Open few files one beside another:
```
:args app/views/*.erb | vertical all
```
### Change mode of explorer:
```
Press: i
```

### Ignore node_modules directory in vimgrep:
```
set wildignore+=**/node_modules/**python
```

### Prettify JSON:
```
:%!python -m json.tool
```

### Change ^M:
```
:%s/^M//g
(to write ^M press Ctrl+V+M)
```

### Change file format from unix to dos:
```
:update
:e ++ff=dos
:w osx
```

### Save file with sudo:
```
:w !sudo tee %
```

### Switching between localizations:
```
Previous: Ctrl-O
Next: Ctrl-I
```

### List of last localizations:
```
:jumps
```

### Vertically buffer split
```
:vert sb 1
```

### Some bash oneliner:
```
for f in *.txt; do mv "$f" `echo $f | sed s/old/new/`; done
```

### Send POST with JSON data:
```
curl -X POST --data @filename.json -H "Content-Type: application/json" http://localhost:8080/
```

### Show which process is running on specific port:
```
lsof -i :15672
```

### Download playlist from YouTube
```
youtube-dl --extract-audio --audio-format mp3 -o "%(title)s.%(ext)s" <url to playlist>
```

### Show status of the file before the last 4 commits:
```
git show HEAD~4:src/main.js
```

### Remove all feature branches:
```
git branch -D `git branch | grep -E 'feature*'`
```

### Prune branches (dry run):
```
git remote prune origin --dry-run
```

### Show number of commits per author:
```
git shortlog -s -n
```

### Solve problem with modifiable off message:
```
:autocmd BufWinEnter * setlocal modifiable
```

### Run macro in 'a' register for line which match pattern:
```
:g/pattern/norm! @a
```

### Set color column in all panes:
```
set colorcolumn=80
```

### Open few files one beside another
```
:args app/views/*.erb | vertical all
```
### Alignment to columns:
```
:!column -t
:%!column -t -s ','
```

### docker clean up:
```
docker-compose down
docker rm -f $(docker container ls -aq)
docker-compose rm -v
docker volume prune
docker system prune
```

### Download single entry
```
youtube-dl -i --extract-audio --audio-format mp3 --audio-quality 0 YT_URL
```

### Download playlist
```
youtube-dl -ict --yes-playlist --extract-audio --audio-format mp3 --audio-quality 0 https://www.youtube.com/playlist?list=UUCvVpbYRgYjMN7mG7qQN0Pg
```

### Download playlist, --download-archive downloaded.txt add successfully downloaded files into downloaded.txt
```
youtube-dl --download-archive downloaded.txt --no-overwrites -ict --yes-playlist --extract-audio --audio-format mp3 --audio-quality 0 --socket-timeout 5 https://www.youtube.com/playlist?list=UUCvVpbYRgYjMN7mG7qQN0Pg
```
```
youtube-dl -o '%(uploader)s/%(playlist)s/%(playlist_index)s - %(title)s.%(ext)s' -x --audio-format mp3 https://www.youtube.com/playlist?list=PL1f-DySmhA2osjYJ6hOS1xqCmxe1xoq9-
```

```
youtube-dl -o '%(playlist)s/%(playlist_index)s - %(title)s.%(ext)s' https://www.youtube.com/playlist?list=PL1f-DySmhA2pE54BOx6nZ8RYK7pB4vxzN
```

### Retry until success, no -i option
```
while ! youtube-dl --download-archive downloaded.txt --no-overwrites -ct --yes-playlist --extract-audio --audio-format mp3 --audio-quality 0 --socket-timeout 5 <YT_PlayList_URL>; do echo DISCONNECTED; sleep 5; done
```

### Download playlist (titles only) from YT
```
$ youtube-dl -i --get-filename --skip-download https://www.youtube.com/playlist?list=PL1f-DySmhA2p1cu7HIAq-S_FPNC5d6PLN
```

### Irssi config
```
# https://irssi.org/documentation/
# https://ixirc.com/
# https://www.xdcc.eu/
servers = (
  {
    address = "irc.abjects.net";
    chatnet = "Abjects";
    port = "6667";
    use_ssl = "no";
    ssl_verify = "no";
    autoconnect = "yes";
  },
);

chatnets = {
  Abjects = { type = "IRC"; };
};

channels = (
   { name = "#mg-chat"; chatnet = "Abjects"; autojoin = "yes"; }
   { name = "#moviegods"; chatnet = "Abjects"; autojoin = "yes"; }
);

settings = {
  core = {
    real_name = "xxx";
    user_name = "xxx";
    nick = "xxx";
  };
  "fe-text" = { actlist_sort = "refnum"; };
  "irc/dcc" = { dcc_autoget = "yes"; };
};
```

### Unknown optymalizacja linuxa
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
