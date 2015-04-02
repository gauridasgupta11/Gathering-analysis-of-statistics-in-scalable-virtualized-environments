Statistics-gathering-and-analysis-tool
======================================

The goal of this project is to create a DPM (Distributed Power Management) and 
DRS (Distributed Resource Scheduler) function and to gather large-scale statistics 
in a scalable virtual environment. To measure the statistics we use the open
source tool logstash. Logstash filters the logs from each VM and stores it in the database.

Functional Requirements :
 Resource Scheduling: The DRS functions should monitor and 
balance the load on the VMs, they should also be able to keep the 
vCPU busy for each VM.
 Power Management: The main function of the DPM must be to 
balance the vHosts and VMs to obtain a lower threshold. It must 
also be able to monitor the usage of the CPU.
 Collection of data: The tool should have the functionality of 
gathering data on a large scale. It should extract logs, and the 
logstash installed should enable the filtering of the raw logs. 
Furthermore, these logs must be stired in the NoSQL database. 
Parsing of the relevant data should be carried out ans stored in the 
SQL database.
 Visualization of the log statistics: The data stored in the SQL 
database must be displayed in the form of visual charts. These 
charts must comprise of real-time data.

Nonfunctional requirements :
 Real-time data must be displayed in a user-friendly way
 The tool must be scalable to any extent
 Old data in the database should be purged after a while

Algorithm used for DRS1:
 Monitoring the CPU usage of the hosts
 Searching for the host that has comparatively low CPU usage 
 Add a new VM to the host that has low CPU usage
 If a condition arises, such that a all the hosts already have high CPU usage, 
then add a new host to place the new VM

Algorithm used for DRS2:
 Monitor the CPU usage of the existing hosts
 Search for the host that has higher CPU usage
 Look for the VM in that particular host that is utilizing the CPU the most
 Create a new host for this VM and migrate the VM to that new host

Algorithm used for DPM:
 Monitoring the CPU usage on each host
 Searching for the host that has the minimum amount of CPU usage
 Looking for the VM in that host which is occupying the maximum CPU
 Moving this VM to another host
 Repeating the above steps until the system consists of minimum amount of 
hosts and maximum utilization
