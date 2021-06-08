# The Springer Nature SUSHI Service (Release 5)

Here's a guideline on how to use the COUNTER Release 5 version of SUSHI, with any system capable of retrieving SUSHI feeds for Springer and/or Nature. Please note that SUSHI for Release 5 is completely different from the Release 4 version (scroll down for Release 4 version). Here is a summary of what is different:

- Output is JSON format by default (for C4 version it was .CSV). <br/>
- The credentials that are valid for Release 4 SUSHI are not valid for Release 5 SUSHI. <br/>
- Provide a valid api_key to use the endpoints in this new version.<br/>

## SUSHI for SpringerLink & nature.com

Our SUSHI Release 5 API enables our customers to download their [COUNTER](http://www.projectcounter.org/) usage statistics for both our [Springerlink](http://link.springer.com) and [nature.com](http://nature.com) platforms. Information on the SUSHI protocol is available from the [swagger website](https://app.swaggerhub.com/apis/COUNTER/counter-sushi_5_0_api/1.0.0)

Our endpoint (SUSHI API URL / Vendor URL) is:

    https://counter.public.springernature.app

Swagger endpoint :

    https://counter.public.springernature.app/swagger-ui
    
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
 
