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


#### Pulumi? YOUNG! AND JavaScript!

1.0 in 09/2019 https://www.heise.de/developer/meldung/Infrastructure-as-Code-Die-Plattform-Pulumi-erreicht-Version-1-0-4516570.html

Pulumi On-premises/self-hosted only in "Pulumi Enterprise": https://www.pulumi.com/pricing/ :(((


#### Roadmap

Roadmap: https://github.com/pulumi/pulumi/wiki/Roadmap

![backlog](backlog.png)

Provisioners!!! :((( (see https://github.com/pulumi/pulumi/issues/127 & https://github.com/pulumi/pulumi/issues/99 & https://github.com/pulumi/pulumi/issues/1691)


> The documentation is pretty incomplete

https://www.reddit.com/r/devops/comments/bcdwsn/pulumi/

> I know some of the guys here do not like YAML. However, it has its place. Not everyone is completely dev minded. YAML in my opinion is a nice middle ground for more ops guys that are gaining more Dev mentality.
 !!! -> Puppet had the problem with code also (abstraction, classes and so on...)

__Ansible xyz googlen__ vs. __Pulumi xyz googlen__

> What would help is better docs - last I checked the docs were not good at all and in a lot of typescript and nodejs. I feel more people who would be doing this would be more comfortable with python and the docs for python were weak. For something like this you need great docs.
  I know there is a guy in a thread who is tired of ansible but man are the docs pretty good. You can literally google 'ansible <thing> module' and the page comes up. I'll look at it again when the docs are better.