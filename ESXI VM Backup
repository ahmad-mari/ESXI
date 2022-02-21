#!/bin/sh
#Variables To Be Modified As Needed

VmName="AAA"
VmID="123"
Date="$(date +%F)"

#This Is The Directory Where The Backups Are Stored
#cd /path/to/Directory/

#Turn Off The Machine
sshpass -p<YOUR PASSWORD> ssh -o StrictHostKeyChecking=no root@<SERVER_IP> vim-cmd vmsvc/power.shutdown ${VmID}
sleep 10m

#Take A Backup With Date
sudo ovftool -dm=thin vi://root:<YOUR PASSWORD>@<SERVER_IP> /${VmName}  /path/to/Directory/${VmName}_${Date}.ova
sleep 1m

#Turn On The Machine
sshpass -p<YOUR PASSWORD> ssh -o StrictHostKeyChecking=no root@<SERVER_IP> vim-cmd vmsvc/power.on ${VmID}

#Test && Send Email If Needed

var1=$(7za t ${VmName}_${Date}.ova | grep -c  "Archives with Warnings: ")
var2=0

if [[ $var1 != $var2 ]]; then
        mutt -s "Backup Failuer in "_${VmName} <YOUR EMAIL> </dev/null
      

fi
