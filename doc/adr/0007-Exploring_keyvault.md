# 4. Setting up Vault as a Certification Authority (CA)
Date: 2017-10-12

## Status 
Proposal

## Context 

We wanted to explore Azure's KeyVault capabilities to serve as a CA for services deployed on the strategic platform at HMCTS, that's to issue the certificates services may need for authentication purposes and compare to our previous findings when . 

## Decision 

The first difference that shows up when comparing Azure's KeyVault (KV) with Hashicorp's Vault (as per ADR 0004) is that the Azure offering is a self hosted service provided by Microsoft whereas Hashicorp's vault would have been an IaaS based solution hosted inside a private VNET. This is an important difference since currently the only way to interact with KV is by connecting to a public endpoint.

Although KV makes its REST endpoints public (SSL encrypted) it is important to highlight that the only way to interact with this service is by first authenticating against Azure's Active Directory service which, in combination with KV's access policy capabilities, provides a fairly granular control with regards to which information and which KV's can be accessed by an app/service_principal.

The KV service supports a couple of methods to create certificates including self-signed as described [here](https://docs.microsoft.com/en-us/rest/api/keyvault/create-a-certificate). The KV REST API provides support for an extensive number of Certificate related operations including the most basic use cases HMCTS might need to cover in CNP currently. The following is a list of the certificate related operations:

#### Certificate operations

The Azure Key Vault REST API supports the following operations on certificates.

* Create a certificate
* Import a certificate
* List versions of a certificate
* List certificates
* Get a certificate
* Delete a certificate
* Update a certificate
* Merge a certificate

#### Certificate management operations

These REST operations are for the management of certificate operations associated with a Key Vault certificate.

* Delete certificate operation
* Get certificate operation
* Update certificate operation

#### Certificate policy operations

The following operations are available on a certificate policy:

* Get a certificate policy
* Update a certificate policy

#### Soft-delete operations

The soft-delete feature supports these operations for deleted certificates:

* Get deleted certificate
* Get deleted certificates
* Purge deleted certificate
* Recover deleted certificate

#### Certificate Issuers

You can do the following with certificate issuers in a key vault:

* Set a certificate issuer
* Get a certificate issuer
* Update a certificate issuer
* Delete a certificate issuer
* Get certificate issuers

#### Certificate Contacts

You can do the following with certificate contacts:

* Get certificate contacts
* Set certificate contacts
* Delete certificate contacts

## Consequences

Although it is not currently clear how we could leverage KV as an Intermediate CA we believe the extensive number of operations that can be controlled via its REST API provide us with enough flexibility to accommodate the webapp + certs use cases currently devised for CNP.

It is also important to note that although we are avoiding the complexities of hosting a similar service on IaaS (i.e. hashicorp's Vault) we'll have to, in the case of KV, design and implement the details of a suitable authentication workflow/framework for webapps to be deployed on CNP i.e. describing which permissions must be enabled at deployment time so that apps can successfully retrieve authentication codes from Active Directory in order to create and retrieve certificates from KV via its REST API. Such workflow/framework will be covered in a separate ADR.

For more information please check the following resources:
https://docs.microsoft.com/en-us/rest/api/keyvault/certificate-scenarios
https://blogs.technet.microsoft.com/kv/2016/09/26/manage-certificates-via-azure-key-vault/
https://docs.microsoft.com/en-us/rest/api/
