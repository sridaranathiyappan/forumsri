Content

[[_TOC_]]

`Available for review`

## What is Collection 

Collection is used to collect the amount for the invoice made against the particular customer. Any balance/pending amount against the Customer should be collected through this transaction. Collection is accounting transaction. 

## Types of Collection 

1. Collection by adjusting pending open documents. 
2. Advance Collection 

## Who creates Collection? 

1. `Collection` are created by `Distributor` & Distributor `Salesperson`. 
2. In general, `Company Salesperson`  don't make collection for the goods supplied by Distributor. 
> Note: `Company Salesperson` collecting on oepn document from distributor is covered as `payment` from distributor. 

# Creation of Collection  
  Collection will be done against the pending sales invoice through multiple Mode of Payment. Collection can be created against Sales Invoice or Without any reference of Sales Invoice (I.e Advance Collection).There should be an provision to handle the collection through Distributor Portal and Mobile application

## Precondition for creating Collection
Before creating a Collection, you need to 
* Create [Customer](Customer)
* Create [Beat](Beat) & [Salesman](Salesman)
* Create [Sales Invoice](Sales Invoice)
* Create [Bank](Bank)
* Create [Payment Mode](Payment Mode)

Creation of Collection vary based on type of creation. 

## To Create Collection Against Pending Invoice  via Collection Module in Distributor Portal 

1. **Collection Date** is often set to default current date
   - There are options to allow backdated Collection but date after present date are restricted. 

2. **In the Customer field**, enter the name of an existing customer. 
   - Collection are created to document the collection amount against the sale of goods to customer. 
   - After Customer selection, Customer related information are pre-populated as below,  
     - default [Beat](Beat), 
     - default [Salesman](Salesman), 
     - default Customer [Payment Mode](Payment Mode), 
     - default Customer [Credit Term](Credit Term) are loaded.

> Further, these details are allowed to be modified as necessary.  

3. **Select a [Beat](Beat)** related to the selected Customer 
    - Multiple beats are loaded when the Customer is associated with multiple Beat

4. **Select a [Salesman](Salesman)** related to the selected Customer 
    - Multiple Salesman are listed based on the Customer associated with multiple Beat. 

5. **[Transaction Series](Transaction Series)**
    - default Collection Transaction Series are loaded, User can change these details as necessary. 

6. **Select a Payment Mode** appropriately
7. **Select a Credit Term** if Payment Mode is credit.  

8. **Customer Billing address** 
    - default Billing address loaded as per sales Invoice , User can change these details as necessary. 

9. Fill in or Modify the remaining fields on the Collection page as necessary.
    - Bank Details
   - Cheque Date
   - Cheque Number
   - Additional Information 

> _These are the header details requires for creation of any Collection._

## To Create Collection with Auto adjustment via Collection Module in Distributor Portal 

10. **Adjustment** 
    - User can Manual adjust or Auto adjust the available open [Credit Note document](Credit Note) of the selected customer. 
    - These Adjustments are posted as implicit [Collection](Collection), these adjustment amount will not reduce the Collection net amount, it has impact in Collection outstanding amount. 

11. **Save Collection** 
On Saving of the Collection document, 
    - Document of sales is recorded with generation of unique Collection Transaction number for a Distributor. 
    - Line Item & quantity of details provided are reduced from the [current stock](Stock & Inventory) of the selected stock location. 
    - (Adjustment & Outstanding)(Collection Adjustment Logic) details are posted as implicit [Collection](Collection) to the selected customer. Credit note documents are adjusted as require. 
    - reference transactions are updated like Sales order status update based on fulfillment. Customer outstanding modified. Customer Master update for address change. These are part of workflow as per configuration.  
    - Off take scheme benefit applied are accounted and updated. 
    - Report data consolidation initiated for relevant data points. 
    - Collection is ready to [Print](Collection Print)
    - Collection delivery process to be initiated for the prepared Collection. 

## Cancellation of Collection
Cancellation of Collection are action performed on un-deliverable Collection after preparation of Collection. The reason may vary like "Wrongly created Collection", "Delivery failure", "Not accepted during delivery" ..etc. Cancelled Collection are not referred in any further transaction like adjustment or collections. Cancelled Collection are considered as valid document and used in all report.  

Cancellation of Collection are restricted based on configuration & workflow, few points as below. 

  - Business level restriction may vary based on configuration.  
    - Delivered Collection are not allowed to cancel, instead sales return to be performed to maintain the logical accounting transactions. 

  - Data integrity related restrictions
    - Validation fails if the customer outstanding update creates negative value scenario. 
    - Validation fails if the implicitly created collection and related adjustment creates negative value scenario.
    - Deactivated master reference like customer, product, distributor, beat, salesman ..etc. will not have any impact to fail the cancellations. 

On Cancel of Collection document, 
  - Document marked for status change to indicate cancellation. 
  - Customer outstanding reversed by reducing the cancelled Collection value.  
  - Cancellation action on implicitly created collection is performed and Adjusted documents are reversed to current state to reflect current pending of the respective document.  
  - Cancelled Collection are considered as valid document and used in all tax report.
  - Report related Collection in Ledger will get recomputed. 

## Amendment on Collection
Amendment to Collection are corrections to the prepared Collection. 
Amendment is not editing in record, the amended document is referred as valid document with status amended. 

Amendment performs validation and two primary actions as below, 
  - Cancel the old document of Collection by executing all cancellation action as mentioned in [Collection cancellation section](#cancellation) 

  - Amendment of Collection are restricted to Business level restriction & Data integrity related restriction as mentioned in [cancellation](#cancellation) section. 

  - Further, Modification of key parameters are not allowed like Customer, Salesman, Beat.  

  - A new Collection created with Collection transaction number of old document. all action performed during Collection save are applicable for the newly created Collection document. 


# Types of Collection

## Create Collection Against Sales Invoice  
 Sales Invoice are recorded by Salesman during market visit  or Distributor operator to record the demand and sales of the products. 
 A [Sales Invoice](Sales Invoice) records the customer's intent to buy the listed products at the stated price. 

  - User will be allowed  to do the payment collection from the customer through multiple mode of payment (Cash , Cheque,NEFT,RTGS)

  - Based on customer type (Cash or credit) , salesman will be allowed to collect the payment as Partial or full payment against the sales invoice from the customer 

  - User allowed to collect the payment for multiple pending invoices of the customer at a time 

## Create Collection with Adjustable return (Credit Note)
 Sales return are recorded by Salesman during market visit  or Distributor operator to record the market returns on previous sales of the products. 
  A[Sales Return](Sales Return) records the customer's intent to return the products that are bought either from the Distributor or Sub distributor. 
 
  - User allowed to do the amount adjustment for multiple returns  at a time 
    [Customer](Customer), [Salesman](Salesman), [Beat](Beat) ,Pending Invoice,Credit Note information are pre-loaded (pre-fetched from Sales Invoice and Sale return) to create the Collection during conversion using Option 1 & 2.

## Salesmanwise Collection
## Create Collection Salesmanwise
 Sales Invoice are recorded by Salesman during the market visit or Distributor operator to record the sales of the products. 

  - User will be allowed  to do the payment collection from all pending Invoices associated with the selected salesman 

  - Provision should be given to pick the required pending invoices based on Salesman/Date/Beat/Customer and do the required collection through multiple mode of payment (Cash ,Cheque,NEFT,RTGS)

  - System should allow to do collection full or partial amount against invoices 


# List of Collection Configurations

## Collection Configuration 
This page list all direct configuration applicable for Collection & related other module configuration which impacts Collections. 

> Other common configuration such as User profile based configuration, Field level configurations, Menu configurations are assumed to be as applicable similar to other modules in application. Refer [Common Application Configurations](Common Application Configurations) 
 
## Application level Configuration  

### Collection Module Configuration
| Configuration                                                                | Related Configuration | Details                                                                         | Ref #                                                     |
|------------------------------------------------------------------------------|-----------------------|---------------------------------------------------------------------------------|-----------------------------------------------------------|
|ALLOW BACK DATED TRANSACTION | | If enabled allow back date from current date on collection screen.,If not, back date is not allowed| [FD-Conf-MAS-Collection-0001](Collection Creation#FD-Conf-MAS-Collection-0001)|
|ALLOW NUMBER OF DECIMAL | |Set range of amount to be displayed on decimal value on screen | [FD-Conf-MAS-Collection-0002](Collection Creation#FD-Conf-MAS-Collection-0002)|
|Display Transferd Customer | | If enabled , display customer re-alligned, If not , do not display customer re-alligned | [FD-Conf-MAS-Collection-0003](Collection Creation#FD-Conf-MAS-Collection-0003)|
|ALLOW AUTO ADJUST | | If enabled display Auto Adjust icon on collection screen,If not, do not display Auto Adjust icon on collection screen| [FD-Conf-MAS-Collection-0004](Collection Creation#FD-Conf-MAS-Collection-0004)|
|Auto Adjust Amount Getting from | | Amount Received == Calculate adjustment on amount received column field value on collection screen , Adjustable Return == Calculate adjustment on outstanding column field value on collection screen| [FD-Conf-MAS-Collection-0005](Collection Creation#FD-Conf-MAS-Collection-0005)|

### Salesman Collection configuration:
| Configuration                                                                | Related Configuration | Details                                                                         | Ref #                                                     |
|------------------------------------------------------------------------------|-----------------------|---------------------------------------------------------------------------------|-----------------------------------------------------------|
|ALLOW NUMBER OF DECIMAL | | Set range of amount to be displayed on decimal value on screen|[FD-Conf-MAS-Collection-0006](Collection Creation#FD-Conf-MAS-Collection-0006)|


### Receive Collection configuration:
| Configuration                                                                | Related Configuration | Details                                                                         | Ref #                                                     |
|------------------------------------------------------------------------------|-----------------------|---------------------------------------------------------------------------------|-----------------------------------------------------------|
|ALLOW NUMBER OF DECIMAL (Collection configuration)| |Set range of amount to be displayed on decimal value on screen|[FD-Conf-MAS-Collection-0007](Collection Creation#FD-Conf-MAS-Collection-0007)|
|Do You Want To Recalcuate The Receive Collection To Collection| |If enabled, based on the collection amount received / available, adjustment are calculated. If not, existing adjustment are calculate|[FD-Conf-MAS-Collection-0008](Collection Creation#FD-Conf-MAS-Collection-0008)|
|ALLOW AUTO ADJUST (Collection configuration)| |If enabled display Auto Adjust icon on collection screen.,If not, do not display Auto Adjust icon on collection screen|[FD-Conf-MAS-Collection-0009](Collection Creation#FD-Conf-MAS-Collection-0009)|
|Auto Adjust Amount Getting from| | Amount Received == Calculate adjustment on amount received column field value on collection screen,Adjustable Return == Calculate adjustment on outstanding column field value on collection screen|[FD-Conf-MAS-Collection-0010](Collection Creation#FD-Conf-MAS-Collection-0010)|
	
<!--stackedit_data:
eyJoaXN0b3J5IjpbNTM1MjUzMDA3XX0=
-->

# Business Rule & Impact 

> Business rules are listed in the below section which requires Domain understanding, hope the previous sections of the Collection are clear. Refer [Collection](Collection), [Collection Creation](#creation-of-sales-Collection)   

1. [FD-BR-0001] - User access 

>  [FD-BR-Collection-0001](#FD-BR-Collection-0001)-Collection Module
    - Login user should has association with a Distributor. 
    -  In case of user associated with multiple user, then distributor selection is require before creating Collection transaction 
    - User with profile access configurations are to be applied while Listing Collection, Create, Modify, View Collection

    > Refer User profile, Distributor User, Corporate User Distributor mapping 

2. [FD-BR-Collection-0002](#FD-BR-Collection-0002) - List view of Collection
    - Listing page is default landing page, where newly created Collection are listed with selected information.
    -  All listing page related features are to be available for Collection listing Page. 
    -  Retrieve recently created top `20` Collection document with selected field where it belongs to a Distributor and sort with Collection date. Default filter for Collection applicable for all users. 
    - Custom filter to be available for all modules
    - Default list view fields for distributor users  
        - "salesmanName"    
        - "customername"    
        - "beatname" 
        - "transactionSeries" 
        - "CollectionDate" 
        - "CollectionCode"
        - "CollectionMode"
        - "AmountReceived"
        - "ReceivedAdjusted"
        - "AmountAdjusted"
        - "AdjustableAmount"
        - "ReceiptNumber"
        - "BankDetails"
        - "ChequeDate"
        - "ChequeNumber"

       In default list view of users associated with multiple Distributors, 
       add `Distributor Name` fields. 

    > Refer [Listing page](Listing Page) functionalities, [Custom Filter](Custom Filter).

3. [FD-BR-Collection-0003](#FD-BR-Collection-0003) - Detail view actions

    - Detail view of Collection record enables you to perform actions like editing, cancel, amend, print the existing record in PDF format, all actions are configured through [Workflow](Workflow). 
    -  From the Collections list view, select the desired record. Details view of Collection record should follow the Field access rule for the login user related profile. 

4. [FD-BR-Collection-0004](#FD-BR-Collection-0004) - Create Collection

    - Allow creation of Collection based on Profile access configuration
    - User Distributor association is mandatory for creating transaction
    - Corporate User are indirect users create transaction related to specific associated distributor
    - Creation of Collection should be restricted to user without distributor association

5. [FD-BR-Collection-0005](#FD-BR-Collection-0005) - Customer Selection 

    - Listing of Customer for **Selection list** in transaction, criteria to be   
       - Distributor related customer, with status as per configuration 
        
      - Customer can be selected in any one of the following ways
      - Direct customer selection
      - Customer selection post Salesman selection
      - Customer selection post Salesman and Beat selection
      
     -  In all the above scenarios Customer, Beat and Salesman mapping is must. 

6. [FD-BR-Collection-0006](#FD-BR-Collection-0006) - Allow Back dated Transaction

      - Allow the user to capture sales collection for Back date based on configuration settings

7. [FD-BR-Collection-0007](#FD-BR-Collection-0007) - Allow collection recompute and adjustment 

      - Allow the user to recompute the collection and do required adjustment based on configuration settings 
 

# Event Flows

## Events at Front End (Create)
  - Collection list view page 
     - Listing Collection
    - While Creating Collection
     - Render page based on user profile (To be explained in separate page) 
     - Listing Salesman
     - On Selection of Salesman, Retrieve Salesman Category info, Filter related Beat, Filter related customer.
     - Listing Beat 
     - On Selection of Beat, Retrieve relevant Customer, Salesman if not selected.  
     - Listing Customer
     - On Selection of Customer, retrieve relevant Beat, Salesman, Customer outstanding, Customer Info, Customer address
     - Listing Transaction Series for Collection
     - Listing Collection Mode
     - Listing Pending Invoices
     - On Selection of populate bills retrieve all invoices with outstanding amount details 
     - Listing Adjustable return 
     - List relevant Adjustment info 
 

## Events at Business logic layer (overview)
- Apply Dynamic front end access control based on user profile. 
- Generate record reference number for transaction internal reference. Every request should have this reference to process, manipulate or produce data. 

- Validate the data submitted from front end - Datatype & security related. 
- Validate the data submitted from front end - Business flow related. 

**Business flow validations**

  - User chooses the 'Collection Entry' menu item. 
  - System should pick the Default Distributor details 
  - User selects the Salesman associated with that distributor
  - User selects the Beat name or code
  - System should list out the customer from the selected beat 
  - User should select the customer from the selected beat 
  - System should pick the customer
  - System should check and  retrieve all pending invoices / returns associated with that customer 
 - User should select the Collection mode as (Cash/Cheque/NEFT/RTGS) . In case of cheque payment additional details to be added as required 
  - User enters the collection amount and adjustment amount against outstanding amount 
  - User enters the adjustment amount against returns in respective fields.
  - System will create Collection and update the total amount as Due for collection against the customer
  - User clicks on 'Collection' link and Collection will be created in 'Created/Publish' status.
  - User can select the 'Collection and print the 'Collection Receipt'

**Events based on Collection Against Sales Invoice**

- Apply Collection
  - Collected Amount will get reduced against the selected invoice for specific customer and also against the Customer Balance 
  - Any Exceptions related to collection computation to be captured and prompted in front end as 'toasted message' and same should get added to application logs

- Apply Amendment
  - User can amend (Edit) the collectionTransactions , changes will get updated against the same transaction of specific customer and also against the Customer Balance 
  - Any Exceptions related to collection computation to be captured and prompted in front end as 'toasted message' and same should get added to application logs

- Apply Cancel
  - User can Cancel the collection Transactions , changes will get updated against the same transaction of specific customer and also against the Customer Balance and status of the collection will get modified as 'Cancel'
  - Any Exceptions related to collection computation to be captured and prompted in front end as 'toasted message' and same should get added to application logs

**Events based on Collection Against Adjustment Return**

- Apply Collection
  - Adjustment Amount in Adjustable return will get reduced against the Customer Balance  of the selected specific customer
  - Any Exceptions related to Adjustable amount computation to be captured and prompted in front end as 'toasted message' and same should get added to application logs

**Events based on Salesmanwise Collection**

- Apply Collection
  - User will be given provision to capture collection for all pending invoices associated with the selected customer based on  Salesman/Date/Beat/Customer and do the required collection through multiple mode of payment (Cash ,Cheque,NEFT,RTGS)
  - Any Exceptions related to Adjustable amount computation to be captured and prompted in front end as 'toasted message' and same should get added to application logs


# See also .. 
  - [Collection](Collection)
  - [Collection Configurations](Collection Configurations)
  - [Domain Object Collection](Domain Object Collection)
  - [Home](Home)

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTIwMTYyMTkzMTNdfQ==
-->
