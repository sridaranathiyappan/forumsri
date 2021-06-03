# Sales Return

* What is the meaning of Sales Return?	
* Who creates Sales Return?	
* What are the impact of sales Return?	
* What is the difference between purchase return and sales return?

## What is the meaning of Sales Return?	

"Businesses often return goods that are already sold.A sales return is merchandise sent back by a buyer to the seller, usually for one of the following reasons:
1.Excess quantity shipped
2.Excess quantity ordered
3.Defective goods
4.Goods shipped too late
5.Product specifications are incorrect
6.Wrong items shipped"

## Who creates Sales Return?	
The seller creates sales return after receiving the sold goods from a buyer.

## What are the impact of sales Return?	
The seller records this return as a debit to a Sales Returns account and a credit to the Revenue account;
 the total amount of sales returns in this account is a deduction from the reported amount of gross sales in a period, which yields a net sales figure. 
The credit to the revenue account reduces the amount of accounts receivable outstanding.

## What is the difference between purchase return and sales return?	
When goods are returned to the suppliers, it is called as purchase return or return outwards but When goods are returned from the customers, 
it is called sales return or return inwards.


# Precondition for Creating a Sales Return 

## Customer listing	
"1.Load Customers, based on Customer active and status configured for allowing transactions.
2.If Beat and Salesman not mapped then system must not allow for selecting customer to proceed return."

## Transaction Series
1.System will load default transaction series, if required user can change and proceed the sales return.

## Listing of SKU's
1.In case of With Ref sales return system will list the SKUs which were on the sales invoice. In case of Without ref system will list all the active Skus.

## Listing of Batch info	
1.System will load the Batch info as FIFO method.
2. Based on Batch Selection, the Price  will loaded on respective SKU's."

## Save Transaction	
1. Successfully saved the sales return, Stocks will get added to location Godown , if the items are saleable. 
2.System will create a credit note for the particular customer.
3.Implicit collection will be created and outstanding will get adjusted, if relevant configuration is ON.

# Business Rule & Impact 

> Business rules are listed in the below section which requires Domain understanding, hope the previous sections of the Sales Return are clear. Refer [Salesreturn](Salereturn)[Sales Return Creation](#creation-of-sales-return)   

1. [FD-BR-SR-0001](#FD-BR-SR-0001) - User access 
    1. Login user should has association with a Distributor. 
    1. In case of user associated with multiple user, then distributor selection is require before creating sales invoice transaction 
    1. User with profile access configurations are to be applied while Listing Sales Return Create, Modify, View Sales return

    > Refer User profile, Distributor User, Corporate User Distributor mapping 

1. [FD-BR-SR-0002](#FD-BR-SR-0002) - List view of Sales return
    1. Listing page is default landing page, where newly created Sales Return are listed with selected information.
    1. All listing page related features are to be available for Sales Return listing Page. 
    1. Retrieve recently created top `20` Sales Return document with selected field where it belongs to a Distributor and sort with Return date. Default filter for Sales Return applicable for all users. 
    1. Custom filter to be available for all modules
    1. Default list view fields for distributor users  
 
       [[ To be Added ]] 

       In default list view of users associated with multiple Distributors, 
       add `Distributor Name` fields. 

  > Refer [Listing page](Listing Page) functionalities, [Custom Filter](Custom Filter).

1. [FD-BR-SR-0003](FD-BR-SR-0003) - Detail view actions
    1. Detail view of Return record enables you to perform actions like editing, cancel, amend, print the existing record in PDF format, all actions are configured through [Workflow](Workflow). 
    1. From the Return list view, select the desired record. Details view of Return record should follow the Field access rule for the login user related profile. 

1. [FD-BR-SR-0004](FD-BR-SR-0004) - Create Sales Return 
    1. Allow creation of Sales Return based on Profile access configuration. 
    1. User Distributor association is mandatory for creating transaction. 
    1. Corporate User are indirect users create transaction related to specific associated distributor. 
    1. Creation of Sales Return should be restricted to user without distributor association. 

1. [FD-BR-SR-0005] -  Customer Selection 
    1. Listing of Customer

## Rate calculation 
1. **Return Price** is shown in any of the following ways.
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

