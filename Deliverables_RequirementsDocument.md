# Requirements Document 

Authors: Mattia Dutto, Francesco Medina, Soufiane Aksadi, Bahizi Alain Divin

Date: 2021/04/21

Version: 1.0

# Contents

- [Essential description](#essential-description)
- [Stakeholders](#stakeholders)
- [Context Diagram and interfaces](#context-diagram-and-interfaces)
	+ [Context Diagram](#context-diagram)
	+ [Interfaces](#interfaces) 
	
- [Stories and personas](#stories-and-personas)
- [Functional and non functional requirements](#functional-and-non-functional-requirements)
	+ [Functional Requirements](#functional-requirements)
	+ [Non functional requirements](#non-functional-requirements)
- [Use case diagram and use cases](#use-case-diagram-and-use-cases)
	+ [Use case diagram](#use-case-diagram)
	+ [Use cases](#use-cases)
    	+ [Relevant scenarios](#relevant-scenarios)
- [Glossary](#glossary)
- [System design](#system-design)
- [Deployment diagram](#deployment-diagram)

# Essential description

Small shops require a simple application to support the owner or manager. A small shop (ex a food shop) occupies 50-200 square meters, sells 500-2000 different item types, has one or a few cash registers 
EZShop is a software application to:
* manage sales
* manage inventory
* manage customers
* support accounting


# Stakeholders


| Stakeholder name  | Description | 
| ----------------- |:-----------:|
| Owner / Manager     | Owner / Manager of the shop             | 
| Employer | He works for the owner / manager, it can do anything except the accounting stuff and add new employer |
| Customer | Person that buy something from the shop |
| Customer with Fidelity Card | Person that is a frequent buyer and he collects point / he is allowed to access to some promotions |
| Supplier | Person that sell to the owner / manager the products and so the shop can sell to the customers | 
| Bank employer / interface | When wView Balance reporte information about the number of item that we have in the werehouse and the accounting things |

# Context Diagram and interfaces

## Context Diagram
\<Define here Context diagram using UML use case diagram>
``` plantuml 

left to right direction
actor "Owner/Manager" as OM
actor Employer as E
actor Customer as C
actor "Customer with FC" as CF
actor Supplier as S
actor "Bank employer / interface" as B
actor "Database" as DB

OM -- (EZShop)
E -- (EZShop)
C -- (EZShop)

C <- CF
(EZShop) -- DB
(EZShop) -- S
(EZShop) -- B

```
\<actors are a subset of stakeholders>

## Interfaces
\<describe here each interface in the context diagram>

\<GUIs will be described graphically in a separate document>

| Actor | Logical Interface | Physical Interface  |
| ------------- |:-------------:| -----:|
| Owner / Manager     | GUI | Cash register |
| Employer | GUI | Cash register |
| Database | API | Internet connection |
| Bank employer / interface | GUI, API | Cash register, internet connection | 

# Stories and personas
\<A Persona is a realistic impersonation of an actor. Define here a few personas and describe in plain text how a persona interacts with the system>

\<Persona is-an-instance-of actor>

\<stories will be formalized later as scenarios in use cases>
Pippo is a 16 years old, he lives is a small city. He play football every afternoon in a big football club. Up to now he is attending the third year of the high school and in the future he wants to became an astronaut. Every day he goes to the grocery shore for buying the lunch before going to the football club. After the training he will do the homeworks. 

Liz is 40. She is from Pinerolo, she attended the Politecnico of Milano 20 years ago. She lives with her husband and her beautiful daughter. She is a full stack developer and she works for a big company in London. But due to the Covid-19 situation she actually come back home and she is working from home. Every weekend she goes out and she buy food for all the next week. She really likes to support small shop because she things that we have to support local business. In her free times she enjoy to play volleyball with her friends but in the last two years she started to do yoga sessions. 

Paolo is 25, he just finished the bachelor degree from Politecnico di Torino in "Ingegneria Gestionale", he doesn't want to go on and 2 months ago he decided to open a local shop where he lives. He lives in a small town at about 15 minuts of train from the centre of Turin. In his free time he enjoy to go out with friends and hiking the mountains near his home. Before became a owner of a shop he worked as an employer for a fruits and vegetables shop. 

Kate is 26. He is from Germany and 7 years ago she moved from Berlin to the same hometown of Paolo. In the last 4 years he worked as employee in a food company and now he want to move in a something smaller. She is a supported of "KM0 and biology foods". In her free time she started a vegetable garden. Her dream is to sell what she can produce in the garden. She has a lot of friends and two years ago she sold her car and bought a bike and when she totally move to ecologic trasport. She asked to Paolo to bacome one of his supplier. 

Camilla is a 80 years old, and unfortunally she doesn't have a car so she can't go to the big supermarket for buying foods. In the last two years she alwats went to same local shop but when Paolo opened the new EZShop she started to go there. When she came to the shop she usually stops for a chat with Paolo or the employer. Camilla has the Fidality card with number 0. She takes care of her 2 nephews and she usually spend a lot of time cooking for the family of the two children.  

# Functional and non functional requirements

## Functional Requirements

\<In the form DO SOMETHING, or VERB NOUN, describe high level capabilities of the system>

\<they match to high level use cases>

| ID        | Description  |
| ------------- |:-------------:| 
|  FR1     | Authorize, authenticate and report |  
|   FR1.1  | Log in |  
|   FR1.2  | Log out |
|   FR1.3  | Create account |
|   FR1.4  | Delete account |
|   FR1.5  | Define roles and skills |
|   FR1.6  | Change account info |
|   FR1.7  | Report information about user access into cash system  |
|  FR2     | Report crash events of the Cash system |
|  FR3     | Handle Sales |  
|   FR3.1  |  Check if product has discounts |
|   FR3.2  |  Apply discount if any |
|   FR3.3  |  Add points to fidelity card |
|   FR3.4  |  Select type of payment |
|   FR3.5  |  Execute the transaction  |
|   FR3.6  |  Compute the total amount to be paid for the shopping  |
|   FR3.7  |  Given the amount paid compute the remaining change to be given |
|   FR3.8  |  Leave a feedback about customer satisfaction |
|   FR3.9  |  Store the information about the shopping made |
|  FR4     | Show the inventory of a shop |
|   FR4.1  |  Add a new product into the shop's inventory |
|   FR4.2  |  Check the stock status |
|   FR4.3  |  Update information of a product |
|   FR4.4  |  Sort by expiration date |
|   FR4.5  |  Sort by price |
|   FR4.6  |  Sort by type |
|   FR4.7  |  Sort by quantity |
|   FR4.8  |  Sort by pieces sold |
|   FR4.9  |  Search by product id |
|   FR4.10 |  Search by product name |
|   FR4.11 |  Search by description |
|   FR4.12 |  Filter by quantity |
|   FR4.13 |  Filter by pieces sold |
|   FR4.14 |  Filter by type |
|   FR4.15 |  Filter by expiration date |
|   FR4.16 |  Filter by supplier |
|   FR4.17 |  Delete a product from the shop's inventory |
|  FR5     | Manage customers |
|   FR5.1  |  Create a customer account |
|   FR5.2  |  Change customer's personal info |
|   FR5.3  |  Delete an customer account |
|   FR5.4  |  Associate fidelity card to a customer |
|   FR5.5  |  Send newsletter or advertising based on customer preferences/habits |
|  FR6     | Support accounting |
|   FR6.1  |  View monthly salary |
|   FR6.2  |  View time table of employees |
|   FR6.3  |  View Balance report |
|  FR7     | Handle orders |
|   FR7.1  |  List all orders |
|   FR7.2  |  Create an orders |
|   FR7.3  |  Delete an order  |
|   FR7.4  |  Edit an order    |
|  FR8     | Handle supplier |
|   FR8.1  |  Update supplier's list |
|   FR8.2  |  Add a new supplier |
|   FR8.3  |  Edit a supplier |
|   FR8.4  |  Delete a supplier |


## Non Functional Requirements

\<Describe constraints on functional requirements>

| ID        | Type (efficiency, reliability, ..)           | Description  | Refers to |
| ------------- |:-------------:| :-----:| -----:|
|  NFR1     | Portability   | The SW can be installed on many different cash systems with JAVA virtual machine (JVM) | All FR |
|  NFR2     | Efficency     | All CRUD operations between cash system and server should take < 1 sec  | All FR |
|  NFR3     | Usability     | GUI should be intuitive. Text and buttons should be big for the cash system  | All FR |
|  NFR4		| Localisation  | Prices should use the local currency and language | All FR |
|  NFR5     | Reliability   | Server should be available 99% of the time | ALL FR|
|  NFR6     | Security      | All billing transactions should be secured with SSL protocol | FR3.5 |
|  NFR7     | Regulatory   | For legal purposes each transaction supervised by the respective cashier should be traceable over the time    | FR3 |
|  NFR8     | Maintainability   | All SW crash events should be reported to reduce the effort to fix the system | FR2 |


# Use case diagram and use cases


## Use case diagram
\<define here UML Use case diagram UCD summarizing all use cases, and their relationships>

left to right direction

actor "Owner/Manager" as om
actor Employee as e
actor SecurityService as ss 
actor BankEmployee as b
actor RegisteredCustomer as cf
actor customer as c

usecase "FR1 Authorise and Authenticate" as authorise
usecase "FR1.1 Log in" as login
usecase "FR1.2 Log out" as logout
usecase "FR1.3 Create account" as create
usecase "FR1.4 Delete account" as delete
usecase "FR1.5 Define roles and skills" as roles
usecase "FR1.6 Change account info" as changeInfo
usecase "FR1.7 Report information about user access into cash system" as reportUser
usecase "FR2 Report crash events of the Cash system" as reportCrash
usecase "FR3 Handle Sales" as handleSales
usecase "FR3.1 Check if product has discounts" as discount
usecase "FR3.2 Apply discount if any" as applyDiscount
usecase "FR3.3 Add points to fidelity card" as fidelity
usecase "FR3.4 Select type of payment" as paymentType
usecase "FR3.5 Execute the transaction"  as executeTransaction
usecase "FR3.6 Compute the total amount to be paid for the shopping" as totalAmount  
usecase "FR3.7 Given the amount paid compute the remaining change to be given" as changeDue
usecase "FR3.8 Leave a feedback about customer satisfaction" as feedback
usecase "FR3.9 Store the information about the shopping made" as shoppingInfo
usecase "FR4 Handle the inventory of a shop" as inventory
usecase "FR4.1 Add a new product into the shop's inventory"  as addProdInv
usecase "FR4.2 Check the stock status" as checkStock
usecase "FR4.3 Update information of a product" as updateProduct
usecase "FR4.4 Sort by expiration date" as expirationDate
usecase "FR4.5 Sort by price" as byPrice
usecase "FR4.6 Sort by type" as byType
usecase "FR4.7 Sort by quantity" as byQuantity
usecase "FR4.8 Sort by pieces sold" as byPieceSold
usecase "FR4.9 Search by product id" as byProductId
usecase "FR4.10 Search by product name" as byProductName
usecase "FR4.11 Filter by description" as byDescriptionFilter
usecase "FR4.12 Filter by quantity" as byQuantityFilter
usecase "FR4.13 Filter by pieces sold" as byPieceSoldFilter
usecase "FR4.14 Filter by type" as byTypeFilter
usecase "FR4.15 Filter by expiration date" as byExpirationDateFilter
usecase "FR4.16 Filter by supplier" as bySupplierFilter
usecase "FR4.17 Delete a product from the shop's inventory" as deleteProduct

usecase "FR5 Manage customers" as manageCust
usecase "FR5.1 Create a customer account"  as createAccount
usecase "FR5.2 Change customer's personal info" as changeCustInfo
usecase "FR5.3 Delete an customer account" as deleteCustAccount
usecase "FR5.4 Associate fidelity card to a customers" as associateFidelityToCustomer
usecase "FR5.5 Send newsletter or advertising based on customer preferences/habits" as sendNewsletter
usecase "FR6 Support accounting" as supportAccount
usecase "FR6.4 Create employee Account" as employeeAccount
usecase "FR6.1 View monthly salary" as monthlySalary
usecase "FR6.2 View time table of employees" as timeTable
usecase "FR6.3 View Balance report" as balanceReport

usecase "FR7 Handle orders" as handleOrders 
usecase "FR7.1 List all orders" as allOrders
usecase "FR7.2 Create an orders" as createOrder
usecase "FR7.3 Delete an order"  as deleteOrder
usecase "FR7.4 Edit an order"    as editOrder

usecase "FR8  Handle supplier" as handleSupplier
usecase "FR8.1 Update supplier's list" as updateSupplier
usecase "FR8.2 Add a new supplier" as newSupplier
usecase "FR8.3 Edit a supplier" as editSupplier
usecase "FR8.4 Delete a supplier" as deleteSupplier



om -- handleSupplier


reportCrash --> om


om -- authorise
e -- reportUser
reportUser --> ss


e --> handleSales
c -- feedback

om -- inventory
e -- inventory

e -- manageCust
sendNewsletter --> cf

om -- supportAccount
om -- employeeAccount
balanceReport --> b
addProdInv ..> checkStock : <<include>>


authorise ..> login : <<include>>
authorise ..> logout : <<include>>
authorise ..> create : <<include>>
authorise ..> delete : <<include>>
authorise ..> roles : <<include>>
authorise ..> changeInfo : <<include>>
authorise ..> reportUser : <<include>>



handleSales ..> discount : <<include>>
handleSales ..> applyDiscount : <<include>>
handleSales ..> fidelity : <<include>>
handleSales ..> paymentType : <<include>>
handleSales ..> executeTransaction : <<include>>
handleSales ..> totalAmount : <<include>>
handleSales ..> changeDue : <<include>>
handleSales ..> feedback : <<include>>
handleSales ..> shoppingInfo : <<include>>


inventory ..> addProdInv : <<include>>
inventory ..> checkStock : <<include>>
inventory ..> updateProduct : <<include>>
inventory ..> expirationDate : <<include>>
inventory ..> byPrice : <<include>>
inventory ..> byType : <<include>>
inventory ..> byQuantity : <<include>>
inventory ..> byPieceSold : <<include>>
inventory ..> byProductId : <<include>>
inventory ..> byProductName : <<include>>
inventory ..> byQuantityFilter : <<include>>
inventory ..> byPieceSoldFilter : <<include>>
inventory ..> byDescriptionFilter : <<include>>
inventory ..> byTypeFilter : <<include>>
inventory ..> bySupplierFilter :<<include>>
inventory ..> byExpirationDateFilter : <<include>>
inventory ..> deleteProduct : <<include>>
deleteProduct ..> updateProduct :<<include>>





manageCust ..> createAccount : <<include>>
manageCust ..> changeCustInfo : <<include>>
manageCust ..> deleteCustAccount: <<include>>
manageCust ..> associateFidelityToCustomer : <<include>>
manageCust ..> sendNewsletter : <<include>>




supportAccount ..> monthlySalary :<<include>>
supportAccount ..> timeTable :<<include>>
supportAccount ..> balanceReport :<<include>>

handleOrders ..> allOrders :<<iclude>>
handleOrders ..> createOrder: <<include>>
checkStock <.. createOrder : <<include>>
handleOrders ..> deleteOrder : <<include>>
handleOrders ..> editOrder: <<include>>

handleSupplier ..> updateSupplier : <<include>>
handleSupplier ..> newSupplier : <<include>>
handleSupplier ..> editSupplier : <<include>>
handleSupplier ..> deleteSupplier :<<include>>



\<next describe here each use case in the UCD>

### Use case 1, UC1 - login
| Actors Involved        | owner |
| ------------- |:-------------:| 
|  Precondition     | 	owner is in the database	 |  
|  Post condition     | 	manager is logged in	 |
|  Nominal Scenario     | owner inters username and password and is authenticated |
|  Variants     | user name or password incorrect ; access denied |


##### Scenario 1.1 

\<describe here scenarios instances of UC1>

\<a scenario is a sequence of steps that corresponds to a particular execution of one use case>

\<a scenario is a more formal description of a story>

\<only relevant scenarios should be described>

| Scenario 1.1 | |
| ------------- |:-------------:| 
|  Precondition     | \<Boolean expression, must evaluate to true before the scenario can start> |
|  Post condition     | \<Boolean expression, must evaluate to true after scenario is finished> |
| Step#        | Description  |
|  1     |  |  
|  2     |  |
|  ...     |  |

##### Scenario 1.2

##### Scenario 1.x

### Use case 2, UC2 - logout

| Actors Involved        | owner,employee |
| ------------- |:-------------:| 
|  Precondition     | user is arlead logged in |  
|  Post condition     | user is logged out |
|  Nominal Scenario     | the user presses the logout button  |

### Use case 4, UC4 - delete account
| Actors Involved        | owner  |
| ------------- |:-------------:| 
|  Precondition     | owner exists in the database |  
|  Post condition     | owner no longer in the database |
|  Nominal Scenario     | the user wants to use the app so he have to first register in order to customize it	|

### Use case 3, UC3 - create account
| Actors Involved        | owner |
| ------------- |:-------------:| 
|  Precondition     |	account not existing in the database |  
|  Post condition     |  |
|  Nominal Scenario     | user inters email and username and password
	|


### Use case 5, UC5 - Define roles and skills 
| Actors Involved        | employee,owner |
| ------------- |:-------------:| 
|  Precondition     | employee is present in the database |  
|  Post condition     |	 |
|  Nominal Scenario     | 	the owner defines  roles for each employee he has for accountability purposes	 |

### Use case 6, UC6 - change account info
| Actors Involved        | owner |
| ------------- |:-------------:| 
|  Precondition     | the owner's info is arleady present in the database |  
|  Post condition     |  |
|  Nominal Scenario     | the owner changes the employee or his own account info eg; roles of employee ... |

### Use case 7, UC7 - report user access into cash
| Actors Involved        |  employee,owner,security services |
| ------------- |:-------------:| 
|  Precondition     | anyone is stealing |  
|  Post condition     |  |
|  Nominal Scenario     | an employee or a customer is stealing and is cought; the owner calls for the security services to follow protocol |

### Use case 8, UC2 - report crash events
| Actors Involved        | employee,owner |
| ------------- |:-------------:| 
|  Precondition     | \<Boolean expression, must evaluate to true before the UC can start> |  
|  Post condition     | \<Boolean expression, must evaluate to true after UC is finished> |
|  Nominal Scenario     | \<Textual description of actions executed by the UC> |
|  Variants     | \<other executions, ex in case of errors> |

### Use case 9, UCx
| Actors Involved        |  |
| ------------- |:-------------:| 
|  Precondition     | \<Boolean expression, must evaluate to true before the UC can start> |  
|  Post condition     | \<Boolean expression, must evaluate to true after UC is finished> |
|  Nominal Scenario     | \<Textual description of actions executed by the UC> |
|  Variants     | \<other executions, ex in case of errors> |

### Use case 10, UCx
| Actors Involved        |  |
| ------------- |:-------------:| 
|  Precondition     | \<Boolean expression, must evaluate to true before the UC can start> |  
|  Post condition     | \<Boolean expression, must evaluate to true after UC is finished> |
|  Nominal Scenario     | \<Textual description of actions executed by the UC> |
|  Variants     | \<other executions, ex in case of errors> |

### Use case 11, UCx
| Actors Involved        |  |
| ------------- |:-------------:| 
|  Precondition     | \<Boolean expression, must evaluate to true before the UC can start> |  
|  Post condition     | \<Boolean expression, must evaluate to true after UC is finished> |
|  Nominal Scenario     | \<Textual description of actions executed by the UC> |
|  Variants     | \<other executions, ex in case of errors> |

### Use case 12, UCx
| Actors Involved        |  |
| ------------- |:-------------:| 
|  Precondition     | \<Boolean expression, must evaluate to true before the UC can start> |  
|  Post condition     | \<Boolean expression, must evaluate to true after UC is finished> |
|  Nominal Scenario     | \<Textual description of actions executed by the UC> |
|  Variants     | \<other executions, ex in case of errors> |

### Use case 13, UCx
| Actors Involved        |  |
| ------------- |:-------------:| 
|  Precondition     | \<Boolean expression, must evaluate to true before the UC can start> |  
|  Post condition     | \<Boolean expression, must evaluate to true after UC is finished> |
|  Nominal Scenario     | \<Textual description of actions executed by the UC> |
|  Variants     | \<other executions, ex in case of errors> |

### Use case 14, UCx
| Actors Involved        |  |
| ------------- |:-------------:| 
|  Precondition     | \<Boolean expression, must evaluate to true before the UC can start> |  
|  Post condition     | \<Boolean expression, must evaluate to true after UC is finished> |
|  Nominal Scenario     | \<Textual description of actions executed by the UC> |
|  Variants     | \<other executions, ex in case of errors> |

### Use case 15, UCx
| Actors Involved        |  |
| ------------- |:-------------:| 
|  Precondition     | \<Boolean expression, must evaluate to true before the UC can start> |  
|  Post condition     | \<Boolean expression, must evaluate to true after UC is finished> |
|  Nominal Scenario     | \<Textual description of actions executed by the UC> |
|  Variants     | \<other executions, ex in case of errors> |

### Use case 16, UCx
| Actors Involved        |  |
| ------------- |:-------------:| 
|  Precondition     | \<Boolean expression, must evaluate to true before the UC can start> |  
|  Post condition     | \<Boolean expression, must evaluate to true after UC is finished> |
|  Nominal Scenario     | \<Textual description of actions executed by the UC> |
|  Variants     | \<other executions, ex in case of errors> |

### Use case 17, UCx
| Actors Involved        |  |
| ------------- |:-------------:| 
|  Precondition     | \<Boolean expression, must evaluate to true before the UC can start> |  
|  Post condition     | \<Boolean expression, must evaluate to true after UC is finished> |
|  Nominal Scenario     | \<Textual description of actions executed by the UC> |
|  Variants     | \<other executions, ex in case of errors> |

### Use case 18, UCx
| Actors Involved        |  |
| ------------- |:-------------:| 
|  Precondition     | \<Boolean expression, must evaluate to true before the UC can start> |  
|  Post condition     | \<Boolean expression, must evaluate to true after UC is finished> |
|  Nominal Scenario     | \<Textual description of actions executed by the UC> |
|  Variants     | \<other executions, ex in case of errors> |

### Use case 19, UCx
| Actors Involved        |  |
| ------------- |:-------------:| 
|  Precondition     | \<Boolean expression, must evaluate to true before the UC can start> |  
|  Post condition     | \<Boolean expression, must evaluate to true after UC is finished> |
|  Nominal Scenario     | \<Textual description of actions executed by the UC> |
|  Variants     | \<other executions, ex in case of errors> |

### Use case 20, UCx
| Actors Involved        |  |
| ------------- |:-------------:| 
|  Precondition     | \<Boolean expression, must evaluate to true before the UC can start> |  
|  Post condition     | \<Boolean expression, must evaluate to true after UC is finished> |
|  Nominal Scenario     | \<Textual description of actions executed by the UC> |
|  Variants     | \<other executions, ex in case of errors> |

### Use case 21, UCx
| Actors Involved        |  |
| ------------- |:-------------:| 
|  Precondition     | \<Boolean expression, must evaluate to true before the UC can start> |  
|  Post condition     | \<Boolean expression, must evaluate to true after UC is finished> |
|  Nominal Scenario     | \<Textual description of actions executed by the UC> |
|  Variants     | \<other executions, ex in case of errors> |

### Use case 22, UCx
| Actors Involved        |  |
| ------------- |:-------------:| 
|  Precondition     | \<Boolean expression, must evaluate to true before the UC can start> |  
|  Post condition     | \<Boolean expression, must evaluate to true after UC is finished> |
|  Nominal Scenario     | \<Textual description of actions executed by the UC> |
|  Variants     | \<other executions, ex in case of errors> |



# Glossary

\<use UML class diagram to define important terms, or concepts in the domain of the system, and their relationships> 

\<concepts are used consistently all over the document, ex in use cases, requirements etc>

# System Design
\<describe here system design>

\<must be consistent with Context diagram>

```plantuml
	class EZShopSystem {
		+ Handle_Sales()
		+ Handle_Inventory()
		+ Handle_Customers()
		+ Support_Accounting()
	}

	class Computer {
	}

	class Switch {
	}
	
	class BadgeSystem {
	}

	class BadgeSensor {
	}

	class FideltyCardSystem {
	}

	class CardIssuer {
	}

	class CashRegistersSystem {
	}

	class PaymentSystem {
	}

	class PaymentReader {
	}

	class BarCodeSystem {
	}

	class BarCodeSensor {
	}

	EZShopSystem o-- Computer
	EZShopSystem o-- BadgeSystem
	EZShopSystem o-- FideltyCardSystem
	EZShopSystem o-- CashRegistersSystem
	Computer o-- Switch
	BadgeSystem o-- BadgeSensor
	FideltyCardSystem o-- CardIssuer
	CashRegistersSystem o-- PaymentSystem
	CashRegistersSystem o-- BarCodeSystem
	PaymentSystem o-- PaymentReader
	BarCodeSystem o-- BarCodeSensor
```

# Deployment Diagram 

\<describe here deployment diagram >

```plantuml
node "Computer" as PC
artifact "EZShop Control Executable" as exe

artifact "ERP" as erp {
	artifact "Sales Services" as Sales
	artifact "Accounting" as Accouting
	artifact "Inventory Services" as Inventory
	artifact "Costumers Services" as Costumers
	} 
node "Shop Server" as Server

erp -- Server
Server -- exe
exe -[dashed]-> PC : deploys
```
