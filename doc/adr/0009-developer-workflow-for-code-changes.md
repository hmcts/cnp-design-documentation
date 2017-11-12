# 9. Developer Workflow for Code Changes

Date: 2017-11-10

## Status

Proposed

## Context

Adoption of the CNP brings with the ability to change and improve the developer workflow when making application code changes.  As per [5. Application Delivery Pipelines](doc/adr/0005-pipeline-design.md) the pipeline is opinionated and promotes the practice of Continuous Delivery.  This proposal goes into the detail of the expected workflow of a developer making an application change in the context of CNP using Continuous Delivery.

### What is Developer Workflow
Developer workflow is the process developers use to create application changes and prepare them for release in a reliable manner.  This includes the branching strategies, code review, and testing, all with a heavy reliance on the pipeline.

### Trunk based development using short lived feature branches
Trunk based development is an enabler for Continuous Delivery via Continuous Integration.  Changes are frequently made to the master branch (trunk) whilst ensuring the master branch is always in a releasable state.  The releasable state is supported by a wide range of automated testing and development strategies for managing change such as feature toggles or branch by abstraction.

A short lived feature branch is a branch created with a specific and small change as its purpose.  The branch should live no more than a couple of days, preferably under a single day, before it is merged into master and deleted.  The merging takes place via a Pull Request in the [Github Flow](https://guides.github.com/introduction/flow/) (not to be confused with the more onerous [GitFlow](http://endoflineblog.com/gitflow-considered-harmful)).  There should be no more than one short lived feature branch per developer and are not shared.  This is easily achievable when change is small, focussed and frequently merged into master.

![Diagram of a short lived feature branch with commits, a PR, comments and a merge to master](../../img/trunk_pr.png)
<br />
_Image from [TrunkBasedDevelopment.com](https://trunkbaseddevelopment.com/short-lived-feature-branches/)_



## Decision

Decision here...

## Consequences

Consequences here...

## Recommended Reading
* [TrunkBasedDevelopment.com](http://trunkbaseddevelopment.com)
* GDS Blog post: [Easing the process of pull request reviews](https://gdstechnology.blog.gov.uk/2016/09/30/easing-the-process-of-pull-request-reviews/)
* [Organisation Pattern: Trunk based Development](https://www.continuousdeliveryconsulting.com/blog/organisation-pattern-trunk-based-development/)
