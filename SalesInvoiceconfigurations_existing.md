[[_TOC_]]

# Sales Invoice Configuration 
This page list all direct configuration applicable for Sales Invoice & related other module configuration which impacts Sales Invoice. 

> Other common configuration such as User profile based configuration, Field level configurations, Menu configurations are assumed to be as applicable similar to other modules in application. Refer [Common Application Configurations](Common Application Configurations) 

 
## Application level Configuration  

### Sales Invoice Module Configuration
| Configuration                                                                | Related Configuration | Details                                                                         | Ref #                                                     |
|------------------------------------------------------------------------------|-----------------------|---------------------------------------------------------------------------------|-----------------------------------------------------------|
| Disable creation of direct sales invoice by disabling "Create Sales Invoice" button.  |  | Set to "True" to disable creation of Sales invoice, by default allow to create sales invoice without any other transaction reference | [FD-Conf-SI-0001](Sales Invoice Creation#FD-Conf-SI-0001) |
| Disable "Draft" button during Sales invoice creation |  | Set to "True" to disable Sales invoice creation as draft stage by use, by default  sales invoice creations are allowed.  | [FD-Conf-SI-0002](Sales Invoice Creation#FD-Conf-SI-0002) |
| Number of days allowed to cancel after creation of Invoice.  |  | Invoice is allowed to cancel based on number of days set in this configuration. By default 0, any value greater than 0 only applies the rule.   | [FD-Conf-SI-0003](Sales Invoice Creation#FD-Conf-SI-0003) |
| Allow user to invoke Customer creation screen from Sales Invoice Screen.  |  | Create Customer button shown in Sales Invoice when this setting is TRUE | [FD-Conf-SI-0004](Sales Invoice Creation#FD-Conf-SI-0004) |
| In Sales Invoice/Van Sales Invoice/Counter Sales Invoice, Hide Location Type |  | Set this configuration to "True" to hide location type in Sales invoice screen.  | [FD-Conf-SI-0005](Sales Invoice Creation#FD-Conf-SI-0005) |
| Disable "Apply Scheme" Button in Sales Invoice |  | Set "True" to disable "Apply Scheme" button, by default "False".  | [FD-Conf-SI-0006](Sales Invoice Creation#FD-Conf-SI-0006) |
| Allow Sales invoice creation for unapproved Customers in the status of [Select Status] |  | This will allow to set the status of unapproved Customer to include in listing & allowing to create Sales invoice. Empty By default | [FD-Conf-SI-0007](Sales Invoice Creation#FD-Conf-SI-0007) |
| How many invoices are allowed for unapproved Customers | Allow Sales invoice creation for unapproved Customers in the status of [Select Status] | Set to configure the number of count of Invoices that to be allowed for unapproved Customer. | [FD-Conf-SI-0008](Sales Invoice Creation#FD-Conf-SI-0008) |
| Allow Editable Billing Address  |  | Set "True" to allow modifying Customer billing address in Sales Invoice, by default "True".  | [FD-Conf-SI-0009](Sales Invoice Creation#FD-Conf-SI-0009) |
| Don't allow Sales Invoice greater than this selected date  |  | The system will not allow to select the date greater than date configured in this field. | [FD-Conf-SI-0010](Sales Invoice Creation#FD-Conf-SI-0010) |
| Back dated transaction |  | Set "True" to allow back dated Sales Invoice transactions | [FD-Conf-SI-0011](Sales Invoice Creation#FD-Conf-SI-0011) |
| Back dated limit | Back dated transaction | In this configuration, user enter the days to allow for back dated transactions. | [FD-Conf-SI-0012](Sales Invoice Creation#FD-Conf-SI-0012) |
| Back dated within the month | Back dated transaction | This will allow for back dated transactions within the month or previous months also. | [FD-Conf-SI-0013](Sales Invoice Creation#FD-Conf-SI-0013) |
| Transaction Series Yearly Reset Alert |  | This configuration will allow to reset transaction series automatically - YES or NO | [FD-Conf-SI-0014](Sales Invoice Creation#FD-Conf-SI-0014) |
| Transaction Series Yearly Reset Date ( To Change The Date Edit Financial Month Starting) |  | This configuration will allow to reset transaction series automatically based on fiscal year start date. | [FD-Conf-SI-0015](Sales Invoice Creation#FD-Conf-SI-0015) |
| Secondary transaction number required |  | Set "True" to enable "Secondary Transaction number" to track the secondary. By default "False" | [FD-Conf-SI-0016](Sales Invoice Creation#FD-Conf-SI-0016) |
| Allow selection of products based on category group attachment for Sales Invoice |  | Salesman Product Category Group header field is enabled in Sales Invoice | [FD-Conf-SI-0017](Sales Invoice Creation#FD-Conf-SI-0017) |
| Treat the selection of product category group as mandatory in sales invoice screen | Allow selection of products based on category group attachment for Sales Invoice | Salesman Product Category Group header field is enabled & mandatory in Sales Invoice | [FD-Conf-SI-0018](Sales Invoice Creation#FD-Conf-SI-0018) |
| Allow Salesman credit Limit |  | When False then system will not validate the Salesman credit limit else system throws an alert message and stop further proceeding | [FD-Conf-SI-0019](Sales Invoice Creation#FD-Conf-SI-0019) |
| Generate Product Category Group based credit norms violation alert in Sales Invoice  |  | When this setting is TRUE then system pop-ups alert based on category group wise credit limit set in Customer master | [FD-Conf-SI-0020](Sales Invoice Creation#FD-Conf-SI-0020) |
| Restrict selling of drug SKU to Non Drug customers for Sales Order / Sales Invoice Y/N  |  | Set "True" to enable filtration of product based on drug Customer. By default "False" | [FD-Conf-SI-0021](Sales Invoice Creation#FD-Conf-SI-0021) |
| Display out-of-stock product's (SKU) in the Sales invoice |  | Set "True" to list product without stock, by default "False" to list product with stock. | [FD-Conf-SI-0022](Sales Invoice Creation#FD-Conf-SI-0022) |
| Filter the Product based on Product Properties 1 & 2 |  | Based on Product (Item) Property selection, the related Product details will be listed. | [FD-Conf-SI-0023](Sales Invoice Creation#FD-Conf-SI-0023) |
| Show alert if tax is not configured for the product.  |  | This configuration will alert user about, Tax not mapped product. | [FD-Conf-SI-0024](Sales Invoice Creation#FD-Conf-SI-0024) |
| Allow List price editable |  | Set to "True" to enable editing the list price, by default list price is not editable  | [FD-Conf-SI-0025](Sales Invoice Creation#FD-Conf-SI-0025) |
| Alert and stop the user if the edited list price is not between PTS and MRP | Allow List price editable | This will restrict user to edit the sale price between PTS and MRP | [FD-Conf-SI-0026](Sales Invoice Creation#FD-Conf-SI-0026) |
| Allow "Net Amount" editable |  | This will allow to edit "Net Amount", by default not editable | [FD-Conf-SI-0027](Sales Invoice Creation#FD-Conf-SI-0027) |
| Allow "Net Rate" editable |  | This will allow to edit "Net Rate", by default not editable  | [FD-Conf-SI-0028](Sales Invoice Creation#FD-Conf-SI-0028) |
| Always load "Net Rate" from "Base Price" |  | Set "True" to load "Net Rate" from "Base Price", by default "Net Rate" are computed in invoice.  | [FD-Conf-SI-0029](Sales Invoice Creation#FD-Conf-SI-0029) |
| Show "Net Rate" in Sales Invoice View |  | This will display the sales invoice view screen | [FD-Conf-SI-0030](Sales Invoice Creation#FD-Conf-SI-0030) |
| Enable "Net PTR" capping |  | This will allow restricting the "Net PTR" based on Capping | [FD-Conf-SI-0031](Sales Invoice Creation#FD-Conf-SI-0031) |
| Enable "PTR" capping |  | This will allow restricting the "PTR" based on Capping | [FD-Conf-SI-0032](Sales Invoice Creation#FD-Conf-SI-0032) |
| ADHOC Discount for each item |  | Set to enable Cash Discount at item detail level | [FD-Conf-SI-0033](Sales Invoice Creation#FD-Conf-SI-0033) |
| ADHOC Discount for transaction |  | Set to enable Cash Discount at transaction/document level | [FD-Conf-SI-0034](Sales Invoice Creation#FD-Conf-SI-0034) |
| SO & SI Customer Max Limit Cash Discount |  | This allow user to configure max limit of cash discount. To be applied for all type of sales invoice  | [FD-Conf-SI-0035](Sales Invoice Creation#FD-Conf-SI-0035) |
| Apply manual discounts on the Original Amount (Quantity X Rate) |  | This will enable compute the manual discount on Gross amount. | [FD-Conf-SI-0036](Sales Invoice Creation#FD-Conf-SI-0036) |
| Invoice Level discount on Per UOM |  | This will allow to compute the Discount, on UOM selected for line item. | [FD-Conf-SI-0037](Sales Invoice Creation#FD-Conf-SI-0037) |
| Line Item Level discount on Per UOM |  | This will allow to compute the Discount, on UOM selected for all line item at invoice level. | [FD-Conf-SI-0038](Sales Invoice Creation#FD-Conf-SI-0038) |
| Enable option to issue free product manually |  | This will allow user to give product as free of cost. | [FD-Conf-SI-0039](Sales Invoice Creation#FD-Conf-SI-0039) |
| Allow Delete scheme free product |  | The user is allowed to delete the scheme applied product when this setting is True | [FD-Conf-SI-0040](Sales Invoice Creation#FD-Conf-SI-0040) |
| Hide 'No Schemes to Apply' Message - if no schemes are applicable |  | This will suppress the message on "No Schemes to Apply" | [FD-Conf-SI-0041](Sales Invoice Creation#FD-Conf-SI-0041) |
| Hide Shipping & Handling Charges |  | This will allow to enable/ disable shipping and handling charges. | [FD-Conf-SI-0042](Sales Invoice Creation#FD-Conf-SI-0042) |
| Auto Adjust Credit Notes in Sales Invoice while saving |  | Set to enable auto adjustment option | [FD-Conf-SI-0043](Sales Invoice Creation#FD-Conf-SI-0043) |
| Allow create implicit collection for Cash Payment mode |  | Set to enable creation of implicit collection transaction for cash payment mode.  | [FD-Conf-SI-0044](Sales Invoice Creation#FD-Conf-SI-0044) |
| Apply Scheme Same as SO |  | This will allow to apply the scheme as per the SO | [FD-Conf-SI-0045](Sales Invoice Creation#FD-Conf-SI-0045) |
| Enable Save & Continue Option |  | This will enable option to continue SO to SI conversion in sequence. | [FD-Conf-SI-0046](Sales Invoice Creation#FD-Conf-SI-0046) |
| Add new item detail Converting SO to SI |  | This will allow add new items while converting SO to SI | [FD-Conf-SI-0047](Sales Invoice Creation#FD-Conf-SI-0047) |
| Allow SO to SI editable price as list price |  | This will allow edit List price while converting SO to SI | [FD-Conf-SI-0048](Sales Invoice Creation#FD-Conf-SI-0048) |
| Invoice print tracking |  | This will allow invoice Print out tracking for generating reports. | [FD-Conf-SI-0049](Sales Invoice Creation#FD-Conf-SI-0049) |
| Sales Invoice Print Formats Display |  | This will allow system to list the relevant Print Formats  | [FD-Conf-SI-0050](Sales Invoice Creation#FD-Conf-SI-0050) |
| Enable to provide Counter Sales Customer Information |  | This will allow to capture the counter sales customer information. | [FD-Conf-SI-0051](Sales Invoice Creation#FD-Conf-SI-0051) |
| Enable List Price Edit in Counter Sales Module |  | This will allow to edit list price | [FD-Conf-SI-0052](Sales Invoice Creation#FD-Conf-SI-0052) |
| Enable Net Rate Edit in Counter Sales Module |  | This will allow to edit Net Rate | [FD-Conf-SI-0053](Sales Invoice Creation#FD-Conf-SI-0053) |
| Enable Net Amount Edit in Counter Sales Module |  | This will allow to edit Net Amount | [FD-Conf-SI-0054](Sales Invoice Creation#FD-Conf-SI-0054) |
| Alert and Stop the if edited value of list price is not between PTS and MRP |  | This will allow sales price to edit between PTS & MRP | [FD-Conf-SI-0055](Sales Invoice Creation#FD-Conf-SI-0055) |
| Enable option to issue free product manually – during counter sales |  | This will allow user to give free product manually by considering 100% discount | [FD-Conf-SI-0056](Sales Invoice Creation#FD-Conf-SI-0056) |
| Alert the user if the TIN Number entered for the walk in customer is available against any of the customer  |  | This allow to prompts message to user that TIN number if already exist in customer master.  | [FD-Conf-SI-0057](Sales Invoice Creation#FD-Conf-SI-0057) |
| Option 1 - alert & continue.  Option 2 - alert & stop | Alert the user if the TIN Number entered for the walk in customer is available against any of the customer  | User can set the action that system would stop or alert and continue | [FD-Conf-SI-0058](Sales Invoice Creation#FD-Conf-SI-0058) |
| Alert the user if the Mobile Number entered for the walk in customer is available against any of the customer  |  | This allow to prompts message to user that mobile  number if already exist in customer master.  | [FD-Conf-SI-0059](Sales Invoice Creation#FD-Conf-SI-0059) |
| Option 1 - alert & continue, Option 2 - alert & stop |  Alert the user if the Mobile Number entered for the walk in customer is available against any of the customer  | User can set the action that system would stop or alert and continue | [FD-Conf-SI-0060](Sales Invoice Creation#FD-Conf-SI-0060) |
| Allow only Cash Payment mode for counter sales   |  | This configuration will allow user to set the payment mode as CASH | [FD-Conf-SI-0061](Sales Invoice Creation#FD-Conf-SI-0061) |
| Disable Adjustment in Counter Sales   |  | This will allow to disable the adjustments | [FD-Conf-SI-0062](Sales Invoice Creation#FD-Conf-SI-0062) |
| Allow auto adjusting the credit notes & sales return in counter sales |  | This will allow to adjust credit notes automatically. | [FD-Conf-SI-0063](Sales Invoice Creation#FD-Conf-SI-0063) |



### Amendment & Cancellation Configuration 

| Configuration                                                                | Related Configuration | Details                                                                         | Ref #                                                     |
|------------------------------------------------------------------------------|-----------------------|---------------------------------------------------------------------------------|-----------------------------------------------------------|
| During amendment, Schemes has to consider based on which date for [original document creation date or Current date] |  | Scheme apply should consider original date or amendment date can be selected | [FD-Conf-SI-Amend-0001](Sales Invoice Creation#FD-Conf-SI-Amend-0001) |
| During amendment, Tax has to consider for [Invoice date or current date] |  | Tax apply should consider original date or amendment date can be selected | [FD-Conf-SI-Amend-0002](Sales Invoice Creation#FD-Conf-SI-Amend-0002) |
| During amendment, Pricing has to consider for [Invoice date or current date]  |  | Sale Price apply should consider original date or amendment date can be selected | [FD-Conf-SI-Amend-0003](Sales Invoice Creation#FD-Conf-SI-Amend-0003) |
| Max no of times a invoice is allowed to amend |  | How many times an invoice can be amended can be provided. System will not allow a invoice to amend more than specified number of times | [FD-Conf-SI-Amend-0004](Sales Invoice Creation#FD-Conf-SI-Amend-0004) |
| After Invoice creation, within how many days it can be amended.  |  | How many days an invoice can be amended can be provided. System will not allow a invoice to amend more than specified number of days | [FD-Conf-SI-Amend-0005](Sales Invoice Creation#FD-Conf-SI-Amend-0005) |
| Reason Mandatory for Amendment |  | When selected True, reason is mandatory for invoice amendment | [FD-Conf-SI-Amend-0006](Sales Invoice Creation#FD-Conf-SI-Amend-0006) |
| Reason Mandatory for Cancellation |  | When selected True, reason is mandatory for invoice cancellation | [FD-Conf-SI-Amend-0007](Sales Invoice Creation#FD-Conf-SI-Amend-0007) |




### Master Related Configurations 
| Configuration                                                                | Related Configuration | Details                                                                         | Ref #                                                     |
|------------------------------------------------------------------------------|-----------------------|---------------------------------------------------------------------------------|-----------------------------------------------------------|
| Alert the user upon clicking on Cancel Button |  | This will alert user with additional popup for cancelling invoices | [FD-Conf-MAS-0001](Sales Invoice Creation#FD-Conf-MAS-0001) |
| Hide the following UOM in transactions |  | This will restrict the UOM's listing on transactions | [FD-Conf-MAS-0002](Sales Invoice Creation#FD-Conf-MAS-0002) |
| Restrict multiple beat mapping for Customer |  | This will restrict to map multiple beat to the customer | [FD-Conf-MAS-0003](Sales Invoice Creation#FD-Conf-MAS-0003) |
| Restrict multiple Salesman mapping for Beat |  | This will restrict to map multiple salesman  to the beat | [FD-Conf-MAS-0004](Sales Invoice Creation#FD-Conf-MAS-0004) |
| Do not allow cross classification Beat Mapping in Salesman & Retailer |  | This will override the Salesman profile selection | [FD-Conf-MAS-0005](Sales Invoice Creation#FD-Conf-MAS-0005) |
| Product with drug flag true are to be listed only for retailer with DL number in customer master |  | Already explained in Sales invoice Product selection | [FD-Conf-MAS-0006](Sales Invoice Creation#FD-Conf-MAS-0006) |
| Allow Send SMS To Customer |  | This will allow to send SMS to customers. | [FD-Conf-MAS-0007](Sales Invoice Creation#FD-Conf-MAS-0007) |


### Customer Related Configurations 
Below configurations from Other Domain Object which have impact in Sales Invoice. 
 
| Configuration                                                                | Related Configuration | Details                                                                         | Ref #                                                     |
|------------------------------------------------------------------------------|-----------------------|---------------------------------------------------------------------------------|-----------------------------------------------------------|
| Display customer in Transaction with status of  |  | This configuration will allow customers list in sales invoice based on status. | [FD-Conf-RET-0001](Sales Invoice Creation#FD-Conf-RET-0001) |


## Distributor level Configuration

| Configuration                                                                | Related Configuration | Details                                                                         | Ref #                                                     |
|------------------------------------------------------------------------------|-----------------------|---------------------------------------------------------------------------------|-----------------------------------------------------------|
| Allow Invoice if Salesman level credit norm settings are violated |  | When this setting is ON then system allows to continue the sales invoice even if salesman exceeds the credit limit  like credit amount , days, no. of bills | [FD-Conf-SI-DP-0001](Sales Invoice Creation#FD-Conf-SI-DP-0001) |
| Option 1 - Seek password for billing for salesman level Credit Norm Violation | Allow Invoice if Salesman level credit norm settings are violated | Set password to seek while validation is violated. Password can be provided to authenticate the transaction post credit limit exceed.  | [FD-Conf-SI-DP-0002](Sales Invoice Creation#FD-Conf-SI-DP-0002) |
| Option 2 -Disable ALERT for billing for Salesman level Credit Norm Violation | Allow Invoice if Salesman level credit norm settings are violated | Disable pop-up for credit limit exceed validation.  | [FD-Conf-SI-DP-0003](Sales Invoice Creation#FD-Conf-SI-DP-0003) |
| Allow Invoice if Customer level credit norm settings are violated |  | When this setting is ON then system allows to continue the sales invoice even if customer exceeds the credit limit  like credit amount , days, no. of bills | [FD-Conf-SI-DP-0004](Sales Invoice Creation#FD-Conf-SI-DP-0004) |
| Option1 -Seek password for billing for customer level credit norm violation | Allow billing if customer level credit norm settings are violated | Set password to seek while validation is violated. Password can be provided to authenticate the transaction post credit limit exceed | [FD-Conf-SI-DP-0005](Sales Invoice Creation#FD-Conf-SI-DP-0005) |
| Option 2 -Disable ALERT for billing for Customer level Credit Norm Violation | Allow billing if customer level credit norm settings are violated | Disable pop-up for customer credit limit exceed | [FD-Conf-SI-DP-0006](Sales Invoice Creation#FD-Conf-SI-DP-0006) |
| Seek password for Sales Invoice Amendment configuration |  | Password can be set for invoice amendment save | [FD-Conf-SI-DP-0007](Sales Invoice Creation#FD-Conf-SI-DP-0007) |
| Seek password for Sales Invoice cancellation configuration |  | Password can be set for invoice cancellation save | [FD-Conf-SI-DP-0008](Sales Invoice Creation#FD-Conf-SI-DP-0008) |
| Ask for password to authenticate the approver |  | Seek password during any approval of Sales Invoice transaction | [FD-Conf-SI-DP-0009](Sales Invoice Creation#FD-Conf-SI-DP-0009) |

# See also .. 
  - [Sales Invoice](Sales Invoice) 
  - [Sales Invoice Creation](Sales Invoice Creation) 
  - [Domain Object Sales Invoice](Domain Object Sales Invoice)
  - [Home](Home)

<!--stackedit_data:
eyJoaXN0b3J5IjpbNTM1MjUzMDA3XX0=
-->
