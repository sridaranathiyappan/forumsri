Content

[[_TOC_]]

`Available for review`
# Merchandizing Process
Merchandizing is the process of managing the visibility of the items in primary and secondary shelf at the retailer place. It gives the provision to record the stock position at  both the shelf.

## Precondition for Performing the Merchandizing Activity
Before creating a Merchandizing part , you need to 
* Create [Distributor](Distributor) details 
* Create [Salesman](Salesman) details 
* Create [Godown](Godown) details 
* Create [Beat](Beat) details 
* Create [Product](Product) details 
* Create [Product Category](Product Category) details 
* Create [Reason](Reason) details 
* Create [Customer](Customer) details 
* Create [Merchandize Type](Merchandize Type) details 
* Create [Display Type](Display Type) details 

## Merchandizing Process

1. **Merchandizing creation Date** is often set to default current date
   - There are options to allow backdated document but date after present date are restricted. 

2. **In the Godown field**, enter the name of the existing Godown
   - Merchandizing Process are created to evaluate and correct  the stock available at the customer place 
   - After Godown selection, Other related information to be filed in below,  
     - default [Distributor](Distributor) and other related details are loaded.

> Further, these details are allowed to be modified as necessary.  

3. **[Godown](Godown)**
    - User can select the required Godown.User can change these details as necessary. 

4. **[Salesman Name](Salesman Name)**
    -  User can select the Salesman name based on the list been displayed , User can change these details as necessary. 

5. **Beat** 
    - User can select the required Beat based on selected salesman and change these details as necessary. 

6. **Customer** 
    - User can select the required customer based on selected Beat and change these details as necessary. 

7. Fill in or Modify the remaining fields on the Merchandizing Process page as necessary.
    - Remarks
    - Reason

8. **Product Category** 
    - User can select the required product hierrachy based on porduct categoryand change these details as necessary. 

> _These are the header details requires for creation of any Merchandizing Process ._
> _You are now ready to fill in the Merchandizing Process lines for products that you are correcting against the Distributor Inventory_

## Addition of line level details
9. **Select a [Product](Product)** from list of eligible product for sales. 
    - After selection of line level [Product](Product), related information are pre-populated  
      - Batch details from current stock of [Distributor](Distributor)
      - [Available Qty](Stock & Inventory) 
      - [Issue Qty](Stock & Inventory) 

10. _Repeat **Addition of line level details** Step for adding more lines of item._ 

## Amendment 
Amendment to Merchandizing activity are corrections to the prepared Merchandizing document. 
Amendment is not editing in record, the amended document is referred as valid document with status amended. 

Amendment performs validation and two primary actions as below, 
  - Cancel the old document of Merchandizing Process by executing all cancellation action as mentioned in [Merchandizing Process cancellation section](#cancellation) 

  - Amendment of Merchandizing Process are restricted to Business level restriction & Data integrity related restriction as mentioned in [cancellation](#cancellation) section. 

  - Further, Modification of key parameters are not allowed like vendor

  - A new Merchandizing Process created with Merchandizing Process transaction number of old document. all action performed during Merchandizing Process save are applicable for the newly created Merchandizing Process document. 

# Merchandizing Process Configuration 
This page list all configuration applicable for Merchandizing Process & related other module configuration  

> Other common configuration such as User profile based configuration, Field level configurations, Menu configurations are assumed to be as applicable similar to other modules in application. Refer [Common Application Configurations](Common Application Configurations) 
 
## Application level Configuration  

### Merchandizing Process Module Configuration
| Configuration                                                                | Related Configuration | Details                                                                         | Ref #                                                     |
|------------------------------------------------------------------------------|-----------------------|---------------------------------------------------------------------------------|-----------------------------------------------------------|
|Product hierarchy level for Merchadising Product||If enabled, Product hierarchy level for Merchadising Product will be loaded based on config|[FD-Conf-MAS-MERCHDZ-0001](Merchandizing document#FD-Conf-MAS-MERCHDZ-0001)|
|Disable direct creation of Merchadising Receipt||If enabled, Merchendising receipt creation icon will be disabled|[FD-Conf-MAS-MERCHDZ-0002](Merchandizing document#FD-Conf-MAS-MERCHDZ-0002)|
|Automatic conversion of Receive Merchadising Issue to Merchadising Issue||If enabled, Automatic conversion of Receive Merchadising Issue to Merchadising Issue will be processed|[FD-Conf-MAS-MERCHDZ-0003](Merchandizing document#FD-Conf-MAS-MERCHDZ-0003)|

# Business Rule & Impact 

> Business rules are listed in the below section which requires Domain understanding, hope the previous sections of the Merchandizing Process are clear. Refer [Merchandizing Process ](Merchandizing Process ), [Merchandizing Process Creation](#creation-of-sales-Invoice  )   

a) User access 

    1. Login user should has association with a Distributor. 
    1. In case of user associated with multiple user, then distributor selection is require before creating Merchandizing Process transaction 
    1. User with profile access configurations are to be applied while Listing Merchandizing Process , Create,View Merchandizing Process 

    > Refer User profile, Distributor User, Corporate User Distributor mapping 

b)  List view of Merchandizing Process 
    1. Listing page is default landing page, where newly created Merchandizing Process are listed with selected information.
    1. All listing page related features are to be available for Merchandizing Process listing Page. 
    1. Retrieve recently created top `20` Merchandizing Process document with selected field where it belongs to a Distributor and sort with Invoice  date. Default filter for Merchandizing Process applicable for all users. 
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

d) Create Merchandizing Process 
    1. Allow creation of Merchandizing Process based on Profile access configuration. 
    1. User Distributor association is mandatory for creating transaction. 
    1. Corporate User are inusers create transaction related to specific associated distributor. 
    1. Creation of Merchandizing Process should be restricted to user without distributor association. 

1.[FD-BR-MERCHDZ-0001](FD-BR-MERCHDZ-0001)- Product hierarchy level for Merchadising Product
- If enabled, Product hierarchy level for Merchadising Product will be loaded based on config
- Apply Configuration Impact [FD-Conf-MAS-MERCHDZ-0001](Merchandizing document#FD-Conf-MAS-MERCHDZ-0001)

2.[FD-BR-MERCHDZ-0002](FD-BR-MERCHDZ-0002)- Disable direct creation of Merchadising Receipt
- If enabled, Merchendising receipt creation icon will be disabled
- Apply Configuration Impact [FD-Conf-MAS-MERCHDZ-0002](Merchandizing document#FD-Conf-MAS-MERCHDZ-0002)

3.[FD-BR-MERCHDZ-0003](FD-BR-MERCHDZ-0003)- Automatic conversion of Receive Merchadising Issue to Merchadising Issue
- If enabled, Automatic conversion of Receive Merchadising Issue to Merchadising Issue will be processed
- Apply Configuration Impact [FD-Conf-MAS-MERCHDZ-0003](Merchandizing document#FD-Conf-MAS-MERCHDZ-0003)

# Event Flows 
## Events at Front End (Create)
  - Merchandizing Process list view page 
    - Listing Merchandize documents
    - Render page based on user profile
    - Listing Godown
    - Listing Salesman
    - Listing Beat
    - Listing Customer
    - Listing Product Category
    - Listing Merchandize Issue code for Merchandizing Process document
    - Listing Product,Product Type,Display Type
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

  - User chooses the 'Merchandizing Process Entry' menu item. 
  - System should pick the Default Distributor details 
  - User should choose the Godown details 
  - User Should choose the Salesman / Beat /Customer 
  - User should click on  'Populate' option and get the list of  sku's part based on selected product Category for the selected Distributor
  - System should check the Distributor-product-pricing group and retrieve these items as qualified items for creating an Merchandizing document
  - User enter the Transfer quantity based on the available quantity and mark the reason to complete the transaction
  - Being continued,user clicks on 'Save' link.
  - System will create Merchandizing Process and update the stock 
  - User clicks on 'Save' link and Merchandizing Process will be created in 'Created/Publish' status.
  - User can select the 'Merchandizing Process' and print the 'Merchandizing Process' if required 

- Apply Transaction series
   - Pick the Auto incremental sequencing codification and Apply for the Transaction series 

- Apply business workflow logic.
  - As per configuration, apply business logic based workflow for the respective modules.
 
- Apply Log 
  - Generate access log for application. 

 <!-- blank line -->
## Events at Unified Log
### Flow of related Events  (Save)

- Merchandizing Process Service scope limited to Merchandizing Processcreation/amendment/cancel/delete. 
- Merchandizing Process Service to trigger the related sub services which are internal and separate service. 

 <!-- blank line -->
- Report related Merchandizing Process data to be updated through services. 

# See also .. 
  - [Merchandizing Process](Merchandizing Process )
  - [Merchandizing ProcessConfigurations](Merchandizing Process Configurations)
  - [Domain Object Merchandizing Process ](Domain Object Merchandizing Process )
  - [Home](Home)

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTIwMTYyMTkzMTNdfQ==
-->
