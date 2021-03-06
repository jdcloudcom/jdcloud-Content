# Setting of Protection Scheduling Rules

If your origin server is at JD Cloud & AI, you can set the protection scheduling rules to implement interaction between Anti-DDoS Pro and cloud resources, and switch to and enable Anti-DDoS Pro only in specific scenarios to guarantee the smooth experience in daily business in case of no DDoS attack and better protection effects in case of any attack.

![防护调度规则](../../../../image/Advanced%20Anti-DDoS/dispatch-rule-01.png)

In case of no attacks, Anti-DDoS Pro serves as the backup; user traffics will directly access cloud resources the protection of Anti-DDoS Basic or Anti-DDoS Protection Package, without addition of any delay; In case of attack, automatically switch to Anti-DDoS Pro. Then, traffics will be cleaned by Anti-DDoS Pro at first and returned to the origin server of the cloud.

## Operation Steps

Configuration steps of protection scheduling rules are as below:

- First log in to [Anti-DDoS Pro Console](https://ip-anti-console.jdcloud.com/instancelist).
- Find the instance to be configured, and click the instance name to enter the **Instance Details** page.
- Switch to **Protection Scheduling Rules** 

![防护调度规则](../../../../image/Advanced%20Anti-DDoS/dispatch-rule-02.png)

Click **Add** to enter the configuration page of protection scheduling rules.

![非网站防护规则](../../../../image/Advanced%20Anti-DDoS/dispatch-rule-03.png)

Well set a rule name, select a corresponding cloud IP, set appropriate scheduling trigger threshold and click **Save

![非网站防护规则](../../../../image/Advanced%20Anti-DDoS/dispatch-rule-04.png)


Some fields of protection scheduling rules configuration are interpreted as below:

Cloud IP: Select the cloud IP to be protected<br>
Scheduling trigger threshold: A scheduling trigger condition that scheduling to Anti-DDoS Pro will be triggered if the request traffic or packets per second to the origin server exceed the threshold set. Two hours after the attack is stopped and when the request traffic or packets per second to the origin server are lower than the threshold, Anti-DDoS Pro will be switched to the origin server.<br>
**Description**: You are suggested to consider the business uprush when setting the scheduling trigger threshold, and set the threshold as 2 times the business peak in history to avoid frequent trigger interaction switch.

## Application Steps:

1. Configure Anti-DDoS Pro forwarding rules
2. Verify whether the Anti-DDoS Pro forwarding rules are normal
3. Configure protection scheduling rules
4. Modify DNS parsing of domain to parse DNS to the CNAME address assigned by protection scheduling rules.

## Notes

1. Pre-configuration of forwarding rules of businesses to be protected is required.
2. After protection scheduling rules are configured, only CNAME provided by protection scheduling rules are configured for CNAME resolution records of DNS, and it is unnecessary to use CNAME produced with forwarding rules.
3. Time for scheduling to Anti-DDoS Pro is limited by the effective time of DNS TTL.
4. To avoid direct attack against cloud IP after the cloud IP is exposed, you are suggested to add backup IP. Normally, in case of any attack, direct access to cloud IP will be returned to the backup IP through Anti-DDoS Pro. The separation of cloud IP for normal use and back-to-origin IP used in case of attack can effectively improve the availability of business.
5. Due to the limit of DNS effective time, there is latency in switch from origin server to Anti-DDoS Pro in case of attack traffic, and when super high traffic directly attacks cloud IP, cloud IP may be blocked by the operator, so please guarantee that the business will not be impacted in case that any individual IP is blocked by the operator.
