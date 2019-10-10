# pulumi-talk
Notes and links for my talk on Pulumi


#### Why Apples vs. Bananas?

First slide: Why Pulumi vs. Ansible?

Ask stackshare.io!! 

--> https://stackshare.io/pulumi/alternatives


#### Pulumi service backend architecture

https://www.pulumi.com/docs/intro/concepts/state/

![pulumi-service-backend-arch](https://www.pulumi.com/images/docs/reference/state_saas.png)

Pulumi self-hosted service-backend is only available in "Pulumi Enterprise": https://www.pulumi.com/pricing/ :(((


#### Pulumi is somehow like a nice Terraform-Wrapper

https://www.pulumi.com/docs/intro/vs/terraform/#using-terraform-providers

Pulumi is able to adapt any Terraform provider - and many of the most interesting Pulumi providers are derived Terraform providers 

--> There's even a Terraform converter: https://www.pulumi.com/docs/intro/vs/terraform/#converting-from-terraform

And Terraform and Pulumi could be used together a the same time: https://www.pulumi.com/blog/using-terraform-remote-state-with-pulumi/



#### Comparing Infrastructure-as-Code tools is hard!

!->; Provisioning vs. Configuration Management tools (see https://blog.gruntwork.io/why-we-use-terraform-and-not-chef-puppet-ansible-saltstack-or-cloudformation-7989dad2865c?gi=cfad03e3531b)

----> BUT: the lines blur! could do some CM tasks with Terraform, but you can do every single provisioning task with Ansible! (AND it's Master AND agentless!)





#### The academic comparison: "Mutable vs. Immutable infrastructure"

See https://blog.gruntwork.io/why-we-use-terraform-and-not-chef-puppet-ansible-saltstack-or-cloudformation-7989dad2865c#b264



__Mutable: Ansible, Chef, Puppet, Saltstack__

> For example, if you tell Ansible to install a new version of OpenSSL, it’ll run the software update on your existing servers and the changes will happen in-place. Over time, as you apply more and more updates, each server builds up a unique history of changes. This often leads to a phenomenon known as configuration drift,

--> simply: same servers, changed every time.

__Immutable: Pulumi, Terraform__

> If you’re using a provisioning tool such as Terraform to deploy machine images created by Docker or Packer, then every “change” is actually a deployment of a new server (just like every “change” to a variable in functional programming actually returns a new variable). For example, to deploy a new version of OpenSSL, you would create a new image using Packer or Docker with the new version of OpenSSL already installed, deploy that image across a set of totally new servers, and then undeploy the old servers.

--> simply: new servers, every time.

__Opinion__: Like most academic classification, this doesn't apply in practice!

1. In practice, your Infrastructure code isn't performed manually by yourself from the CLI. Hell NO! We have CI/CD systems doing that for us! And as we are doing Infrastructure-as-CODE, we treat this code like any other code! It'll go through stages - from dev/branches, to master/stage to production.
   --> that means, you only need to look into your CI/CD pipelines (like GitLab CI) to see the state of your servers!
   --> no configuration drift without git commit possible - and if the drift happens, it is intended
2. These tools have a focus on one classification - but you can also do things from the other concept to some extend. Have a look at Terraform's [remote-exec Provisioner](https://www.terraform.io/docs/provisioners/remote-exec.html) for example. The only exception is Pulumi right now, but it's on the roadmap.
   --> No commands on the systems possible right now with Pulumi!!! :((( (see https://github.com/pulumi/pulumi/issues/127 & https://github.com/pulumi/pulumi/issues/99 & https://github.com/pulumi/pulumi/issues/1691)
   --> It's definitely NOT possible to configure a system/server/container whatsoever with Pulumi!!!
3. If you choose Ansible with it's concept of idempotency! Run your commands once or multiple times: the result will be the same!


__-->__ this leads us to the conclusion: 

> So the state of the machine deviates, or drifts, from the baseline due to manual changes and updates. (see https://shadow-soft.com/ansible-idempotency-configuration-drift/)

##### The core problem is configuration drift! And there are 2 approaches that could be taken to avoid it

1. Rebuild machine instances frequently so they don’t have much time to drift from the baseline.

2. Use Ansible (& Co.) and run them frequently and repeatedly to keep machines in line

--> See?! It's all about the __frequently__ part! You could also say: continuous! That leads us to modern ways on how to work with Infrastructure code: Continuous infrastructure!



##### Procedural vs. Declarative

again see see https://blog.gruntwork.io/why-we-use-terraform-and-not-chef-puppet-ansible-saltstack-or-cloudformation-7989dad2865c?gi=cfad03e3531b

__Procedural: Chef, Ansible__

>  they encourage a procedural style where you write code that specifies, step-by-step, how to to achieve some desired end state.

--> simple: step-by-step "as your code would be the admin" (and as every tutorial states)


__Declarative: Terraform, Pulumi, CloudFormation, SaltStack, Puppet__

> encourage a more declarative style where you write code that specifies your desired end state, and the IAC tool itself is responsible for figuring out how to achieve that state.

--> simple: say what you want, not how. 


Again like Mutalbe vs. Immutalbe: What is the core problem, that should be solved?

###### It's the answer to: What is the current state of my infrastructure? 2 approaches again:

1. Use a declarative approach and have a look into your code.

2. Simply have a look into your CI/CD pipeline to see what has happened last. 

--> In theory, the declaritive approach might "win" the battle. I seems more clean and accurate then these "procedural tools down there in the dust". 
But in practice there are some good reasons why procedural approach is maybe better. 

1. It's absolutely easy to understand! Every Sysadmin knows after minutes of intro: "Ah, this thing automates manual tasks for me! Great!" Try this with Terraform: "What tell hell is this tool doing behind the scenes?"
2. Every tutorial on the web could be easily transformed into procedural code - it's that simple! The declarative tool user simply has a problem, if the needed tool has no provider/module whatsoever for the given task. Or they simply use a procedural tool then ;P
3. less magic - more understanding, what the tool does
4. The downside of a procedural tool, that you don't exactly see the current state of your infrastructure solely in the code, could be wiped out with the use of modern CI/CD tools and GitOps workflows (that you should use in exactly the same way with declarative tools)





#### 2019 state

https://medium.com/@griggheo/good-devops-tech-skills-to-have-in-2019-75d7102eaf28


#### Pulumi? YOUNG! 

1.0 in 09/2019 https://www.heise.de/developer/meldung/Infrastructure-as-Code-Die-Plattform-Pulumi-erreicht-Version-1-0-4516570.html


#### JavaScript! --> Use "every" program language you like is currently simple marketing joke

If you have a look at the docs, you'll soon notice, that the Pulumi JavaScript/Typescript docs are great - but choosing Python already is quite disillusioning. And isn't simply there! And no other language as well.

But it's all on the roadmap:



#### Roadmap

Roadmap: https://github.com/pulumi/pulumi/wiki/Roadmap

![backlog](backlog.png)



#### What does reddit say?

> The documentation is pretty incomplete

https://www.reddit.com/r/devops/comments/bcdwsn/pulumi/


##### Is YAML really bad? Or how to transform an organisation with classic Sysadmins

> I know some of the guys here do not like YAML. However, it has its place. Not everyone is completely dev minded. YAML in my opinion is a nice middle ground for more ops guys that are gaining more Dev mentality.
 !!! -> Puppet had the problem with code also (abstraction, classes and so on...)

There are maybe not only god-like code cracks out there! Imaginge the classic Sysadmin -> maybe you could easily "infect" somebody like this to use a simple YAML-based approach, that could be written with simple editors. Coming around the corner with a full blown language could maybe overwhelm people?!


##### Google isn't Pulumi's friend right now: Ansible xyz googlen__ vs. __Pulumi xyz googlen

> What would help is better docs - last I checked the docs were not good at all and in a lot of typescript and nodejs. I feel more people who would be doing this would be more comfortable with python and the docs for python were weak. For something like this you need great docs.
  I know there is a guy in a thread who is tired of ansible but man are the docs pretty good. You can literally google 'ansible <thing> module' and the page comes up. I'll look at it again when the docs are better.


#### Large Community vs Small Community

![comparison-community-common-iac-tools](comparison-community-common-iac-tools.png)

> Ansible leads the pack in terms of popularity