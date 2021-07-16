Content

[[_TOC_]]

`Available for review`
# Creation of Sales Order
A Sales Order is a market demand that get generated from the customer , It will get created either by distributor operator through distributor portal or by salesperson using mobile application.Counter Sales Order are created for direct end customer at distributor location.  

## Precondition for creating Sales Order 
Before creating a direct sales Order , you need to 
* Create[Customer](Customer) details 
* Create [Beat](Beat) & [Salesman](Salesman) details 
* Create [Item](Product) details 
* Create [Pricing](Pricing) details 
* Create [Scheme](Scheme) details 
* Create [Tax](Tax) details 

Creation of Sales Order vary based on type of creation. 

## To Create Sales Order 

1. **Order Date** is often set to default current date
   - There are options to allow backdated Order but date after present date are restricted. 

2. **In the Customer field**, enter the name of an existing customer. 
   - Sales Order are created to document the sale of goods to customer. 
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

5. **Select a Payment Mode** appropriately
6. **Select a Credit Term** if Payment Mode is credit.  

7. Stock **Location**
    - default distributor Godown to be mapped 
    - user can select appropriately, if there are multiple values in list.     

8. **[Transaction Series](Transaction Series)**
    - default Sales Order Transaction Series are loaded, User can change these details as necessary. 

9. **Customer Shipping address** 
    - default Shipping address loaded, User can change these details as necessary. 

10. **Customer Billing address** 
    - default Billing address loaded, User can change these details as necessary. 

11. Fill in or Modify the remaining fields on the Sales Order page as necessary.
    - Reference number Manual
    - Reference number Additional
    - Secondary Transaction series 
    - Remark 
    - Reason  
    - Description
    - Terms and Conditions
    - Referred by
    - Salesman Category Group 
    - Product Category Group (based on Salesman Category Group)
    - Delivery date
    - Tax Form 

> _These are the header details requires for creation of any Sales Order ._
> _You are now ready to fill in the Sales Order lines for products that you are selling to the Customer._

## Addition of line level details
12. **Select a [Product](Product)** from list of eligible product for sales. 
    - After selection of line level [Product](Product), related information are pre-populated  
      - Batch details from current stock of [Distributor](Distributor)
      - Price to customer [PTR](#rate-calculation)
      - [Available Stock Quantity](Stock & Inventory) 
      - Sales [UOM](Unit of Measurement) 
      - [Applicable Tax](#rate-calculation) 

13. **Provide the sales order quantity**
    - After providing the sales order quantity, 
      - The value in the Line Amount field is calculated as Unit Price x Quantity. 
      - [Applies Tax](#tax) based on predefined [Tax Master](Tax Master) settings
      - Line level [Net Amount](Sales Order Calculation) is calculated. 

14. Fill in the **Discount** as necessary, to re-compute Tax amount & Net amount.
    - Amount Discount 
    - Percentage Discount 
    - Discount Per UOM
    - Manual Free Item  

15. **[Scheme defined](Scheme Master)** for item are applied as per configuration. 
    - any Scheme discount applied will re-compute the Tax amount & Net amount. 
    - Scheme product free are loaded based as per scheme.   
    - [Scheme applied](#scheme) at line level and overall document level. 

16. **Net amount** is computed after discount, Scheme discount & Tax related impact. 
    - _refer [Sales Order calculation logic](#rate-calculation)_

17. _Repeat **Addition of line level details** Step for adding more lines of item._ 

## Order Discount & Adjustments 

18. **Order level discount** can be provided to re-compute final [Order Amount](#rate-calculation)
    - Amount Discount 
    - Percentage Discount 
    - Discount Per UOM
    - Order Level Scheme Discount

19. **Save Sales Order ** 
On Saving of the Sales Order document, 
    - Document of sales Order is recorded with generation of unique Sales Order Transaction number for a Distributor. 
    - Line Item & quantity of details provided are added as part of sales order document as Open order
    - Off take scheme benefit applied are accounted and updated. 
    - Report data consolidation initiated for relevant data points. 
    - Sales Order is ready to [Print](Sales Order Print)

## Cancellation 
Cancellation of Sales Order are action performed on Non-Invoiced sales Order after preparation of Sales Order . The reason may vary like "Wrongly created Order ". Cancelled Order are considered as valid document and used in all reports

Cancellation of Sales Order are restricted based on configuration & workflow, few points as below. 

  - Business level restriction may vary based on configuration.  
    - Invoiced Sales Order are not allowed to cancel, instead before the delivery , sales invoice cancellation to be performed to maintain the logical accounting transactions. 

  - Data integrity related restrictions
    - Validation fails if the customer order amount update creates zero value scenario due to Zero price exist in the system against any line item. 
    - Deactivated master reference like customer, product, distributor, beat, salesman ..etc. will have impact to fail the cancellations. 

On Cancel of Sales Order document, 
  - Document marked for status change to indicate cancellation. 
  - Report related Sales order data to be recomputed. 

## Amendment 
Amendment to Sales Order are corrections to the prepared sales Order . 
Amendment is not editing in record, the amended document is referred as valid document with status amended. 

Amendment performs validation and two primary actions as below, 
  - Cancel the old document of sales Order by executing all cancellation action as mentioned in [Sales Order cancellation section](#cancellation) 

  - Amendment of sales Order are restricted to Business level restriction & Data integrity related restriction as mentioned in [cancellation](#cancellation) section. 

  - Further, Modification of key parameters are not allowed like Customer, Salesman, Beat.  

  - A new Sales Order created with Sales Order transaction number of old document. all action performed during sales Order save are applicable for the newly created sales Order document. 

- Market Sales Order 
  - A [Sales Order](Sales Order) records the customer's intent to buy the listed products at the stated price during the market visit by the salesperson

User can have mulitple choices to convert the open sales orders into Sales Invoice. Sales Order to Sales Invoice conversion can be achieved in various options, as mentioned below.  
   1. Single Order conversion to [Sales Invoice](Sales Invoice)
   2. Bulk Order Processing with user input to confirm each [Sales Invoice](Sales Invoice)
   3. Bulk Order Processing to auto create [Sales Invoice ](Sales Invoice )

[Customer](Customer), [Salesman](Salesman), [Beat](Beat) and Item information are pre-loaded (pre-fetched from Sales Order) to create the Invoice during conversion using Option 1 & 2.
Option 3, is auto processed to create Sales Order . 

# Sales Order Configuration 
This page list all direct configuration applicable for Sales Order & related other module configuration which impacts Collections. 

> Other common configuration such as User profile based configuration, Field level configurations, Menu configurations are assumed to be as applicable similar to other modules in application. Refer [Common Application Configurations](Common Application Configurations) 
 
## Application level Configuration  

### Collection Module Configuration
| Configuration                                                                | Related Configuration | Details                                                                         | Ref #                                                     |
|------------------------------------------------------------------------------|-----------------------|---------------------------------------------------------------------------------|-----------------------------------------------------------|
| Display the stock in qty Godown only | | If enabled, display godown stock also in salesorder screen for quantity|
|Tax Option Enable| |If enabled, select option with tax mode (individual/group) will be displayed, based on selection tax calculation are done.|
|Currency Option Enable||If enabled, select option with currency will be displayed, default indian rupee.|
|Shipping Tax Enable||If enabled, Taxes For Shipping and Handling field will be available on sales order screen. for tax calculation.|
|Allow selection of Buyer from Buyer Master||If enabled, user will be selecting the buyer on salesorder screen.|If not, default buyer will be loaded initial, user can change the buyer if needed.|
|Forbid Generation of Default transaction Series||If enabled, user to select the transaction series on salesorder screen.,If not, default transaction series will be loaded salesorder screen.|
|Allow Loading product out of stock||If enabled, allow product out of stock to display.,If not, allow only stock available product.|Show Current stock for selected item|If enabled, display current stock in salesorder screen.|
*||Allow adding new item to detail||If enabled, display Add product icon in salesorder screen.|
|Throw error when stock position goes negative||If enabled, display alert if stock is on negative values.|
|Allow Adhoc discount for each item||If enabled, display Cash/AddDiscount option on each line item on salesorder screen.|
| Allow Adhoc discount for transaction||If enabled, display Cash/AddDiscount option for transaction on salesorder screen.|
|Allow Applying Scheme for Transaction||If enabled, display schemeDiscount option on each line item on salesorder screen.|
|Warn The User With Current Stock Position||If enabled, warn the user if quantity entered exceed than quantity in stock on salesorder transaction.|
|List Price Editable||If enabled, user is able to edit the price of product on salesorder screen.|
|Salesman Exceeded Credit Limit Allow||If enabled, validate the salesman credit and restrict exceed limit on transaction.|
|Allow selection of products based on category group attachment for the Sales Order||If enabled, display only product mapped on category group on salesorder screen.|
|Treat the selection of product category group as mandatory in sales order screen||If enabled, product category group field is mandatory to be selected.|
|Generate Product Category Group based credit norms violation alert in Sales Order||If enabled, credit norm alert to be displayed based on product category group on salesorder.|
|Net Amount Editable|| If enabled, allow the net amount column as editable.|
|Hide Shipping & Handling Charges||If enabled, donot display Hide Shipping & Handling Charges field on salesorder screen.|
|Net Rate Editable||If enabled, allow the user to edit net rate column on salesorder screen.|
|Filter the Product based on Product Properties 1 & 2|| If enabled, Product Properties 1 & 2 column will be available to filter the product on salesorder screen.|
|Generate alert message – if no tax is configured for the product||If enabled, alert if no tax is configured for product.|
|Enable Save & Continue Option||If enabled, save & continue icon will be displayed on salesorder screen.|
|Hide 'No Schemes to Apply' Message - if no schemes are applicable||If enabled, 'No Schemes to Apply' Message - if no schemes are applicable for product not be displayed.|
|Enable Single Click Option in Bulk Order Conversion||If enabled, icon will be available to convert bulk order so to si option, on bulk order conversion screen.|
|Direct SO to capture Product category||If enabled, on direct so, capture the product category of the product availale on salesorder transaction.|
|Hide Apply Scheme||If enabled, hide apply scheme icon on salesorder screen.|
|Sales Order to get latest batch price implementation||If enabled, display the latest batch price details of product on transaction.|
|Allow SO from unapproved customers in the status of||Set config status of unapprover customer to allow SO. |
|How many SO are allowed for unapproved customers||Set limit for SO from unapproved customers|
|Apply SO Covertions With Completion Percentage||If enabled, pending order conversion is handled with percentage configuration.If not, Order Conversion Invoice Level/Sales Order Conversion Line Level will not be processed.|
|Sales Order Conversion Line Level Completion Percentage|If enabled, set line level value to be perfoemed for conversion|
|Sales Order Conversion Invoice Level Completion Percentage||If enabled, set Order Conversion Invoice Level value to be perfoemed for conversion|
|Allow Single SO to Mutiple SI||If enabled, allow single So to conversion to multiple SI.|
|Restrict selling of drug SKU to Non Drug customers for Sales Order / Sales Invoice Y/N||If enabled, allow drug product selling for non drug customer,If not, restrict selling drug product to non drug customer.|
|Apply manual discounts on the Original Amount (Quantity X Rate)|| If enabled the manual discount to be considerd on amount of quantity,If not, scheme discount is not be considered.|
|Set the maximum discount % as while performing billing at MRP||To be enabled and Set percentage of maximum discount to be applied on billing mrp transaction|
| Selection of Delivery Date Days||To be enabled and Set no of days to configured for the delivery date of salesorder transaction.|
|Auto Close Sales Order Configuration|Close Sales order based on (Default / Order type) config values||If Default, Automatically close the sales order after Days,Set days value to auto close sales order.|
|Sales Order Type Configuration ||Set Order Types and days for the sales order close.,(Ex : mobile order, direct order) to set no of days to close sales order.|
|Auto Closure of Sales Order CRON Configurtion based on Retailer Channel||If enabled, allow user to configure retailer channel and days to close sales order based on retailer channel type,(Ex : Bakery, Bunk, chemist) to set no of days to close sales order.|

# Business Rule & Impact 

> Business rules are listed in the below section which requires Domain understanding, hope the previous sections of the Sales Order are clear. Refer [Sales Order ](Sales Order ), [Sales Order Creation](#creation-of-sales-Order )   

1. [FD-BR-SI-0001] - User access 

>  FD-BR-SI-0001

    1. Login user should has association with a Distributor. 
    1. In case of user associated with multiple user, then distributor selection is require before creating sales Order transaction 
    1. User with profile access configurations are to be applied while Listing Sales Order , Create, Modify, View Sales Order 

    > Refer User profile, Distributor User, Corporate User Distributor mapping 

1. [FD-BR-SI-0002](#FD-BR-SI-0002) - List view of Sales Order 
    1. Listing page is default landing page, where newly created Sales Order are listed with selected information.
    1. All listing page related features are to be available for Sales Order listing Page. 
    1. Retrieve recently created top `20` Sales Order document with selected field where it belongs to a Distributor and sort with Order date. Default filter for Sales Order applicable for all users. 
    1. Custom filter to be available for all modules
    1. Default list view fields for distributor users  
        - "transactionNumber" 
        - "Order Date" 
        - "reference1Manual" 
        - "uniqueRetailerCode" 
        - "customername" 
        - "salesmanName" 
        - "beatname" 
        - "godownName" 
        - "buyerStatename" 
        - "sellerStatename" 
        - "Order Amount" 
        - "Order Outstanding" 
        - "status"
        - "nextStageName"
        - "modifiedon" 

       In default list view of users associated with multiple Distributors, 
       add `Distributor Name` fields. 

    > Refer [Listing page](Listing Page) functionalities, [Custom Filter](Custom Filter).

1. [FD-BR-SI-0003](FD-BR-SI-0003) - Detail view actions
    1. Detail view of Order record enables you to perform actions like editing, cancel, amend, print the existing record in PDF format, all actions are configured through [Workflow](Workflow). 
    1. From the Order s list view, select the desired record. Details view of Order record should follow the Field access rule for the login user related profile. 

1. [FD-BR-SI-0004](FD-BR-SI-0004) - Create Sales Order 
    1. Allow creation of Sales Order based on Profile access configuration. 
    1. User Distributor association is mandatory for creating transaction. 
    1. Corporate User are indirect users create transaction related to specific associated distributor. 
    1. Creation of Sales Order should be restricted to user without distributor association. 

1. [FD-BR-SI-0005] -  Customer Selection 
    1. Listing of Customer for **Selection list** in transaction, criteria to be   
       - Distributor related customer, with status as per configuration 
       - Apply configuration impact [FD-Conf-SI-0007](#FD-Conf-SI-0007)
        
    1. Customer can be selected in any one of the following ways
      - Direct customer selection
      - Customer selection post Salesman selection
      - Customer selection post Salesman and Beat selection
    1. In all the above scenarios Customer, Beat and Salesman mapping is must. 
   

## Rate calculation 
1. **Sale Order Price** is shown in any of the following ways.
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

4. **Sample Calculation**

| Detail Field                         | Description & Calculation Formula                                                                           |
|--------------------------------------|-------------------------------------------------------------------------------------------------------------|
| Item Name                            | User can select the product by Item Code or Name                                                            |
| Batch                                | By default first batch is selected. Batch is listed on FIFO logic                                           |
| UOM                                  | Default Sales UOM is selected initially. User can change if required by shortcut also or manually change it |
| Sale Order Price                           | PTR of the item is shown. PTR is considered based on the Margin or Channel Wise Margin or Quotation         |
| Net Rate                             | Sale Price of item + Tax Amount is calculated for 1 quantity and shown.                                     |
| Quantity                             | User can enter quantity. Quantity entered is considered as per UOM selected                                 |
| Amount                               | Quantity * Sale Price is calculated and shown                                                               |
| Discount%                            | Manual discount percentage                                                                                  |
| Discount Amount                      | Discount Amount is shown                                                                                    |
| Scheme Discount%                     | Scheme Discount % is shown. For Amount scheme also, Discount % is also calculated and shown                 |
| Scheme Amount                        | Scheme Amount is shown.  Even for % Scheme, Discount Amount is calculated and shown                         |
| Net Amount (Taxable)                 | Taxable net amount. Amount - (Scheme Amount + Discount Amount). Based on configuration this formula varies |
| Tax Amount (Tax Split up also shown) | Tax Amount calculated on Net Amount is calculated & Shown                                                   |
| Net Tax Amount                       | Tax amount deducted on proposition from Additional Discount given in Order is shown here                  |
| Type                                 | Always Second Sales                                                                                         |
| Total                                | Net Amount + Tax Amount is calculated & Shown                                                               |
| Scheme Discount (Order Level)      | Order level Scheme Discount is propositioned item level and shown                                         |
| Trade Discount (Order Level)       | Order level Trade Discount amount is proportioned item level and shown                                    |
| Net Amount                           | Total - (Trade Discount + Scheme Discount) is calculated and shown                                          |

  - Sale Order Price : PTR of the item
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


## Scheme 
  - Sales Order are applied with respective scheme as defined or applicable. 
  - Applicable scheme are based on various criteria's like Product, Product category, Customer, Customer Type, Channel Type, Distributor, Distributor Cluster, Geo hierarchy, Mode of payment, ..etc. Refer [Scheme master](Scheme) for types of scheme. 
  - Different types of Scheme applies, some of the most used Scheme Type as below, 
    - Item by Quantity
    - Item by Value
    - Item By Qty - Lines cut 
    - `SMJ Pending - Add Order level scheme types`
  - Gross Amount : (Quantity * Sale Price)
  - Gross Amount with tax : (Quantity * Rate + Tax)
  - After Manual Discount : ((Quantity * Rate - line level Addl. Discount)
  - After Manual Discount with tax : ((Quantity * Rate - line level Addl. Discount+ Tax)
  - **On-Take Scheme** are applied while preparing the Sales Order . 
  - **Off-Take Scheme** benefits are applied as per the pending benefit list as applicable for the selected customer. 
  - Sales Order scheme benefits are [computed](Scheme engine) and applied.  
  
## Tax 
  - Tax Components can be
    - 1. State Tax
    - 2. Central Taxb y
    - 3. Inter-state Tax
    - 4. Cess
    - 5. Cess on Quantity
    - 6. Cess applicable for the particular state
  - Tax applicable for the product, related geo hierarchy of distributor, [State](State) of distributor, [State](State) of Customer, Tax identifier details of customer, Tax form applied for the customer.
  - Multiple Tax are applicable for an item based on tax definition. All relevant tax details with split-up percentage to be available in Sales Order document. 
  - Accurate calculation of tax amount is main criteria of Sales Order document.


# See also .. 
  - [Sales Order ](Sales Order )
  - [Sales Order Configurations](Sales Order Configurations)
  - [Domain Object Sales Order ](Domain Object Sales Order )
  - [Home](Home)

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTIwMTYyMTkzMTNdfQ==
-->