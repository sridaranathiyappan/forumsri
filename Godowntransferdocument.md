Content

[[_TOC_]]

`Available for review`
#  Godown Transfer Process
Godown Transfer is the process of moving the stocks from One to the Another Warehouse based on stock type selection within the Distributor, it will be done every day or weekly once. In this process actual system stocks are considered as base reference and used to transfer the stock between the Godowns with in the Distributor.

## Precondition for Performing  Godown Transfer  
Before creating a  Godown Transfer  , you need to 
* Create [Distributor](Distributor) details 
* Create [Godown](Godown) details 
* Create [Mode of Transferl](Mode of Transfer) details 
* Create [Reference number series](Reference number series) details 
 Create [Transaction series](Transaction series) details 
* Create [Product](Product) details 
* Create [Stock Type](Stock Type) details 

 Godown Transfer process vary based on 2 methods 

##  Godown Transfer  

1. ** Godown Transfer  Date** is often set to default current date
   - There are options to allow backdated Godown Transfer but date after present date are restricted. 

2. **In the Godown field**, enter the name of the existing Godown
   -  Godown Transfer are created to manage the stock movement between the Godowns within the Distributor
   - After Godown selection, Other related information to be filed in below,  
     - default [Distributor](Distributor) and other related details are loaded.

> Further, these details are allowed to be modified as necessary.  

3. **[Reference Number](Reference Number)**
    - default  Godown Transfer  Reference Number are loaded, User can change these details as necessary. 

5. **Stock Type** 
    - User can select the required stock type and change these details as necessary. 

6. Fill in or Modify the remaining fields on the  Godown Transfer  page as necessary.
    - Reason
    - Remarks
    - Transaction Series 

> _These are the header details requires for creation of any  Godown Transfer ._
> _You are now ready to fill in the  Godown Transfer  lines for products that you are correcting against the Distributor Inventory_

## Addition of line level details
7. **Select a [Product](Product)** from list of eligible product for sales. 
    - After selection of line level [Product](Product), related information are pre-populated  
      - Batch details from current stock of [Distributor](Distributor)
      - [From Godown](Distributor Godown) 
      - [To Location](Distributor Godown) 
      - [From Stock Type](From Stock Type)
      - [To Stock Type](To Stock Type)
      - [Available Quantity](Available Quantity)
      - [Transfer Quantity](Transafer Quantity)

8. _Repeat **Addition of line level details** Step for adding more lines of item._ 

## Amendment 
Amendment to  Godown Transfer  are corrections to the prepared  Godown Transfer  . 
Amendment is not editing in record, the amended document is referred as valid document with status amended. 

Amendment performs validation and two primary actions as below, 
  - Cancel the old document of  Godown Transfer  by executing all cancellation action as mentioned in [ Godown Transfer  cancellation section](#cancellation) 

  - Amendment of  Godown Transfer  are restricted to Business level restriction & Data integrity related restriction as mentioned in [cancellation](#cancellation) section. 

  - Further, Modification of key parameters are not allowed like vendor

  - A new  Godown Transfer  created with  Godown Transfer  transaction number of old document. all action performed during  Godown Transfer  save are applicable for the newly created  Godown Transfer  document. 

#  Godown Transfer  Configuration 
This page list all configuration applicable for  Godown Transfer  & related other module configuration  

> Other common configuration such as User profile based configuration, Field level configurations, Menu configurations are assumed to be as applicable similar to other modules in application. Refer [Common Application Configurations](Common Application Configurations) 
 
## Application level Configuration  

###  Godown Transfer  Module Configuration
| Configuration                                                                | Related Configuration | Details                                                                         | Ref #                                                     |
|------------------------------------------------------------------------------|-----------------------|---------------------------------------------------------------------------------|-----------------------------------------------------------|
|Treat reason as mandatory field||If eanbled. reason column is mandatory|[FD-Conf-MAS-GDTRANS-0001](Stock Reconcillation#FD-Conf-MAS-GDTRANS-0001)|
|Treat remarks as mandatory field||If enabled, remark column is mandatory|[FD-Conf-MAS-GDTRANS-0002](Stock Reconcillation#FD-Conf-MAS-GDTRANS-0002)|
|Restrict Free Quantity on Godown Transfer||If enabled, free quantity is restricted on Godown Transfer|[FD-Conf-MAS-GDTRANS-0003](Stock Reconcillation#FD-Conf-MAS-GDTRANS-0003)|
|Validate to allow only digits for transfer quantity||If enabled, decimal values are restricted, only digit are allowed on quantity column|[FD-Conf-MAS-GDTRANS-0004](Stock Reconcillation#FD-Conf-MAS-GDTRANS-0004)|

# Business Rule & Impact 

> Business rules are listed in the below section which requires Domain understanding, hope the previous sections of the  Godown Transfer  are clear. Refer [ Godown Transfer  ]( Godown Transfer  ), [ Godown Transfer  Creation](#creation-of-sales-Invoice  )   

a) User access 

    1. Login user should has association with a Distributor. 
    1. In case of user associated with multiple user, then distributor selection is require before creating  Godown Transfer  transaction 
    1. User with profile access configurations are to be applied while Listing  Godown Transfer  , Create,View  Godown Transfer  

    > Refer User profile, Distributor User, Corporate User Distributor mapping 

b)  List view of  Godown Transfer  
    1. Listing page is default landing page, where newly created  Godown Transfer  are listed with selected information.
    1. All listing page related features are to be available for  Godown Transfer  listing Page. 
    1. Retrieve recently created top `20`  Godown Transfer  document with selected field where it belongs to a Distributor and sort with Invoice  date. Default filter for  Godown Transfer  applicable for all users. 
    1. Custom filter to be available for all modules
    1. Default list view fields for distributor users  
          -"Transaction Number"
          -"Reference Number"
          -"Date"
          -"Mode of Transfer"
          -"Status"
          -"Next Stage Name"

    > Refer [Listing page](Listing Page) functionalities, [Custom Filter](Custom Filter).

c) Detail view actions
    1. Detail view of Stock Reconcilation record enables you to perform actions like editing, cancel, amend, print the existing record in PDF format, all actions are configured through [Workflow](Workflow). 
    1. From the Invoice  s list view, select the desired record. Details view of Stock Reconcilation record should follow the Field access rule for the login user related profile. 

d) Create  Godown Transfer  
    1. Allow creation of  Godown Transfer  based on Profile access configuration. 
    1. User Distributor association is mandatory for creating transaction. 
    1. Corporate User are inusers create transaction related to specific associated distributor. 
    1. Creation of  Godown Transfer  should be restricted to user without distributor association. 

1.[FD-BR-GDTRANS-0001](FD-BR-GDTRANS-0001)- Treat reason as mandatory field
- If eanbled. reason column is mandatory
- Apply Configuration Impact [FD-Conf-MAS-GDTRANS-0001](Stock Reconcillation#FD-Conf-MAS-GDTRANS-0001)

2.[FD-BR-GDTRANS-0002](FD-BR-GDTRANS-0002)Treat remarks as mandatory field
- If enabled, remark column is mandatory
- Apply Configuration Impact [FD-Conf-MAS-GDTRANS-0002](Stock Reconcillation#FD-Conf-MAS-GDTRANS-0002)

3.[FD-BR-GDTRANS-0003](FD-BR-GDTRANS-0003)Restrict Free Quantity on Godown Transfer
- If enabled, free quantity is restricted on Godown Transfer
- Apply Configuration Impact [FD-Conf-MAS-GDTRANS-0003](Stock Reconcillation#FD-Conf-MAS-GDTRANS-0003)

4.[FD-BR-GDTRANS-0004](FD-BR-GDTRANS-0004)Validate to allow only digits for transfer quantity
- If enabled, decimal values are restricted, only digit are allowed on quantity column
- Apply Configuration Impact [FD-Conf-MAS-GDTRANS-0004](Stock Reconcillation#FD-Conf-MAS-GDTRANS-0004)

# Event Flows 
## Events at Front End (Create)
  -  Godown Transfer list view page 
    - Listing Godown Transfer document
  - While Creating Godown Transfer document
    - Render page based on user profile (To be explained in separate page) 
    - Listing Transaction Series 
    - Listing Mode of Transfer
    - Auto populate incremental sequencing of Reference Number for  Godown Transfer document
    - Listing Product
    - On Selection of Product, retrieve relate product info, Batch details, Stock Types.
    - List Batch info of the product
    - List Available Stock Qty relevant Adjustment info 
 
 <!-- blank line -->
## Events at Business logic layer (overview)
- Apply Dynamic front end access control based on user profile. 
- Generate record reference number for transaction internal reference. Every request should have this reference to process, manipulate or produce data. 

- Validate the data submitted from front end - Datatype & security related. 
- Validate the data submitted from front end - Business flow related. 

**Business flow validations**

  - User chooses the ' Godown Transfer  Entry' menu item. 
  - User should choose the Mode of Transfer details 
  - Based on configuration workflow , Mode of Transfer can also set as default mode 
  - User should either select Transaction series or set as default Transaction series based on configuration
  - System should pick the Default Distributor details 
  - System should pick the all the sku's part of count sheet document (I.e Physical stock tale document) of the selected Distributor
  - System should check the Distributor-product-pricing group and retrieve these items as qualified items for creating an  Godown Transfer 
  - System should populate the Available stock for the selected item
  - User should choose the Transer quantity for the selected Item and capture the remarks for the same items 
  - Being continued,user clicks on 'Save' link.
  - System will create  Godown Transfer  and update the stock position in relevant Godown
  - Godown Transfer  will be created in 'Created/Publish' status.
  - User can select the ' Godown Transfer ' and print the ' Godown Transfer ' if required 

- Apply Transaction series
   - Pick the Auto incremental sequencing codification and Apply for the Transaction series 

- Apply business workflow logic.
  - As per configuration, apply business logic based workflow for the respective modules.
 
- Apply Log 
  - Generate access log for application. 

 <!-- blank line -->
## Events at Unified Log
### Flow of related Events  (Save)

-  Godown Transfer  Service scope limited to  Godown Transfer creation/amendment/cancel/delete. 
-  Godown Transfer  Service to trigger the related sub services which are internal and separate service. 

- Report related  Godown Transfer  data to be updated through services. 

# See also .. 
  - [ Godown Transfer]( Godown Transfer  )
  - [ Godown Transfer Configurations]( Godown Transfer  Configurations)
  - [Domain Object  Godown Transfer  ](Domain Object  Godown Transfer  )
  - [Home](Home)

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTIwMTYyMTkzMTNdfQ==
-->
