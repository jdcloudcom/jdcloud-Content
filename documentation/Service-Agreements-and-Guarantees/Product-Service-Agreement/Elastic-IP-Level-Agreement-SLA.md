### 1. Service Scope

The Service Level Agreement (hereinafter referred to as "SLA") specifies the availability level indicators and the compensation scheme for the service of Elastic IP (hereinafter referred to as "EIP") provided by JD Cloud & AI to customers, including self-owned multi-line (BGP) Elastic IP and edge Elastic IP. The SLA is applicable to the followings:

(1) Self-owned multi-line (BGP) EIP: Multi-line BGP IP searched by WHOIS tool and whose netname is JDCOM;

(2) Edge Elastic IP: For EIP with access point at edge zone, the "IP Type" is displayed as "Edge Elastic IP" when you view IP information.

Other types such as single-line EIP accessed by non-edge zone or multi-line BGPIP with the netname other than JDCOM are not covered by the SLA.

### 2. Service Level Indicator

#### 2.1 Service Functions

Elastic IP provides two-way interconnection service between business resources internally deployed in JD Cloud & AI VPC and Internet network, including dynamic association capacity such as associating and disassociating business resources.

#### 2.2 Service Availability

Service availability standard of JD Cloud & AI’s self-owned multi-line (BGP) Elastic IP: is not less than 99.95%.

Service availability standard of JD Cloud & AI Edge Elastic IP: shall not be less than 99.5%.

**2.2.1 Definitions of service availability**

(1) Service cycle: One service cycle is a natural month and if it is less than a month, then it is not counted as a service cycle. The business unit of statistics is single Public IP, and the time unit is minute.

(2) Total number of minutes of service cycle is calculated as follows: Total number of days within service cycle × 24 (hours) × 60 (minutes).

(3) Service unavailable minute: 

Self-owned multi-line (BGP) Elastic IP service unavailable minutes:

When packets are discarded within one minute when the communication between for a Public IP instance between JD Cloud & AI VPC to the egress gateway, or between the egress gateway and one of the three major operators is completely cut off (the egress is deemed as available when the communication is provided by other operators or other regions), the Public IP instance within this minute is deemed as unavailable. Sum of unavailable minutes of EIP instance within one service cycle is the unavailable service minute.

Edge Elastic IP service unavailable minutes:

When packets are discarded within one minute when the communication between for a Public IP instance between JD Cloud & AI VPC to the egress gateway, or between the egress gateway and one of the three major operators is cut off, the Public IP instance within this minute is deemed as unavailable. Sum of unavailable minutes of EIP instance within one service cycle is the unavailable service minute.

**2.2.2 Calculation formula for service availability**

Service availability is counted by service cycle and calculated as per the method below by the dimension of a single Public IP instance:

Public IP service availability = (Total number of minute of a single Public IP per service cycle - Sum of all unavailable minutes of a single Public IP per service cycle) / Total number of minute of a single Public IP per service cycle X 100%.

#### 2.3 Fault Recovery Capability

JD Cloud & AI provides 7×24 hours of operation maintenance for the cloud services of the paying users, provides technical support by means of on-line ticket and telephone fault reporting, and has a series of fault incident response mechanisms such as fault monitoring, automatic alarm, fast positioning and fast recovery.

#### 2.4 Service Metering Accuracy

Public IP service has an accurate and transparent metering and billing system. JD Cloud & AI settles and deducts charges in real time according to the billing type as well as actual consumption of user’s Public IP instance. The specific billing standard shall be subject to the effective billing model and price announced on the JD Cloud & AI official website. The user's original billing log shall be kept for at least 1 year by default for future reference.

### 3. Service Compensation Terms

#### 3.1 Compensation Scope

In the event of failure of normal use of Elastic IP service purchased by users due to JD Cloud & AI’s device faults, design defects or misoperation, JD Cloud & AI will compensate for the unavailable time, excluding the service unavailable time caused by the following reasons:

(1) Caused by the system maintenance that JD Cloud & AI has notified the users in advance, including migration, maintenance, upgrade and simulation fault drill;

(2) Any problems caused by the network, equipment failure or configuration adjustment other than JD Cloud & AI’s device;

(3) Caused by hacker attacks to the customers’ application programs, including but not limited to Public IP is set as in the blackhole status or cleaning status by JD Cloud & AI when it is subject to DDoS attack;

(4) The customer fails to correctly deploy or configure resources associated with Public IP (such as Virtual Machines, Containers, POD, Load Balancer, etc.) and other problems are caused by relevant exception of carried service;

(5) Service unavailability caused by relevant network configuration error (such as wrong configuration of Security Group, ACL and other reasons) of resources associated to the customer’s Elastic IP;

(6) Caused by loss or leakage of data, passwords, etc. due to user’s improper maintenance or improper confidentiality;

(7) Caused by customers failed to follow JD Cloud & AI product usage document or suggestions for use;

(8) Caused by user’s negligence or operations authorized by the user;

(9) Caused by force majeure and accidents;

(10) Public IP suspended or terminated due to breach of JD Cloud & AI Service Agreement by customers, including but not limited to service suspension, release or others of Public IP due to arrearage;

(11) Other unavailability caused not due to JD Cloud & AI’s account.

#### 3.2 Compensation Scheme

JD Cloud & AI Elastic IP service shall be all compensated by 100 times of unavailable time, neglect of monthly package payment, pay by configuration or pay by traffic.

Compensation amount = Average cost per minute in 24 hours before the Elastic IP instance fails × service unavailable time × 100 times.

Description:

(1) If the Elastic IP, paid by configuration, is used for less than 24 hours by the user before the failure, the average cost per minute shall be calculated as per the actual service time.

(2) Service unavailable time is calculated by minutes.

(3) The compensation will only be made against users who incur cost of Elastic IP services in the form of Elastic IP coupons which cannot be converted to cash for return.

(4) The total compensation amount shall not exceed the total cash cost of current service cycle already paid for the Elastic IP.

#### 3.3 Compensation Application Deadline

(1) If the service cycle of a month fails to reach the service availability standard, you can propose a compensation application via the ticket system of your corresponding account after the fifth (5th) working day of the month following the end of corresponding failure service cycle. JD Cloud & AI will correspondingly verify your compensation application and calculate service availability of the service cycle. If there is a dispute between the Parties, the Parties agree to finally solve such dispute subject to the background records of JD Cloud & AI.

(2) The compensation application proposing time shall be no later than sixty (60) natural days after the end of corresponding failure service cycle. If you failed to propose the compensation application within sixty (60) days after the end of corresponding failure service cycle or propose after sixty (60) days after corresponding failure service cycle or failed to propose the application as agreed in the Agreement, it is deemed that you have automatically given up your right of claim and other rights against JD Cloud & AI. JD Cloud & AI has the right to reject your compensation application and make no compensation or indemnity.

### 4. Others

JD Cloud & AI has the right to make adjustments to some service indicators of the Service Level Agreement according to changes, and promptly publish announcements on JD Cloud & AI official website [ www.jdcloud.com](https://www.jdcloud.com/), or send emails or written notices to notify the users of the modified contents. If you disagree with any modification to the Service Level Agreement by JD Cloud & AI, you have the right to stop using the Elastic IP service. If you continue to use the Elastic IP service, it is deemed that you have accepted the modified Service Level Agreement.
