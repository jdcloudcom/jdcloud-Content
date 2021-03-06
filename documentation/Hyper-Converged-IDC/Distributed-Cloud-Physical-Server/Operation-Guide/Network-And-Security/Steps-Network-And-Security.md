## Firewall

Firewall with status may be configured via iptables for Linux server and the connection status created for sending and receiving information packages can be specified and remembered. It is a set of command package to set, maintain and inspect IP package filtration rules of Linux kernel.

iptables firewall of table--Linux has three tables by default, i.e. Filter, NAT and Mangle, and there are also customized tables, among which Filter is the table to be used by default;

chain--band chain, e.g. filter has three chains, i.e. INPUT, OUTPUT and FORWARD.

**Note: Please disable SSH login port 22 with care, as disabling port 22 will lead to inaccessibility from the external to the Distributed Cloud Physical Server.**

### Operation Steps

The following is an example of creating a filter table firewall:

### **1. Clear Original Rules**

```
[root@jd ~]# iptables -F    #Clear the rules of all the rule chains in the preset form filter
[root@jd ~]# iptables -X    #Clear the rules of the user-customized chains in the preset form filter
```
### **2. Set Preset Rules**

```
[root@jd ~]# iptables -P OUTPUT ACCEPT
[root@jd ~]# iptables -P FORWARD DROP
```

### **3. Save Rules**
```
[root@jd ~]# iptables -L –n    #Check if the settings are done, and all the DROPs can be seen This command is temporary, and rebooting the server will still recover to the original rules.
[root@jd ~]# service iptables save # will save the rule in /etc/sysconfig/iptables so that it can take effect after restart.
```

### **4. Add Rules**

Remote SSH Login (Open Port 22)
```
[root@jd ~]# iptables -A INPUT -p tcp --dport 22 -j ACCEPT
[root@jd ~]# iptables -A OUTPUT -p tcp --sport 22 -j ACCEPT
```
WEB Server (Open Port 80)
```
[root@jd ~]# iptables -A INPUT -p tcp --dport 80 -j ACCEPT
```
Email Server (Open Ports 25, 110)
```
[root@jd ~]# iptables -A INPUT -p tcp --dport 110 -j ACCEPT
[root@jd ~]# iptables -A INPUT -p tcp --dport 25 -j ACCEPT
```
FTP Server (Open Port 21)
```
[root@jd ~]# iptables -A INPUT -p tcp --dport 21 -j ACCEPT
```
DNS Server (Open Port 53)
```
[root@jd ~]# iptables -A INPUT -p tcp --dport 53 -j ACCEPT
```
HTTPS (Open Port 443)
```
[root@jd ~]# iptables -A INPUT -p tcp --dport 443-j ACCEPT
```
Allow ICMP (Allow ping)
```
[root@jd ~]# iptables -A OUTPUT -p icmp -j ACCEPT
[root@jd ~]# iptables -A INPUT -p icmp -j ACCEPT
```
Allow loopback (ban of loopback will lead to problems such as failure of normal disabling of DNS)
```
[root@jd ~]# iptables -A INPUT -i lo -p all -j ACCEPT
[root@jd ~]# iptables -A OUTPUT -o lo -p all -j ACCEPT
```
Forbid tcp access of a certain IP
```
[root@jd ~]# iptables -A INPUT -p tcp -s 192.168.1.2 -j DROP
```

### **5. Delete Rules**

First, we need to know the number of the rule; there is a number for each rule

The rule and corresponding number can be shown through iptables -L -n --line-number
```
[root@jd ~]# iptables -L -n --line-number
```

```
num target     prot opt source               destination
1    DROP       tcp -- 0.0.0.0/0            0.0.0.0/0           tcp dpt:3306
2    DROP       tcp -- 0.0.0.0/0            0.0.0.0/0           tcp dpt:21
3    DROP       tcp -- 0.0.0.0/0            0.0.0.0/0           tcp dpt:80
```
 

With the extra line of num, we can see that the corresponding number of the early rule is 2. Then we can conduct the deletion.
```
[root@jd ~]# iptables -D INPUT 2
```
Delete the rule with the INPUT chain number 2

Check by iptables -L -n; the deletion is done.
