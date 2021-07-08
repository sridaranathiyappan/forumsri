[[_TOC_]]

# Sales Invoice Configuration 
This page list all direct configuration applicable for Sales Invoice & related other module configuration which impacts Sales Invoice. 

> Other common configuration such as User profile based configuration, Field level configurations, Menu configurations are assumed to be as applicable similar to other modules in application. Refer [Common Application Configurations](Common Application Configurations) 

 
## Application level Configuration  

### Sales Invoice Module Configuration
| Configuration                                                                | Related Configuration | Details                                                                         | Ref #                                                     |
|------------------------------------------------------------------------------|-----------------------|---------------------------------------------------------------------------------|-----------------------------------------------------------|
|Add new item detail Converting SO to SI| |If enabled, new line item is allowed on so to si,If not, allow only line item from so to si| [FD-Conf-MAS-SI-0001](Sales Invoice Creation#FD-Conf-MAS-SI-0001)|
|Disable Beat refresh post selecting customer in SO and SI Screen| |If enabled beat will not be re-loaded after customer selection,If not, beat will be re-loaded even after customer selection| [FD-Conf-MAS-SI-0002](Sales Invoice Creation#FD-Conf-MAS-SI-0002)|
|Allow GSTIN Threshold Limit Validation| |If enabled, threshold limit is validation,If not, is not be considered for validation| [FD-Conf-MAS-SI-0003](Sales Invoice Creation#FD-Conf-MAS-SI-0003)|
|How many invoices are allowed for unapproved customers| | Set limit count to allow invoice for unapproved customer,If not, invoice not allowed| [FD-Conf-MAS-SI-0004](Sales Invoice Creation#FD-Conf-MAS-SI-0004)|
|Allow receive sales invoice is made against credit norms| |If enabled, days exceed againt credit norm invoice will be received,If not, days exceed againt credit norm invoice will not be received| [FD-Conf-MAS-SI-0005](Sales Invoice Creation#FD-Conf-MAS-SI-0005)|
|Allow selection of Referral details if the sales invoice is made against end consumer| |If enabled, if the ref type is end consumer, will be allowed to select ref details., If not, field will be disabled| [FD-Conf-MAS-SI-0006](Sales Invoice Creation#FD-Conf-MAS-SI-0006)|
|Allow invoice from unapproved customers in the status of| | Selected staus of invoice are allowed for the unapproved customer| [FD-Conf-MAS-SI-0007](Sales Invoice Creation#FD-Conf-MAS-SI-0007)|
|SO & SI Custome Max Limit Cash Discount| |If enabled the limit of max discount is validated,If not, is not considered on validation| [FD-Conf-MAS-SI-0008](Sales Invoice Creation#FD-Conf-MAS-SI-0008)|
|Within How Many Days Invoice Can Be Cancel| |Set limit days on invoice to be cancelled| [FD-Conf-MAS-SI-0009](Sales Invoice Creation#FD-Conf-MAS-SI-0009)|
|Delivery date based on SI date / LR date| |Si date configuration will be based on salesinvoice date| [FD-Conf-MAS-SI-0010](Sales Invoice Creation#FD-Conf-MAS-SI-0010)|
|Password for GSTIN Threshold Limit Violation| |Set password for violation on gstin threshold limit| [FD-Conf-MAS-SI-0011](Sales Invoice Creation#FD-Conf-MAS-SI-0011)|
|Hide Scheme View button| |If enabled, scheme view button is diaabled,If not, button enabled| [FD-Conf-MAS-SI-0012](Sales Invoice Creation#FD-Conf-MAS-SI-0012)|
|Suppress Apply Scheme Button in Sales Invoice| |If enabled, diaabled apply scheme button,If not, enabled button| [FD-Conf-MAS-SI-0013](Sales Invoice Creation#FD-Conf-MAS-SI-0013)|
|Invoice Level discount on Per UOM| |If enabled discount is based on per uom to applicable.,If not, per uom is not applicable| [FD-Conf-MAS-SI-0014](Sales Invoice Creation#FD-Conf-MAS-SI-0014)|
|Invoice print tracking| |If enabled, the print invoices are tracked based on type and user| [FD-Conf-MAS-SI-0015](Sales Invoice Creation#FD-Conf-MAS-SI-0015)|
|Enable NetPTR capping| |If enabled, allow to edit net ptr| [FD-Conf-MAS-SI-0016](Sales Invoice Creation#FD-Conf-MAS-SI-0016)|
|Enable PTR capping| |If enabled, allow to edit ptr| [FD-Conf-MAS-SI-0017](Sales Invoice Creation#FD-Conf-MAS-SI-0017)|
|Get Fixed NetRate from the Base price & Special price settings| |If enabled, display the fixed rate price setting for the line item| [FD-Conf-MAS-SI-0018](Sales Invoice Creation#FD-Conf-MAS-SI-0018)|
|Display out of stock SKUs in the sales invoice| |If enabled, out of stock sku are displayed,If not, sku is not displayed| [FD-Conf-MAS-SI-0019](Sales Invoice Creation#FD-Conf-MAS-SI-0019)|
|Show Net Rate in Sales Invoice View| |If enabled net rated to be displayed on invoice view,,If not, not displayed| [FD-Conf-MAS-SI-0020](Sales Invoice Creation#FD-Conf-MAS-SI-0020)|
|Enable Distwise Invoice Number| |If enabled the invoice number is updated based on datewise| [FD-Conf-MAS-SI-0021](Sales Invoice Creation#FD-Conf-MAS-SI-0021)|
|Secondary transaction number required| |If enabled, consider the secondary transaction number| [FD-Conf-MAS-SI-0022](Sales Invoice Creation#FD-Conf-MAS-SI-0022)|
|Select true for warning SI day close back dated configuration.| |If enabled, allow only create back dated transaction, display alert| [FD-Conf-MAS-SI-0023](Sales Invoice Creation#FD-Conf-MAS-SI-0023)|
|Line Item Level discount on Per UOM| |If enable, line item discont is considered on per UOM| [FD-Conf-MAS-SI-0024](Sales Invoice Creation#FD-Conf-MAS-SI-0024)|
|Net Amount Editable| |If enabled net amount field is editable| [FD-Conf-MAS-SI-0025](Sales Invoice Creation#FD-Conf-MAS-SI-0025)|
|Net Rate Editable| |If enabled net rate field is editable| [FD-Conf-MAS-SI-0026](Sales Invoice Creation#FD-Conf-MAS-SI-0026)|
|Payment Date based on SI date / Delivery date| | Si / deliver date config is to be configured as payment date| [FD-Conf-MAS-SI-0027](Sales Invoice Creation#FD-Conf-MAS-SI-0027)|
|Apply manual discounts on the Original Amount(Quantity X Rate)| |If enabled the manual discount to be considerd on amount of quantity| [FD-Conf-MAS-SI-0028](Sales Invoice Creation#FD-Conf-MAS-SI-0028)|
|Back dated limit| |Set limit to calcualte the back date from current date| [FD-Conf-MAS-SI-0029](Sales Invoice Creation#FD-Conf-MAS-SI-0029)|
|Delete scheme free product| |If enabled the free product for the scheme are diabled| [FD-Conf-MAS-SI-0030](Sales Invoice Creation#FD-Conf-MAS-SI-0030)|
|Enable option to issue free product manually| |If enabled the option to issue free product is available| [FD-Conf-MAS-SI-0031](Sales Invoice Creation#FD-Conf-MAS-SI-0031)|
|Hide 'No Schemes to Apply' Message - if no schemes are applicable| |If enabled the msg is displayed if no scheme to apply| [FD-Conf-MAS-SI-0032](Sales Invoice Creation#FD-Conf-MAS-SI-0032)|
|Hide Shipping & Handling Charges| |If enabled, field will not be shown on invoice screen| [FD-Conf-MAS-SI-0033](Sales Invoice Creation#FD-Conf-MAS-SI-0033)|
|Add new item detail| |If enabled, allow to add new item details on invoice screen| [FD-Conf-MAS-SI-0034](Sales Invoice Creation#FD-Conf-MAS-SI-0034)|
|ADHOC Discount for each item| |If enabled, discount is applied for each item on invoice| [FD-Conf-MAS-SI-0035](Sales Invoice Creation#FD-Conf-MAS-SI-0035)|
|ADHOC Discount for transaction| |If enabled the discount is applicaable for transaction on final amount| [FD-Conf-MAS-SI-0036](Sales Invoice Creation#FD-Conf-MAS-SI-0036)|
|ADHOC Scheme for transaction| |If enabled discount is applicable for final scheme transation details| [FD-Conf-MAS-SI-0037](Sales Invoice Creation#FD-Conf-MAS-SI-0037)|
|Allow selection of vendor| |If enabled , vendor selection is allowed| [FD-Conf-MAS-SI-0038](Sales Invoice Creation#FD-Conf-MAS-SI-0038)|
|Back dated transaction| |If enabled, allow the transaction back date as set Back dated limit| [FD-Conf-MAS-SI-0039](Sales Invoice Creation#FD-Conf-MAS-SI-0039)|
|Billing Address Editable| |If enabled, the field is editabled on screen| [FD-Conf-MAS-SI-0040](Sales Invoice Creation#FD-Conf-MAS-SI-0040)|
|Generate Product Category Group based credit norms violation alert in Sales Invoice| |If enabed, alert is displayed if the product category based on credit norms on invoice| [FD-Conf-MAS-SI-0041](Sales Invoice Creation#FD-Conf-MAS-SI-0041)|
|Treat the selection of product category group as mandatory in sales invoice screen| |If enabled the filed is mandatoy on screen to be selected| [FD-Conf-MAS-SI-0042](Sales Invoice Creation#FD-Conf-MAS-SI-0042)|
|Filter the Product based on Product Properties 1 & 2| |If enabled, the Product Properties 1 & 2 fields are displayed to file=ter the products on invoice screen| [FD-Conf-MAS-SI-0043](Sales Invoice Creation#FD-Conf-MAS-SI-0043)|
|Allow Salesman credit Limit| |If enabled, allow the invoice based on salesman creditlimi on transaction| [FD-Conf-MAS-SI-0044](Sales Invoice Creation#FD-Conf-MAS-SI-0044)|
|Allow selection of products based on category group attachment for Sales Invoice| |If enabled, allow only only product on categiry group to invoice transaction| [FD-Conf-MAS-SI-0045](Sales Invoice Creation#FD-Conf-MAS-SI-0045)|
|Shipping Address Editable| |If enabled, allow the field as editable| [FD-Conf-MAS-SI-0046](Sales Invoice Creation#FD-Conf-MAS-SI-0046)|
|Allow user to invoke customer creation screen from Sales Invoice Screen| |If enabled, allow user to create customer on invoice screen on transaction| [FD-Conf-MAS-SI-0047](Sales Invoice Creation#FD-Conf-MAS-SI-0047)|
|Allow user to pop up Scrap Purchase Screen from Sales Invoice Screen| |If enabled, show the scrap purchase on invoice transaction screen| [FD-Conf-MAS-SI-0048](Sales Invoice Creation#FD-Conf-MAS-SI-0048)|
|Show current stock for items| |If enabled show the current stock for items on the invoice screen| [FD-Conf-MAS-SI-0049](Sales Invoice Creation#FD-Conf-MAS-SI-0049)|
|Back dated within the month| |If enabled, allow the transaction with in back dated duration of limit month| [FD-Conf-MAS-SI-0050](Sales Invoice Creation#FD-Conf-MAS-SI-0050)|
|Sales Invoice Print Formats Display| |Display the sales invocie print format to be displayed option on invoice print screen| [FD-Conf-MAS-SI-0051](Sales Invoice Creation#FD-Conf-MAS-SI-0051)|
|Sales Invoice Default print version| |Set the deffault print version to be handled on invoice print| [FD-Conf-MAS-SI-0052](Sales Invoice Creation#FD-Conf-MAS-SI-0052)|
|Product Price Information Popup is Required| |If enabled, display the product price details on screen| [FD-Conf-MAS-SI-0053](Sales Invoice Creation#FD-Conf-MAS-SI-0053)|
|Enable Save & Continue Option| |If enabled, display option to allow the user to save and continue transaction| [FD-Conf-MAS-SI-0054](Sales Invoice Creation#FD-Conf-MAS-SI-0054)|
|Allow SO to SI editable price as list price| |If enabled allow the user to edit the price on item price details| [FD-Conf-MAS-SI-0055](Sales Invoice Creation#FD-Conf-MAS-SI-0055)|
|Transaction Series Yearly Reset Alert| |If enabled, display the alert is the transaction series is on yearly details alert| [FD-Conf-MAS-SI-0056](Sales Invoice Creation#FD-Conf-MAS-SI-0056)|
|Transaction Series Yearly Reset Date| |Configure the month on yearl to reset the series of transaction| [FD-Conf-MAS-SI-0057](Sales Invoice Creation#FD-Conf-MAS-SI-0057)|
|Enable vehicle number configuration| |If enabled the vechicle number field will be displayed| [FD-Conf-MAS-SI-0058](Sales Invoice Creation#FD-Conf-MAS-SI-0058)|
|In Sales Invoice/Van Sales Invoice/Counter Sales Invoice, Hide Location Type| |Location Type is to be displaye or hide on invoice screen| [FD-Conf-MAS-SI-0059](Sales Invoice Creation#FD-Conf-MAS-SI-0059)|
|Apply Scheme Same as SO| |If enabled the scheme applied on so to be applied on si as same| [FD-Conf-MAS-SI-0060](Sales Invoice Creation#FD-Conf-MAS-SI-0060)|
|Validate Partial tax in Sales Invoice while saving| |If enabled, validate the partial tax on invoince before save| [FD-Conf-MAS-SI-0061](Sales Invoice Creation#FD-Conf-MAS-SI-0061)|
|Alert and stop the user if the edited list price is not between PTS and MRP| |If enabled the price is not between PTS and MRPas user entered will be stoped on transaction| [FD-Conf-MAS-SI-0062](Sales Invoice Creation#FD-Conf-MAS-SI-0062)|
|Disable direct sales invoice creation| |If enabled direction creation of salesinvoice is restricted| [FD-Conf-MAS-SI-0063](Sales Invoice Creation#FD-Conf-MAS-SI-0063)|
|Disable sales invoice draft creation| |If enabled sales invoice draft creation is restricted| [FD-Conf-MAS-SI-0064](Sales Invoice Creation#FD-Conf-MAS-SI-0064)|
|Set the maximum discount % as while performing billing at MRP| |If enabled, Set percentage of discount on billing mrp invoice transaction| [FD-Conf-MAS-SI-0065](Sales Invoice Creation#FD-Conf-MAS-SI-0065)|
|Additional Terms & Conditions| |If enabled display the addition info provide for terms and condition| [FD-Conf-MAS-SI-0066](Sales Invoice Creation#FD-Conf-MAS-SI-0066)|
|Auto Adjust Credit Notes in Sales Invoice while saving| |If enabled, auto adjust is handled based on the request type of invoice (Offtake CRSales Return CRLoyalty points CRManual CRwindow display scheme CR)| [FD-Conf-MAS-SI-0067](Sales Invoice Creation#FD-Conf-MAS-SI-0067)|
|Allow create implicit collection for Cash Payment mode| |If enabled, payment is cash mode, collection is created implicity| [FD-Conf-MAS-SI-0068](Sales Invoice Creation#FD-Conf-MAS-SI-0068)|
|Show UOM based stock and price in batch list| |If enabled the uom stock and price is listed on batch list on transaction| [FD-Conf-MAS-SI-0069](Sales Invoice Creation#FD-Conf-MAS-SI-0069)|
|Show UOM based MRP in batch list| |If enabled uom mrp details will be displayed on battch list details| [FD-Conf-MAS-SI-0070](Sales Invoice Creation#FD-Conf-MAS-SI-0070)|
|Show Display status| |If enabled, the status of the invoice transaction is displayed on screen| [FD-Conf-MAS-SI-0071](Sales Invoice Creation#FD-Conf-MAS-SI-0071)|
|Generate alert message – if no tax is configured for the product| |Set alert type as Alert & Continue == will display alert and continue transaction Alert & Stop == will display alert and stop transaction| [FD-Conf-MAS-SI-0072](Sales Invoice Creation#FD-Conf-MAS-SI-0072)|
|Special Price Setting Round Off Enable| |If enabled, based on the round off range will be calculated SET Special Price Round Off Range| [FD-Conf-MAS-SI-0073](Sales Invoice Creation#FD-Conf-MAS-SI-0073)|
|Don't allow sales invoice| |If enabled, based on the date provided the invoice transaction are restricted on the back dated date| [FD-Conf-MAS-SI-0074](Sales Invoice Creation#FD-Conf-MAS-SI-0074)|



### Counter Sales Configuration
| Configuration                                                                | Related Configuration | Details                                                                         | Ref #                                                     |
|------------------------------------------------------------------------------|-----------------------|---------------------------------------------------------------------------------|-----------------------------------------------------------|
|Enable to provide Counter Sales Customer Information||If enabled, display customer info on transaction screen|[FD-Conf-Countersale-SI-0001](Sales Invoice Creation#FD-Conf-Countersale-SI-0001)|
|Enable List Price Edit in Counter Sales Module||If enable, list price field is editable on invoice screen|[FD-Conf-Countersale-SI-0002](Sales Invoice Creation#FD-Conf-Countersale-SI-0002)|
|Enable Net Rate Edit in Counter Sales Module||If enable, Net Rate field is editable on invoice screen|[FD-Conf-Countersale-SI-0003](Sales Invoice Creation#FD-Conf-Countersale-SI-0003)|
|Enable Net Amount Edit in Counter Sales Module||If enable, Net Amount field is editable on invoice screen|[FD-Conf-Countersale-SI-0004](Sales Invoice Creation#FD-Conf-Countersale-SI-0004)|	
|Alert and stop the user if edited list price is not between PTS and MRP||If enabled, if list price is not between PTS and MRP transaction will not be able to proceed|[FD-Conf-Countersale-SI-0005](Sales Invoice Creation#FD-Conf-Countersale-SI-0005)|
|Enable option to issue free product manually – during counter sales||If enabled, allow product to issue free on invoice screen will be displayed|[FD-Conf-Countersale-SI-0006](Sales Invoice Creation#FD-Conf-Countersale-SI-0006)|
|Alert the user if the TIN Number entered for the walk in customer is available against any of the customer||If enabled, and configured alert&continue == display alert and continue transaction alert&stop == display alert and stop transaction to proceed|[FD-Conf-Countersale-SI-0007](Sales Invoice Creation#FD-Conf-Countersale-SI-0007)|
|Alert the user if the Mobile Number entered for the walk in customer is available against any of the customer||If enabled, and configured alert&continue == display alert and continue transaction alert&stop == display alert and stop transaction to proceed|[FD-Conf-Countersale-SI-0008](Sales Invoice Creation#FD-Conf-Countersale-SI-0008)|
|Allow only Cash Payment mode for counter sales||If enabled, only cash payment mode will be applicable on counter sales|[FD-Conf-Countersale-SI-0009](Sales Invoice Creation#FD-Conf-Countersale-SI-0009)|
|Disable Adjustment in Counter Sales||If enabled, current balance and adjust amount field will be displayed to proceed, amount adjustment on counter sales screen|[FD-Conf-Countersale-SI-0010](Sales Invoice Creation#FD-Conf-Countersale-SI-0010)|

### SI Amendment Configuration
| Configuration                                                                | Related Configuration | Details                                                                         | Ref #                                                     |
|------------------------------------------------------------------------------|-----------------------|---------------------------------------------------------------------------------|-----------------------------------------------------------|
|Schemes has to consider for ||config enable based on invoice date,  sales invoice date will be considered for scheme applicable,config enable based on amend date,sales invoice amend date will be considered for scheme applicable|[FD-Conf-SI-Amend-0001](Sales Invoice Creation#FD-Conf-SI-Amend-0001)|
|Tax has to consider for||config enable based on invoice date,  sales invoice date will be considered for Tax applicable,config enable based on amend date,sales invoice amend date will be considered for Tax applicable|[FD-Conf-SI-Amend-0002](Sales Invoice Creation#FD-Conf-SI-Amend-0002)|
|Pricing has to consider for||config enable based on invoice date,  sales invoice date will be considered for Pricing applicable,config enable based on amend date,sales invoice amend date will be considered for Pricing applicable|[FD-Conf-SI-Amend-0003](Sales Invoice Creation#FD-Conf-SI-Amend-0003)|
|Max no of times can amend||Set limit count for amending sales invoice, not to exceed count on amending sales invoice,If not sales invoice is not able to amendable|[FD-Conf-SI-Amend-0004](Sales Invoice Creation#FD-Conf-SI-Amend-0004)|
|Within how many days invoice can be amendable||Set limit days for amending sales invoice on creation date,If not sales invoice is not able to amendable|[FD-Conf-SI-Amend-0005](Sales Invoice Creation#FD-Conf-SI-Amend-0005)|
|Reason Mandatory for Amendment||Provide reason for amending sales invoice if enabledoptional if not enabled|[FD-Conf-SI-Amend-0006](Sales Invoice Creation#FD-Conf-SI-Amend-0006)|
|Reason Mandatory for Cancellation||Provide reason for cancel sales invoice if enabled,optional if not enabled|[FD-Conf-SI-Amend-0007](Sales Invoice Creation#FD-Conf-SI-Amend-0007)|
|Allow invoice amend based on||Sales invoice date creation with (first or last)|[FD-Conf-SI-Amend-0008](Sales Invoice Creation#FD-Conf-SI-Amend-0008)|
	
### Masters Configuration 
| Configuration                                                                | Related Configuration | Details                                                                         | Ref #                                                     |
|------------------------------------------------------------------------------|-----------------------|---------------------------------------------------------------------------------|-----------------------------------------------------------|
|Alert the user upon clicking on Cancel Button |  | This will alert user with additional popup for cancelling invoices | [FD-Conf-MAS-SI-0001](Sales Invoice Creation#FD-Conf-MAS-SI-0001) |
|Hide the following UOM in transactions |  | This will restrict the UOM's listing on transactions | [FD-Conf-MAS-SI-0002](Sales Invoice Creation#FD-Conf-MAS-SI-0002) |
|Restrict multiple beat mapping for Customer |  | This will restrict to map multiple beat to the customer | [FD-Conf-MAS-SI-0003](Sales Invoice Creation#FD-Conf-MAS-SI-0003) |
|Restrict multiple Salesman mapping for Beat |  | This will restrict to map multiple salesman  to the beat | [FD-Conf-MAS-SI-0004](Sales Invoice Creation#FD-Conf-MAS-SI-0004) |
|Do not allow cross classification Beat Mapping in Salesman & Retailer |  | This will override the Salesman profile selection | [FD-Conf-MAS-SI-0005](Sales Invoice Creation#FD-Conf-MAS-SI-0005) |
|Product with drug flag true are to be listed only for retailer with DL number in customer master |  | Already explained in Sales invoice Product selection | [FD-Conf-MAS-SI-0006](Sales Invoice Creation#FD-Conf-MAS-SI-0006) |
|Allow Send SMS To Customer |  | This will allow to send SMS to customers. | [FD-Conf-MAS-SI-0007](Sales Invoice Creation#FD-Conf-MAS-SI-0007) |
|Validate value level threshold |  | This will allow to validate value level threshold limit to the customer to make further invoices | [FD-Conf-MAS-SI-0008](Sales Invoice Creation#FD-Conf-MAS-SI-0008) |
|Password to allow retailer threshold limit |  | User can set the password to override the threshold validation. | [FD-Conf-MAS-SI-0009](Sales Invoice Creation#FD-Conf-MAS-SI-0009) |
|Action to be taken when "Validate value/volume level threshold" is enabled |  | This will allow for further action if customer reached configured threshold limit.  | [FD-Conf-MAS-SI-0010](Sales Invoice Creation#FD-Conf-MAS-SI-0010) |
|Validate volume level threshold |  | This will allow to validate volume  level threshold limit to the customer to make further invoices | [FD-Conf-MAS-SI-0011](Sales Invoice Creation#FD-Conf-MAS-SI-0011) |



### Customer Master
| Configuration                                                                | Related Configuration | Details                                                                         | Ref #                                                     |
|------------------------------------------------------------------------------|-----------------------|---------------------------------------------------------------------------------|-----------------------------------------------------------|
|Display customer in Transaction with status of  |  | This configuration will allow customers list in sales invoice based on status. | [FD-Conf-RET-0001](Sales Invoice Creation#FD-Conf-RET-0001) |
|Allow unapproved customer in all transactions. |  | This configuration will allow unapproved customers to create sales invoice with limited number of invoices. | [FD-Conf-RET-0002](Sales Invoice Creation#FD-Conf-RET-0002) |



### Salesman Master 
| Configuration                                                                | Related Configuration | Details                                                                         | Ref #                                                     |
|------------------------------------------------------------------------------|-----------------------|---------------------------------------------------------------------------------|-----------------------------------------------------------|
|Salesman classification and Salesman Profile mapping / approval |  | DSR, USR, RSR, VRSR, MER, RSP, -> Based on profile selection mobile integration module will enable and Beat mapping will allow to the users. | [FD-Conf-Salesperson-0009](Sales Invoice Creation#FD-Conf-Salesperson-0009) |



### Configuration by Distributor 
| Configuration                                                                | Related Configuration | Details                                                                         | Ref #                                                     |
|------------------------------------------------------------------------------|-----------------------|---------------------------------------------------------------------------------|-----------------------------------------------------------|
|Allow Invoice if Salesman level credit norm settings are violated |  | When this setting is ON then system allows to continue the sales invoice even if salesman exceeds the credit limit  like credit amount , days, no. of bills | [FD-Conf-SI-DP-0001](Sales Invoice Creation#FD-Conf-SI-DP-0001) |
|Option 1 - Seek password for billing for salesman level Credit Norm Violation | Allow Invoice if Salesman level credit norm settings are violated | Set password to seek while validation is violated. Password can be provided to authenticate the transaction post credit limit exceed.  | [FD-Conf-SI-DP-0002](Sales Invoice Creation#FD-Conf-SI-DP-0002) |
|Option 2 -Disable ALERT for billing for Salesman level Credit Norm Violation | Allow Invoice if Salesman level credit norm settings are violated | Disable pop-up for credit limit exceed validation.  | [FD-Conf-SI-DP-0003](Sales Invoice Creation#FD-Conf-SI-DP-0003) |
|Allow Invoice if Customer level credit norm settings are violated |  | When this setting is ON then system allows to continue the sales invoice even if customer exceeds the credit limit  like credit amount , days, no. of bills | [FD-Conf-SI-DP-0004](Sales Invoice Creation#FD-Conf-SI-DP-0004) |
|Option1 -Seek password for billing for customer level credit norm violation | Allow billing if customer level credit norm settings are violated | Set password to seek while validation is violated. Password can be provided to authenticate the transaction post credit limit exceed | [FD-Conf-SI-DP-0005](Sales Invoice Creation#FD-Conf-SI-DP-0005) |
|Option 2 -Disable ALERT for billing for Customer level Credit Norm Violation | Allow billing if customer level credit norm settings are violated | Disable pop-up for customer credit limit exceed | [FD-Conf-SI-DP-0006](Sales Invoice Creation#FD-Conf-SI-DP-0006) |
|Seek password for Sales Invoice Amendment configuration |  | Password can be set for invoice amendment save | [FD-Conf-SI-DP-0007](Sales Invoice Creation#FD-Conf-SI-DP-0007) |
|Seek password for Sales Invoice cancellation configuration |  | Password can be set for invoice cancellation save | [FD-Conf-SI-DP-0008](Sales Invoice Creation#FD-Conf-SI-DP-0008) |
|Ask for password to authenticate the approver |  | Seek password during any approval of Sales Invoice transaction | [FD-Conf-SI-DP-0009](Sales Invoice Creation#FD-Conf-SI-DP-0009) |



### Round- off Configuration
| Configuration                                                                | Related Configuration | Details                                                                         | Ref #                                                     |
|------------------------------------------------------------------------------|-----------------------|---------------------------------------------------------------------------------|-----------------------------------------------------------|
|Quantity: Align to decimals  |  | Apply the decimal rule in all quantity field of application | [FD-Conf-Decimal-DP-0001](Sales Invoice Creation#FD-Conf-Decimal-DP-0001) |
|Amount: Align to decimals  |  | Apply the decimal rule in all value/amount field of application | [FD-Conf-Decimal-DP-0002](Sales Invoice Creation#FD-Conf-Decimal-DP-0002) |
|Print Quantity: Align to decimals  |  | Apply the decimal rule in all quantity field of application print | [FD-Conf-Decimal-DP-0003](Sales Invoice Creation#FD-Conf-Decimal-DP-0003) |
|Print Amount: Align to decimals  |  | Apply the decimal rule in all value/amount field of application print | [FD-Conf-Decimal-DP-0004](Sales Invoice Creation#FD-Conf-Decimal-DP-0004) |
|Allow Decimal Quantity Transaction for SO and SI (Base UOM)  |  | Apply the decimal rule in base UOM quantity field of SI & SO (Base UOM) | [FD-Conf-Decimal-DP-0005](Sales Invoice Creation#FD-Conf-Decimal-DP-0005) |
|Allow Decimal Quantity Transaction for SO, SI and SR (All UOM)  |  | Apply the decimal rule in quantity field of SI, SR & SO (All UOM) | [FD-Conf-Decimal-DP-0006](Sales Invoice Creation#FD-Conf-Decimal-DP-0006) |



### Round- off Configuration by Distributor
| Configuration                                                                | Related Configuration | Details                                                                         | Ref #                                                     |
|------------------------------------------------------------------------------|-----------------------|---------------------------------------------------------------------------------|-----------------------------------------------------------|
|Quantity: Align to decimals  |  | Apply the decimal rule in all quantity field of application | [FD-Conf-Decimal-0001](Sales Invoice Creation#FD-Conf-Decimal-0001) |
|Amount: Align to decimals  |  | Apply the decimal rule in all value/amount field of application | [FD-Conf-Decimal-0001](Sales Invoice Creation#FD-Conf-Decimal-0001) |
|Print Quantity: Align to decimals  |  | Apply the decimal rule in all quantity field of application print | [FD-Conf-Decimal-0001](Sales Invoice Creation#FD-Conf-Decimal-0001) |
|Print Amount: Align to decimals  |  | Apply the decimal rule in all value/amount field of application print | [FD-Conf-Decimal-0001](Sales Invoice Creation#FD-Conf-Decimal-0001) |
|Allow Decimal Quantity Transaction for SO and SI (Base UOM)  |  | Apply the decimal rule in base UOM quantity field of SI & SO (Base UOM) | [FD-Conf-Decimal-0001](Sales Invoice Creation#FD-Conf-Decimal-0001) |
|Allow Decimal Quantity Transaction for SO, SI and SR (All UOM)  |  | Apply the decimal rule in quantity field of SI, SR & SO (All UOM) | [FD-Conf-Decimal-0001](Sales Invoice Creation#FD-Conf-Decimal-0001) |



# See also .. 
  - [Sales Invoice](Sales Invoice) 
  - [Sales Invoice Creation](Sales Invoice Creation) 
  - [Domain Object Sales Invoice](Domain Object Sales Invoice)
  - [Home](Home)

<!--stackedit_data:
eyJoaXN0b3J5IjpbNTM1MjUzMDA3XX0=
-->

