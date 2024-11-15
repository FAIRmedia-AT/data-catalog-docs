<img src="assets/fairmedia-logo.png" width="30%">

# FairMedia Dataset Catalog Documentation

- [Specification](docs/fairmedia-spec.md)
- [Ontology](docs/fairmedia-ontology.ttl)
- [OpenAPI](docs/openapi.yaml)

## Usage

<img src="docs/fairmedia-dataset-lifecycle.drawio.svg" width="100%">

## Architektur

Der FairMedia Dataset Catalog besteht aus verschiedenen Komponenten und ist folgendermaßen aufgebaut. Zunächst gibt es das Backend, welches auf einem Server läuft und von der API Anfragen empfängt. Über diese API kann ein Partner Datasets anlegen, bearbeiten und löschen. Außerdem kann eine Liste aller Datasets oder aller öffetnlichen Datasets angefragt werden, oder alle Details zu einem spezifischen Dataset. Diese API Endpunkte sind mit einer Authentifizierung versehen, sodass Operationen an einem dataset nur mit der richtigen Authorisierung erfolgen können. Öffentliche Datasets können jedoch über einen eigenen API Enpunkt immer angefragt werden. Bisher wird unterschieden zwischen einem nicht eingeloggten User und einem eingeloggten User. Als nicht eingelggter User kann man alle öffentlichen datasets einsehen. Als eingeloggter User kann man alle Datasets der Organization einsehen, Datasets erstellen, bearbeiten und löschen.
Darüber hinaus greift das Backend auf die Datenbank zu.

<img src="docs/fairmedia-c4-diagram.drawio.svg" width="100%">

## Schema

Das FairMedia Schema basiert auf dem Dataset Vokabular von schema.org, der Croissant Spezifikation inklusive der Croissant RAI (Responsible AI) Spezifikation und erweitert diese um einige weitere Eigenschaften. Dabei wurden vor Allem rechtliche Informationen hinzugefügt.

### Croissant 🥐 by MLCommons

Croissant by [MLCommons](https://mlcommons.org) is a high-level format designed for machine learning (ML) datasets. It brings together four essential layers within a single file:

- **Metadata**: This includes a detailed description of the dataset, emphasizing responsible ML practices and aspects
- **Resources**: These are the raw data sources, which can be one or more files or other types of data origins
- **Structure**: This layer explains how the raw data is assembled and organized into data structures suitable for ML use
- **ML Semantics**: This details how the data is most commonly used in machine learning contexts

The primary aim of Croissant is to establish a standard dataset format that simplifies the process of finding and utilizing ML datasets. Additionally, it facilitates the development of tools that assist in the creation, understanding, and enhancement of ML datasets.

Croissant leverages schema.org and its Dataset vocabulary to improve dataset discoverability. It is already integrated into popular platforms such as Google Dataset Search, Kaggle, OpenML, Hugging Face and TensorFlow Datasets.

In our FairMedia dataset catalog, we utilize Croissant to provide datasets that come with comprehensive descriptions and are presented in a consistent and standardized format.

You can find more information about Croissant on the [official website](https://mlcommons.org/croissant) and on the [GitHub repository](https://github.com/mlcommons/croissant).

### What's missing?

Currently, Croissant covers only minimal legal information regarding datasets and is missing some other information that may be relevant. The following key aspects are missing:

- **Copyrights**: Details on the dataset’s copyrights and whether they are clearly resolved
- **Controllerships**: Information on joint or individual controllerships related to the dataset
- **Usage Rights**: Specifications on the rights to use the dataset
- **Data Anonymization**: Methods used for data anonymization, measures taken to protect the data and identification of personal data included in the dataset
- **Access Conditions**: Clarification on the conditions under which the dataset can be accessed
- **Versioning**: More information about what has changed in the version compared to the old version

### FairMedia Specification

To address these gaps, we have extended the Croissant specification, resulting in the [FairMedia Specification](docs/fairmedia-spec.md). The following changes and additions were made:

fair:changelog: A detailed list of the changes to this version of the dataset with the reasons for the changes.
fair:dataSource: Specification of the source of the dataset.
fair:dataUsageTerms: Specifies the conditions under which the data set may be processed, including permitted commercial and non-commercial uses, text and data mining, etc.
fair:userRights: Specific rights of users using the dataset, including permission to modify or redistribute datasets or the obligation to cite the source.
fair:dataProcessingTerms: Description of the legal basis for the collection of personal data; definition of the legal basis for the provision and further processing of personal data.
fair:controllership: Determination of controllership.
fair:jointControllerAgreementConcluded: Has a Joint Controller Agreement (JCA) been concluded?
fair:liabilityClauses: Description of the disclaimers and limitations of liability in connection with the use of the data in order to minimize legal risks for the data provider.
fair:indemnityClauses: Conditions under which the user must indemnify the data provider, including a third-party provider in the event of legal disputes.
fair:copyright: Provide a detailed description about the copyright of the datasets content.
fair:dataAnonymizationProtocol: Description of the anonymization procedures used to protect the identity of individuals in the data.
fair:dataSecurityProtocol: Description of the security measures taken to protect the data, including encryption, access controls and measures to ensure data integrity, including specific safeguards for different types of personal data including sensitive data (e.g. health data, sexual orientation).
fair:dataProtectionType: Determining whether the data is anonymous/anonymized or personal data.
fair:personalData: Description of the categories and types of personal data.

## Next Steps

We plan to propose and contribute the FairMedia Specification and its extensions to the Croissant Specification.

We also want to improve access management, taking into account that some datasets can be downloaded directly from a URL, some datasets must be requested via a form, and other datasets require a contract to access.

In addition, we want to use the legal information provided to draw clearer conclusions so that users can easily identify the key considerations for using the dataset and understand how to access the dataset. Users could also receive guidance on whether a dataset fits their specific use case.
