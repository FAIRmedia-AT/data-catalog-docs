<img src="assets/fairmedia-logo.png" width="30%">

# FairMedia Data Catalog Documentation

- [Specification](docs/fairmedia-spec.md)
- [Ontology](docs/fairmedia-ontology.ttl)
- [OpenAPI](docs/openapi.yaml)

## Usage

When the FairMedia Data Catalog is opened, you are first greeted with the start page. It currently displays all public datasets in a list. You can open these and view more detailed information about them. The detail page is divided into several tabs (General, Terms & Liabilities, Responsible AI, Distributions and Record Sets) to display the information more clearly.

To access further information, you have to log in. You will then see a list of all datasets created and another button next to the login button to create datasets.

<img src="docs/fairmedia-dataset-lifecycle.drawio.svg" alt="Dataset Lifecycle" width="100%">

Datasets have a lifecycle, which is visualized in the graphic above. After the dataset has been created, it is in draft mode. These datasets can be edited and deleted at any time. However, they are not displayed to people who are not logged in, as they are not publicly available. If you believe that the first version of the dataset is ready, you can publish it. In this mode, it can no longer be edited or deleted. You can only set the visibility (whether it is only visible internally or also publicly) and create a new version of the dataset. This is then back in draft mode and can be edited.

When editing or creating a dataset, you will find the same tabs as in the detail view. The individual form fields are provided with a small help text that offers further information about what should be entered in the respective field. The aim is to describe existing datasets as precisely as possible in order to make it easier for others who may want to use the dataset to decide whether it meets their requirements.

## Architecture

<img src="docs/fairmedia-c4-diagram.drawio.svg" alt="C4 Diagram FairMedia Data Catalog" width="100%">

The FairMedia Data Catalog provides two interfaces to the outside world. On the one hand, there is an API interface that provides various endpoints for managing datasets (for more detailed information, see [OpenAPI](docs/openapi.yaml)). For example, partners can extend their own software and access the FairMedia Data Catalog directly from there. On the other hand, a frontend is also provided, which can be used to manage datasets easily with a user interface. This also outputs JSON-LD, which releases linked data and can be found by crawlers. This linked data is structured according to the [FairMedia Specification](docs/fairmedia-spec.md).

Internally, everything is managed by a backend, which takes care of the API requests and has access to the database.

## Schema

The FairMedia schema is based on the dataset vocabulary of schema.org, the Croissant specification including the Croissant RAI (Responsible AI) specification and extends it with a few additional properties. In particular, legal information has been added.

### Croissant 🥐 by MLCommons

Croissant by [MLCommons](https://mlcommons.org) is a high-level format designed for machine learning (ML) datasets. It brings together four essential layers within a single file:

- **Metadata**: This includes a detailed description of the dataset, emphasizing responsible ML practices and aspects
- **Resources**: These are the raw data sources, which can be one or more files or other types of data origins
- **Structure**: This layer explains how the raw data is assembled and organized into data structures suitable for ML use
- **ML Semantics**: This details how the data is most commonly used in machine learning contexts

The primary aim of Croissant is to establish a standard dataset format that simplifies the process of finding and utilizing ML datasets. Additionally, it facilitates the development of tools that assist in the creation, understanding, and enhancement of ML datasets.

Croissant leverages schema.org and its `Dataset` vocabulary to improve dataset discoverability. It is already integrated into popular platforms such as Google Dataset Search, Kaggle, OpenML, Hugging Face and TensorFlow Datasets.

In our FairMedia Data Catalog, we utilize Croissant to provide datasets that come with comprehensive descriptions and are presented in a consistent and standardized format.

You can find more information about Croissant on the [official website](https://mlcommons.org/croissant) and on the [GitHub repository](https://github.com/mlcommons/croissant).

### What's missing?

Currently, Croissant covers only minimal legal information regarding datasets and is missing some other information that may be relevant. The following key aspects are missing:

- **Copyrights**: Details on the datasets copyrights and whether they are clearly resolved
- **Controllerships**: Information on joint or individual controllerships related to the dataset
- **Usage Rights**: Specifications on the rights to use the dataset
- **Data Anonymization**: Methods used for data anonymization, measures taken to protect the data and identification of personal data included in the dataset
- **Access Conditions**: Clarification on the conditions under which the dataset can be accessed
- **Versioning**: More information about what has changed in the version compared to the old version

### FairMedia Specification

To address these gaps, we have extended the Croissant specification, resulting in the [FairMedia Specification](docs/fairmedia-spec.md). The following additions were made:

<table>
  <tr>
    <td><code>changelog</code></td>
    <td>A detailed list of the changes to this version of the dataset with the reasons for the changes.</td>
  </tr>
  <tr>
    <td><code>dataSource</code></td>
    <td>Specification of the source of the dataset.</td>
  </tr>
  <tr>
    <td><code>dataUsageTerms</code></td>
    <td>Specifies the conditions under which the data set may be processed, including permitted commercial and non-commercial uses, text and data mining, etc.</td>
  </tr>
  <tr>
    <td><code>userRights</code></td>
    <td>Specific rights of users using the dataset, including permission to modify or redistribute datasets or the obligation to cite the source.</td>
  </tr>
  <tr>
    <td><code>dataProcessingTerms</code></td>
    <td>Description of the legal basis for the collection of personal data; definition of the legal basis for the provision and further processing of personal data.</td>
  </tr>
  <tr>
    <td><code>controllership</code></td>
    <td>Determination of controllership.</td>
  </tr>
  <tr>
    <td><code>jointControllerAgreementConcluded</code></td>
    <td>Has a Joint Controller Agreement (JCA) been concluded?</td>
  </tr>
  <tr>
    <td><code>liabilityClauses</code></td>
    <td>Description of the disclaimers and limitations of liability in connection with the use of the data in order to minimize legal risks for the data provider.</td>
  </tr>
  <tr>
    <td><code>indemnityClauses</code></td>
    <td>Conditions under which the user must indemnify the data provider, including a third-party provider in the event of legal disputes.</td>
  </tr>
  <tr>
    <td><code>copyright</code></td>
    <td>Provide a detailed description about the copyright of the datasets content.</td>
  </tr>
  <tr>
    <td><code>dataAnonymizationProtocol</code></td>
    <td>Description of the anonymization procedures used to protect the identity of individuals in the data.</td>
  </tr>
  <tr>
    <td><code>dataSecurityProtocol</code></td>
    <td>Description of the security measures taken to protect the data, including encryption, access controls and measures to ensure data integrity, including specific safeguards for different types of personal data including sensitive data (e.g. health data, sexual orientation).</td>
  </tr>
  <tr>
    <td><code>dataProtectionType</code></td>
    <td>Determining whether the data is anonymous/anonymized or personal data.</td>
  </tr>
  <tr>
    <td><code>personalData</code></td>
    <td>Description of the categories and types of personal data.</td>
  </tr>
</table>

## Next Steps

We plan to propose and contribute the FairMedia Specification and its extensions to the Croissant Specification.

We also want to improve access management, taking into account that some datasets can be downloaded directly from a URL, some datasets must be requested via a form, and other datasets require a contract to access.

In addition, we want to use the legal information provided to draw clearer conclusions so that users can easily identify the key considerations for using the dataset and understand how to access the dataset. Users could also receive guidance on whether a dataset fits their specific use case.
