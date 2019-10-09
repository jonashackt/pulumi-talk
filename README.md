# pulumi-talk
Notes and links for my talk on Pulumi


First slide: Why Pulumi vs. Ansible?

Ask stackshare.io!! 

--> https://stackshare.io/pulumi/alternatives


#### Terraform vs. other IaC

!->; Provisioning vs. Configuration Management tools (see https://blog.gruntwork.io/why-we-use-terraform-and-not-chef-puppet-ansible-saltstack-or-cloudformation-7989dad2865c?gi=cfad03e3531b)

----> BUT: the lines blur! could do some CM tasks with Terraform, but you can do every single provisioning task with Ansible! (AND it's Master AND agentless!)

--> Warning: the `Procedural vs Declarative` part is complete non-sense! No one defines 10 servers inside a Ansible playbook - you always use Inventories, which can also be dynamic based on Cloud infrastructure providers

#### Mutable vs. Immutable infrastructure

See https://blog.gruntwork.io/why-we-use-terraform-and-not-chef-puppet-ansible-saltstack-or-cloudformation-7989dad2865c#b264

Mutable: Ansible
Immutable: Pulumi/Terraform


#### Large Community vs Small Community

![comparison-community-common-iac-tools](comparison-community-common-iac-tools.png)

> Ansible leads the pack in terms of popularity



#### 2019 state

https://medium.com/@griggheo/good-devops-tech-skills-to-have-in-2019-75d7102eaf28