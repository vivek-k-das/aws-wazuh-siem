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
  i.Add Wazuh repository:
      * curl -s https://packages.wazuh.com/key/GPG-KEY-WAZUH | sudo gpg --dearmor -o /usr/share/keyrings/wazuh-archive-keyring.gpg
      * echo "deb [signed-by=/usr/share/keyrings/wazuh-archive-keyring.gpg] https://packages.wazuh.com/4.x/apt/ stable main" | sudo tee /etc/apt/sources.list.d/wazuh.list
      * sudo apt update
  ii.Install Agent:
      * sudo apt install wazuh-agent -y

5.Configure Agent to Connect to Manager:
  * sudo nano /var/ossec/etc/ossec.conf
      <server>
        <address>MANAGER_PRIVATE_IP</address>
      </server>
  *start agent. sudo systemctl start wazuh-agent
6.Add Agent in Manager:
  * sudo /var/ossec/bin/agent-auth -m MANAGER_PRIVATE_IP
  * sudo /var/ossec/bin/agent-auth -m MANAGER_PRIVATE_IP
  * sudo systemctl restart wazuh-agent
