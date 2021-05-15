# Configuring-Switch-Security
This project illustrates how to secure a switch.

There are different ways to secure a switch from threats, which are performed in this project activity. 

Configuring SSH session can also be seen in this project. The topology consists of a router, switch and a PC. First, the devices are cabled as per the topology and then IP addresses are assigned to respective ports so that they can be recognized and used in a network. Just like previous project activities, the basic router and switch setting are configured. 

The next step is configuration of SSH on **S1 (Switch-1)**. For that, first, an ip domain name is set and then its username and password along with its privileges. Then vty lines are assigned to be accessed by SSH only. Lastly crypto keys are generated. 

Now, to secure the switch, one of the basic and common method is used, which is issuing **shutdown** command on all the unused ports. 

Then, we set the MAC address of G0/1 interface of the router R1 as the **port-security mac-address**, in order to give a secure the switch and only one mac address considered secure (G0/1 interface mac address). 

Then connectivity test is conducted by issuing ping command on the router, towards PC-A. The connectivity test is successful. 

Then to see the security violation status, the MAC address of G0/1 is changed to aaaa.bbbb.cccc for which it is required to first shut the port down, then change the mac address and then turn the port on again. Now, from R1, connectivity test is conducted again but this time it is unsuccessful. This is because the mac address on R1 G0/1 interface has been changed to aaaa.bbbb.cccc. Because of this change, the secured port has changed its state to **error disabled**. The mac address of G0/1 of R1 was assigned as the only mac address allowed, but since it was changed, it became an unknown mac address and thus leading the port on the switch go down. 

Now to troubleshoot this, change the mac address on R1 G0/1 by issuing the **no mac-address aaaa.bbbb.cccc**. Conduct connectivity test again. Still the frames are not sent because the port on S1 is still in error disaabled state. To fix this, issue the shutdown command and then no shutdown. 

Now, on conducting the connectivity test again, pings will be successful. 

All the work has been documented and the document file can be found in the same repository.
