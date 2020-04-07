Section 4.6: Transactions
-------------------------

### Section 4.6.1: Transferring Certificates between Organizations

M-RETS Users may transfer active Certificates to:

1.  Another Organization

2.  Another active Account

3.  To a compatible tracking system

After a User initiates a transfer ("Transferor"), the transferred
Certificates enter a 'Pending' state. This effectively "freezes" the
Certificates and the System will prevent the Transferor from making
additional transfers of Certificates in Pending status.

The Pending Transactions table lists all Pending Transactions for both
the Transferor and Transferee. Once the Transferee confirm the transfer,
both the Transferor and Transferee receive an email if their
notifications are enabled.

The Transferor may cancel any transfer before a Transferee confirms the
transfer by withdrawing the transfer in the Pending Transactions table.
The Transferee may reject a transfer prior to acceptance. M-RETS will
notify both the Transferor and Transferee should either party withdraw
or reject a transfer.

### Section 4.6.2: Certificate Imports

A Compatible Certificate Tracking System is a generation tracking system
that has an operating agreement with M-RETS. Only a Compatible
Certificate Tracking System may import Certificates into M-RETS.
Similarly, M-RETS can only export Certificates to a Compatible
Certificate Tracking System. M-RETS supports open and transparent
markets.

Using the M-RETS API, M-RETS supports allowing imports and exports
between all Certificate tracking systems in North America, including
allowing for the import/export of imported/exported Certificates. If a
current system does not have import/export with M-RETS, please contact
them and ask them to establish a connection.

Certificates may be imported into M-RETS by a process of conversion.
Conversion entails retiring the Certificate from the exporting tracking
system and creation of a corresponding M-RETS Certificate. When the new
M-RETS Certificate is issued, all data fields will remain with the
imported Certificate, and the Certificate serial number will be
structured in a way to identify it as a Certificate that originated in a
Compatible Tracking System.

To import Certificates into M-RETS, the M-RETS User must arrange for the
transfer of Certificates from the counterparty privately. In general, as
with all transfers, the party in possession of the Certificates must
initiate the transfer. Therefore, the transferor will notify their
system administrator of the desire to export Certificate(s) from their
system into M-RETS, along with the information about the transferee,
such as name and M-RETS Account number. The administrator of the
transferor's tracking system will then communicate with M-RETS of the
Certificate pending Certificate conversion. M-RETS will then notify the
M-RETS User of the transfer and ask them to accept or reject the
transfer. If the User accepts the transfer, the conversion of
Certificates will ensue. Such a conversion will involve the export of
the Certificate from the exporting system, and the issuance of a new
Certificate by M-RETS. The converted Certificate will designate the
system of origin and M-RETS will maintain a record of the serial number
that was assigned in the exporting system. Through a coding system, the
M-RETS serial number will identify the Certificate as imported and the
tracking system of origin.

If the User rejects the import, M-RETS will notify the administrator of
the other system, and no Certificate conversion will take place.

### Section 4.6.3: Automatic Recurring Transfers 

Users may request Automatic Recurring Transfers of Certificates from any
Generator Fuel Type to the following:

1.  One internal Account

2.  Multiple internal Accounts

3.  An external Organization within M-RETS

4.  A Compatible Certificate Tracking System (Export)

In the registration of Automatic Recurring Transfer, the transferor must
indicate:

1.  Generator

2.  Generator Fuel

3.  Vintage Dates

4.  Destination (Account, Multiple Accounts, External Organization,
    Compatible Tracking System)

5.  Percentage or Maximum Number of Certificates

After a User initiates an Automatic Recurring Transfer ("Transferor"),
the Automatic Recurring Transfer enters a 'Pending' state. The receiving
Organization ("Transferee") then receives an email detailing the pending
Automatic Recurring Transfer.

The Transferee must accept each transfer in the System prior to the
deposit of the Certificates in the Transferee's Account. Please note: An
acceptance of an Automatic Recurring Transfer does not automatically
accept subsequent transfers. The System requires a manual acceptance by
the Transferee in case of an unwanted or incorrect Automatic Recurring
Transfer.

A User may set up multiple Automatic Recurring Transfers. However, each
Generator Fuel Type may only be associated with one Automatic Recurring
Transfer. For example, if your Generator uses both Biomass and Liquid
Biomass, you will be able to create an Automatic Recurring Transfer for
the Biomass and a separate Automatic Recurring Transfer for the Liquid
Biomass. Single-fuel Generators may only set one Automatic Recurring
Transfer at a time.

Each Automatic Recurring Transfer will be set up based on percentage of
Certificates or a maximum number of Certificates. If less Certificates
are issued than the maximum number specified, the total number of
Certificates issued will transfer. If the Certificates are transferring
to multiple Accounts, Users may prioritize the receiving Accounts. If
there is a remainder, the User-set priority determines where to deposit
the remaining Certificates.

### Section 4.6.4: Irrevocable Automatic Recurring Transfers

From a technical standpoint, Irrevocable Automatic Recurring Transfers
are like Automatic Recurring Transfers. However, only M-RETS can edit an
Irrevocable Automatic Recurring Transfer. A change requires written
electronic consent from the Transferor and Transferee. During the
creation of an Automatic Recurring Transfers, Users can select an option
to apply Irrevocable status to the Automatic Recurring Transfer.

### Section 4.6.5: Export of Certificates

M-RETS can only export Certificates to a Compatible Certificate Tracking
System. For Certificates that are exported, the cooperative agreements
between the tracking systems handle how to prevent double counting.

To export Certificates from M-RETS to a Compatible Tracking System, the
M-RETS User must select the batch of Certificates to export from an
active Account and initiate a transfer using the Export Transfer option.
The User must identify the following information:

a.  Compatible Certificate Tracking System

b.  The name of the intended recipient of the exported RECs

c.  System ID of the party receiving the transfer (if available)

After initiation, the designated Certificate is placed in a "pending"
status to ensure that the Certificates cannot be inadvertently
transferred or sold. M-RETS will communicate with the Administrator of
the Compatible Certificate Tracking System and arrange for the transfer
of Certificates. If the Compatible Certificate Tracking System accepts
the transfer, the Certificates will be removed from the M-RETS User's
active Account. The status of the Certificates will be changed from
"export pending" to "exported."

### Section 4.6.6: Re-Import of Exported Certificates

M-RETS allows imports of previously exported Certificates. If any data
fields were lost when the Certificate was originally exported, these
fields will be repopulated with the original data when the Certificate
is re-imported.
