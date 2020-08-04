# Debug_ChkScript
#Shell Script for monitoring filesystem usage and filesystem mount points in a linux server

#Pre-requisites

1.Linux server
2.Shell scripting
3.Passwordless login from Jump box to linux servers 

#Script functions

1.Script will continously monitor the Jboss application servers whether Debug is enabled or not.
2.Script will run from jump box, it will read the configuration file and then it will ssh to each server & checl the Debug configuration.
3.Script will send mail alert if Debug is enabled in Jboss application servers.
4.We don’t need to login to each server explicitly and validate check the configurations, we can invoke a single script for monitoring.

#Installation steps

1.Debug_chkScript.sh & ${env}App.cfg files should be staged in Jump Box server(Main server)

2.Debug_chkScript.sh - Main script for checking the Jboss configuartion of each servers. 

3.${env}App.cfg - List of Jboss application servers and Main script will ssh to these servers & check the jboss configuration.

cat ${env}App.cfg - We can list the servers here. 

#  Hostname   instance names
#
pvmkxxxx yyyy
pvmkxxxx yyyy


4.Passwordless is required to ssh to individual servers & check the jboss configuration.
Please go through https://www.tecmint.com/ssh-passwordless-login-using-ssh-keygen-in-5-easy-steps/ for setting up passwordless login.

5. Add script to crontab - in Jump Box server

crontab -e
0,15,30,45 * * * * /home/webadmin/scripts/DebugChkScript.sh 2> /dev/null












