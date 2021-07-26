Content

[[_TOC_]]

`Available for review`
# Creation of Purchase Order
A Purchase Order is a demand that has get created by the distributer to the Manfacturer based on the secondary order received from the Retailers , It will get created by distributor operator through distributor portal at distributor location.  

## Precondition for creating Purchase Order 
Before creating a direct Purchase Order , you need to 
* Create [Vendor](Vendor) details 
* Create [Customer](Customer) details 
* Create [Salesman](Salesman) details 
* Create [Item](Product) details 
* Create [Pricing](Pricing) details 
* Create [Scheme](Scheme) details 
* Create [Tax](Tax) details 

Creation of Purchase Order vary based on type of creation. 

## To Create Purchase Order 

1. **Purchase Order Date** is often set to default current date
   - There are options to allow backdated Order but date after present date are restricted. 

2. **In the Vendor field**, enter the name of an existing Vendor
   - Purchase Order are created to document the Primary Order to the Supplier 
   - After Vendor selection, Other related information to be filed in below,  
     - default [Salesman](Salesman), 
     - default [Customer](Customer), 
     - default [Company Salesman](Company Salesman),   
     - default [Distributor Shipping address,,City,State,Pincode](Distributor) & 
     - default [Distributor Billing address,City,State,Pincode](Distributor) are loaded.

> Further, these details are allowed to be modified as necessary.  

3. **Select a [Salesman](Salesman)** related to the selected Customer 
    - Multiple Salesman are listed based on the Customer associated with multiple Beat. 

4. **[Transaction Series](Transaction Series)**
    - default Purchase Order Transaction Series are loaded, User can change these details as necessary. 

5. **Customer Shipping address** 
    - default Shipping address loaded, User can change these details as necessary. 

6. **Customer Billing address** 
    - default Billing address loaded, User can change these details as necessary. 

7. Fill in or Modify the remaining fields on the Purchase Order page as necessary.
    - Remark 
    - Reason  

> _These are the header details requires for creation of any Purchase Order ._
> _You are now ready to fill in the Purchase Order lines for products that you are selling to the Customer._

## Addition of line level details
8. **Select a [Product](Product)** from list of eligible product for sales. 
    - After selection of line level [Product](Product), related information are pre-populated  
      - Batch details from current stock of [Distributor](Distributor)
      - Price to customer [PTR](#rate-calculation)
      - [Available Stock Quantity](Stock & Inventory) 
      - Purchase [UOM](Unit of Measurement) 
      - [Applicable Tax](#rate-calculation) 

9. **Provide the Purchase order quantity**
    - After providing the Purchase order quantity, 
      - The value in the Line Amount field is calculated as Unit Price x Quantity. 
      - [Applies Tax](#tax) based on predefined [Tax Master](Tax Master) settings
      - Line level [Net Amount](Purchase Order Calculation) is calculated. 

10. **Net amount** is computed 
    - _refer [Purchase Order calculation logic](#rate-calculation)_

11. _Repeat **Addition of line level details** Step for adding more lines of item._ 

## Cancellation 
Cancellation of Purchase Order are action performed. The reason may vary like "Wrongly created Purchase Order ". Cancelled Order are considered as valid document and used in all reports

Cancellation of Purchase Order are restricted based on configuration & workflow, few points as below. 

  - Business level restriction may vary based on configuration.  
    - Posted Purchase Order are not allowed to cancel, Instead Purchase return can be used to manage the cancellation and maintain the logical accounting transactions. 

  - Data integrity related restrictions
    - Validation fails if the Distributor order amount update creates zero value scenario due to Zero price exist in the system against any line item. 
    - Deactivated master reference like product, distributor . will have impact to fail the cancellations. 

On Cancel of Purchase Order document, 
  - Document marked for status change to indicate cancellation. 
  - Report related Purchase order data to be recomputed. 

## Amendment 
Amendment to Purchase Order are corrections to the prepared Purchase Order . 
Amendment is not editing in record, the amended document is referred as valid document with status amended. 

Amendment performs validation and two primary actions as below, 
  - Cancel the old document of Purchase Order by executing all cancellation action as mentioned in [Purchase Order cancellation section](#cancellation) 

  - Amendment of Purchase Order are restricted to Business level restriction & Data integrity related restriction as mentioned in [cancellation](#cancellation) section. 

  - Further, Modification of key parameters are not allowed like vendor

  - A new Purchase Order created with Purchase Order transaction number of old document. all action performed during Purchase Order save are applicable for the newly created Purchase Order document. 

# Purchase Order Configuration 
This page list all direct configuration applicable for Purchase Order & related other module configuration  

> Other common configuration such as User profile based configuration, Field level configurations, Menu configurations are assumed to be as applicable similar to other modules in application. Refer [Common Application Configurations](Common Application Configurations) 
 
## Application level Configuration  

### Purchase Order Module Configuration
| Configuration                                                                | Related Configuration | Details                                                                         | Ref #                                                     |
|------------------------------------------------------------------------------|-----------------------|---------------------------------------------------------------------------------|-----------------------------------------------------------|
|Populate suggested order quantity when selecting the products manually – for manual PO||If enabled, on PO line item suggest the product order with quantity on selection|[FD-Conf-MAS-PO-0001](Purchase Order Creation#FD-Conf-MAS-PO-0001)|
|Allow Selection of Vendor||If enabled, allow user to select vendor on PO. If not, default vendor will be loaded and restrict selection|[FD-Conf-MAS-PO-0002](Purchase Order Creation#FD-Conf-MAS-PO-0002)|
|is Back Dated Transaction allowed||If enabled allow backdated for transaction|[FD-Conf-MAS-PO-0003](Purchase Order Creation#FD-Conf-MAS-PO-0003)|
|Update Referece Number with Transaction Number||If enabled, reference number is update with transaction number based on series selection on PO screen|[FD-Conf-MAS-PO-0004](Purchase Order Creation#FD-Conf-MAS-PO-0004)|
|Currency Option Enable||If enabled, Currency  column will be loaded on PO item screen|[FD-Conf-MAS-PO-0005](Purchase Order Creation#FD-Conf-MAS-PO-0005)|
|Display Value related fields in the screen||If enabled, display price details column in item details,If not, price details column will be disabled|[FD-Conf-MAS-PO-0006](Purchase Order Creation#FD-Conf-MAS-PO-0006)|
|Alert the user on pending POs if the order is pending for days||Set limit duration days to alert user for pending order|[FD-Conf-MAS-PO-0007](Purchase Order Creation#FD-Conf-MAS-PO-0007)|
|Automatically approve the pending PO days||Set limit days to approve the po as config with duration days|[FD-Conf-MAS-PO-0008](Purchase Order Creation#FD-Conf-MAS-PO-0008)|
|Enable credit limit alert in Purchase Order Screen||If enabled, display alert based on credit limit on PO transaction|[FD-Conf-MAS-PO-0009](Purchase Order Creation#FD-Conf-MAS-PO-0009)|
|Billing Address Editable||If enabled, allow to edit billing address on PO|[FD-Conf-MAS-PO-0010](Purchase Order Creation#FD-Conf-MAS-PO-0010)|
|Shipping Address Editable||If enabled allow to edit shipping address on PO||[FD-Conf-MAS-PO-0010](Purchase Order Creation#FD-Conf-MAS-PO-0010)|
|Display Discount fields in the screen||If enabled, discount field will be available on PO screen|[FD-Conf-MAS-PO-0011](Purchase Order Creation#FD-Conf-MAS-PO-0011)|
|Display Tax field in the screen||If enabled tax column will be displayed on PO screen|[FD-Conf-MAS-PO-0012](Purchase Order Creation#FD-Conf-MAS-PO-0012)|
|Allow Selection of Depot||If enabled, depot is available for selection|[FD-Conf-MAS-PO-0013](Purchase Order Creation#FD-Conf-MAS-PO-0013)|
|Enable Generate Suggested Order||If enabled, Generate Suggested Order icon will be displayed on PO screen|[FD-Conf-MAS-PO-0014](Purchase Order Creation#FD-Conf-MAS-PO-0014)|
|UOM non editable||If enabled, uom column will be non editable|[FD-Conf-MAS-PO-0015](Purchase Order Creation#FD-Conf-MAS-PO-0015)|
|Achieve minimum stock capacity with addition of RO level and Lot size||If enabled, user is not able change the quantity based on min and max to item|[FD-Conf-MAS-PO-0016](Purchase Order Creation#FD-Conf-MAS-PO-0016)|
|Send Single Acknowledgement mail from multiple SO per one PO||If enabled, send single mail acknowledge SO per PO|[FD-Conf-MAS-PO-0017](Purchase Order Creation#FD-Conf-MAS-PO-0017)|
|Enable auto PO Hierarchy Mail||If enabled, Trigger auto mail for PO transaction on hierarchy mail|[FD-Conf-MAS-PO-0018](Purchase Order Creation#FD-Conf-MAS-PO-0018)|
|Enable auto PO Depot Mail||If enabled, trigger auto mail on PO depot mail|[FD-Conf-MAS-PO-0019](Purchase Order Creation#FD-Conf-MAS-PO-0019)|
|Enable option to view DP Purchase Order Dashboard||If enabled, DP dashboard PO will be visible|[FD-Conf-MAS-PO-0020](Purchase Order Creation#FD-Conf-MAS-PO-0020)|
|Alert the user if total Order Quantity is less than MOQ - During PO CreationIf enabled, display alert . Alert & Continue == Display alert and continue process,Alert & Stop == Display alert and restrict continue process|[FD-Conf-MAS-PO-0021](Purchase Order Creation#FD-Conf-MAS-PO-0021)|
|Rules for PO Editing in DP|Allow editing of PO quantity when suggested order quantity is populated|If enabled, allow po quantity editable based on listed config|[FD-Conf-MAS-PO-0022](Purchase Order Creation#FD-Conf-MAS-PO-0022)|
|Rules for PO Editing in DP|Allow editing of PO quantity only if products are linked to properties|Set product property config for po product quantity editable|[FD-Conf-MAS-PO-0023](Purchase Order Creation#FD-Conf-MAS-PO-0023)|
|Restrict reduction of purchase order quantity than suggested order quantity while editing||If enabled, restrict reduction of po quantity than order quantity suggested|[FD-Conf-MAS-PO-0024](Purchase Order Creation#FD-Conf-MAS-PO-0024)|
|Allow Addition of new products to suggested order||If enabled, allow to add new product on PO suggest order|[FD-Conf-MAS-PO-0025](Purchase Order Creation#FD-Conf-MAS-PO-0025)|
|Allow Removal of products from suggested order||If enabled allow removal product on suggest order|[FD-Conf-MAS-PO-0026](Purchase Order Creation#FD-Conf-MAS-PO-0026)|
|Rules for Closing the PO|Close the PO once a Purchase Invoice / GRN is raised against the order|If enabled, close PO once a Purchase Invoice / GRN is raised against|[FD-Conf-MAS-PO-0027](Purchase Order Creation#FD-Conf-MAS-PO-0027)|
|Rules for Closing the PO|Close the PO only when all the products are invoiced in partial|If enabled, close the PO only when all the products are invoiced in partial|[FD-Conf-MAS-PO-0028](Purchase Order Creation#FD-Conf-MAS-PO-0028)|
|Rules for Closing the PO|Close the PO only when all the products are invoiced in full|If enabled, close the PO only when all the products are invoiced in full|[FD-Conf-MAS-PO-0029](Purchase Order Creation#FD-Conf-MAS-PO-0029)|
|Rules for Closing the PO|Close the PO If not approved by same day midnight|If enabled, close the PO If not approved by same day midnight|[FD-Conf-MAS-PO-0030](Purchase Order Creation#FD-Conf-MAS-PO-0030)|
|Approval Rule Settings in CP|Seek Approval for PO if the Ordered products are linked to properties|If enabled, set product property for PO approval|[FD-Conf-MAS-PO-0031](Purchase Order Creation#FD-Conf-MAS-PO-0031)|
|Approval Rule Settings in CP|Allow editing of PO quantity only if products are linked to properties|If enabled, set product property for editing of PO quantity|[FD-Conf-MAS-PO-0032](Purchase Order Creation#FD-Conf-MAS-PO-0032)|
|Approval Rule Settings in CP|Allow Addition of new products to suggested order|If enabled allow add new product on PO suggest order|[FD-Conf-MAS-PO-0033](Purchase Order Creation#FD-Conf-MAS-PO-0033)|
|Approval Rule Settings in CP|Allow Removal of products from suggested order|If enabled allow remove product on PO suggest order|[FD-Conf-MAS-PO-0034](Purchase Order Creation#FD-Conf-MAS-PO-0034)|
|Suggested Order Calculation Logic|Populate Suggested order based on Total Salable Stock (Excluding Van Stock)|If enabled, Populate Suggested order based on Total Salable Stock (Excluding Van Stock)|[FD-Conf-MAS-PO-0035](Purchase Order Creation#FD-Conf-MAS-PO-0035)|
|Suggested Order Calculation Logic|Populate Suggested order based on Total Salable Stock (Excluding Van Stock) - Stock In transit - Pending Order |If enabled, Suggested order based on Total Salable Stock (Excluding Van Stock) - Stock In transit|[FD-Conf-MAS-PO-0036](Purchase Order Creation#FD-Conf-MAS-PO-0036)|
|Suggested Order Calculation Logic|Populate Suggested order based on Total Salable Stock (Excluding Van Stock) - Stock In transit|If enabled, Suggested order based on Total Salable Stock (Excluding Van Stock) - Stock In transit|[FD-Conf-MAS-PO-0037](Purchase Order Creation#FD-Conf-MAS-PO-0037)|
|Suggested Order Calculation Logic|Populate Suggested order based on Total Salable Stock (Excluding Van Stock) - Pending Order|If enabled, Suggested order based on Total Salable Stock (Excluding Van Stock)|[FD-Conf-MAS-PO-0038](Purchase Order Creation#FD-Conf-MAS-PO-0038)|

# Business Rule & Impact 

> Business rules are listed in the below section which requires Domain understanding, hope the previous sections of the Purchase Order are clear. Refer [Purchase Order ](Purchase Order ), [Purchase Order Creation](#creation-of-sales-Order )   

1. [FD-BR-SO-0001] - User access 

>  FD-BR-SO-0001

    1. Login user should has association with a Distributor. 
    1. In case of user associated with multiple user, then distributor selection is require before creating Purchase Order transaction 
    1. User with profile access configurations are to be applied while Listing Purchase Order , Create, Modify, View Purchase Order 

    > Refer User profile, Distributor User, Corporate User Distributor mapping 

2. [FD-BR-SO-0002](#FD-BR-SO-0002) - List view of Purchase Order 
    1. Listing page is default landing page, where newly created Purchase Order are listed with selected information.
    1. All listing page related features are to be available for Purchase Order listing Page. 
    1. Retrieve recently created top `20` Purchase Order document with selected field where it belongs to a Distributor and sort with Order date. Default filter for Purchase Order applicable for all users. 
    1. Custom filter to be available for all modules
    1. Default list view fields for distributor users  
        - "transactionNumber" 
        - "Purchase Order Date" 
        - "referencenumber" 
        - Vendor Name"
        - "Due date" 
        - "customername" 
        - "company salesmanName" 
        - "Bill to party code" 
        - "Distributor Shipping address,City,State,Pincode"
        - "Distributor Billing address,City,State,Pincode"

    > Refer [Listing page](Listing Page) functionalities, [Custom Filter](Custom Filter).

3. [FD-BR-SO-0003](FD-BR-SO-0003) - Detail view actions
    1. Detail view of Order record enables you to perform actions like editing, cancel, amend, print the existing record in PDF format, all actions are configured through [Workflow](Workflow). 
    1. From the Order s list view, select the desired record. Details view of Order record should follow the Field access rule for the login user related profile. 

4. [FD-BR-SO-0004](FD-BR-SO-0004) - Create Purchase Order 
    1. Allow creation of Purchase Order based on Profile access configuration. 
    1. User Distributor association is mandatory for creating transaction. 
    1. Corporate User are indirect users create transaction related to specific associated distributor. 
    1. Creation of Purchase Order should be restricted to user without distributor association. 
   

## Rate calculation 
1. **Purchase Order Price** is shown in any of the following ways.
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
| Purchase Order Price          | DLP of the item is shown. DLP is considered based on the Margin or Channel Wise Margin or Quotation         |
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
| Type                                 | Always Second Purchase                                                                                         |
| Total                                | Net Amount + Tax Amount is calculated & Shown                                                               |
| Scheme Discount (Order Level)      | Order level Scheme Discount is propositioned item level and shown                                         |
| Trade Discount (Order Level)       | Order level Trade Discount amount is proportioned item level and shown                                    |
| Net Amount                           | Total - (Trade Discount + Scheme Discount) is calculated and shown                                          |

  - Purchase Order Price : Distributor Landing Price of the item
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
  - Purchase Order are applied with respective scheme as defined or applicable. 
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
  - **On-Take Scheme** are applied while preparing the Purchase Order . 
  - **Off-Take Scheme** benefits are applied as per the pending benefit list as applicable for the selected customer. 
  - Purchase Order scheme benefits are [computed](Scheme engine) and applied.  
  
## Tax 
  - Tax Components can be
    - 1. State Tax
    - 2. Central Taxb y
    - 3. Inter-state Tax
    - 4. Cess
    - 5. Cess on Quantity
    - 6. Cess applicable for the particular state
  - Tax applicable for the product, related geo hierarchy of distributor, [State](State) of distributor, [State](State) of Customer, Tax identifier details of customer, Tax form applied for the customer.
  - Multiple Tax are applicable for an item based on tax definition. All relevant tax details with split-up percentage to be available in Purchase Order document. 
  - Accurate calculation of tax amount is main criteria of Purchase Order document.


# Event Flows 
## Events at Front End (Create)
  - Purchase Order list view page 
    - Listing Purchase  Order
  - While Creating Purchase  Order
    - Render page based on user profile (To be explained in separate page) 
    - Listing Salesman
    - On Selection of Salesman, Retrieve Salesman Category info, Filter related Beat, Filter related customer.
    - Listing Customer
    - On Selection of Customer, retrieveCustomer Info, Customer address
    - Listing Transaction Series for Purchase Order
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

  - User chooses the 'Purchase Order Entry' menu item. 
  - User should choose the Vendor details 
  - System should pick the Default Distributor details 
  - User selects the Salesman associated with that distributor
  - System should pick the Billing Address and shipping address of the selected Distributor
  - System should check the Distributor-product-pricing group and retrieve these items as qualified items for creating an Purchase Order
  - User enters the product id/product name and desired quantity in respective fields.
  - User clicks on [Add item] button to add the next item.
  - System adds the desired product in draft mode 
  - User applies the Promotion/Coupon code if available.
  - Being continued,user clicks on 'Save' Invoice link.
  - User can enters Credit term type description.
  - System will create Purchase Order and update the total amount as Order Amount
  - User clicks on 'Save' link and Purchase Order will be created in 'Created/Publish' status.
  - User can select the 'Purchase Order' and print the 'Purchase Order' if required 

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

- Purchase Order Service scope limited to Purchase invoice creation/amendment/cancel/delete. 
- Purchase Order Service to trigger the related sub services which are internal and separate service. 

 <!-- blank line -->
- Customer Open orders  to get updated in Distributor Purchase order screen 
- Purchase Order status to get updated depending on the number of orders get fulfilled 

 <!-- blank line -->
- Mail triggers to Customer on order confirmation status
- SMS triggers to Customer on order confirmation status
- Report related Purchase order data to be updated through services. 

# See also .. 
  - [Purchase Order ](Purchase Order )
  - [Purchase Order Configurations](Purchase Order Configurations)
  - [Domain Object Purchase Order ](Domain Object Purchase Order )
  - [Home](Home)

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTIwMTYyMTkzMTNdfQ==
-->
