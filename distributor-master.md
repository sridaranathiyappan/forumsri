# Distributor  

* Who is a Distributor for Manfacturer/Retailer?		
* Who Creates the Distributor?	
* What are the basic fields details required to create a Distributor ?

## Who is a Distributor for Manfacturer/Retailer?	
### Manfacturer 
The distributor who buys the goods or services from a Manfacturer or business in order to sell it to the Retailers

### Retailer	
The firm or Distributor who sells the goods or services to the retailer or Institutions as part of secondary selling 

## Who Creates the Distributor?	
**Company Sales Admin**

A Company Sales Admin can create a new Distributor, whenever there is a service request raised by their company Sales team

## What are the basic fields details required to create a Distributor 	
Creataing a Distributor  required common details to be entered in systematic maner
Distributor Name|Address|Conatct Number|Channel of the Distributor | GSTIN number|and others"

**Creating the  Distributor**

* New Distributor creation request will be raised by company sales team to the admin team with required distributor details 
* Sales Admin adds the required information of the Distributor in the system while creating a new distributor masters. Distributor details like Distributor Name, Address, Email Address,TIN,Phone number,shipping address details are mandatory while creating a new Distributor into the system
* Given master information can be edited any number of times by the Sales admin if the Distributor requests for it. 
* There should also be an provision for the Sales admin to create the Distributor  and do the Order placement at the same time, Salesman also optionally adds the Credit Card(s) , Netbanking account details to the Distributor master. 
* In order to active the online payments for the primary purchase in future.

**Finding the Distributor**

If any existing Distributor contacts the admin user through any channel(Phone, Email, IM), the user locates the existing Distributor  master by Name, phone and/or email, user id,TIN number and take the request 

**Edit the Distributor**

As needed mostly requested by the Distributor , a user adds/updates the details on a Distributor  master e.g. Name, Email, Shipping Address, and Payment Information. 

**Deactivate the Distributor**

If Distributor  has to be blocked for sales or Deactivation from the system , there should be provision for the user to validate the pending Outstanding bills and remind the sales team on the same and do the deactivation of the Distributor

### Data upload process (Controlled Mechanism)
There should be an provison to upload the master data through Excel upload and there should be validation check point on excel upload process to manage the data points for the mandate fields
Also there should be an user roles & rights permisison access in order to authorise the specific user to manage the Distributor related approvals 

## Events at Front End
- User chooses the Distributor Addition menu item to create a New Distributor 
- User enters the Distributor name,ID,Address,Phonenumber,Email,Shipping Address and TIN number
- User selects the supply chain from the drop down list
- User selects the Customer Group  from the drop down list
- User selects the Geography from the drop down list
- User clicks on 'Save' option and the customer details will get added to the customer master

## Events at Business logic layer (overview)
- Providing the front end access control based on user profile to create a Distributor 
- Generate record reference number for record creation Internal reference. Every request should have this reference to process, manipulate or produce data. 

- Validate the data submitted from front end - Datatype & security related. 
- Validate the data submitted from front end - Business related 

## Flow of Related Events 
- Creation of Distributor User
- Distributor and Distributor User has to get Mapped to login into Distributor portal to manage the operations 
- Distributor and Sub Distributor Mapping to be done
- Creation of Vendor and mapping the Vendor with the distributor
- CP user and Distributor has to get mapped 
- CD Key mapping with Distributor to manage the data integration 

## Flow of related Events Chart
graph TB
  subgraph "Report Update Process"
  NodeReport[Update Report Data]
  end

  subgraph "Mail Process"
  NodeMail[Sent Mail to Customer]
  end


# Precondition for Creating a Distributor   

## 1. Before creating a Distributor  , you need to 
* Create [Geography Hierarchy](Geography Hierarchy)
* Create [State](State) 
* Create [City](City) 
* Create [Area](Area)
* Create [Tax](Tax Master) & [Channel Hierarchy](Channel Hierarchy)
* Create [Payment Mode](Payment Mode) 
* Create [Type of Services]
* Create [Distributor Type]
* Create [Credit Limit]


## 2.Fill in the required mandated  fields on the Distributor Master page as necessary.

- Distributor Code
- Distributor Name
- Street
- City
- District
- State
- Region
- Country
- Contact Person
- Email
- Phone
- Pincode
- Forum Code
- Active
- Date Format
- Reports to
- Alternate mobile
- Customer Code Prefix
- Disclaimer Acceptance
- MOQ UOM
- Overall MOQ Quantity
- Bill Print Format
- iStore
- ECO Green
- TCS Collectable
- Aadhar No
- TCS Percentage
- Nil Tax Certification NO
- TIN Number
- ST.Reg Number
- CST. Reg Number
- Credit Limit
- Security Deposit
- GSTIN No
- PAN No
- Type of Services
- FSSAI Number
- Distributor Tax Type
- No of Sales Man
- Drug License no  20 B
- Drug License no  21 B
- CIN Number
- Drug License 20 B Expiry
- Drug License 21 B Expiry
- Supply Chain
- Geography
- Default Depot
- Customer Group
- CD Class
- CD Line
- CD Type
- Distributor Type
- Distributor Margin
- CD Branch
- Proprietor Name
- Latitude
- Longitude
- User Name
- Last Name
- Password
- Confirm Password
- Status

## 3. Select a Payment Mode appropriately
   - Need to have provision to select the Paymode Mode as Cash or  Credit 

## 4. Select a Credit Term if Payment Mode is credit.  
   - Credit days to be set based on Distributor  type 

