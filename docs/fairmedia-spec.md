# FairMedia Specification

Version 1.1.0

## Prerequisites

### Namespaces

<table>
  <thead>
    <th>Prefix</th>
    <th>IRI</th>
    <th>Description</th>
  </thead>
  <tr>
    <td>sc</td>
    <td>https://schema.org/</td>
    <td>The <a href="https://schema.org">schema.org</a> namespace.</td>
  </tr>
  <tr>
    <td>cr</td>
    <td>https://mlcommons.org/croissant/</td>
    <td>Croissant terms.</td>
  </tr>
  <tr>
    <td>rai</td>
    <td>https://mlcommons.org/croissant/RAI/</td>
    <td>Croissant Responsible AI terms.</td>
  </tr>
  <tr>
    <td>fm</td>
    <td>https://joanneum.at/fairmedia/</td>
    <td>FairMedia terms.</td>
  </tr>
</table>

## Dataset

### [sc:Dataset](https://schema.org/Dataset)

<table>
  <thead>
    <th>Property</th>
    <th>Expected Type</th>
    <th>Cardinality</th>
    <th>Description</th>
  </thead>
  <tr>
    <td><a href="https://schema.org/name">sc:name</a></td>
    <td><a href="https://schema.org/Text">sc:Text</a></td>
    <td>ONE</td>
    <td>The name of the dataset.</td>
  </tr>
  <tr>
    <td><a href="https://schema.org/abstract">sc:abstract</a></td>
    <td><a href="https://schema.org/Text">sc:Text</a></td>
    <td>ONE</td>
    <td>An abstract is a short description that summarizes a Dataset.</td>
  </tr>
  <tr>
    <td><a href="https://schema.org/description">sc:description</a></td>
    <td><a href="https://schema.org/Text">sc:Text</a></td>
    <td>ONE</td>
    <td>Description of the dataset.</td>
  </tr>
  <tr>
    <td><a href="https://schema.org/url">sc:url</a></td>
    <td><a href="https://schema.org/URL">sc:URL</a></td>
    <td>ONE</td>
    <td>The URL of the dataset. This generally corresponds to the Web page for the dataset.</td>
  </tr>
  <tr>
    <td><a href="https://schema.org/license">sc:license</a></td>
    <td><a href="https://schema.org/Text">sc:Text</a></td>
    <td>MANY</td>
    <td>A detailed description of the license conditions, including specific rights of use, restrictions and conditions for further processing.</td>
  </tr>
  <tr>
    <td><a href="https://schema.org/conditionsOfAccess">sc:conditionsOfAccess</a></td>
    <td><a href="https://schema.org/Text">sc:Text</a></td>
    <td>ONE</td>
    <td>Defines specific access requirements, e.g. only for registered users, only for academic research or only after approval by an ethics committee, the data records come from a database behind a paywall, etc.</td>
  </tr>
  <tr>
    <td><a href="https://schema.org/creator">sc:creator</a></td>
    <td>
      <a href="https://schema.org/Organization">sc:Organization</a> or<br>
      <a href="https://schema.org/Person">sc:Person</a>
    </td>
    <td>MANY</td>
    <td>The creator(s) of the dataset.</td>
  </tr>
  <tr>
    <td><a href="https://schema.org/dateCreated">sc:dateCreated</a></td>
    <td>
      <a href="https://schema.org/Date">sc:Date</a> or<br>
      <a href="https://schema.org/DateTime">sc:DateTime</a>
    </td>
    <td>ONE</td>
    <td>The date the dataset was initially created.</td>
  </tr>
  <tr>
    <td><a href="https://schema.org/dateModified">sc:dateModified</a></td>
    <td>
      <a href="https://schema.org/Date">sc:Date</a> or<br>
      <a href="https://schema.org/DateTime">sc:DateTime</a>
    </td>
    <td>ONE</td>
    <td>The date the dataset was most recently modified.</td>
  </tr>
  <tr>
    <td><a href="https://schema.org/publisher">sc:publisher</a></td>
    <td>
      <a href="https://schema.org/Organization">sc:Organization</a> or<br>
      <a href="https://schema.org/Person">sc:Person</a>
    </td>
    <td>MANY</td>
    <td>The publisher(s) of the dataset, which may be distinct from its creator.</td>
  </tr>
  <tr>
    <td><a href="https://schema.org/datePublished">sc:datePublished</a></td>
    <td>
      <a href="https://schema.org/Date">sc:Date</a> or<br>
      <a href="https://schema.org/DateTime">sc:DateTime</a>
    </td>
    <td>ONE</td>
    <td>The date the dataset was published.</td>
  </tr>
  <tr>
    <td><a href="https://schema.org/keywords">sc:keywords</a></td>
    <td>
      <a href="https://schema.org/DefinedTerm">sc:DefinedTerm</a> or<br>
      <a href="https://schema.org/Text">sc:Text</a> or<br>
      <a href="https://schema.org/URL">sc:URL</a>
    </td>
    <td>MANY</td>
    <td>A set of keywords associated with the dataset, either as free text, or a DefinedTerm with a formal definition.</td>
  </tr>
  <tr>
    <td><a href="https://schema.org/isBasedOn">sc:isBasedOn</a></td>
    <td>
      Reference<<a href="https://schema.org/Dataset">sc:Dataset</a>> or<br>
      <a href="https://schema.org/URL">sc:URL</a>
    </td>
    <td>MANY</td>
    <td>A resource from which this dataset is derived or from which it is a modification or adaptation.</td>
  </tr>
  <tr>
    <td><a href="https://schema.org/version">sc:version</a></td>
    <td>
      <a href="https://schema.org/Number">sc:Number</a> or<br>
      <a href="https://schema.org/Text">sc:Text</a>
    </td>
    <td>ONE</td>
    <td>The version of the dataset. The recommended versioning scheme to use for datasets is <code>MAJOR.MINOR.PATCH</code>, following <a href="https://semver.org/spec/v2.0.0.html">Semantic Versioning 2.0.0</a>. More specifically:<br>
      - If the <code>PATCH</code> version is incremented, the data remains the same, although it might be serialized differently or is packaged using different file formats.<br>
      - If the <code>MINOR</code> version is incremented, the existing data is the same and can still be retrieved as it: there might be additional data (e.g. new fields, new RecordSet), or even new records in existing RecordSets, as long as the old recordSets can still be retrieved (eg: the new records are added to a different Split).<br>
      - If the <code>MAJOR</code> version is incremented, the existing data has been changed (edited, removed or shuffled records across splits), or extended in a way which doesn't allow for easy access to the data as it was at the previous version.
    </td>
  </tr>
  <tr>
    <td><a href="https://schema.org/releaseNotes">sc:releaseNotes</a></td>
    <td>
      <a href="https://schema.org/Text">sc:Text</a> or<br>
      <a href="https://schema.org/URL">sc:URL</a>
    </td>
    <td>ONE</td>
    <td>Description of what changed in this version of the dataset with the reasons for the changes.</td>
  </tr>
  <tr>
    <td><a href="https://schema.org/inLanguage">sc:inLanguage</a></td>
    <td>
      <a href="https://schema.org/Language">sc:Language</a> or<br>
      <a href="https://schema.org/Text">sc:Text</a>
    </td>
    <td>MANY</td>
    <td>The language(s) of the content of the dataset.</td>
  </tr>
  <tr>
    <td><a href="https://schema.org/sameAs">sc:sameAs</a></td>
    <td><a href="https://schema.org/URL">sc:URL</a></td>
    <td>MANY</td>
    <td>The URL of another Web resource that represents the same dataset as this one.</td>
  </tr>
  <tr>
    <td><a href="https://schema.org/distribution">sc:distribution</a></td>
    <td>
      <a href="https://mlcommons.github.io/croissant/docs/croissant-spec.html#fileobject">cr:FileObject</a> or<br>
      <a href="https://mlcommons.github.io/croissant/docs/croissant-spec.html#fileset">cr:FileSet</a>
    </td>
    <td>MANY</td>
    <td>
      A downloadable form of this dataset, at a specific location, in a specific format. This property can be repeated if different variations are available. There is no expectation that different downloadable distributions must contain exactly equivalent information (see also DCAT on this point). Different distributions might include or exclude different subsets of the entire dataset, for example.<br>
      By contrast with <a href="https://schema.org/Dataset">schema.org/Dataset</a>, Croissant requires the distribution property to have values of type FileObject or FileSet.
    </td>
  </tr>
  <tr>
    <td>cr:citeAs</td>
    <td><a href="https://schema.org/Text">sc:Text</a></td>
    <td>ONE</td>
    <td>A citation to the dataset itself, or a citation for a publication that describes the dataset. Ideally, citations should be expressed using the <a href="https://www.bibtex.org">bibtex</a> format.<br>
      Note that this is different from <a href="https://schema.org/citation">schema.org/citation</a>, which is used to make a citation to another publication from this dataset.
    </td>
  </tr>
  <tr>
    <td>fm:dataSource</td>
    <td><a href="https://schema.org/Text">sc:Text</a></td>
    <td>MANY</td>
    <td>Specification of the source of the dataset.</td>
  </tr>
  <tr>
    <td>fm:dataUsageTerms</td>
    <td><a href="https://schema.org/Text">sc:Text</a></td>
    <td>ONE</td>
    <td>Specifies the conditions under which the data set may be processed, including permitted commercial and non-commercial uses, text and data mining, etc.</td>
  </tr>
  <tr>
    <td>fm:userRights</td>
    <td><a href="https://schema.org/Text">sc:Text</a></td>
    <td>ONE</td>
    <td>Specific rights of users using the dataset, including permission to modify or redistribute datasets or the obligation to cite the source.</td>
  </tr>
  <tr>
    <td>fm:dataProcessingTerms</td>
    <td><a href="https://schema.org/Text">sc:Text</a></td>
    <td>ONE</td>
    <td>Description of the legal basis for the collection of personal data; definition of the legal basis for the provision and further processing of personal data.</td>
  </tr>
  <tr>
    <td>fm:controllership</td>
    <td>"sole controllership" or "joint controllership"</td>
    <td>ONE</td>
    <td>Determination of controllership.</td>
  </tr>
  <tr>
    <td>fm:jointControllerAgreementConcluded</td>
    <td><a href="https://schema.org/Boolean">sc:Boolean</a></td>
    <td>ONE</td>
    <td>Has a Joint Controller Agreement (JCA) been concluded?</td>
  </tr>
  <tr>
    <td>fm:liabilityClauses</td>
    <td><a href="https://schema.org/Text">sc:Text</a></td>
    <td>ONE</td>
    <td>Description of the disclaimers and limitations of liability in connection with the use of the data in order to minimize legal risks for the data provider.</td>
  </tr>
  <tr>
    <td>fm:indemnityClauses</td>
    <td><a href="https://schema.org/Text">sc:Text</a></td>
    <td>ONE</td>
    <td>Conditions under which the user must indemnify the data provider, including a third-party provider in the event of legal disputes.</td>
  </tr>
  <tr>
    <td>fm:copyright</td>
    <td><a href="https://schema.org/Text">sc:Text</a></td>
    <td>ONE</td>
    <td>Provide a detailed description about the copyright of the datasets content.</td>
  </tr>
  <tr>
    <td>rai:dataCollection</td>
    <td><a href="https://schema.org/Text">sc:Text</a></td>
    <td>ONE</td>
    <td>Description of the data collection process.</td>
  </tr>
  <tr>
    <td>rai:dataCollectionType</td>
    <td><a href="https://schema.org/Text">sc:Text</a></td>
    <td>MANY</td>
    <td>Define the data collection type. Recommended values:<br>Surveys, Secondary Data analysis, Physical data collection, Direct measurement, Document analysis, Manual Human Curator, Software Collection, Experiments, Web Scraping, Web API, Focus groups, Self-reporting, Customer feedback data, User-generated content data, Passive Data Collection, Others.
    </td>
  </tr>
  <tr>
    <td>rai:dataCollectionMissingData</td>
    <td><a href="https://schema.org/Text">sc:Text</a></td>
    <td>ONE</td>
    <td>Description of missing data in structured/unstructured form.</td>
  </tr>
  <tr>
    <td>rai:dataCollectionRawData</td>
    <td><a href="https://schema.org/Text">sc:Text</a></td>
    <td>ONE</td>
    <td>Description of the raw data i.e. source of the data.</td>
  </tr>
  <tr>
    <td>rai:dataCollectionTimeframe</td>
    <td><a href="https://schema.org/DateTime">sc:DateTime</a></td>
    <td>MANY</td>
    <td>Timeframe in terms of start and end date of the collection process.</td>
  </tr>
  <tr>
    <td>rai:dataImputationProtocol</td>
    <td><a href="https://schema.org/Text">sc:Text</a></td>
    <td>ONE</td>
    <td>Description of data imputation process if applicable.</td>
  </tr>
  <tr>
    <td>rai:dataManipulationProtocol</td>
    <td><a href="https://schema.org/Text">sc:Text</a></td>
    <td>ONE</td>
    <td>Description of data manipulation process if applicable.</td>
  </tr>
  <tr>
    <td>fm:dataAnonymizationProtocol</td>
    <td><a href="https://schema.org/Text">sc:Text</a></td>
    <td>ONE</td>
    <td>Description of the anonymization procedures used to protect the identity of individuals in the data.</td>
  </tr>
  <tr>
    <td>rai:dataPreprocessingProtocol</td>
    <td><a href="https://schema.org/Text">sc:Text</a></td>
    <td>MANY</td>
    <td>Description of the steps that were required to bring collected data to a state that can be processed by an ML model/algorithm, e.g. filtering out incomplete entries etc.</td>
  </tr>
  <tr>
    <td>fm:dataSecurityProtocol</td>
    <td><a href="https://schema.org/Text">sc:Text</a></td>
    <td>ONE</td>
    <td>Description of the security measures taken to protect the data, including encryption, access controls and measures to ensure data integrity, including specific safeguards for different types of personal data including sensitive data (e.g. health data, sexual orientation).</td>
  </tr>
  <tr>
    <td>rai:dataAnnotationProtocol</td>
    <td><a href="https://schema.org/Text">sc:Text</a></td>
    <td>ONE</td>
    <td>Description of annotations (labels, ratings) produced, including how these were created or authored - Annotation Workforce Type, Annotation Characteristic(s), Annotation Description(s), Annotation Task(s), Annotation Distribution(s).</td>
  </tr>
  <tr>
    <td>rai:dataAnnotationPlatform</td>
    <td><a href="https://schema.org/Text">sc:Text</a></td>
    <td>MANY</td>
    <td>Platform, tool, or library used to collect annotations by human annotators.</td>
  </tr>
  <tr>
    <td>rai:dataAnnotationAnalysis</td>
    <td><a href="https://schema.org/Text">sc:Text</a></td>
    <td>MANY</td>
    <td>Considerations related to the process of converting the "raw" annotations into the labels that are ultimately packaged in a dataset - Uncertainty or disagreement between annotations on each instance as a signal in the dataset, analysis of systematic disagreements between annotators of different socio demographic group, how the final dataset annotations will relate to individual annotator responses.</td>
  </tr>
  <tr>
    <td>rai:dataReleaseMaintenancePlan</td>
    <td><a href="https://schema.org/Text">sc:Text</a></td>
    <td>MANY</td>
    <td>Versioning information in terms of the updating timeframe, the maintainers, and the deprecation policies.</td>
  </tr>
  <tr>
    <td>rai:personalSensitiveInformation</td>
    <td><a href="https://schema.org/Text">sc:Text</a></td>
    <td>MANY</td>
    <td>Sensitive Human Attribute(s) - Gender, Socio-economic status, Geography, Language, Age, Culture, Experience or Seniority, Others (please specify).</td>
  </tr>
  <tr>
    <td>fm:dataProtectionType</td>
    <td>"anonymized" or "personal"</td>
    <td>ONE</td>
    <td>Determining whether the data is anonymous/anonymized or personal data.</td>
  </tr>
  <tr>
    <td>fm:personalData</td>
    <td><a href="https://schema.org/Text">sc:Text</a></td>
    <td>ONE</td>
    <td>Description of the categories and types of personal data.</td>
  </tr>
  <tr>
    <td>rai:dataSocialImpact</td>
    <td><a href="https://schema.org/Text">sc:Text</a></td>
    <td>ONE</td>
    <td>Discussion of social impact, if applicable.</td>
  </tr>
  <tr>
    <td>rai:dataBiases</td>
    <td><a href="https://schema.org/Text">sc:Text</a></td>
    <td>MANY</td>
    <td>Description of biases in dataset, if applicable.</td>
  </tr>
  <tr>
    <td>rai:dataLimitations</td>
    <td><a href="https://schema.org/Text">sc:Text</a></td>
    <td>MANY</td>
    <td>Known limitations - Data generalization limits (e.g related to data distribution, data quality issues, or data sources) and on-recommended uses.</td>
  </tr>
  <tr>
    <td>rai:dataUseCases</td>
    <td><a href="https://schema.org/Text">sc:Text</a></td>
    <td>MANY</td>
    <td>Dataset Use(s) - Training, Testing, Validation, Development or Production Use, Fine Tuning, Others (please specify), Usage Guidelines. Recommended uses.</td>
  </tr>
  <tr>
    <td>rai:annotationsPerItem</td>
    <td><a href="https://schema.org/Text">sc:Text</a></td>
    <td>ONE</td>
    <td>Number of human labels per dataset item.</td>
  </tr>
  <tr>
    <td>rai:annotatorDemographics</td>
    <td><a href="https://schema.org/Text">sc:Text</a></td>
    <td>MANY</td>
    <td>List of demographics specifications about the annotators.</td>
  </tr>
  <tr>
    <td>rai:machineAnnotationTools</td>
    <td><a href="https://schema.org/Text">sc:Text</a></td>
    <td>MANY</td>
    <td>List of software used for data annotation (e.g. concept extraction, NER, and additional characteristics of the tools used for annotation to allow for replication or extension).</td>
  </tr>
</table>

## Resources

### [cr:FileObject](https://mlcommons.github.io/croissant/docs/croissant-spec.html#fileobject)

<table>
  <thead>
    <th>Property</th>
    <th>Expected Type</th>
    <th>Cardinality</th>
    <th>Description</th>
  </thead>
  <tr>
    <td><a href="https://schema.org/name">sc:name</a></td>
    <td><a href="https://schema.org/Text">sc:Text</a></td>
    <td>ONE</td>
    <td>The name of the file. As much as possible, the name should reflect the name of the file as downloaded, including the file extension. e.g. "images.zip".</td>
  </tr>
  <tr>
    <td><a href="https://schema.org/contentUrl">sc:contentUrl</a></td>
    <td><a href="https://schema.org/URL">sc:URL</a></td>
    <td>ONE</td>
    <td>Actual bytes of the media object, for example the image file or video file.</td>
  </tr>
  <tr>
    <td><a href="https://schema.org/contentSize">sc:contentSize</a></td>
    <td><a href="https://schema.org/Text">sc:Text</a></td>
    <td>ONE</td>
    <td>File size in (mega/kilo/...)bytes. Defaults to bytes if a unit is not specified.</td>
  </tr>
  <tr>
    <td><a href="https://schema.org/encodingFormat">sc:encodingFormat</a></td>
    <td><a href="https://schema.org/Text">sc:Text</a></td>
    <td>ONE</td>
    <td>The format of the file, given as a mime type.</td>
  </tr>
  <tr>
    <td><a href="https://schema.org/sameAs">sc:sameAs</a></td>
    <td><a href="https://schema.org/URL">sc:URL</a></td>
    <td>MANY</td>
    <td>URL (or local name) of a FileObject with the same content, but in a different format.</td>
  </tr>
  <tr>
    <td><a href="https://schema.org/description">sc:description</a></td>
    <td><a href="https://schema.org/Text">sc:Text</a></td>
    <td>ONE</td>
    <td>A description of how to get the file.</td>
  </tr>
  <tr>
    <td><a href="https://schema.org/sha256">sc:sha256</a></td>
    <td><a href="https://schema.org/Text">sc:Text</a></td>
    <td>ONE</td>
    <td>Checksum for the file contents.</td>
  </tr>
  <tr>
    <td>cr:containedIn</td>
    <td>
      <a href="https://mlcommons.github.io/croissant/docs/croissant-spec.html#fileobject">cr:FileObject</a> or<br>
      <a href="https://mlcommons.github.io/croissant/docs/croissant-spec.html#fileset">cr:FileSet</a>
    </td>
    <td>MANY</td>
    <td>Another <code>FileObject</code> or <code>FileSet</code> that this one is contained in, e.g., in the case of a file extracted from an archive. When this property is present, the <code>contentUrl</code> is evaluated as a relative path within the container object.</td>
  </tr>
</table>

### [cr:FileSet](https://mlcommons.github.io/croissant/docs/croissant-spec.html#fileset)

<table>
  <thead>
    <th>Property</th>
    <th>Expected Type</th>
    <th>Cardinality</th>
    <th>Description</th>
  </thead>
  <tr>
    <td><a href="https://schema.org/name">sc:name</a></td>
    <td><a href="https://schema.org/Text">sc:Text</a></td>
    <td>ONE</td>
    <td>The name of the file. As much as possible, the name should reflect the name of the file as downloaded, including the file extension. e.g. "images.zip".</td>
  </tr>
  <tr>
    <td><a href="https://schema.org/contentUrl">sc:contentUrl</a></td>
    <td><a href="https://schema.org/URL">sc:URL</a></td>
    <td>ONE</td>
    <td>Actual bytes of the media object, for example the image file or video file.</td>
  </tr>
  <tr>
    <td><a href="https://schema.org/contentSize">sc:contentSize</a></td>
    <td><a href="https://schema.org/Text">sc:Text</a></td>
    <td>ONE</td>
    <td>File size in (mega/kilo/...)bytes. Defaults to bytes if a unit is not specified.</td>
  </tr>
  <tr>
    <td><a href="https://schema.org/encodingFormat">sc:encodingFormat</a></td>
    <td><a href="https://schema.org/Text">sc:Text</a></td>
    <td>ONE</td>
    <td>The format of the file, given as a mime type.</td>
  </tr>
  <tr>
    <td><a href="https://schema.org/sameAs">sc:sameAs</a></td>
    <td><a href="https://schema.org/URL">sc:URL</a></td>
    <td>MANY</td>
    <td>URL (or local name) of a FileSet with the same content, but in a different format.</td>
  </tr>
  <tr>
    <td><a href="https://schema.org/description">sc:description</a></td>
    <td><a href="https://schema.org/Text">sc:Text</a></td>
    <td>ONE</td>
    <td>A description of how to get the file.</td>
  </tr>
  <tr>
    <td><a href="https://schema.org/sha256">sc:sha256</a></td>
    <td><a href="https://schema.org/Text">sc:Text</a></td>
    <td>ONE</td>
    <td>Checksum for the file contents.</td>
  </tr>
  <tr>
    <td>cr:containedIn</td>
    <td>
      Reference<<a href="https://mlcommons.github.io/croissant/docs/croissant-spec.html#fileobject">cr:FileObject</a>> or<br>
      Reference<<a href="https://mlcommons.github.io/croissant/docs/croissant-spec.html#fileset">cr:FileSet</a>>
    </td>
    <td>MANY</td>
    <td>The source of data for the <code>FileSet</code>, e.g., an archive. If multiple values are provided for <code>containedIn</code>, then the union of their contents is taken (e.g., this can be used to combine files from multiple archives).</td>
  </tr>
  <tr>
    <td>cr:includes</td>
    <td><a href="https://schema.org/Text">sc:Text</a></td>
    <td>MANY</td>
    <td>A glob pattern that specifies the files to include.</td>
  </tr>
  <tr>
    <td>cr:excludes</td>
    <td><a href="https://schema.org/Text">sc:Text</a></td>
    <td>MANY</td>
    <td>A glob pattern that specifies the files to exclude.</td>
  </tr>
</table>

## RecordSets

### [cr:RecordSet](https://mlcommons.github.io/croissant/docs/croissant-spec.html#recordset)

<table>
  <thead>
    <th>Property</th>
    <th>Expected Type</th>
    <th>Cardinality</th>
    <th>Description</th>
  </thead>
  <tr>
    <td><a href="https://schema.org/name">sc:name</a></td>
    <td><a href="https://schema.org/Text">sc:Text</a></td>
    <td>ONE</td>
    <td>The name of the <code>RecordSet</code>.</td>
  </tr>
  <tr>
    <td><a href="https://schema.org/description">sc:description</a></td>
    <td><a href="https://schema.org/Text">sc:Text</a></td>
    <td>ONE</td>
    <td>Description of the <code>RecordSet</code>.</td>
  </tr>
  <tr>
    <td>cr:field</td>
    <td><a href="https://mlcommons.github.io/croissant/docs/croissant-spec.html#field">cr:Field</a></td>
    <td>MANY</td>
    <td>A data element that appears in the records of the <code>RecordSet</code> (e.g., one column of a table).</td>
  </tr>
  <tr>
    <td>cr:key</td>
    <td><a href="https://schema.org/Text">sc:Text</a></td>
    <td>MANY</td>
    <td>One or more fields whose values uniquely identify each record in the <code>RecordSet</code>.</td>
  </tr>
</table>

### [cr:Field](https://mlcommons.github.io/croissant/docs/croissant-spec.html#field)

<table>
  <thead>
    <th>Property</th>
    <th>Expected Type</th>
    <th>Cardinality</th>
    <th>Description</th>
  </thead>
  <tr>
    <td><a href="https://schema.org/name">sc:name</a></td>
    <td><a href="https://schema.org/Text">sc:Text</a></td>
    <td>ONE</td>
    <td>The name of the field.</td>
  </tr>
  <tr>
    <td><a href="https://schema.org/description">sc:description</a></td>
    <td><a href="https://schema.org/Text">sc:Text</a></td>
    <td>ONE</td>
    <td>Description of the field.</td>
  </tr>
  <tr>
    <td>cr:source</td>
    <td><a href="https://mlcommons.github.io/croissant/docs/croissant-spec.html#datasource">cr:DataSource</a></td>
    <td>ONE</td>
    <td>The data source of the field. This will generally reference a <code>FileObject</code> or <code>FileSet</code>'s contents (e.g., a specific column of a table).</td>
  </tr>
  <tr>
    <td>cr:dataType</td>
    <td><a href="https://mlcommons.github.io/croissant/docs/croissant-spec.html#datatype">cr:DataType</a></td>
    <td>MANY</td>
    <td>The data type of the field, identified by the URI of the corresponding class. It could be either an atomic type (e.g, <code>sc:Integer</code>) or a semantic type (e.g., <code>sc:GeoLocation</code>).</td>
  </tr>
</table>

### [cr:DataSource](https://mlcommons.github.io/croissant/docs/croissant-spec.html#datasource)

<table>
  <thead>
    <th>Property</th>
    <th>Expected Type</th>
    <th>Cardinality</th>
    <th>Description</th>
  </thead>
  <tr>
    <td>cr:fileObject</td>
    <td>Reference<<a href="https://mlcommons.github.io/croissant/docs/croissant-spec.html#fileobject">cr:FileObject</a>></td>
    <td>ONE</td>
    <td>The name of the referenced <code>FileObject</code> source of the data.</td>
  </tr>
  <tr>
    <td>cr:fileSet</td>
    <td>Reference<<a href="https://mlcommons.github.io/croissant/docs/croissant-spec.html#fileset">cr:FileSet</a>></td>
    <td>ONE</td>
    <td>The name of the referenced <code>FileSet</code> source of the data.</td>
  </tr>
  <tr>
    <td>cr:recordSet</td>
    <td>Reference<<a href="https://mlcommons.github.io/croissant/docs/croissant-spec.html#recordset">cr:RecordSet</a>></td>
    <td>ONE</td>
    <td>The name of the referenced <code>RecordSet</code> source.</td>
  </tr>
  <tr>
    <td>cr:extract</td>
    <td><a href="https://mlcommons.github.io/croissant/docs/croissant-spec.html#extract">cr:Extract</a></td>
    <td>ONE</td>
    <td>The extraction method from the provided source.</td>
  </tr>
</table>

#### [cr:Extract](https://mlcommons.github.io/croissant/docs/croissant-spec.html#extract)

<table>
  <thead>
    <th>Property</th>
    <th>Expected Type</th>
    <th>Cardinality</th>
    <th>Description</th>
  </thead>
  <tr>
    <td>cr:fileProperty</td>
    <td>"fullPath", "fileName", "content", "lines" or "lineNumber"</td>
    <td>ONE</td>
    <td>The file property to extract from the data source metadata. One of:
      <ul>
        <li><code>fullpath</code>: The full path to the file within the Croissant extraction or download folders.</li>
        <li><code>filename</code>: The name of the file.</li>
        <li><code>content</code>: The byte content of the file.</li>
        <li><code>lines</code>: The byte content of each line in the file.</li>
        <li><code>lineNumbers</code>: The number of each line in the file (starting from 0).</li>
      </ul>
    </td>
  </tr>
  <tr>
    <td>cr:column</td>
    <td><a href="https://schema.org/Text">sc:Text</a></td>
    <td>ONE</td>
    <td>In case the data source is CSV data, a column name to extract the values in the specified column.</td>
  </tr>
</table>

### [cr:DataType](https://mlcommons.github.io/croissant/docs/croissant-spec.html#datatype)

`DataType` is a subclassOf: [sc:URL](https://schema.org/URL) and represents the data type of values expected for a Field in a RecordSet. This class is inspired by the `Datatype` class in [CSVW](https://csvw.org/). In addition to simple atomic types, types can be semantic types, such as [schema.org](https://schema.org/DataType) classes, as well types defined in other vocabularies.

## Dataset Creators / Publishers

### [sc:Organization](https://schema.org/Organization)

<table>
  <thead>
    <th>Property</th>
    <th>Expected Type</th>
    <th>Cardinality</th>
    <th>Description</th>
  </thead>
  <tr>
    <td><a href="https://schema.org/name">sc:name</a></td>
    <td><a href="https://schema.org/Text">sc:Text</a></td>
    <td>ONE</td>
    <td>The name of the organization.</td>
  </tr>
  <tr>
    <td><a href="https://schema.org/address">sc:address</a></td>
    <td><a href="https://schema.org/Text">sc:Text</a></td>
    <td>ONE</td>
    <td>The postal address of the organization.</td>
  </tr>
  <tr>
    <td><a href="https://schema.org/email">sc:email</a></td>
    <td><a href="https://schema.org/Text">sc:Text</a></td>
    <td>ONE</td>
    <td>The representative email address of the organization.</td>
  </tr>
  <tr>
    <td><a href="https://schema.org/telephone">sc:telephone</a></td>
    <td><a href="https://schema.org/Text">sc:Text</a></td>
    <td>ONE</td>
    <td>The contact telephone number of the organization.</td>
  </tr>
</table>

### [sc:Person](https://schema.org/Person)

<table>
  <thead>
    <th>Property</th>
    <th>Expected Type</th>
    <th>Cardinality</th>
    <th>Description</th>
  </thead>
  <tr>
    <td><a href="https://schema.org/name">sc:name</a></td>
    <td><a href="https://schema.org/Text">sc:Text</a></td>
    <td>ONE</td>
    <td>The first name of the person.</td>
  </tr>
  <tr>
    <td><a href="https://schema.org/familyName">sc:familyName</a></td>
    <td><a href="https://schema.org/Text">sc:Text</a></td>
    <td>ONE</td>
    <td>The last name of the person.</td>
  </tr>
  <tr>
    <td><a href="https://schema.org/address">sc:address</a></td>
    <td><a href="https://schema.org/Text">sc:Text</a></td>
    <td>ONE</td>
    <td>The postal address of the person.</td>
  </tr>
  <tr>
    <td><a href="https://schema.org/email">sc:email</a></td>
    <td><a href="https://schema.org/Text">sc:Text</a></td>
    <td>ONE</td>
    <td>The email address of the person.</td>
  </tr>
  <tr>
    <td><a href="https://schema.org/telephone">sc:telephone</a></td>
    <td><a href="https://schema.org/Text">sc:Text</a></td>
    <td>ONE</td>
    <td>The telephone number of the person.</td>
  </tr>
</table>
