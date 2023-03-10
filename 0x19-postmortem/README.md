Update Issue Postmortem

This is the postmortem for the downtime of the ALX Whaha website that occurred on the 21st of February, 2023.

Issue Summary

From 9:00 pm to 10:25 pm WAT on the 21st of February, 2023, the ALX Whaha website experienced downtime after an update of the software from version 1.0 to 1.1. All users who tried to access the site during this time got a 404 error. The root cause was a failure to update the server configuration during the update.

Timeline (West African Time)

09:00pm - Servers are updated and service stops working.

09:12 pm - Customers complain that the site is unreachable.

09:35 pm - Engineer on call checks that application server is running and reachable.

09:48 pm - Dev team is called in to investigate issue.

10:03 pm - Server configuration is investigated.

10:15 pm - Server configuration is updated and tested.

10:25 pm - Servers are fully online and functional.

Root Cause

The servers were updated at 9:00pm with the help of an update script. The update script however did not handle the configuration of nginx to proxy requests to the application server. This caused nginx to give a 404 error when any request was made.

￼

Resolution

The dev team had to manually ssh into the servers and update the configuration files for nginx. The servers were then tested using ApacheBench to make sure the volume of requests received could be handled.

Corrective and preventative measures

On analysis of the outage, we have decided that the following actions will help prevent such an incident in the future:

Better automate the update and server configuration process

Setup monitoring tools to inform devs of server downtime

Create custom error pages to improve user experience during outages

Improve disaster recovery system to reduce MTA and MTR

Give free coffee to devs on call ☕
