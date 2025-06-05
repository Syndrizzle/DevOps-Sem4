# Task 2: Establish Auto Scaling using ASG
---

This guide provides step-by-step instructions to configure automatic scaling of EC2 instances using a Launch Template and an Auto Scaling Group (ASG). Auto Scaling ensures that your application can handle varying loads by automatically adjusting the number of EC2 instances.

## 1. Create a Launch Template

A Launch Template defines the configuration for EC2 instances, including the Amazon Machine Image (AMI), instance type, key pair, security groups, and other parameters.

**Steps:**

1. **Access the EC2 Console**:
   * Navigate to the [Amazon EC2 console](https://console.aws.amazon.com/ec2/).

2. **Create a New Launch Template**:
   * In the navigation pane, under **Instances**, select **Launch Templates**.
   * Click **Create launch template**.

3. **Configure the Launch Template**:
   * **Launch template name**: Provide a descriptive name.
   * **Template version description**: Optionally, add a version description.
   * **AMI ID**: Choose the Amazon Machine Image for your instances.
   * **Instance type**: Select the desired instance type (e.g., `t2.micro`).
   * **Key pair**: Choose an existing key pair for SSH access.
   * **Security groups**: Select one or more security groups to define firewall rules.
   * **User data (optional)**: Add any initialization scripts to be run on instance launch.([docs.aws.amazon.com][1])

4. **Create the Template**:
   * Review your settings and click **Create launch template**.

![NVIDIA_Overlay_AI7UP1UMjV](https://github.com/user-attachments/assets/71645723-f9df-4517-914c-72e45651d3c5)

## 2. Create an Auto Scaling Group (ASG)

An Auto Scaling Group manages a collection of EC2 instances, automatically scaling the number of instances based on defined policies.

**Steps:**

1. **Access Auto Scaling Groups**:
   * In the EC2 console, navigate to **Auto Scaling Groups**.

2. **Create a New Auto Scaling Group**:
   * Click **Create Auto Scaling group**.

3. **Configure the Auto Scaling Group**:
   * **Auto Scaling group name**: Provide a name for your Auto Scaling group.
   * **Launch template**: Select the launch template created earlier.
   * **Version**: Choose the default or latest version of the launch template.
![NVIDIA_Overlay_8jcXH30QaZ](https://github.com/user-attachments/assets/22cc123c-e26b-422a-b835-eaad33db6a08)

4. **Configure Network Settings**:
   * **VPC**: Select the Virtual Private Cloud (VPC) where your instances will reside.
   * **Subnets**: Choose one or more subnets within the selected VPC.
![NVIDIA_Overlay_hq1B8jOBcy](https://github.com/user-attachments/assets/a9e86466-ce38-4a68-ada2-db350a90f940)

5. **Set Group Size and Scaling Policies**:
   * **Desired capacity**: Set the initial number of instances.
   * **Minimum capacity**: Define the minimum number of instances.
   * **Maximum capacity**: Define the maximum number of instances.

6. **Review and Create**:
   * Review all settings and click **Create Auto Scaling group**.

![NVIDIA_Overlay_yqyR7E0bwA](https://github.com/user-attachments/assets/8f4c4ed5-8f40-49a4-800f-465c0837a176)

