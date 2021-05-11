# The Springer Nature SUSHI Service (Release 5)

Here's a guideline on how to use the COUNTER Release 5 version of SUSHI, with any system capable of retrieving SUSHI feeds for Springer and/or Nature. Please note that SUSHI for Release 5 is completely different from the Release 4 version (scroll down for Release 4 version). Here is a summary of what is different:

- Output is JSON format by default (for C4 version it was .CSV). <br/>
- The credentials that are valid for Release 4 SUSHI are not valid for Release 5 SUSHI. <br/>
- Provide a valid api_key to use the endpoints in this new version.<br/>

## SUSHI for SpringerLink & nature.com

Our SUSHI Release 5 API enables our customers to download their [COUNTER](http://www.projectcounter.org/) usage statistics for both our [Springerlink](http://link.springer.com) and [nature.com](http://nature.com) platforms. Information on the SUSHI protocol is available from the [swagger website](https://app.swaggerhub.com/apis/COUNTER/counter-sushi_5_0_api/1.0.0)

Our endpoint (SUSHI API URL / Vendor URL) is:

    https://counter.public.springernature.app

Data can be retrieved by posting a valid SUSHI request by providing the mandatory fields. 

The following reports are currently supported:
    
    TR    (/reports/tr)
    TR_B1 (/reports/tr_b1)
    TR_B2 (/reports/tr_b2)
    TR_B3 (/reports/tr_b3)
    TR_J1 (/reports/tr_j1)
    TR_J2 (/reports/tr_j2)
    TR_J3 (/reports/tr_j3)
    TR_J4 (/reports/tr_j4)
    PR    (/reports/pr)
    PR_P1 (/reports/pr_p1)
    
    
### Headers
    
The following header can be provided for requesting JSON format. However, fhe file format is by default JSON so it is not mandatory. 
    
    Key: Accept
    Value: application/json
    
### Parameters

For the TR Standard Views; the only parameters are `customer_id`, `api_key`, `begin_date`, `end_date`, `platform`.

To get data for your organisation you need to know the Springer Nature Business Partner ID ("BPID") of your organisation, and set the `customer_id` parameter accordingly. To find your BPID, go to [identity details](https://link.springer.com/identity-details). If your organization is listed, then use this as your `customer_id`. If you see several organizations, or none, contact [customer service](https://support.springernature.com/en/support/tickets/new).

    Parameter: customer_id
    Value: [your customer_id]	

The `api_key` for your organization can be found in the [Springer Nature Librarian Admin Portal](https://librarian.springernature.com/organizations/usage#counter5sushi)

    Parameter: api_key
    Value: [your api_key]	

The `begin_date` and `end_date` are also mandatory and should follow the YYYY-MM format. Please note that data is currently available from September 2019 onwards.

    Parameter: begin_date
    Value: 2020-01
    
    Parameter: end_date
    Value: 2020-12

`platform` is an optional parameter. Is the name of the Platform the usage is being requested for. If omitted, you would get usage for all platforms.
    
    Parameter: platform
    Value, one of the following:
    - adis (AdisInsight)
    - BMC
    - mat (SpringerMaterials)
    - nature.com
    - NatureAsia
    - SciAm (Scientific American)
    - SN:ResearchGate
    - SpringerLink  

    (name of platform supplied in Parentheses for values it's not clear enough)
    
For TR (title master report); there are more options for parameters in addition to the above listed ones. Please refer to the [official swagger document.](https://app.swaggerhub.com/apis-docs/COUNTER/counter-sushi_5_0_api/1.0.0#/default/getReportsTR)
        
### Example

```
    https://counter.public.springernature.app/reports/[report type]?customer_id=[your customer_id]&begin_date=2019-09&end_date=2020-01&api_key=[your api_key]
```
Here are some example requests & reports.

[TR (/reports/tr)](https://counter.public.springernature.app/reports/tr?customer_id=3000093925&begin_date=2019-09&end_date=2020-01&api_key=kLibyHnf4wDjkvkt37MUxXQcdZYnVsYH)

[TR_J1 (/reports/tr_j1)](https://counter.public.springernature.app/reports/tr_j1?customer_id=3000093925&begin_date=2019-09&end_date=2020-01&api_key=kLibyHnf4wDjkvkt37MUxXQcdZYnVsYH)

[TR_B1 (/reports/tr_b1)](https://counter.public.springernature.app/reports/tr_b1?customer_id=3000093925&begin_date=2019-09&end_date=2020-01&api_key=kLibyHnf4wDjkvkt37MUxXQcdZYnVsYH)
 
    
# The Springer Nature SUSHI Service (Release 4)

## SUSHI for Springerlink

The Springer SUSHI service enables our customers to download their [COUNTER](http://www.projectcounter.org/) usage statistics for the [Springer Link](http://link.springer.com) platform. Information on the SUSHI protocol is available from the [NISO website](http://www.niso.org/workrooms/sushi/), as is the [schema](http://www.niso.org/schemas/sushi/counter_sushi4_0.xsd) and the [WSDL](http://www.niso.org/schemas/sushi/counter_sushi4_0.wsdl).

Our endpoint is located at `http://services.springer.com/sushi`.

Data can be retrieved by posting a valid SUSHI request like the sample included in this repository:

    curl -d @sample_request.xml "http://services.springer.com/sushi" --header "content-type: text/xml"

In order to retrieve data for your organisation you need to know the Springer Business Partner ID of the organisation. This should be supplied as the value for the `//CustomerReference/ID` element in the request. Your email address should be supplied as the value for `//Requestor/Email`:

    <sus:Requestor>
      <sus:ID></sus:ID>
      <sus:Name></sus:Name>
      <sus:Email>example@springer.com</sus:Email>
     </sus:Requestor>
     <sus:CustomerReference>
       <sus:ID>3000093925</sus:ID>
    </sus:CustomerReference>

The report required should be requested using the ReportDefinition element:

    <sus:ReportDefinition Name="JR1" Release="4">

The following report names are supported:

    JR1
    JR1 GOA
    JR2
    JR5
    BR2
    BR3

The only supported value for Release is `4`.

Consortia admins looking to harvest data for their members can download a list of member business partner identifiers via the admin interface. Note that we do not support the combined CR1 report.


## SUSHI for Nature

To obtain usage statistics for [Nature](http://www.nature.com) you need to post a request to the endpoint `http://services.springer.com/sushi/nature`.

In this case you need to use your BPID as the value of `//CustomerReference/ID`

    <sus:Requestor>
      <sus:ID></sus:ID>
      <sus:Name></sus:Name>
      <sus:Email>example@biomedcentral.com</sus:Email>
    </sus:Requestor>
    <sus:CustomerReference>
      <sus:ID>3000093925</sus:ID>
    </sus:CustomerReference>
    
 For Nature only the following journal reports apply:

    JR1
    JR1 GOA
    JR2
    JR5
    
    
## SUSHI for BioMed Central and SpringerOpen

To obtain usage statistics for the [BioMed central platform](http://www.biomedcentral.com) and [SpringerOpen site](http://www.springeropen.com) you need to post a similar request to the endpoint `http://services.springer.com/sushi/bmc`.

In this case you need to use your BioMed Central Institutional ID as the value of `//CustomerReference/ID` and this should be namespaced with the prefix `BMC:` e.g.

    <sus:Requestor>
      <sus:ID></sus:ID>
      <sus:Name></sus:Name>
      <sus:Email>example@biomedcentral.com</sus:Email>
    </sus:Requestor>
    <sus:CustomerReference>
      <sus:ID>BMC:201</sus:ID>
    </sus:CustomerReference>

For these platforms only the journal reports apply:

    JR1
    JR1 GOA
    JR2
    JR5
    
## SUSHI for Scientific American

To obtain usage statistics for the [Scientific American platform](https://www.scientificamerican.com) you need to post a request to the endpoint `http://services.springer.com/sushi/sciam`.

In this case you need to use your BPID as the value of `//CustomerReference/ID`

    <sus:Requestor>
      <sus:ID></sus:ID>
      <sus:Name></sus:Name>
      <sus:Email>example@scientificamerican.com</sus:Email>
    </sus:Requestor>
    <sus:CustomerReference>
      <sus:ID>3000093925</sus:ID>
    </sus:CustomerReference>

For these platforms only the journal reports apply:

    JR1
    JR1 GOA
    JR2
    JR5


