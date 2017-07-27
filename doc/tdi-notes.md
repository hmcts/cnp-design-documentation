
With Infrastructure as Code, we open up a new way of working - a new way of cooperating - which is fundamental to the emerging Devops movement.
When you are adding a new feature or to fix a bug, getting the confidence you are not making things worse is key.

Avoiding:
Functional harm - introduction of bugs into the system, striving to release bug-free IaC. We won't ever be able to eradicate mistakes, but we can accept responsibility for them and ensure that we learn from them putting mechanisms in place to avoid repeating them.
Structural harm - introducing inflexibility into our systems, making infrastructure as code harder to change. Under a positive prospective, it must be possible to make changes without the cost of change being exorbitantly high

As infrastructure developers, the software we have written builds and runs the entire infrastructure on which our production systems, the applications, and ultimately the business, operate. The cost of a bug, or of introducing structural inflexibility to the underpinning infrastructure on which our business runs is potentially even greater than that of a bug in the application code itself. An error in the infrastructure could lead to the entire system becoming compromised or could result in an outage rendering all dependent systems unavailable.

How can we introduce no bugs, and maintain system flexibility? How can we take responsibility for it? The answer lies in testing.

In the case of infrastructure code, we want to verify that changes made for one platform don’t cause unexpected side-effects on other platforms. The more we test, the more confident we are.

We must be committed to regular refactoring, regular small improvements, across the team.
As infrastructure developers, if we’re afraid to make changes to our code that’s a big red flag
test harness to protect them and catch the breaks.


## The Philosophy of Test-Driven Infrastructure

* The tools and approaches which make up the infrastructure testing ecosystem have evolved significantly
* Area with a high rate of changes and few established best practices


### Underpinning philosophy

1. Infrastructure can and should be treated as code
2. Infrastructure developers should adhere to the same principles of professionalism as other software developers

- While there are a number of implications following from those assumptions, the primary concern is that all infrastructure code must be thoroughly tested. 
- The most effective way of developing infrastructure as code is test-fist approach.

### What is Infrastructure as Code?

> When deploying and administering large infrastructures, it is still common to think in terms of individual machines rather than view an entire infrastructure as a combined whole. This standard practice creates many problems, including labor-intensive administration, high cost of ownership, and limited generally-available knowledge or code usable for administering large infrastructures.

> In today’s computer industry, we still typically install and maintain computers the way the automotive industry built cars in the early 1900s. An individual craftsman manually manipulates a machine into being, and manually maintains it afterwards.
  The automotive industry discovered first mass production, then mass customisation using standard tooling. The systems administration industry has a long way to go, but is getting there.

### The origin of infrastructure as code
* Modeling infrastructure with code and then design, implement, and deploy our web application infrastructure with software best practices. We work with this code
using the same tools as we would with any other modern software project. The code that models, builds and manages the infrastructure is committed into source code
management alongside the application code.
* thinking about infrastructure as redeployable from a code base, in which we are using the same kinds of software development methodologies that have developed over the last 20 years

### The journey to value on Infrastructure as Code

1. Repeatability 

   Because we’re building systems in a high-level programming language and committing our code, we start to become more confident that our systems are ordered and repeatable. With the same inputs, the same code should produce the same outputs. This means we can now be confident (and ensure on a regular basis) that what we believe will recreate our environment really will do that.

2. Automation

   By utilizing already mature tools for deploying applications, written in modern programming languages, the very act of abstracting out infrastructures brings us the benefits of automation

3. Agility

   The discipline of source code management and version control means we have the ability to roll forwards or backwards to a known state. Because we can redeploy entire systems, we are able to drastically reconfigure or change topology with ease, responding to defects and business-driven changes. In the event of a problem, we can go to the commit logs and identify what changed and who changed it. This is made all the easier because our infrastructure code is just text, and as such can be examined and compared using standard file comparison tools, such as diff.

4. Scalability

   Repeatability and automation make it possible to grow our server fleet easily, especially when combined with the kind of rapid hardware/services provisioning that the cloud provides. Modular code design and reuse manages complexity as our applications grow in features, type, and quantity

5. Reassurance

   Whilst all of the benefits bring reassurance in their way, in particular, the fact that the architecture and design of our infrastructure is modelled - and not merely implemented - in code means that we may reasonably use the source code as documentation and see at a glance how the systems work. This knowledge repository mitigates the risk of only a single sysadmin or architect holding the full understanding of how the system hangs together. That is risky - this person is now able to hold the organization to ransom, and should they leave or become ill, the company is endangered.

6. Disaster Recovery

   In the event of a catastrophic event that wipes out the production systems, if our entire infrastructure has been broken down into modular components and described as code, recovery is as simple as provisioning new compute power, restoring from backup, and deploying the infrastructure and application code. What may have been a business-ending event in the old paradigm of custom-built, partially-automated infrastructure becomes a manageable outage with procedures we can test in advance.

#### THE PRINCIPLES OF INFRASTRUCTURE AS CODE 

Core principles to put in practice that describe the characteristic of reusable primitive components look like (Adam Jacob, co-founder of Opscode), to build infrastructure in a predictable and reliable way.

Two high-level steps:

1. Break the infrastructure down into independent, reusable, network-accessible services.
2. Integrate these services in such a way as to produce the functionality our infrastructure requires

*10 Principles:*

1. Modularity

   Our services should be small and simple - think at the level of the simplest freestanding, useful component.
   
2. Cooperation

   Our design should discourage overlap of services and should encourage other people and services to use our service in a way which fosters continuous improvement of our design and implementation.

3. Composability

   Our services should be like building blocks - we should be able to build complete, complex systems by integrating them.

4. Extensibility

   Our services should be easy to modify, enhance, and improve in response to new demands

5. Flexibility

   We should build our services using tools that provide unlimited power to ensure we have the (theoretical) ability to solve even the most complicated of problems.

6. Repeatability

   With the same inputs, our services should produce the same results in the same way every time.

7. Declaration

   We should specify our services in terms of what we want to do, not how we want to do it.

8. Abstraction

   We should not worry about the details of the implementation, and think at the level of the component and its function.

9. Idempotence

   Our services should only be configured when required; action should only be taken once.

10. Convergence

   Our services should take responsibility for their own state being in line with policy; over time, the overall system will tend to correctness.
   

The key enabler in this context is a powerful, declarative configuration management system that enables engineers (I like the term infrastructure developer) to write executable code that both describes the shape, behavior and characteristics of an infrastructure that they are designing.


### RISKS OF INFRASTRUCTURE AS CODE: What to avoid

* Sprawling masses of infrastructure code.Duplication, contradiction, and a lack of clear understanding of what it all does.
* Fear of change: a sense that we dare not meddle with the manifests or recipes because we’re not entirely certain how the system will behave.
* Bespoke software that started off well-engineered and thoroughly tested, but is now littered with TODOs, FIXMEs, and quick hacks.
*nDespite the lofty goal of capturing the expertise required to understand an infrastructure in the code itself, a sense that the organization would be in trouble if one or two key people were to leave.
* War stories of times when a seemingly trivial change in one corner   of the system had catastrophic side-effects elsewhere.

There are six areas where we need to focus our attention to ensure that our infrastructure code is developed with the same degree of thoroughness and professionalism as our application code:

* Design
  
  Our infrastructure code should seek to be simple and iterative, and we should avoid feature creep.
  
* Collective Ownership
  All members of the team should be involved in the design and writing of infrastructure code and, wherever possible, code should be written in pairs.

* Code Review
  
  The team should be set up in such a way as to both pair frequently and to see regular notifications of when changes are made.
  
* Code Standards

  Infrastructure code should follow the same internal and external development community standards; where standards and patterns have grown up around the configuration management framework, these should be adhered to.
  
* Refactoring

  This should happen at the point of need as part of the iterative and collaborative process of developing infrastructure code; however, it’s difficult to do this without a safety net in the form of thorough test coverage of one’s code.
  
* Testing

  Systems should be in place to ensure that one’s code produces the environment needed and to ensure that our changes have not caused side effects that alter other aspects of the infrastructure.
  
Good practices in all those areas is a natural by-product of bringing development best practices to infrastructure code - in particular by embracing the idea of test-first programming.

### TESTING
The trouble is, testing takes time. Lots of testing takes lots of time. In the world of infrastructure code, testing takes even more time because sometimes the feedback loops are significantly longer than traditional test scenarios. This makes it imperative that we automate our testing. Testing, especially of complicated, disparate systems, is also difficult. Writing good tests for code is hard to do. That makes it imperative for us to write code that is easy to test. The best way to do that is to write the tests first. We’ll discuss this in more depth later, but the essential and applicable takeaway is that consistent, automated, and quality testing of infrastructure code is mandatory for the Devops professional.

Testing our infrastructure code, thoroughly and repeatably, is non-negotiable, and is an essential component of the infrastructure developer’s work.