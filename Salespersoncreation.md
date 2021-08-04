Content

[[_TOC_]]

`Available for review`
# Creation of Salesperson
A person who sells goods on behalf of the owner is known as a salesperson or salesman. A Salesperson master record represents Salesperson as a sales position rather than a person, further these positions can be associated with multiple contact persons. Contacts are persons employed by distributor who works as a Salesperson.  
A [Beat](Beat) is an area allocated to a salesperson. Beat is a day level route for field Salesperson to cover for Capturing [Sales Order](Sales Order), [Collection](Collection), Available Stock(Stock & Inventory), etc... Salesperson can be associated with multiple Beat. 
Salesperson credit settings gives product wise control on credit limit allocation with restrictions for number of open Sales Invoice. Credit norm can be set to Salesperson.

## Who creates Salesperson?
Salesperson are created and altered by [Distributor related users](Distributor Roles), this can also be governed by [Company sales team](Company User Roles). 

# Salesperson Creation 
Create a Salesperson by providing Salesperson Name, Salesperson Code and other details. 


## Precondition for creating Salesperson
Before creating a Salesperson, you need to 
* Create [Salesaman category](Salesaman category)
* Create [Salesaman classification](Salesaman classification)
* Create [Organisation Hierarchy](Organisation Hierarchy)
* Create [Credit Term](Credit Term)

Creation of Sales Person 

1. `Salesperson Name` to be provided. 
1. `Salesperson Code` is allowed to be editable based on configuration. 
1. `Classification` is to allow the Salesperson to be associated with specific classification. 
  - Sample Urban sales rep (USR), Rural sales rep (RSR), DSR, etc... 
  - profile type can be set based on classification. [profile type](Domain-Related-Picklist#picklist_profile_type) 
1. `Unique code` based on classification are generated while saving Salesperson. 
1. `Organization hierarchy` of salesperson can be allocated to associate the Company sales Organization hierarchy
1. `Reporting to user name` can be set to company sales team application user. These associations have impact in mobile application and target allocation. 
1. Other details like `current mobile number`, `current email` can be defined or updated from Contact creation in later section. 
1. Salesperson can be allocated with mobile application. For allocated Mobile Salesperson users, `password` can be set & reset while creating Salesperson. 
1. Default `credit term`, `Total number of credit bills`, `credit amount` set to control the credit limit allocation for Salesperson. Based on these setting, appropriate application level alter will get generated during transaction creation. 
1. `send sms` allows the application for sending alters to Salesperson.

1. Other optional fields are as below, these fields are available depending of implementation / configuration. 
    - `Sales category group`, Allocated to categories sale of only specific category of products   
    - `Product category group`, auto allocated based on Sales category group, preserved for view only. 
    - `Counter Salesperson` (Listing of Salesperson restricted to Counter Sales operations)
    - `Route map` (Linked to Sub Distributor which are defined as part of Customer master)
- `Salary` per month compensation amount is require and used in salary claim 
- `Daily allowance` per day allowance amount is require and used in claim. 

5. On Save, 
    - Salesperson is recorded with generation of unique Salesperson code across application. 
    - Newly created Salesperson are active, based on workflow configuration status of beat & next stage name are set. 
    - depending on workflow, Salesperson may get approval from distributor's higher role user. 
    - active Salesperson are associated to Beat, Credit norm can be set, multiple contact details can be set.  

### Creating Salesperson Beat association
  - Salesperson Beat association is allocation of market area served by Distributor. 

1. After creating Salesperson, `Add Beat` to associate Multiple active Beat with a Salesperson. 
1. Based on configuration, a beat associated with a Salesperson may not be allocated to another Salesperson. 
1. Creating Beat Salesperson will update Modified date of Salesperson. 

#### Edit - Salesperson Beat association 
1. Edit option is require to modify the Beat associated with Salesperson. 
2. Editing a record by selecting another Beat would perform creating new association by update. 

#### Delete - Salesperson Beat association 

1. Delete option is require to remove the Beat associated with Salesperson. 
2. Deleting a record by selecting the option would perform `soft delete` to update the record. 

### Create Credit Norm 

#### Edit Credit Norm 
#### Delete Credit Norm 

### Create Contact 
1. New contact can be created by using option `Add Contact`
1. Below are the details to be provided for creating Salesperson contact, 
  - `date of joining` 
  - `salesperson contact name`
  - `salesman contact mobile number`
  - `address`
  - `driving license number`
  - `pan number`
  - `aadhar number`
  - `date of birth`
  - `account information`
  - `active`
1. A Salesperson can have multiple contact details, but at any given time only one contact information is active. 

#### Edit Contact 
1. The existing active contact details can be modified. 
2. Modified details can be updated to the existing record. 

#### Delete Contact 
1. Option to delete the existing contact will trigger a Soft delete to update the record. 
2. Deleted record are not to be considered to display. 

## Salesperson Modification
6. Created Salesperson can be modified at any given point in time. 
7. On Edit, 
    - Salesperson are allowed to edit based on configuration. 
    - Edited Salesperson information can be saved similar to save process explained above. 
    - Deactivated / Deleted Salesperson are not listed in application, deactivation can be referred to deletion or updating status to deactivation of Salesperson as there is no such action like cancellation of Salesperson.   

8. Deleting 
    - Deleting is not allowed for distributor user or corporate user. 
    - Apply delete operation as soft delete to update the record with `is_deleted` value after updating require logs.  

# Types of Sales Person
    - Distributor Salesperson
    - Company Salesperson

## Distributor Salesperson
"Salesperson" created at distributor location by the distributor operator. Any changes related to existing/new salesman modification will be controlled by the distributor 

## Company Salesperson
"Company Salesperson" created in corporate portal through Corporate Portal users. Any changes related to existing/new company salesman modification will be controlled by the Corporate users in CP
 
## Application level Configuration  

### Salesman Master Configuration:
| Configuration                                                                | Related Configuration | Details                                                                         | Ref #                                                     |
|------------------------------------------------------------------------------|-----------------------|---------------------------------------------------------------------------------|-----------------------------------------------------------|
|Set value for 'Status' column while creating implicit salesman||Status config is created for implicit salesman status|[ FD-Conf-MAS-SM-0001](Salesperson Creation#FD-Conf-MAS-SM-0001)|
|Set value for 'Next stage name' column while creating implicit salesman||Next stage name config is created for implicit salesman Next stage name|[ FD-Conf-MAS-SM-0002](Salesperson Creation#FD-Conf-MAS-SM-0002)|
|Generate 'Unique Code' based on salesman classification||If enabled, unique code is generated for salesman on creation|[ FD-Conf-MAS-SM-0003](Salesperson Creation#FD-Conf-MAS-SM-0003)|
|Enable Channel Classification Configuration for Salesman||If enabled, Channel classification is enabled ofr salesman on creation|[ FD-Conf-MAS-SM-0004](Salesperson Creation#FD-Conf-MAS-SM-0004)|
|Display salesman in Transaction with status of ||Set staus for display salesman on transaction based on salesman status|[ FD-Conf-MAS-SM-0005](Salesperson Creation#FD-Conf-MAS-SM-0005)|
|Update Salesman Name From 'Salesman Unique Code'||If enabled, salesman name is updated as generated Salesman Unique Code|[ FD-Conf-MAS-SM-0006](Salesperson Creation#FD-Conf-MAS-SM-0006)|
|Inactive salesman without sales or sales return transactions for more than months||Set month duration limit to change active salesman to inactive salesman if no transaction with configured maonth range|[ FD-Conf-MAS-SM-0007](Salesperson Creation#FD-Conf-MAS-SM-0007)|
|Channel Config||User channel classification === set channel classification|[ FD-Conf-MAS-SM-0008](Salesperson Creation#FD-Conf-MAS-SM-0008)|
|Channel Config||User channel classification nextstage === set nextstage for the selected channel classification to be configured|[ FD-Conf-MAS-SM-0009](Salesperson Creation#FD-Conf-MAS-SM-0009)|
|Profile Config||Salesman classification === Set the salesman classification type|[ FD-Conf-MAS-SM-0010](Salesperson Creation#FD-Conf-MAS-SM-0010)|
|Profile Config||Salesman Profile === set profile towards the salesman classification tombe configured|[ FD-Conf-MAS-SM-0011](Salesperson Creation#FD-Conf-MAS-SM-0011)|

# Business Rule & Impact 

> Business rules are listed in the below section which requires Domain understanding, hope the previous sections of the Sales Person are clear. Refer [Sales Person](Sales Person), [Sales Person Creation](#creation-of-sales-invoice)   

1. [FD-BR-SM-0001] - User access 

>  FD-BR-SM-0001

    1. Login user should has association with a Distributor. 
    1. In case of user associated with multiple user, then distributor selection is require before creating Salesperson for any transactions 
    1. User with profile access configurations are to be applied while Listing Sales Person, Create, Modify, View Sales Person

    > Refer User profile, Distributor User, Corporate User Distributor mapping 

2. [FD-BR-SM-0002](FD-BR-SM-0002) - List view of Salesperson
    1. Listing page is default landing page, where newly created Salesperson are listed with selected information.
    1. All listing page related features are to be available for Sales Person listing Page. 
    1. Retrieve recently created top `20` Salesperson document with selected field where it belongs to a Distributor and sort with creation date. Default filter for Salesperson applicable for all users. 
    1. Custom filter to be available for all modules
    1. Default list view fields for distributor users  
        -"Unique Salesman Code"
        -"Salesman "
        -"Salesman Code"
        -"Mobile No"
        -"Email"
        -"Password"
        -"Salesman Category Group"
        -"Product Category Group"
        -"Salesman Classification"
        -"Reports to Oraganization Hierarchy"
        -"Credit Days"
        -"Reports to CP User"

    > Refer [Listing page](Listing Page) functionalities, [Custom Filter](Custom Filter).

3. [FD-BR-SM-0003](FD-BR-SM-0003) - Detail view actions
    1. Detail view of salesperson record enables you to perform actions like editing, cancel, amend, print the existing record in PDF format, all actions are configured through [Workflow](Workflow). 
    1. From the salesperson list view, select the desired record. Details view of salesperson record should follow the Field access rule for the login user related profile. 

4. [FD-BR-SM-0004](FD-BR-SM-0004) - Create Salesperson
    1. Allow creation of Salesperson based on Profile access configuration. 
    1. User Distributor association is mandatory for creating any new salesperson record
    1. Corporate User are indirect users to create salesperson related to specific associated distributor. 
    1. Creation of Salesperson should be restricted to user without distributor association. 

5. [FD-BR-SM-0005](FD-BR-SM-0005) - Set value for 'Status' column while creating an salesman
    1.Value to be set for 'Status' Column to make an salesman active/Inactive 

6. [FD-BR-SM-0006](FD-BR-SM-0006) - Set value for 'Next stage name while creating an salesman
    1. Value to be set as Created/Publish to proceed with Next stage of salesman creation process

7. [FD-BR-SM-0007](FD-BR-SM-0007) - Salesman Classification value set 
    1. Required values need to be setup for Salesman classification field to map the salesman with proper classification of salesman 

8. [FD-BR-SM-0008](FD-BR-SM-0008) - Salesman Channel value set 
    1. Required values need to be setup for Salesman Channel field to map the salesman with proper channel


# See also 
  - [Domain-Object-Salesperson](Domain-Object-Salesperson) 
  - [Beat](Beat)
  - [Customer](Customer)
  - [Sales Person](Sales Person)
  - [Sales Order](Sales Order)
  - [Sales](Sales)
  - [Home](Home)

