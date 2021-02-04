# Section 4.5.4: Hourly Claims

The hourly retirement process embeds the hourly production data into the retirement claims process. This exciting achievement does more than just integrate hourly data into the claim. The process verifies that REC batches retired for hourly claims are whole and not split post issuance. The process allows for multiple batches to be retired at once and provides aggregate hourly data by hour, day, and month for the batches subject to the transaction.

M-RETS allows Hourly Claims only for intact (i.e. not subdivided after issuance) batches of Certificates. The following will render a batch of certificates ineligible for an hourly claim at this time:

1. Certificates that an Organization has separated into multiple active batches for any reason, even if they maintain ownership of all the RECs from the original issuance.

2. Certificates in a batch where RECs from the issuance batch were transferred to another party.

3. Certificates where any of the RECs from the batch as issued were retired.

In other words, Organizations may not make an Hourly Claim in the situation that separate batches of active Certificates include the entirety of the original Issuance. This may change as the market develops, and M-RETS will keep our users updated. If you have questions about whether your Certificates qualify for Hourly Claims, please contact systemadmin@mrets.org.
