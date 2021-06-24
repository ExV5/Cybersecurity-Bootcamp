#### Domain: Network Security

**Question 1:  Faulty Firewall**

Suppose you have a firewall that's supposed to block SSH connections, but instead lets them through. How would you debug it?

Make sure each section of your response answers the questions laid out below.
​

1. Restate the Problem

   A firewall that needs to be blocking SSH connections. However it is still allowing SSH connections? To understand why they would still be allowing connections the first thing I would do is inspect the inbound rules created within the Network Security Group.

   

2. Provide a Concrete Example Scenario

   An example I have of needing to do this myself is when I was setting up VM's running docker containers. In order to set them up I needed to set up inbound rules to allow SSH (port 22) connections from specific IP addresses..  

   

3. Explain the Solution Requirements

   The first thing I would inspect the inbound rules created within the network security group that the VM's are part of. I would look at the priority of rules that have been created and inspect them for an errors that could cause the ability to allow SSH connections.

   


4. Explain the Solution Details

   After inspecting rules in place I would either edit if needed or create a new rule that would block SSH (port 22) connections from any source. Once a inbound rule was edited or created I would use my terminal (git bash) to try and connect to the system myself. If corrected I should receive a timeout message meaning the connection could not go through.

   

5. Identify Advantages/Disadvantages of the Solution.

   What I would create next is a ELK system using kabana to monitor and log attempts of any suspicious authentication attempts.

   

   