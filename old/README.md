# markbogatzki.github.io

##JavaScript
How to check usage of local storage
```
var total = 0;for(var x in localStorage){total += ((localStorage[x].length * 2)/1024/1024); console.log(x+'='+((localStorage[x].length * 2)/1024/1024).toFixed(4)+' MB')}; console.log('Total:',total.toFixed(4)+' MB');
```
Date in format YYYY-MM-DD
```
(new Date()).toISOString().slice(0,10);
```
One-line saving data to file
```
require('fs').writeFile('/Users/marek/Desktop/test.json',JSON.stringify(data),function(err){err ? console.log(err):console.log('saved');});
```
Interesting links:
[Closures](http://javascriptissexy.com/understand-javascript-closures-with-ease/)
[Tricks and best practices](http://modernweb.com/2013/12/23/45-useful-javascript-tips-tricks-and-best-practices/vim2016-04-18)

##Bash
Create 7zip archive with 4GB size and password:
```
7z a SOME_NAME.7z -v4000m SOURCE_TO_PACK/ -p=SOME_PASSWORD
```
Enable possibility to editing system files in El Captian and newer:
```
reboot with CMD+R
csrutil disable
reboot
```
Finding apache process:
```
ps aux | grep apache
```
Create nested directories:
```
mkdir -p /new/new/new
```
Bash clipboard:
```
Ctrl-u Ctrl-y
```
Replace and execute last command:
```
^CHANGE_THIS^TO_THIS
```
Show ASCII table:
```
man 7 ascii
```
Other shortcuts:
```
Ctrl + U Delete to beginning of command from current cursor position.
Ctrl + K Delete to end of command from current cursor position.
Ctrl + R Reverse search history
Ctrl + - Incremental undo
```
Replacement for arrows, Home and End keys in terminal:
```
  Up Arrow:    Ctrl + p
  Down Arrow:  Ctrl + n
  Left Arrow:  Ctrl + b
  Right Arrow: Ctrl + f
  Home:        Ctrl + a
  End:         Ctrl + e
```
Shorthands and Magic variables:
```
!!                          The last command
!$                          The last argument from the last command.
![word]                     The last command starting with [word]
![word]:p                   Print the last command starting with [word] (but do not run)
^[word]^[replacement]       Find last command starting with [word] and re-run it with [replacement].
[command] [argument]{a,b,c} Run [command] with [argument] three times, each time changing the postfix to a, then b, then c. For example, mkdir test{1,2} would make two directories: test1 and test2
set -o vi                   Use vi-like movement to edit commands :)
```
Get IP address in OSX terminal
```
ifconfig en0 | grep -o '[0-9\.]\{7,15\} '
```
List tmux sessions and attaching to session:
```
tmux list-sessions
tmux attach -t session_name
```
Copy all directory:
```
cp -R dirName target/newDirName
```
Kill some connection:
```
tcpkill host IPADDRESS
```
Add user public ssh key to authorized keys on server:
```
cat ~/.ssh/id_rsa.pub | ssh username@hostname 'cat >> .ssh/authorized_keys'
or
ssh-copy-id root@someAddress
```
Some bash oneliner:
```
for f in *.txt; do mv "$f" `echo $f | sed s/old/new/`; done
```
Close ssh connection and back to terminal:
```
Press: Enter ~ .
```
Show connection to specific IP:
```
netstat -an IPADDRESS | grep EXAMPLE_IP
```
Tmux - change number of active window:
```
CTRL + b + .
```
Tmux - go to two-digit window number:
```
CTRL + b + w
```
Selection in iTerm:
```
OPTION (alt)
```
VirtualBox - Harddisk uuid error:
```
VBoxManage internalcommands sethduuid disk.vhd
```
Rotate screen:
```
xrandr --output LVDS1 --rotate right|left|normal
```
Check services:
```
netstat -plnt
```
Write terminal commands in editor:
```
(must be set EDITOR=vim in .bashrc)
Ctrl-x Ctrl-e
```
Copy using rsync
```
rsync -ah --progress source-file destination
```
Go to previous localization and go to home localization:
```
cd -
cd
```
Clear terminal:
```
Ctrl + l
```
Change two letters in command:
```
Ctrl + t
```
Interesting links:
[Syntax keyboard](http://ss64.com/bash/syntax-keyboard.html)

##Git
Show status of the file before the last 4 commits:
```
git show HEAD~4:src/main.js
```
Add files to last commit and add new commit message:
```
git commit --amend –C HEAD , git commit --amend -m "New commit message"
```
Merge two last commits into one commit:
```
git rebase --interactive HEAD~2
```
Show log of two last commits:
```
git loge -2
```
Remove .DS_Store files from repository:
```
# remove any existing files from the repo, skipping over ones not in repo
find . -name .DS_Store -print0 | xargs -0 git rm --ignore-unmatch
# specify a global exclusion list
git config --global core.excludesfile ~/.gitignore
# adding .DS_Store to that list
echo .DS_Store >> ~/.gitignore
```
Autocomplete git commands:
```
brew install bash-completion
and add to .bash_profile:
if [ -f `brew --prefix`/etc/bash_completion ]; then
    . `brew --prefix`/etc/bash_completion
fi
```
Name of branch in prompt:
```
(add this to .bash_profile)
parse_git_branch() {
    git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/ (\1)/'
}

export PS1="\u@\h \w\[\033[32m\]\$(parse_git_branch)\[\033[00m\]$ "
```
Interactive adding files:
```
git add -i
```
Interesting links:
[Hot tips](http://wesbos.com/git-hot-tips)

##Vim
Move text from vim register to tmux pane and execute:
```
call system("tmux load-buffer -", @r)
call system('tmux paste-buffer -t "s01:repl.1"')
```
Surrounding word in parentheses:
```
viwxi()<esc>P
```
Bind command for example eslint to key:
```
map <f5> :!eslint %<cr>
```
Create alias for long text:
```
imap =tlt test long text
```
Hex view:
```
Turn on:  :%!xxd
Turn off: :%!xxd -r
```
Change size of panes:
```
Width: 10 CTRL + w + > 
Height: 10 CTRL + w + + 
```
Equal sizes of all panes:
```
CTRL + w + =
```
Replace text in all specified files:
```
:argsadd ./path/*.js //dodaje ścieżkę do zmiennej args
:arg //wyświetla pliki
:argdo %s/pattern/replace/ge | update //podmienia
```
Case sensitive replace:
```
:%s/foo/bar/gI
```
Replace this word (not when this is a part of other word):
```
:%s/\/bar/g
```
Turn on diff and turn off diff:
```
:windo diffthis
:windo diffoff
```
Set color column in all panes:
```
set colorcolumn=80
```
Change two vertically split windows to horizontally split
and horizontally split to vertically:
```
Ctrl-w t Ctrl-w K
Ctrl-w t Ctrl-w H
```
Open few files one beside another:
```
:args app/views/*.erb | vertical all
```
Change mode of explorer:
```
Press: i
```
Ignore node_modules directory in vimgrep:
```
set wildignore+=**/node_modules/**python
```
Prettify JSON:
```
:%!python -m json.tool
```
Change ^M:
```
:%s/^M//g
(to write ^M press Ctrl+V+M)
```
Change file format from unix to dos:
```
:update
:e ++ff=dos
:w osx
```
Save file with sudo:
```
:w !sudo tee %
```
Switching between localizations:
```
Previous: Ctrl-O
Next: Ctrl-I
```
List of last localizations:
```
:jumps
```
Vertically buffer split
```
:vert sb 1
```
Copy to 'a' register:
```
"ay
```
Paste with replace:
```
viwp
```
Insert line with width of text:
```
yypVr-
```
Run terminal command:
```
:!ls
```
Insert result of terminal command to active buffer:
```
:read !ls
```
Alignment to columns:
```
:!column -t
```
Alternative for using Esc:
```
CTRL-C
```
Interesting links:
[Why using Vim](http://www.viemu.com/a-why-vi-vim.html)
[Talking with Vim](http://stackoverflow.com/a/1220118)

