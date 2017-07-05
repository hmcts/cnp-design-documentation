# Naming Conventions

## Glossary of Parameters 

#### env  
Instantiation of  infrastructure and code.  
		Examples: dev, prod, test, toms-test-env, demo-for-alpha

#### product
The name of the product stack being built. A product can contain multiple applications

#### application
A component which provides a service. This is also a deployable component. One or more applications make up a product

## Naming of Azure Resources

1.  Use descriptive names
2.  Avoid using abbreviations
3.  Do not include the type of the resource in the name. For example, avoid using *rhubarb-dev-resourcegroup*

## Resource groups 
	1. Applications:            

```  
    <product>-<application>-<env>
    rhubarb-frontend-dev
    rhubarb-admin-frontend-dev
    rhubarb-image-service-prod
    probate-validation-service-prod
```       



