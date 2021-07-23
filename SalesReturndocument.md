Content

[[_TOC_]]

`Available for review`
# Creation of Sales Return 
A Sales Return  is a market return that get generated from the customer based on expiry stock / Damages , It will get created either by distributor operator through distributor portal or by salesperson using mobile application 

## Precondition for creating Sales Return  
Before creating a direct sales Return  , you need to 
* Create [Customer](Customer) details 
* Create [Beat](Beat) & [Salesman](Salesman) details 
* Create [Item](Product) details 
* Create [Pricing](Pricing) details 
* Create [Tax](Tax) details 

Creation of Sales Return  vary based on type of creation. 

## To Create Sales Return  

1. **Return  Date** is often set to default current date
   - There are options to allow backdated Return  but date after present date are restricted. 

2. **In the Customer field**, enter the name of an existing customer. 
   - Purchase Order are created to document the sale of goods to customer. 
   - After Customer selection, Customer related information are pre-populated as below,  
     - default [Beat](Beat), 
     - default [Salesman](Salesman), 
     - default Customer [Credit Term](Credit Term), 
     - default [Customer Shipping address](Customer) & 
     - default [Customer Billing address](Customer) are loaded.

> Further, these details are allowed to be modified as necessary.  

3. **Select a [Beat](Beat)** related to the selected Customer 
    - Multiple beats are loaded when the Customer is associated with multiple Beat

4. **Select a [Salesman](Salesman)** related to the selected Customer 
    - Multiple Salesman are listed based on the Customer associated with multiple Beat. 

5. **[Transaction Series](Transaction Series)**
    - default Purchase Order Transaction Series are loaded, User can change these details as necessary. 

6. **Customer Shipping address pick** 
    - default Shipping address loaded, User can change these details as necessary. 

7. **Sales Return Type** 
    - With Ref ir Withot Ref details , User can change these details as necessary. 

8. **Remarks**
     - Additional info can be provided 

9. Fill in or Modify the remaining fields on the Sales Return page as necessary.
    - Product
    - Batch
    - Sales Invoice
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

11. **Provide the Sales Return  quantity**
    - After providing the Sales Return  quantity, 
      - The value in the Line Amount field is calculated as Unit Price x Quantity. 
      - [Applies Tax](#tax) based on predefined [Tax Master](Tax Master) settings
      - Line level [Net Amount](Purchase Order Calculation) is calculated. 

12. **Select the Sales Invoice**
    - After providing the Sales Invoice reference  
      - The value in the Sales Invoice  calculated as Unit Price x Return Quantity. 
      - [Applies Tax](#tax) based on predefined [Tax Master](Tax Master) settings
      - Line level [Net Amount](Purchase Order Calculation) is calculated. 
    - _refer [Purchase Order calculation logic](#rate-calculation)_

## Invoice Discount & Adjustments against Sales Return

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

16. **Save Sales Return  ** 
On Saving of the Sales Return document, 
    - Document of Sales Return  is recorded with generation of unique Sales Return  Transaction number for a Customer
    - Line Item & quantity of details provided are added as part of Sales Return document 
    - Report data consolidation initiated for relevant data points. 
    - Sales Return is ready to [Print](Sales Return Print)

## Cancellation 
Cancellation of Sales Return are action performed against Delivered items (Sales Invoice or Without Sales Invoice ref) after preparation of Sales Return  . The reason may vary like "Wrongly created Return  ". Cancelled Return  are considered as valid document and used in all reports

Cancellation of Sales Return  are restricted based on configuration & workflow, few points as below. 

  - Business level restriction may vary based on configuration.  
    - Approved Sales Return  are not allowed to cancel, instead before the approval , sales return cancellation to be performed to maintain the logical accounting transactions. 

  - Data integrity related restrictions
    - Validation fails if the customer Return  amount update creates zero value scenario due to Zero price exist in the system against any line item. 
    - Deactivated master reference like customer, product, distributor, beat, salesman ..etc. will have impact to fail the cancellations. 

On Cancel of Sales Return  document, 
  - Document marked for status change to indicate cancellation. 
  - Report related Sales Return  data to be recomputed. 

## Amendment 
Amendment to Sales Return  are corrections to the prepared sales Return  . 
Amendment is not editing in record, the amended document is referred as valid document with status amended. 

Amendment performs validation and two primary actions as below, 
  - Cancel the old document of sales Return  by executing all cancellation action as mentioned in [Sales Return  cancellation section](#cancellation) 

  - Amendment of sales Return  are restricted to Business level restriction & Data integrity related restriction as mentioned in [cancellation](#cancellation) section. 

  - Further, Modification of key parameters are not allowed like Customer, Salesman, Beat.  

  - A new Sales Return  created with Sales Return  transaction number of old document. all action performed during sales Return  save are applicable for the newly created sales Return  document. 

- Market Sales Return  
  - A [Sales Return ](Sales Return ) records the customer's intent to return the damaged / Expired products at the stated price during the market visit by the salesperson

[Customer](Customer), [Salesman](Salesman), [Beat](Beat) and Item information are pre-loaded (pre-fetched from Sales Return ) to create the Invoice during conversion using Option 1 & 2.
Option 3, is auto processed to create Sales Return  . 

# Sales Return  Configuration 
This page list all direct configuration applicable for Sales Return  & related other module configuration which impacts Collections. 

> Other common configuration such as User profile based configuration, Field level configurations, Menu configurations are assumed to be as applicable similar to other modules in application. Refer [Common Application Configurations](Common Application Configurations) 
 
## Application level Configuration  

### Sales Return  Module Configuration
| Configuration                                                                | Related Configuration | Details                                                                         | Ref #                                                     |
|------------------------------------------------------------------------------|-----------------------|---------------------------------------------------------------------------------|-----------------------------------------------------------|
|Allow Back Dated Transaction||If enabled, allow back dated configuration|[ FD-Conf-MAS-SR-0001](Sales Order Creation#FD-Conf-MAS-SR-0001)|
|Display Transferd Customer||If enabled, display transfer customer on sales return screen|[ FD-Conf-MAS-SR-0002](Sales Order Creation#FD-Conf-MAS-SR-0002)|
|Allow Auto Batch Selection||If enabled, latest bctch will be auto loaded, on conversion from Rsr to SR transactions.If not, user has to select manual batch for line items|[ FD-Conf-MAS-SR-0003](Sales Order Creation#FD-Conf-MAS-SR-0003)|
|Compute tax even if the retailer not having GSTIN No||If enabled, allow to compute tax if retailer has no GSTIN|[ FD-Conf-MAS-SR-0004](Sales Order Creation#FD-Conf-MAS-SR-0004)|
|Restrict Free Quantity on Sales Return||If enabled, free quantity on sales return are restricted on transaction|[ FD-Conf-MAS-SR-0005](Sales Order Creation#FD-Conf-MAS-SR-0005)|
|Allow query search to take batch information from central repository||If enabled, batch populate list are displayed with batch information from central repository|[ FD-Conf-MAS-SR-0006](Sales Order Creation#FD-Conf-MAS-SR-0006)|
|Allow to select batch details before salesinvoice||If enabled, user can select batch details before selecting invoice details on sr SCREEN.If not, only after selecting salesinvoice no, batch details are allowed to select|[ FD-Conf-MAS-SR-0007](Sales Order Creation#FD-Conf-MAS-SR-0007)|
|Salesman and Beat are mandatory||If enabled, salesman and beat column are mandatory selection on SR transaction|[ FD-Conf-MAS-SR-0008](Sales Order Creation#FD-Conf-MAS-SR-0008)|
|Disable new batch creation on without reference SR||If enabled, new batch icon will be enabled only if SR type is without reference SR|[ FD-Conf-MAS-SR-0009](Sales Order Creation#FD-Conf-MAS-SR-0009)|
|Disable the tax on without reference sales returns||If enabled, sr type without reference sales returns transaction tax are disabled.If not, tax are calculated sr type without reference sales returns transaction|[ FD-Conf-MAS-SR-0010](Sales Order Creation#FD-Conf-MAS-SR-0010)|
|Sales Return to get special price for without reference||If enabled, allow transaction to get special price for line item on SR transaction|[ FD-Conf-MAS-SR-0011](Sales Order Creation#FD-Conf-MAS-SR-0011)|
|Back dated within the month||If enabled, allow only back dated for respective month|[ FD-Conf-MAS-SR-0012](Sales Order Creation#FD-Conf-MAS-SR-0012)|
|Back dated limit||Set limit, of no of days to back date list|[ FD-Conf-MAS-SR-0013](Sales Order Creation#FD-Conf-MAS-SR-0013)|
|Allow discount field to be editable for without reference||If enabled, discount filed is editable on SR screen|[ FD-Conf-MAS-SR-0014](Sales Order Creation#FD-Conf-MAS-SR-0014)|
|Within How Many Days SalesReturn Can Be Cancelled||Set limit day config on sr for cancellation days|[ FD-Conf-MAS-SR-0015](Sales Order Creation#FD-Conf-MAS-SR-0015)|
|Within How Many Days SalesReturn Can Be Amended||Set limit days, for SR amend transaction|[ FD-Conf-MAS-SR-0016](Sales Order Creation#FD-Conf-MAS-SR-0016)|
|Show pop-up when invoice number is selected to populate the rest of the line items automatically||If enabled, pop up will be displayed on selecting invoice with listig product in invoice no applied|[ FD-Conf-MAS-SR-0017](Sales Order Creation#FD-Conf-MAS-SR-0017)|
|TCS applicable for same month return only||If enabled, TCS is applicable for the same month on return transaction|[ FD-Conf-MAS-SR-0018](Sales Order Creation#FD-Conf-MAS-SR-0018)|
|Sales return auto close/expired months||Set limit duration to SR transaction to be closed/expire|[ FD-Conf-MAS-SR-0019](Sales Order Creation#FD-Conf-MAS-SR-0019)|
|Sales Return Default print version||Set default print version to print SR transaction|[ FD-Conf-MAS-SR-0020](Sales Order Creation#FD-Conf-MAS-SR-0020)|
|Disable Non salable quantity and Non Salable Stock||If enabled, Non salable quantity and Non Salable Stock are not allowe in SR transaction|[ FD-Conf-MAS-SR-0021](Sales Order Creation#FD-Conf-MAS-SR-0021)|
|Disable Godown Filed In SR||If enabled, gowdown filed will be disabled in SR screen|[ FD-Conf-MAS-SR-0022](Sales Order Creation#FD-Conf-MAS-SR-0022)|
|Disable Without Referance Option In Sales return type||If enabled, Without Referance Option will not be displayed on SR type option|[ FD-Conf-MAS-SR-0023](Sales Order Creation#FD-Conf-MAS-SR-0023)|
|Sales Invoice Selection Period in Months||Set limit month duration to select sales invoice transaction on SR|[ FD-Conf-MAS-SR-0024](Sales Order Creation#FD-Conf-MAS-SR-0024)|
|Enabling/Disabling SR Option||If enabled, + icon will be displayed on SR screen.If not, + icon will not be displayed|[ FD-Conf-MAS-SR-0025](Sales Order Creation#FD-Conf-MAS-SR-0025)|
|Allow multiple SalesInvoices in single SalesReturn||If enabled, allow multiple invoice selection on SR transaction|[ FD-Conf-MAS-SR-0026](Sales Order Creation#FD-Conf-MAS-SR-0026)|
|List deactivated product in sales return (with or without reference)||If enabled, allow inactive product in SR transaction.If not, allow only active products in SR transaction|[ FD-Conf-MAS-SR-0027](Sales Order Creation#FD-Conf-MAS-SR-0027)|
|Tariff based tax calculation in Sales Return||If enabled, allow tariff based calculation on SR transaction|[ FD-Conf-MAS-SR-0028](Sales Order Creation#FD-Conf-MAS-SR-0028)|
|Restrict users from returning invoices older then days,||If enabled, set limit of days to restrict returning the invoice for SR|[ FD-Conf-MAS-SR-0029](Sales Order Creation#FD-Conf-MAS-SR-0029)|
|Allow price recalculation in Central batch repository And formula is||If enabled, set formula for price recalculation in central batch|[ FD-Conf-MAS-SR-0030](Sales Order Creation#FD-Conf-MAS-SR-0030)|
|Tax Do not compute the tax amount for Sales Return without reference||If enabled, SR transaction tax will not be computated|[ FD-Conf-MAS-SR-0031](Sales Order Creation#FD-Conf-MAS-SR-0031)|
|Do not compute the tax amount for sales returns with reference if the return is performed after months from invoice date||If enabled, set limit duration of months, to restrict tax computation of sales invoice to SR|[ FD-Conf-MAS-SR-0032](Sales Order Creation#FD-Conf-MAS-SR-0032)|
|Generate alert message – if no tax is configured for the product||If enabled, alert will be notified if no tax mapped for product|[ FD-Conf-MAS-SR-0033](Sales Order Creation#FD-Conf-MAS-SR-0033)|
|Allow manual entry / editing of price points during new batch creation||If enabled, allow user to edit price on batch creation diplay|[ FD-Conf-MAS-SR-0034](Sales Order Creation#FD-Conf-MAS-SR-0034)|
|Re-compute the PTR based on formula – of formula is configured for PTR calculation||If enabled, based on formula configured, PTR will be re computed for SR transaction|[ FD-Conf-MAS-SR-0035](Sales Order Creation#FD-Conf-MAS-SR-0035)|


# Business Rule & Impact 

> Business rules are listed in the below section which requires Domain understanding, hope the previous sections of the Sales Return  are clear. Refer [Sales Return  ](Sales Return  ), [Sales Return  Creation](#creation-of-sales-Return  )   

1. [FD-BR-SR-0001] - User access 

>  FD-BR-SR-0001

    1. Login user should has association with a Distributor. 
    1. In case of user associated with multiple user, then distributor selection is require before creating sales Return  transaction 
    1. User with profile access configurations are to be applied while Listing Sales Return  , Create, Modify, View Sales Return  

    > Refer User profile, Distributor User, Corporate User Distributor mapping 

2. [FD-BR-SR-0002](#FD-BR-SR-0002) - List view of Sales Return  
    1. Listing page is default landing page, where newly created Sales Return  are listed with selected information.
    1. All listing page related features are to be available for Sales Return  listing Page. 
    1. Retrieve recently created top `20` Sales Return  document with selected field where it belongs to a Distributor and sort with Return  date. Default filter for Sales Return  applicable for all users. 
    1. Custom filter to be available for all modules
    1. Default list view fields for distributor users  
        - "transactionNumber" 
        - "Return  Date" 
        - "reference1Manual" 
        - "uniqueRetailerCode" 
        - "customername" 
        - "salesmanName" 
        - "beatname" 
        - "godownName" 
        - "buyerStatename" 
        - "sellerStatename" 
        - "Return  Amount" 
        - "Return  Outstanding" 
        - "status"
        - "nextStageName"
        - "modifiedon" 

       In default list view of users associated with multiple Distributors, 
       add `Distributor Name` fields. 

    > Refer [Listing page](Listing Page) functionalities, [Custom Filter](Custom Filter).

3. [FD-BR-SR-0003](FD-BR-SR-0003) - Detail view actions
    1. Detail view of Return  record enables you to perform actions like editing, cancel, amend, print the existing record in PDF format, all actions are configured through [Workflow](Workflow). 
    1. From the Return  s list view, select the desired record. Details view of Return  record should follow the Field access rule for the login user related profile. 

4. [FD-BR-SR-0004](FD-BR-SR-0004) - Create Sales Return  
    1. Allow creation of Sales Return  based on Profile access configuration. 
    1. User Distributor association is mandatory for creating transaction. 
    1. Corporate User are indirect users create transaction related to specific associated distributor. 
    1. Creation of Sales Return  should be restricted to user without distributor association. 

5. [FD-BR-SR-0005] -  Customer Selection 
    1. Listing of Customer for **Selection list** in transaction, criteria to be   
       - Distributor related customer, with status as per configuration 
       - Apply configuration impact [FD-Conf-SO-0007](#FD-Conf-SO-0007)
        
    1. Customer can be selected in any one of the following ways
      - Direct customer selection
      - Customer selection post Salesman selection
      - Customer selection post Salesman and Beat selection
    1. In all the above scenarios Customer, Beat and Salesman mapping is must. 
   

## Rate calculation 
1. **Sale Return  Price** is shown in any of the following ways.
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
| Sale Return Price                           | PTR of the item is shown. PTR is considered based on the Margin or Channel Wise Margin or Quotation         |
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

  - Sale Return  Price : PTR of the item
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
  - Multiple Tax are applicable for an item based on tax definition. All relevant tax details with split-up percentage to be available in Sales Return  document. 
  - Accurate calculation of tax amount is main criteria of Sales Return  document.


# Event Flows 
## Events at Front End (Create)
  - Sales Return  list view page 
    - Listing Sales  Return 
  - While Creating Sales  Return 
    - Render page based on user profile (To be explained in separate page) 
    - Listing Salesman
    - On Selection of Salesman, Retrieve Salesman Category info, Filter related Beat, Filter related customer.
    - Listing Beat 
    - On Selection of Beat, Retrieve relevant Customer, Salesman if not selected.  
    - Listing Customer
    - On Selection of Customer, retrieve relevant Beat, Salesman, Customer outstanding, Customer Info, Customer address
    - Listing Transaction Series for Sales Return 
    - Listing Product
    - On Selection of Product, retrieve relate product info, Batch details, Tax info, Scheme info, current stock position.
    - Listing Sales Invoice
    - List Batch info of the product
    - List relevant Adjustment info 
 
 <!-- blank line -->
## Events at Business logic layer (overview)
- Apply Dynamic front end access control based on user profile. 
- Generate record reference number for transaction internal reference. Every request should have this reference to process, manipulate or produce data. 

- Validate the data submitted from front end - Datatype & security related. 
- Validate the data submitted from front end - Business flow related. 

**Business flow validations**

  - User chooses the 'Sales Return  Entry' menu item. 
  - System should pick the Default Distributor details 
  - User selects the Salesman associated with that distributor
  - User selects the Beat name or code
  - System should list out the customer from the selected beat 
  - User should select the customer from the selected beat 
  - System should pick the shipping address Pick of the selected customer 
  - System should check the Customer-salesman-product-pricing group and retrieve these items as qualified items for creating an invoice
  - System should also check the invoice reference 
  - User enters the product id/product name and desired quantity in respective fields.
  - User clicks on [Add item] button to add the next item.
  - System adds the desired product in draft mode 
  - Being continued,user clicks on 'Save' Return' link.
  - System will create Sales Return  and update the total amount as Return  Amount
  - User clicks on 'Save' link and Sales Return  will be created in 'Created/Publish' status.
  - User can select the 'Sales Return ' and print the 'Sales Return ' if required 

**Events based on Mobile Based Return**

- Apply pricing 
  - Price for specific customer channel & product are to be arrived and same will get recomputed , price will not get Reapply
  - Any Exceptions related to pricing computation to be captured and prompted in front end as 'toasted message' and same should get added to application logs


- Apply Tax 
  - Recompute Tax as per the tax definition applicable for the distributor, customer, product criteria, tax identification availability.  
  - Any Exceptions related to Tax computation to be captured and prompted in front end as 'toasted message' and same should get added to application logs


- Apply Transaction series
   - Pick the Auto incremental sequencing codification and Apply for the Transaction series 


- Apply business workflow logic.
  - As per configuration, apply business logic based workflow for the respective modules.


- Apply Log 
  - Generate access log for application. 

**Events based on Direct Sales Return in Distributor Portal**

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

- Sales Return  Service scope limited to Sales invoice creation/amendment/cancel/delete. 
- Sales Return  Service to trigger the related sub services which are internal and separate service. 

 <!-- blank line -->
- Customer Open Return s  to get updated in Distributor sales Return  screen 
- Sales Return  status to get updated depending on the number of Return s get fulfilled 

 <!-- blank line -->
- Mail triggers to Customer on Return  confirmation status
- SMS triggers to Customer on Return  confirmation status
- Report related Sales Return  data to be updated through services. 

# See also .. 
  - [Sales Return  ](Sales Return  )
  - [Sales Return  Configurations](Sales Return  Configurations)
  - [Domain Object Sales Return  ](Domain Object Sales Return  )
  - [Home](Home)

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTIwMTYyMTkzMTNdfQ==
-->
