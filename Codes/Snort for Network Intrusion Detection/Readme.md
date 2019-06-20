Snort is a network packet sniffer and Intrusion Detection tool and prevention system.
Snort can be configured to protect a network server or an instance by configuring its snort.conf file.
Snort uses a set of rules, preprocessor rules and decoder rules which are defined in the rules directory in Snort folder. these rules are used for matching the network traffic to detect previously defined patterns. snort has a pre defines (can be altered/configured) way of passing the packets through it. 
snort can be run in three possible ways:
1) Packet sniffer mode
2) Packet logger mode
3) Network Intrusion Detection Mode
- Packet Sniffer mode is used just to give a detailed log of all the network packets being received on the server on a terminal.
- Packet logger mode is used to log all the data in a log file in a defined folder.
- Network Intrusion Detection Mode is used in order to detect threat attacks like DoS, DDoS, Port Scanning and Bad traffic on the basis of preprocessor, decoder, dynamic libraries and alert rules.

In order to start using Snort do the following:
1) Press Ctrl+Alt+T (Opens Terminal.)
Put the following commands in order: 
2) apt-get update -y 
3) apt-get upgrade -y
4) apt-get install openssh-server ethtool build-essential libpcap-dev libpcre3-dev libdumbnet-dev bison flex zlib1g-dev liblzma-dev openssl libssl-dev
5) wget https://www.snort.org/downloads/snort/snort-2.9.13.tar.gz
6) tar -zxvf daq-2.9.13.tar.gz
7) cd daq-2.9.13
8) ./configure && make && make install
9) ldconfig
10) ln -s /usr/local/bin/snort /usr/sbin/snort
11) snort -V
The last command above will give you the snort version you are running if everything is installed properly.
The Snort folder is present at /etc/snort and the configuration files along with all the rules file are stored there.
12) cd
13) mkdir SnortOrigin
14) git clone https://github.com/sachin10101998/Cogoport-Internship.git
15) cd Cogoport-Internship-master
16) cd Codes
17) cd Snort For Network Intrusion Detection
18) cd snort
Now open the folder /etc/snort/ on your device.
19) Copy the contents of snort.conf file from the cloned copy of sachin10101998 github repo and paste it in the snort.conf file of the /etc/snort/snort.conf
20) ifconfig
21) Check the inet address of the network interface on which network packets are being received.
22) For example if you are installing snort on your local machine, then you'll probably be looking for wlo1 interface.
23) Copy the inet address of wlo1 interface then open the /etc/snort/snort.conf file in another terminal.
24) scroll down at the place where $HOME_NET variable is defined. It's currently set at 10.10.1.56.
25) Set it to the inet value of the network interface which you are protecting.
26) Copy the rules folder from the cloned copy of snort and paste it in the /etc/snort/ folder.
27) Similarly replace the so_rules and preproc_rules folder by copying from the cloned copy and pasting it in the /etc/snort folder.
28) Come back to terminal and give the following command
29) sudo snort -A console -i wlo1 -c /etc/snort/snort.conf -l /var/log/snort -K ascii
30) Before running the command make an empty log folder in the /var/ directory.
31) Change the rules by commenting out the not required ones in the snort.conf file.

The default way in which Snort applies its rules to packets may not be appropriate for all installations. The Pass rules
are applied first, then the Drop rules, then the Alert rules and finally, Log rules are applied.
Several command line options are available to change the order in which rule actions are taken.
- "--alert-before-pass" option forces alert rules to take affect in favor of a pass rule.
- "--treat-drop-as-alert" causes drop and reject rules and any associated alerts to be logged as alerts, rather
then the normal action. This allows use of an inline policy with passive/IDS mode. The sdrop rules are not
loaded.
- "--process-all-events" option causes Snort to process every event associated with a packet, while taking the
actions based on the rules ordering. Without this option (default case), only the events for the first action based
on rules ordering are processed.
