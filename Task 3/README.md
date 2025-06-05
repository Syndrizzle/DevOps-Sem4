# Task 3: Application Load Balancer-Based Path-Based Routing

The *Application Load Balancer (ALB)* is one of the strong traffic management tools offered by *Amazon Web Services (AWS). Using request attributes like URL path, host headers, or query strings, ALB is made to route HTTP and HTTPS traffic to your targets. One of the most popular methods is **Path-Based Routing*, which routes traffic to various target groups according to the URL path in incoming requests.

For instance, the ALB can use these paths to route traffic to various backend resources (such as EC2 instances) if you have multiple applications running in different environments (e.g., /app1 and /app2).

Creating a *Application Load Balancer* and establishing listener rules to analyze the path in the incoming requests are the first steps in setting this up. Depending on the specified path, the listener will forward traffic to various *Target Groups* (traffic to /app1/* goes to Target Group 1 and /app2/* goes to Target Group 2). One or more EC2 instances or additional resources, such as Lambda functions, may be present in each target group.

Additionally, you set up *Nginx* (or another server) on the backend to manage the traffic and route it according to the URL path. For instance, the ALB may handle requests to /app1 behind the scenes, while another application may handle requests to /app2. These Apps will be hosted on two different instances.

With *Path-Based Routing*, you can maintain a tidy and effective infrastructure configuration while optimizing traffic flow, isolating application tiers, and enhancing scalability by allocating traffic to various resources according to the URL path.

#### 1) ALB 
![WhatsApp Image 2025-05-30 at 12 32 32_2a3b4169](https://github.com/user-attachments/assets/02484d7c-23f0-49fa-a41c-82786de4cbd3)

#### 2) Two target groups for each instance
![WhatsApp Image 2025-05-30 at 12 32 42_1d45586c](https://github.com/user-attachments/assets/f581eeee-a576-41d8-bafe-9001bc488fe5)

#### 3) Health Checks for both of the target groups 
![WhatsApp Image 2025-05-30 at 12 58 38_d6e67a04](https://github.com/user-attachments/assets/d7d9767a-4a8d-48db-8725-8f03d93e0c51)

![WhatsApp Image 2025-05-30 at 13 16 18_5a708f8e](https://github.com/user-attachments/assets/00261dba-bd33-4338-9f8c-e7b965419e51)

#### 4) Final result, the index.html page after alb routes the traffic to the desired instance.
app1

![WhatsApp Image 2025-05-30 at 13 16 39_8546513c](https://github.com/user-attachments/assets/e9ab8ea0-5188-4698-913a-96398f4674c1)

app2

![WhatsApp Image 2025-05-30 at 12 51 52_29c08064](https://github.com/user-attachments/assets/d2173025-fab7-4fc8-ba0b-c7390e45a3e6)