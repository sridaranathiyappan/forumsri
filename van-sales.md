# Van Sales

* What is the meaning of Vansales ?	
* What will get created through Vansale ?
* Who will do the Van-sale ?	
* What is the difference between Vansale and Presale ?

## What is the meaning of Vansales ?	





## What will get created through Vansale ?





## Who will do the Van-sale ?




## What is the difference between Vansale and Presale ?	





# Precondition for Creating a Sales Vansale 













# Business Rule & Impact 

> Business rules are listed in the below section which requires Domain understanding, hope the previous sections of the Sales Invoice are clear. Refer [SalesInvoice](Salesinvoice)[Sales Invoice Creation](#creation-of-sales-Invoice)   

1. [FD-BR-SI-0001](#FD-BR-SI-0001) - User access 
    1. Login user should has association with a Distributor. 
    1. In case of user associated with multiple user, then distributor selection is require before creating sales invoice transaction 
    1. User with profile access configurations are to be applied while Listing Sales Invoice Create, Modify, View Sales return

    > Refer User profile, Distributor User, Corporate User Distributor mapping 

1. [FD-BR-SI-0002](#FD-BR-SI-0002) - List view of Sales Invoice 
    1. Listing page is default landing page, where newly created Sales Invoice are listed with selected information.
    1. All listing page related features are to be available for Sales Invoice listing Page. 
    1. Retrieve recently created top `20` Sales Invoice document with selected field where it belongs to a Distributor and sort with Invoice date. Default filter for Sales Invoice applicable for all users. 
    1. Custom filter to be available for all modules
    1. Default list view fields for distributor users  
 
       [[ To be Added ]] 

       In default list view of users associated with multiple Distributors, 
       add `Distributor Name` fields. 

  > Refer [Listing page](Listing Page) functionalities, [Custom Filter](Custom Filter).

1. [FD-BR-SI-0003](FD-BR-SI-0003) - Detail view actions
    1. Detail view of Invoice record enables you to perform actions like editing, cancel, amend, print the existing record in PDF format, all actions are configured through [Workflow](Workflow). 
    1. From the Invoice list view, select the desired record. Details view of Invoice record should follow the Field access rule for the login user related profile. 

1. [FD-BR-SI-0004](FD-BR-SI-0004) - Create Sales Invoice 
    1. Allow creation of Sales Invoice based on Profile access configuration. 
    1. User Distributor association is mandatory for creating transaction. 
    1. Corporate User are indirect users create transaction related to specific associated distributor. 
    1. Creation of Sales Invoice should be restricted to user without distributor association. 

1. [FD-BR-SI-0005] -  Customer Selection 
    1. Listing of Customer

## Rate calculation 
1. **Invoice Price** is shown in any of the following ways.
    - PTR value stored in Batch
    - Special price defined for the customer channel and GST registration status. 
    - When Bill at latest price is enabled for the item in the item master then latest Base Price is always considered until Special price is  defined for the item. 
    - User can override the rate based on settings

2. **UOM** can be selected as **Base UOM**, **UOM 1**, **UOM 2** ...,**UOM 7**
    - For this sample, Base UOM, UOM 1 & UOM 2 are only considered. 

    - **Sample Product UOM conversion & Rate** _Product Atta 2 KG_
 
| UOM Type | UOM | Conversion Factor | Batch Rate | Special Price | Base Price |
| ------ | ------ | ------ | ------ | ------ | ------ | 
| Base UOM | KG | 1 | 44.41 | 40 | 44.60 |
| UOM 1 | CFC | 30 | 1332.30 | 1200 | 1338 |
| UOM 2 | PAC | 2 | 88.82 | 80 | 89.2 |

3. **Tax**
    - **Sample Product Tax** _Product Atta 2 KG_

| Tax Component  | Tax %  |
|----------------|--------|
| SGST           | 2.50%  |
| CGST           | 2.50%  |










