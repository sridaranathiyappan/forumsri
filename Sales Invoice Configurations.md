[[_TOC_]]

# Sales Invoice Configuration 
This page list all direct configuration applicable for Sales Invoice & related other module configuration which impacts Sales Invoice. 

> Other common configuration such as User profile based configuration, Field level configurations, Menu configurations are assumed to be as applicable similar to other modules in application. Refer [Common Application Configurations](Common Application Configurations) 

 
## Application level Configuration  

### Sales Invoice Module Configuration
| Configuration                                                                | Related Configuration | Details                                                                         | Ref #                                                     |
|------------------------------------------------------------------------------|-----------------------|---------------------------------------------------------------------------------|-----------------------------------------------------------|
|Add new item detail Converting SO to SI| |If enabled, new line item is allowed on so to si,If not, allow only line item from so to si|
|Disable Beat refresh post selecting customer in SO and SI Screen| |If enabled beat will not be re-loaded after customer selection,If not, beat will be re-loaded even after customer selection|
|Allow GSTIN Threshold Limit Validation| |If enabled, threshold limit is validation,If not, is not be considered for validation|
|How many invoices are allowed for unapproved customers| | Set limit count to allow invoice for unapproved customer,If not, invoice not allowed|
|Allow receive sales invoice is made against credit norms| |If enabled, days exceed againt credit norm invoice will be received,If not, days exceed againt credit norm invoice will not be received|
|Allow selection of Referral details if the sales invoice is made against end consumer| |If enabled, if the ref type is end consumer, will be allowed to select ref details., If not, field will be disabled|
|Allow invoice from unapproved customers in the status of| | Selected staus of invoice are allowed for the unapproved customer|
|SO & SI Custome Max Limit Cash Discount| |If enabled the limit of max discount is validated,If not, is not considered on validation|
|Within How Many Days Invoice Can Be Cancel| |Set limit days on invoice to be cancelled|
|Delivery date based on SI date / LR date| |Si date configuration will be based on salesinvoice date|
|Password for GSTIN Threshold Limit Violation| |Set password for violation on gstin threshold limit|
|Hide Scheme View button| |If enabled, scheme view button is diaabled,If not, button enabled|
|Suppress Apply Scheme Button in Sales Invoice| |If enabled, diaabled apply scheme button,If not, enabled button|
|Invoice Level discount on Per UOM| |If enabled discount is based on per uom to applicable.,If not, per uom is not applicable|
|Invoice print tracking| |If enabled, the print invoices are tracked based on type and user|
|Enable NetPTR capping| |If enabled, allow to edit net ptr|
|Enable PTR capping| |If enabled, allow to edit ptr|
|Get Fixed NetRate from the Base price & Special price settings| |If enabled, display the fixed rate price setting for the line item|
|Display out of stock SKUs in the sales invoice| |If enabled, out of stock sku are displayed,If not, sku is not displayed|
|Show Net Rate in Sales Invoice View| |If enabled net rated to be displayed on invoice view,,If not, not displayed|
|Enable Distwise Invoice Number| |If enabled the invoice number is updated based on datewise|
|Secondary transaction number required| |If enabled, consider the secondary transaction number|
|Select true for warning SI day close back dated configuration.| |If enabled, allow only create back dated transaction, display alert|
|Line Item Level discount on Per UOM| |If enable, line item discont is considered on per UOM|
|Net Amount Editable| |If enabled net amount field is editable|
|Net Rate Editable| |If enabled net rate field is editable|
|Payment Date based on SI date / Delivery date| | Si / deliver date config is to be configured as payment date|
|Apply manual discounts on the Original Amount(Quantity X Rate)| |If enabled the manual discount to be considerd on amount of quantity|
|Back dated limit| |Set limit to calcualte the back date from current date|
|Delete scheme free product| |If enabled the free product for the scheme are diabled|
|Enable option to issue free product manually| |If enabled the option to issue free product is available|
|Hide 'No Schemes to Apply' Message - if no schemes are applicable| |If enabled the msg is displayed if no scheme to apply|
|Hide Shipping & Handling Charges| |If enabled, field will not be shown on invoice screen|
|Add new item detail| |If enabled, allow to add new item details on invoice screen|
|ADHOC Discount for each item| |If enabled, discount is applied for each item on invoice|
|ADHOC Discount for transaction| |If enabled the discount is applicaable for transaction on final amount|
|ADHOC Scheme for transaction| |If enabled discount is applicable for final scheme transation details|
|Allow selection of vendor| |If enabled , vendor selection is allowed|
|Back dated transaction| |If enabled, allow the transaction back date as set Back dated limit|
|Billing Address Editable| |If enabled, the field is editabled on screen|
|Generate Product Category Group based credit norms violation alert in Sales Invoice| |If enabed, alert is displayed if the product category based on credit norms on invoice|
|Treat the selection of product category group as mandatory in sales invoice screen| |If enabled the filed is mandatoy on screen to be selected|
|Filter the Product based on Product Properties 1 & 2| |If enabled, the Product Properties 1 & 2 fields are displayed to file=ter the products on invoice screen|
|Allow Salesman credit Limit| |If enabled, allow the invoice based on salesman creditlimi on transaction|
|Allow selection of products based on category group attachment for Sales Invoice| |If enabled, allow only only product on categiry group to invoice transaction|
|Shipping Address Editable| |If enabled, allow the field as editable|
|Allow user to invoke customer creation screen from Sales Invoice Screen| |If enabled, allow user to create customer on invoice screen on transaction|
|Allow user to pop up Scrap Purchase Screen from Sales Invoice Screen| |If enabled, show the scrap purchase on invoice transaction screen|
|Show current stock for items| |If enabled show the current stock for items on the invoice screen|
|Back dated within the month| |If enabled, allow the transaction with in back dated duration of limit month|
|Sales Invoice Print Formats Display| |Display the sales invocie print format to be displayed option on invoice print screen|
|Sales Invoice Default print version| |Set the deffault print version to be handled on invoice print|
|Product Price Information Popup is Required| |If enabled, display the product price details on screen|
|Enable Save & Continue Option| |If enabled, display option to allow the user to save and continue transaction|
|Allow SO to SI editable price as list price| |If enabled allow the user to edit the price on item price details|
|Transaction Series Yearly Reset Alert| |If enabled, display the alert is the transaction series is on yearly details alert|
|Transaction Series Yearly Reset Date| |Configure the month on yearl to reset the series of transaction|
|Enable vehicle number configuration| |If enabled the vechicle number field will be displayed|
|In Sales Invoice/Van Sales Invoice/Counter Sales Invoice, Hide Location Type| |Location Type is to be displaye or hide on invoice screen|
|Apply Scheme Same as SO| |If enabled the scheme applied on so to be applied on si as same|
|Validate Partial tax in Sales Invoice while saving| |If enabled, validate the partial tax on invoince before save|
|Alert and stop the user if the edited list price is not between PTS and MRP| |If enabled the price is not between PTS and MRPas user entered will be stoped on transaction|
|Disable direct sales invoice creation| |If enabled direction creation of salesinvoice is restricted|
|Disable sales invoice draft creation| |If enabled sales invoice draft creation is restricted|
|Set the maximum discount % as while performing billing at MRP| |If enabled, Set percentage of discount on billing mrp invoice transaction|
|Additional Terms & Conditions| |If enabled display the addition info provide for terms and condition|
|Auto Adjust Credit Notes in Sales Invoice while saving| |If enabled, auto adjust is handled based on the request type of invoice (Offtake CR  Sales Return CR  Loyalty points CR  Manual CR  window display scheme CR)|
|Allow create implicit collection for Cash Payment mode| |If enabled, payment is cash mode, collection is created implicity|
|Show UOM based stock and price in batch list| |If enabled the uom stock and price is listed on batch list on transaction|
|Show UOM based MRP in batch list| |If enabled uom mrp details will be displayed on battch list details|
|Show Display status| |If enabled, the status of the invoice transaction is displayed on screen|
|Generate alert message – if no tax is configured for the product| |Set alert type as Alert & Continue == will display alert and continue transaction Alert & Stop == will display alert and stop transaction|
|Special Price Setting Round Off Enable| |If enabled, based on the round off range will be calculated SET Special Price Round Off Range|
|Don't allow sales invoice| |If enabled, based on the date provided the invoice transaction are restricted on the back dated date|


### Counter Sales Configuration
| Configuration                                                                | Related Configuration | Details                                                                         | Ref #                                                     |
|------------------------------------------------------------------------------|-----------------------|---------------------------------------------------------------------------------|-----------------------------------------------------------|
|Enable to provide Counter Sales Customer Information||If enabled, display customer info on transaction screen|
|Enable List Price Edit in Counter Sales Module||If enable, list price field is editable on invoice screen|
|Enable Net Rate Edit in Counter Sales Module||If enable, Net Rate field is editable on invoice screen|
|Enable Net Amount Edit in Counter Sales Module||If enable, Net Amount field is editable on invoice screen|	
|Alert and stop the user if edited list price is not between PTS and MRP||If enabled, if list price is not between PTS and MRP transaction will not be able to proceed|
|Enable option to issue free product manually – during counter sales||If enabled, allow product to issue free on invoice screen will be displayed|
|Alert the user if the TIN Number entered for the walk in customer is available against any of the customer||If enabled, and configured alert&continue == display alert and continue transaction alert&stop == display alert and stop transaction to proceed|
|Alert the user if the Mobile Number entered for the walk in customer is available against any of the customer||If enabled, and configured alert&continue == display alert and continue transaction alert&stop == display alert and stop transaction to proceed|
|Allow only Cash Payment mode for counter sales||If enabled, only cash payment mode will be applicable on counter sales|
|Disable Adjustment in Counter Sales||If enabled, current balance and adjust amount field will be displayed to proceed, amount adjustment on counter sales screen|

### SI Amendment Configuration
| Configuration                                                                | Related Configuration | Details                                                                         | Ref #                                                     |
|------------------------------------------------------------------------------|-----------------------|---------------------------------------------------------------------------------|-----------------------------------------------------------|
|Schemes has to consider for ||config enable based on invoice date,  sales invoice date will be considered for scheme applicable,config enable based on amend date,sales invoice amend date will be considered for scheme applicable|
|Tax has to consider for||config enable based on invoice date,  sales invoice date will be considered for Tax applicable,config enable based on amend date,sales invoice amend date will be considered for Tax applicable|
|Pricing has to consider for||config enable based on invoice date,  sales invoice date will be considered for Pricing applicable,config enable based on amend date,sales invoice amend date will be considered for Pricing applicable|
|Max no of times can amend||Set limit count for amending sales invoice, not to exceed count on amending sales invoice,If not sales invoice is not able to amendable|
|Within how many days invoice can be amendable||Set limit days for amending sales invoice on creation date,If not sales invoice is not able to amendable|
|Reason Mandatory for Amendment||Provide reason for amending sales invoice if enabledoptional if not enabled|
|Reason Mandatory for Cancellation||Provide reason for cancel sales invoice if enabled,optional if not enabled|
|Allow invoice amend based on||Sales invoice date creation with (first or last)|
	
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
