Content

[[_TOC_]]

`Available for review`
# Creation of Purchase Invoice 
 Purchase Invoice is a primary order fullfillment that has get created by the supplier to the Distributor based on the purchase order raised by the distributor , It will get created by Supplier from Plant location.  

## Precondition for creating Purchase Invoice  
Before creating a direct Purchase Invoice  , you need to 
* Create [Vendor](Vendor) details 
* Create [Distributor](Distributor) details 
* Create [Item](Product) details 
* Create [Pricing](Pricing) details 
* Create [Scheme](Scheme) details 
* Create [Tax](Tax) details 

Creation of Purchase Invoice  vary based on type of creation. 

## To Create Purchase Invoice  

1. **Purchase Invoice  Date** is often set to default current date
   - There are options to allow backdated Invoice  but date after present date are restricted. 

2. **In the Vendor field**, enter the name of an existing Vendor
   - Purchase Invoice  are created to document the Primary order to the distributor
   - After Vendor selection, Other related information to be filed in below,  
     - default [Distributor](Distributor), 
     - default [Distributor Shipping address,,City,State,Pincode](Distributor) & 
     - default [Distributor Billing address,City,State,Pincode](Distributor) are loaded.

> Further, these details are allowed to be modified as necessary.  

3. **[Transaction Series](Transaction Series)**
    - default Purchase Invoice  Transaction Series are loaded, User can change these details as necessary. 

4. **Customer Shipping address** 
    - default Shipping address loaded, User can change these details as necessary. 

5. **Customer Billing address** 
    - default Billing address loaded, User can change these details as necessary. 

7. Fill in or Modify the remaining fields on the Purchase Invoice  page as necessary.
    - Remark 
    - Reason  

> _These are the header details requires for creation of any Purchase Invoice  ._
> _You are now ready to fill in the Purchase Invoice  lines for products that you are selling to the Customer._

## Addition of line level details
8. **Select a [Product](Product)** from list of eligible product for sales. 
    - After selection of line level [Product](Product), related information are pre-populated  
      - Batch details from current stock of [Distributor](Distributor)
      - Price to customer [PTR](#rate-calculation)
      - [Available Stock Quantity](Stock & Inventory) 
      - Purchase [UOM](Unit of Measurement) 
      - [Applicable Tax](#rate-calculation) 

9. **Provide the Purchase Invoice  quantity**
    - After providing the Purchase Invoice  quantity, 
      - The value in the Line Amount field is calculated as Unit Price x Quantity. 
      - [Applies Tax](#tax) based on predefined [Tax Master](Tax Master) settings
      - Line level [Net Amount](Purchase Invoice  Calculation) is calculated. 

10. **Net amount** is computed 
    - _refer [Purchase Invoice  calculation logic](#rate-calculation)_

11. _Repeat **Addition of line level details** Step for adding more lines of item._ 

## Cancellation 
Cancellation of Purchase Invoice  are action performed. The reason may vary like "Wrongly created Purchase Invoice  ". Cancelled Invoice  are considered as valid document and used in all reports

Cancellation of Purchase Invoice  are restricted based on configuration & workflow, few points as below. 

  - Business level restriction may vary based on configuration.  
    - Posted Purchase Invoice  are not allowed to cancel, Instead Purchase return can be used to manage the cancellation and maintain the logical accounting transactions. 

  - Data integrity related restrictions
    - Validation fails if the Distributor Invoice  amount update creates zero value scenario due to Zero price exist in the system against any line item. 
    - Deactivated master reference like product, distributor . will have impact to fail the cancellations. 

On Cancel of Purchase Invoice  document, 
  - Document marked for status change to indicate cancellation. 
  - Report related Purchase Invoice  data to be recomputed. 

## Amendment 
Amendment to Purchase Invoice  are corrections to the prepared Purchase Invoice  . 
Amendment is not editing in record, the amended document is referred as valid document with status amended. 

Amendment performs validation and two primary actions as below, 
  - Cancel the old document of Purchase Invoice  by executing all cancellation action as mentioned in [Purchase Invoice  cancellation section](#cancellation) 

  - Amendment of Purchase Invoice  are restricted to Business level restriction & Data integrity related restriction as mentioned in [cancellation](#cancellation) section. 

  - Further, Modification of key parameters are not allowed like vendor

  - A new Purchase Invoice  created with Purchase Invoice  transaction number of old document. all action performed during Purchase Invoice  save are applicable for the newly created Purchase Invoice  document. 

# Purchase Invoice  Configuration 
This page list all direct configuration applicable for Purchase Invoice  & related other module configuration  

> Other common configuration such as User profile based configuration, Field level configurations, Menu configurations are assumed to be as applicable similar to other modules in application. Refer [Common Application Configurations](Common Application Configurations) 
 
## Application level Configuration  

### Purchase Invoice  Module Configuration
| Configuration                                                                | Related Configuration | Details                                                                         | Ref #                                                     |
|------------------------------------------------------------------------------|-----------------------|---------------------------------------------------------------------------------|-----------------------------------------------------------|
|Allow Selection of Vendor||If enabled, allow user ti select vendor.If not, default vendor will be loaded|[FD-Conf-MAS-PI-0001](Purchase Invoice  Creation#FD-Conf-MAS-PI-0001)|
|Is BackDated Transactions allowed||If enabled, allow backdated for PI transaction|[FD-Conf-MAS-PI-0002](Purchase Invoice  Creation#FD-Conf-MAS-PI-0002)|
|System Transaction Number||If enabled, generate System Transaction Number for PI transaction|[FD-Conf-MAS-PI-0003](Purchase Invoice  Creation#FD-Conf-MAS-PI-0003)|
|Load products those are out of stock||If enabled, Load products those are out of stock will be liated on PI|[FD-Conf-MAS-PI-0004](Purchase Invoice  Creation#FD-Conf-MAS-PI-0004)|
|Show Current Stock for each item||If enabled , Show Current Stock for each item on PI line items|[FD-Conf-MAS-PI-0005](Purchase Invoice  Creation#FD-Conf-MAS-PI-0005)|
|Adding New Item Allowed||I enabled, Add product icon will be displayed on PI screen|[FD-Conf-MAS-PI-0006](Purchase Invoice  Creation#FD-Conf-MAS-PI-0006)|
|Show Error when Stock is Negative||If enabled, if stock is negative, error msg will be notified|[FD-Conf-MAS-PI-0007](Purchase Invoice  Creation#FD-Conf-MAS-PI-0007)|
|Adhoc discount applicable for each item||If enabled, discount is applicable for each line item|[FD-Conf-MAS-PI-0008](Purchase Invoice  Creation#FD-Conf-MAS-PI-0008)|
|Adhoc discount applicable for transaction||If enabled, discount is applicable for PI transaction|[FD-Conf-MAS-PI-0009](Purchase Invoice  Creation#FD-Conf-MAS-PI-0009)|
|Adhoc scheme applicable on transaction||If enabled, scheme discount is applicable PI transaction|[FD-Conf-MAS-PI-0010](Purchase Invoice  Creation#FD-Conf-MAS-PI-0010)|
|List Price is editable||If enabled, user can edit the list price of items on PI|[FD-Conf-MAS-PI-0011](Purchase Invoice  Creation#FD-Conf-MAS-PI-0011)|
|Tax Option Enable||If enabled, Tax column (individual / group) is displayed for tax type compute on PI.If not, individual is for tax type compute on PI|[FD-Conf-MAS-PI-0012](Purchase Invoice  Creation#FD-Conf-MAS-PI-0012)|
|Currency Option Enable||If enabled, Currency Option column will be displayed on PI item screen|[FD-Conf-MAS-PI-0013](Purchase Invoice  Creation#FD-Conf-MAS-PI-0013)|
|Shipping Tax Enable||If enabled, shipping tax column is available on PI screen to compute|[FD-Conf-MAS-PI-0014](Purchase Invoice  Creation#FD-Conf-MAS-PI-0014)|
|Credit Limit Popup||If enabled, alert user if any credit limit on PI transaction|[FD-Conf-MAS-PI-0015](Purchase Invoice  Creation#FD-Conf-MAS-PI-0015)|
|Billing Address Editable||If enabled, billing address is editable|[FD-Conf-MAS-PI-0016](Purchase Invoice  Creation#FD-Conf-MAS-PI-0016)|
|Shipping Address Editable||If enabled, shipping address is editable|[FD-Conf-MAS-PI-0017](Purchase Invoice  Creation#FD-Conf-MAS-PI-0017)|
|Enable Credit Limit Alert For Purchase Invoice Screen||If enabled, Credit Limit Alert For Purchase Invoice Screen will be displayed to user|[FD-Conf-MAS-PI-0018](Purchase Invoice  Creation#FD-Conf-MAS-PI-0018)|
|Restrict User From Entering Excess Quantity In Purchase Invoice||If enabled, user has restriction on entering the quantity not to exceeed on product|[FD-Conf-MAS-PI-0019](Purchase Invoice  Creation#FD-Conf-MAS-PI-0019)|
|Block Discount popup when converting Receive Purchase Invoice to Purchase Invoice||If enaboed, discount pop will not be vissible on RPI to PI conversion|[FD-Conf-MAS-PI-0020](Purchase Invoice  Creation#FD-Conf-MAS-PI-0020)|
|Allow Direct PI when MRP value as ZERO||If enabled, PI is allowed to create with ZERO mrp value|[FD-Conf-MAS-PI-0021](Purchase Invoice  Creation#FD-Conf-MAS-PI-0021)|
|Disable direct creation of Purchase Invoice||If enabled, direct PI creation is restricted for user ti create|[FD-Conf-MAS-PI-0022](Purchase Invoice  Creation#FD-Conf-MAS-PI-0022)|
|Restrict Free Quantity on Purchase Invoice||If enabled, free quantity will not be populated on PI transaction|[FD-Conf-MAS-PI-0023](Purchase Invoice  Creation#FD-Conf-MAS-PI-0023)|
|Apply price based on Product Price||If enabled, mrp, pts and ptr are loaded as applicable for product on PI|[FD-Conf-MAS-PI-0024](Purchase Invoice  Creation#FD-Conf-MAS-PI-0024)|
|Load Suggestions for prices in manual PI||If enabled, PI product are listed with price and not editable|[FD-Conf-MAS-PI-0025](Purchase Invoice  Creation#FD-Conf-MAS-PI-0025)|
|Disable corporate default vendor in manual invoice||If enabled, vendor default loading is restricted on PI|[FD-Conf-MAS-PI-0026](Purchase Invoice  Creation#FD-Conf-MAS-PI-0026)|
|Load last billed prices in Manual PI||If enabled, load latest bill prce for product in PI transaction|[FD-Conf-MAS-PI-0027](Purchase Invoice  Creation#FD-Conf-MAS-PI-0027)|
|Show Net PTS in Batch Grid||If enabled, net pts value will be displayed on product batch grip|[FD-Conf-MAS-PI-0028](Purchase Invoice  Creation#FD-Conf-MAS-PI-0028)|
|Show Orginal PTS in Batch Grid||If enabled, display Orginal PTS in Batch Grid product details|[FD-Conf-MAS-PI-0029](Purchase Invoice  Creation#FD-Conf-MAS-PI-0029)|
|Show PFM in Batch Grid||If enabled, display PFM in Batch Grid product details|[FD-Conf-MAS-PI-0030](Purchase Invoice  Creation#FD-Conf-MAS-PI-0030)|
|Show Other discounts in PI||If enabled,  display Other discounts column in PI|[FD-Conf-MAS-PI-0031](Purchase Invoice  Creation#FD-Conf-MAS-PI-0031)|
|Show Secondary Transaction Series||If enabled, Secondary Transaction Series field will be displayed on PI screen|[FD-Conf-MAS-PI-0032](Purchase Invoice  Creation#FD-Conf-MAS-PI-0032)|
|Recalculate price in Batch grid based on UOM||If enabled, Recalculate price in Batch grid based on UOM based on UOM and quantity of product|[FD-Conf-MAS-PI-0033](Purchase Invoice  Creation#FD-Conf-MAS-PI-0033)|
|Display Purchase Invoice with the status of||Set status to Display PI on screen with configure status|[FD-Conf-MAS-PI-0034](Purchase Invoice  Creation#FD-Conf-MAS-PI-0034)|
|Display Purchase Invoice with the next stage of||Set next stage to Display PI on screen with configure next stage|[FD-Conf-MAS-PI-0035](Purchase Invoice  Creation#FD-Conf-MAS-PI-0035)|
|Update Stock based on Purchase bill date when Date wise Inventory is ON||If enabled, stock updated based on PI bill date.If not, transaction based on PI stock updated on PI date|[FD-Conf-MAS-PI-0036](Purchase Invoice  Creation#FD-Conf-MAS-PI-0036)|
|Show price in batch grid based on RPI Price||If enabled, PI price details are listed based on RPI price details|[FD-Conf-MAS-PI-0037](Purchase Invoice  Creation#FD-Conf-MAS-PI-0037)|
|Disable purchase invoice draft creation||If enabled, Draft icon is disabled on PI screen|[FD-Conf-MAS-PI-0038](Purchase Invoice  Creation#FD-Conf-MAS-PI-0038)|
|Enable Reference Number mandatory in Manual and Auto PI||If enabled, Reference Number field is mandatory on PI fields and Auto pi|[FD-Conf-MAS-PI-0039](Purchase Invoice  Creation#FD-Conf-MAS-PI-0039)|
|Unique Validation Configuration For Manual PI||Set configure Unique Validation Configuration For Manual PI based on ref no, ref descripton, ref no+ref description|[FD-Conf-MAS-PI-0040](Purchase Invoice  Creation#FD-Conf-MAS-PI-0040)|
|Unique Validation Configuration For Auto PI||Set configure Unique Validation Configuration For Auto PI based on ref no, ref descripton, ref no+ref description|[FD-Conf-MAS-PI-0041](Purchase Invoice  Creation#FD-Conf-MAS-PI-0041)|
|Update Reference Number with Reference Description value if empty||If enabled, Refer num is updated with ref desc if ref no is empty|[FD-Conf-MAS-PI-0042](Purchase Invoice  Creation#FD-Conf-MAS-PI-0042)|
|Allow zero PTS in Manual Purchase Invoice||If enabled, pts zero value is allowed on manual PI|[FD-Conf-MAS-PI-0043](Purchase Invoice  Creation#FD-Conf-MAS-PI-0043)|
|Allow zero PTR in Manual Purchase Invoice||If enabled, ptr zero value is allowed on manual PI|[FD-Conf-MAS-PI-0044](Purchase Invoice  Creation#FD-Conf-MAS-PI-0044)|
|Select False to validate PTR should not be greater than MRP||If false selected, restrict user if ptr is greater then mrp|[FD-Conf-MAS-PI-0045](Purchase Invoice  Creation#FD-Conf-MAS-PI-0045)|
|Allow vendor based credit term||If enabled, vendor based credit term is allowe on PI transaction|[FD-Conf-MAS-PI-0046](Purchase Invoice  Creation#FD-Conf-MAS-PI-0046)|
|Allow editing of quantity in batch when creating PI from RPI||If enabled, quantity value can be changed from conversion of RPI to PI|[FD-Conf-MAS-PI-0047](Purchase Invoice  Creation#FD-Conf-MAS-PI-0047)|
|Different Transaction Series For Manual Purchase Invoice||If enabled, allow system to configure other than default transaction series on Manual PI|[FD-Conf-MAS-PI-0048](Purchase Invoice  Creation#FD-Conf-MAS-PI-0048)|
|Show Net PTR field in Purchase invoice||If enabled, display Net PTR field in Purchase invoice|[FD-Conf-MAS-PI-0049](Purchase Invoice  Creation#FD-Conf-MAS-PI-0049)|
|Enable Shipping to different party||If enabled, new column will be displayed to select party for PI transaction|[FD-Conf-MAS-PI-0050](Purchase Invoice  Creation#FD-Conf-MAS-PI-0050)|
|Invoice Level before Tax||If enable, tax compute before invoice level|[FD-Conf-MAS-PI-0051](Purchase Invoice  Creation#FD-Conf-MAS-PI-0051)|
|Generate alert message – if no tax is configured for the product||If enabled, alert message displayed if no tax is configured for the product on PI|[FD-Conf-MAS-PI-0052](Purchase Invoice  Creation#FD-Conf-MAS-PI-0052)|
|Generate alert message||Alert & Continue == alert and continue transaction|[FD-Conf-MAS-PI-0053](Purchase Invoice  Creation#FD-Conf-MAS-PI-0053)|
|Generate alert message||Alert & Stop == alert and stop transaction flow|[FD-Conf-MAS-PI-0054](Purchase Invoice  Creation#FD-Conf-MAS-PI-0054)|
|Allow manual entry/editing of price points during Purchase Invoice||If enabled, price points and editale on PI based on following config|[FD-Conf-MAS-PI-0055](Purchase Invoice  Creation#FD-Conf-MAS-PI-0055)|
|Recompute the PTR based on formula - if formula is configured for PTR Computation||If enabled, PTR is recopute on PI if configred with formula|[FD-Conf-MAS-PI-0056](Purchase Invoice  Creation#FD-Conf-MAS-PI-0056)|
|PTS editable in PI||If enabled, PTS editable in PI|[FD-Conf-MAS-PI-0057](Purchase Invoice  Creation#FD-Conf-MAS-PI-0057)|
|PTR editable in PI||If enabled, PTR editable in PI|[FD-Conf-MAS-PI-0058](Purchase Invoice  Creation#FD-Conf-MAS-PI-0058)|
|PFM editable in PI||If enabled, PFM editable in PI|[FD-Conf-MAS-PI-0059](Purchase Invoice  Creation#FD-Conf-MAS-PI-0059)|
|MRP Per Pack Editable in PI||If enabled, MRP Per Pack Editable in PI|[FD-Conf-MAS-PI-0060](Purchase Invoice  Creation#FD-Conf-MAS-PI-0060)|
|ECP editable in PI||If enabled, ECP editable in PI|[FD-Conf-MAS-PI-0061](Purchase Invoice  Creation#FD-Conf-MAS-PI-0061)|


# Business Rule & Impact 

> Business rules are listed in the below section which requires Domain understanding, hope the previous sections of the Purchase Invoice  are clear. Refer [Purchase Invoice  ](Purchase Invoice  ), [Purchase Invoice  Creation](#creation-of-sales-Invoice  )   

1. [FD-BR-SO-0001] - User access 

>  FD-BR-SO-0001

    1. Login user should has association with a Distributor. 
    1. In case of user associated with multiple user, then distributor selection is require before creating Purchase Invoice  transaction 
    1. User with profile access configurations are to be applied while Listing Purchase Invoice  , Create, Modify, View Purchase Invoice  

    > Refer User profile, Distributor User, Corporate User Distributor mapping 

2. [FD-BR-SO-0002](#FD-BR-SO-0002) - List view of Purchase Invoice  
    1. Listing page is default landing page, where newly created Purchase Invoice  are listed with selected information.
    1. All listing page related features are to be available for Purchase Invoice  listing Page. 
    1. Retrieve recently created top `20` Purchase Invoice  document with selected field where it belongs to a Distributor and sort with Invoice  date. Default filter for Purchase Invoice  applicable for all users. 
    1. Custom filter to be available for all modules
    1. Default list view fields for distributor users  
        - "transactionNumber" 
        - "Purchase Invoice  Date" 
        - "referencenumber" 
        - Vendor Name"
        - "Due date" 
        - "customername" 
        - "Bill to party code" 
        - "Distributor Shipping address,City,State,Pincode"
        - "Distributor Billing address,City,State,Pincode"

    > Refer [Listing page](Listing Page) functionalities, [Custom Filter](Custom Filter).

3. [FD-BR-SO-0003](FD-BR-SO-0003) - Detail view actions
    1. Detail view of Invoice  record enables you to perform actions like editing, cancel, amend, print the existing record in PDF format, all actions are configured through [Workflow](Workflow). 
    1. From the Invoice  s list view, select the desired record. Details view of Invoice  record should follow the Field access rule for the login user related profile. 

4. [FD-BR-SO-0004](FD-BR-SO-0004) - Create Purchase Invoice  
    1. Allow creation of Purchase Invoice  based on Profile access configuration. 
    1. User Distributor association is mandatory for creating transaction. 
    1. Corporate User are indirect users create transaction related to specific associated distributor. 
    1. Creation of Purchase Invoice  should be restricted to user without distributor association. 
   

## Rate calculation 
1. **Purchase Invoice  Price** is shown in any of the following ways.
    - Distributor Landing price value stored in Batch
    - Special price defined for the Dsitributor channel and GST registration status. 
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
| UOM                                  | Default Purchase UOM is selected initially. User can change if required by shortcut also or manually change it |
| Billing Price                      | DLP of the item is shown. DLP is considered based on the Margin or Channel Wise Margin or Quotation         |
| Net Rate                             | Sale Price of item + Tax Amount is calculated for 1 quantity and shown.                                     |
| Quantity                             | User can enter quantity. Quantity entered is considered as per UOM selected                                 |
| Amount                               | Quantity * Sale Price is calculated and shown                                                               |
| Discount%                            | Manual discount percentage                                                                                  |
| Discount Amount                      | Discount Amount is shown                                                                                    |
| Scheme Discount%                     | Scheme Discount % is shown. For Amount scheme also, Discount % is also calculated and shown                 |
| Scheme Amount                        | Scheme Amount is shown.  Even for % Scheme, Discount Amount is calculated and shown                         |
| Net Amount (Taxable)                 | Taxable net amount. Amount - (Scheme Amount + Discount Amount). Based on configuration this formula varies |
| Tax Amount (Tax Split up also shown) | Tax Amount calculated on Net Amount is calculated & Shown                                                   |
| Net Tax Amount                       | Tax amount deducted on proposition from Additional Discount given in Invoice  is shown here                  |
| Type                                 | Always Second Purchase                                                                                         |
| Total                                | Net Amount + Tax Amount is calculated & Shown                                                               |
| Scheme Discount (Invoice  Level)      | Invoice  level Scheme Discount is propositioned item level and shown                                         |
| Trade Discount (Invoice  Level)       | Invoice  level Trade Discount amount is proportioned item level and shown                                    |
| Net Amount                           | Total - (Trade Discount + Scheme Discount) is calculated and shown                                          |

  - Purchase Invoice  Price : Distributor Landing Price of the item
  - Net Rate : Sale Price of item + Tax Amount is calculated for 1 quantity and shown.
  - Amount : (Quantity * Sale Price)
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
  - Purchase Invoice  are applied with respective scheme as defined or applicable. 
  - Applicable scheme are based on various criteria's like Product, Product category, Customer, Customer Type, Channel Type, Distributor, Distributor Cluster, Geo hierarchy, Mode of payment, ..etc. Refer [Scheme master](Scheme) for types of scheme. 
  - Different types of Scheme applies, some of the most used Scheme Type as below, 
    - Item by Quantity
    - Item by Value
    - Item By Qty - Lines cut 
    - `SMJ Pending - Add Invoice  level scheme types`
  - Gross Amount : (Quantity * Sale Price)
  - Gross Amount with tax : (Quantity * Rate + Tax)
  - After Manual Discount : ((Quantity * Rate - line level Addl. Discount)
  - After Manual Discount with tax : ((Quantity * Rate - line level Addl. Discount+ Tax)
  - **On-Take Scheme** are applied while preparing the Purchase Invoice  . 
  - **Off-Take Scheme** benefits are applied as per the pending benefit list as applicable for the selected customer. 
  - Purchase Invoice  scheme benefits are [computed](Scheme engine) and applied.  
  
## Tax 
  - Tax Components can be
    - 1. State Tax
    - 2. Central Taxb y
    - 3. Inter-state Tax
    - 4. Cess
    - 5. Cess on Quantity
    - 6. Cess applicable for the particular state
  - Tax applicable for the product, related geo hierarchy of distributor, [State](State) of distributor, [State](State) of Customer, Tax identifier details of customer, Tax form applied for the customer.
  - Multiple Tax are applicable for an item based on tax definition. All relevant tax details with split-up percentage to be available in Purchase Invoice  document. 
  - Accurate calculation of tax amount is main criteria of Purchase Invoice  document.


# Event Flows 
## Events at Front End (Create)
  - Purchase Invoice  list view page 
    - Listing Purchase  Invoice 
  - While Creating Purchase  Invoice 
    - Render page based on user profile (To be explained in separate page) 
    - Listing Vendor
    - Listing Depot
    - Listing Customer
    - On Selection of Customer, retrieve relevant Customer Info, Customer address
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

  - User chooses the 'Purchase Invoice  Entry' menu item. 
  - User should choose the Vendor details 
  - System should pick the Default Distributor details 
  - User selects the Salesman associated with that distributor
  - System should pick the Billing Address and shipping address of the selected Distributor
  - System should check the Distributor-product-pricing group and retrieve these items as qualified items for creating an Purchase Invoice 
  - User enters the product id/product name and desired quantity in respective fields.
  - User clicks on [Add item] button to add the next item.
  - System adds the desired product in draft mode 
  - User applies the Promotion/Coupon code if available.
  - Being continued,user clicks on 'Save' Invoice link.
  - User can enters Credit term type description.
  - System will create Purchase Invoice  and update the total amount as Invoice  Amount
  - User clicks on 'Save' link and Purchase Invoice  will be created in 'Created/Publish' status.
  - User can select the 'Purchase Invoice ' and print the 'Purchase Invoice ' if required 

**Events based on Mobile Based Invoice **

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

**Events based on Direct Invoice **

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

- Purchase Invoice  Service scope limited to Purchase invoice creation/amendment/cancel/delete. 
- Purchase Invoice  Service to trigger the related sub services which are internal and separate service. 

 <!-- blank line -->
- Customer Open Invoice s  to get updated in Distributor Purchase Invoice  screen 
- Purchase Invoice  status to get updated depending on the number of Invoice s get fulfilled 

 <!-- blank line -->
- Mail triggers to Customer on Invoice  confirmation status
- SMS triggers to Customer on Invoice  confirmation status
- Report related Purchase Invoice  data to be updated through services. 

# See also .. 
  - [Purchase Invoice  ](Purchase Invoice  )
  - [Purchase Invoice  Configurations](Purchase Invoice  Configurations)
  - [Domain Object Purchase Invoice  ](Domain Object Purchase Invoice  )
  - [Home](Home)

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTIwMTYyMTkzMTNdfQ==
-->
