# STINGAR-Honeypot

**Overview**
1. Setup a Azure ubuntu VM
2. Install Cowrie SSH honeypot
3. Expose to internet for 24hrs
4. Collect log data
5. Harden VM
6. Assess controls

**Situation**
Vendor Cyber Threat Intelligence (CTI) often faces issues such as a lack of relevance and context—feeds are frequently too generic and not tailored to an organization’s specific industry, threat landscape, or region. Timeliness is another concern, as intelligence may arrive after adversaries have already evolved their tactics. The large volume of indicators, many of which are outdated or false positives, can overwhelm analysts and create alert fatigue. Additionally, vendors often provide limited transparency about data sources and collection methods, making it hard to assess reliability. Vendor CTI also tends to focus on external threats, offering little insight into internal compromises or organization-specific attacker behavior. Finally, high costs and restrictive licensing models can lead to vendor lock-in, limiting flexibility and collaboration across multiple intelligence sources.

**Solution**
Honeypots provide an excellent source of threat intelligence data with a high signal-to-noise ratio that is organization-specific and contextualized.

**Steps**
1. Deploy Ubuntu Azure VM  
<img width="1601" height="856" alt="image" src="https://github.com/user-attachments/assets/77fd09d1-ab7f-4ad5-bc56-30b9413604cf" />

2. SSH into VM, make new cowrie directory and git clone Cowrie  
<img width="692" height="234" alt="image" src="https://github.com/user-attachments/assets/3cf68d20-9792-4d29-b037-1cde57858742" />

3. Launch a python virtual env (good practice for running python packages) and activate it
```
python3 -m venv cowrie-env
source cowrie-env/bin/activate
```

5. Install python requirements
```
pip install --upgrade pip
pip install -r requirements.txt
```

6. Copy and edit the config
```
cp etc/cowrie.cfg.dist etc/cowrie.cfg
vi etc/cowrie.cfg
```

7. Setup port forwarding for SSH to Cowrie
```
sudo iptables -t nat -A PREROUTING -p tcp --dport 22 -j REDIRECT --to-port 2222
sudo iptables-save
```
iptables is a Linux command-line utility that configures the Linux kernel's Netfilter firewall for filtering and manipulating network traffic. It inspects and filters IP packets using tables, which contain chains of rules that can accept, reject, or drop packets based on conditions like IP address, protocol, and port.  

8. 









2. Install docker & docker-compose
<img width="678" height="518" alt="image" src="https://github.com/user-attachments/assets/7ec45c8e-578a-4862-bbdf-d195458e8d62" />
Docker Compose is a tool used for defining and running multi-container Docker applications. It allows you to configure your application's services, networks, and volumes in a single YAML file.  

3. Clone repo
```
sudo git clone -b v1.9 https://github.com/CommunityHoneyNetwork/chn-quickstart.git /opt/chnserver && sudo chown -R  ubuntu:docker /opt/chnserver
```

4. installs all Python packages listed in a file called requirements.txt using pip > Use a virtual environment so packages stay isolated from the system
```
python3 -m venv venv
source venv/bin/activate
python3 -m pip install -r requirements.txt
```




**References**  
https://github.com/CommunityHoneyNetwork  
https://stingar.security.duke.edu/  
https://communityhoneynetwork.readthedocs.io/en/stable/  
https://github.com/cowrie/cowrie  
https://www.cowrie.org/  

