## Project Scope :
Digital Payment System is a process to manage the secondary sales payment collections from the retailer & sub distributor through online payment channels like Credit card / Gpay /E-Wallets/I have paid cheque,Cash

## Roles
Each interaction in a Web Payments scenario involves a number of entities. In order to make it clear who the actors are, the following roles are defined:

### payer
- the entity sending value in a transaction.

### payee
- the entity receiving value in a transaction.

### buyer
- an entity purchasing a product or service.

### merchant
- an entity that is offering a product or service for sale.

### payment processor
- an entity that is responsible for transferring value between entities and generating verifiable digital receipts.

## Credentials
- In order to interact, an entity may require one or more pieces of information from another entity. Each of these pieces of information, which may be digitally signed by a 3rd party, are called a credential. The following credentials are commonly used throughout this document:

### identity credential
- An identity credential contains a pseudo-anonymous URL that can be used to uniquely identify an entity. The URI typically doesn't contain any personally identifiable information

### email credential
- An email credential contains a verified email address and proves that the entity associated with the credential has verified their email address with a 3rd party.

### payment processor credential
- A payment processor credential contains a verified payment processor URL that was assigned to the entity associated with the credential by their payment processor.

### shipping address credential
- A shipping address credential contains a verified address where shipping deliveries may be made that is also associated with the entity associated with the credential. Typically, organizations that are capable of associating a shipping address with an entity, such as the United States Postal Service, provide these credentials.

### Who are the users of  Digital payment system
The main actors of this digital payment systems are retailer /sub-distributor and salesman 

* Retailer - Retailer already using an retailer app to manage his order placing and tracking the delivery. Using this digital payment process he can able to pick the outstanding invoices and do the required payments 
through various mode of channels (Credit card / Gpay /E-Wallets ) to the distributor

* Sub distributor - Sub Distributor already using an retailer app to manage his order placing and tracking the delivery from his distributor . Using this digital payment process he can able to pick the outstanding invoices and do the required payments 
through various mode of channels (Credit card / Gpay /E-Wallets ) to the distributor

* Salesman - Salesman already been using the current mode of collection through (Cash/Cheque). additionally they will given an provision to collect the payment through other channels like Credit card / Gpay /E-Wallets 

### Why we need this digital payment system
Using Digital payment system , retailer can able to make the Hassles free payment instantly and get the immediate visibility on the outstanding amount. which will certainely enable the distributor to complete the collection reconcillation and plan for the quick order delivery to the retailers / sub distributors 


## Existing Solution : 

Currently , There is no provision to handle the payment collection from retailers through Retailer App. 
All Pending Invoices are made available for collection through Distributor portal & Mobile app.The Current Availble payments types are (Cash/Cheque) 

### Salesperson Collection process:

 During the Market visit , Salesperson has to collect the payment from the retailer against the pending invoices through Mobile app and upload it to backend 
 Mode of payment allowed are , Cash collection & Cheque collection. In case of credit customer , system allow to collect the partial payment against Pending Invoices 
 Based on the collection entry received against Invoice , system will calculate the collection outstanding and update the same in customer ledger / Salesman Ledger 

### Vansale collection process:

 In Ready Van scenario , Vansale  person will do the invoicing on the spot and collect the payment from the retailer against the invoices through Mobile app and upload it to backend 
Mode of payment allowed are , Cash collection & Cheque collection. In case of credit customer , system allow to collect the partial payment against Pending Invoices 
 Based on the collection entry received against Invoice , system will calculate the collection outstanding and update the same in customer ledger / Salesman Ledge

## Proposed Solution: 

### Data Dictionary

### Payment process:
   - There should be an provision for the retailer to make the invoice payment to the distributor bank account using various mode of payment (Credit / Debit Card/UPI/Amazon pay)

![image](https://user-images.githubusercontent.com/84070217/131771632-a5ef0928-4e83-4013-860c-242054e838c6.png)


### Payment gateway portal
   - It connects a bank account to the relevant payment processor.It transmits the transaction information either virtually through web payment services and APIs or in-person through a payment terminal

### Payment service
   -  This payment service authorizes the different modes of online transactions such as internet banking, credit cards, UPI (Unified Payments Interface), and other forms of digital wallets.it ensures secure payments and protects sensitive data , so that 
      Customers can safely store their essential information, like credit card details in the Payment Card Industry Data Security Standard (PCI-DSS) portal 
    - Many payment gateways tools also come with fraud screening tools, including CVV (Card Verification Value), AVS (Address Verification Service), and payer authentication, to reduce the risk of information loss and theft. Some payment gateways also support cross-border online payments, making it easier for aspiring business owners to scale their payments at the international level


## Precondition for creating the Digital payment Process

Before setup a Digital payment part , you need to 
* Create [Distributor](Distributor) details 
* Create [Salesman](Salesman) details 
* Create [Beat](Beat) details 
* Create [Customer](Customer) details 
* Create [Payment types](Payment types) details 
* Create [Payment Gateway](Payment Gateway) details 
* Create [Payment Processor](Payment Processor) details 
* Create [Token Vault](Token Vault) details 

## What data to carry
* Payer Details (Retailer) Name, Email Address, Address, PAN (Primary Account Number),Card Number, Card Expiration Date, and CVV

### Credit Card Data: What is Allowed to be Stored
 * Cardholder name 
 * PAN (Primary Account Number) (the 16 digit number on the front of the card)
 * Expiration date 
 * Service code (You won’t find this data on the card itself. It lives within the magnetic stripe

### Credit Card Data: What is Not Allowed to be Stored
 * Sensitive authentication data (e.g., the full magnetic stripe info)
 * PIN
 * PIN block (i.e., the encrypted PIN)
 * CVV/CVC (the three or four-digit code on the back of the card)

## How to carry
 - Payer card details to be carried through Payment Gateway (3rd Party Payment Gateway or Create Own payment Gateway)

### Billing and recurring payments
 - For Distributor working with recurring payments, tokenization can be a blessing to their business. With credit card payment tokenization, Each distributor  can store customers’ billing information for subsequent automatic payments.
The Distributor won’t even need to keep all customer data on a file: it can store Retailer tokens and use them for the next purchase.

## What standard to be followed

### Own Payment Gateway
 - If we  need to store the card data ourself, our bar for self-assessment is very high and we may need to have a QSA (Qualified Security Assessor) come onsite and perform an audit to ensure that we have all of the controls in place necessary to meet the PCI DSS specifications.

### Get an SSL certificate
 - Online payment security technology that establishes a link between the customer’s Mobile web browser and our Portal. To encrypting all communications to ensure that sensitive information (like credit card data) is unreadable for any third parties

### Credit Card Data: What is Not Allowed to be Stored
- Sensitive Authentication Data (SAD) can not be stored after authorization of a transaction. This data includes the full magnetic stripe data found on the back of the card, as well as any equivalent data on the EMV chip or elsewhere. 
-SAD also includes the CVV (or equivalent data) as well as the PIN and PIN block. This data is extremely valuable to attackers for use in both card-present and card-not-present environment.

## How tokenized transaction works
- A customer decides to make a purchase. They initiate a transaction and enter their credit card information.
- The token requestor, which can be an online store or an issuer application, sends a cardholder’s PAN to the separate token vault.
- The issuer performs identification and verification (ID&V) and submits these results to the token vault. This process is called “binding” and it completes the token registration.
- The token vault transfers the registered payment token to the requestor and thereby completes the token request process 
- The acquirer transfers the token to the credit card network for further authorization. The customer’s primary account number and token are sent to the issuer who makes an authorization decision.
- After authorization, the customer’s data is stored in the bank’s secure virtual vaults, and the token is matched with the customer’s account number.
- The bank checks the availability of funds and approves or rejects the transaction

## Storing of Credit / Debit card details :
- Most merchants will be storing the  credit card data for recurring billing.The best way to store credit card data for recurring billing is by utilizing a third party credit card vault and tokenization provider. 

## Tokenization URL : 
      - https://pcivault.io/ 

- If you need to store the card data yourself, your bar for self-assessment is very high and you may need to have a QSA (Qualified Security Assessor) come onsite and perform an audit to ensure that you have all of the controls in place necessary to meet the PCI DSS specifications.
-End-to-end encryption – Designed to render cardholder data unreadable, encrypted at the device.
- Token vault – Cardholder data is replaced by digital “tokens” and is stored in the secure Global Payments Integrated vault, rather than the merchant environment

## Where to store card details
- Card details will be tokenized and stored in Vault (Centraised server) . Token Service works by simply replacing a cardholder’s 16-digit account number with a secure token that protects the card number. A payment token can be limited to a specific eCommerce merchant, mobile device, or a certain number of purchases before expiration.

## Using 3rd party how to manage the payment
- Some of the 3rd party's are VISA / Google Pay :

* Step-by-step explanation of how Google Pay tokenization works.

 - A user attaches their card to the Google Pay app.
 - Google Pay requests a token representing the card the user is trying to add from the bank that issued the card.
 - After token issuance, the card becomes tokenized: it receives a unique identification number associated with it.
 - Google Pay encrypts the new tokenized card so it is ready for payments

## Business Rule 

### Digital payment Process

1. **Payment creation Date** is often set to default current date
   - User allowed to capture the collection only for the current date , Also date after present date should also be restricted. 

2. **Credit Card details**  field validation
    - User allowed to select the mode of payment On select of credit card , Validation to be done on 
         *  Credit card number , validation to be done for '16'  digit numerical values
         *  CVV number, validation to be done for 3 -4 digits 
         *  Expiry Date , validation to be done for date format and expiry date check
        
3. **UPI**  field validation
    - User allowed to select the mode of payment , On select of UPI option , user allowed to scan QR code  or enter his UPI ID. system should do the '@' symbol validation  


### Card details Amendment 
Amendment to Credit card details are the corrections to the card number / CVV / expiry date entered in the payment card entry screen

Amendment performs validation actions as below, 
  - Clear the values only for the required fields in the payment card entry screen and enter the required values newly and proceed with payment authentication process 

### Card details Cancellation
Cancellation to the Credit card details are the event to cancel all the entry in that screen and re-enter new card number / CVV / expiry date in the payment card entry screen

> Business rules are listed in the below section which requires Domain understanding, hope the previous sections of the Digital payment Process are clear

a) User access 

    1. Login user should has association with a Distributor. 
    2. In case of user associated with multiple user, then distributor selection is require before doing an Digital payment against the Oustanding Invocies

    > Refer User profile, Distributor User, Corporate User Distributor mapping 

b)  View of Payment screen 
    1. Payment capture screen view with fields for retailer / salesman users  
       -"Mode of payment"
       -"Card number"  
       -"Card Holders's Name"
       -"Expiry Date"
       -"CVV"

c) Detail view actions
    1. Detail view of card details record enables you to perform actions like editing, cancel, amend, existing record 

d) Process timeout Exception Handling
    1.

