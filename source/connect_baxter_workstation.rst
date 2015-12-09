Connect the robot and the workstation
=====================================
These steps are particular for the
Baxter at Heni's Lab:

1. Get an Ethernet cable and connect
   the robot and your workstation.
2. To communicate your workstation
   and Baxter you need the IP or hostname
   information from both, which is easy
   to obtain:
3. Workstation: Open a terminal and type

   .. code-block:: bash

      sudo avahi-autoipd eth0

   After a few seconds, you will see a IP in the
   terminal. Write it down and leave that
   terminal open and running for the rest of the 
   robot session (i.e. I got 169.254.65.23).
4. Baxter: His IP by default is his serial number
   (you can read it on its back sticker). His serial
   number will be SERIAL_NUMBER.local (i.e. this
   Baxter IP is 011505P0001.local).
5. Just if you want to check, you can ping to Baxter
   and ping to yourself to make sure the connection is on.
   
   .. code-block:: bash

      ping 011505P0001.local
      ping 169.254.65.23

   If it pings, then good, if not, ask me.

6. Go to your catkin workspace. In my case it is catkin_ws.
   Edit the script baxter.sh with the information
   you obtained:

   .. code-block:: bash

      baxter_hostname="011505P0001.local"
      your_ip="169.254.65.23"
      #your_hostname=THIS MUST BE COMMENTED OUT I YOU USE YOUR_IP

7. You are ready to run Baxter. To enable him (step required
   before moving him), you just open a new terminal and:

   .. code-block:: bash

      # This takes you to catkin_ws/devel
      roscd
      # This goes to catkin_ws
      cd ..
      # Run script so this terminal knows that ROS master is running on Baxter
      . baxter.sh
      # Enable the robot
      rosrun baxter_tool enable_robot.py -e

