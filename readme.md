# The Springer SUSHI service

The Springer SUSHI service enables our customers to download their [COUNTER](http://www.projectcounter.org/) usage statistics for the [Springer Link](http://link.springer.com) platform. Information on the SUSHI protocol is available from the [NISO website](http://www.niso.org/workrooms/sushi/), as is the [schema](http://www.niso.org/schemas/sushi/counter_sushi4_0.xsd) and the [WSDL](http://www.niso.org/schemas/sushi/counter_sushi4_0.wsdl).

Our endpoint is located at `http://services.springer.com/sushi`.

Data can be retrieved by posting a valid SUSHI request like the sample included in this repository:

    curl -d @sample_request.xml "http://services.springer.com/sushi" --header "content-type: text/xml"

In order to retrieve data for your organisation you need to know the Springer Business Partner ID of the organisation. This should be supplied as the value for the //CustomerReference/ID element in the request. Your email address should be supplied as the value for //Requestor/Email:

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