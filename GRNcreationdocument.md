Content

[[_TOC_]]

`Available for review`
# Creation of GRN
 GRN is a process to inward the Stock into the Distributor warehouse based on the purchase Invoice that has get received from the supplier Plant end , GRN Process will get done by distributor operator at Distributor location through Distributor Portal

## Precondition for creating GRN 
Before creating a direct GRN , you need to 
* Create [Vendor](Vendor) details 
* Create [Godown](Godown) details 
* Create [Distributor](Distributor) details 
* Create [Depot](Depot) details 

Creation of GRN vary based on type of creation. 

## To Create GRN 

1. **GRN Date** is often set to default current date
   - There are options to allow backdated Invoice  but date after present date are restricted. 

2. **In the Vendor field**, enter the name of an existing Vendor
   - GRN are created to document the Inwarding of Stock based into the distributor Warehouse/Godown
   - After Vendor selection, Other related information to be filed in below,  
     - default [Godown](Godown), 
     - default [Depot](Depot) are loaded.

> Further, these details are allowed to be modified as necessary.  

3. **[Transaction Series](Transaction Series)**
    - default GRN Transaction Series are loaded, User can change these details as necessary. 

4. **Purchase Invoice Billdate** 
    - default purchase Invoice Billdate are get loaded based on configuration. 

5. Fill in or Modify the remaining fields on the GRN page as necessary.
    - Remark 
    - Reason  

> _These are the header details requires for creation of any GRN ._
> _You are now ready to fill in the GRN lines for products that you are selling to the Customer._

## Addition of line level details
6. **Select a [Product](Product)** from list of eligible product for sales. 
    - After selection of line level [Product](Product), related information are pre-populated  
     - Inventory Qty of [Distributor](Distributor)
     - Received Qty of [Distributor](Distributor)
      - Batch details from current stock of [Distributor](Distributor)
      - Damaged Qty of [Distributor](Distributor)
      - Price to customer [PTR](#rate-calculation)
      - [Available Stock Quantity](Stock & Inventory) 
      - Purchase [UOM](Unit of Measurement) 
      - [Applicable Tax](#rate-calculation) 

7. **Provide the GRN quantity**
    - After providing the GRN quantity, 
      - The value in the Line Amount field is calculated as Unit Price x Quantity. 
      - [Applies Tax](#tax) based on predefined [Tax Master](Tax Master) settings
      - Line level [Net Amount](GRN Calculation) is calculated. 

8. **Net amount** is computed 
    - _refer [GRN calculation logic](#rate-calculation)_

9. _Repeat **Addition of line level details** Step for adding more lines of item._ 

## Cancellation 
Cancellation of GRN are action performed. The reason may vary like "Wrongly created GRN ". Cancelled Invoice  are considered as valid document and used in all reports

Cancellation of GRN are restricted based on configuration & workflow, few points as below. 

  - Business level restriction may vary based on configuration.  
    - Posted GRN are not allowed to cancel, Instead Stock Destruction can be used to manage the cancellation and maintain the logical accounting transactions. 

  - Data integrity related restrictions
    - Validation fails if the Distributor Invoice  amount update creates zero value scenario due to Zero price exist in the system against any line item. 
    - Deactivated master reference like product, distributor . will have impact to fail the cancellations. 

On Cancel of GRN document, 
  - Document marked for status change to indicate cancellation. 
  - Report related GRN data to be recomputed. 

## Amendment 
Amendment to GRN are corrections to the prepared GRN . 
Amendment is not editing in record, the amended document is referred as valid document with status amended. 

Amendment performs validation and two primary actions as below, 
  - Cancel the old document of GRN by executing all cancellation action as mentioned in [GRN cancellation section](#cancellation) 

  - Amendment of GRN are restricted to Business level restriction & Data integrity related restriction as mentioned in [cancellation](#cancellation) section. 

  - Further, Modification of key parameters are not allowed like vendor

  - A new GRN created with GRN transaction number of old document. all action performed during GRN save are applicable for the newly created GRN document. 

# GRN Configuration 
This page list all direct configuration applicable for GRN & related other module configuration  

> Other common configuration such as User profile based configuration, Field level configurations, Menu configurations are assumed to be as applicable similar to other modules in application. Refer [Common Application Configurations](Common Application Configurations) 
 
## Application level Configuration  

### GRN Module Configuration
| Configuration                                                                | Related Configuration | Details                                                                         | Ref #                                                     |
|------------------------------------------------------------------------------|-----------------------|---------------------------------------------------------------------------------|-----------------------------------------------------------|
|Currency Option Enable||If enabled, Currency Option column will be displayed on GRN screen|[FD-Conf-MAS-GRN-0001](GRN Creation#FD-Conf-MAS-GRN-0001)|
|System Transaction Number||If enabled, allow to generate transaction number based on configured system transaction number for GRN transaction|[FD-Conf-MAS-GRN-0002](GRN Creation#FD-Conf-MAS-GRN-0002)|
|Allow Selection of Vendor||If enabled, vendor column is loaded and allow user to select field data,If not, default vendor will be loaded and selcted|[FD-Conf-MAS-GRN-0003](GRN Creation#FD-Conf-MAS-GRN-0003)|
|List Price Editable or Readonly||If enabled, List Price Editable by user.If not, List Price Editable cant be editabled by user|[FD-Conf-MAS-GRN-0004](GRN Creation#FD-Conf-MAS-GRN-0004)|
|Allow Direct GRN Creation||If enabled, user can create direct GRN.If not, user is restricted on creation of GRN screen|[FD-Conf-MAS-GRN-0005](GRN Creation#FD-Conf-MAS-GRN-0005)|
|Allow Back Dated Transaction||If enabled, user is allowed to create back dated GRN transaction|[FD-Conf-MAS-GRN-0006](GRN Creation#FD-Conf-MAS-GRN-0006)|
|Update Stock based on Purchase bill date in GRN when Date wise Inventory is ON||If enabled, stock updated based on purchase bill date in GRN transaction|[FD-Conf-MAS-GRN-0007](GRN Creation#FD-Conf-MAS-GRN-0007)|

# Business Rule & Impact 

> Business rules are listed in the below section which requires Domain understanding, hope the previous sections of the GRN are clear. Refer [GRN ](GRN ), [GRN Creation](#creation-of-sales-Invoice  )   

1. [FD-BR-GRN-0001] - User access 

>  FD-BR-GRN-0001

    1. Login user should has association with a Distributor. 
    1. In case of user associated with multiple user, then distributor selection is require before creating GRN transaction 
    1. User with profile access configurations are to be applied while Listing GRN , Create, Modify, View GRN 

    > Refer User profile, Distributor User, Corporate User Distributor mapping 

2. [FD-BR-GRN-0002](#FD-BR-GRN-0002) - List view of GRN 
    1. Listing page is default landing page, where newly created GRN are listed with selected information.
    1. All listing page related features are to be available for GRN listing Page. 
    1. Retrieve recently created top `20` GRN document with selected field where it belongs to a Distributor and sort with Invoice  date. Default filter for GRN applicable for all users. 
    1. Custom filter to be available for all modules
    1. Default list view fields for distributor users  
        - "transactionNumber" 
        - "GRN Date" 
        - "referencenumber" 
        - "Vendor Name"
        - "Depot"
        - "Godown"

    > Refer [Listing page](Listing Page) functionalities, [Custom Filter](Custom Filter).

3. [FD-BR-GRN-0003](FD-BR-GRN-0003) - Detail view actions
    1. Detail view of Invoice  record enables you to perform actions like editing, cancel, amend, print the existing record in PDF format, all actions are configured through [Workflow](Workflow). 
    1. From the Invoice  s list view, select the desired record. Details view of Invoice  record should follow the Field access rule for the login user related profile. 

4. [FD-BR-GRN-0004](FD-BR-GRN-0004) - Create GRN 
    1. Allow creation of GRN based on Profile access configuration. 
    1. User Distributor association is mandatory for creating transaction. 
    1. Corporate User are indirect users create transaction related to specific associated distributor. 
    1. Creation of GRN should be restricted to user without distributor association

5. [FD-BR-GRN-0005](FD-BR-GRN-0005) - Create GRN Transaction Series 
    1.Set the provison to enable or disable the Transaction series to automate the GRN document series generation 

6. [FD-BR-GRN-0006](FD-BR-GRN-0006) - Create Direct GRN Transaction
    1.Allow user to create Direct GRN without any sales Invoice reference 

7. [FD-BR-GRN-0007](FD-BR-GRN-0007) - Create Backdated GRN Transaction
    1.Allow user to create Back Dated GRN    

# Event Flows 
## Events at Front End (Create)
  - GRN list view page 
    - Listing Purchase  Invoice 
  - While Creating Purchase  Invoice 
    - Render page based on user profile (To be explained in separate page) 
    - Listing Vendor
    - Listing Depot
    - Listing Godown
    - Listing Transaction Series for GRN
    - Listing Product
    - On Selection of Product, retrieve relate product info, Batch details, Tax info, Scheme info, current stock position.
    - List Batch info of the product
    - List relevant Adjustment info 
 
 <!-- blank line -->
## Events at Business logic layer (overview)
- Apply Dynamic front end access control based on user profile. 
- Generate record reference number for transaction internal reference. Every request should have this reference to process, manipulate or produce data. 

- Validate the data submitted from front end - Datatype & security related. 
- Validate the data submitted from front end - Business flow related. 

**Business flow validations**

  - User chooses the 'GRN Entry' menu item. 
  - User should choose the Vendor details 
  - System should pick the Default Distributor details
  - System should pick the Supplier Address and shipping address of the selected Distributor
  - System should check the Distributor-product-pricing group and retrieve these items as qualified items for creating an GRN
  - User enters the product id/product name and desired quantity in respective fields.
  - User clicks on [Add item] button to add the next item.
  - System adds the desired product in draft mode 
  - Being continued,user clicks on 'Save' GRN link.
  - System will create GRN and update the stock inward details and total amount 
  - User clicks on 'Save' link and GRN will be created in 'Created/Publish' status.
  - User can select the 'GRN' and print the 'GRN' if required 

# See also .. 
  - [GRN ](GRN )
  - [GRN Configurations](GRN Configurations)
  - [Domain Object GRN ](Domain Object GRN )
  - [Home](Home)

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTIwMTYyMTkzMTNdfQ==
-->
