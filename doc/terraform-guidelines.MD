# Terraform Guidelines



## What is a module, what is a project?
[Terraform Modules](https://www.terraform.io/intro/getting-started/modules.html) are self contained packages of configuration
A Terraform module provides a reusable service composed of resources needed to provide an infrastructure building block.

A Terraform project builds the infrastructure for use. A Terraform project is composed of modules. 
A Terraform project is an application or product specific infrastructure.

A Terraform project’s outputs can and should be used in other projects by referring to the outputs in the state.

![Pipeline Flow](../img/pipelineflow.png)

### Do
- Extract out a module from a project, if you see reusable functionality. 
- Provide an opinionated Terraform module that encapsulates best practice. 
- Provide sane and secure default variables where possible.

### Don’t
- Create a module with only one provider primitive. The exception to this is encapsulating an ARM template in a module.
-  Expose too many configuration variables, as this can lead to too many variations on how the module can be used. 

## TerraServices

A TerraService is an opinionated terraform module that provides an architectural building block. A terra service may use other Terraform modules. 

A TerraService will have a CI pipeline. A TerraService will have unit, integration and compliance tests. 


## TerraServices as building blocks

Use TerraServices to build application and product specific infrastructure. 

## Publishing and versioning TerraServices

Use [Semantic versioning](http://semver.org/) to publish a TerraService in the CI pipeline automatically when tests have passed. Tag a release, and point the *latest* tag to the latest release.

Increment major version when there is a major new feature or a major breaking change.

Increment minor versions for minor feature changes. 
Increment the patch version on every build.


## Storing State

Terraform Projects store state in a backend. 
State will be stored with the following structure

```code
https://<statestorebackend>/<project>/<env>/terraform.tfstate
```

For example

```code
bootstrap/dev/terraform.tfstate
bootstrap/prod/terraform.tfstate

probate/dev/terraform.tfstate
probate/test/terraform.tfstate
```

```code
env : environment to create/update infrastructure
project : name of the infrastructure to build

```

Set the default env in scripts to **local**. Use a CI server to pass the env for other environments. This will ensure that non-dev environments are not overwritten accidentally.
 
## Project structure


```text
project-name\
		variables.tf
		state.tf
		main.tf
		frontend-cluster.tf
		validation-service-cluster.tf
		output.tf				
```

Required tf files:

- **variables.tf** : variables for the project. Mandatory variables are listed below
    
    - env - environment to apply the changes to. Resources created within a project should be tagged and named with the environment 
    - azure authentication details (TBD)  

-  **main.tf** - main entry point with the provider definition.
-  **output.tf** - outputs from the project.
-  Infrastructure component specific tf files should contain the logically related resources to build a component. Avoid scattering resources needed for one component across several files.
-  Organise files by function not by technical details.
         


## TerraService/Module structure

```text
module-<modulename>\
	variables.tf 
	main.tf
	output.tf
	application-service.tf
	files\
		arm-template.json
	tests\
		fixture\
			main.tf 
```

## Roles and responsibilities 

Application and product teams own Terraform projects and will compose their infrastructure using tested and published TerraServices. Teams may have their own modules, but this should be the exception than the norm.

TerraServices will be maintained and guided by a Platform engineering team. The Platform engineering team will use an OpenSource style maintainer model and accept contributions. 
