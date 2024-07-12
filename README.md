# BitSight Company Findings Splunk TA
The BitSight Splunk TA Add-on is designed to enhance integration between BitSight security ratings and Splunk, providing comprehensive visibility into company ratings and vulnerability findings directly within your Splunk environment.

## Features
Dual Sourcetypes: Indexes two main sourcetypes:

- `bitsight:companies`: Stores current company ratings and metadata.
- `bitsight:findings`: Retrieves detailed vulnerability findings using the BitSight API `(GET /ratings/v1/companies/{guid}/findings?{params_set_on_input_stanza})`
- Event Indexing: Each finding is indexed as a single event with CIM-field mapping for seamless integration with Splunk's Common Information Model (CIM).
- Eventtype classification for Vulnerability data model.


## Installation
- Clone or download the BitSight Findings Splunk TA repository.
- Install the add-on in your Splunk environment:
- For Splunk Enterprise, navigate to Apps > Manage Apps > Install app from file.
- For Splunk Cloud, upload the add-on via Apps > Browse more apps.

#### Inputs Configuration & Requirements

- Configure input stanzas in Splunk to specify parameters for retrieving BitSight findings and company data.
- A valid BitSight token
- Company GUID for collection on specific company only
- Two (2) parameters to configure
    - Impacts Risk Vector Grade (Yes/No)
    - Severity (Severe, Material, Moderate, Minor)

## Support
You may reach out or send me a pint of IPA via daniel.l.astillero@gmail.com