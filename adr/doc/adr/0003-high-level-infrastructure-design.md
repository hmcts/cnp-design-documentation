# 3. High Level Infrastructure Design

Date: 2017-07-24

## Status

Proposed

## Context

A just enough high level infrastructure design is needed to drive how we build the strategic infrastructure.

The key questions are;
- How do Application Service Environments (ASEs) fit in the infrastructure?
- What are the IP ranges?
-  What’s the IP allocation policy?
-  How do we handle internal DNS queries?
-  How do the components connect to each other on the network?


## Decision

[High Level Design](https://www.lucidchart.com/documents/edit/69b50fa0-77e7-43b5-92ed-1933abb10a80)

[](high-level-infra-design.png)

### Production Applications Infrastructure VNet (applications-prod)
Production services will run inside a dedicated Virtual Network (VNet). 

### Management and Tooling Infrastructure VNet (management-prod)
Management and Tooling will be hosted inside a dedicated VNet. This hosts the CI/CD Tooling and components which support  managing and deploying applications. 
 
### Non-Production Applications Infrastructure VNet (applications-non-prod)
Dev, Test (QA) and Load test versions the services will run inside this VNet. The same infrastructure as code (IaC) will drive both prod and non-prod infrastructure.

### Azure Traffic Manager 
[Azure Traffic Manager](https://azure.microsoft.com/en-gb/services/traffic-manager/) will be used to host the public DNS entries for each Citizen facing frontend. 

Traffic Manager supports configurable routing, which will support [blue/green deployments](https://martinfowler.com/bliki/BlueGreenDeployment.html).

### Azure Application Gateway + Web Application Firewall
[Azure Application Gateway](https://docs.microsoft.com/en-us/azure/application-gateway/application-gateway-introduction)

The Azure Application Gateway 

### Azure Application Service Environments with Internal Load balancer
### Private DNS 
## Consequences

Consequences here...
