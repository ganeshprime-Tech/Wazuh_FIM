# wazuh-Lab
1. Installed and configured wazuh manager in Ubuntu virtual machine
2. Add a linux and windows virual machine as a agents

# File integrity monitoring
![image](https://github.com/user-attachments/assets/0a64bbaf-0e94-43b2-84e4-52519b17d2ea)
Go to # /var/ossec/etc/ossec.conf file and specify the path(under FIM syscheck block) for which folder can be monitoried

![image](https://github.com/user-attachments/assets/8f5e0fce-0b72-4be8-b7f5-bdad20ef3c91)

crating text file in agent

![image](https://github.com/user-attachments/assets/46f645bf-dbc1-4a4c-bca6-a7df31b8106c)
I can able to see the integrity monitoring logs

# Active response

![image](https://github.com/user-attachments/assets/474a4337-c2e4-49ef-88cb-0c6e4394da98)
Add path to monitor under the FIM syscheck block

Install jq, a utility that processes JSON input from the active response script.
sudo apt update
sudo apt -y install jq

![image](https://github.com/user-attachments/assets/e2d29ff0-2174-4675-b1a8-f3a21766d44b)
Create the /var/ossec/active-response/bin/remove-threat.sh active response script to remove malicious files from the endpoint

Change the /var/ossec/active-response/bin/remove-threat.sh file ownership, and permissions:
sudo chmod 750 /var/ossec/active-response/bin/remove-threat.sh
sudo chown root:wazuh /var/ossec/active-response/bin/remove-threat.sh

Restart the Wazuh agent to apply the changes:
sudo systemctl restart wazuh-agent

#wazuh server
Add the following rules to the /var/ossec/etc/rules/local_rules.xml file on the Wazuh server. These rules alert about changes in the /home/wazu-linuc-agent directory that are detected by FIM scans.
![image](https://github.com/user-attachments/assets/8d3aef3b-2d64-4e92-ae8b-0862beab7502)

Add the virus total configuration to the Wazuh server /var/ossec/etc/ossec.conf
Append the remove-threat.sh blocks to the Wazuh server /var/ossec/etc/ossec.conf

![image](https://github.com/user-attachments/assets/8f9bd80c-82d0-453b-8ae8-d1bf9f8d6f6d)


sudo systemctl restart wazuh-manager

![image](https://github.com/user-attachments/assets/1cb00944-c85b-4a07-b6ee-0ce95237fbd0)




