Section 4.4: Generation
-----------------------

Any User with Generation Upload permissions can submit MWh data into
M-RETS. Each time M-RETS receives generation data for a Generator, the
date and quantity of MWhs is posted to the Generation Log. Any
fractional remainders (i.e. kWh) will not issue Certificates but will
roll over to the next month of generation. Once uploaded, data will be
labeled with one of the following:

-   **Accepted**: Applies to all generation less than 1 MWh reported to
    M-RETS. The System will add this data to the subsequent month of
    generation for issuance.

-   **Issued**: Applies to all generation 1 MWh or greater and indicates
    the Certificates are now active.

-   **Pending**: Generation that fails feasibility and therefore needs
    M-RETS approval; or generation waiting to receive a 'fuel type'
    allocation from a multi-fuel Generator. Pending Generation is not
    issued and therefore not represented by Active Certificates.

### 

### Section 4.4.1: Acceptable Format

A QRE or User must upload generation through the M-RETS portal. The data
must be in a .csv file format. Excel or Notepad can create a CSV file.
Programs (e.g. Microsoft Excel) that add formatting may reformat date
fields which will result in errors when loading the file. The data shall
be in ASCII Text with data fields delimited by commas (Comma-Separated
Value -- CSV format). M-RETS supports two types of reporting. Users may
upload all their generation for the whole month or in partial months as
long as a whole month is uploaded.

#### Monthly Generation Data Field Requirements

![A close up of a logo Description automatically
generated](media/image2.png){width="3.6461537620297464in"
height="0.7364654418197726in"}

1.  Generator ID: The M-RETS ID. Use just the number (e.g. M805 should
    be listed as 805).

2.  Reporting Unit ID: The Reporting Unit ID.

3.  Vintage: Month and year of generation, formatted at MM/YYYY for any
    month in the current Reporting Period. This must be 7 characters
    long or the upload will fail.

4.  Start Date of the Month: Begin month-day-year of generation output
    period formatted as MM/DD/YYYY. This must be 10 characters long or
    the upload will fail.

5.  End Date of the Month: End month-day-year of generation output
    period formatted as MM/DD/YYYY. This must be 10 characters long or
    the upload will fail.

6.  Total MWh: Total MWhs for the Reporting Month

#### Hourly Generation Data Field Requirements

![A close up of text on a white background Description automatically
generated](media/image3.png){width="2.8396620734908136in"
height="3.2447648731408574in"}

1.  Generator ID: The M-RETS ID. Use just the number (e.g. M805 should
    be listed as 805).

2.  Reporting Unit ID: The Reporting Unit ID.

3.  Date of Generation: The date the generation occurred formatted as
    MM/DD/YYYY.

4.  Total MWH: Total MWHs for the Reporting Month.

5.  Hour of Generation (1-24). All hours for the total reporting period
    must Accounted for or the file will be rejected.

6.  Total kWh for that specific hour.

Monthly generation will be uploaded in MWH. Hourly/minute data must be
uploaded in kWh.

-   Uploading by hour or minute is optional.

-   RECs are still created, retired, and transferred in MWH. Generation
    by hour or minute provide more granularity in the data associated
    with each REC batch. 

-   While generation by hour or minute increments is uploaded in kWh,
    Certificates are still only created in MWh.

> MISO also provides data with On Peak/Off Peak designation. This data
> is for informational purposes only, however, it will give Generator
> owners more information about their production. 

-   MISO defines On Peak and Off Peak in their [[FERC approved
    Tariff]{.underline} ](https://mrets.us10.list-manage.com/track/click?u=3881192bd43372fa77b8a86ab&id=51e3db43e1&e=cfa8a6389f)as: 

    -   Off-Peak: All periods of time not classified as On Peak.

    -   On Peak: Period of time between Hour-ending 0700 EST through and
        including Hour-ending 2200 Hours EST Monday through Friday
        excepting New Year's, Memorial Day, Fourth of July, Labor Day,
        Thanksgiving Day, and Christmas Day or if the holiday occurs on
        a Sunday, the Monday immediately following the holiday.

### Section 4.4.2: Uploading Time Restrictions

To encourage timely reporting, M-RETS enabled automatic validations to
generation uploads. For small Generators (1 to 150 kW nameplate
capacity), Users have up to one year from the generation end date to
upload generation. For large Generators (\>150 kW nameplate capacity),
Users have 62-days from the generation end date to upload generation.
M-RETS must approve any generation outside of these ranges. Failure to
adhere to these ranges may lead to delays in receiving Certificates.

For new Generators, M-RETS will accept generation within 62 days from
the date of registration without supplemental documentation. However,
M-RETS may accept generation which occurred between the 62-day deadline
and two years prior to the current month with a completed Variance
Request Form. Upon registration, the Organization must contact M-RETS
(<systemadmin@mrets.org>) in writing and ask that M-RETS grant a
variance. M-RETS shall review all issuance requests made outside of the
62-day window and may grant a variance if they determine that the
request is made in good faith and: that the Organization submitted their
request for a variance in writing at the time of Generator registration,
that there is a legitimate reason to issue the Certificates, and that
there is no likelihood Certificates were previously claimed or retired.
M-RETS may submit the variance request---or send an email outlining the
circumstances---to a state or provincial regulator should there be
concern compliance with the variance request could result in potential
double counting.

### Section 4.4.3: Requirements of Data Reporting Entities (QREs)

M-RETS will accept generation data from Control Area Operators,
Qualified Reporting Entities and Self-Reporting Generators.

M-RETS maintains an agreement with each of these reporting entities,
known as the Reporting Entity Terms of Use, that describes the terms and
conditions under which the reporting entity agrees to exchange
information and conduct business with M-RETS. M-RETS will maintain a
list in each QRE's Organization of the Generating Units for which the
QRE is reporting. M-RETS will outline the protocols for collection of
information such as meter IDs, data format, communication protocols and
timing, and security requirements for data collection in the Interface
Control Document. M-RETS will update this document when any changes are
made that may impact the data collection process. To minimize the impact
of document changes, this document is a general template that outlines a
common approach and set of standards. The Reporting Entity Terms of Use
contain the specific data collection parameters for each reporting
entity. M-RETS will work with the personnel from the QREs to verify
information and address specific requirements of each reporting entity.

M-RETS reserves the right to audit the MWh data totals submitted at any
time.

### Section 4.4.4: Measurement of Generation and Adjustments

M-RETS will measure the output from each Generating Unit delivered into
either the transmission or distribution grid. Certificates do not
reflect nor does M-RETS measure losses occurring on the bulk
transmission or distribution systems after the metering. M-RETS will not
create Certificates for that portion of the generation used to supply
station service. Therefore, generation data supplied to M-RETS must not
reflect station service supplied from the Generator's side of the point
of interconnection. For wholesale Generators also serving on-site loads,
M-RETS will create Certificates for the on-site load distinct from
station service, if the Generator Owner can provide evidence that the
metering used is capable of distinguishing between on-site load and
station service. Otherwise, M-RETS will assume a conservative default
fraction of total generation is station service unless it can be proved
otherwise.

If, due to metering, reporting, error or any other reason, the data
requires an adjustment, the reporting entity must report the adjustment
as soon as possible to M-RETS.

### Section 4.4.5: Changes to Issuances (Rollbacks and Prior Period Adjustments)

The User must notify M-RETS if they believe the generation data amount
recorded on the Generation Log is inaccurate for any reason. This is
known as registering a dispute. Adjustments made after the upload of
generation data to M-RETS and/or Certificate issuance are known as
Rollbacks or Prior Period Adjustments.

If the QRE or User uploaded incorrect generation data and the
Certificates remain in the issuance Account, M-RETS will Rollback the
issuance. Once the Rollback is complete, the Certificates may be
re-uploaded.

If the QRE or User uploaded incorrect generation data and the
Certificates do not remain in the issuance Account, a Prior Period
Adjustment is required. M-RETS will post the Prior Period Adjustment to
the Generation Log associated with the Generating Unit. This will have
the effect of applying a credit or debit to the generation amount
reported in the current month. Consequently, the adjustment occurs upon
the next Certificate issuance. If new Certificates are created, the
month of creation of the Certificates shall be the same as all other
Certificates created that month, however the Certificates will also
indicate the month the prior period generation occurred.

If a User requests a Rollback outside of the acceptable upload range,
M-RETS may require evidence of data inaccuracy. This includes, but is
not limited to:

a.  Screenshot(s) of internal readings

b.  Official readouts of generation

All requests for Rollbacks and Prior Period Adjustments are subject to
review by M-RETS.

### Section 4.4.6: Data Transmittal

Users must electronically transfer data files to M-RETS using a secured
protocol and a standard format specified by M-RETS. The data shall
reflect, at a minimum, the month and year of the generation, monthly
accumulated MWhs for each meter ID and the associated meter ID(s) for
each resource.

The data must be transmitted by a single entity, which must be either
(1) the Control Area Operator, or (2) a QRE, or (3) a Self-Reporting
Generator.
