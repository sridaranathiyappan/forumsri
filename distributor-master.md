# Distributor Master

* What is a Distributor Master Used for?
* Who Created Distributor Master?
* When is a Distributor is Created?


## What is a Distributor Master Used for?

 Distributor Master is used to create the  details of  the Primay user(Distributor) who will be using the Distribuot Portal. Based on the Information/Configuration in this Master DP portals Pricing, Tax and other Logic will behave


## Who Created Distributor Master?
1. Corprate Portal designated user or admin will be creating the Distributor Master
2. If Integration has been enabled to the Primary ERP the same will flow through Integration"


## When is a Distributor is Created?
1. Whenever a new  Distributor is added to the system
2. Whenever a alignment to the distributor is done - Geographical Shift, Business Category Shift
3. Whenever a ammendment to the Distributor Statuotry details"


# Precondition for Creating a Distributor 
Before creating a direct sales invoice, you need to 
* Create [Geography Hierarchy](Geography Hierarchy)
* Create [State](State) 
* Create [Tax](Tax Master) & [Channel Hierarchy](Channel Hierarchy)
* Create [State](State) 

>> Fill in the required mandated  fields on the Distributor Master page as necessary.
    - Distributor Code 
    - Distributor Name
    - State
    - City
    - Country 
    - Remark 
    - TIN number
    - Terms and Conditions
    - Tax Type
    - Depot Warehouse 

# Business Rule & Impact 

> Business rules are listed in the below section which requires Domain understanding, hope the previous sections of the Distributor. Refer [-----]


1. [FD-BR-DM-0001](#FD-BR-DM-0001) - User access 
    1. Login user should has admin rights to create Distributor

    > Refer User profile,Corporate Admin User  

2. [FD-BR-DM-0002](#FD-BR-DM-0002) - New Distribution Creation
        1. Login user should have required  admin rights to create the Distributor

3.
        

             
 


