Delete process in running on macOS
Find
sudo lsof -i :3000
3000 is port number

Kill
kill -9 <PID>
-9 kills the process immediately and gives it no chance of cleaning up after itself
-15: TERM
-3: QUIT