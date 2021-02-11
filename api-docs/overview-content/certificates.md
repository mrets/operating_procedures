# Certificates Overview

RECs (Renewable Energy Certificates) created and tracked within M-RETS represent all renewable attributes from one MWh of renewable generation. The system only issues RECs in whole numbers. M-RETS RECs are “Whole Certificates,” meaning that none of the renewable attributes may be split off from the Certificate while it is in circulation in the M-RETS system. M-RETS only creates Certificates for renewable and recycled fuel types. See the below resources for more extensive resources on RECs, REC policies, and REC markets.

RECs are represented in the system by the `Certificate` and `Certificate Quantity` objects. The `Certificate` object contains immutable attributes such as the vintage, state or province, and associations such as to the `Generation Entry` and `Eligibilities`. 

The `Certificate Quantity` is associated with the `Certificate` and represents a specific range of serial numbers. Upon issuance, an instance of a `Certificate` is created along with one associated `Certificate Quantity` that represents the complete range of certificates equivalent. This should be nearly equivalent to submit generation (See the Generation Entry overview section for further information on how M-RETS handles remainders.) During the life cycle of a batch of certificate quantities, they could be split into multiple batches by completing a transaction. Say for example an external transfer is completed with only half of the original issued of certificates quantity. When this occurs, the original `Certificate Quantity` instance is deleted and replaced by two new instances, one representing the serial numbers that have been transferred, and the other representing the serial numbers that remained in the original account. 


## Resources
