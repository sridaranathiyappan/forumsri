Content

[[_TOC_]]

`Available for review`
# Stock Reconcilliation Process
Stock Reconciliation is the process of counting and evaluating stock available with the Distributor, usually at an Distributor level in order to value the total stock for preparation of the accounts it will be done every day or weekly once. In this process actual physical stocks are checked and recorded in the system. The actual stocks and the stock in the system should be accurate.It will get created by Supplier from Plant location.  

## Precondition for Performing Stock Reconcilliation  
Before creating a Stock Reconcilliation  , you need to 
* Create [Distributor](Distributor) details 
* Create [Hierarchy Level](Hierarchy Level) details 
* Create [Hierarchy Level Value](Hierarchy Level Value) details 
* Create [Product](Product) details 
* Create [Stock Type](Stock Type) details 
* Create [Godown](Godown) details 
* Create [Count Sheet](Physical Stock taking) details 

Stock Reconcilliation process vary based on 2 methods 

## Stock Reconcilliation  

1. **Stock Reconcilliation  Date** is often set to default current date
   - There are options to allow backdated Document but date after present date are restricted. 

2. **In the Godown field**, enter the name of the existing Godown
   - Stock Reconcilliation are created to evaluate the stock available with the Distributor
   - After Godown selection, Other related information to be filed in below,  
     - default [Distributor](Distributor) and other related details are loaded.

> Further, these details are allowed to be modified as necessary.  

3. **[Reference Number](Reference Number)**
    - default Stock Reconcilliation  Reference Number are loaded, User can change these details as necessary. 

4. **[Count sheet No](Count sheet No)**
    - User can select the required Count sheet no which has got generated during the Physical stock take.User can change these details as necessary. 

5. **Stock Type** 
    - User can select the required stock type and change these details as necessary. 

6. Fill in or Modify the remaining fields on the Stock Reconcilliation  page as necessary.
    - Remarks
    - Status
    - Approval Remarks  

> _These are the header details requires for creation of any Stock Reconcilliation  ._
> _You are now ready to fill in the Stock Reconcilliation  lines for products that you are correcting against the Distributor Inventory_

## Addition of line level details
8. **Select a [Product](Product)** from list of eligible product for sales. 
    - After selection of line level [Product](Product), related information are pre-populated  
      - Batch details from current stock of [Distributor](Distributor)
      - [Physical stock](Stock & Inventory) 
      - [System stock](Stock & Inventory) 
      - Base [UOM](Unit of Measurement) 

9. **Populate the System Stock quntity**
    - After providing the Physical stock quantity,Populate the system stock icon, So that Variance will get Autocomputed and get published 
      - [Variance](Variance)
      - [Reason](Reason is an Optional)
      - [Reconcile](Reconcile)

10. _Repeat **Addition of line level details** Step for adding more lines of item._ 

## Amendment 
Amendment to Stock Reconcilliation  are corrections to the prepared Stock Reconcilliation  . 
Amendment is not editing in record, the amended document is referred as valid document with status amended. 

Amendment performs validation and two primary actions as below, 
  - Cancel the old document of Stock Reconcilliation  by executing all cancellation action as mentioned in [Stock Reconcilliation  cancellation section](#cancellation) 

  - Amendment of Stock Reconcilliation  are restricted to Business level restriction & Data integrity related restriction as mentioned in [cancellation](#cancellation) section. 

  - Further, Modification of key parameters are not allowed like vendor

  - A new Stock Reconcilliation  created with Stock Reconcilliation  transaction number of old document. all action performed during Stock Reconcilliation  save are applicable for the newly created Stock Reconcilliation  document. 

# Stock Reconcilliation  Configuration 
This page list all configuration applicable for Stock Reconcilliation  & related other module configuration  

> Other common configuration such as User profile based configuration, Field level configurations, Menu configurations are assumed to be as applicable similar to other modules in application. Refer [Common Application Configurations](Common Application Configurations) 
 
## Application level Configuration  

### Stock Reconcilliation  Module Configuration
| Configuration                                                                | Related Configuration | Details                                                                         | Ref #                                                     |
|------------------------------------------------------------------------------|-----------------------|---------------------------------------------------------------------------------|-----------------------------------------------------------|
|Disable Populate System Stock on screen and auto populate the same on document save||If enabled, system stock populate is disabled on stock Reconciliation process|[FD-Conf-MAS-STKRECON-0001](Stock Reconcillation#FD-Conf-MAS-STKRECON-0001)|
|Show Hierarchy level value instead of Hierarchy Path||If enabled, Hierarchy level value is displayed.If not, Hierarchy Path is displayed|[FD-Conf-MAS-STKRECON-0001](Stock Reconcillation#FD-Conf-MAS-STKRECON-0001)|
|Disable New Batch Creation on screen (Add Batch)||If enabled, New batch icon for creation is disabled on stock Reconciliation screen If not, New batch icon for creation is available|[FD-Conf-MAS-STKRECON-0001](Stock Reconcillation#FD-Conf-MAS-STKRECON-0001)|
|Restrict Stock updation Approval for Saleable& Saleable Free||If enabled, Stock updation Approval for Saleable& Saleable Free quantity is restricted|[FD-Conf-MAS-STKRECON-0001](Stock Reconcillation#FD-Conf-MAS-STKRECON-0001)|

# Business Rule & Impact 

> Business rules are listed in the below section which requires Domain understanding, hope the previous sections of the Stock Reconcilliation  are clear. Refer [Stock Reconcilliation  ](Stock Reconcilliation  ), [Stock Reconcilliation  Creation](#creation-of-sales-Invoice  )   

a) User access 

    1. Login user should has association with a Distributor. 
    1. In case of user associated with multiple user, then distributor selection is require before creating Stock Reconcilliation  transaction 
    1. User with profile access configurations are to be applied while Listing Stock Reconcilliation  , Create,View Stock Reconcilliation  

    > Refer User profile, Distributor User, Corporate User Distributor mapping 

b)  List view of Stock Reconcilliation  
    1. Listing page is default landing page, where newly created Stock Reconcilliation  are listed with selected information.
    1. All listing page related features are to be available for Stock Reconcilliation  listing Page. 
    1. Retrieve recently created top `20` Stock Reconcilliation  document with selected field where it belongs to a Distributor and sort with Invoice  date. Default filter for Stock Reconcilliation  applicable for all users. 
    1. Custom filter to be available for all modules
    1. Default list view fields for distributor users  
          -"Reference Number"
          -"Date"
          -"Count Sheet No"
          -"Count Sheet Date"
          -"Hierarchy Level"
          -"Hierarchy Level Value"
          -"Stock Type"
          -"Stock Status"
          -"Godown"
          -"Remarks"

    > Refer [Listing page](Listing Page) functionalities, [Custom Filter](Custom Filter).

c) Detail view actions
    1. Detail view of Stock Reconcilation record enables you to perform actions like editing, cancel, amend, print the existing record in PDF format, all actions are configured through [Workflow](Workflow). 
    1. From the Invoice  s list view, select the desired record. Details view of Stock Reconcilation record should follow the Field access rule for the login user related profile. 

d) Create Stock Reconcilliation  
    1. Allow creation of Stock Reconcilliation  based on Profile access configuration. 
    1. User Distributor association is mandatory for creating transaction. 
    1. Corporate User are inusers create transaction related to specific associated distributor. 
    1. Creation of Stock Reconcilliation  should be restricted to user without distributor association. 

1.[FD-BR-STKRECON-0001](FD-BR-STKRECON-0001)- Disable Populate System Stock on screen and auto populate the same on document save
- If enabled, system stock populate is disabled on stock Reconciliation process
- Apply Configuration Impact [FD-Conf-MAS-STKRECON-0001](Stock Reconcillation#FD-Conf-MAS-STKRECON-0001)

2.[FD-BR-STKRECON-0002](FD-BR-STKRECON-0002)- Show Hierarchy level value instead of Hierarchy Path
- If enabled, Hierarchy level value is displayed.If not, Hierarchy Path is displayed
- Apply Configuration Impact [FD-Conf-MAS-STKRECON-0002](Stock Reconcillation#FD-Conf-MAS-STKRECON-0002)

3.[FD-BR-STKRECON-0003](FD-BR-STKRECON-0003)- Disable New Batch Creation on screen (Add Batch)
- If enabled, New batch icon for creation is disabled on stock Reconciliation screen If not, New batch icon for creation is available
- Apply Configuration Impact [FD-Conf-MAS-STKRECON-0003](Stock Reconcillation#FD-Conf-MAS-STKRECON-0003)

4.[FD-BR-STKRECON-0004](FD-BR-STKRECON-0004)- Restrict Stock updation Approval for Saleable& Saleable Free
- If enabled, Stock updation Approval for Saleable& Saleable Free quantity is restricted
- Apply Configuration Impact [FD-Conf-MAS-STKRECON-0004](Stock Reconcillation#FD-Conf-MAS-STKRECON-0004)


# Event Flows 
## Events at Front End (Create)
  - Stock Reconcilliation  list view page 
    - Listing Stock Reconcilation document
  - While Creating Stock Reconcilation document
    - Render page based on user profile (To be explained in separate page) 
    - Listing Godown
    - Listing Count Sheet No
    - Listing Reference Number Series for Stock Reconcilliation document
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

  - User chooses the 'Stock Reconcilliation  Entry' menu item. 
  - User should choose the count sheet No details 
  - System should pick the Default Distributor details 
  - System should pick the all the sku's part of count sheet document (I.e Physical stock tale document) of the selected Distributor
  - System should check the Distributor-product-pricing group and retrieve these items as qualified items for creating an Stock Reconcilliation 
  - User either choose Manual or Import option to capture Physical stock quantity for the listed items in respective fields.
  - User clicks on [Populate System Stock] button to update system stock position for the listed items 
  - Being continued,user clicks on 'Save' link.
  - System will create Stock Reconcilliation  and update the total difference in stock (Physical stock-System stock) as 'Variance'
  - User clicks on 'Save' link and Stock Reconcilliation  will be created in 'Created/Publish' status.
  - User can select the 'Stock Reconcilliation ' and print the 'Stock Reconcilliation ' if required 

- Apply Transaction series
   - Pick the Auto incremental sequencing codification and Apply for the Transaction series 

- Apply business workflow logic.
  - As per configuration, apply business logic based workflow for the respective modules.
 
- Apply Log 
  - Generate access log for application. 

 <!-- blank line -->
## Events at Unified Log
### Flow of related Events  (Save)

- Stock Reconcilliation  Service scope limited to Stock Reconcilliation creation/amendment/cancel/delete. 
- Stock Reconcilliation  Service to trigger the related sub services which are internal and separate service. 

 <!-- blank line -->
- Report related Stock Reconcilliation  data to be updated through services. 

# See also .. 
  - [Stock Reconcilliation](Stock Reconcilliation  )
  - [Stock Reconcilliation Configurations](Stock Reconcilliation  Configurations)
  - [Domain Object Stock Reconcilliation  ](Domain Object Stock Reconcilliation  )
  - [Home](Home)

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTIwMTYyMTkzMTNdfQ==
-->
