## Command

# pwd
print working directory

# ls
list directory contents

ls -l: list with details

ls -a: list all files including hidden files

ls -lh: list with human-readable file sizes

ls -R: list all files in subdirectories

# cd
change directory

cd ..: go up one directory

cd ~: go to home directory

cd -: go to previous directory

cd /: go to root directory

cd /path/to/directory: go to specific directory

# mkdir
make directory

mkdir -p: create parent directories if they don't exist

mkdir -v: verbose output

# rmdir
remove empty directory

# rm
remove files or directories

rm -r: remove directories and their contents recursively

rm -f: force remove files without prompt

rm -i: prompt before removing each file

rm -v: verbose output

rm -rf: force remove directories and their contents recursively

# cp
copy files and directories

cp -r: copy directories recursively

# whoami
print current user

# cat
concatenate and display file content

cat file.txt: display content of file.txt

cat file1.txt file2.txt: concatenate and display content of both files

# touch
create an empty file or update the timestamp of an existing file

touch file.txt: create an empty file named file.txt

# mv
move or rename files and directories

mv file.txt newfile.txt: rename file.txt to newfile.txt

mv file.txt /path/to/destination/: move file.txt to the specified directory

# vim
open file in Vim editor
vim file.txt: open file.txt in Vim editor

# ssh
secure shell

ssh user@hostname: connect to remote host

ssh -p port user@hostname: connect to remote host with specified port

ssh -i keyfile user@hostname: connect to remote host with specified key file

# chmod
change file permissions

read r

write w

execute x

rwx

000 - 0 - no permissions

100 - 4 - read only

101 - 5 - read and execute

110 - 6 - read and write

111 - 7 - read, write, and execute

chmod 755 file.txt: set permissions to rwxr-xr-x (owner can read, write, execute; group and others can

order: owner, group, others

# ps
process status

ps aux: display all running processes

ps -ef: display all running processes with full format

ps -u username: display processes for a specific user

ps -p pid: display process with specific PID

ps -l: display processes in long format

# systemctl
system control

systemctl start service: start a service

systemctl stop service: stop a service

systemctl restart service: restart a service

systemctl status service: check the status of a service

systemctl enable service: enable a service to start on boot

systemctl disable service: disable a service from starting on boot

systemctl list-units: list all active units

# kill
terminate a process

kill pid: terminate process with specific PID

kill -9 pid: force terminate process with specific PID

killall process_name: terminate all processes with specific name

killall -9 process_name: force terminate all processes with specific name

# grep
search for a pattern in files

grep pattern file.txt: search for pattern in file.txt

grep -r pattern /path/to/directory: search for pattern in all files in the specified directory

grep -i pattern file.txt: search for pattern in file.txt ignoring case

grep -v pattern file.txt: search for lines not matching the pattern in file.txt

grep -n pattern file.txt: search for pattern in file.txt and show line numbers

grep -c pattern file.txt: count the number of lines matching the pattern in file.txt

