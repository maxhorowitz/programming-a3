Patrick Lyons (pml84), Samuel Aberman (sa685), Max Horowitz (mgh68)

Check specification: ```harmony electiontest.hny```

Check implementation ```harmony -m election=electionimpl electiontest.hny```

Write up: ```For our locks, we created individual locks for each candidate and 
citizen. This is better than a single lock for an entire election since threads 
that alter different candidates/citizens can work concurrently since they alter 
independent data. This makes it faster than one master lock. We prevent a 
deadlock from occuring in the transfer function by adding a transfer lock so 
only one thread can call transfer at a time. If candidate A wanted to transfer 
to candidate B and vice versa simultaneouly, and candidate A acquired it's lock 
and then the thread switched and candidate B acquired it's lock then there would 
be a deadlock. For this reason we created a transfer lock which makes the 
program slower but is needed to ensure there are no deadlocks. ```