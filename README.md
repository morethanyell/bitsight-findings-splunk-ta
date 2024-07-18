# BitSight Company Findings Splunk TA
The BitSight Splunk TA Add-on is designed to enhance integration between BitSight security ratings and Splunk, providing comprehensive visibility into company ratings and vulnerability findings directly within your Splunk environment.

## Releases
Version 1.0.1 was published on 18 July 2024. It introduces [Findings Sampling](https://help.bitsighttech.com/hc/en-us/articles/6145673764759-Findings-Sampling) as a new parameter in the Inputs configuration. This feature was suggested by [R. Srinivasan](https://www.linkedin.com/in/rajashekar-srinivasan-36809bbb).

## Features
Dual Sourcetypes: Indexes two main sourcetypes:

- `bitsight:companies`: Stores current company ratings and metadata.
- `bitsight:findings`: Retrieves detailed vulnerability findings using the BitSight API `(GET /ratings/v1/companies/{guid}/findings?{params_set_on_input_stanza})`
- Event Indexing: Each finding is indexed as a single event with CIM-field mapping for seamless integration with Splunk's Common Information Model (CIM).
- Eventtype classification for Vulnerability data model.


## Installation
- Clone or download the [BitSight Findings Splunk TA repository](https://splunkbase.splunk.com/app/7467).
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

#### Troubleshooting
- Look for internal logs using SPL
```
index=_internal 
    host="<the host where the TA is installed>" 
    source="/opt/splunk/var/log/splunk/ta_bitsight_findings_bitsight_findings.log" 
    sourcetype="tabitsight:log"
| transaction pid source startswith="Start of collection" endswith="ends here"
```

## Support
You may reach out or send me a pint of IPA via daniel.l.astillero@gmail.com