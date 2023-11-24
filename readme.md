# The Springer Nature SUSHI Service (Release 5.0.2)

Here's a guideline on how to use the [COUNTER](http://www.projectcounter.org/) Release 5.0.2 version of SUSHI, with any system capable of retrieving SUSHI feeds. Information on the SUSHI protocol is available from the [swagger website](https://app.swaggerhub.com/apis/COUNTER/counter-sushi_5_0_api/1.0.0). Details about which data is available are listed on our [support pages](https://support.springernature.com/en/support/solutions/articles/6000230255-counter-release-5-details).

Our endpoint (SUSHI API URL / Vendor URL) is:

    https://counter.public.springernature.app
    
The following reports are supported:
    
    TR    (/reports/tr)
    TR_B1 (/reports/tr_b1)
    TR_B2 (/reports/tr_b2)
    TR_B3 (/reports/tr_b3)
    TR_J1 (/reports/tr_j1)
    TR_J2 (/reports/tr_j2)
    TR_J3 (/reports/tr_j3)
    TR_J4 (/reports/tr_j4)
    DR    (/reports/dr)
    DR_D1 (/reports/dr_d1)
    DR_D2 (/reports/dr_d2)
    PR    (/reports/pr)
    PR_P1 (/reports/pr_p1)
    
### Headers
    
We can deliver JSON or TSV files. JSON is the default so this header is not mandatory.
    
    Key: Accept
    Value, one of the following:
    - application/json
    - text/tab-separated-values

### Parameters

For the Standard Views the parameters are `customer_id`, `api_key`, `begin_date`, `end_date`, and `platform`.

The `customer_id` and `api_key` are mandatory. They can be found in the [Springer Nature Librarian Portal](https://librarian.springernature.com/organizations/usage#counter5sushi).

    Parameter: customer_id
    Value: [your customer_id]	

    Parameter: api_key
    Value: [your api_key]	

The `begin_date` and `end_date` are mandatory and should follow the YYYY-MM format. [Details on which date ranges are available.](https://support.springernature.com/en/support/solutions/articles/6000230255-counter-release-5-details)

    Parameter: begin_date
    Value: 2020-01
    
    Parameter: end_date
    Value: 2020-12

`platform` is an optional parameter to choose which platform to get usage for. The default is that you get usage for all our platforms.
    
    Parameter: platform
    Value, one of the following:
    - adis (AdisInsight)
    - BMC
    - mat (SpringerMaterials)
    - nature.com
    - NatureAsia (natureasia.com)
    - SciAm (Scientific American)
    - SN:ResearchGate
    - SpringerLink  

    (The platform name in paranthesis is for clarification and should not be used for requests.)
    
You can filter reports based on more parameterers than the above. All details are available in the [official swagger documentation](https://app.swaggerhub.com/apis-docs/COUNTER/counter-sushi_5_0_api/1.0.0).
        
### Example

```
    https://counter.public.springernature.app/reports/[report type]?customer_id=[your customer_id]&api_key=[your api_key]&begin_date=2019-09&end_date=2020-01
```
Here are some example requests & reports.

[TR (/reports/tr)](https://counter.public.springernature.app/reports/tr?customer_id=3000093925&api_key=kLibyHnf4wDjkvkt37MUxXQcdZYnVsYH&begin_date=2019-09&end_date=2020-01)

[TR_J1 (/reports/tr_j1)](https://counter.public.springernature.app/reports/tr_j1?customer_id=3000093925&api_key=kLibyHnf4wDjkvkt37MUxXQcdZYnVsYH&begin_date=2019-09&end_date=2020-01)

[TR_B1 (/reports/tr_b1)](https://counter.public.springernature.app/reports/tr_b1?customer_id=3000093925&api_key=kLibyHnf4wDjkvkt37MUxXQcdZYnVsYH&begin_date=2019-09&end_date=2020-01)
