# Task 6: VPC Examining Two AWS Accounts

For improved isolation, security, and management, resources are frequently dispersed across several AWS accounts in real-world cloud architectures. AWS has a powerful feature called *VPC Peering* that allows two *Virtual Private Clouds (VPCs)* to communicate with each other, even if they are part of different AWS accounts.

This task involves establishing *VPC Peering* between two VPCs, each of which is housed in a different AWS account. Creating VPCs, setting up subnets, connecting Internet Gateways (IGWs), and creating a *Peering Connection* that permits private communication between instances in one VPC and instances in the other are the steps involved.

To route traffic through the peering connection, *Route Tables* in both VPCs must be updated after the peering request is approved. In order to allow communication, *Security Groups* must also allow ICMP or other required protocols.

By avoiding the public internet and facilitating smooth networking between apps or services operating across various AWS accounts, this configuration improves *security* and *latency*. It is particularly helpful in shared services models between teams or organizational units, hybrid environments, and microservices architectures.
#### 1) Subnet creation
![image](https://github.com/user-attachments/assets/6e72c631-02bd-41f9-afef-eb8bdcf87157)
#### 2) VPC Creation
![image](https://github.com/user-attachments/assets/9cc9f68a-d5ab-4ff7-b8d6-d8a901da25b6)
#### 3) IGW Creation
![image](https://github.com/user-attachments/assets/1950dfc0-0472-4754-b9fe-748941ff76c1)
#### 4) Route Tables Creation
![image](https://github.com/user-attachments/assets/6d21e96b-8d0a-4f1e-b41f-4e47bed3d7d4)
#### 5) Instance Creation
![image](https://github.com/user-attachments/assets/118be950-90a6-43eb-844b-add2bf031644)
#### 6) Establish Peering Connection
![WhatsApp Image 2025-05-31 at 00 46 19_be94a9bd](https://github.com/user-attachments/assets/647bfa29-f53b-4df2-8dfd-160835371353)
#### 7) Access the other instance using SSH from the first instance and vice versa
#### instance 2 via instance 1
![WhatsApp Image 2025-05-31 at 00 32 21_fdad36e4](https://github.com/user-attachments/assets/967e4736-32d1-4d15-9f89-acfeceb947f9)
#### instance 1 via instance 2
![WhatsApp Image 2025-05-31 at 00 33 49_4e4a213a](https://github.com/user-attachments/assets/0dc9cee0-2f88-4a79-bb37-d078c1323040)
