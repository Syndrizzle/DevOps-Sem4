# Task 1: Establish connectivity to private EC2 instance from Public EC2 (Bastion Host)
---

## 1. Virtual Private Cloud (VPC) Setup

* **Create a VPC** with an appropriate IPv4 CIDR block (e.g., `10.0.0.0/16`).
* **Enable DNS support and hostnames** to facilitate name resolution within the VPC.
![VPC](https://github.com/user-attachments/assets/f1221bab-5c23-4c81-bf79-9627ccdadc40)

## 2. Subnet Configuration

* **Public Subnet**:
  * Allocate a CIDR block (e.g., `10.0.1.0/24`).
    ![zen_dIijhaqc9I](https://github.com/user-attachments/assets/2f2e896d-970d-4126-88e5-eb85e795dd3f)
  * Enable auto-assign public IP for instances launched here.
    ![zen_i3qdctubtM](https://github.com/user-attachments/assets/2670f056-8b3d-42d7-8281-69ab6d607827)

* **Private Subnet**:
  * Allocate a different CIDR block (e.g., `10.0.2.0/24`).
  * ![zen_fxf82XMuyB](https://github.com/user-attachments/assets/8e903e55-57bd-403b-a6dd-bc7d3505b8ac)

## 3. Internet Gateway (IGW)

* **Create an IGW** and attach it to your VPC.
* This allows instances in the public subnet to access the internet.
![zen_W8HEwE2Wu1](https://github.com/user-attachments/assets/34e1e662-8929-4c56-90ea-af4f3cea6780)
![zen_JtDY0fYJlH](https://github.com/user-attachments/assets/efcce3a2-9e7b-4884-89a3-9875a276222c)

## 4. Route Tables

* **Public Route Table**:
  * Add a route directing `0.0.0.0/0` traffic to the IGW.
  * Associate this route table with the public subnet.
    ![zen_fkVKPpUdjf](https://github.com/user-attachments/assets/f90b8bda-54d0-4ffc-b3bb-e51a332ee9a1)

* **Private Route Table**:
  * Initially, no route to the internet is added.
  * Associate this route table with the private subnet.
    ![zen_QGH2M9pUWz](https://github.com/user-attachments/assets/568fc43b-aa74-4c4f-b541-c381b6a6ed6e)

## 5. NAT Gateway (Optional)

* **Allocate an Elastic IP** for the NAT Gateway.
  ![zen_k5BwrPDj4N](https://github.com/user-attachments/assets/9653ab97-cc07-47d5-a2f1-cdf412d1dd8f)
* **Create a NAT Gateway** in the public subnet using the allocated Elastic IP.
  ![zen_E0HVD3Ha7s](https://github.com/user-attachments/assets/614b5a5c-dcef-4cbd-9881-d53e66244130)
* **Update the Private Route Table** to route `0.0.0.0/0` traffic to the NAT Gateway.
  ![zen_5OvbWkD1eQ](https://github.com/user-attachments/assets/6fd232f3-9069-49ab-8b6f-49e099422021)
* This allows instances in the private subnet to initiate outbound connections to the internet.

### Resource Map upto this point:
![zen_6vRDzncq1o](https://github.com/user-attachments/assets/198b3e17-853f-46a5-8e22-65eeab9cc415)

## 6. Bastion Host (Public EC2 Instance)

* **Launch an EC2 instance** in the public subnet.
* **Assign a public IP address** to this instance.
![zen_R7nJZjm98e](https://github.com/user-attachments/assets/44a5fc8c-e6d4-447a-9b3c-0624bda99d65)
![zen_O36ljRwAd8](https://github.com/user-attachments/assets/81741a63-a5e9-40db-a56f-301b82e68467)

## 7. Private EC2 Instance

* **Launch an EC2 instance** in the private subnet.
* **Do not assign a public IP address** to maintain its private status.
* **Security Group Configuration**:
  * Inbound: Allow SSH (port 22) from the bastion host's security group.
  * Outbound: Allow all traffic if the instance needs to access the internet via the NAT Gateway.
![zen_1fFpa3JsbG](https://github.com/user-attachments/assets/0428dffe-94c3-42d8-a726-abaa7bf06d5f)

## 8. SSH Access Workflow

* **Connect to Bastion Host**:
  * Use your SSH key to connect:
    ```bash
    ssh -i /path/to/key.pem ubuntu@<Bastion_Public_IP>
    ```
    ![NVIDIA_Overlay_14BUYlJ0yJ](https://github.com/user-attachments/assets/ae320edf-65ee-4728-b7fd-b044a8949945)

* **From Bastion Host to Private Instance**:
  * Use the private IP of the target instance:
    ```bash
    ssh -i /path/to/key.pem ubuntu@<Private_Instance_Private_IP>
    ```
    ![NVIDIA_Overlay_v6DkM9WwcT](https://github.com/user-attachments/assets/a3c05116-d8f5-4c4a-bb37-5b417df9f737)
