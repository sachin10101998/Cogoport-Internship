# NIDS -  Network based Intrusion detection system for Cogoport<br>
1. A Network based intrusion detection system for Cogoport.
2. This NIDS was built suing python 2.7 and scapy. Scapy is a packet manipulation tool for computer networks, written in Python.
3. In order to start sniffing packets for any malicious patterns or calls:
  - Clone the repo.
  - `cd NIDScogoport`
  - `sudo python -B src/NIDS.py rules/rules.txt`
4. Alerts are generated and Log files are created after each session is completed.
5. This IDS is used only for detecting requests using Scapy and not to protect the system by automatic response.
6. I have added the rules for DDos attack detection in the rules.txt file.
![Working Screengrab](https://user-images.githubusercontent.com/34926285/58416573-ad782b80-809f-11e9-9566-fadcacbcd752.png)
