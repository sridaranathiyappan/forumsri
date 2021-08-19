Content

[[_TOC_]]

`Available for review`
# Stock DestructionProcess
Stock Destruction is the process of moving the damaged stock within the Distributor from Main warehouse location  to Damage warehouse location , The actual stocks and the stock in the system should be made accurate based on stock destruction.

## Precondition for Performing Stock Destruction 
Before creating a Stock Destruction , you need to 
* Create [Distributor](Distributor) details 
* Create [Transaction Type](Transaction Type) details 
* Create [Stock Type](Stock Type) details 
* Create [UOM](UOM) details 
* Create [Product](Product) details 
* Create [Godown](Godown) details 
* Create [Depot](Depot) details 

Stock Destructionprocess vary based on 2 methods 

## Stock Destruction 

1. **Stock Destruction Date** is often set to default current date
   - There are options to allow backdated document but date after present date are restricted. 

2. **In the Godown field**, enter the name of the existing Godown
   - Stock Destructionare created to evaluate and correct  the stock available with the Distributor
   - After Godown selection, Other related information to be filed in below,  
     - default [Distributor](Distributor) and other related details are loaded.

> Further, these details are allowed to be modified as necessary.  

3. **[Reference Number](Reference Number)**
    - default Stock Destruction Reference Number are loaded, User can change these details as necessary. 

4. **[Godown](Godown)**
    - User can select the required Godown.User can change these details as necessary. 

5. **Stock Type** 
    - User can select the required stock type and change these details as necessary. 

6. Fill in or Modify the remaining fields on the Stock Destruction page as necessary.
    - Remarks
    - Transaction Type
    - Approval Remarks  

> _These are the header details requires for creation of any Stock Destruction ._
> _You are now ready to fill in the Stock Destruction lines for products that you are correcting against the Distributor Inventory_

## Addition of line level details
8. **Select a [Product](Product)** from list of eligible product for sales. 
    - After selection of line level [Product](Product), related information are pre-populated  
      - Batch details from current stock of [Distributor](Distributor)
      - [Available Qty](Stock & Inventory) 
      - [Transfer Qty](Stock & Inventory) 
      - Base [UOM](Unit of Measurement) 

9. _Repeat **Addition of line level details** Step for adding more lines of item._ 

## Amendment 
Amendment to Stock Destruction are corrections to the prepared Stock Destruction . 
Amendment is not editing in record, the amended document is referred as valid document with status amended. 

Amendment performs validation and two primary actions as below, 
  - Cancel the old document of Stock Destruction by executing all cancellation action as mentioned in [Stock Destruction cancellation section](#cancellation) 

  - Amendment of Stock Destruction are restricted to Business level restriction & Data integrity related restriction as mentioned in [cancellation](#cancellation) section. 

  - Further, Modification of key parameters are not allowed like vendor

  - A new Stock Destruction created with Stock Destruction transaction number of old document. all action performed during Stock Destruction save are applicable for the newly created Stock Destruction document. 

# Stock Destruction Configuration 
This page list all configuration applicable for Stock Destruction & related other module configuration  

> Other common configuration such as User profile based configuration, Field level configurations, Menu configurations are assumed to be as applicable similar to other modules in application. Refer [Common Application Configurations](Common Application Configurations) 
 
## Application level Configuration  

### Stock Destruction Module Configuration
| Configuration                                                                | Related Configuration | Details                                                                         | Ref #                                                     |
|------------------------------------------------------------------------------|-----------------------|---------------------------------------------------------------------------------|-----------------------------------------------------------|
|Hide Column for Total||If enabled, total column will be disabld on stock destruction screen|[FD-Conf-MAS-STKDES-0001](Stock Reconcillation#FD-Conf-MAS-STKDES-0001)|
|Hide Column for Price||If enabled, price column will be disabld on stock destruction screen|[FD-Conf-MAS-STKDES-0002](Stock Reconcillation#FD-Conf-MAS-STKDES-0002)|
|Treat reason as mandatory field||If enabled, reason column is mandatory|[FD-Conf-MAS-STKDES-0003](Stock Reconcillation#FD-Conf-MAS-STKDES-0003)|
|Treat remarks as mandatory field||If enabled, remark column is mandatory|[FD-Conf-MAS-STKDES-0004](Stock Reconcillation#FD-Conf-MAS-STKDES-0004)|
|Raise claim for the stock destruction amount||If enabled, checkbox is enabled to raise claim for stock destruction amount|[FD-Conf-MAS-STKDES-0005](Stock Reconcillation#FD-Conf-MAS-STKDES-0005)|
|Raise claim only if the attached reason(s) are selected||If enabled, claim is raised based on the configured reason as related to transaction on screen|[FD-Conf-MAS-STKDES-0006](Stock Reconcillation#FD-Conf-MAS-STKDES-0006)|
|Reason (Note: add values as comma separated)||Set config reason for column to display reason field details|[FD-Conf-MAS-STKDES-0007](Stock Reconcillation#FD-Conf-MAS-STKDES-0007)|
|Hide Stock Destruction Creation in CP||If enabled cp portal creation is disabled for stock destruction|[FD-Conf-MAS-STKDES-0008](Stock Reconcillation#FD-Conf-MAS-STKDES-0008)|
|Product hierarchy level for Stock Destruction||Set hierarchy level for product populate in stock destruction screen|[FD-Conf-MAS-STKDES-0009](Stock Reconcillation#FD-Conf-MAS-STKDES-0009)|
|Enable Product Hierarchy Based Stock Destruction||If enabled, based on product hierarchy stock destruction are created as product are populated|[FD-Conf-MAS-STKDES-0010](Stock Reconcillation#FD-Conf-MAS-STKDES-0010)|
|Enable From Date and To Date in Stock Destruction||If enabled, Two fields From and to date are enabled on stock destruction screen}|[FD-Conf-MAS-STKDES-0011](Stock Reconcillation#FD-Conf-MAS-STKDES-0011)|
|Distributor Type Based Approval|Enable Distributor Type Based Approval|If enabled, set approval configuration for stock destruction based on type and stage name|[FD-Conf-MAS-STKDES-0012](Stock Reconcillation#FD-Conf-MAS-STKDES-0012)|
|Distributor Type Based Approval||Distributor Type === set distributor type for approval|[FD-Conf-MAS-STKDES-0013](Stock Reconcillation#FD-Conf-MAS-STKDES-0013)|
|Distributor Type Based Approval||Stage name=== set stage name for the approavl based on distributor type|[FD-Conf-MAS-STKDES-0014](Stock Reconcillation#FD-Conf-MAS-STKDES-0014)|


# Business Rule & Impact 

> Business rules are listed in the below section which requires Domain understanding, hope the previous sections of the Stock Destruction are clear. Refer [Stock Destruction ](Stock Destruction ), [Stock Destruction Creation](#creation-of-sales-Invoice  )   

a) User access 

    1. Login user should has association with a Distributor. 
    1. In case of user associated with multiple user, then distributor selection is require before creating Stock Destruction transaction 
    1. User with profile access configurations are to be applied while Listing Stock Destruction , Create,View Stock Destruction 

    > Refer User profile, Distributor User, Corporate User Distributor mapping 

b)  List view of Stock Destruction 
    1. Listing page is default landing page, where newly created Stock Destruction are listed with selected information.
    1. All listing page related features are to be available for Stock Destruction listing Page. 
    1. Retrieve recently created top `20` Stock Destruction document with selected field where it belongs to a Distributor and sort with Invoice  date. Default filter for Stock Destruction applicable for all users. 
    1. Custom filter to be available for all modules
    1. Default list view fields for distributor users  
       -"Distributor"
       -"Transaction Reference no"  
       -"Date"
       -"Stock Type"
       -"Status"
       -"Next Stage Name"

    > Refer [Listing page](Listing Page) functionalities, [Custom Filter](Custom Filter).

c) Detail view actions
    1. Detail view of Stock Reconcilation record enables you to perform actions like editing, cancel, amend, print the existing record in PDF format, all actions are configured through [Workflow](Workflow). 
    1. From the Invoice  s list view, select the desired record. Details view of Stock Reconcilation record should follow the Field access rule for the login user related profile. 

d) Create Stock Destruction 
    1. Allow creation of Stock Destruction based on Profile access configuration. 
    1. User Distributor association is mandatory for creating transaction. 
    1. Corporate User are inusers create transaction related to specific associated distributor. 
    1. Creation of Stock Destruction should be restricted to user without distributor association. 

1.[FD-BR-STKDES-0001](FD-BR-STKDES-0001)- Hide Column for Total
- If enabled, total column will be disabld on stock destruction screen
- Apply Configuration Impact [FD-Conf-MAS-STKDES-0001](Stock Reconcillation#FD-Conf-MAS-STKDES-0001)

2.[FD-BR-STKDES-0002](FD-BR-STKDES-0002)-Hide Column for Price
- If enabled, price column will be disabld on stock destruction screen
-Apply Configuration Impact [FD-Conf-MAS-STKDES-0002](Stock Reconcillation#FD-Conf-MAS-STKDES-0002)

3.[FD-BR-STKDES-0003](FD-BR-STKDES-0003)-Treat reason as mandatory field
- If enabled, reason column is mandatory
- Apply Configuration Impact [FD-Conf-MAS-STKDES-0003](Stock Reconcillation#FD-Conf-MAS-STKDES-0003)

4.[FD-BR-STKDES-0004](FD-BR-STKDES-0004)-Treat remarks as mandatory field
- If enabled, remark column is mandatory
- Apply Configuration Impact [FD-Conf-MAS-STKDES-0004](Stock Reconcillation#FD-Conf-MAS-STKDES-0004)

5.[FD-BR-STKDES-0005](FD-BR-STKDES-0005)-Raise claim for the stock destruction amount
- If enabled, checkbox is enabled to raise claim for stock destruction amount
- Apply Configuration Impact [FD-Conf-MAS-STKDES-0005](Stock Reconcillation#FD-Conf-MAS-STKDES-0005)

6.[FD-BR-STKDES-0006](FD-BR-STKDES-0006)-Raise claim only if the attached reason(s) are selected
- If enabled, claim is raised based on the configured reason as related to transaction on screen
- Apply Configuration Impact [FD-Conf-MAS-STKDES-0006](Stock Reconcillation#FD-Conf-MAS-STKDES-0006)

7.[FD-BR-STKDES-0007](FD-BR-STKDES-0007)-Reason (Note: add values as comma separated)
- Set config reason for column to display reason field details
- Apply Configuration Impact [FD-Conf-MAS-STKDES-0007](Stock Reconcillation#FD-Conf-MAS-STKDES-0007)

8.[FD-BR-STKDES-0008](FD-BR-STKDES-0008)-Hide Stock Destruction Creation in CP
- If enabled cp portal creation is disabled for stock destruction
- Apply Configuration Impact [FD-Conf-MAS-STKDES-0008](Stock Reconcillation#FD-Conf-MAS-STKDES-0008)

9.[FD-BR-STKDES-0009](FD-BR-STKDES-0009)-Product hierarchy level for Stock Destruction
- Set hierarchy level for product populate in stock destruction screen
- Apply Configuration Impact [FD-Conf-MAS-STKDES-0009](Stock Reconcillation#FD-Conf-MAS-STKDES-0009)

10.[FD-BR-STKDES-0010](FD-BR-STKDES-0010)-Enable Product Hierarchy Based Stock Destruction
- If enabled, based on product hierarchy stock destruction are created as product are populated
- Apply Configuration Impact [FD-Conf-MAS-STKDES-0010](Stock Reconcillation#FD-Conf-MAS-STKDES-0010)

11.[FD-BR-STKDES-0011](FD-BR-STKDES-0011)-Enable From Date and To Date in Stock Destruction
- If enabled, Two fields From and to date are enabled on stock destruction screen}
- Apply Configuration Impact [FD-Conf-MAS-STKDES-0011](Stock Reconcillation#FD-Conf-MAS-STKDES-0011)

12.[FD-BR-STKDES-0012](FD-BR-STKDES-0012)-Distributor Type Based Approval
- Enable Distributor Type Based Approval 
- If enabled, set approval configuration for stock destruction based on type and stage name
- Apply Configuration Impact [FD-Conf-MAS-STKDES-0012](Stock Reconcillation#FD-Conf-MAS-STKDES-0012)

13.[FD-BR-STKDES-0013](FD-BR-STKDES-0013)-Distributor Type Based Approval
- Distributor Type === set distributor type for approval
- Apply Configuration Impact [FD-Conf-MAS-STKDES-0013](Stock Reconcillation#FD-Conf-MAS-STKDES-0013)

14.[FD-BR-STKDES-0014](FD-BR-STKDES-0014)-Distributor Type Based Approval
- Stage name=== set stage name for the approval based on distributor type
- Apply Configuration Impact [FD-Conf-MAS-STKDES-0014](Stock Reconcillation#FD-Conf-MAS-STKDES-0014)


# Event Flows 
## Events at Front End (Create)
  - Stock Destruction list view page 
    - Listing Stock Reconcilation document
  - While Creating Stock Reconcilation document
    - Render page based on user profile (To be explained in separate page) 
    - Listing Godown
    - Listing Stock Type
    - Listing Transaction Type  for Stock Destructiondocument
    - Listing Group 
    - Listing Product
    - On Selection of Product, retrieve relate product info, Batch details, Physical stock and system  stock position.
    - List Batch info of the product
    - List relevant Adjustment info 
 
 <!-- blank line -->
## Events at Business logic layer (overview)
- Apply Dynamic front end access control based on user profile. 
- Generate record reference number for transaction internal reference. Every request should have this reference to process, manipulate or produce data. 

- Validate the data submitted from front end - Datatype & security related. 
- Validate the data submitted from front end - Business flow related. 

**Business flow validations**

  - User chooses the 'Stock Destruction Entry' menu item. 
  - System should pick the Default Distributor details 
  - User should choose the Godown details 
  - User Should choose the Stock Type / Transaction type /Group 
  - User should click on  'Populate' option and get the list of  sku's part of selected transaction type of the selected Distributor
  - System should check the Distributor-product-pricing group and retrieve these items as qualified items for creating an Stock Destruction
  - User enter the Transfer quantity based on the available quantity and mark the reason to complete the transaction
  - Being continued,user clicks on 'Save' link.
  - System will create Stock Destruction and update the stock 
  - User clicks on 'Save' link and Stock Destruction will be created in 'Created/Publish' status.
  - User can select the 'Stock Destruction' and print the 'Stock Destruction' if required 

- Apply Transaction series
   - Pick the Auto incremental sequencing codification and Apply for the Transaction series 

- Apply business workflow logic.
  - As per configuration, apply business logic based workflow for the respective modules.
 
- Apply Log 
  - Generate access log for application. 

 <!-- blank line -->
## Events at Unified Log
### Flow of related Events  (Save)

- Stock Destruction Service scope limited to Stock Destructioncreation/amendment/cancel/delete. 
- Stock Destruction Service to trigger the related sub services which are internal and separate service. 

 <!-- blank line -->
- Report related Stock Destruction data to be updated through services. 

# See also .. 
  - [Stock Reconcilliation](Stock Destruction )
  - [Stock DestructionConfigurations](Stock Destruction Configurations)
  - [Domain Object Stock Destruction ](Domain Object Stock Destruction )
  - [Home](Home)

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTIwMTYyMTkzMTNdfQ==
-->
