## Section 4.4: Generation

Any User with Generation Upload permissions can submit MWh data into M-RETS. Each time M-RETS receives generation data for a Generator, the date and quantity of MWhs is posted to the Generation Log. Any fractional remainders (i.e. kWh) will not issue Certificates but will roll over to the next month of generation. Once uploaded, data will be labeled with one of the following:

- **Accepted** : Applies to all generation less than 1 MWh reported to M-RETS. The System will add this data to the subsequent month of generation for issuance.
- **Issued** : Applies to all generation 1 MWh or greater and indicates the Certificates are now active.
- **Pending** : Generation that fails feasibility and therefore needs M-RETS approval; or generation waiting to receive a &#39;fuel type&#39; allocation from a multi-fuel Generator. Pending Generation is not issued and therefore not represented by Active Certificates.
