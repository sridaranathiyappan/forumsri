Content 

[[_TOC_]]

## Who is Customer 
A customer is a person who purchases goods. Secondary customer master are also refered for retailers, who are direct customer to Distributors and Sub Distributors. 

## Types of Customer 
  - A customer becomes a consumer when he or she uses the goods or services, they are also referred as "End Consumer"  
  - A customer become reseller when the sell the good purchased. They are also referred as "Retailer", Sub Distributor"
  - Retailer are merchant who sells direct to the public.

  - Customers are more classified using different Channels. 

## Who creates Customer? 
Customers are created by Distributor, [Retailer](Retailer) & [Company Retailer](Company Retailer). 
  1. Distributor can create customer using create option or import 
  1. Retailer can create a new customer while visiting market. 
  1. Company Retailer can create customer using import option. 

  
## Use Story 

  - Distributor perspective
    1. Customer Master is used to capture Secondary Customer information. 
    1. Customer Master should have option to create, Edit, View and Activate/Deactivate. 
    1. Following details related to the secondary customer are captured, Customer code, Name, Short Name, Customer  Group, Customer  Category, Customer  sub category, Customer classifications.
    1. Further information as required for Customer for processing transaction and MIS will be manually entered like Statutory Tax details. 
    1. Default information for transactions like credit term, cash discount and credit limits are to be entered. 
    1. Credit limit & number of credit bills allowed for customers are to control aspects of credit transactions with customers. system should warn the user.   
    1. In secondary customer master there should be provision to add more than one shipping address & billing address. 
    1. Easy customer selection during transactions. While creating other transactions, Selection of customer can be also based on Short name, customer name, customer code in all transactions. 

  - Corprate user perspective
    1. Customer created in application are to be identified unique.  
    1. Customer created are to be really available in the market, require visiblity to contact if require. 
    1. Customer classification are important & help in planning promotions & marketing activities. 
    1. Each Customer should be approved by company field sales team.
    1. Potential Customer can be created in Universal master by any sales team member in application and the information to be sent to respective distribution network to convert the potential business entity to customer. 
    1. Customer has to be created from Universal secondary customer master. While converting a universal customer into a customer, universal customer code to be refered. 
    1. While creating customer without reference to universal master, information from customer master to be used to create universal master with unique code generated in universal master. 
    1. Universal master provides visibility on number of customer in the line of business.

## To create [Customer](Customer)

### Precondition for creating Customer

Before creating a Customer, you need to

* Create [Channel Hierarchy](Channel)
* Create [Supply chain Hierarchy](Supply chain Hierarchy)
* Create [Geo Hierarchy](Geo Hierarchy) 
* Create [Distributor](Distributor)
* Create [State](State)
* Create [Credit term](Credit-term)
* Create [Payment mode](Payment-mode)

### Create Customer 
1. `Customer Name` & `Customer Code`  are require. 
    - Customer Code can be system generated for each Distributor based on configurations. 
1. `Internal ref` is ment for additonal reference to the parallel system like customer code in Tally software. 
1.  `unique retailer code` auto generated 
    - unique code across distributor throughout application. 
1. email, phone & mobile number are contact details of customer
    - mobile number can be set to verify with OTP number 
1. Address information are detailed with `Pin code` selection from preloaded data
    - On selection of available `pincode`, other related information are loaded `Area`, `Taluk`, `District`, `State`. These details can be changed by user as applicable. 
    - The address detail provided are saved to shipping address & billing address. Further additional address can be added after successfull creation of `customer`. 
1. Customer are associated with `Channel hierarchy`, `Supply chain hierarchy`, `Geo hierarchy` 
    - Channel hierarchy are channel details of customer, parent channel & Channel are allowed to select. This data can be further approved or redefiend by corportate users. 
    - Supply chain hierarchy to classify the level of supply chain, for customer it may be `Sub Distributor` or `Retailer`. 
    - `Geo hierarchy` to specify the location under Geo herearchy. 
1. Customers are classified with appropriate classification data selected for `customer group`, `general classification`,  `value classification`, `potential classification`, `service type`, `retailer type`
    - These classification has impact in applying schemes & promotions 
1. Retailer program are specifci data run by corporate to apply classification and promotions to specific customer. 
    - Appropriate program type to be set or selected.  
    - Number of fields in program types are based on configuration. 
1. `Default Payment Mode`, `Credit days`, `Credit amount`, `Outstanding validation`, `Max Cash discount` are to be set for customer. 
1. Statutory informations are related to tax & regulations
    - `GST Number`, `Type of service`, `PAN Number`, `Drug license`details, `Tax type` are to be provided during customer creation. 
    - `GST number` can be verified through application. 
1. Other details such as Store type or Shop type can be set to classify the Customer, whcih can be used in Reports. 
1. Save Customer, On Saving of customer master record, 
    - Customer record created with generation of unique code & internal reference unique document ID 
    - Universal customer record to be created for each customer created in the application 
    - Newly created universal record ID referent to be associated to customer record by updating. 
    - Report data to be updated for new customer info. Count of customer will get increased for distributor & related company Retailer. 
    - Customer record set with appropriate status based on workflow configuration. 

1. After Customer creation, 
    - Multiple `Beats` & Multiple `address` can be associated with customer
    - `Default Beat` & `Default address` set to load during customer selection in related transactions. 
    - Associated Beat can be allowed to remove. 
    - Address is allowed to be modified. 
1. Customer credit norms are further classified by associating Product category wise norms
    - Number of Credit bill and Credit amount are set for each type of product category. 
    - These are applied during product category specific salesman interactions. 

### Edit 
1. Customer master records are allowed to edit based on workflow configurations. 
1. Editing of particular fields are allowed based on configuration. 
1. Document / Record get updated while submitting the editted record to Save. 

### Cancel / Deactivate
1. Cancellation of Customer is not applicable but deactivate is possible based on workflow configurations. 
1. Status updated to the document and these deactivated customer are not listed in new transactions. 

### Approve 
1. Approval are stage of customer created, approval actions are controlled by workflow configurations. 
1. Status updated to the document and these approved customer are listed in new transactions. 
1. Based on configuration unapproved customers also listed in some of the transactions. 

### Delete Customer Record 
1. Deletion of customer are action performed only by users of specific profiles. 
1. Hard delete of record or only status to be updated are `yet to be decided` 
1. These customers are not listed in transactions 

### Types of Customer creation 
1. Customers are created using create customer page by distributor user 
1. Customer are created using universal master by converting selecting available universal master and convert it to Customer. 
1. Using Importing option by distributor or company users. 
1. Customers created by Retailer from field using mobile device. These informations are recevied and converted to customer. 
1. During Sub distributor and Distributor associations, Customers are created implicitly
1. During Retailer re-alignment, Customers are created implicitly.

## Application level Configuration  

### Retailer Master Configuration:
| Configuration                                                                | Related Configuration | Details                                                                         | Ref #                                                     |
|------------------------------------------------------------------------------|-----------------------|---------------------------------------------------------------------------------|-----------------------------------------------------------|
|Enable credit norm mapping in customer creation||If enabled, credit norm mapping in customer creation grid is available|[FD-Conf-MAS-RET-0001](Retailer Creation#FD-Conf-MAS-RET-0001)|
|Set the default business channel type, while creating customers through customer master|||[FD-Conf-MAS-RET-0002](Retailer Creation#FD-Conf-MAS-RET-0002)|
|Set the config for channel type to be displayed on creating customer|||[FD-Conf-MAS-RET-0003](Retailer Creation#FD-Conf-MAS-RET-0003)|
|Set the maximum discount % as ‘’ ‘’ in the customer master|||[FD-Conf-MAS-RET-0004](Retailer Creation#FD-Conf-MAS-RET-0004)|
|Set max discount for customer to applicable on transaction|||[FD-Conf-MAS-RET-0005](Retailer Creation#FD-Conf-MAS-RET-0005)|
|Allow Customer type related business channel type, while creating customers through customer master||Set config to display Customer type on customer creation, related to channel type|[FD-Conf-MAS-RET-0005](Retailer Creation#FD-Conf-MAS-RET-0005)|
|Allow selection of Inactive Retailer in||Set config module to allow inactive retailer on transaction screen|[FD-Conf-MAS-RET-0006](Retailer Creation#FD-Conf-MAS-RET-0006)|
|Alert if the mobile number do not start with any of the following numbers||If enabled, restrict mobile number validation on customer creation|[FD-Conf-MAS-RET-0007](Retailer Creation#FD-Conf-MAS-RET-0007)|
|Mobile digits ||Set mobile digit to be started|[FD-Conf-MAS-RET-0008](Retailer Creation#FD-Conf-MAS-RET-0008)|
|Alert & Continue|| If enabled, alert if mobile digit not matched with configured digit to be started, and continue flow|[FD-Conf-MAS-RET-0009](Retailer Creation#FD-Conf-MAS-RET-0009)|
|Alert & Stop ||If enabled, alert if mobile digit not matched with configured digit to be started, and restrict flow|[FD-Conf-MAS-RET-0010](Retailer Creation#FD-Conf-MAS-RET-0010)|
|Alert if the mobile number is not equal to 10 digits||If enabled, restriction based on config is validated|[FD-Conf-MAS-RET-0011](Retailer Creation#FD-Conf-MAS-RET-0011)|
|Alert & Continue ||Alert if mobile no not equal to 10 digit and continue flow|[FD-Conf-MAS-RET-0012](Retailer Creation#FD-Conf-MAS-RET-0012)|
|Alert & Stop||Alert if mobile no not equal to 10 digit and restrict flow|[FD-Conf-MAS-RET-0013](Retailer Creation#FD-Conf-MAS-RET-0013)|
|Alert if the mobile number is duplicated||If enabled, restriction based on config is validated|[FD-Conf-MAS-RET-0014](Retailer Creation#FD-Conf-MAS-RET-0014)|
|Within the distributor data||Validate if mobile no is duplicate with respective distributor on customer creation|[FD-Conf-MAS-RET-0015](Retailer Creation#FD-Conf-MAS-RET-0015)|
|Within the company data||Validate if mobile no is duplicate with in customer on customer creation|[FD-Conf-MAS-RET-0016](Retailer Creation#FD-Conf-MAS-RET-0016)|
|Alert & Continue||Alert if mobile no duplicated and continue flow|[FD-Conf-MAS-RET-0017](Retailer Creation#FD-Conf-MAS-RET-0017)|
|Alert & Stop||Alert if mobile no duplicated and restrict flow|[FD-Conf-MAS-RET-0018](Retailer Creation#FD-Conf-MAS-RET-0018)|
|Enable OTP Feature in retailer creation||If enabled, OTP column details are available on retailer creation|[FD-Conf-MAS-RET-0019](Retailer Creation#FD-Conf-MAS-RET-0019)|
|Maximum validity period for OTP (in Mins)||Set config value for to maintain OTP validity period|[FD-Conf-MAS-RET-0020](Retailer Creation#FD-Conf-MAS-RET-0020)|
|Display customer in Transaction with status of||Set status config to display customer on screen transaction|[FD-Conf-MAS-RET-0021](Retailer Creation#FD-Conf-MAS-RET-0021)|
|Set value for 'Status' column while OTP is verified successfully|||[FD-Conf-MAS-RET-0022](Retailer Creation#FD-Conf-MAS-RET-0022)|
|Set config status value, of customer if OTP verification is successful|||[FD-Conf-MAS-RET-0023](Retailer Creation#FD-Conf-MAS-RET-0023)|
|Set value for 'Next stage name' column while OTP is verified successfully|||[FD-Conf-MAS-RET-0024](Retailer Creation#FD-Conf-MAS-RET-0024)|
|Set config Next stage name value, of customer if OTP verification is successful|||[FD-Conf-MAS-RET-0025](Retailer Creation#FD-Conf-MAS-RET-0025)|
|Set the maximum rows to fill while importing the customers|||[FD-Conf-MAS-RET-0026](Retailer Creation#FD-Conf-MAS-RET-0026)|
|Set config value to import and fill customer rows|||[FD-Conf-MAS-RET-0027](Retailer Creation#FD-Conf-MAS-RET-0027)|
|Check customer code to be unique by distributor wise||If enabled, customer code is unique based on distributor wise, to be validated|[FD-Conf-MAS-RET-0028](Retailer Creation#FD-Conf-MAS-RET-0028)|
|Load Supply Chain Hierarchy Based On Channel Hierarchy||If enabled, on customer creation supply chain hierarchy is loaded based on channel hierarchy selected on respective column|[FD-Conf-MAS-RET-0029](Retailer Creation#FD-Conf-MAS-RET-0029)|
|Make the pincode dependent fields as readonly||If enabled, pincode related fields like (District, city) are made as non editable on creation|[FD-Conf-MAS-RET-0030](Retailer Creation#FD-Conf-MAS-RET-0030)|
|Populate the cities list(census data) based on the City(If Check)||If enabled, based on city list the census data are to be displayed on screen of customer creation|[FD-Conf-MAS-RET-0031](Retailer Creation#FD-Conf-MAS-RET-0031)|
|Retailer GPS Capture||If enabled, Retailer GPS is enabled to capture and to be recorder in lat / long column|[FD-Conf-MAS-RET-0032](Retailer Creation#FD-Conf-MAS-RET-0032)|
|Alert if the GST number is duplicated||If enabled, restriction based on config is validated|[FD-Conf-MAS-RET-0033](Retailer Creation#FD-Conf-MAS-RET-0033)|
|Within the distributor data||Validate if GST number is duplicate with respective distributor on customer creation|[FD-Conf-MAS-RET-0034](Retailer Creation#FD-Conf-MAS-RET-0034)|
|Within the company data|| Validate if GST number is duplicate with in customer on customer creation|[FD-Conf-MAS-RET-0035](Retailer Creation#FD-Conf-MAS-RET-0035)|
|Alert & Continue||Alert if GST number duplicated and continue flow|[FD-Conf-MAS-RET-0036](Retailer Creation#FD-Conf-MAS-RET-0036)|
|Alert & Stop||Alert if GST number duplicated and restrict flow|[FD-Conf-MAS-RET-0037](Retailer Creation#FD-Conf-MAS-RET-0037)|
|Re-Align Sub-retailers also when moving Retailer||If enabled, customer which are to be re-allign, includes sub-retailers also to be re-allign respectively|[FD-Conf-MAS-RET-0038](Retailer Creation#FD-Conf-MAS-RET-0038)|
|Show Creation Button in Retailer List and Retailer Detail view||If enabled, + icon will be visble for create customer|[FD-Conf-MAS-RET-0039](Retailer Creation#FD-Conf-MAS-RET-0039)|
|Active filed default active for the New Retailer creation||If enabled, retailer is set to active staus on creation|[FD-Conf-MAS-RET-0040](Retailer Creation#FD-Conf-MAS-RET-0040)|
|Allow default beat mapping for retailer in salesinvoice||If enabled, on salesinvoice transaction beat mapping is loaded default towards customer|[FD-Conf-MAS-RET-0041](Retailer Creation#FD-Conf-MAS-RET-0041)|
|Populate new customer channel dropdown||If enabed, retailer channel type column are listed with channel type details on fields|[FD-Conf-MAS-RET-0042](Retailer Creation#FD-Conf-MAS-RET-0042)|
|Allow Customer Code Editable||If enabled, customer code is allowed to edit by user|[FD-Conf-MAS-RET-0043](Retailer Creation#FD-Conf-MAS-RET-0043)|
|Customer realignment customers are new retailers||If enabled, re-allign customer are treated as new retailer|[FD-Conf-MAS-RET-0044](Retailer Creation#FD-Conf-MAS-RET-0044)|
|Auto populate Distributor Code in the Customer Code Prefix field (In distribitor Master Screen)||If enabled, Distributor code is populated based on customer prefix code|[FD-Conf-MAS-RET-0045](Retailer Creation#FD-Conf-MAS-RET-0045)|
|Populate the Universal Master details based on the user and distributor mapping||If enabled, Universal Master details based on the user and distributor mapping are populated on Universal screen|[FD-Conf-MAS-RET-0046](Retailer Creation#FD-Conf-MAS-RET-0046)|
|Set Prefix When Creating customer through Universal master approval||If enabled, set config prefix value on approval process on universal master creating customer|[FD-Conf-MAS-RET-0047](Retailer Creation#FD-Conf-MAS-RET-0047)|
|Customer Category to be filtered based on parent selection||If enabled, set value for filter category level|[FD-Conf-MAS-RET-0048](Retailer Creation#FD-Conf-MAS-RET-0048)|
|Customer Category to be filtered based on parent selection||Set value to filter Customer Category parent level|[FD-Conf-MAS-RET-0049](Retailer Creation#FD-Conf-MAS-RET-0049)|
|Customer Category to be filtered based on parent selection||Set value to filter Customer Category child level|[FD-Conf-MAS-RET-0050](Retailer Creation#FD-Conf-MAS-RET-0050)|
|Inactive retailers without sales or sales return transactions for more than Months||Set month config limit to inactivate customer without transaction|[FD-Conf-MAS-RET-0051](Retailer Creation#FD-Conf-MAS-RET-0051)|
|Customer Approval Process||Enable Customer Approval Process|If enabled, set config for Customer Approval Process|[FD-Conf-MAS-RET-0052](Retailer Creation#FD-Conf-MAS-RET-0052)|
|Customer Approval Process||Generate Unique Code – Upon Approval of Customers|If enabled, unique code is genrated on approval customer|[FD-Conf-MAS-RET-0053](Retailer Creation#FD-Conf-MAS-RET-0053)|
|Customer Approval Process||Unique Code Start Digit|set value to generate unique code start with|[FD-Conf-MAS-RET-0054](Retailer Creation#FD-Conf-MAS-RET-0054)|
|Customer Approval Process||Generate Retailer unique code based on state master zone prefix 3 character + state code 2 char+ district code 3 char + division / city / vilage / town code 6 char + 6 decimal length running sequence|[FD-Conf-MAS-RET-0055](Retailer Creation#FD-Conf-MAS-RET-0055)|
|Customer Approval Process||If enabled, based on setting unique code will be generated|[FD-Conf-MAS-RET-0056](Retailer Creation#FD-Conf-MAS-RET-0056)|
|Customer Approval Process||Unique Code Sequence == set unique code sequence for generation|[FD-Conf-MAS-RET-0057](Retailer Creation#FD-Conf-MAS-RET-0057)|
|Allow unapproved customer in all transactions.||If enabled, unapproved customer are allowed on transaction|[FD-Conf-MAS-RET-0058](Retailer Creation#FD-Conf-MAS-RET-0058)|
|Restrict Distributor to edit the following fields in customer master – after approval||If enabled, set filed column not be editable after customer approval|[FD-Conf-MAS-RET-0059](Retailer Creation#FD-Conf-MAS-RET-0059)|
|Enable Channel Classification Configuration|Channel Config||User channel classification== set user channel classification types|[FD-Conf-MAS-RET-0060](Retailer Creation#FD-Conf-MAS-RET-0060)|
|Enable Channel Classification Configuration|Channel Config||User channel classification nextstage == set nextstage status value config respective mapped towards User channel classification|[FD-Conf-MAS-RET-0061](Retailer Creation#FD-Conf-MAS-RET-0061)|

# Business Rule & Impact 

> Business rules are listed in the below section which requires Domain understanding, hope the previous sections of the Retailer Master are clear. Refer [Retailer](Retailer), [RetailerCreation](#creation-of-Retailer)   

1. [FD-BR-RET-0001] - User access 

>  FD-BR-RET-0001

    1. Login user should has association with a Distributor. 
    1. In case of user associated with multiple user, then distributor selection is require before creating Retailer for any transactions 
    1. User with profile access configurations are to be applied while Listing Retailer, Create, Modify, View Retailer

    > Refer User profile, Distributor User, Corporate User Distributor mapping 

2. [FD-BR-RET-0002](FD-BR-RET-0002) - List view of Retailer
    1. Listing page is default landing page, where newly created Retailer are listed with selected information.
    1. All listing page related features are to be available for Retailer listing Page. 
    1. Retrieve recently created top `20` Retailer document with selected field where it belongs to a Distributor and sort with creation date. Default filter for Retailer applicable for all users. 
    1. Custom filter to be available for all modules
    1. Default list view fields for distributor users  
      -"Customercode"
      -"Customername"
      -"Address"
      -"Contact person"
      -"Email"
      -"Phone"
      -"State"
      -"City"
      -"Pincode"
      -"TypeShop"
      -"Countersale Customer"
      -"Active"
      -"Village Type"
      -"TDS Applicable"
      -"TCS Applicable"
      -"TIN Number"
      -"GSTIN Number"
      -"PAN Number"
      -"Customer Category"
      -"Customer Channel"
      -"Supply Chain Hierarchy"
      -"Supply Chain Distributor code"
      -"Geography"
      -"Name of the Bank"
      -"Bank Account Number"
      -"IFSC Code"
      -"Name of the Bank Branch"


    > Refer [Listing page](Listing Page) functionalities, [Custom Filter](Custom Filter).

3. [FD-BR-RET-0003](FD-BR-RET-0003) - Detail view actions
    1. Detail view of Retailer record enables you to perform actions like editing, cancel, amend, print the existing record in PDF format, all actions are configured through [Workflow](Workflow). 
    1. From the Retailer list view, select the desired record. Details view of Retailer record should follow the Field access rule for the login user related profile. 

4. [FD-BR-RET-0004](FD-BR-RET-0004) - Create Retailer
    1. Allow creation of Retailer based on Profile access configuration. 
    1. User Distributor association is mandatory for creating any new Retailer record
    1. Corporate User are indirect users to create Retailer related to specific associated distributor. 
    1. Creation of Retailer should be restricted to user without distributor association. 

5. [FD-BR-RET-0005](FD-BR-RET-0005) - Set value for 'Status' column while creating an salesman
    1.Value to be set for 'Status' Column to make an salesman active/Inactive 

6. [FD-BR-RET-0006](FD-BR-RET-0006) - Set value for 'Next stage name while creating an salesman
    1. Value to be set as Created/Publish to proceed with Next stage of salesman creation process

7. [FD-BR-RET-0007](FD-BR-RET-0007) - Customer Category value set 
    1. Required values need to be setup for Customer Category field to map the salesman with proper classification of salesman 

8. [FD-BR-RET-0008](FD-BR-RET-0008) - Customer Channel value set 
    1. Required values need to be setup for Customer Channel field to map the salesman with proper channel

9. [FD-BR-RET-0009](FD-BR-RET-0009) - Set the default business channel type, while creating customers
  1.To set the default Business channel while creating a customer , Provision given to change the Business channel as required 

10. [FD-BR-RET-0010](FD-BR-RET-0010) - Alert if the mobile number do not start with any of the following numbers
  1. Required data validation to check whether mobile number is inline with proper numbering format like 10 digits

11. [FD-BR-RET-0011](FD-BR-RET-0011) - Load Supply Chain Hierarchy Based On Channel Hierarchy
   1. Need to load the supply chain hierarchy based on the selection of Channel Hierarchy

12. [FD-BR-RET-0012](FD-BR-RET-0012) - Alert if the GST number is duplicated
   1. There should be an validation to check GST number duplication and revert with Alert Message to the user

13. [FD-BR-RET-0013](FD-BR-RET-0013) - Prefix When Creating customer through Universal master approval
   1.Required Prefix for customer code should get populated based on the prefix codification

14. [FD-BR-RET-0014](FD-BR-RET-0014) - Customer Category to be filtered based on parent selection
   1. Requried to set customer category based on the parent category selection 

15. [FD-BR-RET-0015](FD-BR-RET-0015) - Customer Approval Process
  1.On approval of New customer , New customer code need to get generated based on the prefix codification


### [Domain Object Customer](Domain-Object-Customer)

## See also 
  - [Home](Home)
  - [Distributor](Distributor)
  - [Sales](Sales)
  - [Sales Order](Sales Order) 
  - [Sales Invoice](Sales Invoice) 
