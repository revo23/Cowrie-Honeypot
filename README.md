# STINGAR-Honeypot

**Overview**
1. Setup a VM Honeypot
2. Expose to internet for 24hrs
3. Collect log data
4. Harden VM
5. Assess controls

**Situation**
Vendor Cyber Threat Intelligence (CTI) often faces issues such as a lack of relevance and context—feeds are frequently too generic and not tailored to an organization’s specific industry, threat landscape, or region. Timeliness is another concern, as intelligence may arrive after adversaries have already evolved their tactics. The large volume of indicators, many of which are outdated or false positives, can overwhelm analysts and create alert fatigue. Additionally, vendors often provide limited transparency about data sources and collection methods, making it hard to assess reliability. Vendor CTI also tends to focus on external threats, offering little insight into internal compromises or organization-specific attacker behavior. Finally, high costs and restrictive licensing models can lead to vendor lock-in, limiting flexibility and collaboration across multiple intelligence sources.


**Solution**
Honeypots provide an excellent source of threat intelligence data with a high signal-to-noise ratio that is organization-specific and contextualized.

**Steps**
1. Deploy Ubuntu Azure VM
<img width="1601" height="856" alt="image" src="https://github.com/user-attachments/assets/77fd09d1-ab7f-4ad5-bc56-30b9413604cf" />

2. Install docker & docker-compose
<img width="678" height="518" alt="image" src="https://github.com/user-attachments/assets/7ec45c8e-578a-4862-bbdf-d195458e8d62" />
Docker Compose is a tool used for defining and running multi-container Docker applications. It allows you to configure your application's services, networks, and volumes in a single YAML file.  

3. 




**References**  
https://github.com/CommunityHoneyNetwork

