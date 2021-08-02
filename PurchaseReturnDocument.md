Content

[[_TOC_]]

`Available for review`
# Creation of Purchase Return 
A Purchase Return is a primary return that get generated from the Distributor, based on expiry stock / Damages , It will get created by the distributor operator through distributor portal

## Precondition for creating Purchase Return  
Before creating a direct Purchase Return  , you need to 
* Create [Vendor](Vendor) details 
* Create [Godown](Godown) details 
* Create [Item](Product) details 
* Create [Pricing](Pricing) details 
* Create [Scheme](Scheme) details 
* Create [Tax](Tax) details 

Creation of Purchase Return  vary based on type of creation. 

## To Create Purchase Return  

1. **Return  Date** is often set to default current date
   - There are options to allow backdated Return  but date after present date are restricted. 

2. **In the Vendor field**, enter the name of an existing Vendor
   - Purchase return are created to document the Primary order to the distributor
   - After Vendor selection, Other related information to be filed in below,  
     - default [Distributor](Distributor), 
     - default [Distributor Shipping address,,City,State,Pincode](Distributor) & 
     - default [Distributor Billing address,City,State,Pincode](Distributor) are loaded.

> Further, these details are allowed to be modified as necessary.  

3. **[Transaction Series](Transaction Series)**
    - default Purchase ReturnTransaction Series are loaded, User can change these details as necessary. 

4. **Customer Shipping address** 
    - default Shipping address loaded, User can change these details as necessary. 

5. Fill in or Modify the remaining fields on the Purchase Return page as necessary.
    - Remark 
    - Reason  

6. **Customer Shipping address pick** 
    - default Shipping address loaded, User can change these details as necessary. 

7. **Purchase Return Type** 
    - With Ref ir Withot Ref details , User can change these details as necessary. 

8. **Remarks**
     - Additional info can be provided 

9. Fill in or Modify the remaining fields on the Purchase Return page as necessary.
    - Product
    - Batch
    - Purchase Invoice 
    - UOM
    - Saleable Return quantity
    - Non-Saleable Return quantity

> _These are the header details requires for creation of any Sales Return._
> _You are now ready to fill in the Purchase Order lines for products that you are selling to the Customer._

## Addition of line level details
10. **Select a [Product](Product)** from list of eligible product for sales. 
    - After selection of line level [Product](Product), related information are pre-populated  
      - Batch details from current stock of [Distributor](Distributor)
      - Price to customer [PTR](#rate-calculation)
      - [Available Stock Quantity](Stock & Inventory) 
      - Purchase [UOM](Unit of Measurement) 
      - [Applicable Tax](#rate-calculation) 

11. **Provide the Purchase Return  quantity**
    - After providing the Purchase Return  quantity, 
      - The value in the Line Amount field is calculated as Unit Price x Quantity. 
      - [Applies Tax](#tax) based on predefined [Tax Master](Tax Master) settings
      - Line level [Net Amount](Purchase return Calculation) is calculated. 

12. **Select the Purchase Invoice**
    - After providing the Purchase Invoice  reference  
      - The value in the Purchase Invoice   calculated as Unit Price x Return Quantity. 
      - [Applies Tax](#tax) based on predefined [Tax Master](Tax Master) settings
      - Line level [Net Amount](Purchase Order Calculation) is calculated. 
    - _refer [Purchase Order calculation logic](#rate-calculation)_

## Invoice Discount & Adjustments against Purchase Return

13. **[Scheme defined](Scheme Master)** for item are applied as per configuration. 
    - any Scheme discount applied will re-compute the Tax amount & Net amount. 
    - Scheme product free are loaded based as per scheme.   
    - [Scheme applied](#scheme) at line level and overall document level. 

14. **Invoice  level discount** can be provided to re-compute final [Return Amount](#rate-calculation)
    - Amount Discount 
    - Percentage Discount 
    - Discount Per UOM
    - Invoice Level Scheme Discount

15. _Repeat **Addition of line level details** Step for adding more lines of item._ 

16. **Save Purchase Return  ** 
On Saving of the Purchase Return document, 
    - Document of Purchase Return  is recorded with generation of unique Purchase Return  Transaction number for a Customer
    - Line Item & quantity of details provided are added as part of Purchase Return document 
    - Report data consolidation initiated for relevant data points. 
    - Purchase Return is ready to [Print](Purchase Return Print)

## Cancellation 
Cancellation of Purchase Return are action performed against Delivered items (Purchase Invoice  or Without Purchase Invoice  ref) after preparation of Purchase Return  . The reason may vary like "Wrongly created Return  ". Cancelled Return  are considered as valid document and used in all reports

Cancellation of Purchase Return  are restricted based on configuration & workflow, few points as below. 

  - Business level restriction may vary based on configuration.  
    - Approved Purchase Return  are not allowed to cancel, instead before the approval , Purchase Return cancellation to be performed to maintain the logical accounting transactions. 

  - Data integrity related restrictions
    - Validation fails if the customer Return  amount update creates zero value scenario due to Zero price exist in the system against any line item. 
    - Deactivated master reference like customer, product, distributor, beat, salesman ..etc. will have impact to fail the cancellations. 

On Cancel of Purchase Return  document, 
  - Document marked for status change to indicate cancellation. 
  - Report related Purchase Return  data to be recomputed. 

## Amendment 
Amendment to Purchase Return  are corrections to the prepared Purchase Return  . 
Amendment is not editing in record, the amended document is referred as valid document with status amended. 

Amendment performs validation and two primary actions as below, 
  - Cancel the old document of Purchase Return  by executing all cancellation action as mentioned in [Purchase Return  cancellation section](#cancellation) 

  - Amendment of Purchase Return  are restricted to Business level restriction & Data integrity related restriction as mentioned in [cancellation](#cancellation) section. 

  - Further, Modification of key parameters are not allowed like Customer, Salesman, Beat.  

  - A new Purchase Return  created with Purchase Return  transaction number of old document. all action performed during Purchase Return  save are applicable for the newly created Purchase Return  document. 

- Market Purchase Return  
  - A [Purchase Return ](Purchase Return ) records the distributors intent to return the damaged / Expired products at the stated price 

[Distributor](Distributor), [vendor](vendor), [Depot](depot) and Item information are pre-loaded (pre-fetched from Purchase Return ) to create Purchase Return  . 

# Purchase Return  Configuration 
This page list all direct configuration applicable for Purchase Return  & related other module configuration which impacts Collections. 

> Other common configuration such as User profile based configuration, Field level configurations, Menu configurations are assumed to be as applicable similar to other modules in application. Refer [Common Application Configurations](Common Application Configurations) 
 
## Application level Configuration  

### Purchase Return  Module Configuration
| Configuration                                                                | Related Configuration | Details                                                                         | Ref #                                                     |
|------------------------------------------------------------------------------|-----------------------|---------------------------------------------------------------------------------|-----------------------------------------------------------|
|Generate alert message – if no tax is configured for the product||If enabled, Display alert if tax has not configured with product|[FD-Conf-MAS-PR-0001](Purchase Return Creation#FD-Conf-MAS-PR-0001)|
|Allow Back Dated Transaction||If enabled, PR transaction is allowed with back dated|[FD-Conf-MAS-PR-0002](Purchase Return Creation#FD-Conf-MAS-PR-0002)|
|Hide Free Quantity||If enabled, Free quantity are restricted on PR transaction|[FD-Conf-MAS-PR-0003](Purchase Return Creation#FD-Conf-MAS-PR-0003)|
|Hide Damage Quantity||If enabled, Damage quantity are not allowed in PR transaction|[FD-Conf-MAS-PR-0004](Purchase Return Creation#FD-Conf-MAS-PR-0004)|
|Hide Damage Quantity by Role||Set role config to restrict damage quantity display based on user role on PR transaction|[FD-Conf-MAS-PR-0005](Purchase Return Creation#FD-Conf-MAS-PR-0005)|
|Validate to allow only digits on base UOM for return quantity||If enabled, UOM quantity is allowed only digits, decimal are restricted|[FD-Conf-MAS-PR-0006](Purchase Return Creation#FD-Conf-MAS-PR-0006)|
|Hide Purchase Return type||If enabled, PR type column on PR transaction screen is disabled|[FD-Conf-MAS-PR-0007](Purchase Return Creation#FD-Conf-MAS-PR-0007)|
|TCS applicable for same month return only||If enabled, PR retirn with same month is applicable for TCS|[FD-Conf-MAS-PR-0008](Purchase Return Creation#FD-Conf-MAS-PR-0008)|
|Allow multiple PurchaseInvoices in single PurchaseReturn||If enabled, multiple PurchaseInvoices in single PurchaseReturn without duplicate invoice on PR transaction|[FD-Conf-MAS-PR-0009](Purchase Return Creation#FD-Conf-MAS-PR-0009)|
|Show alert notification for reason||If enabled, display alert if reason is not selected on PR transaction|[FD-Conf-MAS-PR-0010](Purchase Return Creation#FD-Conf-MAS-PR-0010)|
|Restrict users from returning invoices older then days||If enabled, user can return PI with configured days, if days exceed will not be accepted|[FD-Conf-MAS-PR-0011](Purchase Return Creation#FD-Conf-MAS-PR-0011)|
|Tax|Do not compute the tax amount for Purchase Return without reference|If enabled tax amount is not compute on PR if type without ref|[FD-Conf-MAS-PR-0012](Purchase Return Creation#FD-Conf-MAS-PR-0012)|
|Tax|Do not compute the tax amount for purchase returns with reference|if the return is performed after months from invoice dateIf enabled, set month duration, on PR not to compute the tax amount for purchase returns type with reference|[FD-Conf-MAS-PR-0013](Purchase Return Creation#FD-Conf-MAS-PR-0013)|


# Business Rule & Impact 

> Business rules are listed in the below section which requires Domain understanding, hope the previous sections of the Purchase Return  are clear. Refer [Purchase Return  ](Purchase Return  ), [Purchase Return  Creation](#creation-of-sales-Return  )   

1. [FD-BR-PR-0001] - User access 

>  FD-BR-PR-0001

    1. Login user should has association with a Distributor. 
    1. In case of user associated with multiple user, then distributor selection is require before creating Purchase Return  transaction 
    1. User with profile access configurations are to be applied while Listing Purchase Return  , Create, Modify, View Purchase Return  

    > Refer User profile, Distributor User, Corporate User Distributor mapping 


2. [FD-BR-PR-0002](#FD-BR-PR-0002) - List view of Purchase Return
    1. Listing page is default landing page, where newly created Purchase return  are listed with selected information.
    1. All listing page related features are to be available for Purchase Invoice  listing Page. 
    1. Retrieve recently created top `20` Purchase Return document with selected field where it belongs to a Distributor and sort with Invoice  date. Default filter for Purchase Invoice  applicable for all users. 
    1. Custom filter to be available for all modules
    1. Default list view fields for distributor users  
        - "transactionNumber" 
        - "Purchase Return Date" 
        - "referencenumber" 
        - Vendor Name"
        - "Due date" 
        - "customername" 
        - "Bill to party code" 
        - "Distributor Shipping address,City,State,Pincode"
        - "Distributor Billing address,City,State,Pincode"

    > Refer [Listing page](Listing Page) functionalities, [Custom Filter](Custom Filter).

3. [FD-BR-PR-0003](FD-BR-PR-0003) - Detail view actions
    1. Detail view of purchase return record enables you to perform actions like editing, cancel, amend, print the existing record in PDF format, all actions are configured through [Workflow](Workflow). 
    1. From the returns list view, select the desired record. Details view of returns record should follow the Field access rule for the login user related profile. 

4. [FD-BR-PR-0004](FD-BR-PR-0004) - Create Purchase Return
    1. Allow creation of Purchase Return based on Profile access configuration. 
    1. User Distributor association is mandatory for creating transaction. 
    1. Corporate User are indirect users create transaction related to specific associated distributor. 
    1. Creation of Purchase Return should be restricted to user without distributor association. 

5. [FD-BR-PR-0005](FD-BR-PR-0005) -Allow Back Dated Transaction
    1.Enable provision to allow user to input Back dated Purchase return transactions

6. [FD-BR-PR-0006](FD-BR-PR-0006) -Allow only digits on base UOM for return quantity
    1.Enable provision to allow user to enter only Digits as part of Based UOM 

7. [FD-BR-PR-0007](FD-BR-PR-0007) -TCS applicable for same month return only
    1.Based on the parameter, TCS will be made applicable for same month purchase return only

8. [FD-BR-PR-0008](FD-BR-PR-0008) -Allow multiple PurchaseInvoices in single Purchase Return
    1.Allow user to select multiple purchase Invoices as part of Single Purchase return transaction

9. [FD-BR-PR-0009](FD-BR-PR-0009) -Restriction users from returning invoices older then days
    1. Set the no of days to allow the user to do  purchase return agaianst the Older purchase Invoices 

## Rate calculation 
1. **Purchase Return  Price** is shown in any of the following ways.
    - Return Price value stored in Batch
    - When Bill at Return price is enabled for the item in the item master then latest return Price is always considered until return price is  defined for the item. 
    - User can override the rate based on settings

2. **UOM** can be selected as **Base UOM**, **UOM 1**, **UOM 2** ...,**UOM 7**
    - For this sample, Base UOM, UOM 1 & UOM 2 are only considered. 

    - **Sample Product UOM conversion & Rate** _Product Atta 2 KG_
 
| UOM Type | UOM | Conversion Factor | Batch Rate | Return Price | Base Price |
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

4. **Sample Calculation**

| Detail Field                         | Description & Calculation Formula                                                                           |
|--------------------------------------|-------------------------------------------------------------------------------------------------------------|
| Item Name                            | User can select the product by Item Code or Name                                                            |
| Batch                                | By default first batch is selected. Batch is listed on FIFO logic                                           |
| UOM                                  | Default Sales UOM is selected initially. User can change if required by shortcut also or manually change it |
| Purchase Return Price                           | PTR of the item is shown. PTR is considered based on the Margin or Channel Wise Margin or Quotation         |
| Net Rate                             | Sale Price of item + Tax Amount is calculated for 1 quantity and shown.                                     |
| Quantity                             | User can enter quantity. Quantity entered is considered as per UOM selected                                 |
| Amount                               | Quantity * Sale Price is calculated and shown                                                               |
| Discount%                            | Manual discount percentage                                                                                  |
| Discount Amount                      | Discount Amount is shown                                                                                    |
| Scheme Discount%                     | Scheme Discount % is shown. For Amount scheme also, Discount % is also calculated and shown                 |
| Scheme Amount                        | Scheme Amount is shown.  Even for % Scheme, Discount Amount is calculated and shown                         |
| Net Amount (Taxable)                 | Taxable net amount. Amount - (Scheme Amount + Discount Amount). Based on configuration this formula varies |
| Tax Amount (Tax Split up also shown) | Tax Amount calculated on Net Amount is calculated & Shown                                                   |
| Net Tax Amount                       | Tax amount deducted on proposition from Additional Discount given in Return  is shown here                  |
| Type                                 | Always Second Sales                                                                                         |
| Total                                | Net Amount + Tax Amount is calculated & Shown                                                               |
| Scheme Discount (Return  Level)      | Return  level Scheme Discount is propositioned item level and shown                                         |
| Trade Discount (Return  Level)       | Return  level Trade Discount amount is proportioned item level and shown                                    |
| Net Amount                           | Total - (Trade Discount + Scheme Discount) is calculated and shown                                          |

  - Purchase Return  Price : PTR of the item
  - Net Rate : Sale Price of item + Tax Amount is calculated for 1 quantity and shown.
  - Amount : (Quantity * Sale Price)
  - Discount Amount : Amount * Discount% or Direct amount given by end user
  - Scheme Amount : Amount * Scheme Discount% or Scheme Amount As per definition of scheme. 
  - Net Amount (Taxable) : Amount - (Scheme Amount + Discount Amount) 
> Based on configuration, `Net Amount (Taxable)` varies. 
  - Tax Amount : Net Amount (Taxable) * Tax % `Calculate for each component of Tax`
  - Total : Net Amount (Taxable) + Tax Amount
  - Net Amount : Total - (Trade Discount + Scheme Discount)


| Product   | Quantity | UOM | Rate  | Amount | Scheme Discount | Discount | Tax   | Net Rate | Net Amount |
|-----------|----------|-----|-------|--------|-----------------|----------|-------|----------|------------|

    - Base UOM without discount 

| Product   | Quantity | UOM | Rate  | Amount | Scheme Discount | Discount | Tax   | Net Rate | Net Amount |
|-----------|----------|-----|-------|--------|-----------------|----------|-------|----------|------------|
| Atta 2 KG | 2        | KG  | 44.41 | 88.82  | 0               | 0        | 4.441 | 46.6305  | 93.261     |

    - Base UOM - with Scheme and Other discount

 | Product   | Quantity | UOM | Rate  | Amount | Scheme Discount | Discount | Tax   | Net Rate | Net Amount |
|-----------|----------|-----|-------|--------|-----------------|----------|-------|----------|------------|
| Atta 2 KG | 2        | KG  | 44.41 | 88.82  | 5               | 2        | 4.091 | 42.9555  | 85.911     |

    - UOM1 - without discount

| Product   | Quantity | UOM | Rate   | Amount | Scheme Discount | Discount | Tax    | Net Rate | Net Amount |
|-----------|----------|-----|--------|--------|-----------------|----------|--------|----------|------------|
| Atta 2 KG | 2        | CFC | 1332.3 | 2664.6 | 0               | 0        | 133.23 | 1398.915 | 2797.83    |

    - UOM 1- with Scheme and Other discount

| Product   | Quantity | UOM | Rate   | Amount | Scheme Discount | Discount | Tax    | Net Rate | Net Amount |
|-----------|----------|-----|--------|--------|-----------------|----------|--------|----------|------------|
| Atta 2 KG | 2        | CFC | 1332.3 | 2664.6 | 5               | 2        | 132.88 | 1395.24  | 2790.48    |

    - When Net Rate is changed (Base UOM - without discount)
| Product   | Quantity | UOM | Rate  | Amount | Scheme Discount | Discount | Tax  | Net Rate | Net Amount |
|-----------|----------|-----|-------|--------|-----------------|----------|------|----------|------------|
| Atta 2 KG | 2        | KG  | 42.86 | 85.71  | 0               | 0        | 4.29 | 45       | 90         |

    - When Net Rate is changed (Base UOM - with discount)

| Product   | Quantity | UOM | Rate  | Amount | Scheme Discount | Discount | Tax  | Net Rate | Net Amount |
|-----------|----------|-----|-------|--------|-----------------|----------|------|----------|------------|
| Atta 2 KG | 2        | KG  | 98.74 | 197.48 | 5               | 2        | 9.52 | 100      | 200        |

  
## Tax 
  - Tax Components can be
    - 1. State Tax
    - 2. Central Taxb y
    - 3. Inter-state Tax
    - 4. Cess
    - 5. Cess on Quantity
    - 6. Cess applicable for the particular state
  - Tax applicable for the product, related geo hierarchy of distributor, [State](State) of distributor, [State](State) of Customer, Tax identifier details of customer, Tax form applied for the customer.
  - Multiple Tax are applicable for an item based on tax definition. All relevant tax details with split-up percentage to be available in Purchase Return  document. 
  - Accurate calculation of tax amount is main criteria of Purchase Return  document.


# Event Flows 
## Events at Front End (Create)
  - Purchase Return list view page 
    - Listing Purchase Return
  - While Creating Purchase Return
    - Render page based on user profile (To be explained in separate page) 
    - Listing Vendor
    - Listing Depot
    - Listing Transaction Series for Purchase Invoice 
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

  - User chooses the 'Purchase Return  Entry' menu item. 
  - User should choose the Vendor details 
  - User should choose the Main Godown details 
  - User should choose the Depot details 
 - User should choose the Purchase Return Type details 
  - System should pick the Default Distributor details 
  - System should pick the Billing Address and shipping address of the selected Distributor
  - System should check the Distributor-product-pricing group and retrieve these items as qualified items for creating an Purchase Invoice 
  - User enters the product id/product name and desired quantity in respective fields.
  - User clicks on [Add item] button to add the next item.
  - System adds the desired product in draft mode 
  - User applies the Promotion/Coupon code if available.
  - Being continued,user clicks on 'Save' Invoice link.
  - User can enters Credit term type description.
  - System will create Purchase return and update the total amount as Return Amount
  - User clicks on 'Save' link and Purchase return will be created in 'Created/Publish' status.
  - User can select the 'Purchase return' and print the 'Purchase Invoice ' if required 

**Events based on Direct Purchase Return in Distributor Portal**

- Apply pricing 
  - Price for specific customer channel & product are to be arrived and same will get applied
  - Any Exceptions related to pricing computation to be captured and prompted in front end as 'toasted message' and same should get added to application logs

- Apply Tax 
  - Apply Tax as per the tax definition applicable for the distributor, customer, product criteria, tax identification availability.  
  - Any Exceptions related to Tax computation to be captured and prompted in front end as 'toasted message' and same should get added to application logs

- Apply Transaction series
   - Pick the Auto incremental sequencing codification and Apply for the Transaction series 

- Apply business workflow logic.
  - As per configuration, apply business logic based workflow for the respective modules.
 
- Apply Log 
  - Generate access log for application. 

 <!-- blank line -->
## Events at Unified Log
### Flow of related Events  (Save)

- Purchase Return  Service scope limited to Purchase Invoice  creation/amendment/cancel/delete. 
- Purchase Return  Service to trigger the related sub services which are internal and separate service. 

 <!-- blank line -->
- Customer Open Returns  to get updated in Distributor Purchase Return  screen 
- Purchase Return  status to get updated depending on the number of Return s get fulfilled 

 <!-- blank line -->
- Report related Purchase Return  data to be updated through services. 

# See also .. 
  - [Purchase Return  ](Purchase Return  )
  - [Purchase Return  Configurations](Purchase Return  Configurations)
  - [Domain Object Purchase Return  ](Domain Object Purchase Return  )
  - [Home](Home)

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTIwMTYyMTkzMTNdfQ==
-->
