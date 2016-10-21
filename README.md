shift-zabbix-template
=====================

Description
-----------

This is a basic template to get info from your SHIFT node.

Forked from: 

https://github.com/pilldriver/lisk-zabbix-template)

Monitoring information by now:

* Api: Approval Percentage
* Api: Delegate Rank
* Api: Forging Status
* Api: Missed Blocks
* Api: Node Productivity
* Api: Produced Blocks
* Api: Status Sync [Blocks]
* Api: Status Sync [Height]
* Log: Received New Block (timestamped blocks from app.log)
* Log: Fork Detected (logs.log)
* Log: Forged New Block (logs.log)
* Log: Failed Generate Block (logs.log)
* Log: Failed Common Block (logs.log)
* Process: Memory Usage
* Process: SHIFT Status
* Cluster: Forging Enabled (aggregated check)
* Stats: Avg Blocks Per Minute
* Trigger: Api: Missed Block on {HOST.NAME}
* Trigger: Cluster: Forging Nodes > 1
* Trigger: Log: Failed Generate Block on {HOST.NAME}
* Trigger: Log: Fork Detected on {HOST.NAME}
* Trigger: Process: SHIFT is not running on {HOST.NAME}
* Trigger: Stats: SHIFT Block Height on {HOST.NAME} is unchanged for last 10 minutes

Todo:
* Better included graphs and a extend monitoring screen
* What else?

Installation on a Zabbix Client
-------------------------------

Copy userparameter_shift.conf to /etc/zabbix/zabbix_agentd.d/ - userparameter_shift.conf must
be updated if you want to use a different port than port 9503

Restart the zabbix-agent

Installation in the Zabbix Server
---------------------------------

In your Zabbix frontend: Configuration-Templates section, Import bottom in the right.

Choose the XML file (for server installation: lisk_zabbix_template.xml) and import it.

Apply this new template to your SHIFT servers. 


Template Config
---------------

From your Zabbix Template view click on the "Template App SHIFT Service"

Go to the Macros section and fill in the details where needed

* {$SHIFT.ADDRESS} <- Your SHIFT address from your Forging account
* {$SHIFT.APPLOG} <- Location of your SHIFT app.log on your node
* {$SHIFT.FORGING} <- Used for aggregated check # nodes forging enabled (dont change!)
* {$SHIFT.LOG} <- Location of your SHIFT logs.log on your node
* {$SHIFT.PORT} <- The port SHIFT is running on (default 8000 for mainnet)
* {$SHIFT.PUBLICKEY} <- Your SHIFT publicKey from your Forging account
* {$ZABBIX.GROUP} <- The zabbix groupname of your SHIFT Servers


Requirements on your SHIFT node
------------------------------

Debian / Ubuntu / Raspbian
```
sudo apt-get install jq
```

RHEL / CentOS / Fedora
```
sudo yum install jq
```