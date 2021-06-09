# Customer 

* Who is a Customer?	
* Who Creates the Customers?	
* What are the basic fields details required to create a customer?

## Who is a Customer?	
A firm or individual person who buys goods or services from a shop or business in order to sell it to the end consumer or Institutions 


## Who Creates the Customers?	
### 1.Distributor or Distributor Operator
A distributor can create a customers over the telephonic or through a direct Walk-in to the customer place

### 2.SalesMan
A distributor saleman can create a new customer, During his regular market visit plan

### 3.Company Salesman
A Company saleman can create a new customer,based on the plan for the market visit

## What are the basic fields details required to create a customer	
1.Creataing a Customer required common details to be entered in systematic maner
Reatiler Name|Address|Conatct Number|Channel of the retailers|GSTIN number|and others"

# User Story :

## Story 1: Creating the  Customer
1.New customer contacts the Salesman for placing an order for the desired product. Salesman creates a new customer profile and subsequently place an order for him. 
2.Salesman adds required information of the customer in the system while creating a new profile. Customer details like First Name, Last Name, Email Address,TIN,Phone number,shipping address details are mandatory while creating a new customer into the system
3.Given profile information can be edited any number of times by the Salesman if the customer requests for it. 
4.There should also be an provision for the salesman to create the customer do the Order placement at the same time, Salesman also optionally adds the Credit Card(s) , Netbanking account details to the the customer profile. In order to active the online payments in future  

## Story 2: Finding the Customer
If any existing customer contacts the user through any channel(Phone, Email, IM), the user locates the existing customer profile by Name, phone and/or email, user id,TIN number and take the request 

## Story 3: Edit the Customer
As needed mostly requested by the customer, a user adds/updates the details on a customer profile e.g. Name, Email, Shipping Address, and Payment Information. 

## Story 4: Deactivate the Customer
If customer has to be blocked for sales or Deactivation from the system , there should be provision for the user to validate the pending Outstanding bills and initiate the deactivation of customer from the system


# Precondition for Creating a Customer  

## 1. Before creating a Customer , you need to 
* Create [Geography Hierarchy](Geography Hierarchy)
* Create [State](State) 
* Create [City](City) 
* Create [Area](Area)
* Create [Tax](Tax Master) & [Channel Hierarchy](Channel Hierarchy)
* Create [Payment Mode](Payment Mode) 
*Create [Gender](Gender) 

## 2.Fill in the required mandated  fields on the Distributor Master page as necessary.

   -Distributor Code
   -Customer Name
   -Customer Code
   -Address 1
   -Customer Category
   -Customer Channel
   -PIN Code
   -City
   -State
   -Mobile No
   -District
   -Payment Mode
   -Registration Date
   -Geography
   -Customer First Name
   -Customer Last Name
   -Gender
   -Area Name 
  -Street Name
  -Market Name
  -Type Shop/Firm
  -Plot Number
  -Alternate Mobile Number
  -Tehsil/Taluka Name
  -Retailer Tax Type
  -GSTIN No
  -PAN No
  -Aadhaar No
  -Is Drug License Required

## 3. Select a Payment Mode appropriately
   - Need to have provision to select the Paymode Mode as Cash or  Credit 

## 4. Select a Credit Term if Payment Mode is credit.  
   - Credit days to be set based on customer type 
   
# Business Rule & Impact 

## > Business rules are listed in the below section which requires Domain understanding, hope the previous sections of the Customer Management . Refer [Customer] (Customer), [Customer Creation](#creation-of-customer)   

### 1. [FD-BR-CM-0001](#FD-BR-CM-0001) - User access 
    1. Login user should has association with a Distributor. 
    2. In case of user associated with multiple distributor, then distributor selection is require before creating the customer under the Distributor
    3. User with profile access configurations are to be applied for Customer (Create, Modify, View , Deactivation) 

    > Refer User profile, Distributor User, Corporate User Distributor mapping 

### 2. [FD-BR-CM-0002](#FD-BR-CM-0002) - List view of Customer Master
    1. Listing page is default landing page of the customer where newly created Customers are listed with selected information.
    2. Custom filter to be available for all modules
    3. Default list view fields for Customers Filters view 
    
   -Customer Name
   -Customer Code
   -Address 1
   -Customer Category
   -Customer Channel
   -PIN Code
   -City
   -State
   -Mobile No
   -District
   -Payment Mode
   -Registration Date
   -Geography
   -Customer First Name
   -Customer Last Name
   -Gender
   -Area Name
   -Street Name
   -Market Name
   -Type Shop/Firm
   -Plot Number
   -Alternate Mobile Number
   -Tehsil/Taluka Name
   -Retailer Tax Type
   -GSTIN No
   -PAN No
   -Aadhaar No
   -Is Drug License Required
       

## 3. [FD-BR-CM-0003](FD-BR-CM-0003) - Detail view actions
    1. Detail view of customer record enables you to perform actions like editing, cancel, amend, print the existing record in PDF format, all actions are configured through [Workflow](Workflow). 
    2. From the customer list view, select the desired record. Details view of customer master record should follow the Field access rule for the login user related profile. 

## 4. [FD-BR-CM-0004](FD-BR-CM-0004) - Create Sales Order 
    1. Allow creation of Sales Order for the Created Customer through [Sales order](Sales Order) Module  
    2. User Distributor association is mandatory for creating transaction. 
    3. Corporate User are indirect users create transaction related to specific associated distributor. 
    4. Creation of Sales Invoice should be restricted to user without distributor association. 

## 5. [FD-BR-CM-0005](FD-BR-CM-0005) - Create Sales Invoice 
    1. Allow creation of Sales Invoice for the Created Customer through [Sales Invoice] (Sales Invoice Module ) 
    2. User Distributor association is mandatory for creating transaction. 
    3. Corporate User are indirect users create transaction related to specific associated distributor. 
    4. Creation of Sales Invoice should be restricted to user without distributor association. 
      
## 6. [FD-BR-CM-0005](FD-BR-CM-0005) - Create Sales Return
    1. Allow creation of Sales Return for the Created Customer through [Sales Retur][(Sales Return)Module  
    2. User Distributor association is mandatory for creating transaction. 
    3. Corporate User are indirect users create transaction related to specific associated distributor. 
    4. Creation of Sales Invoice should be restricted to user without distributor association. 

## 7. [FD-BR-CM-0006](FD-BR-CM-0006) - Create Sales Collections 
    1. Allow creation of Sales Collection against outstanding bills for the Created Customer through [Sales Collections[(Sales Collections)Module  
    2. User Distributor association is mandatory for creating transaction. 
    3. Corporate User are indirect users create transaction related to specific associated distributor. 
    4. Creation of Sales Collections should be restricted to user without distributor association. 
 


