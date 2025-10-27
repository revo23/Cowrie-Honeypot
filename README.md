# Cowrie-Honeypot

**Overview**
1. Setup a Azure Debian VM
2. Install Cowrie SSH honeypot
3. Bruteforce using Nmap and Hydra using Kali
4. View logs

**Situation**
Vendor Cyber Threat Intelligence (CTI) often faces issues such as a lack of relevance and context—feeds are frequently too generic and not tailored to an organization’s specific industry, threat landscape, or region. Timeliness is another concern, as intelligence may arrive after adversaries have already evolved their tactics. The large volume of indicators, many of which are outdated or false positives, can overwhelm analysts and create alert fatigue. Additionally, vendors often provide limited transparency about data sources and collection methods, making it hard to assess reliability. Vendor CTI also tends to focus on external threats, offering little insight into internal compromises or organization-specific attacker behavior. Finally, high costs and restrictive licensing models can lead to vendor lock-in, limiting flexibility and collaboration across multiple intelligence sources.

**Task**
Honeypots provide an excellent source of threat intelligence data with a high signal-to-noise ratio that is organization-specific and contextualized.  

Cowrie is a medium to high interaction SSH and Telnet honeypot designed to log brute force attacks and the shell interaction performed by the attacker. In medium interaction mode (shell) it emulates a UNIX system in Python, in high interaction mode (proxy) it functions as an SSH and telnet proxy to observe attacker behavior to another system.  

**Steps**
1. Deploy Debian Azure VM  
<img width="1805" height="918" alt="image" src="https://github.com/user-attachments/assets/809ee3f1-d701-401c-984a-b751ab603b7f" />


2. SSH into VM and install system dependencies
```
sudo apt-get update

sudo apt-get install git python3-pip python3-venv libssl-dev libffi-dev build-essential libpython3-dev python3-minimal authbind
```

3. git clone the code
```
git clone http://github.com/cowrie/cowrie

cd cowrie
```

4. Setup virtual env adn install packages
```
pwd
/home/stingar/cowrie
python3 -m venv cowrie-env
source cowrie-env/bin/activate
(cowrie-env) $ python -m pip install --upgrade pip
(cowrie-env) $ python -m pip install -e .
```
5. Start cowrie and check status
```
source cowrie-env/bin/activate
(cowrie-env) $ cowrie start
(cowrie-env) $ cowrie status
cowrie is running (PID: 2759).
```

6. Listening on port 22

The SSH daemon runs on port 22 by default. Cowrie runs on port 2222 by default. To receive most traffic, Cowrie will need to listen on port 22. This requires two changes: First, If you have an existing SSHD on port 22 it will need to be moved to another port. Second, Cowrie will need to listen to requests on port 22.

7. View logs
tail -f var/log/cowrie/cowrie.log

<img width="937" height="370" alt="image" src="https://github.com/user-attachments/assets/fe707a00-9850-494f-b7e3-4162c7bbc1b9" />

8. On my Kali machine use nmap and password bruteforce towards the honeypot
```
nmap -Pn 20.186.92.10 > port scan 
nc -vz 20.186.92.10 22 > check if port 22 on VM reachable
hydra -h
hydra -l stingar -P /usr/share/wordlists/rockyou.txt -t 4 -f ssh://20.186.92.10

```
What -Pn does (short)

- Skips the initial host discovery (ping) phase.

- nmap assumes the host is up and proceeds directly to port scanning.

- Useful when ICMP/host discovery is blocked by a firewall/IDS.

When to use -Pn

- The target drops/ignores ICMP, ARP, or discovery probes (common on hardened servers/cloud VMs).

- You see Host seems down results but you know the host is live.

- You're troubleshooting a service behind a firewall that blocks ping.

<img width="936" height="986" alt="image" src="https://github.com/user-attachments/assets/c36ec0ac-cb33-4e01-b58c-b30f6a99474d" />

**Result**  
Source IP and bruteforce attampts (user/password) logged

**References**  
 
https://github.com/cowrie/cowrie  
https://www.cowrie.org/  
https://www.youtube.com/watch?v=uSohtNwQXuI

