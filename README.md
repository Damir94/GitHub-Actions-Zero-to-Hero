# GitHub Actions using Self-Hosted Runner 

<img width="979" height="386" alt="Screenshot 2025-09-30 at 12 29 56 PM" src="https://github.com/user-attachments/assets/4953977b-2463-4d2f-ae46-9df6628c66e8" />

## Setting up a Self-Hosted GitHub Action Runner for Python-Based Application on AWS EC2 Instance

GitHub Actions is a powerful and flexible platform for automating software development workflows. With GitHub Actions, developers can easily build, test, and deploy their code directly from their GitHub repositories. GitHub provides two types of runners: GitHub-hosted runners and self-hosted runners. In this blog post, we will focus on the benefits of using self-hosted runners for Python applications and how to set them up using an EC2 instance.

## Why Self-Hosted Runners?

Self-hosted GitHub runners offer more control, customization, and scalability for organizations with specific requirements or workflows that demand more resources than the default runners can provide. These are mostly used for Private Projects, and ones that require some kind of specific dependencies or Software Version.

## Steps to Follow

Step 1 — Create an AWS EC2 T2 Micro Instance(Free Tier). Configure Inbound and Outbound Rules to allow SSH (Port22), HTTP (Port 80), and HTTPS (Port 443) Traffic.

<img width="1606" height="191" alt="Screenshot 2025-09-30 at 12 19 00 PM" src="https://github.com/user-attachments/assets/41de3284-bdd0-4c9d-95d3-dc6210a9c503" />

## Enabling Inbound and Outbound SSH and HTTP Traffic

<img width="1614" height="368" alt="Screenshot 2025-09-30 at 12 20 13 PM" src="https://github.com/user-attachments/assets/d128e9c5-7313-4664-9687-c5f29d3f395f" />

<img width="1600" height="360" alt="Screenshot 2025-09-30 at 12 21 24 PM" src="https://github.com/user-attachments/assets/88124385-e365-42da-9521-7606f3ebe35f" />

Step 2 — Connect your AWS EC2 Instance with your GitHub Actions Repository and an example of Self Hosted Runner

 - Goto your GitHub Repository → Actions → Runners → Click on Create self hosted runner → Add a new self hosted runner
 - Select the image as Linux and architecture based on your EC2 Instance configuration.
 - Run all the commands in the Download section on your EC2 Instance, this will set up the connection using token and authentication.

<img width="1437" height="582" alt="Screenshot 2025-09-30 at 12 25 38 PM" src="https://github.com/user-attachments/assets/d96cdae8-4cd3-4c35-a33f-4188c5c98d87" />

Once the self-hosted runner is set up, you can use it to run your workflows on your EC2 instance. In the workflow file, you can specify the runs-on parameter as the name of the self-hosted runner.

For example, if you have named your runner “my-runner”, you can specify it in your workflow file like this:

<img width="683" height="709" alt="Screenshot 2025-09-30 at 1 04 58 PM" src="https://github.com/user-attachments/assets/32d80b93-6343-4205-bc21-3a4cdf71d434" />

You will need to change runs on to self-hosted.

This will ensure that your workflow runs on the self-hosted runner instead of the GitHub-hosted runner i.e. self-hosted runner.yml.

Once you do the same, you will get the below output

<img width="824" height="239" alt="Screenshot 2025-09-30 at 12 45 13 PM" src="https://github.com/user-attachments/assets/5e56eb5b-7952-41b6-ae9f-4038089dfe1c" />

When you goto your GitHub console, you should be able to see the below changes.

<img width="1884" height="518" alt="Screenshot 2025-09-30 at 12 45 40 PM" src="https://github.com/user-attachments/assets/059ca31c-5c34-4b66-8c37-b508e67c6cdf" />


## Comparing with Jenkins 

### Advantages of GitHub Actions over Jenkins

- Hosting: Jenkins is self-hosted, meaning it requires its own server to run, while GitHub Actions is hosted by GitHub and runs directly in your GitHub repository.

- User interface: Jenkins has a complex and sophisticated user interface, while GitHub Actions has a more streamlined and user-friendly interface that is better suited for simple to moderate automation tasks.

- Cost: Jenkins can be expensive to run and maintain, especially for organizations with large and complex automation needs. GitHub Actions, on the other hand, is free for open-source projects and has a tiered pricing model for private repositories, making it more accessible to smaller organizations and individual developers.

### Advantages of Jenkins over GitHub Actions

- Integration: Jenkins can integrate with a wide range of tools and services, but GitHub Actions is tightly integrated with the GitHub platform, making it easier to automate tasks related to your GitHub workflow.

In conclusion, Jenkins is better suited for complex and large-scale automation tasks, while GitHub Actions is a more cost-effective and user-friendly solution for simple to moderate automation needs.


