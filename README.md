



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

---

## Table of Contents
1. [Controllers](#controllers)
    i. [Datasource Controller](#datasource-controller)
    ii. [Interoperability Record Controller](#interoperability-record-controller)
    iii. [Provider Controller](#provider-controller)
    iv. [Service Controller](#service-controller)
    v. [Training Resource Controller](#training-resource-controller)
    vi. [Tool Controller](#tool-controller)
    vii. [Vocabulary Controller](#vocabulary-controller)
2. [Model](#model)
    i. [Datasource](#datasource-bundle)
    ii. [Interoperability Record](#interoperability-record-bundle)
    iii. [Provider](#provider-bundle)
    iv. [Service](#service-bundle)
    v. [Training Resource](#training-resource-bundle)
    vi. [Tool](#tool-bundle)
    vii. [Vocabulary](#vocabulary)
    viii. [Miscellaneous](#miscellaneous)
3. [List of Vocabularies](#list-of-vocabularies)
4. [Data Validation](#data-validation)

---

## Controllers

     
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
    - Returns the Datasource with the given id.
      ```diff
      /datasources/{prefix}/{suffix}
      Params:
        prefix: String [required]
        suffix: String [required]
      ```
    - Filter a list of Datasources based on a set of filters.
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
      
  - POST
    - Creates a new Datasource.
      ```diff
      /datasources
      Body:
        Datasource JSON [required]
      ```
        
  - PUT
    - Updates a specific Datasource.
      ```diff
      /datasources
      Body:
        Datasource JSON [required]
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
| `status`               | `String`       | No       | No     | Provides information about the resource status.            |
| `resourceOrganisationGroupID`               | `String`       | No       | No     |ID of the provider's organization
| `nodeId`               | `String`       | No       | Yes     |ID of the node the resource belongs
| `metadata`             | `Metadata`     | No       | Yes    | Additional metadata for the resource.                      |
| `loggingInfo`          | `LoggingInfo`  | No       | No     | Contains details about resource updates.                   |
| `latestOnboardingInfo` | `LoggingInfo`  | No       | No     | Details of the latest onboarding action.                   |
| `softwareRepository`   | `Boolean`      | No       | Yes     | Indicates whether the datasource is a software repository. |
| `originalOpenAIREId`   | `Boolean`      | No       | Yes     | Original OpenAIRE ID, if datasource already exists in the OpenAIRE Catalogue. |
| `oaiPmhInfo`           | `OaiPmhInfo`   | No      | Yes    | Metadata related to oai-pmh.                           |
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
| `jurisdiction`         | `String`       | Yes      | Yes    | Jurisdiction where the datasource operates.                 |
| `datasourceClassification` | `String`   | Yes      | Yes    | Classification of the datasource.                           |
| `researchEntityTypes`  | `List<String>` | No       | Yes    | List of research entity types related to the datasource.    |
| `thematic`             | `Boolean`      | Yes      | Yes    | Indicates if the datasource is thematic.                    |
| `researchProductLicensings` | `List<ResearchProductLicensing>` | No | Yes | List of research product licensing details.                 |
| `researchProductAccessPolicies` | `List<String>` | No | Yes | List of research product access policies.                   |
| `researchProductMetadataLicensing` | `ResearchProductMetadataLicensing` | No | Yes | Metadata licensing details for research products.           |
| `researchProductMetadataAccessPolicies` | `List<String>` | No | Yes | List of research product metadata access policies.          |
| `harvestable`          | `Boolean`      | No       | Yes    | Indicates if the datasource is harvestable.                 |


##### OAIPMHInfo

| Field                  | Type           | Required | Public | Description                                                 |
|------------------------|----------------|----------|--------|-------------------------------------------------------------|
| `protocol`                   | `String`       | No | Yes    | Protocol used for OAI-PMH.                       |
| `baseUrl`                   | `String`       | No | Yes    | Url of OAI-PMH endpoint.                       |
| `sets`                   | `List<String>`       | No | Yes    | OAI-PMH sets.                       |
| `format`                   | `String`       | No | Yes    | OAI format.                       |
| `compatibility`                   | `String`       | No | Yes    | Unique identifier for the datasource.                       |
| `openAIRECompliance`            | `String`       | No | Yes    | Indicates if resource is compliant with openAIRE specifications.                   |
| `repositoryIdentifier`           | `Identifier`       | No | Yes    | Identifier for the repository.          
| `alternativeIdentifiers`                   | `List<Identifier>`       | No | Yes    | Alternative identifiers.                  |


##### PersistentIdentitySystem

| Field                  | Type           | Required | Public | Description                                                 |
|------------------------|----------------|----------|--------|-------------------------------------------------------------|
| `persistentIdentityEntityType`        | `String`         |Yes              | Yes      | Type of the persistent identity entity.           |
| `persistentIdentityEntityTypeSchemes` | `List<String>`     |Yes            | Yes       | Schemes for the persistent identity entity types. |

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
        "protocol": "oai",
        "baseUrl": "https://example.com/oai/request",
        "sets": [
            "set1",
            "set2"
        ],
        "format": "oai dc",
        "compatibility": "not compatible",
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
                "persistentIdentityEntityType": "Type1",
                "persistentIdentityEntityTypeSchemes": [
                    "Scheme1",
                    "Scheme2"
                ]
            }
        ],
        "jurisdiction": "Country X",
        "datasourceClassification": "Scientific database",
        "researchEntityTypes": [
            "Type1",
            "Type2"
        ],
        "thematic": true,
        "researchProductLicensings": [
            {
                "researchProductLicenseName": "License1",
                "researchProductLicenseURL": "https://example.com/license1"
            }
        ],
        "researchProductAccessPolicies": [
            "Policy1",
            "Policy2"
        ],
        "researchProductMetadataLicensing": {
            "researchProductMetadataLicenseName": "Metadata License1",
            "researchProductMetadataLicenseURL": "https://example.com/metadata-license1"
        },
        "researchProductMetadataAccessPolicies": [
            "MetadataPolicy1",
            "MetadataPolicy2"
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
| `status`               | `String`       | No       | No     | Provides information about the resource status.            |
| `metadata`             | `Metadata`     | No       | Yes    | Additional metadata for the resource.       
| `resourceOrganisationGroupID`    | `String`       | No       | No     |ID of the provider's organization               |
| `loggingInfo`          | `LoggingInfo`  | No       | No     | Contains details about resource updates.                   |
| `latestOnboardingInfo` | `LoggingInfo`  | No       | No     | Details of the latest onboarding action.                      |
| `latestUpdateInfo` | `LoggingInfo`  | No       | No     | Details of the latest update action.                  |
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
| `status`                 | `String`                      | Yes   | Yes   | Current status of the interoperability record.                                   |
| `domain`                 | `String`                      | No    | Yes   | Domain to which the record pertains.                                             |
| `eoscGuidelineType`      | `String`                      | Yes   | Yes   | Type of EOSC (European Open Science Cloud) guideline associated with the record. |
| `eoscIntegrationOptions` | `List<String>`                | No     | Yes  | Options for integrating the record into EOSC.                                    |
| `alternativeIdentifiers` | `List<AlternativeIdentifier>` | No     | Yes  | Alternative identifiers for the record.                                          |

#### Nested Objects

##### IdentifierInfo

| Field            | Type     | Required | Description                                      |
|------------------|----------|----------|--------------------------------------------------|
| `identifier`     | `String` | Yes      | Main identifier for the interoperability record. |
| `identifierType` | `String` | Yes      | Type of the identifier, e.g., DOI, Handle.       |

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
| `nameType`    | `String` | Yes      | Type of name, e.g., personal, organizational. |

##### CreatorAffiliationInfo

| Field                   | Type     | Description                             |
|-------------------------|----------|-----------------------------------------|
| `affiliation`           | `String` | Name of the affiliation of the creator. |
| `affiliationIdentifier` | `String` | Identifier for the affiliation, if any. |

##### ResourceTypeInfo

| Field                 | Type     | Required | Description                                         |
|-----------------------|----------|----------|-----------------------------------------------------|
| `resourceType`        | `String` | Yes      | Specific type of the resource, e.g., dataset, tool. |
| `resourceTypeGeneral` | `String` | Yes      | General category of the resource type.              |

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

##### AlternativeIdentifier

| Field   | Type     | Description                                      |
|---------|----------|--------------------------------------------------|
| `type`  | `String` | Type of alternative identifier, e.g., DOI, ISBN. |
| `value` | `String` | Value of the alternative identifier.             |

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
        "catalogueId": "catalogue_001",
        "providerId": "provider_001",
        "identifierInfo": {
            "identifier": "10.1234/interop",
            "identifierType": "DOI"
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
        "status": "Active",
        "domain": "Data Science",
        "eoscGuidelineType": "EOSC Interoperability",
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
| `status`               | `String`       | No       | No     | Provides information about the resource status.            |
| `metadata`             | `Metadata`     | No       | Yes    | Additional metadata for the resource.       
| `resourceOrganisationGroupID`    | `String`       | No       | No     |ID of the provider's organization               |
| `loggingInfo`          | `LoggingInfo`  | No       | No     | Contains details about resource updates.                   |
| `latestOnboardingInfo` | `LoggingInfo`  | No       | No     | Details of the latest onboarding action.                      |
| `latestUpdateInfo` | `LoggingInfo`  | No       | No     | Details of the latest update action.                  |
| `provider`           | `Provider`   | Yes      | Yes    | Metadata of the actual resource.                           |


### Provider

| Field                     | Type                       | Required |Public | Description                                                                                       |
|---------------------------|----------------------------|----------|----|-----------------------------------------------------------------------------------------------|
| `id`                      | `String`                      | auto-gen |Yes      | Unique identifier for the provider.                                                               |
| `abbreviation`            | `String`                      | Yes      | Yes      |Abbreviation of the provider's name.                                                              |
| `name`                    | `String`                      | Yes      | Yes      |Full name of the provider.                                                                        |
| `website`                 | `URL`                         | Yes      |Yes      | URL of the provider's website.                                                                    |
| `legalEntity`             | `boolean`                     | Yes      | Yes      |Indicates if the provider is a legal entity.                                                      |
| `legalStatus`             | `String`                      | No       | Yes      |Legal status of the provider.                                                                     |
| `hostingLegalEntity`      | `String`                      | No       |Yes      | Hosting legal entity responsible for the provider.                                                |
| `alternativeIdentifiers`  | `List<AlternativeIdentifier>` | No       |Yes      | List of alternative identifiers for the provider.                                                 |
| `description`             | `String`                      | Yes      | Yes      |Description of the provider.                                                                      |
| `logo`                    | `URL`                         | Yes      |Yes      | URL of the provider's logo.                                                                       |
| `multimedia`              | `List<MultimediaPair>`        | No       | Yes      |List of multimedia items associated with the provider.                                            |
| `scientificDomains`       | `List<ServiceProviderDomain>` | No       | Yes      |Scientific domains related to the provider's services.                                            |
| `tags`                    | `List<String>`                | No       | Yes      |Tags associated with the provider.                                                                |
| `structureTypes`          | `List<String>`                | No       | Yes      |Types of structures associated with the provider.                                                 |
| `location`                | `ProviderLocation`            | Yes      | Yes      |Physical location details of the provider.                                                        |
| `mainContact`             | `ProviderMainContact`         | Yes      | No      |Main contact information for the provider.                                                        |
| `publicContacts`          | `List<ProviderPublicContact>` | Yes      |Yes      | List of public contacts for the provider.                                                         |
| `lifeCycleStatus`         | `String`                      | No       | Yes      |Current lifecycle status of the provider.                                                         |
| `certifications`          | `List<String>`                | No       | Yes      |List of certifications held by the provider.                                                      |
| `participatingCountries`  | `List<String>`                | No       | Yes      |List of countries participating in the provider's services.                                       |
| `affiliations`            | `List<String>`                | No       | Yes      |List of affiliations related to the provider.                                                     |
| `networks`                | `List<String>`                | No       | Yes      |Networks associated with the provider.                                                                 |
| `esfriDomains`            | `List<String>`                | No       |Yes      | ESFRI (European Strategy Forum on Research Infrastructures) domains associated with the provider. |
| `esfriType`               | `String`                      | No       |Yes      | ESFRI type classification of the provider.                                                        |
| `merilScientificDomains`  | `List<ProviderMerilDomain>`   | No       | Yes      |MERIL scientific domains associated with the provider.                                            |
| `areasOfActivity`         | `List<String>`                | No       | Yes      |Areas of activity related to the provider's services.                                             |
| `societalGrandChallenges` | `List<String>`                | No       |Yes      | Societal grand challenges addressed by the provider.                                              |
| `nationalRoadmaps`        | `List<String>`                | No       |Yes      | National roadmaps associated with the provider.                                                   |
| `users`                   | `List<User>`                  | Yes      |No      | List of users associated with the provider.                                                       |

#### Nested Objects

##### AlternativeIdentifier

| Field   | Type     | Required | Description                          |
|---------|----------|----------|--------------------------------------|
| `type`  | `String` | No       | Type of the alternative identifier.  |
| `value` | `String` | No       | Value of the alternative identifier. |

##### MultimediaPair

| Field            | Type     | Required | Description                      |
|------------------|----------|----------|----------------------------------|
| `multimediaURL`  | `URL`    | Yes      | URL to the multimedia resource.  |
| `multimediaName` | `String` | No       | Name of the multimedia resource. |

##### ServiceProviderDomain

| Field                 | Type     | Required | Description                                    |
|-----------------------|----------|----------|------------------------------------------------|
| `scientificDomain`    | `String` | Yes      | Scientific domain related to the catalogue.    |
| `scientificSubdomain` | `String` | No       | Scientific subdomain related to the catalogue. |

##### ProviderLocation

| Field                 | Type      | Required | Description                                     |
|-----------------------|-----------|----------|-------------------------------------------------|
| `streetNameAndNumber` | `String`  | Yes      | Street address of the catalogue's location.     |
| `postalCode`          | `String`  | Yes      | Postal code of the catalogue's location.        |
| `city`                | `String`  | Yes      | City where the catalogue is located.            |
| `region`              | `String`  | No       | Region or state where the catalogue is located. |
| `country`             | `String`  | Yes      | Country where the catalogue is located.         |

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
| `merilScientificDomain`    | `String` | Yes      | MERIL scientific domain related to the provider.    |
| `merilScientificSubdomain` | `String` | No       | MERIL scientific subdomain related to the provider. |

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
            "actionType": "offboarded"
        }
    ],
    "status": "offboarded",
    "resourceOrganisationGroupID": "groupId",
    "id": "provider_001",
    "provider": {
        "id": "provider_001",
        "abbreviation": "PROV",
        "name": "Sample Provider",
        "website": "https://example.com",
        "legalEntity": true,
        "legalStatus": "Non-profit",
        "hostingLegalEntity": "Hosting Entity",
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
                "scientificDomain": "Science",
                "scientificSubdomain": "Physics"
            }
        ],
        "tags": [
            "science",
            "research"
        ],
        "structureTypes": [
            "type1",
            "type2"
        ],
        "location": {
            "streetNameAndNumber": "123 Main St",
            "postalCode": "12345",
            "city": "Sample City",
            "region": "Sample Region",
            "country": "Sample Country"
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
        "lifeCycleStatus": "Active",
        "certifications": [
            "ISO9001",
            "ISO27001"
        ],
        "participatingCountries": [
            "Country1",
            "Country2"
        ],
        "affiliations": [
            "Affiliation1",
            "Affiliation2"
        ],
        "networks": [
            "Network1",
            "Network2"
        ],
        "catalogueId": "catalogue_001",
        "esfriDomains": [
            "Domain1",
            "Domain2"
        ],
        "esfriType": "Type1",
        "merilScientificDomains": [
            {
                "merilScientificDomain": "MERIL Domain",
                "merilScientificSubdomain": "Subdomain"
            }
        ],
        "areasOfActivity": [
            "Activity1",
            "Activity2"
        ],
        "societalGrandChallenges": [
            "Challenge1",
            "Challenge2"
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
| `status`               | `String`       | No       | No     | Provides information about the resource status.            |
| `metadata`             | `Metadata`     | No       | Yes    | Additional metadata for the resource.       
| `resourceOrganisationGroupID`    | `String`       | No       | No     |ID of the provider's organization               |
| `loggingInfo`          | `LoggingInfo`  | No       | No     | Contains details about resource updates.                   |
| `latestOnboardingInfo` | `LoggingInfo`  | No       | No     | Details of the latest onboarding action.                      |
| `latestUpdateInfo` | `LoggingInfo`  | No       | No     | Details of the latest update action.                  |      |
| `sites`             | `List<Site>`     | No       | Yes    | Information on the service's sites.    
| `service`           | `Service`   | Yes      | Yes    | Metadata of the actual resource.                           |
| `nodeId`                   | `String`       | No| Yes    | ID of the node the resource belongs

### Service

| Field                  | Type           | Required | Public | Description                                                 |
|------------------------|----------------|----------|--------|-------------------------------------------------------------|
| `id`                          | `String`                      | auto-gen |  Yes    |Unique identifier for the service.                                        |
| `abbreviation`                | `String`                      | Yes      | Yes    | Abbreviation of the service's name.                                       |
| `name`                        | `String`                      | Yes      |  Yes    |Full name of the service.                                                 |
| `resourceOrganisation`        | `String`                      | Yes      | Yes    | Name of the resource organization providing the service.                  |
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
| `targetUsers`                 | `List<String>`                | Yes      |  Yes    |List of target users for the service.                                     |
| `accessTypes`                 | `List<String>`                | No       | Yes    | Types of access provided by the service (e.g., open, restricted).         |
| `accessModes`                 | `List<String>`                | No       |  Yes    |Modes of access available for the service (e.g., online, in-person).      |
| `tags`                        | `List<String>`                | No       |  Yes    |Tags associated with the service.                                         |
| `horizontalService`           | `Boolean`                     | No       |  Yes    |Indicates if the service is a horizontal service.                         |
| `serviceCategories`           | `List<String>`                | No       | Yes    | List of service categories associated with the service.                   |
| `marketplaceLocations`        | `List<String>`                | No       | Yes    | List of marketplace locations where the service is available.             |
| `geographicalAvailabilities`  | `List<String>`                | Yes      |  Yes    |List of geographical availabilities of the service.                       |
| `languageAvailabilities`      | `List<String>`                | Yes      |  Yes    |List of language availabilities of the service.                           |
| `resourceGeographicLocations` | `List<String>`                | No       | Yes    | List of locations where the service resources are geographically located. |
| `mainContact`                 | `ServiceMainContact`          | Yes      | No    | Main contact information for the service.                                 |
| `publicContacts`              | `List<ServicePublicContact>`  | Yes      |  Yes    |List of public contacts for the service.                                  |
| `helpdeskEmail`               | `String`                      | Yes      |  Yes    |Email address for the service's helpdesk.                                 |
| `securityContactEmail`        | `String`                      | Yes      | Yes    | Email address for security contact.                                       |
| `trl`                         | `String`                      | Yes      |  Yes    |Technology Readiness Level of the service.                                |
| `lifeCycleStatus`             | `String`                      | No       |  Yes    |Life cycle status of the service.                                         |
| `certifications`              | `List<String>`                | No       |  Yes    |List of certifications related to the service.                            |
| `standards`                   | `List<String>`                | No       | Yes    | Standards that the service complies with.                                 |
| `openSourceTechnologies`      | `List<String>`                | No       |  Yes    |List of open-source technologies used in the service.                     |
| `version`                     | `String`                      | No       | Yes    | Current version of the service.                                           |
| `lastUpdate`                  | `Date`                        | No       | No    | Date and time of the last update.                                         |
| `changeLog`                   | `List<String>`                | No       | No    | List of changes made to the service.                                      |
| `requiredResources`           | `List<String>`                | No       | Yes    | List of required resources for the service.                               |
| `relatedResources`            | `List<String>`                | No       | Yes    | List of related resources linked to the service.                          |
| `relatedPlatforms`            | `List<String>`                | No       | Yes    | List of related platforms connected to the service.                        |
| `fundingBody`                 | `List<String>`                | No       | Yes    | List of funding bodies supporting the service.                            |
| `fundingPrograms`             | `List<String>`                | No       |  Yes    |List of funding programs related to the service.                          |
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
| `orderType`                   | `String`                      | Yes      |  Yes    |Type of order required for the service.                                   |
| `order`                       | `URL`                         | No       |  Yes    |URL for ordering the service.                                             |
| `paymentModel`                | `URL`                         | No       |  Yes    |URL of the payment model information.                                     |
| `pricing`                     | `URL`                         | No       | Yes    | URL of the pricing details.                                               |

#### Nested Objects

##### AlternativeIdentifier

| Field   | Type     | Required | Description                          |
|---------|----------|----------|--------------------------------------|
| `type`  | `String` | No       | Type of the alternative identifier.  |
| `value` | `String` | No       | Value of the alternative identifier. |

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

##### ServiceProviderDomain

| Field                 | Type     | Required | Description                    |
|-----------------------|----------|----------|--------------------------------|
| `scientificDomain`    | `String` | Yes      | Main scientific domain.        |
| `scientificSubdomain` | `String` | Yes      | Specific scientific subdomain. |

##### ServiceCategory

| Field         | Type     | Required | Description                 |
|---------------|----------|----------|-----------------------------|
| `category`    | `String` | Yes      | Category of the service.    |
| `subcategory` | `String` | No       | Subcategory of the service. |

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

##### Site

| Field   | Type     | Required |  Description                          |
|---------|----------|----------|--------------------------------------|
| `name`  | `String` | No       | Name of the site.  |
| `endpoints` | `List<Endpoints>` | No       | List of the endpoints. |

##### Endpoint

| Field   | Type     | Required |  Description                          |
|---------|----------|----------|--------------------------------------|
| `name`  | `String` | No       | Name of the endpoint.  |
| `type` | `String` | No       | Type of the endpoint. |
| `monitoringServiceType` | `String` | No       | Type of the endpoint regarding monitoring service. |
| `url` | `String` | No       | URL of the endpoint. |

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
                    "type": "endpoint_type",
                    "url": "endpoint_url"
                }
            ]
        }
    ],
    "resourceOrganisationGroupID": "groupId",
    "service": {
        "id": "service_001",
        "abbreviation": "SERV",
        "name": "Sample Service",
        "resourceOrganisation": "Sample Organisation",
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
                "scientificDomain": "Biology",
                "scientificSubdomain": "Molecular Biology"
            }
        ],
        "categories": [
            {
                "category": "Category1",
                "subcategory": "Subcategory1"
            }
        ],
        "targetUsers": [
            "Researchers",
            "Students"
        ],
        "accessTypes": [
            "Open",
            "Restricted"
        ],
        "accessModes": [
            "Online",
            "In-person"
        ],
        "tags": [
            "innovation",
            "technology"
        ],
        "horizontalService": true,
        "serviceCategories": [
            "CategoryA",
            "CategoryB"
        ],
        "marketplaceLocations": [
            "Location1",
            "Location2"
        ],
        "geographicalAvailabilities": [
            "Global"
        ],
        "languageAvailabilities": [
            "English",
            "French"
        ],
        "resourceGeographicLocations": [
            "Location A",
            "Location B"
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
        "trl": "TRL 7",
        "lifeCycleStatus": "Active",
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
            "Platform1",
            "Platform2"
        ],
        "catalogueId": "catalogue_001",
        "fundingBody": [
            "Funding Body1",
            "Funding Body2"
        ],
        "fundingPrograms": [
            "Program1",
            "Program2"
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
        "orderType": "Online",
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
| `status`               | `String`       | No       | No     | Provides information about the resource status.            |
| `metadata`             | `Metadata`     | No       | Yes    | Additional metadata for the resource.       
| `resourceOrganisationGroupID`    | `String`       | No       | No     |ID of the provider's organization               |
| `loggingInfo`          | `LoggingInfo`  | No       | No     | Contains details about resource updates.                   |
| `latestOnboardingInfo` | `LoggingInfo`  | No       | No     | Details of the latest onboarding action.                      |
| `latestUpdateInfo` | `LoggingInfo`  | No       | No     | Details of the latest update action.                  |      |
| `trainingResource`           | `TrainingResource`   | Yes      | Yes    | Metadata of the actual resource.       
                    |
### Training Resource

| Field                        | Type                          | Required | Public| Description                                                                       |
|------------------------------|-------------------------------|----------|----|-------------------------------------------------------------------------------|
| `id`                         | `String`                      | auto-gen| Yes | Unique identifier for the training resource.                                      |
| `title`                      | `String`                      | Yes    | Yes  | Title of the training resource.                                                   |
| `resourceOrganisation`       | `String`                      | Yes   | Yes   | Organisation providing the resource.                                              |
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

##### AlternativeIdentifier

| Field   | Type     | Required | Description                          |
|---------|----------|----------|--------------------------------------|
| `type`  | `String` | No       | Type of the alternative identifier.  |
| `value` | `String` | No       | Value of the alternative identifier. |

##### ServiceProviderDomain

| Field                 | Type     | Required | Description                    |
|-----------------------|----------|----------|--------------------------------|
| `scientificDomain`    | `String` | Yes      | Main scientific domain.        |
| `scientificSubdomain` | `String` | Yes      | Specific scientific subdomain. |

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
| `status`               | `String`       | No       | No     | Provides information about the resource status.            |
| `metadata`             | `Metadata`     | No       | Yes    | Additional metadata for the resource.       
| `resourceOrganisationGroupID`    | `String`       | No       | No     |ID of the provider's organization.               |
| `loggingInfo`          | `LoggingInfo`  | No       | No     | Contains details about resource updates.                   |
| `latestOnboardingInfo` | `LoggingInfo`  | No       | No     | Details of the latest onboarding action.                      |
| `latestUpdateInfo` | `LoggingInfo`  | No       | No     | Details of the latest update action. 
| `security`           | `ToolSecurity`   | Yes      | Yes    | Security related metadata.                    |      |
| `contributorProvided`                | `Boolean`      | No       | No     | Indicates whether the resource is related to a Provider.
| `tool`           | `Tool`   | Yes      | Yes    | Metadata of the actual resource.       
                    |
### Tool

| Field                        | Type                          | Required | Public| Description                                                                       |
|------------------------------|-------------------------------|----------|----|-------------------------------------------------------------------------------|
| `id`                         | `String`                      | auto-gen| Yes | Unique identifier for the training resource.                                      |
| `name`                      | `String`                      | Yes    | Yes  | Name of the tool.                                                   |
| `resourceOrganisation`       | `String`                      | No   | Yes   | Name of the organisation providing the resource.                                              |
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
---

## List of Vocabularies
  - [ACCESS_MODE](https://github.com/madgeek-arc/resource-catalogue-docs/blob/master/vocabularies/ACCESS_MODE.json)
  - [ACCESS_TYPE](https://github.com/madgeek-arc/resource-catalogue-docs/blob/master/vocabularies/ACCESS_TYPE.json)
  - [CATALOGUE_STATE](https://github.com/madgeek-arc/resource-catalogue-docs/blob/master/vocabularies/CATALOGUE_STATE.json)
  - [CATEGORY](https://github.com/madgeek-arc/resource-catalogue-docs/blob/master/vocabularies/CATEGORY.json)
  - [COUNTRY](https://github.com/madgeek-arc/resource-catalogue-docs/blob/master/vocabularies/COUNTRY.json)
  - [CT_COMPATIBILITY](https://github.com/madgeek-arc/resource-catalogue-docs/blob/master/vocabularies/CT_COMPATIBILITY.json)
  - [CT_PROTOCOL](https://github.com/madgeek-arc/resource-catalogue-docs/blob/master/vocabularies/CT_PROTOCOL.json)
  - [DS_CLASSIFICATION](https://github.com/madgeek-arc/resource-catalogue-docs/blob/master/vocabularies/DS_CLASSIFICATION.json)
  - [DS_COAR_ACCESS_RIGHTS_1_0](https://github.com/madgeek-arc/resource-catalogue-docs/blob/master/vocabularies/DS_COAR_ACCESS_RIGHTS_1_0.json)
  - [DS_JURISDICTION](https://github.com/madgeek-arc/resource-catalogue-docs/blob/master/vocabularies/DS_JURISDICTION.json)
  - [DS_PERSISTENT_IDENTITY_SCHEME](https://github.com/madgeek-arc/resource-catalogue-docs/blob/master/vocabularies/DS_PERSISTENT_IDENTITY_SCHEME.json)
  - [DS_RESEARCH_ENTITY_TYPE](https://github.com/madgeek-arc/resource-catalogue-docs/blob/master/vocabularies/DS_RESEARCH_ENTITY_TYPE.json)
  - [FUNDING_BODY](https://github.com/madgeek-arc/resource-catalogue-docs/blob/master/vocabularies/FUNDING_BODY.json)
  - [FUNDING_PROGRAM](https://github.com/madgeek-arc/resource-catalogue-docs/blob/master/vocabularies/FUNDING_PROGRAM.json)
  - [GEOGRAPHIC_LOCATION](https://github.com/madgeek-arc/resource-catalogue-docs/blob/master/vocabularies/GEOGRAPHIC_LOCATION.json)
  - [IR_EOSC_GUIDELINE_TYPE](https://github.com/madgeek-arc/resource-catalogue-docs/blob/master/vocabularies/IR_EOSC_GUIDELINE_TYPE.json)
  - [IR_IDENTIFIER_TYPE](https://github.com/madgeek-arc/resource-catalogue-docs/blob/master/vocabularies/IR_IDENTIFIER_TYPE.json)
  - [IR_NAME_TYPE](https://github.com/madgeek-arc/resource-catalogue-docs/blob/master/vocabularies/IR_NAME_TYPE.json)
  - [IR_RESOURCE_TYPE_GENERAL](https://github.com/madgeek-arc/resource-catalogue-docs/blob/master/vocabularies/IR_RESOURCE_TYPE_GENERAL.json)
  - [IR_STATUS](https://github.com/madgeek-arc/resource-catalogue-docs/blob/master/vocabularies/IR_STATUS.json)
  - [LANGUAGE](https://github.com/madgeek-arc/resource-catalogue-docs/blob/master/vocabularies/LANGUAGE.json)
  - [LIFE_CYCLE_STATUS](https://github.com/madgeek-arc/resource-catalogue-docs/blob/master/vocabularies/LIFE_CYCLE_STATUS.json)
  - [MARKETPLACE_LOCATION](https://github.com/madgeek-arc/resource-catalogue-docs/blob/master/vocabularies/MARKETPLACE_LOCATION.json)
  - [MONITORING_MONITORED_BY](https://github.com/madgeek-arc/resource-catalogue-docs/blob/master/vocabularies/MONITORING_MONITORED_BY.json)
  - [ORDER_TYPE](https://github.com/madgeek-arc/resource-catalogue-docs/blob/master/vocabularies/ORDER_TYPE.json)
  - [PROVIDER_AREA_OF_ACTIVITY](https://github.com/madgeek-arc/resource-catalogue-docs/blob/master/vocabularies/PROVIDER_AREA_OF_ACTIVITY.json)
  - [PROVIDER_ESFRI_DOMAIN](https://github.com/madgeek-arc/resource-catalogue-docs/blob/master/vocabularies/PROVIDER_ESFRI_DOMAIN.json)
  - [PROVIDER_ESFRI_TYPE](https://github.com/madgeek-arc/resource-catalogue-docs/blob/master/vocabularies/PROVIDER_ESFRI_TYPE.json)
  - [PROVIDER_HOSTING_LEGAL_ENTITY](https://github.com/madgeek-arc/resource-catalogue-docs/blob/master/vocabularies/PROVIDER_HOSTING_LEGAL_ENTITY.json)
  - [PROVIDER_LEGAL_STATUS](https://github.com/madgeek-arc/resource-catalogue-docs/blob/master/vocabularies/PROVIDER_LEGAL_STATUS.json)
  - [PROVIDER_LIFE_CYCLE_STATUS](https://github.com/madgeek-arc/resource-catalogue-docs/blob/master/vocabularies/PROVIDER_LIFE_CYCLE_STATUS.json)
  - [PROVIDER_MERIL_SCIENTIFIC_DOMAIN](https://github.com/madgeek-arc/resource-catalogue-docs/blob/master/vocabularies/PROVIDER_MERIL_SCIENTIFIC_DOMAIN.json)
  - [PROVIDER_MERIL_SCIENTIFIC_SUBDOMAIN](https://github.com/madgeek-arc/resource-catalogue-docs/blob/master/vocabularies/PROVIDER_MERIL_SCIENTIFIC_SUBDOMAIN.json)
  - [PROVIDER_NETWORK](https://github.com/madgeek-arc/resource-catalogue-docs/blob/master/vocabularies/PROVIDER_NETWORK.json)
  - [PROVIDER_SOCIETAL_GRAND_CHALLENGE](https://github.com/madgeek-arc/resource-catalogue-docs/blob/master/vocabularies/PROVIDER_SOCIETAL_GRAND_CHALLENGE.json)
  - [PROVIDER_STATE](https://github.com/madgeek-arc/resource-catalogue-docs/blob/master/vocabularies/PROVIDER_STATE.json)
  - [PROVIDER_STRUCTURE_TYPE](https://github.com/madgeek-arc/resource-catalogue-docs/blob/master/vocabularies/PROVIDER_STRUCTURE_TYPE.json)
  - [REGION](https://github.com/madgeek-arc/resource-catalogue-docs/blob/master/vocabularies/REGION.json)
  - [RELATED_PLATFORM](https://github.com/madgeek-arc/resource-catalogue-docs/blob/master/vocabularies/RELATED_PLATFORM.json)
  - [RESEARCH_CATEGORY](https://github.com/madgeek-arc/resource-catalogue-docs/blob/master/vocabularies/RESEARCH_CATEGORY.json)
  - [RESOURCE_STATE](https://github.com/madgeek-arc/resource-catalogue-docs/blob/master/vocabularies/RESOURCE_STATE.json)
  - [SCIENTIFIC_DOMAIN](https://github.com/madgeek-arc/resource-catalogue-docs/blob/master/vocabularies/SCIENTIFIC_DOMAIN.json)
  - [SCIENTIFIC_SUBDOMAIN](https://github.com/madgeek-arc/resource-catalogue-docs/blob/master/vocabularies/SCIENTIFIC_SUBDOMAIN.json)
  - [SEMANTIC_RELATIONSHIP](https://github.com/madgeek-arc/resource-catalogue-docs/blob/master/vocabularies/SEMANTIC_RELATIONSHIP.json)
  - [SERVICE_CATEGORY](https://github.com/madgeek-arc/resource-catalogue-docs/blob/master/vocabularies/SERVICE_CATEGORY.json)
  - [SERVICE_TYPE](https://github.com/madgeek-arc/resource-catalogue-docs/blob/master/vocabularies/SERVICE_TYPE.json)
  - [SUBCATEGORY](https://github.com/madgeek-arc/resource-catalogue-docs/blob/master/vocabularies/SUBCATEGORY.json)
  - [SUPERCATEGORY](https://github.com/madgeek-arc/resource-catalogue-docs/blob/master/vocabularies/SUPERCATEGORY.json)
  - [TARGET_USER](https://github.com/madgeek-arc/resource-catalogue-docs/blob/master/vocabularies/TARGET_USER.json)
  - [TEMPLATE_STATE](https://github.com/madgeek-arc/resource-catalogue-docs/blob/master/vocabularies/TEMPLATE_STATE.json)
  - [TRL](https://github.com/madgeek-arc/resource-catalogue-docs/blob/master/vocabularies/TRL.json)
  - [TR_ACCESS_RIGHT](https://github.com/madgeek-arc/resource-catalogue-docs/blob/master/vocabularies/TR_ACCESS_RIGHT.json)
  - [TR_CONTENT_RESOURCE_TYPE](https://github.com/madgeek-arc/resource-catalogue-docs/blob/master/vocabularies/TR_CONTENT_RESOURCE_TYPE.json)
  - [TR_DCMI_TYPE](https://github.com/madgeek-arc/resource-catalogue-docs/blob/master/vocabularies/TR_DCMI_TYPE.json)
  - [TR_EXPERTISE_LEVEL](https://github.com/madgeek-arc/resource-catalogue-docs/blob/master/vocabularies/TR_EXPERTISE_LEVEL.json)
  - [TR_QUALIFICATION](https://github.com/madgeek-arc/resource-catalogue-docs/blob/master/vocabularies/TR_QUALIFICATION.json)
  - [TR_URL_TYPE](https://github.com/madgeek-arc/resource-catalogue-docs/blob/master/vocabularies/TR_URL_TYPE.json)

---

## Data Validation
This project provides [LinkML](https://linkml.io/) schemas for validating your data. Users can validate their data files 
(e.g., YAML, JSON) against these schemas to ensure compliance with the defined structure, data types, and constraints. 
Simply provide your data and use LinkML’s built-in tools or Python libraries to run the validation process. Errors or 
mismatches will be reported to help you identify and fix issues.
  - [View All Available Schemas](https://github.com/madgeek-arc/resource-catalogue-docs/tree/master/linkml/schemas) to
    explore the structures and constraints defined for validation.
  - [Example Data Files](https://github.com/madgeek-arc/resource-catalogue-docs/tree/master/linkml/data) are provided to
    help you get started quickly and understand the expected format.

### Quick Guide (Linux based systems):
To validate your data against the provided LinkML schemas:
1. Install LinkML 
   `pip install linkml`
2. Download [schemas](https://github.com/madgeek-arc/resource-catalogue-docs/tree/master/linkml/schemas) folder
3. Create a folder for your data 
   `mkdir path/to/data`
4. Run the validation command 
   `linkml-validate -s path/to/schemas/schema.yaml path/to/data/data.yaml`f
