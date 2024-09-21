Delete process in running on macOS
<br>
Find
<br>
sudo lsof -i :3000
<br>
3000 is port number

Kill
<br>
````kill -9 <PID>````
<br>
-9 kills the process immediately and gives it no chance of cleaning up after itself
<br>
-15: TERM
<br>
-3: QUIT