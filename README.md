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

**Task**
Honeypots provide an excellent source of threat intelligence data with a high signal-to-noise ratio that is organization-specific and contextualized.  

Cowrie is a medium to high interaction SSH and Telnet honeypot designed to log brute force attacks and the shell interaction performed by the attacker. In medium interaction mode (shell) it emulates a UNIX system in Python, in high interaction mode (proxy) it functions as an SSH and telnet proxy to observe attacker behavior to another system.  

**Steps**
1. Deploy Debian Azure VM  
<img width="1805" height="918" alt="image" src="https://github.com/user-attachments/assets/809ee3f1-d701-401c-984a-b751ab603b7f" />


2. SSH into VM and create user account cowrie 
```
sudo adduser --disabled-password cowrie

sudo su - cowrie
```

It’s strongly recommended to run with a dedicated non-root user id

3. git clone the code
```
git clone http://github.com/cowrie/cowrie

cd cowrie
```

4. Setup virtual env adn install packages
```
pwd
python3 -m venv cowrie-env
source cowrie-env/bin/activate
(cowrie-env) $ python -m pip install --upgrade pip
(cowrie-env) $ python -m pip install -e .
```











**References**  
https://github.com/CommunityHoneyNetwork  
https://stingar.security.duke.edu/  
https://communityhoneynetwork.readthedocs.io/en/stable/  
https://github.com/cowrie/cowrie  
https://www.cowrie.org/  

