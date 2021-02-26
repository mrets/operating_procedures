| Name | Data Field | Description |
|-------------------------|-------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|Transaction Type|transaction_type|'Internal': a transfer to one or multiple internal Account(s), 'External': a transfer to another M-RETS Organization, and 'Export': a transfer out of M-RETS to another supported tracking system|
|Start Date|vintage_start|The start date of an automatic recurring transfer.|
|End Date|vintage_end|The end date of an automatic recurring transfer. Open-ended transfers do not have an end date.|
|Max Quantity|max_quantity|The maximum number of Certificates to be transferred upon each upload. The entire Certificate batch will be transferred if the Max Quanitity is not reahed.|
|Percentage|percentage|Percentage of Certificates to be transferred upon each upload.|
|Is Irrevocable?|is_irrevocable|'true': , 'false': Determines if a transfer is Irrevocable. Only M-RETS can modify Irrevocable transfers.|
|Status|status|'accepted': the receipient has accepted the transfer.<br>, 'pending': The recipient has neither accpeted nor rejected the transfer. <br> 'rejected': The recipient has rejected the transfer.|
|Generator Fuel|relationship:generator_fuel|Users may set up a transfer for each fuel type.|
|Organization|relationship:organization|The Organization who originiated the transfer.|
|User|relationship:user|The User who originiated the transfer.|
