#### 1. Service Scope

Database of JD Cloud & AI provides users with online database services. Support MySQL，Percona，MariaDB，SQL Server, PostgreSQL, and provide database online expansion, backup roll-back, performance monitoring and analysis capabilities. The cloud database supports resilient capacity expansion and provides on-demand and pay-as-you go settling functions based on the cloud computing model.

The SLA only applies to primary and secondary high-availability versions of the database, rather than the standalone version.

### 2. Service Level Indicators

#### 2.1 Data Persistence

- Primary Instance:
- Data Persistence: No less than 99.9999%.
- Data persistence is counted by service period. One service period is a natural month. If it is less than one month, it is not counted as one service period. That is, for every 1,000,000 database instances of cloud database users, the probability that the data is not lost is 99.9999%, or only one cloud database instance may have data loss every month.
- Read-only Instance:

Read-only instances do not guarantee data persistence.

#### 2.2 Data Destructibility

2.2.1 If the user deletes the data or needs to destroy the data after the service expires, JD Cloud & AI will automatically clear the disk and memory data on the corresponding physical server, so that the data cannot be recovered.

2.2.2 Before the equipment used in the cloud service is scrapped, disposed, repaired by outsourcing or resold, JD Cloud & AI will degauss its physical disk.

#### 2.3 Data Migration

The cloud database is delivered to the user as an online database instance and currently it supports MySQL 5.6, MySQL 5.7, Percona 5.7, SQL Server 2008 R2, PostgreSQL10.6 and PostgreSQL11.2 version. Users can import or export standard data formats through the corresponding database customer software to meet the migration requirements of user data.

#### 2.4 Data Privacy

JD Cloud & AI uses encryption, security group isolation and other means to ensure that user data in the same resource pool is mutually invisible. The security group isolates different user resources through a series of identity and access management technologies such as data link layer and network layer.

#### 2.5 Right to Know about Data

2.5.1 The user has the right to know the data, the geographical location of the data center where the backup data is located, and the number of data backups, among which:

2.5.1.1 At present, the data centers of JD Cloud & AI are located in cn-north-1, cn-east-1, cn-east-2 and cn-south-1. Users must select the corresponding data according to the geological position when applying for cloud service and the user data will be stored in its designated data center;

2.5.1.2 JD Cloud & AI Service has automatic data backup function. Please refer to the related technical documents for the number of backups. The backup data is stored in the same data center as the source data by default. The user does not need to specify the number of automatic backups and the location where the data backed up automatically is stored.

2.5.2 JD Cloud & AI data center will comply with relevant local laws and regulations, and users have the right to know about this, and can contact JD Cloud & AI's customer service personnel for detailed information.

2.5.3 Unless required by local laws and regulations, or regulatory and auditing requirements of government's regulatory authorities, all data, applications and behavior logs of users will not be provided to third parties. In addition to the statistics and analysis of the operating status of the products used by JD Cloud & AI, the user's behavior log will not present the user's personal information data.

#### 2.6 Data Reviewability

In accordance with current laws and regulations or according to the requirements of government regulatory authorities, safety compliance, auditing or forensics investigations and in the context of complete processes and procedures, JD Cloud & AI can provide relevant information of the service purchased by the user, including running logs of key components, operation records of operation and maintenance personnel, and user's operation records.

#### 2.7 Service Features

The cloud database is an online database service that supports MySQL 5.6, MySQL 5.7, Percona 5.7, SQL Server 2008R2, PostgreSQL10.6 and PostgreSQL11.2 version. The cloud database instance can be available through the Web or API, and it provides online database capacity expansion, backup roll-back, performance monitoring and analysis functions, as well as data backup, data recovery, log management and other management functions. For details on all the specific functions of the cloud database, please refer to the detailed description documentation, technical documentation and help documentation provided by JD Cloud & AI on the official website. All functional changes to the cloud database that may affect the user will be announced to the user.

#### 2.8 Service Availability

- Primary Instance:
- Service availability: no less than 99.95%.
- The cloud database availability calculation formula is: all available time per service term for a single database instance/ (all available time per service term for a single database instance + all unavailable time per service term for a single database instance).

Wherein:

(1) Cloud database availability is counted according to service term. One service term is a natural month. If it is less than one month, it is not counted as one service term. The statistical business unit is a single database instance, and the time unit is minutes.

(2) Unavailable Time: The time when the service provided by cloud database is not available for 5 minutes or more, and if the service is unavailable for less than 5 minutes, it is not counted into unavailable time. The unavailable time of cloud database service does not include daily system maintenance time, and the unavailable time due to user reasons, third-party causes, or force majeure.

(3) The temporary instance service provided by the cloud database does not provide service availability guarantee.

- Read-only Instance:

Read-only instances do not guarantee service availability. Use read-write separation techniques to ensure high availability of links.

#### 2.9 Service Resource Allocation Capability

The cloud database provides multiple configurations and flexible capacity expansion. Currently, the minimum configuration supports 1 core, 1GB of memory and 300 maximum connections. The maximum configuration supports 16 cores, 64GB of memory and 16,000 maximum connections. Users can expand or reduce cloud database resources used according to the demand, and realize online seamless upgrade of the database.

#### 2.10 Fault Recovery Capability

JD Cloud & AI provides 7×24h operation and maintenance for the cloud services of paying users, and provides technical support by means of online open ticket and phone reporting, and has a series of fault emergency response mechanisms such as fault monitoring, automatic alarm, rapid positioning and fast recovery.

#### 2.11 Service Measurement Accuracy

Cloud database service has an accurate and transparent metering and billing system. JD Cloud & AI settles and charges in real time according to the actual usage of the user's cloud database, and the specific billing standard is subject to the effective billing mode and price announced on the official website of JD Cloud & AI. The user's original billing log is reserved for a minimum of 1 year by default for future reference.

#### 2.12 Service Compensation Terms

2.12.1 Compensation Scope:

For the inability of cloud database service to work properly caused by JD Cloud & AI fault, and the inability of normal access to the website caused by JD Cloud & AI fault, JD Cloud & AI will compensate for the unavailable time. However, the service unavailable time caused by the following reasons is not included:

(1) Caused by the system maintenance procedures after JD Cloud & AI's notification in advance, including cutting, maintenance, upgrading and simulated fault drill;

(2) Packet loss and delay caused by operators' fault;

(3) Caused by the hackers' hacking to the users' application programs or data information;

(4) Caused by the loss or leakage of data, commands, passwords etc. due to user's improper maintenance or improper confidentiality measures;

(5) Caused by the user upgrading the operating system by himself;

(6) Caused by the user's application or installation activities;

(7) Caused by user's negligence or operation authorized by the user;

(8) Caused by force majeure and accidents;

(9) Unavailability caused by other reasons not related to JD Cloud & AI.

2.12.2 Compensation plan

Fault time = unavailable time.

Cloud database in monthly package is compensated in the way of service time compensation, i.e. 100 times/set of the fault time.

Cloud database pay by configuration is compensated in the form of coupon, the payout amount = the average hourly cost in the first 24 hours of the fault/ 60 × fault time × 100.

Instructions:

If the use time of cloud database pay by quantity is less than 24 hours, the cost shall be calculated based on the average of actual use time;

The fault time is calculated in points;

Total amount of compensation shall not exceed the total amount of cash paid for current service by a single cloud database;

### 3. Others

JD Cloud & AI has the right to make adjustments to some service indicators of the SLA according to the changes, and promptly publish announcements at [www.jdcloud.com](https://www.jdcloud.com) or send emails or written notices to notify users of the revised content.
