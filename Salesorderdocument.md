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

7. **[Transaction Series](Transaction Series)**
    - default Sales Order Transaction Series are loaded, User can change these details as necessary. 

8. **Customer Shipping address** 
    - default Shipping address loaded, User can change these details as necessary. 

9. **Customer Billing address** 
    - default Billing address loaded, User can change these details as necessary. 

10. Fill in or Modify the remaining fields on the Sales Order page as necessary.
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
11. **Select a [Product](Product)** from list of eligible product for sales. 
    - After selection of line level [Product](Product), related information are pre-populated  
      - Batch details from current stock of [Distributor](Distributor)
      - Price to customer [PTR](#rate-calculation)
      - [Available Stock Quantity](Stock & Inventory) 
      - Sales [UOM](Unit of Measurement) 
      - [Applicable Tax](#rate-calculation) 

12. **Provide the sales order quantity**
    - After providing the sales order quantity, 
      - The value in the Line Amount field is calculated as Unit Price x Quantity. 
      - [Applies Tax](#tax) based on predefined [Tax Master](Tax Master) settings
      - Line level [Net Amount](Sales Order Calculation) is calculated. 

13. Fill in the **Discount** as necessary, to re-compute Tax amount & Net amount.
    - Amount Discount 
    - Percentage Discount 
    - Discount Per UOM
    - Manual Free Item  

14. **[Scheme defined](Scheme Master)** for item are applied as per configuration. 
    - any Scheme discount applied will re-compute the Tax amount & Net amount. 
    - Scheme product free are loaded based as per scheme.   
    - [Scheme applied](#scheme) at line level and overall document level. 

15. **Net amount** is computed after discount, Scheme discount & Tax related impact. 
    - _refer [Sales Order calculation logic](#rate-calculation)_

16. _Repeat **Addition of line level details** Step for adding more lines of item._ 

## Order Discount & Adjustments 

17. **Order level discount** can be provided to re-compute final [Order Amount](#rate-calculation)
    - Amount Discount 
    - Percentage Discount 
    - Discount Per UOM
    - Order Level Scheme Discount

18. **Save Sales Order ** 
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

## Bulk Order Processing
Bulk Order Processing refers to processing the mutiple sales open orders at the same time.
During the time of Bulk Order Processing , system will auto validate the configurations related to stock check based order conversion / Partial or full order conversion / credit limit norm checks

# Sales Order Configuration 
This page list all direct configuration applicable for Sales Order & related other module configuration which impacts Collections. 

> Other common configuration such as User profile based configuration, Field level configurations, Menu configurations are assumed to be as applicable similar to other modules in application. Refer [Common Application Configurations](Common Application Configurations) 
 
## Application level Configuration  

### Sales Order Module Configuration
| Configuration                                                                | Related Configuration | Details                                                                         | Ref #                                                     |
|------------------------------------------------------------------------------|-----------------------|---------------------------------------------------------------------------------|-----------------------------------------------------------|
| Display the stock in qty Godown only | | If enabled, display godown stock also in salesorder screen for quantity|[ FD-Conf-MAS-SO-0001](Sales Order Creation#FD-Conf-MAS-SO-0001)|
|Tax Option Enable|| If enabled, select option with tax mode (individual/group) will be displayed, based on selection tax calculation are done.|[ FD-Conf-MAS-SO-0002](Sales Order Creation#FD-Conf-MAS-SO-0002)|
|Currency Option Enable| | If enabled, select option with currency will be displayed, default indian rupee.|[ FD-Conf-MAS-SO-0003](Sales Order Creation#FD-Conf-MAS-SO-0003)|
|Shipping Tax Enable| | If enabled, Taxes For Shipping and Handling field will be available on sales order screen. for tax calculation.|[ FD-Conf-MAS-SO-0004](Sales Order Creation#FD-Conf-MAS-SO-0004)|
|Allow selection of Buyer from Buyer Master| | If enabled, user will be selecting the buyer on salesorder screen,If not, default buyer will be loaded initial, user can change the buyer if needed.|[ FD-Conf-MAS-SO-0005](Sales Order Creation#FD-Conf-MAS-SO-0005)|
|Forbid Generation of Default transaction Series| | If enabled, user to select the transaction series on salesorder screen.,If not, default transaction series will be loaded salesorder screen.|[ FD-Conf-MAS-SO-0006](Sales Order Creation#FD-Conf-MAS-SO-0006)|
|Allow Loading product out of stock| |If enabled, allow product out of stock to display.,If not, allow only stock available product.|Show Current stock for selected item|If enabled, display current stock in salesorder screen.|[ FD-Conf-MAS-SO-0007](Sales Order Creation#FD-Conf-MAS-SO-0007)|
|Allow adding new item to detail| | If enabled, display Add product icon in salesorder screen.|[ FD-Conf-MAS-SO-0008](Sales Order Creation#FD-Conf-MAS-SO-0008)|
|Throw error when stock position goes negative| | If enabled, display alert if stock is on negative values.|[ FD-Conf-MAS-SO-0009](Sales Order Creation#FD-Conf-MAS-SO-0009)|
|Allow Adhoc discount for each item| | If enabled, display Cash/AddDiscount option on each line item on salesorder screen.|[ FD-Conf-MAS-SO-0010](Sales Order Creation#FD-Conf-MAS-SO-0010)|
| Allow Adhoc discount for transaction| | If enabled, display Cash/AddDiscount option for transaction on salesorder screen.|[ FD-Conf-MAS-SO-0011](Sales Order Creation#FD-Conf-MAS-SO-0011)|
|Allow Applying Scheme for Transaction| | If enabled, display schemeDiscount option on each line item on salesorder screen.|[ FD-Conf-MAS-SO-0012](Sales Order Creation#FD-Conf-MAS-SO-0012)|
|Warn The User With Current Stock Position| | If enabled, warn the user if quantity entered exceed than quantity in stock on salesorder transaction.|[ FD-Conf-MAS-SO-0013](Sales Order Creation#FD-Conf-MAS-SO-0013)|
|List Price Editable| | If enabled, user is able to edit the price of product on salesorder screen.|[ FD-Conf-MAS-SO-0014](Sales Order Creation#FD-Conf-MAS-SO-0014)|
|Salesman Exceeded Credit Limit Allow| | If enabled, validate the salesman credit and restrict exceed limit on transaction.|[ FD-Conf-MAS-SO-0015](Sales Order Creation#FD-Conf-MAS-SO-0015)|
|Allow selection of products based on category group attachment for the Sales Order| | If enabled, display only product mapped on category group on salesorder screen.|[ FD-Conf-MAS-SO-0016](Sales Order Creation#FD-Conf-MAS-SO-0016)|
|Treat the selection of product category group as mandatory in sales order screen| | If enabled, product category group field is mandatory to be selected.|[ FD-Conf-MAS-SO-0017](Sales Order Creation#FD-Conf-MAS-SO-0017)|
|Generate Product Category Group based credit norms violation alert in Sales Order| | If enabled, credit norm alert to be displayed based on product category group on salesorder.|[ FD-Conf-MAS-SO-0018](Sales Order Creation#FD-Conf-MAS-SO-0018)|
|Net Amount Editable| | If enabled, allow the net amount column as editable.|[ FD-Conf-MAS-SO-0019](Sales Order Creation#FD-Conf-MAS-SO-0019)|
|Hide Shipping & Handling Charges| | If enabled, donot display Hide Shipping & Handling Charges field on salesorder screen.|[ FD-Conf-MAS-SO-0020](Sales Order Creation#FD-Conf-MAS-SO-0020)|
|Net Rate Editable| | If enabled, allow the user to edit net rate column on salesorder screen.|[ FD-Conf-MAS-SO-0021](Sales Order Creation#FD-Conf-MAS-SO-0021)|
|Filter the Product based on Product Properties 1 & 2| | If enabled, Product Properties 1 & 2 column will be available to filter the product on salesorder screen.|[ FD-Conf-MAS-SO-0022](Sales Order Creation#FD-Conf-MAS-SO-0022)|
|Generate alert message – if no tax is configured for the product| | If enabled, alert if no tax is configured for product.|[ FD-Conf-MAS-SO-0023](Sales Order Creation#FD-Conf-MAS-SO-0023)|
|Enable Save & Continue Option| | If enabled, save & continue icon will be displayed on salesorder screen.|[ FD-Conf-MAS-SO-0024](Sales Order Creation#FD-Conf-MAS-SO-0024)|
|Hide 'No Schemes to Apply' Message - if no schemes are applicable| | If enabled, 'No Schemes to Apply' Message - if no schemes are applicable for product not be displayed.|[ FD-Conf-MAS-SO-0025](Sales Order Creation#FD-Conf-MAS-SO-0025)|
|Enable Single Click Option in Bulk Order Conversion| | If enabled, icon will be available to convert bulk order so to si option, on bulk order conversion screen.|[ FD-Conf-MAS-SO-0026](Sales Order Creation#FD-Conf-MAS-SO-0026)|
|Direct SO to capture Product category| | If enabled, on direct so, capture the product category of the product availale on salesorder transaction.|[ FD-Conf-MAS-SO-0027](Sales Order Creation#FD-Conf-MAS-SO-0027)|
|Hide Apply Scheme| | If enabled, hide apply scheme icon on salesorder screen.|[ FD-Conf-MAS-SO-0028](Sales Order Creation#FD-Conf-MAS-SO-0028)|
|Sales Order to get latest batch price implementation| | If enabled, display the latest batch price details of product on transaction.|[ FD-Conf-MAS-SO-0029](Sales Order Creation#FD-Conf-MAS-SO-0029)|
|Allow SO from unapproved customers in the status of| | Set config status of unapprover customer to allow SO. |[ FD-Conf-MAS-SO-0030](Sales Order Creation#FD-Conf-MAS-SO-0030)|
|How many SO are allowed for unapproved customers| | Set limit for SO from unapproved customers|[ FD-Conf-MAS-SO-0031](Sales Order Creation#FD-Conf-MAS-SO-0031)|
|Apply SO Covertions With Completion Percentage| | If enabled, pending order conversion is handled with percentage configuration.If not, Order Conversion Invoice Level/Sales Order Conversion Line Level will not be processed.|[ FD-Conf-MAS-SO-0032](Sales Order Creation#FD-Conf-MAS-SO-0032)|
|Sales Order Conversion Line Level Completion Percentage| | If enabled, set line level value to be perfoemed for conversion|[ FD-Conf-MAS-SO-0033](Sales Order Creation#FD-Conf-MAS-SO-0033)|
|Sales Order Conversion Invoice Level Completion Percentage| | If enabled, set Order Conversion Invoice Level value to be perfoemed for conversion|[ FD-Conf-MAS-SO-0034](Sales Order Creation#FD-Conf-MAS-SO-0034)|
|Allow Single SO to Mutiple SI| | If enabled, allow single So to conversion to multiple SI.|[ FD-Conf-MAS-SO-0035](Sales Order Creation#FD-Conf-MAS-SO-0035)|
|Restrict selling of drug SKU to Non Drug customers for Sales Order / Sales Invoice Y/N| | If enabled, allow drug product selling for non drug customer,If not, restrict selling drug product to non drug customer.|[ FD-Conf-MAS-SO-0036](Sales Order Creation#FD-Conf-MAS-SO-0036)|
|Apply manual discounts on the Original Amount (Quantity X Rate) | |If enabled the manual discount to be considerd on amount of quantity,If not, scheme discount is not be considered.|[ FD-Conf-MAS-SO-0037](Sales Order Creation#FD-Conf-MAS-SO-0037)|
|Set the maximum discount % as while performing billing at MRP| |To be enabled and Set percentage of maximum discount to be applied on billing mrp transaction|[ FD-Conf-MAS-SO-0038](Sales Order Creation#FD-Conf-MAS-SO-0038)|
| Selection of Delivery Date Days| | To be enabled and Set no of days to configured for the delivery date of salesorder transaction.|[ FD-Conf-MAS-SO-0039](Sales Order Creation#FD-Conf-MAS-SO-0039)|
|Auto Close Sales Order Configuration|Close Sales order based on (Default / Order type) config values|If Default, Automatically close the sales order after Days,Set days value to auto close sales order.|[ FD-Conf-MAS-SO-0040](Sales Order Creation#FD-Conf-MAS-SO-0040)|
|Sales Order Type Configuration | | Set Order Types and days for the sales order close.,(Ex : mobile order, direct order) to set no of days to close sales order.|[ FD-Conf-MAS-SO-0041](Sales Order Creation#FD-Conf-MAS-SO-0041)|
|Auto Closure of Sales Order CRON Configurtion based on Retailer Channel| | If enabled, allow user to configure retailer channel and days to close sales order based on retailer channel type,(Ex : Bakery, Bunk, chemist) to set no of days to close sales order.|[ FD-Conf-MAS-SO-0042](Sales Order Creation#FD-Conf-MAS-SO-0042)|

# Bulk Order Conversion Configuration:

### Bulk Order Coversion Module Configuration
| Configuration                                                                | Related Configuration | Details                                                                         | Ref #                                                     |
|------------------------------------------------------------------------------|-----------------------|---------------------------------------------------------------------------------|-----------------------------------------------------------|
|Create Bill with available Stock for orders with partial stock availability||If enabled, allow conversion orders with partial stock quantity to invoice| [FD-Conf-MAS-BulkSO-0001](Bulk Sales Order Creation#FD-Conf-MAS-BulkSO-0001)|
|Product category to Product conversion to be applied||If enabled, product conversion is applied based on the product category|[FD-Conf-MAS-BulkSO-0002](Bulk Sales Order Creation#FD-Conf-MAS-BulkSO-0002)|
|SOH Lowest to Highest||If enabled, the product list is ordered from lowest to highest by quantity| [FD-Conf-MAS-BulkSO-0003](Bulk Sales Order Creation#FD-Conf-MAS-BulkSO-0003)|
|MRP Lowest to Highest||If enabled, the product list is ordered from lowest to highest by mrp|[FD-Conf-MAS-BulkSO-0004](Bulk Sales Order Creation#FD-Conf-MAS-BulkSO-0004)|
|SOH Lowest to Highest / SOH Lowest to Highest  ||If both enabled,  the product list is ordered from lowest to highest by quantity and mrp|[FD-Conf-MAS-BulkSO-0005](Bulk Sales Order Creation#FD-Conf-MAS-BulkSO-0005)|
|Settings for one click conversion|Customer credit norm violation treatment|Ignore customer credit norm violations while converting orders to invoices,If enabled, allow order conversion customer credit norms to invoices|[FD-Conf-MAS-BulkSO-0006](Bulk Sales Order Creation#FD-Conf-MAS-BulkSO-0006)|
|Do not convert the orders if the customer credit norm is violated||If enabled, do not allow order conversion customer credit norms to invoices|[FD-Conf-MAS-BulkSO-0006](Bulk Sales Order Creation#FD-Conf-MAS-BulkSO-0006)|
|Salesman credit norm violation treatment||Ignore salesman credit norm violations while converting orders to invoices,If enabled, allow order conversion salesman credit norms to invoices|[FD-Conf-MAS-BulkSO-0007](Bulk Sales Order Creation#FD-Conf-MAS-BulkSO-0007)|
|Do not convert the orders if the salesman credit norm is violated||If enabled, do not allow order conversion salesman credit norms to invoices|[FD-Conf-MAS-BulkSO-0008](Bulk Sales Order Creation#FD-Conf-MAS-BulkSO-0008)|
|Conversion rule setting in case of insufficient stock||Create bills with available stock for orders with partial stock availability,If enabled, allow conversion orders with partial stock quantity to invoice.|[FD-Conf-MAS-BulkSO-0009](Bulk Sales Order Creation#FD-Conf-MAS-BulkSO-0009)|
|Do not convert the orders to invoice in case of insufficient stock availability||If enabled, do not allow conversion orders with partial stock quantity to invoice|[FD-Conf-MAS-BulkSO-0010](Bulk Sales Order Creation#FD-Conf-MAS-BulkSO-0010)|

# Business Rule & Impact 

> Business rules are listed in the below section which requires Domain understanding, hope the previous sections of the Sales Order are clear. Refer [Sales Order ](Sales Order ), [Sales Order Creation](#creation-of-sales-Order )   

1.[FD-BR-SO-0001](FD-BR-SO-0001)- User access 

    1. Login user should has association with a Distributor. 
    2. In case of user associated with multiple user, then distributor selection is require before creating sales Order transaction 
    3. User with profile access configurations are to be applied while Listing Sales Order , Create, Modify, View Sales Order 

    > Refer User profile, Distributor User, Corporate User Distributor mapping 

2. [FD-BR-SO-0002](FD-BR-SO-0002) - List view of Sales Order 
    1. Listing page is default landing page, where newly created Sales Order are listed with selected information.
    2. All listing page related features are to be available for Sales Order listing Page. 
    3. Retrieve recently created top `20` Sales Order document with selected field where it belongs to a Distributor and sort with Order date. Default filter for Sales Order applicable for all users. 
    4. Custom filter to be available for all modules
    5. Default list view fields for distributor users  
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

3. [FD-BR-SO-0003](FD-BR-SO-0003) - Detail view actions
    1. Detail view of Order record enables you to perform actions like editing, cancel, amend, print the existing record in PDF format, all actions are configured through [Workflow](Workflow). 
    2. From the Order s list view, select the desired record. Details view of Order record should follow the Field access rule for the login user related profile. 

4. [FD-BR-SO-0004](FD-BR-SO-0004) - Create Sales Order 
    1. Allow creation of Sales Order based on Profile access configuration. 
    2. User Distributor association is mandatory for creating transaction. 
    3. Corporate User are indirect users create transaction related to specific associated distributor. 
    4. Creation of Sales Order should be restricted to user without distributor association. 

5. [FD-BR-SO-0005](FD-BR-SO-0005) -  Customer Selection 
    1. Listing of Customer for **Selection list** in transaction, criteria to be   
       - Distributor related customer, with status as per configuration 
       - Apply configuration impact [FD-Conf-SO-0007](#FD-Conf-SO-0007)
        
    2. Customer can be selected in any one of the following ways
      - Direct customer selection
      - Customer selection post Salesman selection
      - Customer selection post Salesman and Beat selection
    3. In all the above scenarios Customer, Beat and Salesman mapping is must. 
 
6. [FD-BR-SO-0006](FD-BR-SO-0006) -  Godown stock availability
    1.Order screen should have provision to display the Godown current stock 

7. [FD-BR-SO-0007](FD-BR-SO-0007) -  selection of Buyer from Buyer Master
    1.System should be allowed to either pick default buyer or user allowed to select buyer from buyer master  

8. [FD-BR-SO-0008](FD-BR-SO-0008) -  Generation of Default transaction Series
    1. Generation of Default transaction series or user allowed to set transaction series to generate running sequence for an order number

9. [FD-BR-SO-0009](FD-BR-SO-0009) - Display out of stock
    1.System should show the out of stock items based on configuration of out of stock show/not show 

10. [FD-BR-SO-0010](FD-BR-SO-0010) - Alert to show negative stock
   1. There should be an alert msg to show the list of items which has the negative stock 

11. [FD-BR-SO-0011](FD-BR-SO-0011) - Price Edit
   1. There should be an provision to enable / disable the price edit in the order screen

12. [FD-BR-SO-0012](FD-BR-SO-0012) -  SO allowed for unapproved customers
   1. There should be limit to allow the user to create the orders for Unapproved customers in the system 


13. [FD-BR-SO-0013](FD-BR-SO-0013) -  Single SO to Mutiple SI
   1.Enabling the option to either create Single SO to Single SI or Mulitple SI 


14. [FD-BR-SO-0014](FD-BR-SO-0014) - Selection of Delivery Date Days
   1.No of days to be configurable for the delivery date of each salesorder transaction.

### Bulk Order Conversion Configuration:

15. [FD-BR-SO-0015](FD-BR-SO-0015) - Invoice creation with available Stock for orders with partial stock availability
   1.Allow conversion of orders with partial stock quantity to invoice


16. [FD-BR-SO-0016](FD-BR-SO-0016) - Settings for one click conversion of Order
   1.Provision to Ignore / Allow customer credit norm violations while converting orders to invoices


17. [FD-BR-SO-0017](FD-BR-SO-0017) - Conversion rule setting in case of insufficient stock
   1.Create Invoice based on stock availability, To allow conversion of orders to invoice based on partial / full stock quantity 


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


# Event Flows 
## Events at Front End (Create)
  - Sales Order list view page 
    - Listing Sales  Order
  - While Creating Sales  Order
    - Render page based on user profile (To be explained in separate page) 
    - Listing Salesman
    - On Selection of Salesman, Retrieve Salesman Category info, Filter related Beat, Filter related customer.
    - Listing Beat 
    - On Selection of Beat, Retrieve relevant Customer, Salesman if not selected.  
    - Listing Customer
    - On Selection of Customer, retrieve relevant Beat, Salesman, Customer outstanding, Customer Info, Customer address
    - Listing Transaction Series for Sales Order
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

  - User chooses the 'Sales Order Entry' menu item. 
  - System should pick the Default Distributor details 
  - User selects the Salesman associated with that distributor
  - User selects the Beat name or code
  - System should list out the customer from the selected beat 
  - User should select the customer from the selected beat 
  - System should pick the Billing Address and shipping address of the selected customer 
  - System should check the Customer-salesman-product-pricing group and retrieve these items as qualified items for creating an invoice
  - System should also check the list of schemes available for the qualified items and  apply it while creating an Invoice 
  - System should check for configuration to apply or not to apply scheme on the invoice 
  - User enters the product id/product name and desired quantity in respective fields.
  - User clicks on [Add item] button to add the next item.
  - System adds the desired product in draft mode 
  - User applies the Promotion/Coupon code if available.
  - Being continued,user clicks on 'Save' Invoice link.
  - User can enters Credit term type description.
  - System will create Sales Order and update the total amount as Order Amount
  - User clicks on 'Save' link and Sales Order will be created in 'Created/Publish' status.
  - User can select the 'Sales Order' and print the 'Sales Order' if required 

**Events based on Mobile Based Order**

- Apply pricing 
  - Price for specific customer channel & product are to be arrived and same will get recomputed , price will not get Reapply
  - Any Exceptions related to pricing computation to be captured and prompted in front end as 'toasted message' and same should get added to application logs


- Apply Tax 
  - Recompute Tax as per the tax definition applicable for the distributor, customer, product criteria, tax identification availability.  
  - Any Exceptions related to Tax computation to be captured and prompted in front end as 'toasted message' and same should get added to application logs


- Apply scheme 
  - As per the scheme definition for the customer criteria, applicable distributor and product,Scheme will get reapplied
  - Apply Offtake scheme benefit as applicable for the customer. 
  - Any Exceptions related to scheme computation to be captured and prompted in front end as 'toasted message' and same should get added to application logs


- Apply Transaction series
   - Pick the Auto incremental sequencing codification and Apply for the Transaction series 


- Apply business workflow logic.
  - As per configuration, apply business logic based workflow for the respective modules.


- Apply Log 
  - Generate access log for application. 

**Events based on Direct Order**

- Apply pricing 
  - Price for specific customer channel & product are to be arrived and same will get applied
  - Any Exceptions related to pricing computation to be captured and prompted in front end as 'toasted message' and same should get added to application logs

- Apply Tax 
  - Apply Tax as per the tax definition applicable for the distributor, customer, product criteria, tax identification availability.  
  - Any Exceptions related to Tax computation to be captured and prompted in front end as 'toasted message' and same should get added to application logs


- Apply scheme 
  - As per the scheme definition for the customer criteria, aplicable distributor and product,Scheme has to be applied
  - Apply Offtake scheme benefit as applicable for the customer. 
  - Any Exceptions related to scheme computation to be captured and prompted in front end as 'toasted message' and same should get added to application logs

- Apply Transaction series
   - Pick the Auto incremental sequencing codification and Apply for the Transaction series 

- Apply business workflow logic.
  - As per configuration, apply business logic based workflow for the respective modules.
 
- Apply Log 
  - Generate access log for application. 

 <!-- blank line -->
## Events at Unified Log
### Flow of related Events  (Save)

- Sales Order Service scope limited to Sales invoice creation/amendment/cancel/delete. 
- Sales Order Service to trigger the related sub services which are internal and separate service. 

 <!-- blank line -->
- Customer Open orders  to get updated in Distributor sales order screen 
- Sales Order status to get updated depending on the number of orders get fulfilled 

 <!-- blank line -->
- Mail triggers to Customer on order confirmation status
- SMS triggers to Customer on order confirmation status
- Report related Sales order data to be updated through services. 

# See also .. 
  - [Sales Order ](Sales Order )
  - [Sales Order Configurations](Sales Order Configurations)
  - [Domain Object Sales Order ](Domain Object Sales Order )
  - [Home](Home)

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTIwMTYyMTkzMTNdfQ==
-->
