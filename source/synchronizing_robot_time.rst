Synchronizing robot time
========================

Do step 1 once in a while, after
your robot gets some drift. Steps
2 and 3 should have been done
in the past, so likely you don't
need to do them again.

1. Connect your robot to the network 
   (use the Ethernet cable to connect
   the robot to the network patch).
   The robot uses NTP so when it
   connects to the network it updates
   its clock.
2. Make sure your own workstation
   also runs NTP.

3. The step above should be enough
   IF your robot is set up to the 
   same time zone of your real
   location. For instance, Baxter
   was set to EST zone, whereas
   in Arizona we are on the SMT
   zone. To change it you have
   to use the FSM in the robot
   (check online or ask me).
   I already updated it to
   be on time US/Arizona, so we are covered
   with this Baxter.
