<img src="assets/fairmedia-logo.png" width="30%">

# FairMedia Dataset Catalog Documentation

- [Specification](docs/fairmedia-spec.md)
- [Ontology](docs/fairmedia-ontology.ttl)
- [OpenAPI](docs/openapi.yaml)

## Architektur

<img src="docs/fairmedia-c4-diagram.drawio.svg" width="100%">

## Schema

## Beschreibung

<img src="docs/fairmedia-dataset-lifecycle.drawio.svg" width="100%">

### Roles

#### Viewer (logged out - unauthorized)

- view all public datasets of an organization

#### Author (loggid in - authorized)

assigned through database operation

- view all public, intern published and draft datasets
- create a dataset
- edit, delete and publish dataset drafts he is an author of
- assign other authors to dataset drafts he is an author of
- edit its own name, email address and password

## Croissant 🥐 by MLCommons

Croissant by [MLCommons](https://mlcommons.org) is a high-level format designed for machine learning (ML) datasets. It brings together four essential layers within a single file:

- **Metadata**: This includes a detailed description of the dataset, emphasizing responsible ML practices and aspects.
- **Resources**: These are the raw data sources, which can be one or more files or other types of data origins.
- **Structure**: This layer explains how the raw data is assembled and organized into data structures suitable for ML use.
- **ML Semantics**: This details how the data is most commonly used in machine learning contexts.

The primary aim of Croissant is to establish a standard dataset format that simplifies the process of finding and utilizing ML datasets. Additionally, it facilitates the development of tools that assist in the creation, understanding, and enhancement of ML datasets.

Croissant leverages schema.org and its Dataset vocabulary to improve dataset discoverability. It is already integrated into popular platforms such as Google Dataset Search, Kaggle, OpenML, Hugging Face and TensorFlow Datasets.

In our FAIRMedia dataset catalog, we utilize Croissant to provide datasets that come with comprehensive descriptions and are presented in a consistent and standardized format.

You can find more information about Croissant on the [official website](https://mlcommons.org/croissant) and on the [GitHub repository](https://github.com/mlcommons/croissant).

### Improvements on Croissant

Currently, Croissant covers only minimal legal information regarding datasets. The following key aspects are missing:

- **Copyrights**: Details on the dataset’s copyrights and whether they are clearly resolved.
- **Controllerships**: Information on joint or individual controllerships related to the dataset.
- **Usage Rights**: Specifications on the rights to use the dataset.
- **Data Anonymization**:
  - Methods used for data anonymization.
  - Measures taken to protect the data.
  - Identification of personal data included in the dataset.
- **Access Conditions**: Clarification on the conditions under which the dataset can be accessed.

To address these gaps, we have extended the Croissant specification, resulting in the [FairMedia specification](docs/fairmedia-spec.md).

## Next Steps

We plan to propose and contribute these changes and extensions to the Croissant specification.

We also want to improve access management, taking into account that some datasets can be downloaded directly from a URL, some datasets must be requested via a form, and other datasets require a contract to access.

In addition, we want to use the legal information provided to draw clearer conclusions so that users can easily identify the key considerations for using the dataset and understand how to access the dataset. Users could also receive guidance on whether a dataset fits their specific use case.
