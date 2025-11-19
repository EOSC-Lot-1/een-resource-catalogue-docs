



# Resource Catalogue Documentation for Eosc EU node
[![License](https://img.shields.io/badge/license-Apache%202.0-blue.svg)](LICENSE)
[![Contributor Covenant](https://img.shields.io/badge/Contributor%20Covenant-2.1-4baaaa.svg)](CODE_OF_CONDUCT.md)
<a href="https://confluence.egi.eu/display/EOSCBeyond/Software+and+Services+Quality+Assurance+%28SQA%29+guidelines">
<img src="https://img.shields.io/badge/SQAaaS-Bronze-CD7F32"/></a>

---

**Work in Progress:** This section is a work in progress and is subject to modification.

## Description
**ΕΕΝ Resource Catalogue Documentation** provides a comprehensive guide to the API endpoints, models, and core components 
of the **[Resource Catalogue](https://github.com/EOSC-Lot-1/resource-catalogue)** project, offering detailed 
descriptions of each controller, along with their associated functionalities and endpoints. It includes an overview of 
its data models and a detailed list of vocabularies used within the platform. Additionally, the documentation provides 
schemas for validating data of the various classes, ensuring consistency and reliability across the system.  

_Resource Catalogue version: v5.0.0+u123_

---

## Table of Contents
1. [Controllers](#controllers)  
    i. [Datasource Controller](#datasource-controller)  
    ii. [Interoperability Record Controller](#interoperability-record-controller)  
    iii. [Provider Controller](#provider-controller)  
    iv. [Service Controller](#service-controller)  
    v. [Training Resource Controller](#training-resource-controller)  
    vi. [Tool Controller](#tool-controller)  
    vii. [Resource Revision Controller](#resource-revision-controller)  
    viii. [Vocabulary Controller](#vocabulary-controller)  
2. [Model](#model)  
    i. [Datasource](#datasource-bundle)  
    ii. [Interoperability Record](#interoperability-record-bundle)  
    iii. [Provider](#provider-bundle)  
    iv. [Service](#service-bundle)  
    v. [Training Resource](#training-resource-bundle)  
    vi. [Tool](#tool-bundle)  
    vi. [Resource Revision](#resource-revision-bundle)  
    vii. [Vocabulary](#vocabulary)  
    viii. [Miscellaneous](#miscellaneous)  
3. [List of Vocabularies](#list-of-vocabularies)

---

## Controllers

Note: All operations handle resources as Bundle objects. \
For example, GET and POST operations use a ServiceBundle containing the Service resource.

- ### Datasource Controller
  
  #### Operations for Datasources
  
  - DELETE
    - Deletes the Datasource with the given id (for non-published resources).
      ```diff
      /datasources/{prefix}/{suffix}
      Params:
        prefix: String [required]
        suffix: String [required]
      ```
      
  - GET
    - Returns the DatasourceBundle with the given id.
      ```diff
      /datasources/{prefix}/{suffix}
      Params:
        prefix: String [required]
        suffix: String [required]
      ```
    - Filter a list of DatasourceBundles based on a set of filters.
      ```diff
      /datasources
      Params:
        active: boolean [optional]
        keyword : String (Keyword to refine the search) [optional]
        from : String (Starting index in the result set, default 0) [optional]
        quantity: String (Quantity to be fetched, default 10) [optional]
        order: String (Order of results - asc/desc, default asc) [optional]
        sort: String (Field to use for ordering) [optional]
      ```
      Example: ```resource-catalogue-url/datasources?active=true&keyword=test1&quantity=50```

  - POST
    - Creates a new Datasource.
      ```diff
      /datasources
      Body:
        DatasourceBundle JSON [required]
      ```
        
  - PUT
    - Updates a specific Datasource.
      ```diff
      /datasources
      Body:
        DatasourceBundle JSON [required]
      ```
        
- ### Interoperability Record Controller
  
  #### Operations for Interoperability Records
  
  - DELETE
    - Deletes the Interoperability Record with the given id (for non-published resources).
      ```diff
      /interoperability-records/{prefix}/{suffix}
      Params:
        prefix: String [required]
        suffix: String [required]
      ```
      
  - GET
    - Returns the Interoperability Record with the given id.
      ```diff
      /interoperability-records/{prefix}/{suffix}
      Params:
        prefix: String [required]
        suffix: String [required]
      ```
      
    - Get all Interoperability Records.
      ```diff
      /interoperability-records
      Params:
        keyword : String (Keyword to refine the search) [optional]
        from : String (Starting index in the result set, default 0) [optional]
        quantity: String (Quantity to be fetched, default 10) [optional]
        order: String (Order of results - asc/desc, default asc) [optional]
        sort: String (Field to use for ordering) [optional]
      ```
      Example: ```resource-catalogue-url/interoperability-records?active=true&keyword=test1&quantity=50```

  - POST
    - Creates a new Interoperability Record.
      ```diff
      /interoperability-records
      Body:
        Interoperability Record JSON [required]
      ```
    - Validates the Interoperability Record without actually changing the repository.
      ```diff
      /interoperability-records/validate
      Body:
        Interoperability Record JSON [required]
      ```
      
  - PUT
    - Updates the Interoperability Record with the given id.
      ```diff
      /interoperability-records
      Body:
        Interoperability Record JSON [required]
      ```
        
- ### Provider Controller
  
  #### Operations for Providers
  
  - DELETE
    - Deletes a Provider with the given id.
      ```diff
      /providers/{prefix}/{suffix}
      Params:
        prefix: String [required]
        suffix: String [required]
      ```    
      
  - GET
    - Returns a Provider with the given id.
      ```diff
      /providers/{prefix}/{suffix}
      Params:
        prefix: String [required]
        suffix: String [required]
      ```       
    - Filter a list of Providers based on a set of filters.
      ```diff
      /providers
      Params:
        active: boolean [optional]
        query : String (Keyword to refine the search) [optional]
        from : String (Starting index in the result set, default 0) [optional]
        quantity: String (Quantity to be fetched, default 10) [optional]
        order: String (Order of results - asc/desc, default asc) [optional]
        sort: String (Field to use for ordering) [optional]

      Example: ```resource-catalogue-url/providers?active=true&keyword=test1&quantity=50```

  - POST
    - Create a new Provider.
      ```diff
      /providers
      Body:
        Provider JSON [required]
      ```
    - Validates a Provider without actually changing the repository.
      ```diff
      /providers/validate
      Body:
        Provider JSON [required]
      ```
      
  - PUT
    - Updates a Provider given its id.
      ```diff
      /providers
      Body:
        Provider JSON [required]
      ```
  
- ### Service Controller
  
  #### Operations for Services
  
  - DELETE
    - Deletes a Service given its id.
      ```diff
      /services/{prefix}/{suffix}
      Params:
        prefix: String [required]
        suffix: String [required]
      ```

  - GET
    - Returns a Service given its id.
      ```diff
        /services/{prefix}/{suffix}
        Params:
          prefix: String [required]
          suffix: String [required]
      ```
    - Returns a list of all Services based on a set of filters.
      ```diff
        /services
        Params:
          active: boolean [optional]
          keyword : String (Keyword to refine the search) [optional]
          from : String (Starting index in the result set, default 0) [optional]
          quantity: String (Quantity to be fetched, default 10) [optional]
          order: String (Order of results - asc/desc, default asc) [optional]
          sort: String (Field to use for ordering) [optional]
      ```
      
      Example: ```resource-catalogue-url/services?active=true&keyword=test1&quantity=50```

  - POST
    - Creates a new Service.
      ```diff
        /services
        Body:
          Service JSON [required]
    - Validates a Service without actually changing the repository.
      ```diff
      /services/validate
      Body:
        Service JSON [required]
  - PUT
    - Updates a specific Service.
      ```diff
      /services
      Body:
        Service JSON [required]
      ```

- ### Training Resource Controller
  
  #### Operations for Training Resources
  
  - DELETE
    - Deletes a Training Resource given its id.
      ```diff
      /training-resources/{prefix}/{suffix}
      Params:
        prefix: String [required]
        suffix: String [required]
      ```
      
  - GET
    - Returns a Training Resource given its id.
      ```diff
        /training-resources/{prefix}/{suffix}
        Params:
          prefix: String [required]
          suffix: String [required]
      ```
    - Returns a list of all Training Resources based on a set of filters .
      ```diff
        /training-resources
        Params:
          active: boolean [optional]
          keyword : String (Keyword to refine the search) [optional]
          from : String (Starting index in the result set, default 0) [optional]
          quantity: String (Quantity to be fetched, default 10) [optional]
          order: String (Order of results - asc/desc, default asc) [optional]
          sort: String (Field to use for ordering) [optional]
      ```
      
      Example: ```resource-catalogue-url/training-resources?active=true&keyword=test1&quantity=50```

  - POST
    - Creates a new Training Resource.
      ```diff
        /training-resources
        Body:
          Training Resource JSON [required]
    - Validates a Training Resource without actually changing the repository.
      ```diff
      /training-resources/validate
      Body:
        Training Resource JSON [required]
  - PUT
    - Updates a specific Training Resource.
      ```diff
      /training-resources
      Params:
        comment: String
      Body:
        Training Resource JSON [required]
      ```

- ### Tool Controller
  
  #### Operations for Tools
  
  - DELETE
    - Deletes a Tool given its id.
      ```diff
      /tools/{prefix}/{suffix}
      Params:
        prefix: String [required]
        suffix: String [required]
      ```
      
  - GET
    - Returns a Tool given its id.
      ```diff
        /tools/{prefix}/{suffix}
        Params:
          prefix: String [required]
          suffix: String [required]
      ```
    - Returns a list of all Tools in the Portal based on a set of filters.
      ```diff
        /tools
        Params:
          active: boolean [optional]
          keyword : String (Keyword to refine the search) [optional]
          from : String (Starting index in the result set, default 0) [optional]
          quantity: String (Quantity to be fetched, default 10) [optional]
          order: String (Order of results - asc/desc, default asc) [optional]
          sort: String (Field to use for ordering) [optional]
      ```
      
      Example: ```resource-catalogue-url/tools?active=true&keyword=test1&quantity=50```

  - POST
    - Creates a new Tool.
      ```diff
        /tools
        Body:
          Tool JSON [required]
    - Validates a Tool without actually changing the repository.
      ```diff
      /tools/validate
      Body:
        Tool JSON [required]
  - PUT
    - Updates a specific Tool.
      ```diff
      /tools
      Params:
        comment: String
      Body:
        Tool JSON [required]
      ```
      
- ### Resource Revision Controller
  
  #### Operations for Resource Revisions
  
  - DELETE
    - Deletes a Resource Revision given its id.
      ```diff
      /resource-revisions/{prefix}/{suffix}
      Params:
        prefix: String [required]
        suffix: String [required]
      ```
      
  - GET
    - Returns a Resource Revision given its id.
      ```diff
        /resource-revisions/{prefix}/{suffix}
        Params:
          prefix: String [required]
          suffix: String [required]
      ```
    - Returns a list of all Resource Revisions in the Catalogue based on a set of filters.
      ```diff
        /resource-revisions
        Params:
          active: boolean [optional]
          keyword : String (Keyword to refine the search) [optional]
          from : String (Starting index in the result set, default 0) [optional]
          quantity: String (Quantity to be fetched, default 10) [optional]
          order: String (Order of results - asc/desc, default asc) [optional]
          sort: String (Field to use for ordering) [optional]
      ```
      
      Example: ```resource-catalogue-url/resource-revisions?active=true&keyword=test1&quantity=50```

  - POST
    - Creates a new Resource Revision.
      ```diff
        /resource-revisions
        Body:
          Resource Revision JSON [required]
    - Validates a Resource Revision without actually changing the repository.
      ```diff
      /resource-revisions/validate
      Body:
        Resource Revision JSON [required]
  - PUT
    - Updates a specific Resource Revision.
      ```diff
      /resource-revisions
      Params:
        comment: String
      Body:
        Resource Revision JSON [required]
      ```
     
- ### Vocabulary Controller
  
  #### Get information about Vocabularies
  
  - GET
    - Get all Vocabularies grouped by Type:
      ```diff
      /vocabulary/byType
      ```
    - Get all Vocabularies of a specific Type:
      ```diff
      /vocabulary/byType/{type}
      Params:
        type: Vocabulary Type [required]
      ```
    - Get a list of EU Countries:
      ```diff
      /vocabulary/countries/EU
      ```
    - Get a list of WW Countries:
      ```diff
      /vocabulary/countries/WW
      ```
    - Get a specific Vocabulary given its ID:
      ```diff
      /vocabulary/{id}
      Params:[required](required)
      ```

---

## Model




### Datasource Bundle
| Field                  | Type           | Required | Public | Description                                                 |
|------------------------|----------------|----------|--------|-------------------------------------------------------------|
| `id`                   | `String`       | auto-gen | Yes    | Unique identifier for the resource.                        |
| `active`               | `Boolean`      | No       | No     | Indicates whether the resource is active.                  |
| `suspended`            | `Boolean`      | No       | No     | Indicates whether the resource is suspended.               |
| `draft`                | `Boolean`      | No       | No     | Indicates whether the resource is in draft state.          |
| `legacy`               | `Boolean`      | No       | No     | Indicates whether the resource is from EOSC Future.        |
| `status`               | `String`       | No       | No     | Provides information about the resource status ([RESOURCE_STATUS](#resource_status-)). |
| `resourceOrganisationGroupID`               | `String`       | No       | No     |ID of the provider's organization
| `nodeId`               | `String`       | No       | Yes     |ID of the node the resource belongs
| `metadata`             | `Metadata`     | No       | Yes    | Additional metadata for the resource.                      |
| `loggingInfo`          | `LoggingInfo`  | No       | No     | Contains details about resource updates.                   |
| `latestOnboardingInfo` | `LoggingInfo`  | No       | No     | Details of the latest onboarding action.                   |
| `softwareRepository`   | `Boolean`      | No       | Yes     | Indicates whether the datasource is a software repository. |
| `originalOpenAIREId`   | `String`      | No       | Yes     | Original OpenAIRE ID, if datasource already exists in the OpenAIRE Catalogue. |
| `datasourceType`   | `String`      | No       | Yes     | Type of the datasource ([DATASOURCE_TYPE](#datasource_type-)). |
| `oaiPmhInfo`           | `OaiPmhInfo`   | No      | Yes    | Metadata related to oai-pmh.                           |
| `offboardRequestPending`                | `Boolean`      | No       | No     | Indicates whether the resource has a pending offboard request.          |
| `acknowledgement`           | `Acknowledgement`   | No      | No    | Acknowledgement for different statements.                           |
| `datasource`           | `Datasource`   | Yes      | Yes    | Metadata of the actual resource.                           |


### Nested Objects


### Datasource
| Field                  | Type           | Required | Public | Description                                                 |
|------------------------|----------------|----------|--------|-------------------------------------------------------------|
| `id`                   | `String`       | auto-gen | Yes    | Unique identifier for the datasource.                       |
| `serviceId`            | `String`       | No      | Yes    | Identifier of the associated service.                       |
| `submissionPolicyURL`  | `URL`          | No       | Yes    | URL of the submission policy.                               |
| `preservationPolicyURL`| `URL`          | No       | Yes    | URL of the preservation policy.                             |
| `versionControl`       | `Boolean`      | No       | Yes    | Indicates if version control is used.                       |
| `persistentIdentitySystems` | `List<PersistentIdentitySystem>` | No | Yes | List of persistent identity systems associated with the datasource. |
| `jurisdiction`         | `String`       | Yes      | Yes    | Jurisdiction where the datasource operates ([DS_JURISDICTION](#ds_jurisdiction-)).                 |
| `datasourceClassification` | `String`   | Yes      | Yes    | Classification of the datasource ([DS_CLASSIFICATION](#ds_classification-)).                           |
| `researchEntityTypes`  | `List<String>` | No       | Yes    | List of research entity types related to the datasource  ([DS_RESEARCH_ENTITY_TYPE](#ds_research_entity_type-)).    |
| `thematic`             | `Boolean`      | Yes      | Yes    | Indicates if the datasource is thematic.                    |
| `researchProductLicensings` | `List<ResearchProductLicensing>` | No | Yes | List of research product licensing details.                 |
| `researchProductAccessPolicies` | `List<String>` | No | Yes | List of research product access policies ([DS_COAR_ACCESS_RIGHTS_1_0](#ds_coar_access_rights_1_0-)).                   |
| `researchProductMetadataLicensing` | `ResearchProductMetadataLicensing` | No | Yes | Metadata licensing details for research products.           |
| `researchProductMetadataAccessPolicies` | `List<String>` | No | Yes | List of research product metadata access policies ([DS_COAR_ACCESS_RIGHTS_1_0](#ds_coar_access_rights_1_0-)).          |
| `harvestable`          | `Boolean`      | No       | Yes    | Indicates if the datasource is harvestable.                 |


##### OAIPMHInfo

| Field                  | Type           | Required | Public | Description                                                 |
|------------------------|----------------|----------|--------|-------------------------------------------------------------|
| `protocol`                   | `String`       | No | Yes    | Protocol used for OAI-PMH ([DS_PROTOCOL](#ds_protocol-)).               |
| `baseUrl`                   | `String`       | Yes | Yes    | Url of OAI-PMH endpoint.                       |
| `sets`                   | `List<String>`       | No | Yes    | OAI-PMH sets.                       |
| `format`                   | `String`       | No | Yes    | OAI format ([DS_FORMAT](#ds_format-)).                       |
| `compatibility`                   | `String`       | No | Yes    | Datasource oai compatibility ([DS_COMPATIBILITY](#ds_compatibility-)).                       |
| `openAIRECompliance`            | `String`       | No | Yes    | Indicates if resource is compliant with openAIRE specifications.                   |
| `repositoryIdentifier`           | `AlternativeIdentifier`       | No | Yes    | Identifier for the repository.          
| `alternativeIdentifiers`                   | `List<AlternativeIdentifier>`       | No | Yes    | Alternative identifiers.                  |


##### PersistentIdentitySystem

| Field                  | Type           | Required | Public | Description                                                 |
|------------------------|----------------|----------|--------|-------------------------------------------------------------|
| `persistentIdentityEntityType`        | `String`         |Yes              | Yes      | Type of the persistent identity entity ([DS_RESEARCH_ENTITY_TYPE](#ds_research_entity_type-)).           |
| `persistentIdentityEntityTypeSchemes` | `List<String>`     |Yes            | Yes       | Schemes for the persistent identity entity types ([DS_PERSISTENT_IDENTITY_SCHEME](#ds_persistent_identity_scheme-)). |

##### ResearchProductLicensing

| Field                  | Type           | Required | Public | Description                                                 |
|------------------------|----------------|----------|--------|-------------------------------------------------------------|
| `researchProductLicenseName` | `String` | Yes   |Yes   | Name of the research product license. |
| `researchProductLicenseURL`  | `URL`    | Yes   |Yes | URL of the research product license.  |

##### ResearchProductMetadataLicensing

| Field                  | Type           | Required | Public | Description                                                 |
|------------------------|----------------|----------|--------|-------------------------------------------------------------|
| `researchProductMetadataLicenseName` | `String` | Yes | Yes     | Name of the research product metadata license. |
| `researchProductMetadataLicenseURL`  | `URL`    | Yes  |Yes    | URL of the research product metadata license.  |

##### Alternative Identifier

| Field                  | Type           | Required | Public | Description                                                 |
|------------------------|----------------|----------|--------|-------------------------------------------------------------|
| `type`        | `String`         |Yes              | Yes      | Type of the identifier.           |
| `value` | `String`     |Yes            | Yes       | Value of the identifier. |
### Example

```json
  
{
    "metadata": {
        "registeredBy": "system",
        "registeredAt": "1699050379221",
        "modifiedBy": "system",
        "modifiedAt": "1699050525681",
        "published": false
    },
    "active": true,
    "suspended": false,
    "draft": false,
    "legacy": false,
    "status": "pending",
    "originalOpenAIREId": "openaireId",
    "softwareRepository": false,
    "oaiPmhInfo": {
        "protocol": "ds_protocol-oai",
        "baseUrl": "https://example.com/oai/request",
        "sets": [
            "set1",
            "set2"
        ],
        "format": "ds_oai_formats-oai_datacite",
        "compatibility": "ds_oai_compatibility-not_compatible",
        "openAIRECompliance": false,
        "repositoryIdentifier": {
            "type": "type1",
            "value": "3540"
        }
    },
    "resourceOrganisationGroupID": "groupId",
    "nodeId": "nodeId",
    "id": "datasource_001",
    "datasource": {
        "id": "datasource_001",
        "serviceId": "service_001",
        "submissionPolicyURL": "https://example.com/submission-policy",
        "preservationPolicyURL": "https://example.com/preservation-policy",
        "versionControl": true,
        "persistentIdentitySystems": [
            {
                "persistentIdentityEntityType": "ds_research_entity_type-organizations",
                "persistentIdentityEntityTypeSchemes": [
                    "ds_persistent_identity_scheme-doi",
                    "ds_persistent_identity_scheme-handle"
                ]
            }
        ],
        "jurisdiction": "ds_jurisdiction-global",
        "datasourceClassification": "ds_classification-scientific_database",
        "researchEntityTypes": [
            "ds_research_entity_type-projects",
            "ds_research_entity_type-organizations"
        ],
        "thematic": true,
        "researchProductLicensings": [
            {
                "researchProductLicenseName": "License1",
                "researchProductLicenseURL": "https://example.com/license1"
            }
        ],
        "researchProductAccessPolicies": [
            "ds_coar_access_rights_1_0-open_access"
        ],
        "researchProductMetadataLicensing": {
            "researchProductMetadataLicenseName": "Metadata License1",
            "researchProductMetadataLicenseURL": "https://example.com/metadata-license1"
        },
        "researchProductMetadataAccessPolicies": [
            "ds_coar_access_rights_1_0-restricted_access",
            "ds_coar_access_rights_1_0-open_access"
        ],
        "harvestable": true
    }
}
```

### Interoperability Record Bundle
| Field                  | Type           | Required | Public | Description                                                 |
|------------------------|----------------|----------|--------|-------------------------------------------------------------|
| `id`                   | `String`       | auto-gen | Yes    | Unique identifier for the resource.                        |
| `active`               | `Boolean`      | No       | No     | Indicates whether the resource is active.                  |
| `suspended`            | `Boolean`      | No       | No     | Indicates whether the resource is suspended.               |
| `draft`                | `Boolean`      | No       | No     | Indicates whether the resource is in draft state.          |
| `legacy`               | `Boolean`      | No       | No     | Indicates whether the resource is from EOSC Future.        |
| `status`               | `String`       | No       | No     | Provides information about the resource status ([RESOURCE_STATUS](#resource_status-)). |
| `metadata`             | `Metadata`     | No       | Yes    | Additional metadata for the resource.       
| `resourceOrganisationGroupID`    | `String`       | No       | No     |ID of the provider's organization               |
| `offboardRequestPending`                | `Boolean`      | No       | No     | Indicates whether the resource has a pending offboard request.          |
| `loggingInfo`          | `LoggingInfo`  | No       | No     | Contains details about resource updates.                   |
| `latestOnboardingInfo` | `LoggingInfo`  | No       | No     | Details of the latest onboarding action.                      |
| `latestUpdateInfo` | `LoggingInfo`  | No       | No     | Details of the latest update action.                  |
| `acknowledgement`           | `Acknowledgement`   | No      | No    | Acknowledgement for different statements.                           |
| `interoperabilityRecord`           | `InteroperabilityRecord`   | Yes      | Yes    | Metadata of the actual resource.                           |


### Interoperability Record

| Field                    | Type                          | Required | Public | Description                                                                      |
|--------------------------|-------------------------------|----------| ------------|----------------------------------------------------------------------------------|
| `id`                     | `String`                      | auto-gen | Yes | Unique identifier for the interoperability record.                                     |
| `providerId`             | `String`                      | Yes    | Yes | Identifier of the provider associated with the record.                           |
| `identifierInfo`         | `IdentifierInfo`              | Yes    | Yes  | Information about the primary identifier of the record.                          |
| `creators`               | `List<Creator>`               | Yes    | Yes  | List of creators involved in the creation of the resource.                       |
| `title`                  | `String`                      | Yes    | Yes  | Title of the interoperability record.                                            |
| `publicationYear`        | `Integer`                     | Yes    | Yes  | Year of publication for the record.                                              |
| `resourceTypesInfo`      | `List<ResourceTypeInfo>`      | Yes   | Yes   | List of resource types associated with the record.                               |
| `created`                | `String`                      | No   | Yes    | Timestamp indicating when the record was created.                                |
| `updated`                | `String`                      | No   | Yes    | Timestamp indicating the last update to the record.                              |
| `relatedStandards`       | `List<RelatedStandard>`       | No   | Yes    | List of related standards connected to the interoperability record.              |
| `rights`                 | `List<Right>`                 | Yes   | Yes   | List of rights associated with the record.                                       |
| `description`            | `String`                      | Yes    | Yes  | Description of the interoperability record.                                      |
| `status`                 | `String`                      | Yes   | Yes   | Current status of the interoperability record ([IR_STATUS](#ir_status-)).                                   |
| `domain`                 | `String`                      | No    | Yes   | Domain to which the record pertains ([SCIENTIFIC_DOMAIN](#scientific_domain-)).                                             |
| `eoscGuidelineType`      | `String`                      | Yes   | Yes   | Type of EOSC (European Open Science Cloud) guideline associated with the record ([IR_EOSC_GUIDELINE_TYPE](#ir_eosc_guideline_type-)). |
| `eoscIntegrationOptions` | `List<String>`                | No     | Yes  | Options for integrating the record into EOSC.                                    |
| `alternativeIdentifiers` | `List<AlternativeIdentifier>` | No     | Yes  | Alternative identifiers for the record.                                          |

#### Nested Objects

##### IdentifierInfo

| Field            | Type     | Required | Description                                      |
|------------------|----------|----------|--------------------------------------------------|
| `identifier`     | `String` | Yes      | Main identifier for the interoperability record. |
| `identifierType` | `String` | Yes      | Type of the identifier, e.g., DOI, Handle ([IR_IDENTIFIER_TYPE](#ir_identifier_type-)).       |

##### Creator

| Field                    | Type                     | Required | Description                                     |
|--------------------------|--------------------------|----------|-------------------------------------------------|
| `creatorNameTypeInfo`    | `CreatorNameTypeInfo`    | Yes      | Information about the creator's name and type.  |
| `givenName`              | `String`                 | No       | Given name of the creator.                      |
| `familyName`             | `String`                 | No       | Family name of the creator.                     |
| `nameIdentifier`         | `String`                 | No       | Unique identifier for the creator, e.g., ORCID. |
| `creatorAffiliationInfo` | `CreatorAffiliationInfo` | No       | Affiliation details of the creator.             |

##### CreatorNameTypeInfo

| Field         | Type     | Required | Description                                   |
|---------------|----------|----------|-----------------------------------------------|
| `creatorName` | `String` | Yes      | Full name of the creator.                     |
| `nameType`    | `String` | Yes      | Type of name, e.g., personal, organizational ([IR_NAME_TYPE](#ir_name_type-)). |

##### CreatorAffiliationInfo

| Field                   | Type     | Description                             |
|-------------------------|----------|-----------------------------------------|
| `affiliation`           | `String` | Name of the affiliation of the creator. |
| `affiliationIdentifier` | `String` | Identifier for the affiliation, if any. |

##### ResourceTypeInfo

| Field                 | Type     | Required | Description                                         |
|-----------------------|----------|----------|-----------------------------------------------------|
| `resourceType`        | `String` | Yes      | Specific type of the resource, e.g., dataset, tool. |
| `resourceTypeGeneral` | `String` | Yes      | General category of the resource type ([IR_RESOURCE_TYPE_GENERAL](#ir_resource_type_general-)).              |

##### RelatedStandard

| Field                       | Type     | Description                          |
|-----------------------------|----------|--------------------------------------|
| `relatedStandardIdentifier` | `String` | Identifier for the related standard. |
| `relatedStandardURI`        | `URL`    | URI linking to the related standard. |

##### Right

| Field             | Type     | Required | Description                                    |
|-------------------|----------|----------|------------------------------------------------|
| `rightTitle`      | `String` | Yes      | Title of the right associated with the record. |
| `rightURI`        | `URL`    | Yes      | URI linking to the right.                      |
| `rightIdentifier` | `String` | Yes      | Identifier for the right.                      |

### Example

```json
{
    "metadata": {
        "registeredBy": "system",
        "registeredAt": "1686743648277",
        "modifiedBy": "system",
        "modifiedAt": "1699348557618",
        "published": false
    },
    "active": true,
    "suspended": false,
    "draft": false,
    "legacy": true,
    "status": "pending",
    "id": "interop_001",
    "interoperabilityRecord": {
        "id": "interop_001",
        "providerId": "provider_001",
        "identifierInfo": {
            "identifier": "10.1234/interop",
            "identifierType": "ir_identifier_type-doi"
        },
        "creators": [
            {
                "creatorNameTypeInfo": {
                    "creatorName": "John Smith",
                    "nameType": "Personal"
                },
                "givenName": "John",
                "familyName": "Smith",
                "nameIdentifier": "0000-0002-1825-0097",
                "creatorAffiliationInfo": {
                    "affiliation": "University of Example",
                    "affiliationIdentifier": "org_001"
                }
            }
        ],
        "title": "Interoperability Record Example",
        "publicationYear": 2024,
        "resourceTypesInfo": [
            {
                "resourceType": "Dataset",
                "resourceTypeGeneral": "Data"
            }
        ],
        "created": "2024-01-01T12:00:00Z",
        "updated": "2024-09-01T12:00:00Z",
        "relatedStandards": [
            {
                "relatedStandardIdentifier": "standard_001",
                "relatedStandardURI": "https://example.com/standard"
            }
        ],
        "rights": [
            {
                "rightTitle": "Open Access",
                "rightURI": "https://example.com/right",
                "rightIdentifier": "right_001"
            }
        ],
        "description": "This is a sample interoperability record description.",
        "status": "ir_status-on_hold",
        "domain": "scientific_domain-engineering_and_technology",
        "eoscGuidelineType": "ir_eosc_guideline_type-eosc_core_interoperability_guideline",
        "eoscIntegrationOptions": [
            "Integration A",
            "Integration B"
        ],
        "alternativeIdentifiers": [
            {
                "type": "Handle",
                "value": "hdl:20.500.12345"
            }
        ]
    }
}
```
### Provider Bundle
| Field                  | Type           | Required | Public | Description                                                 |
|------------------------|----------------|----------|--------|-------------------------------------------------------------|
| `id`                   | `String`       | auto-gen | Yes    | Unique identifier for the resource.                        |
| `active`               | `Boolean`      | No       | No     | Indicates whether the resource is active.                  |
| `suspended`            | `Boolean`      | No       | No     | Indicates whether the resource is suspended.               |
| `draft`                | `Boolean`      | No       | No     | Indicates whether the resource is in draft state.          |
| `legacy`               | `Boolean`      | No       | No     | Indicates whether the resource is from EOSC Future.        |
| `status`               | `String`       | No       | No     | Provides information about the resource status([RESOURCE_STATUS](#resource_status-)). |
| `metadata`             | `Metadata`     | No       | Yes    | Additional metadata for the resource.       
| `resourceOrganisationGroupID`    | `String`       | No       | No     |ID of the provider's organization               |
| `loggingInfo`          | `LoggingInfo`  | No       | No     | Contains details about resource updates.                   |
| `latestOnboardingInfo` | `LoggingInfo`  | No       | No     | Details of the latest onboarding action.                      |
| `latestUpdateInfo` | `LoggingInfo`  | No       | No     | Details of the latest update action.                  |
| `nodeInfo`           | `NodeInfo`   | No      | Yes    | Metadata of the actual resource.                           |
| `acknowledgement`           | `Acknowledgement`   | No      | No    | Acknowledgement for different statements.                           |
| `provider`           | `Provider`   | Yes      | Yes    | Metadata of the actual resource.                           |


### Provider

| Field                     | Type                       | Required |Public | Description                                                                                       |
|---------------------------|----------------------------|----------|----|-----------------------------------------------------------------------------------------------|
| `id`                      | `String`                      | auto-gen |Yes      | Unique identifier for the provider.                                                               |
| `abbreviation`            | `String`                      | Yes      | Yes      |Abbreviation of the provider's name.                                                              |
| `name`                    | `String`                      | Yes      | Yes      |Full name of the provider.                                                                        |
| `website`                 | `URL`                         | Yes      |Yes      | URL of the provider's website.                                                                    |
| `legalEntity`             | `boolean`                     | Yes      | Yes      |Indicates if the provider is a legal entity.                                                      |
| `legalStatus`             | `String`                      | No       | Yes      |Legal status of the provider([PROVIDER_LEGAL_STATUS](#provider_legal_status-)).                                                                     |
| `hostingLegalEntity`      | `String`                      | No       |Yes      | Hosting legal entity responsible for the provider ([PROVIDER_HOSTING_LEGAL_ENTITY](#provider_hosting_legal_entity-)).                                                |
| `alternativeIdentifiers`  | `List<AlternativeIdentifier>` | No       |Yes      | List of alternative identifiers for the provider.                                                 |
| `description`             | `String`                      | Yes      | Yes      |Description of the provider.                                                                      |
| `logo`                    | `URL`                         | Yes      |Yes      | URL of the provider's logo.                                                                       |
| `multimedia`              | `List<MultimediaPair>`        | No       | Yes      |List of multimedia items associated with the provider.                                            |
| `scientificDomains`       | `List<ServiceProviderDomain>` | No       | Yes      |Scientific domains related to the provider's services.                                            |
| `tags`                    | `List<String>`                | No       | Yes      |Tags associated with the provider.                                                                |
| `structureTypes`          | `List<String>`                | No       | Yes      |Types of structures associated with the provider ([PROVIDER_STRUCTURE_TYPE](#provider_structure_type-)).                                                 |
| `location`                | `ProviderLocation`            | Yes      | Yes      |Physical location details of the provider.                                                        |
| `mainContact`             | `ProviderMainContact`         | Yes      | No      |Main contact information for the provider.                                                        |
| `publicContacts`          | `List<ProviderPublicContact>` | Yes      |Yes      | List of public contacts for the provider.                                                         |
| `lifeCycleStatus`         | `String`                      | No       | Yes      |Current lifecycle status of the provider.                                                         |
| `certifications`          | `List<String>`                | No       | Yes      |List of certifications held by the provider.                                                      |
| `participatingCountries`  | `List<String>`                | No       | Yes      |List of countries participating in the provider's services ([COUNTRY](#country-)).                                       |
| `affiliations`            | `List<String>`                | No       | Yes      |List of affiliations related to the provider.                                                     |
| `networks`                | `List<String>`                | No       | Yes      |Networks associated with the provider ([PROVIDER_NETWORK](#provider_network-)).                                                                 |
| `esfriDomains`            | `List<String>`                | No       |Yes      | ESFRI (European Strategy Forum on Research Infrastructures) domains associated with the provider ([PROVIDER_ESFRI_DOMAIN](#provider_esfri_domain-)). |
| `esfriType`               | `String`                      | No       |Yes      | ESFRI type classification of the provider ([PROVIDER_ESFRI_TYPE_](#provider_esfri_type-)).                                                        |
| `merilScientificDomains`  | `List<ProviderMerilDomain>`   | No       | Yes      |MERIL scientific domains associated with the provider.                                            |
| `areasOfActivity`         | `List<String>`                | No       | Yes      |Areas of activity related to the provider's services ([PROVIDER_AREA_OF_ACTIVITY](#provider_area_of_activity-)).                                             |
| `societalGrandChallenges` | `List<String>`                | No       |Yes      | Societal grand challenges addressed by the provider ([PROVIDER_SOCIETAL_GRAND_CHALLENGE](#provider_societal_grand_challenge-)).                                             |
| `nationalRoadmaps`        | `List<String>`                | No       |Yes      | National roadmaps associated with the provider.                                                   |
| `users`                   | `List<User>`                  | Yes      |No      | List of users associated with the provider.                                                       |

#### Nested Objects

##### MultimediaPair

| Field            | Type     | Required | Description                      |
|------------------|----------|----------|----------------------------------|
| `multimediaURL`  | `URL`    | Yes      | URL to the multimedia resource.  |
| `multimediaName` | `String` | No       | Name of the multimedia resource. |

##### ProviderLocation

| Field                 | Type      | Required | Description                                     |
|-----------------------|-----------|----------|-------------------------------------------------|
| `organizationName` | `String`  | No      | Name of the organization.     |
| `streetNameAndNumber` | `String`  | Yes      | Street address of the provider's location.     |
| `postalCode`          | `String`  | Yes      | Postal code of the provider's location.        |
| `city`                | `String`  | Yes      | City where the provider is located.            |
| `region`              | `String`  | No       | Region or state where the provider is located. |
| `country`             | `String`  | Yes      | Country where the provider is located ([COUNTRY](#country-)).         |

##### ProviderMainContact

| Field          | Type     | Required | Description                               |
|----------------|----------|----------|-------------------------------------------|
| `firstName`    | `String` | Yes      | First name of the main contact person.    |
| `lastName`     | `String` | No       | Last name of the main contact person.     |
| `email`        | `String` | Yes      | Email address of the main contact person. |
| `phone`        | `String` | No       | Phone number of the main contact person.  |
| `position`     | `String` | No       | Position of the main contact person.      |
| `organisation` | `String` | No       | Organisation of the main contact person.  |

##### ProviderPublicContact

| Field          | Type     | Required | Description                                 |
|----------------|----------|----------|---------------------------------------------|
| `firstName`    | `String` | No       | First name of the public contact person.    |
| `lastName`     | `String` | No       | Last name of the public contact person.     |
| `email`        | `String` | Yes      | Email address of the public contact person. |
| `phone`        | `String` | No       | Phone number of the public contact person.  |
| `position`     | `String` | No       | Position of the public contact person.      |
| `organisation` | `String` | No       | Organisation of the public contact person.  |

##### ProviderMerilDomain

| Field                      | Type     | Required | Description                                         |
|----------------------------|----------|----------|-----------------------------------------------------|
| `merilScientificDomain`    | `String` | Yes      | MERIL scientific domain related to the provider ([PROVIDER_MERIL_SCIENTIFIC_DOMAIN](#provider_meril_scientific_domain-)).    |
| `merilScientificSubdomain` | `String` | No       | MERIL scientific subdomain related to the provider ([PROVIDER_MERIL_SCIENTIFIC_SUBDOMAIN](#provider_meril_scientific_subdomain-)). |

##### NodeInfo 

| Field                      | Type     | Required | Public | Description                                         |
|----------------------------|----------|----------|-------------------------|----------------------------|
| `isNode`    | `String` | No      |Yes |Indicates if resource is a Node.    |
| `openAIRECommunityTag` | `String` | No | No | OpenAIRE tag if node exists there. |
| `nodeType`    | `String` | No      |No |Type of the Node ([NODE_TYPE](#node_type-)).    |
| `enrollmentSteps`    | `EnrollmentSteps`  | No      |No |Steps for node enrollement.    |

##### EnrollmentSteps 

| Field                      | Type     | Required | Public | Description                                         |
|----------------------------|----------|----------|-------------------------|----------------------------|
| `aaiEnrollment`    | `String` | No      |No |Aai enrollment status ([ENROLLMENT_STATUS](#enrollment_status-)).    |
| `cataloguesEnrollment` | `String` | No | No |Catalogues enrollment status ([ENROLLMENT_STATUS](#enrollment_status-)). |
| `helpdeskEnrollment`    | `String` | No      |No |Helpdesk enrollment status ([ENROLLMENT_STATUS](#enrollment_status-)).    |
| `monitoringEnrollment`    | `String`    | No      |No |Monitoring enrollment status ([ENROLLMENT_STATUS](#enrollment_status-)).    |
| `enrollmentGreenLight`    | `EnrollmentSteps`  | No      |No |Greenlight status for official node enrollment ([ENROLLMENT_STATUS](#enrollment_status-)).      |
| `legalFramework`    | `EnrollmentSteps`  | No      |No |LegalFramework status for node enrollment ([ENROLLMENT_STATUS](#enrollment_status-)).        |


#### Example

```json
{
    "metadata": {
        "registeredBy": "system",
        "registeredAt": "1612355292822",
        "modifiedBy": "system",
        "modifiedAt": "1644856675445",
        "published": false
    },
    "active": false,
    "suspended": false,
    "draft": false,
    "legacy": true,
    "loggingInfo": [
        {
            "date": "1739388620330",
            "userEmail": "null",
            "userFullName": "System",
            "userRole": "admin",
            "type": "update",
            "comment": "null",
            "actionType": "updated"
        },
        {
            "date": "1739388620330",
            "userEmail": "null",
            "userFullName": "System",
            "userRole": "admin",
            "type": "onboard",
            "comment": "null",
            "actionType": "approved"
        }
    ],
    "status": "approved",
    "resourceOrganisationGroupID": "groupId",
    "nodeInfo": {
        "isNode": true,
        "openAIRECommunityTag": "openAIREtag",
        "nodeType": "node_type-thematic",
        "enrollmentSteps": {
            "aaiEnrollment": "enrollment_status-completed",
            "cataloguesEnrollment": "enrollment_status-completed",
            "helpdeskEnrollment": "enrollment_status-completed",
            "monitoringEnrollment": "enrollment_status-completed"
        }
    },
    "id": "provider_001",
    "provider": {
        "id": "provider_001",
        "abbreviation": "PROV",
        "name": "Sample Provider",
        "website": "https://example.com",
        "legalEntity": true,
        "legalStatus": "provider_legal_status-non_for_profit_company",
        "hostingLegalEntity": "provider_hosting_legal_entity-athena",
        "alternativeIdentifiers": [
            {
                "type": "Other ID Type",
                "value": "123-abc"
            }
        ],
        "description": "This is a sample provider description.",
        "logo": "https://example.com/logo.png",
        "multimedia": [
            {
                "multimediaURL": "https://example.com/media",
                "multimediaName": "Sample Multimedia"
            }
        ],
        "scientificDomains": [
            {
                "scientificDomain": "scientific_domain-generic",
                "scientificSubdomain": "scientific_subdomain-generic-generic"
            }
        ],
        "tags": [
            "science",
            "research"
        ],
        "structureTypes": [
            "provider_structure_type-other"
        ],
        "location": {
            "organizationName": "Organization name",
            "streetNameAndNumber": "123 Main St",
            "postalCode": "12345",
            "city": "Sample City",
            "region": "EU",
            "country": "EL"
        },
        "mainContact": {
            "firstName": "John",
            "lastName": "Doe",
            "email": "john.doe@example.com",
            "phone": "+123456789",
            "position": "Manager"
        },
        "publicContacts": [
            {
                "firstName": "Jane",
                "lastName": "Smith",
                "email": "jane.smith@example.com",
                "phone": "+987654321",
                "position": "Support"
            }
        ],
        "lifeCycleStatus": "provider_life_cycle_status-other",
        "certifications": [
            "ISO9001",
            "ISO27001"
        ],
        "participatingCountries": [
            "IT",
            "GB"
        ],
        "affiliations": [
            "Affiliation1",
            "Affiliation2"
        ],
        "networks": [
            "Network1",
            "Network2"
        ],
        "esfriDomains": [
            "provider_esfri_domain-environment",
            "provider_esfri_domain-other"
        ],
        "esfriType": "provider_esfri_type-project",
        "merilScientificDomains": [
            {
                "merilScientificDomain": "provider_meril_scientific_domain-other",
                "merilScientificSubdomain": "provider_meril_scientific_domain-other-other"
            }
        ],
        "areasOfActivity": [
            "provider_area_of_activity-basic_research",
            "provider_area_of_activity-applied_research"
        ],
        "societalGrandChallenges": [
            "provider_societal_grand_challenge-energy"
        ],
        "nationalRoadmaps": [
            "Roadmap1",
            "Roadmap2"
        ],
        "users": [
            {
                "id": "user_001",
                "email": "user@example.com",
                "name": "User Name",
                "surname": "Surname"
            }
        ]
    }
}
```
### Service Bundle
| Field                  | Type           | Required | Public | Description                                                 |
|------------------------|----------------|----------|--------|-------------------------------------------------------------|
| `id`                   | `String`       | auto-gen | Yes    | Unique identifier for the resource.                        |
| `active`               | `Boolean`      | No       | No     | Indicates whether the resource is active.                  |
| `suspended`            | `Boolean`      | No       | No     | Indicates whether the resource is suspended.               |
| `draft`                | `Boolean`      | No       | No     | Indicates whether the resource is in draft state.          |
| `legacy`               | `Boolean`      | No       | No     | Indicates whether the resource is from EOSC Future.        |
| `status`               | `String`       | No       | No     | Provides information about the resource status([RESOURCE_STATUS](#resource_status-)). |
| `metadata`             | `Metadata`     | No       | Yes    | Additional metadata for the resource.       
| `resourceOrganisationGroupID`    | `String`       | No       | No     |ID of the provider's organization.               |
| `loggingInfo`          | `LoggingInfo`  | No       | No     | Contains details about resource updates.                   |
| `latestOnboardingInfo` | `LoggingInfo`  | No       | No     | Details of the latest onboarding action.                      |
| `latestUpdateInfo` | `LoggingInfo`  | No       | No     | Details of the latest update action.                  |      |
| `resourceExtras` | `ResourceExtras`  | No       | Yes     | Extra resource information.                  |      |
| `sites`             | `List<Site>`     | No       | Yes    | Information on the service's sites.  
| `onboardingIntegration`           | `OnboardingIntegration`       | No| Yes    | Information about onboarding integration steps.
| `nodeId`                   | `String`       | No| Yes    | ID of the node the resource belongs.
| `offboardRequestPending`                | `Boolean`      | No       | No     | Indicates whether the resource has a pending offboard request.          |
| `acknowledgement`           | `Acknowledgement`   | No      | No    | Acknowledgement for different statements.                           |  
| `service`           | `Service`   | Yes      | Yes    | Metadata of the actual resource.                           |

### Service

| Field                  | Type           | Required | Public | Description                                                 |
|------------------------|----------------|----------|--------|-------------------------------------------------------------|
| `id`                          | `String`                      | auto-gen |  Yes    |Unique identifier for the service.                                        |
| `abbreviation`                | `String`                      | Yes      | Yes    | Abbreviation of the service's name.                                       |
| `name`                        | `String`                      | Yes      |  Yes    |Full name of the service.                                                 |
| `resourceOrganisation`        | `String`                      | Yes      | Yes    | The PID of the organization providing the service.                  |
| `resourceProviders`           | `List<String>`                | No       |  Yes    |List of resource providers associated with the service.                   |
| `webpage`                     | `URL`                         | Yes      |  Yes    |URL of the service's webpage.                                             |
| `alternativeIdentifiers`      | `List<AlternativeIdentifier>` | No       | Yes    | List of alternative identifiers for the service.                          |
| `description`                 | `String`                      | Yes      | Yes    | Detailed description of the service.                                      |
| `tagline`                     | `String`                      | Yes      | Yes    | Short tagline summarizing the service.                                    |
| `logo`                        | `URL`                         | Yes      |  Yes    |URL of the service's logo.                                                |
| `multimedia`                  | `List<MultimediaPair>`        | No       | Yes    | List of multimedia items related to the service.                          |
| `useCases`                    | `List<UseCasesPair>`          | No       |  Yes    |List of use cases demonstrating the service in action.                    |
| `scientificDomains`           | `List<ServiceProviderDomain>` | Yes      |  Yes    |List of scientific domains related to the service.                        |
| `categories`                  | `List<ServiceCategory>`       | Yes      |  Yes    |Categories and subcategories of the service.                              |
| `targetUsers`                 | `List<String>`                | Yes      |  Yes    |List of target users for the service ([TARGET_USER](#target_user-)).                                     |
| `accessTypes`                 | `List<String>`                | No       | Yes    | Types of access provided by the service (e.g., open, restricted) ([ACCESS_TYPE](#access_type-)).         |
| `accessModes`                 | `List<String>`                | No       |  Yes    |Modes of access available for the service (e.g., online, in-person) ([ACCESS_MODE](#access_mode-)).      |
| `tags`                        | `List<String>`                | No       |  Yes    |Tags associated with the service.                                         |
| `horizontalService`           | `Boolean`                     | No       |  Yes    |Indicates if the service is a horizontal service.                         |
| `serviceCategories`           | `List<String>`                | No       | Yes    | List of service categories associated with the service ([SERVICE_CATEGORY](#service_category-)).                   |
| `marketplaceLocations`        | `List<String>`                | No       | Yes    | List of marketplace locations where the service is available ([MARKETPLACE_LOCATION](#marketplace_location-)).             |
| `classTier`        | `ServiceClassTier`                | No       | Yes    | Information related to the tier of a service in the EOSC EU Node           |
| `geographicalAvailabilities`  | `List<String>`                | Yes      |  Yes    |List of geographical availabilities of the service ([REGION](#region-)).                       |
| `languageAvailabilities`      | `List<String>`                | Yes      |  Yes    |List of language availabilities of the service ([LANGUAGE](#language-)).                           |
| `resourceGeographicLocations` | `List<String>`                | No       | Yes    | List of locations where the service resources are geographically located ([COUNTRY](#country-)). |
| `mainContact`                 | `ServiceMainContact`          | Yes      | No    | Main contact information for the service.                                 |
| `publicContacts`              | `List<ServicePublicContact>`  | Yes      |  Yes    |List of public contacts for the service.                                  |
| `helpdeskEmail`               | `String`                      | Yes      |  Yes    |Email address for the service's helpdesk.                                 |
| `securityContactEmail`        | `String`                      | Yes      | Yes    | Email address for security contact.                                       |
| `trl`                         | `String`                      | Yes      |  Yes    |Technology Readiness Level of the service ([TRL](#trl-)).                                |
| `lifeCycleStatus`             | `String`                      | No       |  Yes    |Life cycle status of the service ([LIFE_CYCLE_STATUS](#life_cycle_status-)).                                         |
| `certifications`              | `List<String>`                | No       |  Yes    |List of certifications related to the service.                            |
| `standards`                   | `List<String>`                | No       | Yes    | Standards that the service complies with.                                 |
| `openSourceTechnologies`      | `List<String>`                | No       |  Yes    |List of open-source technologies used in the service.                     |
| `version`                     | `String`                      | No       | Yes    | Current version of the service.                                           |
| `lastUpdate`                  | `Date`                        | No       | No    | Date and time of the last update.                                         |
| `changeLog`                   | `List<String>`                | No       | No    | List of changes made to the service.                                      |
| `requiredResources`           | `List<String>`                | No       | Yes    | List of required resources for the service.                               |
| `relatedResources`            | `List<String>`                | No       | Yes    | List of related resources linked to the service.                          |
| `relatedPlatforms`            | `List<String>`                | No       | Yes    | List of related platforms connected to the service ([RELATED_PLATFORM](#related_platform-)).                        |
| `fundingBody`                 | `List<String>`                | No       | Yes    | List of funding bodies supporting the service ([FUNDING_BODY](#funding_body-)).                            |
| `fundingPrograms`             | `List<String>`                | No       |  Yes    |List of funding programs related to the service ([FUNDING_PROGRAM](#funding_program-)).                          |
| `grantProjectNames`           | `List<String>`                | No       |  Yes    |Yes    | List of grant project names associated with the service.                  |
| `helpdeskPage`                | `URL`                         | No       | Yes    | URL of the helpdesk page.                                                 |
| `userManual`                  | `URL`                         | No       | Yes    | URL of the user manual.                                                   |
| `termsOfUse`                  | `URL`                         | Yes      | Yes    | URL of the terms of use.                                                  |
| `privacyPolicy`               | `URL`                         | Yes      | Yes    | URL of the privacy policy.                                                |
| `accessPolicy`                | `URL`                         | No       |  Yes    |URL of the access policy.                                                 |
| `resourceLevel`               | `URL`                         | No       | Yes    | URL of the resource level details.                                        |
| `trainingInformation`         | `URL`                         | No       | Yes    | URL of the training information.                                          |
| `statusMonitoring`            | `URL`                         | No       | Yes    | URL for status monitoring information.                                    |
| `maintenance`                 | `URL`                         | No       | Yes    | URL of the maintenance details.                                           |
| `orderType`                   | `String`                      | Yes      |  Yes    |Type of order required for the service ([ORDER_TYPE](#order_type-)).                                   |
| `order`                       | `URL`                         | No       |  Yes    |URL for ordering the service.                                             |
| `paymentModel`                | `URL`                         | No       |  Yes    |URL of the payment model information.                                     |
| `pricing`                     | `URL`                         | No       | Yes    | URL of the pricing details.                                               |

#### Nested Objects

##### MultimediaPair

| Field            | Type     | Required | Description                      |
|------------------|----------|----------|----------------------------------|
| `multimediaURL`  | `URL`    | Yes      | URL to the multimedia resource.  |
| `multimediaName` | `String` | No       | Name of the multimedia resource. |

##### UseCasesPair

| Field         | Type     | Required | Description                    |
|---------------|----------|----------|--------------------------------|
| `useCaseURL`  | `URL`    | Yes      | URL to the use case resource.  |
| `useCaseName` | `String` | No       | Name of the use case resource. |

##### ServiceCategory

| Field         | Type     | Required | Description                 |
|---------------|----------|----------|-----------------------------|
| `category`    | `String` | Yes      | Category of the service ([CATEGORY](#category-)).    |
| `subcategory` | `String` | No       | Subcategory of the service ([SUBCATEGORY](#subcategory-)). |

##### ServiceMainContact

| Field          | Type     | Required | Description                        |
|----------------|----------|----------|------------------------------------|
| `firstName`    | `String` | Yes      | First name of the main contact.    |
| `lastName`     | `String` | Yes      | Last name of the main contact.     |
| `email`        | `String` | Yes      | Email address of the main contact. |
| `phone`        | `String` | No       | Phone number of the main contact.  |
| `position`     | `String` | No       | Position of the main contact.      |
| `organisation` | `String` | No       | Organization of the main contact.  |

##### ServicePublicContact

| Field          | Type     | Required | Description                          |
|----------------|----------|----------|--------------------------------------|
| `firstName`    | `String` | No       | First name of the public contact.    |
| `lastName`     | `String` | No       | Last name of the public contact.     |
| `email`        | `String` | Yes      | Email address of the public contact. |
| `phone`        | `String` | No       | Phone number of the public contact.  |
| `position`     | `String` | No       | Position of the public contact.      |
| `organisation` | `String` | No       | Organization of the public contact.  |


##### ResourceExtras

| Field         | Type     | Required | Description                 |
|---------------|----------|----------|-----------------------------|
| `EOSCIFGuidelines`    | `List<EOSCIFGuidelines>` | No      | EOSC Interoperability Framework Guidelines.    |


##### EOSCIFGuidelines

| Field         | Type     | Required | Description                 |
|---------------|----------|----------|-----------------------------|
| `pid`    | `String` | No      | Pid of the guideline.    |
| `label`    | `String` | No      | Label for the guideline.    |
| `url`    | `URL` | No      | URL of the guideline.    |
| `semanticRelationship`    | `String` | No      | Semantic Relationship ([SEMANTIC_RELATIONSHIP](#semantic_relationship-)).    |

##### Site

| Field   | Type     | Required |  Public | Description                          |
|---------|----------|----------|---------|-----------------------------|
| `name`  | `String` | No       | Yes       |Name of the site.  |
| `endpoints` | `List<Endpoint>` | No       | Yes       |List of the endpoints. |

##### Endpoint

| Field   | Type     | Required |  Public | Description                          |
|---------|----------|----------|---------|-----------------------------|
| `name`  | `String` | No       |  Yes       |Name of the endpoint.  |
| `type` | `String` | No        |Yes       | Type of the endpoint ([ENDPOINT_TYPE](#endpoint_type-)). |
| `monitoringServiceType` | `String` | No       | No       | Type of the endpoint regarding monitoring service ([MONITORING_SERVICE_TYPE](#monitoring_service_type-)). |
| `url` | `String` | No       |  Yes       |URL of the endpoint. |

##### ServiceClassTier

| Field   | Type     | Required |  Public | Description                          |
|---------|----------|----------|---------|-----------------------------|
| `level`  | `Integer` | Yes       |  Yes       |Tier level.  |
| `accessPolicy` | `String` | No       | Yes       | Access policy of the service|
| `costModel` | `String` | No       |  Yes       |Cost model of the service. |
| `offerings` | `List <String>` | No       |  Yes       |List of offferings. |



##### OnboardingIntegration 

| Field                      | Type     | Required | Public | Description                                         |
|----------------------------|----------|----------|-------------------------|----------------------------|
| `serviceOfferFinalization`    | `String` | No      |No |Service offer finalization status ([INTEGRATION_STATUS](#integration_status-)).    |
| `accountIntegration` | `String` | No | No |Account integration status ([INTEGRATION_STATUS](#integration_status-)). |
| `aaiIntegration`    | `String` | No      |No |AAI integration status ([INTEGRATION_STATUS](#integration_status-)).    |
| `omsIntegration`    | `String`    | No      |No |Oms integration status ([INTEGRATION_STATUS](#integration_status-)).    |
| `securityCompliance`    | `String` | No      |No |Security compliance status ([INTEGRATION_STATUS](#integration_status-)).    |
| `wpfsIntegration`    | `String`    | No      |No |Wpfs Integration status ([INTEGRATION_STATUS](#integration_status-)).    |

### Example

```json
{
    "metadata": {
        "registeredBy": "system",
        "registeredAt": "1613666632297",
        "modifiedBy": "system",
        "modifiedAt": "1613666963711",
        "published": true
    },
    "active": true,
    "suspended": false,
    "draft": false,
    "legacy": false,
    "status": "approved",
    "sites": [
        {
            "name": "site_name",
            "endpoints": [
                {
                    "name": "endpoint_name",
                    "type": "endpoint_type-api",
                    "url": "endpoint_url",
                    "monitoringServiceType": "eu.eosc.container_platform.api"
                }
            ]
        }
    ],
    "resourceOrganisationGroupID": "groupId",
    "service": {
        "id": "service_001",
        "abbreviation": "SERV",
        "name": "Sample Service",
        "resourceOrganisation": "organisation_pid",
        "resourceProviders": [
            "Provider1",
            "Provider2"
        ],
        "webpage": "https://example.com",
        "alternativeIdentifiers": [
            {
                "type": "Other ID Type",
                "value": "abc-123"
            }
        ],
        "description": "This is a sample service description.",
        "tagline": "Providing high-quality services.",
        "logo": "https://example.com/logo.png",
        "multimedia": [
            {
                "multimediaURL": "https://example.com/media",
                "multimediaName": "Sample Multimedia"
            }
        ],
        "useCases": [
            {
                "useCaseURL": "https://example.com/use-case",
                "useCaseName": "Sample Use Case"
            }
        ],
        "scientificDomains": [
            {
                "scientificDomain": "scientific_domain-engineering_and_technology",
                "scientificSubdomain": "scientific_subdomain-engineering_and_technology-chemical_engineering"
            }
        ],
        "categories": [
            {
                "category": "category-access_physical_and_eInfrastructures-compute",
                "subcategory": "subcategory-access_physical_and_eInfrastructures-network-content_delivery_network"
            }
        ],
        "targetUsers": [
            "target_user-businesses",
            "target_user-other"
        ],
        "accessTypes": [
            "access_type-remote",
            "access_type-other"
        ],
        "accessModes": [
            "access_mode-free"
        ],
        "tags": [
            "innovation",
            "technology"
        ],
        "horizontalService": true,
        "serviceCategories": [
            "service_category-compute",
            "service_category-other"
        ],
        "marketplaceLocations": [
            "marketplace_location-discover_research_outputs",
            "marketplace_location-manage_research_data"
        ],
        "geographicalAvailabilities": [
            "EU"
        ],
        "languageAvailabilities": [
            "en",
            "el"
        ],
        "resourceGeographicLocations": [
            "EL",
            "UK"
        ],
        "mainContact": {
            "firstName": "John",
            "lastName": "Doe",
            "email": "contact@example.com",
            "phone": "123-456-7890",
            "position": "Manager",
            "organisation": "Sample Org"
        },
        "publicContacts": [
            {
                "firstName": "Jane",
                "lastName": "Smith",
                "email": "jane.smith@example.com",
                "phone": "098-765-4321",
                "position": "Support",
                "organisation": "Sample Org"
            }
        ],
        "helpdeskEmail": "helpdesk@example.com",
        "securityContactEmail": "security@example.com",
        "trl": "trl-7",
        "lifeCycleStatus": "life_cycle_status-operation",
        "certifications": [
            "Certification1",
            "Certification2"
        ],
        "standards": [
            "Standard1",
            "Standard2"
        ],
        "openSourceTechnologies": [
            "Technology1",
            "Technology2"
        ],
        "version": "1.0.0",
        "lastUpdate": "2024-09-09T12:00:00Z",
        "changeLog": [
            "Initial release.",
            "Minor updates."
        ],
        "requiredResources": [
            "Resource1",
            "Resource2"
        ],
        "relatedResources": [
            "RelatedResource1",
            "RelatedResource2"
        ],
        "relatedPlatforms": [
            "related_platform-datacite",
            "related_platform-egiace"
        ],
        "fundingBody": [
            "funding_body-aka",
            "funding_body-arc"
        ],
        "fundingPrograms": [
            "funding_program-agr"
        ],
        "grantProjectNames": [
            "Project1",
            "Project2"
        ],
        "helpdeskPage": "https://example.com/helpdesk",
        "userManual": "https://example.com/user-manual",
        "termsOfUse": "https://example.com/terms",
        "privacyPolicy": "https://example.com/privacy",
        "accessPolicy": "https://example.com/access-policy",
        "resourceLevel": "https://example.com/resource-level",
        "trainingInformation": "https://example.com/training",
        "statusMonitoring": "https://example.com/status-monitoring",
        "maintenance": "https://example.com/maintenance",
        "orderType": "order_type-order_required",
        "order": "https://example.com/order",
        "paymentModel": "https://example.com/payment-model",
        "pricing": "https://example.com/pricing"
    }
}
```
### Training Resource Bundle
| Field                  | Type           | Required | Public | Description                                                 |
|------------------------|----------------|----------|--------|-------------------------------------------------------------|
| `id`                   | `String`       | auto-gen | Yes    | Unique identifier for the resource.                        |
| `active`               | `Boolean`      | No       | No     | Indicates whether the resource is active.                  |
| `suspended`            | `Boolean`      | No       | No     | Indicates whether the resource is suspended.               |
| `draft`                | `Boolean`      | No       | No     | Indicates whether the resource is in draft state.          |
| `legacy`               | `Boolean`      | No       | No     | Indicates whether the resource is from EOSC Future.        |
| `status`               | `String`       | No       | No     | Provides information about the resource status ([RESOURCE_STATUS](#resource_status-)). |
| `metadata`             | `Metadata`     | No       | Yes    | Additional metadata for the resource.       
| `resourceOrganisationGroupID`    | `String`       | No       | No     |ID of the provider's organization               |
| `offboardRequestPending`                | `Boolean`      | No       | No     | Indicates whether the resource has a pending offboard request. |
| `loggingInfo`          | `LoggingInfo`  | No       | No     | Contains details about resource updates.                   |
| `latestOnboardingInfo` | `LoggingInfo`  | No       | No     | Details of the latest onboarding action.                      |
| `latestUpdateInfo` | `LoggingInfo`  | No       | No     | Details of the latest update action.                  |      |
| `acknowledgement`           | `Acknowledgement`   | No      | No    | Acknowledgement for different statements.                           |  
| `trainingResource`           | `TrainingResource`   | Yes      | Yes    | Metadata of the actual resource.       
                    |
### Training Resource

| Field                        | Type                          | Required | Public| Description                                                                       |
|------------------------------|-------------------------------|----------|----|-------------------------------------------------------------------------------|
| `id`                         | `String`                      | auto-gen| Yes | Unique identifier for the training resource.                                      |
| `title`                      | `String`                      | Yes    | Yes  | Title of the training resource.                                                   |
| `resourceOrganisation`       | `String`                      | Yes   | Yes   | The PID of the organization providing the training resource.                                              |
| `resourceProviders`          | `List<String>`                | No    | Yes   | List of resource providers associated with the training resource.                 |
| `authors`                    | `List<String>`                | Yes  | Yes    | List of authors who contributed to the training resource.                         |
| `url`                        | `URL`                         | Yes   | Yes   | URL linking to the training resource.                                             |
| `urlType`                    | `String`                      | No   | Yes    | Type of URL, e.g., landing page, direct link, etc.                                |
| `eoscRelatedServices`        | `List<String>`                | No   | Yes    | List of related services in the European Open Science Cloud (EOSC).               |
| `alternativeIdentifiers`     | `List<AlternativeIdentifier>` | No  | Yes     | List of alternative identifiers for the training resource.                        |
| `description`                | `String`                      | No   | Yes    | Description of the training resource.                                             |
| `keywords`                   | `List<String>`                | No  | Yes     | Keywords associated with the training resource.                                   |
| `license`                    | `String`                      | Yes  | Yes    | License under which the training resource is distributed.                         |
| `accessRights`               | `String`                      | Yes    | Yes  | Access rights for the training resource, e.g., open, restricted, etc.             |
| `versionDate`                | `Date`                        | Yes   | Yes   | Date and time when the version was published.                                     |
| `targetGroups`               | `List<String>`                | Yes  | Yes    | List of target groups intended for the training resource.                         |
| `learningResourceTypes`      | `List<String>`                | No  | Yes     | Types of learning resources, e.g., video, article, tutorial.                      |
| `learningOutcomes`           | `List<String>`                | Yes | Yes     | List of learning outcomes expected from the training resource.                    |
| `expertiseLevel`             | `String`                      | Yes | Yes     | Expertise level required for the training resource, e.g., beginner, intermediate. |
| `contentResourceTypes`       | `List<String>`                | No | Yes      | Types of content included in the training resource, e.g., text, multimedia.       |
| `qualifications`             | `List<String>`                | No  | Yes     | List of qualifications or certifications associated with the resource.            |
| `duration`                   | `String`                      | No  | Yes     | Duration of the training resource, e.g., "2 hours".                               |
| `languages`                  | `List<String>`                | Yes  | Yes    | Languages in which the training resource is available.                            |
| `geographicalAvailabilities` | `List<String>`                | Yes| Yes      | List of geographical locations where the resource is available.                   |
| `scientificDomains`          | `List<ServiceProviderDomain>` | Yes  | Yes    | List of scientific domains and subdomains relevant to the training resource.      |
| `contact`                    | `ServiceMainContact`          | Yes   | No   | Contact details for the main contact person for the training resource.            |                                 |

#### Nested Objects

##### ServiceMainContact

| Field          | Type     | Required | Description                        |
|----------------|----------|----------|------------------------------------|
| `firstName`    | `String` | Yes      | First name of the main contact.    |
| `lastName`     | `String` | Yes      | Last name of the main contact.     |
| `email`        | `String` | Yes      | Email address of the main contact. |
| `phone`        | `String` | No       | Phone number of the main contact.  |
| `position`     | `String` | No       | Position of the main contact.      |
| `organisation` | `String` | No       | Organization of the main contact.  |

### Example

```json
{
    "metadata": {
        "registeredBy": "system",
        "registeredAt": "1694002755178",
        "modifiedBy": "system",
        "modifiedAt": "1711537582178",
        "published": false
    },
    "active": false,
    "suspended": false,
    "draft": true,
    "legacy": false,
    "status": "pending",
    "trainingResource": {
        "id": "training_001",
        "title": "Introduction to Data Science",
        "resourceOrganisation": "Data Science Institute",
        "resourceProviders": [
            "Provider A",
            "Provider B"
        ],
        "authors": [
            "Author One",
            "Author Two"
        ],
        "url": "https://example.com/training-resource",
        "urlType": "landingPage",
        "eoscRelatedServices": [
            "Service A",
            "Service B"
        ],
        "alternativeIdentifiers": [
            {
                "type": "DOI",
                "value": "10.1234/training"
            }
        ],
        "description": "An introductory course on data science concepts.",
        "keywords": [
            "Data Science",
            "Machine Learning"
        ],
        "license": "Creative Commons Attribution 4.0",
        "accessRights": "Open Access",
        "versionDate": "2024-09-10T00:00:00Z",
        "targetGroups": [
            "Researchers",
            "Students"
        ],
        "learningResourceTypes": [
            "Course",
            "Tutorial"
        ],
        "learningOutcomes": [
            "Understand basics of data science",
            "Apply machine learning models"
        ],
        "expertiseLevel": "Beginner",
        "contentResourceTypes": [
            "Video",
            "PDF"
        ],
        "qualifications": [
            "Certificate of Completion"
        ],
        "duration": "3 hours",
        "languages": [
            "English",
            "Spanish"
        ],
        "geographicalAvailabilities": [
            "Europe",
            "Global"
        ],
        "scientificDomains": [
            {
                "scientificDomain": "Computer Science",
                "scientificSubdomain": "Machine Learning"
            }
        ],
        "contact": {
            "firstName": "John",
            "lastName": "Doe",
            "email": "john.doe@example.com",
            "phone": "+123456789",
            "position": "Course Coordinator",
            "organisation": "Data Science Institute"
        }
    }
}
```
### Tool Bundle
| Field                  | Type           | Required | Public | Description                                                 |
|------------------------|----------------|----------|--------|-------------------------------------------------------------|
| `id`                   | `String`       | auto-gen | Yes    | Unique identifier for the resource.                        |
| `active`               | `Boolean`      | No       | No     | Indicates whether the resource is active.                  |
| `suspended`            | `Boolean`      | No       | No     | Indicates whether the resource is suspended.               |
| `draft`                | `Boolean`      | No       | No     | Indicates whether the resource is in draft state.          |
| `legacy`               | `Boolean`      | No       | No     | Indicates whether the resource is from EOSC Future.        |
| `status`               | `String`       | No       | No     | Provides information about the resource status([RESOURCE_STATUS](#resource_status-)). |
| `metadata`             | `Metadata`     | No       | Yes    | Additional metadata for the resource.       
| `resourceOrganisationGroupID`    | `String`       | No       | No     |ID of the provider's organization.               |
| `loggingInfo`          | `LoggingInfo`  | No       | No     | Contains details about resource updates.                   |
| `latestOnboardingInfo` | `LoggingInfo`  | No       | No     | Details of the latest onboarding action.                      |
| `latestUpdateInfo` | `LoggingInfo`  | No       | No     | Details of the latest update action. 
| `security`           | `ToolSecurity`   | Yes      | Yes    | Security related metadata.                    |      |
| `contributorProvided`                | `Boolean`      | No       | No     | Indicates whether the resource is related to a Provider.
| `offboardRequestPending`                | `Boolean`      | No       | No     | Indicates whether the resource has a pending offboard request.          |
| `acknowledgement`           | `Acknowledgement`   | No      | No    | Acknowledgement for different statements.                           |  
| `tool`           | `Tool`   | Yes      | Yes    | Metadata of the actual resource.       
                    |
### Tool

| Field                        | Type                          | Required | Public| Description                                                                       |
|------------------------------|-------------------------------|----------|----|-------------------------------------------------------------------------------|
| `id`                         | `String`                      | auto-gen| Yes | Unique identifier for the training resource.                                      |
| `name`                      | `String`                      | Yes    | Yes  | Name of the tool.                                                   |
| `resourceOrganisation`       | `String`                      | No   | Yes   | The PID of the organisation providing the resource.                                              |
| `resourceProvider`          | `String`                | No    | Yes   | ID of the resource provider.              |
| `author`                    | `String`                | Yes  | Yes    | Authors who contributed to the tool.                         |                        |
| `relatedResources`        | `List<String>`                | No   | Yes    | List of related resources in the European Open Science Cloud (EOSC).               |                       |
| `description`                | `String`                      | No   | Yes    | Description of the training resource.                                             |
| `keywords`                   | `List<String>`                | Yes  | Yes     | Keywords associated with the tool.                                   |
| `license`                    | `String`                      | Yes  | Yes    | License under which the training resource is distributed.                         |          |
| `versionDate`                | `Date`                       | Yes   | Yes   | Date and time when the version was published.                                     |                    |
| `targetInfrastructure`      | `List<String>`               | Yes  | Yes     | Target infrastructures of the tool.                      |
| `targetGroups`      | `List<String>`               | No  | Yes     | Target groups of the tool.               
| `deprecated`               | `Boolean`      | No       | No     | Indicates whether the resource is deprecated.        |       |                  |      |      |      
| `scientificDomains`          | `List<ServiceProviderDomain>` | Yes  | Yes    | List of scientific domains and subdomains relevant to the training resource.      |
| `helpdeskPage`                    | `String`          | No   | Yes   | Helpdesk page of the tool.            |                                
| `creditCost`                    | `String`          | No   | Yes   | Credit cost of the tool.            |     
| `email`                    | `String`          | No   | No   | Contact email for the tool.            |      |

##### ToolSecurity

| Field          | Type     | Required | Description                        |
|----------------|----------|----------|------------------------------------|
| `status`    | `String` | No      | Security status.    |
| `vulnerabilities`     | `String` | No      | Tool vulnerabilities.     |
| `lastCheck`        | `String` | No      | Datetime of the last security check. |
| `reportUrl`        | `String` | No       | URL of the report.  |
| `reviewed`     | `String` | No       | Indicates if tool is reviewed.      |

### Example

```json
{
    "metadata": {
        "registeredBy": "null",
        "registeredAt": "1733734606",
        "modifiedBy": "null",
        "modifiedAt": "1733739459",
        "published": true
    },
    "active": false,
    "suspended": false,
    "draft": false,
    "legacy": false,
    "loggingInfo": [
        {
            "date": "1733739490542",
            "userEmail": "null",
            "userFullName": "System",
            "userRole": "admin",
            "type": "update",
            "comment": "null",
            "actionType": "updated"
        },
        {
            "date": "1733739490542",
            "userEmail": "null",
            "userFullName": "System",
            "userRole": "admin",
            "type": "onboard",
            "comment": "null",
            "actionType": "approved"
        }
    ],
    "latestOnboardingInfo": {
        "date": "1733739490542",
        "userEmail": "null",
        "userFullName": "System",
        "userRole": "admin",
        "type": "onboard",
        "comment": "null",
        "actionType": "approved"
    },
    "status": "approved",
    "security": {},
    "contributorProvided": false,
    "tool": {
        "id": "21.11162/6WP3Id",
        "name": "go to top 2",
        "resourceOrganisation": "EU_node_pid",
        "description": "desc",
        "keywords": [
            "eu"
        ],
        "license": "tool_license-apache",
        "versionDate": "2024-12-09T08:56:46.990+00:00",
        "targetInfrastructure": [
            "tool_target_infrastructure-vm"
        ],
        "targetGroups": [
            "target_user-other"
        ],
        "author": "EU Node",
        "deprecated": true,
        "scientificDomains": [
            {
                "scientificDomain": "scientific_domain-agricultural_sciences",
                "scientificSubdomain":        "scientific_subdomain-agricultural_sciences-agricultural_biotechnology"
            }
        ],
        "creditCost": "-",
        "email": "john.doe@example.com"
    },
    "id": "tool_id"
}
```
### Resource Revision Bundle
| Field                  | Type           | Required | Public | Description                                                 |
|------------------------|----------------|----------|--------|-------------------------------------------------------------|
| `id`                   | `String`       | auto-gen | Yes    | Unique identifier for the resource.                        |
| `originalId`               | `String`      | No       | No     | Identifier of the original resource.                  |       |
| `status`               | `String`       | No       | No     | Provides information about the resource status([RESOURCE_STATUS](#resource_status-)). |
| `active`               | `Boolean`      | No       | No     | Indicates whether the resource is active.                  |
| `draft`                | `Boolean`      | No       | No     | Indicates whether the resource is in draft state.          |
| `resourceType`               | `String`       | No       | No     | Provides information about the resource type([RESOURCE_TYPE](#resource_type-)). |
| `metadata`             | `Metadata`     | No       | Yes    | Additional metadata for the resource.                |
| `loggingInfo`          | `LoggingInfo`  | No       | No     | Contains details about resource updates.                   |                |
| `latestUpdateInfo` | `LoggingInfo`  | No       | No     | Details of the latest update action. 
| `linkedServiceRevisionId` | `String`  | No       | No     | Id of the linked service revision (for datasources)
| `resourceRevision`           | `Tool`   | Yes      | Yes    | Metadata of the actual resource.       
                    |
### Resource Revision

| Field                        | Type                          | Required | Public| Description                                                                       |
|------------------------------|-------------------------------|----------|----|-------------------------------------------------------------------------------|
| `id`                         | `String`                      | auto-gen| Yes | Unique identifier for the resource revision.                                      |
| `resourceData`                      | `String`                      | No    | No  | JSON data of the resource for approval.                                                   |

### Example

```json
{
    "metadata": {
        "registeredBy": "null",
        "registeredAt": "1733734606",
        "modifiedBy": "null",
        "modifiedAt": "1733739459",
        "published": true
    },
    "loggingInfo": [
        {
            "date": "1733739490542",
            "userEmail": "null",
            "userFullName": "System",
            "userRole": "admin",
            "type": "update",
            "comment": "null",
            "actionType": "updated"
        },
        {
            "date": "1733739490542",
            "userEmail": "null",
            "userFullName": "System",
            "userRole": "admin",
            "type": "onboard",
            "comment": "null",
            "actionType": "pending"
        }
    ],
    "status": "pending",
    "originalId": "service_id",
    "resourceType": "service",
    "active": "true",
    "draft": "false",
    "resourceRevision": {
        "id": "resource_revision_id",
        "resourceData": "{\"metadata\":{\"registeredBy\":\"system\",\"registeredAt\":\"1613666632297\",\"modifiedBy\":\"system\",\"modifiedAt\":\"1613666963711\",\"published\":true},\"active\":true,\"suspended\":false,\"draft\":false,\"legacy\":false,\"status\":\"approved\",\"scientificDomains\": [{\"scientificDomain\": \"scientific_domain-engineering_and_technology\",\"scientificSubdomain\": \"scientific_subdomain-engineering_and_technology-chemical_engineering\"}]..."
    },
    "id": "resource_revision_id"
}
```

### Vocabulary


| Field         | Type                  | Required | Description                                             |
|---------------|-----------------------|----------|---------------------------------------------------------|
| `id`          | `String`              | auto-gen | A unique identifier for the vocabulary.                 |
| `name`        | `String`              | Yes      | The name of the vocabulary.                             |
| `description` | `String`              | No       | A brief description of the vocabulary.                  |
| `parentId`    | `String`              | No       | The identifier of the parent vocabulary, if applicable. |
| `type`        | `String`              | Yes      | Specifies the type/category of the vocabulary.          |
| `extras`      | `Map<String, String>` | No       | A map for storing additional key-value pairs.           |

#### Example

```json
{
    "id": "access_mode-free",
    "name": "Free",
    "description": "Users can freely access the Resource provided, registration may be needed.",
    "parentId": null,
    "type": "Access mode",
    "extras": {}
}
```
### Miscellaneous

##### Metadata

| Field          | Type     | Required | Public| Description                        |
|----------------|----------|----------|-------|-----------------------------|
| `registeredBy`    | `String` | Yes    |No  | Person who registered the resource.    |
| `registeredAt`     | `String` | Yes   |Yes   | Timestamp when the resource was registered.     |
| `modifiedBy`        | `String` | Yes  |No    | Person who modified the resource. |
| `modifiedAt`        | `String` | No   |No    | Timestamp when the resource was modified.  |
| `published` | `String` | No      |No |Indicates if resource is published.  |

##### Acknowledgement

| Field      | Type     | Required | Public| Description                          |
|------------|----------|----------|-------|-----------------------------|
| `catalogueStoreAck`  | `Boolean` | No       |No  | Acknowledgement for catalogue store.  |
| `resourceHubAck`  | `Boolean` | No       | No |Acknowledgement for Resource Hub.  |
| `monitoringServiceAck`  | `Boolean` | No    |No | Acknowledgement for monitoring service.  |
| `securityContactAck`  | `Boolean` | No       | No   |Acknowledgement for security contact.  |

##### ServiceProviderDomain

| Field                 | Type     | Required | Description                                    |
|-----------------------|----------|----------|------------------------------------------------|
| `scientificDomain`    | `String` | Yes      | Scientific domain related to the catalogue.    |
| `scientificSubdomain` | `String` | No       | Scientific subdomain related to the catalogue. |

##### AlternativeIdentifier

| Field   | Type     | Required | Description                          |
|---------|----------|----------|--------------------------------------|
| `type`  | `String` | No       | Type of the alternative identifier.  |
| `value` | `String` | No       | Value of the alternative identifier. |

## List of Vocabularies

### ACCESS_MODE [🔗](https://github.com/EOSC-Lot-1/een-resource-catalogue-docs/blob/eosc/vocabularies/ACCESS_MODE.json)
### ACCESS_TYPE [🔗](https://github.com/EOSC-Lot-1/een-resource-catalogue-docs/blob/eosc/vocabularies/ACCESS_TYPE.json)
### CATALOGUE_STATE [🔗](https://github.com/EOSC-Lot-1/een-resource-catalogue-docs/blob/eosc/vocabularies/CATALOGUE_STATE.json)
### CATEGORY [🔗](https://github.com/EOSC-Lot-1/een-resource-catalogue-docs/blob/eosc/vocabularies/CATEGORY.json)
### COUNTRY [🔗](https://github.com/EOSC-Lot-1/een-resource-catalogue-docs/blob/eosc/vocabularies/COUNTRY.json)
### COUNTRY_PHONE_CODES [🔗](https://github.com/EOSC-Lot-1/een-resource-catalogue-docs/blob/eosc/vocabularies/COUNTRY_PHONE_CODES.json)
### CT_COMPATIBILITY [🔗](https://github.com/EOSC-Lot-1/een-resource-catalogue-docs/blob/eosc/vocabularies/CT_COMPATIBILITY.json)
### CT_PROTOCOL [🔗](https://github.com/EOSC-Lot-1/een-resource-catalogue-docs/blob/eosc/vocabularies/CT_PROTOCOL.json)
### DATASOURCE_TYPE [🔗](https://github.com/EOSC-Lot-1/een-resource-catalogue-docs/blob/eosc/vocabularies/DATASOURCE_TYPE.json)
### DS_CLASSIFICATION [🔗](https://github.com/EOSC-Lot-1/een-resource-catalogue-docs/blob/eosc/vocabularies/DS_CLASSIFICATION.json)
### DS_COAR_ACCESS_RIGHTS_1_0 [🔗](https://github.com/EOSC-Lot-1/een-resource-catalogue-docs/blob/eosc/vocabularies/DS_COAR_ACCESS_RIGHTS_1_0.json)
### DS_JURISDICTION [🔗](https://github.com/EOSC-Lot-1/een-resource-catalogue-docs/blob/eosc/vocabularies/DS_JURISDICTION.json)
### DS_OAI_COMPATIBILITY [🔗](https://github.com/EOSC-Lot-1/een-resource-catalogue-docs/blob/eosc/vocabularies/DS_OAI_COMPATIBILITY.json)
### DS_OAI_FORMATS [🔗](https://github.com/EOSC-Lot-1/een-resource-catalogue-docs/blob/eosc/vocabularies/DS_OAI_FORMATS.json)
### DS_PROTOCOL [🔗](https://github.com/EOSC-Lot-1/een-resource-catalogue-docs/blob/eosc/vocabularies/DS_PROTOCOL.json)
### DS_PERSISTENT_IDENTITY_SCHEME [🔗](https://github.com/EOSC-Lot-1/een-resource-catalogue-docs/blob/eosc/vocabularies/DS_PERSISTENT_IDENTITY_SCHEME.json)
### DS_RESEARCH_ENTITY_TYPE [🔗](https://github.com/EOSC-Lot-1/een-resource-catalogue-docs/blob/eosc/vocabularies/DS_RESEARCH_ENTITY_TYPE.json)
### ENDPOINT_TYPE [🔗](https://github.com/EOSC-Lot-1/een-resource-catalogue-docs/blob/eosc/vocabularies/ENDPOINT_TYPE.json)
### ENROLLMENT_STATUS [🔗](https://github.com/EOSC-Lot-1/een-resource-catalogue-docs/blob/eosc/vocabularies/ENROLLMENT_STATUS.json)
### FUNDING_BODY [🔗](https://github.com/EOSC-Lot-1/een-resource-catalogue-docs/blob/eosc/vocabularies/FUNDING_BODY.json)
### FUNDING_PROGRAM [🔗](https://github.com/EOSC-Lot-1/een-resource-catalogue-docs/blob/eosc/vocabularies/FUNDING_PROGRAM.json)
### GEOGRAPHIC_LOCATION [🔗](https://github.com/EOSC-Lot-1/een-resource-catalogue-docs/blob/eosc/vocabularies/GEOGRAPHIC_LOCATION.json)
### INTEGRATION_STATUS [🔗](https://github.com/EOSC-Lot-1/een-resource-catalogue-docs/blob/eosc/vocabularies/INTEGRATION_STATUS.json)
### IR_EOSC_GUIDELINE_TYPE [🔗](https://github.com/EOSC-Lot-1/een-resource-catalogue-docs/blob/eosc/vocabularies/IR_EOSC_GUIDELINE_TYPE.json)
### IR_IDENTIFIER_TYPE [🔗](https://github.com/EOSC-Lot-1/een-resource-catalogue-docs/blob/eosc/vocabularies/IR_IDENTIFIER_TYPE.json)
### IR_NAME_TYPE [🔗](https://github.com/EOSC-Lot-1/een-resource-catalogue-docs/blob/eosc/vocabularies/IR_NAME_TYPE.json)
### IR_RESOURCE_TYPE_GENERAL [🔗](https://github.com/EOSC-Lot-1/een-resource-catalogue-docs/blob/eosc/vocabularies/IR_RESOURCE_TYPE_GENERAL.json)
### IR_STATUS [🔗](https://github.com/EOSC-Lot-1/een-resource-catalogue-docs/blob/eosc/vocabularies/IR_STATUS.json)
### LANGUAGE [🔗](https://github.com/EOSC-Lot-1/een-resource-catalogue-docs/blob/eosc/vocabularies/LANGUAGE.json)
### LIFE_CYCLE_STATUS [🔗](https://github.com/EOSC-Lot-1/een-resource-catalogue-docs/blob/eosc/vocabularies/LIFE_CYCLE_STATUS.json)
### MARKETPLACE_LOCATION [🔗](https://github.com/EOSC-Lot-1/een-resource-catalogue-docs/blob/eosc/vocabularies/MARKETPLACE_LOCATION.json)
### MONITORING_MONITORED_BY [🔗](https://github.com/EOSC-Lot-1/een-resource-catalogue-docs/blob/eosc/vocabularies/MONITORING_MONITORED_BY.json)
### MONITORING_SERVICE_TYPE [🔗](https://github.com/EOSC-Lot-1/een-resource-catalogue-docs/blob/eosc/vocabularies/MONITORING_SERVICE_TYPE.json)
### NODE_TYPE [🔗](https://github.com/EOSC-Lot-1/een-resource-catalogue-docs/blob/eosc/vocabularies/NODE_TYPE.json)
### ORDER_TYPE [🔗](https://github.com/EOSC-Lot-1/een-resource-catalogue-docs/blob/eosc/vocabularies/ORDER_TYPE.json)
### PROVIDER_AREA_OF_ACTIVITY [🔗](https://github.com/EOSC-Lot-1/een-resource-catalogue-docs/blob/eosc/vocabularies/PROVIDER_AREA_OF_ACTIVITY.json)
### PROVIDER_ESFRI_DOMAIN [🔗](https://github.com/EOSC-Lot-1/een-resource-catalogue-docs/blob/eosc/vocabularies/PROVIDER_ESFRI_DOMAIN.json)
### PROVIDER_ESFRI_TYPE [🔗](https://github.com/EOSC-Lot-1/een-resource-catalogue-docs/blob/eosc/vocabularies/PROVIDER_ESFRI_TYPE.json)
### PROVIDER_HOSTING_LEGAL_ENTITY [🔗](https://github.com/EOSC-Lot-1/een-resource-catalogue-docs/blob/eosc/vocabularies/PROVIDER_HOSTING_LEGAL_ENTITY.json)
### PROVIDER_LEGAL_STATUS [🔗](https://github.com/EOSC-Lot-1/een-resource-catalogue-docs/blob/eosc/vocabularies/PROVIDER_LEGAL_STATUS.json)
### PROVIDER_LIFE_CYCLE_STATUS [🔗](https://github.com/EOSC-Lot-1/een-resource-catalogue-docs/blob/eosc/vocabularies/PROVIDER_LIFE_CYCLE_STATUS.json)
### PROVIDER_MERIL_SCIENTIFIC_DOMAIN [🔗](https://github.com/EOSC-Lot-1/een-resource-catalogue-docs/blob/eosc/vocabularies/PROVIDER_MERIL_SCIENTIFIC_DOMAIN.json)
### PROVIDER_MERIL_SCIENTIFIC_SUBDOMAIN [🔗](https://github.com/EOSC-Lot-1/een-resource-catalogue-docs/blob/eosc/vocabularies/PROVIDER_MERIL_SCIENTIFIC_SUBDOMAIN.json)
### PROVIDER_NETWORK [🔗](https://github.com/EOSC-Lot-1/een-resource-catalogue-docs/blob/eosc/vocabularies/PROVIDER_NETWORK.json)
### PROVIDER_SOCIETAL_GRAND_CHALLENGE [🔗](https://github.com/EOSC-Lot-1/een-resource-catalogue-docs/blob/eosc/vocabularies/PROVIDER_SOCIETAL_GRAND_CHALLENGE.json)
### PROVIDER_STATE [🔗](https://github.com/EOSC-Lot-1/een-resource-catalogue-docs/blob/eosc/vocabularies/PROVIDER_STATE.json)
### PROVIDER_STRUCTURE_TYPE [🔗](https://github.com/EOSC-Lot-1/een-resource-catalogue-docs/blob/eosc/vocabularies/PROVIDER_STRUCTURE_TYPE.json)
### REGION [🔗](https://github.com/EOSC-Lot-1/een-resource-catalogue-docs/blob/eosc/vocabularies/REGION.json)
### RELATED_PLATFORM [🔗](https://github.com/EOSC-Lot-1/een-resource-catalogue-docs/blob/eosc/vocabularies/RELATED_PLATFORM.json)
### RESEARCH_CATEGORY [🔗](https://github.com/EOSC-Lot-1/een-resource-catalogue-docs/blob/eosc/vocabularies/RESEARCH_CATEGORY.json)
### RESOURCE_STATUS [🔗](https://github.com/EOSC-Lot-1/een-resource-catalogue-docs/blob/eosc/vocabularies/RESOURCE_STATUS.json)
### RESOURCE_TYPE [🔗](https://github.com/EOSC-Lot-1/een-resource-catalogue-docs/blob/eosc/vocabularies/RESOURCE_TYPE.json)
### SCIENTIFIC_DOMAIN [🔗](https://github.com/EOSC-Lot-1/een-resource-catalogue-docs/blob/eosc/vocabularies/SCIENTIFIC_DOMAIN.json)
### SCIENTIFIC_SUBDOMAIN [🔗](https://github.com/EOSC-Lot-1/een-resource-catalogue-docs/blob/eosc/vocabularies/SCIENTIFIC_SUBDOMAIN.json)
### SEMANTIC_RELATIONSHIP [🔗](https://github.com/EOSC-Lot-1/een-resource-catalogue-docs/blob/eosc/vocabularies/SEMANTIC_RELATIONSHIP.json)
### SERVICE_CATEGORY [🔗](https://github.com/EOSC-Lot-1/een-resource-catalogue-docs/blob/eosc/vocabularies/SERVICE_CATEGORY.json)
### SERVICE_TYPE [🔗](https://github.com/EOSC-Lot-1/een-resource-catalogue-docs/blob/eosc/vocabularies/SERVICE_TYPE.json)
### SUBCATEGORY [🔗](https://github.com/EOSC-Lot-1/een-resource-catalogue-docs/blob/eosc/vocabularies/SUBCATEGORY.json)
### SUPERCATEGORY [🔗](https://github.com/EOSC-Lot-1/een-resource-catalogue-docs/blob/eosc/vocabularies/SUPERCATEGORY.json)
### TARGET_USER [🔗](https://github.com/EOSC-Lot-1/een-resource-catalogue-docs/blob/eosc/vocabularies/TARGET_USER.json)
### TEMPLATE_STATE [🔗](https://github.com/EOSC-Lot-1/een-resource-catalogue-docs/blob/eosc/vocabularies/TEMPLATE_STATE.json)
### TOOL_LICENSE [🔗](https://github.com/EOSC-Lot-1/een-resource-catalogue-docs/blob/eosc/vocabularies/TOOL_LICENSE.json)
### TOOL_SECURITY_STATUS [🔗](https://github.com/EOSC-Lot-1/een-resource-catalogue-docs/blob/eosc/vocabularies/TOOL_SECURITY_STATUS.json)
### TOOL_TARGET_INFRASTRUCTURE [🔗](https://github.com/EOSC-Lot-1/een-resource-catalogue-docs/blob/eosc/vocabularies/TOOL_TARGET_INFRASTRUCTURE.json)
### TOOL_VULNERABILITIES [🔗](https://github.com/EOSC-Lot-1/een-resource-catalogue-docs/blob/eosc/vocabularies/TOOL_VULNERABILITIES.json)
### TRL [🔗](https://github.com/EOSC-Lot-1/een-resource-catalogue-docs/blob/eosc/vocabularies/TRL.json)
### TR_ACCESS_RIGHT [🔗](https://github.com/EOSC-Lot-1/een-resource-catalogue-docs/blob/eosc/vocabularies/TR_ACCESS_RIGHT.json)
### TR_CONTENT_RESOURCE_TYPE [🔗](https://github.com/EOSC-Lot-1/een-resource-catalogue-docs/blob/eosc/vocabularies/TR_CONTENT_RESOURCE_TYPE.json)
### TR_DCMI_TYPE [🔗](https://github.com/EOSC-Lot-1/een-resource-catalogue-docs/blob/eosc/vocabularies/TR_DCMI_TYPE.json)
### TR_EXPERTISE_LEVEL [🔗](https://github.com/EOSC-Lot-1/een-resource-catalogue-docs/blob/eosc/vocabularies/TR_EXPERTISE_LEVEL.json)
### TR_QUALIFICATION [🔗](https://github.com/EOSC-Lot-1/een-resource-catalogue-docs/blob/eosc/vocabularies/TR_QUALIFICATION.json)
### TR_URL_TYPE [🔗](https://github.com/EOSC-Lot-1/een-resource-catalogue-docs/blob/eosc/vocabularies/TR_URL_TYPE.json)
