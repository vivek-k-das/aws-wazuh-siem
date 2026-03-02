1.Launch EC2 Instances:
*Launch two Ubuntu 22.04/20.04 LTS instances:
   1.Manager: Wazuh server
   2.Agent: Wazuh agent

2.Install Wazuh Manager:
  * curl -s https://packages.wazuh.com/key/GPG-KEY-WAZUH | sudo gpg --dearmor -o /usr/share/keyrings/wazuh-archive-keyring.gpg
  * echo "deb [signed-by=/usr/share/keyrings/wazuh-archive-keyring.gpg] https://packages.wazuh.com/4.x/apt/ stable main" | sudo tee /etc/apt/sources.list.d/wazuh.list
  * sudo apt update
  * sudo apt install wazuh-manager -y

3.Start & Enable Service:
  * sudo systemctl enable wazuh-manager
  * sudo systemctl start wazuh-manager
  * sudo systemctl status wazuh-manager

4.Install Wazuh Agent:
  * curl -s https://packages.wazuh.com/key/GPG-KEY-WAZUH | sudo gpg --dearmor -o /usr/share/keyrings/wazuh-archive-keyring.gpg
  * echo "deb [signed-by=/usr/share/keyrings/wazuh-archive-keyring.gpg] https://packages.wazuh.com/4.x/apt/ stable main" | sudo tee /etc/apt/sources.list.d/wazuh.list
  * sudo apt update
  * sudo apt install wazuh-agent -y

5.Configure Agent to Connect Manager and Add agent in manager:
  * sudo nano /var/ossec/etc/ossec.conf
  * sudo systemctl start wazuh-agent
  * sudo /var/ossec/bin/agent-auth -m MANAGER_PRIVATE_IP
  * sudo /var/ossec/bin/agent-auth -m MANAGER_PRIVATE_IP
  * sudo systemctl restart wazuh-agent



