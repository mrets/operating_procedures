| Name                                  | Data Field                | Description |
|---------------------------------------|---------------------------|-------------|
|Details|details|The details schema defined on the Eligibility. |
|Eligible?|eligible|'True': This Generator is eligible for the related [Program](https://www.mrets.org/resources/statutes/). <br> 'False': This Generator is not eligible for the related Program.|
|Start Date|start_date|The first date this Generator is eligible for the selected Program. *Note: If your Generator does not have an specific Start Date, use the Generator's online date.*|
|Verified Date|verified_date|The date this Generator was approved for a specific Program. Leave this blank if there is no specific date.|
|Good Through|good_thru_date|The expiration date of this Generator's ability to participate in a specific Program. Leave this blank if there is no expiration date.|
|Certification Number|certification_number|An identification number given by a Program Administrator. *Example: A WI PSC Order Number.*|
|Eligibility|relationship:eligibility|The specific Program Eligiblity for which this Generator qualifies.|
|Eligiblity Bondable|relationship:eligibility_bondable|The Generator's Fuel.|
