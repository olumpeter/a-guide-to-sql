# A guide to SQL

## Module 1: INTRODUCTION TO KIMTAY PET SUPPLIES AND STAYWELL STUDENT ACCOMMODATION DATABASES

### WHAT IS A DATABASE?

- A **database** is a structure that contains different *categories* of information and the *relationships* between these categories. 
    - For example, the KimTay Pet Supplies database contains information about categories such as sales representatives (sales reps), customers, invoices, and items. The StayWell database contains information about the offices that manage the accommodation, the owners of the accommodation, the residents, and the services (such as cleaning and maintenance) offered for the properties.
    - Each database also contains relationships between categories. For example, the KimTay Pet Supplies database contains information that relates sales reps to the customers they represent and customers to the invoices they have placed. The StayWell database contains information that relates the two main company offices to the properties that they manage, the owners, the different services to the service request, and to the resident renting a property.

### THE KIMTAY PET SUPPLIES DATABASE

#### Problem (Why Kim Pet Supplies needs a database)

- The management of KimTay Pet Supplies (a supplier of pet supplies, food, and accessories located in Cody, Wyoming) has determined that the company’s recent growth no longer makes it feasible to maintain customer, invoice, and inventory data using its manual systems. In addition, KimTay Pet Supplies wants to build an Internet presence. With the data stored in a database, management will be able to ensure that the data is up-to-date and more accurate than in the current manual systems. In addition, managers will be able to obtain answers to their questions concerning the data in the database easily and quickly, with the option of producing a variety of useful reports.
- Management has determined that KimTay Pet Supplies must maintain the following
information about its sales reps, customers, and inventory in the new database:
    - The sales rep ID, first name, last name, full address, cell phone number, total commission, and commission rate for each sales rep.
    - The customer ID, first name, last name, full address, e-mail address, current balance, and credit limit for each customer, as well as the ID of the sales rep who represents the customer.
    - The item ID, description, number of units on hand, category, storage location,and unit price for each item in inventory.
- KimTay Pet Supplies also must store information about invoices. Figure 1-1 shows a sample invoice.
- The sample invoice shown in Figure 1-1 has three sections:
    - The heading (top) of the invoice contains the company name and contact information; the invoice number and date; the customer’s ID, name, and full address; and the sales rep’s ID and full name.
    - The body of the invoice contains one or more invoice lines, sometimes called line items. Each invoice line contains an item ID, an item description,the number of units of the item ordered, and the quoted price for the item. Each invoice line also contains a total, usually called an extension, which is the result of multiplying the number ordered by the quoted price.
    - Finally, the footing (bottom) of the invoice contains the invoice total.
    
  
![Figure 1-1: a sample invoice](images/figure-1-1-sample-invoice.JPG)

- KimTay Pet Supplies also must store the following items in the database for each
customer’s invoice:
    - The invoice number, the date the invoice was placed, and the ID of the customer that placed the invoice. The customer’s name, full address, and the ID of the sales rep who represents the customer are stored with the customer information. The name of the sales rep is stored with the sales rep information.
    - The invoice number, the item ID, the quantity ordered, and the quoted price for each invoice line. The item description is stored with the information about items. The result of multiplying the number of units ordered by the quoted price is not stored because the database can calculate it when needed.
- The overall invoice total is not stored. Instead, the database calculates the total whenever an invoice is printed or displayed on the screen.
- Figure 1-2 shws sample data for KimTay Pet Supplies.

![figure 1-2a: sample data for KimTay Pet Supplies customer table](images/figure-1-2a-customer-table.JPG)

![figure 1-2a: sample data for KimTay Pet Supplies sales rep table](images/figure-1-2b-sales-rep-table.JPG)

![figure 1-2a: sample data for KimTay Pet Supplies item table](images/figure-1-2c-items-table.JPG)

![figure 1-2a: sample data for KimTay Pet Supplies invoices and invoice line tables](images/figure-1-2d-invoice-tables.JPG)

- In the SALES_REP table, you see that there are four reps, whose ID values are 05, 10, 15, and 20. The name of sales rep 05 is Susan Garcia. Her street address is 42 Mountain Ln. She lives in Cody, WY, and her postal code is 82414. Her cell phone number is 307-824-1245. Her total commission is \$12,743.16, and her commission rate is 0.04 (four percent).
- In the CUSTOMER table, 12 KimTay Pet Supplies customers are identified with the ID values of 126, 182, 227, 294, 314, 375, 435, 492, 543, 616, 721, and 795. The name of customer number 126 is Joey Smith. This customer’s address is 17 Fourth St in Cody, WY, with a postal code of 82414. The e-mail address of the customer is jsmith17@ example.com. The customer’s current balance is \$80.68, and their credit limit is \$500.00. The value 05 in the REP_ID column indicates that Joey Smith is represented by sales rep 05 (Susan Garcia).
- In the table named ITEM, you see that there are 15 items, whose item ID values are AD72, BC33, CA75, DT12, FM23, FS39, FS42, KH81, LD14, LP73, PF19, QB92, SP91, UF39, and WB49. Item AD72 is a Dog Feeding Station, and KimTay Pet Supplies has 12 units of this item on hand. The Dog Feeding Station item is in the DOG category, and it is located in area B. The price of the Dog Feeding Station is \$79.99. Other categories are BRD (bird), CAT, FSH (fish), and HOR (horse).
- In the table named INVOICES, you see that there are eight invoices which are identified with the numbers 14216, 14219, 14222, 14224, 14228, 14231, 14233, and 14237. Invoice number 14216 was placed on November 15, 2021, by customer 125 (Joey Smith).
- The table named INVOICE_LINE might seem strange at first glance. Why do you need a separate table for the invoice lines? Could they be included in the INVOICES table? The answer is technically yes. You could structure the table named INVOICES as shown in Figure 1-3. Notice that this table contains the same invoices as shown in Figure 1-2, with the same dates and customer ID numbers. In addition, each table row in Figure 1-3 contains all the invoice lines for a given invoice. Examining the second row, for example, you see that invoice 14219 has two invoice lines. One of the invoice lines is for 2 units of item AD72 at \$79.99 each, and the other invoice line is for 4 units of item DT12 at \$39.99 each.

![FIGURE 1-3 Alternative INVOICES table structure](images/figure-1-3-alternative-invoice-tables.JPG)

> **Q & A**
> **Question**: How is the information from Figure 1-2 represented in Figure 1-3?
> Answer: Examine the INVOICE_LINE table shown in Figure 1-2 and note the second and third rows. The second row indicates that there is an invoice line on invoice 14219 for 2 units of item AD72 at \$79.99 each. The third row indicates that there is an invoice line on invoice 14219 for 4 units of item DT12 at \$39.99 each. Thus, the information that you find in Figure 1-3 is represented in Figure 1-2 in two separate rows rather than in one row.

- It might seem inefficient to use two rows to store information that could be represented in one row. There is a problem, however, with the arrangement shown in Figure 1-3 — the table is more complicated. In Figure 1-2, there is a single entry at each location in the table. In Figure 1-3, some of the individual positions within the table contain multiple entries, making it difficult to track the information between columns. In the row for invoice number 14219, for example, it is crucial to know that the AD72 corresponds to the 2 in the QUANTITY column (not to the 4) and that it corresponds to the \$79.99 in the QUOTED_PRICE column (not to the \$39.99). In addition, a more complex table raises practical issues, such as the following:
    - How much room do you allow for these multiple entries?
    - What happens when an invoice has more invoice lines than you have allowed room for?
    - For a given item, how do you determine which invoices contain invoice lines for that item?
- Although none of these problems is unsolvable, they do add a level of complexity that is not present in the arrangement shown in Figure 1-2. In Figure 1-2, there are no multiple entries to worry about, it does not matter how many invoice lines exist for any invoice, and finding every invoice that contains an invoice line for a given item is easy (just look for all invoice lines with the given item number in the ITEM_ID column). In general, this simpler structure is preferable, and that is why invoice lines appear in a separate table.
- To test your understanding of the KimTay Pet Supplies data, use Figure 1-2 to answer the following questions.

> **Q & A**
> **Question**: What are the customer ID values of the customers represented by Susan Garcia?
> **Answer**: 126, 375, 543, and 795. (Look up the REP_ID value of Susan Garcia in the SALES_REP table and obtain the value 05. Then find all customers in the CUSTOMER table that have the value 05 in the REP_ID field.)

> **Q & A**
> **Question**: What is the name of the customer that placed invoice 14222, and what is the name of the sales rep who represents the customer?
> **Answer**: Samantha Smith is the customer, and Richard Miller is the sales rep. (Look up the CUST_ID value in the INVOICES table for invoice 14222 and obtain the ID value 294. Then find the customer in the CUSTOMER table with the CUST_ID value of 294. Using the REP_ID value, which is 10, find the name of the sales rep in the SALES_REP table.)

> **Q & A**
> **Question**: List all items that appear in invoice 14228. For each item, give the description, quantity ordered, and quoted price.
> **Answer**: Item ID: FS42; description: Aquarium (55 Gallon); quantity ordered: 1; and quoted price: \$124.99. Also, item ID: PF19; description: Pump & Filter Kit; quantity ordered: 1; and quoted price: \$74.99. (Look up each INVOICE_LINE table row on which the invoice number is 14228. Each of these rows contains an item ID, quantity ordered, and quoted price. Use the item ID to look up the corresponding item description in the ITEM table.)

> **Q & A**
> **Question**: Why is the QUOTED_PRICE column in the INVOICE_LINE table? Can’t you just use the item ID and look up the price in the ITEM table?
> **Answer**: If the QUOTED_PRICE column did not appear in the INVOICE_LINE table, you would need to obtain the price for an item on an invoice line by looking up the price in the ITEM table. Although this approach is reasonable, it prevents KimTay Pet Supplies from charging different prices to different customers for the same item. Because KimTay Pet Supplies wants the flexibility to quote and charge different prices to different customers, the QUOTED_PRICE column is included in the INVOICE_LINE table. If you examine the INVOICE_LINE table, you will see cases in which the quoted price matches the actual price in the ITEM table, and cases in which it differs. For example, in invoice number 14216, Joey Smith bought three Enclosed Cat Litter Stations, and KimTay Pet Supplies charged only \$37.99 each, not the regular price of \$39.99.

### STAYWELL STUDENT ACCOMMODATION DATABASE

- StayWell finds and manages accommodation for owners of student accommodation in the Seattle area. The company rents out and helps to maintain 1–5-bedroom properties located in two main areas in the city, Columbia City and Georgetown. This is done on behalf of property owners based both in the local area and throughout the United States. Each location is administrated by a different office, StayWell-Columbia City and StayWell-Georgetown.
- StayWell wishes to expand its business. The current model relies on advertisements in student and university publications in print and online, but prospective owners and renters need to contact the offices and speak to an administrator on all matters relating to renting of properties. The office organizes maintenance services for a fee, which is also currently done via email or direct communication.
- StayWell has decided that the best way to increase efficiency and move toward an e-commerce-based business model is to store all the data about the properties, owners, tenants and services in databases. This will mean that the information can be easily accessed. StayWell hopes that these databases can then be used in future projects such asmobile apps and online booking systems.
- The data is split into several tables as described below.
- The OFFICE table shown in Figure 1-4 shows the office number, office location,
address, area, city, state, and ZIP code.

![FIGURE 1-4 Sample data for StayWell offices](images/figure-1-4-staywell-office-table.JPG)

- StayWell is split into two offices to better manage the properties. This management includes communicating with owners about the status and upkeep of their properties. They also facilitate the payment from the properties, meaning that the owners get regular income without having to collect rent in arrears. Offices also advertise properties and place students in appropriate properties, facilitating initial visits and taking deposits. Lastly the office administers the maintenance of the properties, communicating with residents, owners, and maintenance services. This is discussed later.
- StayWell stores information about the owners of each property in the OWNER table, as seen in Figure 1-5. Each owner is identified by a unique owner number that consists of two uppercase letters followed by a three-digit number. For each owner, the table also includes the last name, first name, address, city, state, and ZIP code. Notice the owners are from across the United States. Although some apartments may be owned by a couple or a family, only the primary contact is given.

![FIGURE 1-5 Sample data for the owners of StayWell properties](images/figure-1-5-staywell-owners-table.JPG)

- Each property at each location is identified by a property ID, as seen in Figure 1-6. Each property also includes the office number that manages the property, address, floor size, the number of bedrooms, the number of floors, monthly rent per property, and the owner number. The property ID is an integer unique for each property.

![FIGURE 1-6 Sample data for StayWell properties](images/figure-1-6-staywell-properties-table.JPG)

-It might at first seem reasonable to include property IDs in the OWNER table, as it would only add one more column. However, if you look at the tables, you notice that there are more properties than owners because some owners have more than one property managed by StayWell. If the OWNER table included the property codes, this would require some entries to have more than one property ID. This would either require multiple property columns or require single rows to contain multiple data entries, creating issues in cross-referencing.
- StayWell provides maintenance services across the properties in the two areas; this is shown in Figure 1-7. The SERVICE_CATEGORY table includes details of these services. The CATEGORY_NUM provides a unique number for the service, and
CATEGORY_DESCRIPTION shows what the service is.

![FIGURE 1-7 Sample category data for StayWell maintenance services](images/figure-1-7-staywell-service-category-table.JPG)

- The SERVICE_REQUEST, as shown in Figure 1-8, table shows requests that residents have put into the offices for maintenance. Each row contains a unique service ID number, the property ID, and the category relating to Figure 1-7. For example, the first line shows the unique service ID, followed by the property ID, which is 11. Looking at the PROPERTY table, we can see that this is 9531 Sherwood Rd, and by referencing the office number we can see that this is managed by StayWell-Georgetown. The table includes details of the request, along with the current status. The estimated time to complete the service is included, plus the actual amount of time and the date of the action to be taken, where applicable.

![FIGURE 1-8 Sample service request category](images/figure-1-8-staywell-service-request-table.JPG)

- The RESIDENTS database, as shown in Figure 1-9, includes details about the residents living in each property. The RESIDENT column includes the first name and last name for each of the residents, along with a resident ID. The PROPERTY_ID is the unique identification number of the property in which they are staying.

![FIGURE 1-9 Sample data for StayWell residents](images/figure-1-9-staywell-residents-table.JPG)

### Module Summary

- KimTay Pet Supplies is an organization whose information requirements include sales reps, customers, items, invoices, and invoice lines.
- StayWell Student Accommodation is an organization whose information requirements include management offices, property details, owners, residents, and services requests.

### Key Term

- database

### Case Exercises

#### KimTay Pet Supplies

- Answer each of the following questions using the KimTay Pet Supplies data shown in Figure 1-2. No computer work is required.

> **Q-1**: List the first and last names of all customers that have a credit limit above, but not including,$500
> 
> **Answer**: Billy Rufton, James Gonzalez, Angie Hendricks, Leslie Smith

> **Q-2**: List the invoice numbers for invoices placed by customer ID 435 on November 18, 2021.
> 
> **Answer**: 14228, 14233

> **Q-3**: List the item ID, item description, and on-hand value for each item in category HOR. (Hint: On-hand value is the result of multiplying the number of units on hand by the price.)
> 
> **Answer**:
> | item ID | item description       | on-hand value  |
> | ---     | ---                    | ---            |
> | FM23    | Fly Mask with Ears     | $(41*24.95)    |
> | FS39    | Folding Saddle Stand   | $(12*39.99)    |
> | QB92    | Quilted Stable Blanket | $(32*119.99)   |
> | WB49    | Insulated Water Bucket | $(34*79.99)    |

> **Q-4**: List the item ID and item description of all items that are in category DOG.
> 
> **Answer**:
> | item ID | item description         |
> | ---     | ---                      |
> | AD72    | Dog Feeding Station      |
> | DT12    | Dog Toy Gift Set         |
> | LD14    | Locking Small Dog Door   |
> | LP73    | Large Pet Carrier        |
> | UF39    | Underground Fence System |

> **Q-5**: How many customers have a balance that exceeds their credit limit?
> 
> **Answer**: 1  Customer. Customer 375 (Melanie, Jackson).

> **Q-6**: What is the item ID, description, and price of the least expensive item in the database?
> 
> **Answer**:
> | item ID | description            | price          |
> | ---     | ---                    | ---            |
> | KH81    | Wild Bird Food (25 lb) | $19.99         |

> **Q-7**: For each invoice, list the invoice number, invoice date, customer ID, and customer first and last names.
> 
> **Answer**:
> | Invoice number | invoice date | customer ID | customer first and last names|
> | ---   | ---        | --- | ---            |
> | 14216 | 11/15/2021 | 126 | Joey Smith     |  
> | 14219 | 11/15/2021 | 227 | Sandra Pincher |
> | 14222 | 11/16/2021 | 294 | Samantha Smith |
> | 14224 | 11/16/2021 | 182 | Billy Rufton   |
> | 14228 | 11/18/2021 | 435 | James Gonzalez |
> | 14231 | 11/18/2021 | 126 | Joey Smith     |
> | 14233 | 11/18/2021 | 435 | James Gonzalez |
> | 14237 | 11/19/2021 | 616 | Sally Cruz     |

> **Q-8**: For each invoice placed on November 16, 2021, list the invoice number, customer ID, and customer first and last names.
> 
> **Answer**:
> | Invoice number | customer ID | customer first and last names| 
> | ---   | --- | ---            |
> | 14222 | 294 | Samantha Smith |
> | 14224 | 182 | Billy Rufton   |

> **Q-9**: 
> List the sales rep ID, and first and last names, for every sales rep who represents at least one customer with a credit limit of $1,000.
> 
> **Answer**:
> | sales rep ID | first and last names |
> | --- | ---            | 
> | 15  | James Gonzalez | 
> | 10  | Leslie Smith   | 

> **Q-10**: For each invoice placed on November 15, 2021, list the invoice number, item ID, item description, and category for each item ordered.
> 
> **Answer**:
> | Invoice number | Item ID | Item description | Category |
> | ---   | ---  | ---                          | --- |
> | 14216 | CA75 | Enclosed Cat Litter Station  | CAT |
> | 14219 | AD72 | Dog Feeding Station          | DOG |
> | 14219 | DT12 | Dog Toy Gift Set             | DOG |

- Critical Thinking
> **Q-1**: KimTay Pet Supplies needs to be able to contact customers when problems arise concerning an invoice. What other types of data could KimTay include in the CUSTOMER table to assist in contacting customers?
> 
> **Answer**: Phone number

#### StayWell Student Accomodation

Answer each of the following questions using the StayWell data shown in Figures 1-4
through 1–9. No computer work is required.

> **Q-1.** List the owner number, last name, and first name of every property owner.
> **Answer**:
> 
> | owner number | last name | first name |
> | --- | --- | --- |
> | MO100 | Moore | Elle-May | 
> | PA101 | Patel | Makesh |
> | AK102 | Aksoy | Ceyda | 
> | CO103 | Cole | Meerab |
> | KO104 | Kowalczyk | Jakub |
> | SI105 | Sims | Haydon |
> | BU106 | Burke | Ernest |
> | RE107 | Redman | Seth |
> | LO108 | Lopez | Janine |
> | BI109 | Bianchi | Nicole |
> | JO110 | Jones | Ammarah |

> **Q-2.** List the last name and first name of every owner located in Seattle.
> 
> **Answer**:
> | last name | first name |
> | --- | --- |
> | Patel | Makesh |
> | Aksoy | Ceyda |
> | Redman | Seth |
> | Jones | Ammarah |

> **Q-3.** List the property ID for each condo that is smaller than 1,600 square feet.
> 
> **Answer**: 1, 3, 5, 9, 11

> **Q-4.** List the last name, first name, and city of every owner who owns more than one property in the database.
> 
> **Answer**:
> | last name | first name | city |
> | --- | --- | --- |
> | Kowalczyk | Jakub | Bellingham |

> **Q-5.** List the last name, first name, and city of every owner with a property that has a monthly rent of less than $1,400 per month.
> 
> **Answer**:
> | last name | first name | city |
> | --- | --- | --- |
> | Bianchi | Nicole | New York |
> | Sims | Haydon | Portland |
> | Patel | Makesh | Seattle |
> | Jones | Ammarah | Seattle |

> **Q-6.** List all the residents staying at 782 Queen Ln.
> 
> **Answer**: Milosz Polansky, Ashanti Lucas, Randy Woodrue

> **Q-7.** How many properties have two floors?
> 
> **Answer**: 5 (Property ID 2, 6, 7, 8, and 12)

> **Q-8.** How many owners live outside of Washington state (WA)?
> 
> **Answer**: 4 owners. (Moore Elle-May, Sims Haydon, Burke Ernest, Bianchi Nicole)

> **Q-9.** List the owner’s last and first names and property IDs for each property that has a scheduled or open service request.
> 
> **Answer**:
> | Last name | First name | Property ID |
> | --- | --- | --- |
> | Redman | Seth | 11 |
> | Burke | Ernest | 1 |
> | Moore | Elle-May | 6 |
> | Aksoy | Ceyda | 2 |
> | Kowalczyk | Jakub | 8 |
> | Kowalczyk | Jakub | 4 |
> | Patel | Makesh | 9 |
> | Redman | Seth | 12 |

> **Q-10.** List the property ID and square footage for each property that has a maintenance service request.
> 
> **Answer**:
> | Property ID | Square footage |
> | --- | --- |
> | 11 | 1,075 |
> | 1 | 1,600 |
> | 6 | 2,125 |
> | 2 | 2,100 |
> | 8 | 2,700 |
> | 4 | 1,750 |
> | 9 | 700 | 
> | 12 | 1,400 |

> **Q-11.** List the property ID and office number for all service requests for which the estimated number of hours is greater than 5.
> 
> **Answer**:
> | Property ID | Office number |
> | --- | --- |
> | 10 | 2 |
> | 8 | 2 |

> **Q-12.** What is the average rent for all three-bedroom properties?
> 
> **Answer**:
>  (1400 + 1650 + 1700 + 1600 + 1700) / 5


## Module 2: DATABASE DESIGN FUNDAMENTALS

### INTRODUCTION

- **Database design**: The process of determining the particular tables and columns that comprise a database, and identify the relationships between the tables.

### DATABASE CONCEPTS

####  Relational Databases

- A **relational database** is a collection of tables like the ones you examined for KimTay Pet Supplies in Module 1. Formally, these tables are called relations, and this is how this type of database gets its name.

![FIGURE 2-1 Sample data for KimTay Pet Supplies](./images/figure-2-1-sample-data-for-kimtay-pet-supplies.JPG)

![FIGURE 2-1 Sample data for KimTay Pet Supplies b (Continued)](./images/figure-2-1b-sample-data-for-kimtay-pet-supplies.continued.JPG)

> **HELPFUL HINT**: 
> - The names of columns and tables in this text follow a common naming convention in which column names use uppercase letters and replace spaces between words with an underscore (_). For example, KimTay Pet Supplies uses the column named FIRST_NAME to store first names and the column named INVOICE_NUM to store invoice numbers.

####  Entities, Attributes, and Relationships

- An **entity** is like a noun; it is a person, place, thing, or event. For example, the entities of interest to KimTay Pet Supplies are customers, invoices, and sales reps. The entities that are of interest to a school include students,faculty, and classes; a real estate agency is interested in clients, houses, and agents; and a used car dealer is interested in vehicles, customers, and manufacturers.
- An **attribute** is a property of an entity. The term is used here exactly as it is used in everyday English. For example, for the entity person, the list of attributes might include such things as eye color and height. For KimTay Pet Supplies, the attributes of interest for the entity customer are first name, last name, address, city, and so on. For the entity faculty at a school, the attributes are faculty ID, name, office number, phone, and so on. For the entity vehicle at a car dealership, the attributes are the vehicle identification number, model, color, year, and so on.
- A **relationship** is the association between entities. For example, at KimTay Pet Supplies there is an association between customers and sales reps. A sales rep is associated with all of his or her customers, and a customer is associated with his or her sales rep. Technically, you say that a sales rep is *related* to all of his or her customers, and a customer is *related* to his or her sales rep.
- The relationship between sales reps and customers is an example of a **one-to-many relationship** because one sales rep is associated with many customers, but each customer is associated with only one sales rep. In this type of relationship, the word *many* is used in a way that is different from everyday English; it might not always mean a large number. In this context, for example, the term many means that a sales rep might be associated with *any* number of customers. That is, one sales rep can be associated with zero, one, or more customers.
> **Question**: 
> - How does a relational database handle entities, attributes of entities, and relationships between entities? 
> **Answer**: 
> - Entities and attributes are fairly simple. Each entity has its own table. In the KimTay Pet Supplies database, there is one table for sales reps, one table for customers, and so on. The attributes of an entity become the columns in the table. In the table for sales reps, for example, there is a column for the sales rep ID, a column for the sales rep’s first name, and so on.
> **Question**: 
> - What about relationships? At KimTay Pet Supplies, there is a one-to-many relationship between sales reps and customers, meaning each sales rep is related to the many customers that he or she represents, and each customer is related to the one sales rep who represents the customer. How is this relationship implemented in a relational database?
> **Answer**: 
> - If you want to determine the name of the sales rep who represents Billy Rufton (customer ID 182), you would locate the row for Billy Rufton in the CUSTOMER table and determine that the value for REP_ID is 10. Then you would look for the row in the SALES_REP table in which the REP_ID is 10. The one rep with REP_ID 10 is Richard Miller, who represents Billy Rufton.
> - On the other hand, if you want to determine the names of all the customers of the rep named Susan Garcia, you locate the row for Susan Garcia in the SALES_REP table and determine that the value in the REP_ID column is 05. Then you look for all the rows in the CUSTOMER table on which the REP_ID is 05. After identifying Susan Garcia’s rep number, you find that the many customers she represents are numbered 125 (Joey Smith), 375 (Melanie Jackson), 543 (Angie Hendricks), and 795 (Randy Blacksmith).
> - You implement these relationships by having common columns in two or more tables. The REP_ID column in the SALES_REP table and the REP_ID column in the CUSTOMER table are used to implement the relationship between sales reps and customers. Given a sales rep, you can use these columns to determine all the customers that he or she represents; given a customer, you can use these columns to find the sales rep who represents the customer.
> - In this context, a relation is essentially a two-dimensional table. You can see that certain restrictions are placed on relations. Each column has a unique name, and entries within each column should match this column name. For example, if the column name is CREDIT_LIMIT, all entries in that column must be credit limits. In addition, each row should be unique — when two rows are identical, the second row does not provide any new information. For maximum flexibility, the order of the columns and rows should be immaterial. Finally, the table’s design should be as simple as possible by restricting each position to a single entry and by preventing multiple entries (also called repeating groups) in an individual location in the table. Figure 2-2 shows a table design that includes repeating groups.
> 
> ![FIGURE 2-2 Table with repeating groups](images/figure-2-2-table-with-repeating-groups.JPG)
> 
> - Figure 2-3 shows a better way to represent the same information shown in Figure 2-2. In Figure 2-3, every position in the table contains a single value.
> 
> ![FIGURE 2-3 INVOICES table without repeating groups](images/figure-2-3-invoices-table-without-repeating-groups.JPG)
> 
> - When you remove the repeating groups from Figure 2-2, all of the rows in Figure 2-3 are single-valued. This structure is formally called a relation. A relation is a two-dimensional table in which the entries in the table are single-valued (each location in the table contains a single entry), each column has a distinct name, all values in the column match this name, the order of the rows and columns is immaterial, and each row contains unique values. A relational database is a collection of relations.

> **HELPFUL HINT**:
> - Rows in a table (relation) are also called records or tuples. Columns in a table (relation) are also called fields or attributes. This text uses the terms tables, columns, and rows unless the more formal terms of relation, attributes, and tuples are necessary for clarity.

- There is a commonly accepted shorthand representation to show the tables and columns in a relational database: for each table, you write the name of the table and then within parentheses list all of the columns in the table. In this representation, each table appears on its own line. Using this method, you represent the KimTay Pet Supplies database as follows:

> SALES_REP (REP_ID, FIRST_NAME, LAST_NAME, ADDRESS, CITY, STATE, POSTAL, CELL_PHONE, COMMISSION, RATE)

> CUSTOMER (CUST_ID, FIRST_NAME, LAST_NAME, ADDRESS, CITY, STATE, POSTAL, EMAIL, BALANCE, CREDIT_LIMIT, REP_ID)

> INVOICES (INVOICE_NUM, INVOICE_DATE, CUST_ID)

> INVOICE_LINE (INVOICE_NUM, ITEM_ID, QUANTITY, QUOTED_PRICE)

> ITEM (ITEM_ID, DESCRIPTION, ON_HAND, CATEGORY, LOCATION, PRICE)

- Notice that some tables contain columns with duplicate names. For example, the REP_ID column appears in both the SALES_REP table and the CUSTOMER table. Suppose a situation existed wherein someone, or the **database management system (DBMS)** might confuse the two columns. Note the DBMS is a set of programs that allows users to store, manipulate, and retrieve data efficiently. For example, if you write REP_ID, it is not clear which REP_ID column you want to use. You need a mechanism for indicating the REP_ID column to which you are referring. One common approach to solving this problem is to write both the table name and the column name, separated by a period. Thus, you reference the REP_ID column in the CUSTOMER table as CUSTOMER.REP_ID, and you reference the REP_ID column in the SALES_REP table as SALES_REP.REP_ID. Technically, when you reference columns in this format, you say that you qualify the names. It is always acceptable to qualify column names, even when there is no potential for confusion. If confusion might arise, however, it is *essential* to qualify column names.

### FUNCTIONAL DEPENDENCE

- To illustrate functional dependence, suppose that the SALES_REP table for KimTay Pet Supplies is structured as shown in Figure 2-4. The only difference between the
SALES_REP table shown in Figure 2-4 and the one shown in module 1 is the addition of an extra column named PAY_CLASS.

![FIGURE 2-4 SALES_REP table with a PAY_CLASS column](images/figure-2-4-sales_rep-table-with-a-pay_class-column.JPG)

- Suppose that one of the policies at KimTay Pet Supplies is that all sales reps in any given pay class earn their commissions at the same rate. To describe this situation, you could say that a sales rep’s pay class *determines* his or her commission rate. Alternatively, you could say that a sales rep’s commission rate *depends* on his or her pay class. This phrasing uses the words *determines* and *depends* on in the same way that you describe functional dependency. If you wanted to be formal, you would precede either expression with the word functionally. For example, you might say, "A sales rep’s pay class functionally
determines his or her commission rate," and "A sales rep’s commission rate functionally depends on his or her pay class." You can also define functional dependency by saying that when you know a sales rep’s pay class, you can determine his or her commission rate.
- In a relational database, column B is functionally dependent on another column (or a collection of columns), A, if at any point in time a value for A determines a single value for B. You can think of this as follows: When you are given a value for A, do you know that you can find a single value for B? If so, B is functionally dependent on A (often written as A → B). You also can say that A functionally determines B.
- At KimTay Pet Supplies, is the LAST_NAME column in the SALES_REP table functionally dependent on the REP_ID column? Yes, it is. If you are given a value for REP_ID, such as 10, there is a single LAST_NAME, Miller, associated with it. This is represented as: REP_ID → LAST_NAME

> **Q & A**
> **Question**: In the CUSTOMER table, is LAST_NAME functionally dependent on REP_ID?
> **Answer**: No. Given the REP_ID 10, for example, you do not find a single customer last name because the sales rep with REP_ID 10 appears on more than one row in the table because he has four customers.

> **Q & A**
> **Question**: In the INVOICE_LINE table, is QUANTITY functionally dependent on INVOICE_NUM?
> **Answer**: No. An INVOICE_NUM might be associated with several items in an invoice, so having just an INVOICE_NUM does not provide enough information.

> **Q & A**
> **Question**: Is QUANTITY functionally dependent on ITEM_ID?
> **Answer**: No. Again, just as with INVOICE_NUM, an item ID might be associated with more than one invoice, so ITEM_ID does not provide enough information.

> **Q & A**
> **Question**: On which columns in the INVOICE_LINE table is QUANTITY functionally dependent?
> **Answer**: To determine a value for QUANTITY, you need both an invoice number and an item ID. In other words, QUANTITY is functionally dependent on the combination (formally called the concatenation) of INVOICE_NUM and ITEM_ID. That is, given an invoice number and an item ID, you can find a single value for QUANTITY.

- At this point, a question naturally arises: How do you determine functional dependencies? Can you determine them by looking at sample data, for example? The answer is no.
- Consider the SALES_REP table in Figure 2-5, in which last names are unique. It is very tempting to say that LAST_NAME functionally determines ADDRESS, CITY, STATE, and POSTAL (or equivalently that ADDRESS, CITY, STATE, and POSTAL are all functionally dependent on LAST_NAME). After all, given the last name of a rep, you can find the single complete address; however, this is not always the case. What would happen if multiple sales reps had the same last name?

![FIGURE 2-5 SALES_REP table](images/figure-2-5-sales_rep-table.JPG)

- What would happen if the last name of rep 20 was also Garcia? You would have the
situation illustrated in Figure 2-6. Because there are now two reps with the last name of Garcia, you can no longer find a single address using a rep’s last name—you were misled by the original data. The only way to determine functional dependencies is to examine the user’s policies. This process can involve discussions with users, an examination of user documentation, and so on. For example, if managers at KimTay Pet Supplies have a policy not to hire two reps with the same last name, then LAST_NAME would indeed determine the other columns.

![FIGURE 2-6 SALES_REP table with two reps named Garcia](images/figure-2-6-sales_rep-table-with-two-reps-named-garcia.JPG)

### PRIMARY KEYS

- In the simplest terms, the **primary key** is the unique identifier for a table. For example, the REP_ID column is the unique identifier for the SALES_REP table. Given a rep ID in the table, such as 10, there is only one row on which that rep ID occurs. Thus, the rep ID 10 uniquely identifies a row (in this case, the second row).
- Column A (or a collection of columns) is the primary key for a table if the following is true:
    - Property 1. All columns in the table are functionally dependent on A.
    - Property 2. No subcollection of the columns in A (assuming A is a collection of columns and not just a single column) also has Property 1.
  
> **Q & A**
> **Question**: Is the CATEGORY column the primary key for the ITEM table?
> **Answer**: No, because the other columns are not functionally dependent on CATEGORY. Given the category DOG, for example, you cannot determine an item ID, description, or anything else, because there are several rows on which the category is DOG.

> **Q & A**
> **Question**: Is the CUST_ID column the primary key for the CUSTOMER table?
> **Answer**: Yes, because KimTay Pet Supplies assigns unique customer ID values. A specific customer ID cannot appear on more than one row. Thus, all columns in the CUSTOMER table are functionally dependent on CUST_ID.

> **Q & A**
> **Question**: Is the INVOICE_NUM column the primary key for the INVOICE_LINE table?
> **Answer**: No, because it does not functionally determine either QUANTITY or QUOTED_PRICE.

> **Q & A**
> **Question**: Is the combination of the INVOICE_NUM and ITEM_ID columns the primary key for the INVOICE_LINE table?
> **Answer**: Yes, because you can determine all columns by this combination of columns, and, further, neither the INVOICE_NUM nor the ITEM_ID alone has this property.

> **Q & A**
> **Question**: Is the combination of the ITEM_ID and DESCRIPTION columns the primary key for the ITEM table?
> **Answer**: No. Although it is true that you can determine all columns in the ITEM table by this combination, ITEM_ID alone also has this property.

- You can indicate a table’s primary key with a shorthand representation of a database by underlining the column or collection of columns that comprise the primary key. The complete shorthand representation for the KimTay Pet Supplies database is as follows:

> SALES_REP (<ins>REP_ID</ins>, FIRST_NAME, LAST_NAME, ADDRESS, CITY, STATE, POSTAL, CELL_PHONE, COMMISSION, RATE)

> CUSTOMER (<ins>CUST_ID</ins>, FIRST_NAME, LAST_NAME, ADDRESS, CITY, STATE, POSTAL, EMAIL, BALANCE, CREDIT_LIMIT, REP_ID)

> INVOICES (<ins>INVOICE_NUM</ins>, INVOICE_DATE, CUST_ID)

> INVOICE_LINE (<ins>INVOICE_NUM</ins>, <ins>ITEM_ID</ins>, QUANTITY, QUOTED_PRICE)

> ITEM (<ins>ITEM_ID</ins>, DESCRIPTION, ON_HAND, CATEGORY, LOCATION, PRICE)

> HELPFUL HINT:
> - Sometimes you might identify one or more columns that you can use as a table’s primary key. For example, if the KimTay Pet Supplies database also included an EMPLOYEE table that contains employee numbers and Social Security numbers, either the employee number or the Social Security number could serve as the table’s primary key. In this case, both columns are referred to as candidate keys. Like a primary key, a candidate key is a column or collection of columns on which all columns in the table are functionally dependent—the definition for primary key really defines candidate key as well. From all the candidate keys, you would choose one to be the primary key.

> HELPFUL HINT:
> - According to the definition of a candidate key, a Social Security number is a legitimate primary key. Many databases, such as those that store data about students at a college or university or those that store data about employees at a company, store a person’s Social Security number as a primary key. However, many institutions and organizations are moving away from using Social Security numbers as primary keys because of privacy issues. Instead of using Social Security numbers, many institutions and organizations use unique student ID values or employee numbers as primary keys.

> HELPFUL HINT: 
> - Some institutions prefer to assign values to use as primary keys for items such as customer ID values, item ID values, and student numbers. Others simply let the computer generate the values. In this case, the DBMS simply assigns the next available value. For example, if the database has already assigned customer numbers 1500 through 1936, it assigns the next new customer added to the database the customer number 1937.

### DATABASE DESIGN

- To design a database, you *must* be given a set of requirements that the database must support. The determination of the requirements is part of the process known as **systems analysis**. A systems analyst interviews users, examines existing and proposed documents, and examines organizational policies to determine exactly the type of data needs the database must support. This text does not cover this analysis. Rather, it focuses on how to take the set of requirements that this process produces and determine the appropriate database design.

#### Design Method

To design a database for a set of requirements, complete the following steps:

1. Read the requirements, identify the entities (objects) involved, and name the entities. For example, when the design involves departments and employees, you might use the entity names DEPARTMENT and EMPLOYEE. When the design involves customers and sales reps, you might use the entity names CUSTOMER and SALES_REP.
2. Identify the unique identifiers for the entities you identified in Step 1. For
example, when one of the entities is ITEM, determine what information is
required to uniquely identify each individual item. In other words, what
information does the organization use to distinguish one item from another? For the ITEM entity, the unique identifier for each item might be ITEM_ID; for a CUSTOMER entity, the unique identifier might be CUST_ID. When no unique identifier is available from the data you know about the entity, you need to create one. For example, you might use a unique number to identify items when no item numbers exist.
3. Identify the attributes for all the entities. These attributes become the columns in the tables. It is possible for two or more entities to contain the same attributes.
4. Identify the functional dependencies that exist among the attributes. Ask yourself the following question: If you know a unique value for an attribute, do you also know the unique values for other attributes? For example, when you have the three attributes REP_ID, FIRST_NAME, and LAST_NAME and you know a unique value for REP_ID, do you also know a unique value for FIRST_NAME and LAST_NAME? If so, then FIRST_NAME and LAST_NAME are functionally dependent on REP_ID (REP_ID → FIRST_NAME, LAST_NAME).
5. Use the functional dependencies to identify the tables by placing each attribute with the attribute or minimum combination of attributes on which it is functionally dependent. The attribute(s) for an entity on which all other attributes are dependent is the primary key of the table. The remaining attributes are the other columns in the table. Once you have determined all the columns in the table, you can give the table an appropriate name. Usually the name will be the same as the name you identified for the entity in Step 1.
6. Identify any relationships between tables. In some cases, you might be able to determine the relationships directly from the requirements. It might be clear, for example, that one sales rep is related to many customers and that each customer is related to exactly one sales rep. When it is not, look for matching columns in the tables you created. For example, if both the SALES_REP table and the CUSTOMER table contain a REP_ID column and the values in these columns must match, you know that reps and customers are related. The fact that the REP_ID column is the primary key in the SALES_REP table tells you that the SALES_REP table is the one part of the relationship and the CUSTOMER table is the *many* part of the relationship.

- In the next section, you will apply this process to produce the design for the KimTay Pet Supplies database using the collection of requirements that this database must support.

#### Database Design Requirements

The analyst has interviewed users and examined documents at KimTay Pet Supplies. In the process, the analyst has determined that the database must support the following requirements:
1. For a sales rep, store the sales rep’s ID, first name, last name, street address, city, state, postal code, cell phone number, total commission, and commission rate.
2. For a customer, store the customer’s ID, first name, last name, street address, city, state, postal code, e-mail address, balance, and credit limit. In addition, store the ID, first name, and last name of the sales rep who represents this customer. The analyst has also determined that a sales rep can represent many customers, but a customer must have exactly one sales rep (in other words, a sales rep must represent a customer; a customer cannot be represented by zero or more than one sales reps).
3. For an item, store the item’s ID, description, units on hand, category, the value of the location in which the item is located, and the price. All units of a particular item are stored in the same location.
4. For an invoice, store the invoice number, invoice date, along with the ID, first name, and last name of the customer that placed the invoice, as well as the ID of the sales rep who represents that customer.
5. For each invoice item within an invoice, store the item ID and description, the quantity ordered, and the quoted price. The analyst also obtained the following information concerning invoices:
    <ol style="list-style-type: lower-alpha;">
        <li>There is only one customer per invoice.</li>
        <li>On a given invoice, there is at most one line item for a given item. For example, item AD72 cannot appear on several lines within the same invoice.</li>
        <li>The quoted price might differ from the actual price when the sales rep discounts a certain item on a specific invoice.</li>
    </ol>

#### Database Design Process Example

The following steps apply the design process to the requirements for KimTay Pet Supplies to produce the appropriate database design:
- **Step 1**: There appear to be four entities: sales reps, customers, items, and invoices. The names assigned to these entities are SALES_REP, CUSTOMER, ITEM, and INVOICES, respectively.
- **Step 2**: From the collection of entities, review the data and determine the unique identifier for each entity. For the SALES_REP, CUSTOMER, ITEM, and INVOICES entities, the unique identifiers are the rep ID, customer ID, item ID, and invoice number, respectively. These unique identifiers are named REP_ID, CUST_ID, ITEM_ID, and INVOICE_NUM, respectively.
- **Step 3**: The attributes mentioned in the first requirement all refer to sales reps. The specific attributes mentioned in the requirement are the sales rep’s ID, first name, last name, street address, city, state, postal code, cell phone number, total commission, and commission rate. Assigning appropriate names to these attributes produces the following list:
    <ul style="list-style-type: none">
        <li>REP_ID</li>
        <li>FIRST_NAME</li>
        <li>LAST_NAME</li>
        <li>ADDRESS</li>
        <li>CITY</li>
        <li> STATE</li>
        <li>POSTAL</li>
        <li>CELL_PHONE</li>
        <li>COMMISSION</li>
        <li>RATE</li>
    </ul>
- The attributes mentioned in the second requirement refer to customers. The specific attributes are the customer’s ID, first name, last name, street address, city, state, postal code, e-mail address, balance, and credit limit. The requirement also mentions the rep ID, first name, and last name of the sales rep who represents this customer. Assigning appropriate names to these attributes produces the following list:
    <ul style="list-style-type: none">
        <li>CUST_ID</li>
        <li>FIRST_NAME</li>
        <li>LAST_NAME</li>
        <li>ADDRESS</li>
        <li>CITY</li>
        <li>STATE</li>
        <li>POSTAL</li>
        <li>EMAIL</li>
        <li>BALANCE</li>
        <li>CREDIT_LIMIT</li>
        <li>REP_ID</li>
        <li>REP_FIRST_NAME</li>
        <li>REP_LAST_NAME</li>
    </ul>
> **HELPFUL HINT**
> Note above that the names given to the first and last name for each customer is FIRST_NAME and LAST_NAME, similar to the names given to represent the first and last names of each sales rep when determining the list of attributes for the entity SALES_REP. However, in this case we are wanting to include both the first and last names for the customer and the first and last names for the sales rep, in the same list pertaining to the entity CUSTOMER. When naming attributes associated with a single entity, in this case CUSTOMER, no two attributes can have the same name. Therefore, we cannot use FIRST_NAME and LAST_NAME for the first and last name for the sales rep (as attributes associated with the entity CUSTOMER) and use FIRST_NAME and LAST_NAME as the first and last name of a customer. Instead, we can use REP_FIRST_NAME and REP_LAST_NAME to represent the first and last name of the sales rep as attributes related to CUSTOMER. You will see as we continue to progress through the design process that this will be remedied and not be an issue. However, it is important to note at this juncture. In summary, two attributes can have the same name if they refer to different entities such as using FIRST_NAME and LAST_NAME as attributes for the entities SALES_REP and CUSTOMER independently; however, when associated with a single entity, no two attributes can have the same name.

- There are attributes named FIRST_NAME, LAST_NAME, ADDRESS, CITY, STATE, and POSTAL for sales reps as well as attributes named FIRST_NAME, LAST_NAME, ADDRESS, CITY, STATE, and POSTAL for customers. To distinguish these attributes in the final collection, follow the name of the attribute by the name of the corresponding entity in parentheses. For example, the address for a sales rep is ADDRESS (SALES_REP) and the address for a customer is ADDRESS (CUSTOMER).
- The attributes mentioned in the third requirement refer to items. The specific attributes are the item’s ID, description, units on hand, category, value of the location in which the item is located, and price. Assigning appropriate names to these attributes produces the following list:
    <ul style="list-style-type: none">
        <li>ITEM_ID</li>
        <li>DESCRIPTION</li>
        <li>ON_HAND</li>
        <li>CATEGORY</li>
        <li>LOCATION</li>
        <li>PRICE</li>
    </ul>
- The attributes mentioned in the fourth requirement refer to invoices. The specific attributes include the invoice number, invoice date, customer’s ID, first and last names of who placed the invoice, and ID of the sales rep who represents the customer. Assigning appropriate names to these attributes produces the following list:
    <ul style="list-style-type: none">
        <li>INVOICE_NUM</li>
        <li>INVOICE_DATE</li>
        <li>CUST_ID</li>
        <li>FIRST_NAME</li>
        <li>LAST_NAME</li>
        <li>REP_ID</li>
    </ul>
- The specific attributes associated with the statement in the requirements concerning invoice line items are the invoice number (to determine the invoice to which the line item corresponds), item ID, description, quantity ordered, and quoted price. If the quoted price must be the same as the price, you could simply call it PRICE. According to requirement 5c, however, the quoted price might differ from the price, so you must add the quoted price to the list. Assigning appropriate names to these attributes produces the following list:
    <ul style="list-style-type: none">
        <li>INVOICE_NUM</li>
        <li>ITEM_ID</li>
        <li>DESCRIPTION</li>
        <li>QUANTITY</li>
        <li>QUOTED_PRICE</li>
    </ul>
- The complete list grouped by entity is as follows:
    <ul style="list-style-type: none">
        <li><b>SALES_REP</b></li>
        <li>REP_ID</li>
        <li>FIRST_NAME (SALES_REP)</li>
        <li>LAST_NAME (SALES_REP)</li>
        <li>ADDRESS (SALES_REP)</li>
        <li>CITY (SALES_REP)</li>
        <li>STATE (SALES_REP)</li>
        <li>POSTAL (SALES_REP)</li>
        <li>CELL_PHONE</li>
        <li>COMMISSION</li>
        <li>RATE</li>
    </ul>

     <ul style="list-style-type: none">
        <li><b>CUSTOMER</b></li>
        <li>CUST_ID</li>
        <li>FIRST_NAME (CUSTOMER)</li>
        <li>LAST_NAME (CUSTOMER)</li>
        <li>ADDRESS (CUSTOMER)</li>
        <li>CITY (CUSTOMER)</li>
        <li>STATE (CUSTOMER)</li>
        <li>POSTAL (CUSTOMER)</li>
        <li>EMAIL</li>
        <li>BALANCE</li>
        <li>CREDIT_LIMIT</li>
        <li>REP_ID</li>
        <li>REP_FIRST_NAME</li>
        <li>REP_LAST_NAME</li>
    </ul>

    <ul style="list-style-type: none">
        <li><b>ITEM_ID</b></li>
        <li>DESCRIPTION</li>
        <li>ON_HAND</li>
        <li>CATEGORY</li>
        <li>LOCATION</li>
        <li>PRICE</li>
    </ul>

    <ul style="list-style-type: none">
        <li><b>INVOICES</b></li>
        <li>INVOICE_NUM</li>
        <li>INVOICE_DATE</li>
        <li>CUST_ID</li>
        <li>FIRST_NAME</li>
        <li>LAST_NAME</li>
        <li>REP_ID</li>
    </ul>

- For invoice line items within an invoice:
    <ul style="list-style-type: none">
        <li>INVOICE_NUM</li>
        <li>ITEM_ID</li>
        <li>DESCRIPTION</li>
        <li>QUANTITY</li>
        <li>QUOTED_PRICE</li>
    </ul>

- **Step 4**: The fact that the unique identifier for sales reps is the rep ID gives the following functional dependencies:
<dl>
    <dd>
        FIRST_NAME (SALES_REP), LAST_NAME (SALES_REP), ADDRESS (SALES_REP), CITY (SALES_REP), STATE (SALES_REP), POSTAL (SALES_REP), CELL_PHONE, COMMISSION, RATE
    </dd>
</dl>

- This notation indicates that the FIRST_NAME (SALES_REP), LAST_NAME (SALES_REP), ADDRESS (SALES_REP), CITY (SALES_REP), STATE (SALES_REP), POSTAL (SALES_REP), CELL_PHONE, COMMISSION, and RATE are all functionally dependent on REP_ID.
- The fact that the unique identifier for customers is the customer ID gives the following functional dependencies:
<dl>
    <dd>
        CUST_ID → FIRST_NAME (CUSTOMER), LAST_NAME (CUSTOMER), ADDRESS (CUSTOMER), CITY (CUSTOMER), STATE (CUSTOMER), POSTAL (CUSTOMER), EMAIL, BALANCE, CREDIT_LIMIT, REP_ID, REP_FIRST_NAME, REP_LAST_NAME
    </dd>
</dl>

>**Q & A**
> **Question**: Do you really need to include the first name and last name of a sales rep in the list of attributes determined by the customer ID?
> **Answer**: There is no need to include them in this list because they both can be determined from the sales rep ID and are already included in the list of attributes determined by REP_ID.

- Thus, the functional dependencies for the CUSTOMER entity are as follows:

<dl>
    <dd>
        CUST_ID → FIRST_NAME (CUSTOMER), LAST_NAME (CUSTOMER), ADDRESS (CUSTOMER), CITY (CUSTOMER), STATE (CUSTOMER), POSTAL (CUSTOMER), EMAIL, BALANCE, CREDIT_LIMIT, REP_ID
    </dd>
</dl>

- The fact that the unique identifier for items is the item number gives the following functional dependencies:

<dl>
    <dd>
        CUST_ID → FIRST_NAME (CUSTOMER), LAST_NAME (CUSTOMER), ADDRESS (CUSTOMER), CITY (CUSTOMER), STATE (CUSTOMER), POSTAL (CUSTOMER), EMAIL, BALANCE, CREDIT_LIMIT, REP_ID
    </dd>
</dl>

The fact that the unique identifier for invoices is the invoice number gives the
following functional dependencies:

<dl>
    <dd>
        INVOICE_NUM → INVOICE_DATE, CUST_ID, FIRST_NAME (CUSTOMER), LAST_NAME(CUSTOMER), REP_ID
    </dd>
</dl>

>**Q & A**
> **Question**: Do you really need to include the first name and last name of a customer and the ID of the customer’s rep in the list of attributes determined by the invoice number?
> **Answer**: There is no need to include the customer’s first and last names and the rep ID in this list because you can determine them from the customer ID and they are already included in the list of attributes determined by CUST_ID.

- The functional dependencies for the INVOICES entity are as follows:
  
<dl>
    <dd>
        INVOICE_NUM → INVOICE_DATE, CUST_ID
    </dd>
</dl>

- The final attributes to be examined are those associated with the invoice line items within the invoice: ITEM_ID, DESCRIPTION, QUANTITY, and QUOTED_PRICE.

>**Q & A**
> **Question**: Why are QUANTITY and QUOTED_PRICE not included in the list of attributes determined by the invoice number?
> **Answer**: There is no need to include them in this list because they both can be determined from the sales rep ID and are already included in the list of attributes determined by REP_ID.

- Thus, the functional dependencies for the CUSTOMER entity are as follows:

<dl>
    <dd>
        CUST_ID → FIRST_NAME (CUSTOMER), LAST_NAME (CUSTOMER), ADDRESS (CUSTOMER), CITY (CUSTOMER), STATE (CUSTOMER), POSTAL (CUSTOMER), EMAIL, BALANCE, CREDIT_LIMIT, REP_ID
    </dd>
</dl>

- The fact that the unique identifier for items is the item number gives the following functional dependencies:

<dl>
    <dd>
        ITEM_ID → DESCRIPTION, ON_HAND, CATEGORY, LOCATION, PRICE
    </dd>
</dl>

The fact that the unique identifier for invoices is the invoice number gives the following functional dependencies:

<dl>
    <dd>
        INVOICE_NUM → INVOICE_DATE, CUST_ID, FIRST_NAME (CUSTOMER), LAST_NAME(CUSTOMER), REP_ID
    </dd>
</dl>

>**Q & A**
> **Question**: Do you really need to include the first name and last name of a customer and the ID of the customer’s rep in the list of attributes determined by the invoice number?
> **Answer**: There is no need to include the customer’s first and last names and the rep ID in this list because you can determine them from the customer ID and they are already included in the list of attributes determined by CUST_ID.

- The functional dependencies for the INVOICES entity are as follows:
  
<dl>
    <dd>
        INVOICE_NUM → INVOICE_DATE, CUST_ID
    </dd>
</dl>

The final attributes to be examined are those associated with the invoice line items within the invoice: ITEM_ID, DESCRIPTION, QUANTITY, and QUOTED_PRICE.

>**Q & A**
> **Question**: Why are QUANTITY and QUOTED_PRICE not included in the list of attributes determined by the invoice number?
> **Answer**: To uniquely identify a particular value for QUANTITY or QUOTED_PRICE, INVOICE_NUM alone is not sufficient, because there can be multiple items purchased on a single invoice. Therefore, it requires the combination of INVOICE_NUM and ITEM_ID.

- The following shorthand representation indicates that the combination of INVOICE_NUM and ITEM_ID functionally determines QUANTITY and QUOTED_PRICE:

<dl>
    <dd>
        INVOICE_NUM, ITEM_ID → QUANTITY, QUOTED_PRICE
    </dd>
</dl>

>**Q & A**
> **Question**: Does DESCRIPTION need to be included in this list?
> **Answer**: No, because DESCRIPTION can be determined by the ITEM_ID alone, and it already appears in the list of attributes dependent on the ITEM_ID.

- The complete list of functional dependencies is as follows:

<dl>
    <dd>
        REP_ID → FIRST_NAME (SALES_REP), LAST_NAME (SALES_REP), ADDRESS (SALES_REP),CITY (SALES_REP), STATE (SALES_REP), POSTAL (SALES_REP), CELL_PHONE,COMMISSION, RATE
    </dd>
</dl>

<dl>
    <dd>
        CUST_ID → FIRST_NAME (CUSTOMER), LAST_NAME (CUSTOMER), ADDRESS (CUSTOMER), CITY (CUSTOMER), STATE (CUSTOMER), POSTAL (CUSTOMER), EMAIL, BALANCE, CREDIT_LIMIT, REP_ID
    </dd>
</dl>

<dl>
    <dd>
        ITEM_ID → DESCRIPTION, ON_HAND, CATEGORY, LOCATION, PRICE
    </dd>
</dl>

<dl>
    <dd>
        INVOICE_NUM → INVOICE_DATE, CUST_ID
    </dd>
</dl>

<dl>
    <dd>
        INVOICE_NUM, ITEM_ID → QUANTITY, QUOTED_PRICE
    </dd>
</dl>

- **Step 5**: Using the functional dependencies, you can create tables with the attribute(s) to the left of the arrow being the primary key and the attribute(s) to the right of the arrow being the other columns. For relations corresponding to those entities identified in Step 1, you can use the name you already determined. Because you did not identify any entity that had a unique identifier that was the combination of INVOICE_NUM and ITEM_ID, you need to assign a name to the table whose primary key consists of these two columns. Because this table represents the individual lines within an invoice, the name INVOICE_LINE is a good choice. The final collection of tables is as follows:

<dl>
    <dd>
        SALES_REP (<ins>REP_ID</ins>, FIRST_NAME, LAST_NAME, ADDRESS, CITY, STATE, POSTAL, CELL_PHONE, COMMISSION, RATE)
    </dd>
</dl>

<dl>
    <dd>
        CUSTOMER (<ins>CUST_ID</ins>, FIRST_NAME, LAST_NAME, ADDRESS, CITY, STATE, POSTAL, EMAIL, BALANCE, CREDIT_LIMIT, REP_ID)
    </dd>
</dl>

<dl>
    <dd>
        ITEM (<ins>ITEM_ID</ins>, DESCRIPTION, ON_HAND, CATEGORY, LOCATION, PRICE)
    </dd>
</dl>

<dl>
    <dd>
        INVOICES (<ins>INVOICE_NUM</ins>, INVOICE_DATE, CUST_ID)
    </dd>
</dl>

<dl>
    <dd>
        INVOICE_LINE (<ins>INVOICE_NUM</ins>, <ins>ITEM_ID</ins>, QUANTITY, QUOTED_PRICE)
    </dd>
</dl>

- **Step 6**: Examining the tables and identifying common columns gives the following list of relationships between the tables:
    - The CUSTOMER and SALES_REP tables are related using the REP_ID columns. Because the REP_ID column is the primary key for the SALES_REP table, this indicates a one-to-many relationship between SALES_REP and CUSTOMER (one rep to many customers).
    - The INVOICES and CUSTOMER tables are related using the CUST_ID columns. Because the CUST_ID column is the primary key for the CUSTOMER table, this indicates a one-to-many relationship between CUSTOMER and INVOICES (one customer to many invoices).
    - The INVOICE_LINE and INVOICES tables are related using the INVOICE_NUM columns. Because the INVOICE_NUM column is the primary key for the INVOICES table, this indicates a one-to-many relationship between INVOICES and INVOICE_LINE (one invoice to many invoice lines).
    - The INVOICE_LINE and ITEM tables are related using the ITEM_ID columns. Because the ITEM_ID column is the primary key for the ITEM table, this indicates a one-to-many relationship between ITEM and INVOICE_LINE (one item to many invoice lines).

#### NORMALIZATION

- After creating the database design, you must analyze it to make sure it is free of potential problems. To do so, you follow a process called normalization, in which you identify the existence of potential problems, such as data duplication and redundancy, and implement ways to correct these problems.
- The goal of normalization is to convert unnormalized relations (tables that satisfy the definition of a relation except that they might contain repeating groups) into various types of normal forms. A table in a particular normal form possesses a certain desirable collection of properties. Although there are several normal forms, the most common are first normal form, second normal form, and third normal form. Normalization is a process in which a table that is in first normal form is better than a table that is not in first normal form, a table that is in second normal form is better than one that is in first normal form, and so on. The goal of this process is to allow you to take a table or collection of tables and produce a new collection of tables that represents the same information but is free of problems.

##### First Normal Form

- According to the definition of a relation, a relation (table) cannot contain a repeating group in which multiple entries exist on a single row. However, in the database design process, you might create a table that has all the other properties of a relation but contains a repeating group. Removing repeating groups is the starting point when converting an unnormalized collection of data into a table that is in first normal form. A table (relation) is in first normal form (1NF) when it does not contain a repeating group.
- For example, in the design process you might create the following INVOICES table, in which there is a repeating group consisting of ITEM_ID and QUANTITY. The notation for this table is as follows:

<dl>
    <dd>
        INVOICES (<ins>INVOICE_NUM</ins>, INVOICE_DATE, (ITEM_ID, QUANTITY))
    </dd>
</dl>

- This notation describes a table named INVOICES that consists of a primary key, INVOICE_NUM, and a column named INVOICE_DATE. The inner parentheses indicate a repeating group that contains two columns, ITEM_ID and QUANTITY. This table contains one row per invoice with values in the ITEM_ID and QUANTITY columns for each invoice with the number INVOICE_NUM and placed on INVOICE_DATE. Figure 2-7 shows a single invoice with multiple combinations of an item ID and a corresponding quantity of units ordered.

![FIGURE 2-7 Unnormalized invoice data](images/figure-2-7-unnormalized-invoice-data.JPG)

To convert the table to first normal form, you remove the repeating group as follows: INVOICES (<ins>INVOICE_NUM</ins>, INVOICE_DATE, ITEM_ID, QUANTITY) Figure 2-8 shows the table in first normal form.

<dl>
    <dd>
        INVOICES (<ins>INVOICE_NUM</ins>, INVOICE_DATE, <ins>ITEM_ID</ins>, QUANTITY)
    </dd>
</dl>

Figure 2-8 shows the table in first normal form.

![FIGURE 2-8 Invoice data converted to firstnormal form](images/figure-2-8-invoice-data-converted-to-first.JPG)

In Figure 2-7, the second row indicates that item AD72 and item DT12 are both included in invoice 14219. In Figure 2-8, this information is represented by two rows, the second and third. The primary key for the unnormalized INVOICES table was the INVOICE_NUM column alone. The primary key for the normalized table is now the combination of the INVOICE_NUM and ITEM_ID columns.
- When you convert an unnormalized table to a table in first normal form, the primary key of the table in first normal form is usually the primary key of the unnormalized table concatenated with the key for the repeating group. The key for the repeating group is the column in the repeating group that distinguishes one occurrence of the repeating group from another. In the INVOICES table, ITEM_ID was the key to the repeating group and INVOICE_NUM was the primary key for the table. When converting the unnormalized data to first normal form, the primary key becomes the concatenation of the INVOICE_NUM and ITEM_ID columns.

##### Second Normal Form

The following INVOICES table is in first normal form, because it does not contain a
repeating group:

<dl>
    <dd>
        INVOICES (INVOICE_NUM, INVOICE_DATE, ITEM_ID, DESCRIPTION, QUANTITY,QUOTED_PRICE)
    </dd>
</dl>

- The table contains the following functional dependencies:

<dl>
    <dd>
        INVOICE_NUM → INVOICE_DATE
        ITEM_ID → DESCRIPTION
        INVOICE_NUM, ITEM_ID → INVOICE_DATE, DESCRIPTION, QUANTITY
    </dd>
</dl>

- This notation indicates that INVOICE_NUM alone determines INVOICE_DATE, and ITEM_ID alone determines DESCRIPTION, but it requires both INVOICE_NUM and ITEM_ID to determine either QUANTITY or QUOTED_PRICE. Consider the sample of this table shown in Figure 2-9.

![FIGURE 2-9 Sample Invoices table](images/figure-2-9-sample-invoices-table.JPG)

- Although the INVOICES table is in first normal form (because it contains no repeating groups), problems exist within the table that require you to restructure it.
- The description of a specific item, KH81 for example, occurs twice in the table. This duplication (formally called redundancy) causes several problems. It is certainly wasteful of space, but that is not nearly as serious as some of the other problems. These other problems are called update anomalies and they fall into four categories:

    1. **Updates**: If you need to change to the description of item KH81, you must change it twice—once in each row on which item KH81 appears. Updating the item description more than once makes the update process much more cumbersome and time consuming.
    2. **Inconsistent data**: There is nothing about the design that prohibits item KH81 from having two *different* descriptions in the database. In fact, if item KH81 occurs on 2 rows in the table, it is possible for this item to have 20 different descriptions in the database.
    3. **Additions**: When you try to add a new item and its description to the database, you will face a real problem. Because the primary key for the INVOICES table consists of both INVOICE_NUM and ITEM_ID, you need values for both of these columns to add a new row to the table. If you add an item to the table that does not yet have any invoices, what do you use for INVOICE_NUM? The only solution is to create a dummy INVOICE_NUM and then replace it with a real INVOICE_NUM once an order for this item is actually received. Certainly, this is not an acceptable solution.
    4. **Deletions**: If you delete invoice 14216 from the database and it is the only invoice that contains item CA75, deleting the invoice also deletes all information about item CA75. For example, you would no longer know that item CA75 is an Enclosed Cat Litter Station.

- These problems occur because the DESCRIPTION column is dependent on only a portion of the primary key (ITEM_ID) and *not* on the complete primary key. This situation leads to the definition of second normal form. Second normal form represents an improvement over first normal form because it eliminates update anomalies in these situations. A table (relation) is in **second normal form (2NF)** when it is in first normal form and no nonkey column (that is, a column that is not part of the primary key) is dependent on only a portion of the primary key.

>**HELPFUL HINT**
> When the primary key of a table contains only a single column, the table is automatically in second normal form.

- You can identify the fundamental problem with the INVOICES table: It is not in second normal form. Although it is important to identify the problem, what you really need is a method to correct it; you want to be able to convert tables to second normal form. First, take each subset of the set of columns that make up the primary key and begin a new table with this subset as its primary key. For the INVOICES table, the new design is as follows:

<dl>
    <dd>
        (INVOICE_NUM,
        (ITEM_ID,
        (INVOICE_NUM, ITEM_ID,
    </dd>
</dl>

- Next, place each of the other columns with the appropriate primary key; that is, place each one with the minimal collection of columns on which it depends. For the INVOICES table, add the new columns as follows:

<dl>
    <dd>
        (INVOICE_NUM, INVOICE_DATE)
        (ITEM_ID, DESCRIPTION)
        (INVOICE_NUM, ITEM_ID, QUANTITY, QUOTED_PRICE)
    </dd>
</dl>

Each of these new tables is given a descriptive name based on the meaning and contents of the table, such as INVOICES, ITEM, and INVOICE_LINE. Figure 2-10 shows samples of these tables.

![FIGURE 2-10 INVOICES table converted to second normal form](images/figure-2-10-invoices-table-converted-to-second-normal-form.JPG)

- In Figure 2-10, converting the original INVOICES table to a new INVOICES table, an ITEM table, and an INVOICE_LINE table eliminates the update anomalies. A description appears only once for each item, so you do not have the redundancy that existed in the original table design. Changing the description of item KH81 from Wild Bird Food (25 lb) to KimTay Premium Wild Bird Food (25 lb), for example, is now a simple process involving a single change. Because the description for an item occurs in a single place, it is not possible to have multiple descriptions for a single item in the database at the same time.
- To add a new item and its description, you create a new row in the ITEM table,regardless of whether that item has pending or actual invoices. In addition, deleting invoice 14216 does not delete item number CA75 from the database because it still exists in the ITEM table. Finally, you have not lost any information by converting the INVOICES table to second normal form. You can reconstruct the data in the original table from the data in the new tables.

##### Third Normal Form

Problems can still exist with tables that are in second normal form. For example, suppose that you create the following CUSTOMER table:

<dl>
    <dd>
        CUSTOMER (CUST_ID, FIRST_NAME, LAST_NAME, BALANCE, CREDIT_LIMIT, REP_ID, REP_FIRST_NAME, REP_LAST_NAME)
    </dd>
</dl>

This table has the following functional dependencies:

<dl>
    <dd>
        CUST_ID point &rarr; FIRST_NAME, LAST_NAME, BALANCE, CREDIT_LIMIT, REP_ID, REP_FIRST_NAME, REP_LAST_NAME
        REP_ID &rarr; REP_FIRST_NAME, REP_LAST_NAME
    </dd>
</dl>

- CUST_ID determines all the other columns. In addition, REP_ID determines
REP_FIRST_NAME and REP_LAST_NAME.
- When a table’s primary key is a single column, the table is automatically in second normal form. (If the table were not in second normal form, some column would be dependent on only a portion of the primary key, which is impossible when the primary key is just one column.) Thus, the CUSTOMER table is in second normal form.
- Although this table is in second normal form, Figure 2-11 shows that it still possesses update problems similar to those identified for the INVOICES table shown in Figure 2-9. In Figure 2-11, the sales rep name occurs many times in the table.

![FIGURE 2-11 Sample CUSTOMER table](images/figure-2-11-sample-customer-table.JPG)

- The redundancy of including a sales rep ID and full name in the CUSTOMER table results in the same set of problems that existed for the INVOICES table. In addition to the problem of wasted space, you have the following update anomalies:

    1. **Updates**: Changing the sales rep full name requires changes to multiple rows in the table.
    2. **Inconsistent** data: The design does not prohibit multiple iterations of sales rep names in the database. For example, a sales rep might represent 20 customers, and his or her name might be entered 20 different ways in the table.
    3. **Additions**: To add sales rep 25 (Juanita Sanchez) to the database, she must represent at least one customer. If Juanita does not yet represent any customers, you either cannot record the fact that her name is Juanita Sanchez, or you must create a fictitious customer for her to represent until she represents an actual customer. Neither of these solutions is desirable.
    4. **Deletions**: If you delete all the customers of sales rep 05 from the database, you will also lose all information about sales rep 05.

- These update anomalies are because the REP_ID determines REP_FIRST_NAME and
REP_LAST_NAME, but REP_ID is not the primary key. As a result, the same REP_ID and
consequently the same REP_FIRST_NAME and REP_LAST_NAME can appear on many
different rows.
- You have seen that tables in second normal form represent an improvement over tables in first normal form, but to eliminate problems with tables in second normal form, you need an even better strategy for creating tables. Third normal form provides that strategy. Before looking at third normal form, however, you need to become familiar with the special name that is given to any column that determines another column (like REP_ID in the CUSTOMER table). Any column (or collection of columns) that determines another column is called a **determinant**. A table’s primary key is a determinant. In fact, by definition, any candidate key is a determinant. (Remember that a candidate key is a column or collection of columns that could function as the primary key.) In Figure 2-11, REP_ID is a determinant, but it is not a candidate key, and that is the problem.
- A table is in **third normal form (3NF)** when it is in second normal form and the only determinants it contains are candidate keys.

> **HELPFUL HINT**
> This text’s definition of third normal form is not the original definition. This more recent definition, which is preferable to the original, is often referred to as **Boyce-Codd normal form (BCNF)** when it is important to make a distinction between this definition and the original definition. This text does not make such a distinction but will take this to be the definition of third normal form.

- Now you have identified the problem with the CUSTOMER table: It is not in third normal form. There are several steps for converting tables to third normal form.
- First, for each determinant that is not a candidate key, remove from the table the columns that depend on this determinant (but do not remove the determinant). Next, create a new table containing all the columns from the original table that depend on this determinant. Finally, make the determinant the primary key of this new table.
- In the CUSTOMER table, for example, remove REP_FIRST_NAME and REP_LAST_NAME because they depend on the determinant REP_ID, which is not a candidate key. A new table, SALES_REP, is formed, consisting of REP_ID as the primary key and the columns REP_FIRST_NAME and REP_LAST__NAME, as follows:

<dl>
    <dd>
        CUSTOMER (<ins>CUST_ID<ins>, FIRST_NAME, LAST_NAME, BALANCE, CREDIT_LIMIT, REP_ID)
    <dd>
</dl>

and

<dl>
    <dd>
        SALES_REP (<ins>REP_ID<ins>, REP_FIRST_NAME, REP_LAST_NAME)
    <dd>
</dl>

- Previously the first and last names for the sales rep were named REP_FIRST_NAME and REP_LAST_NAME, respectively. It was not possible to use the identifiers FIRST_NAME and LAST_NAME because in the CUSTOMER table FIRST_NAME and LAST_NAME were being used to identify the first and last names of the customer. Because the fields REP_FIRST_NAME and REP_LAST_NAME are now being removed from the CUSTOMER table and placed into the SALES_REP table, it is now possible to use the identifiers of FIRST_NAME and LAST_NAME to correspond to the first and last names for a sales rep. The SALES_REP table will now be noted as follows, incorporating the desired identifiers for the first and last names for the sales rep:

<dl>
    <dd>
        SALES_REP (<ins>REP_ID<ins>, FIRST_NAME, LAST_NAME)
    <dd>
</dl>

Figure 2-12 shows the original CUSTOMER table and the tables created when converting the original table to third normal form.

![FIGURE 2-12 CUSTOMER table converted to third normal form](images/figure-2-9-sample-invoices-table.JPG)

- Has this new design for the CUSTOMER table corrected all of the previously identified problems? A sales rep’s name appears only once, thus avoiding redundancy and simplifying the process of storing a sales rep’s first and last name. This design prohibits a sales rep from having different names in the database. To add a new sales rep to the database, you add a row to the SALES_REP table; it is not necessary for a new rep to represent a customer. Finally, deleting all customers of a given sales rep will not remove the sales rep’s record from the SALES_REP table, retaining the sales rep’s first and last name in the database. You can reconstruct all the data in the original table from the data in the new collection of tables. All previously mentioned problems have indeed been solved.

<dl>
    <dd>
        STUDENT_NUM &rarr; STUDENT_NAME, NUM_CREDITS, ADVISOR_NUM, ADVISOR_NAME
    </dd>
    <dd>
        ADVISOR_NUM &rarr; ADVISOR_NAME, COURSE_NUM
    </dd>
    <dd>
        COURSE_NUM &rarr; DESCRIPTION.
    </dd>
    <dd>
        STUDENT_NUM, COURSE_NUM &rarr; GRADE.
    </dd>
</dl>


<dl>
    <dd>
        STUDENT (<ins>STUDENT_NUM<ins>, NAME, NUM_CREDITS, ADVISOR_NUM, COURSE_NUM)
    </dd>
    <dd>
        ADVISOR (<ins>ADVISOR_NUM<ins> ADVISOR_NAME, COURSE_NUM)
    </dd>
    <dd>
        COURSE (<ins>COURSE_NUM<ins>, DESCRIPTION)
    </dd>
    <dd>
        GRADE (<ins>STUDENT_NUM<ins>, <ins>COURSE_NUM<ins>, GRADE).
    </dd>
</dl>

> **Q & A**
> Question: Convert the following table to third normal form. In this table, STUDENT_NUM determines STUDENT_NAME, NUM_CREDITS, ADVISOR_NUM, and ADVISOR_NAME. ADVISOR_NUM determines ADVISOR_NAME. COURSE_NUM determines DESCRIPTION. The combination of a STUDENT_NUM and a COURSE_NUM determines GRADE.
> <dl>
>   <dd>
>       STUDENT (<ins>STUDENT_NUM</ins>, STUDENT_NAME, NUM_CREDITS, ADVISOR_NUM, ADVISOR_NAME, (COURSE_NUM, DESCRIPTION, GRADE))
>   </dd>
> </dl>
> **Answer:** Complete the following steps:
> - **Step 1**: Remove the repeating group to convert the table to first normal form, as follows:
> <dl>
>   <dd>
>       STUDENT (<ins>STUDENT_NUM</ins>, STUDENT_NAME, NUM_CREDITS, ADVISOR_NUM, ADVISOR_NAME, <ins>COURSE_NUM</ins>, DESCRIPTION, GRADE)
>   </dd>
> </dl>
> - The STUDENT table is now in first normal form because it has no repeating groups. It is not, however, in second normal form because STUDENT_NAME is dependent only on STUDENT_NUM, which is only a portion of the primary key.
> - **Step 2**: Convert the STUDENT table to second normal form. First, for each subset of the primary key, start a table with that subset as its key yielding the following:
> <dl>
>   <dd>
>       (<ins>STUDENT_NUM</ins>, )
>       (<ins>COURSE_NUM</ins>, )
>       (<ins>STUDENT_NUM</ins>, <ins>COURSE_NUM</ins>,)
>   </dd>
> </dl>
> Next, place the rest of the columns with the smallest collection of columns on which they depend, as follows:
> <dl>
>   <dd>
>       (<ins>STUDENT_NUM</ins>, STUDENT_NAME, NUM_CREDITS, ADVISOR_NUM, ADVISOR_NAME)
>       (<ins>COURSE_NUM</ins>, DESCRIPTION)
>       (<ins>STUDENT_NUM</ins>, <ins>COURSE_NUM</ins>, GRADE)
>   </dd>
> </dl>
> Finally, assign names to each of the new tables:
> <dl>
>   <dd>
>       STUDENT (<ins>STUDENT_NUM</ins>, STUDENT_NAME, NUM_CREDITS, ADVISOR_NUM, ADVISOR_NAME)
>       COURSE(<ins>COURSE_NUM</ins>, DESCRIPTION)
>       STUDENT_COURSE(<ins>STUDENT_NUM</ins>, <ins>COURSE_NUM</ins>, GRADE)
>   </dd>
> </dl>
> - Although these tables are all in second normal form, the COURSE and STUDENT_COURSE tables are also in third normal form. The STUDENT table is not in third normal form, however, because it contains a determinant (ADVISOR_NUM) that is not a candidate key.
> - **Step 3**: Convert the STUDENT table to third normal form by removing the column that depends on the determinant ADVISOR_NUM and placing it in a separate table, as follows:
> <dl>
>   <dd>
>       (<ins>STUDENT_NUM</ins>, STUDENT_NAME, NUM_CREDITS, ADVISOR_NUM)
>       (<ins>ADVISOR_NUM</ins>, ADVISOR_NAME))
>   </dd>
> </dl>
> - **Step 4**: Name the tables and put the entire collection together, as follows:
> <dl>
>   <dd>
>       STUDENT (<ins>STUDENT_NUM</ins>, STUDENT_NAME, NUM_CREDITS, ADVISOR_NUM)
>       ADVISOR (<ins>ADVISOR_NUM</ins>, ADVISOR_NAME))
>       COURSE (<ins>COURSE_NUM</ins>, DESCRIPTION)
>       STUDENT_COURSE (<ins>STUDENT_NUM</ins>, <ins>COURSE_NUM</ins>, GRADE)
>   </dd>
> </dl>

### DIAGRAMS FOR DATABASE DESIGN

- For many people, an illustration of a database’s structure is quite useful. A popular type of illustration used to represent the structure of a database is the **entity-relationship (E-R)** diagram. In an E-R diagram, a rectangle represents an entity (table). One-to-many relationships between entities are drawn as lines between the corresponding rectangles.
- Several different styles of E-R diagrams are used to diagram a database design. In the version shown in Figure 2-13, an arrowhead indicates the many side of the relationship between tables. In the relationship between the SALES_REP and CUSTOMER tables, for example, the arrow points from the SALES_REP table to the CUSTOMER table, indicating that one sales rep is related to many customers. The INVOICE_LINE table has two one-to-many relationships, as indicated by the line from the INVOICES table to the INVOICE_LINE table and the line from the ITEM table to the INVOICE_LINE table.

![FIGURE 2-13 E-R diagram for the KimTay Pet Supplies database with rectangles and arrows](images/figure-2-13-e-r-diagram-for-the-kim-tay-pet-supplies-database-with-rectangles-and-arrows.JPG)

> HELPFUL HINT
> - In this style of E-R diagram, you can put the rectangles in any position to represent the entities and relationships. The important thing is that the arrows connect the appropriate rectangles.

- Another style of E-R diagram is to represent the many side of a relationship between
tables with a crow’s foot, as shown in Figure 2-14.

![FIGURE 2-14 E-R diagram for the KimTay Pet Supplies database with crow’s foot](images/figure-2-14-e-r-diagram-for-the-kimtay-pet-supplies-database-with-crows-foot.JPG)

- The E-R diagram shown in Figure 2-15 represents the original style of E-R diagrams. In this style, relationships are indicated in diamonds that describe the relationship. The relationship between the SALES_REP and CUSTOMER tables, for example, is named REPRESENTS, reflecting the fact that a sales rep represents a customer. The relationship between the CUSTOMER and INVOICES table is named PLACED, reflecting the fact that customers place invoices. The relationship between the INVOICES and INVOICE_LINE tables is named CONTAINS, reflecting the fact that an invoice contains invoice lines. The relationship between the ITEM and INVOICE_LINE tables is named IS_ON, reflecting the fact that a given item is on many invoices. In this style of E-R diagram, the number 1 indicates the one side of the relationship and the letter n represents the many side of the relationship.

![FIGURE 2-15 E-R diagram for the KimTay Pet Supplies database with named relationships](images/figure-2-15-e-r-diagram-for-the-kimtay-pet-supplies-database%20with-named-relationships.JPG)

### Module Summary

- An entity is a person, place, thing, or event. An attribute is a property of an entity. A relationship is an association between entities.
- A relation is a two-dimensional table in which the entries in the table contain only single values, each column has a distinct name, all values in a column match this name, the order of the rows and columns is immaterial, and each row contains unique values. A relational database is a collection of relations.
- Column B is functionally dependent on another column, A (or possibly a collection of columns), when a value for A determines a single value for B at any one time.
- Column A (or a collection of columns) is the primary key for a relation (table), R, if all columns in R are functionally dependent on A and no subcollection of the columns in A (assuming A is a collection of columns and not just a single column) also has Property 1.
- To design a database to satisfy a particular set of requirements, first read the requirements and identify the entities (objects) involved. Give names to the entities and identify the unique identifiers for these entities. Next, identify the attributes for all the entities and the functional dependencies that exist among the attributes and then use the functional dependencies to identify the tables and columns. Finally, identify any relationships between tables by looking at matching columns.
- A table (relation) is in first normal form (1NF) when it does not contain a repeating group. To convert an unnormalized table to first normal form, remove the repeating group and expand the primary key to include the original primary key along with the key to the repeating group.
- A table (relation) is in second normal form (2NF) when it is in first normal form and no nonkey column (that is, a column that is not part of the primary key) is dependent on only a portion of the primary key. To convert a table in first normal form to a collection of tables in second normal form, take each subset of the set of columns that make up the primary key and begin a new table with this subset as its primary key. Next, place each of the other columns with the appropriate primary key; that is, place each one with the minimal collection of columns on which it depends. Finally, give each of these new tables a name that is descriptive of the meaning and contents of the table.
• A table is in third normal form (3NF) when it is in second normal form and the only determinants (columns on which at least one other column depends) it contains are candidate keys (columns that could function as the primary key). To convert a table in second normal form to a collection of tables in third normal form, first, for each determinant that is not a candidate key, remove from the table the columns that depend on this determinant (but do not remove the determinant). Next, create a new table containing all the columns from the original table that depend on this determinant. Finally, make the determinant the primary key of this new table.
• An entity-relationship (E-R) diagram is an illustration that represents the design of a database. There are several common styles of illustrating database design that use shapes to represent entities and connectors to illustrate the relationships between those entities.


### Key Terms

- attribute, Boyce-Codd normal form (BCNF), candidate key, concatenation, database design, database management system (DBMS), determinant, entity, entity-relationship (E-R) diagram, field, first normal form (1NF), functionally dependent, functionally determine, nonkey column, normal form, normalization, one-to-many relationship, primary key, qualify, record, redundancy, relation, relational database, relationship, repeating group, second normal form (2NF), third normal form (3NF), tuple, unnormalized relation, update anomaly

### Review Questions

#### Module Quiz

> **Q-1**: What is an entity?
> 
> **Answer**: An entity is an object that exists. For example, a person, place, thing, or event. 

> **Q-2**: What is an attribute?
> 
> **Answer**: An attribute is a property of an entity. For example, attibutes of the person attribute might include such thing as first name, last name, eye color, height, gender, weight, etc.

> **Q-3**: What is a relationship? What is a one-to-many relationship?
> 
> **Answer**: 
> - A relationship is the association between two entities. For example, there might be an association between the customer entity and the sale representative entity.
> - A one-to-many relationship is the one in which one record in one entity is associated to any number of records in the other entity. For example, the customer entity and the sale representative entity have a one-to-many relationship because one sale representative can represent more than one customer.

> **Q-4**: What is a repeating group?
> 
> **Answer**: A repeating group is a case in which multiple entries exist in an individual location in a relation or table. For example, a cell in a relation or table can contain more than one entries. 

> **Q-5**: What is a relation?
> 
> **Answer**: A relation is a two-dimensional table in which the entries in the table contain only single values, each column has a distinct name, all values in a column match this name, the order of the rows and columns is immaterial, and each row contains unique values.

> **Q-6**: What is a relational database?
> 
> **Answer**: A relational database is a collection of relations. 

> **Q-7**: Describe the shorthand representation of the structure of a relational database. Why is it important to be able to represent the structure of a database in a shorthand fashion?
> 
> **Answer**: The shorthand representation of the structure of a relational database is used to show the tables and the columns in a relational database. For each table, you write the name of the table and then within parenthesis list all the columns in the table. In this representation, each table appears on its own line. The primary key of each table can be indicated underlining the column or collection of columns that comprise the primary key.
> 

> **Q-8**: How do you qualify the name of a field, and when do you need to do this?
> 
> **Answer**: Some tables contains columns with duplicate names.  To avoid confusion, You need to qualify each name by writing both the table name and the column name, separated by a period. For example, if you have a CUSTOMER table with a column named REP_ID and a SALES_REP table with a column named REP_ID, you can reference the REP_ID column in the CUSTOMER table as CUSTOMER.REP_ID and the REP_ID in the SALES_REP table as SALES_REP.REP_ID.

> **Q-9**: What does it mean for a column to be functionally dependent on another column?
> 
> **Answer**: A column say Y is functionally dependent on another column (or a collection of columns), say X, if at any point in time a value of X determines a single value for Y. You can say that X functionaly determines Y. For example, you can say that in a SALES_REP table, THE sales rep first and last names is functionally dependent on the REP_ID column because you can determine the first name and the last name of that sales rep using his or her sales rep ID.

> **Q-10**: What is a primary key? Why is a primary key required for proper database design?
> 
> **Answer**: A primary key is a unique identifier for a table that is used to uniquely identify each row or record in the table. For example, in a SALES_REP table, REP_ID is the primary key because it's used to uniquely identify each row in the SALES_REP table. Also, all the other columns in the table are fuctionally dependent on the primary key.

> **Q-11**: A database at a college must support the following requirements:
>   <ol>
>       <li style="list-style-type:lower-alpha">
>           For a department, store its number and name.
>       </li>
>       <li style="list-style-type:lower-alpha">
>           For an advisor, store his or her number, last name, first name, and the department number to which the advisor is assigned.
>       </li>
>       <li style="list-style-type:lower-alpha">
>           For a course, store its code and description (for example, DBA210, SQL Programming).
>       </li>
>       <li style="list-style-type:lower-alpha">
>           For a student, store his or her number, first name, and last name. For each course the student takes, store the course code, course description, and grade earned. Also, store the number and name of the student’s advisor. Assume that an advisor might advise any number of students but that each student has just one advisor. 
>       </li>
>   </ol>
>
> Design the database for the preceding set of requirements. Use your own experience as a student to determine any functional dependencies. List the tables, columns, and relationships. In addition, represent your design with an E-R diagram.
> 
> **Answer**:
>
> **Step 1**: From the requirements, there appear to be four entities: department, advisor, course, and student. They will be named DEPARTMENT, ADVISOR, COURSE, and STUDENT, respectively. 
>
> **Step 2**: For the DEPARTMENT, ADVISOR, COURSE, and STUDENT entities, the unique identifiers are department number, advisor number, course code, and student number. They will be named DEPARTMENT_NUM, ADVISOR_NUM, COURSE_CODE, and STUDENT_NUM, respectively.
>
> **Step 3**: From the requirement, the attributes for each entity is as follows:
>
> **DEPARTMENT**
> DEPARTMENT_NUM
> NAME
>
> **ADVISOR**
> ADVISOR_NUM
> LAST_NAME
> FIRST_NAME
> DEPARTMENT_NUM
> 
> **COURSE**
> COURSE_CODE
> DESCRIPTION
> 
> **STUDENT**
> STUDENT_NUM
> FIRST_NAME (STUDENT)
> LAST_NAME (STUDENT)
> COURSE_CODE
> COURSE_ DESCRIPTION
> COURSE_GRADE
> ADVISOR_NUM
> ADVISOR_LAST_NAME
> ADVISOR_FIRST_NAME
>
> **Step 4**:
>
> The fact that the unique identifier for DEPARTMENT entity is the DEPARTMENT_NUM gives the following functional dependencies:
> 
> <ul style="list-style-type: none;">
>   <li>
>       DEPARTMENT_NUM &rarr; NAME
>   </li>
> </ul>
>
> The fact that the unique identifier for ADVISOR entity is the ADVISOR_NUM gives the following functional dependencies:
>
> <ul style="list-style-type: none;">
>   <li>
>       ADVISOR_NUM &rarr; LAST_NAME, FIRST_NAME, DEPARTMENT_NUM
>   </li>
> </ul>
>
> The fact that the unique identifier for COURSE entity is the COURSE_CODE gives the following functional dependencies:
>
> <ul style="list-style-type: none;">
>   <li>
>       COURSE_CODE &rarr; DESCRIPTION
>   </li>
> </ul>
>
> The fact that the unique identifier for STUDENT entity is the STUDENT_NUM gives the following functional dependencies:
>
> <ul style="list-style-type: none;">
>   <li>
>       STUDENT_NUM &rarr; FIRST_NAME, LAST_NAME, COURSE_CODE, COURSE_DESCRIPTION, COURSE_GRADE, ADVISOR_NUM, ADVISOR_LAST_NAME, ADVISOR_FIRST_NAME
> </ul>
>
> **Step 5**:
> The final collection of tables are as follows:
>
> <ul style="list-style-type: none;">
>   <li>
>        DEPARTMENT (<ins>DEPARTMENT_NUM</ins>, NAME)
>   </li>
> </ul>
>
> <ul style="list-style-type: none;">
>   <li>
>       ADVISOR (<ins>ADVISOR_NUM</ins>, LAST_NAME, FIRST_NAME, DEPARTMENT_NUM)
>   </li>
> </ul>
>
> <ul style="list-style-type: none;">
>   <li>
>       COURSE (<ins>COURSE_CODE</ins>, DESCRIPTION)
>   </li>
> </ul>
>
> <ul style="list-style-type: none;">
>   <li>
>       STUDENT (<ins>STUDENT_NUM</ins>, FIRST_NAME, LAST_NAME, COURSE_CODE, COURSE_DESCRIPTION, GRADE, ADVISOR_NUM, ADVISOR_LAST_NAME, ADVISOR_FIRST_NAME)
> </ul>
>
> **Step 6**: The following is a list of relationships between tables:
>
> **Answer**: 
> The DEPARTMENT and ADVISOR tables are related using the DEPARTMENT_NUM columns. Because DEPARTMENT_NUM is the primary key for the DEPARTMENT table, this indicates a one-to-many relationship between DEPARTMENT and ADVISOR (one department can have to many advisors).
> 
> The ADVISOR and STUDENT tables are related using the ADVISOR_NUM columns. Because ADVISOR_NUM is the primary key for the ADVISOR table, this indicates a one-to-many relationship between ADVISOR and STUDENT (one advisor can advice many students).
> 
> The COURSE and STUDENT tables are related using the COURSE_CODE columns. Because COURSE_CODE is the primary key for the COURSE table, this indicates a one-to-many relationship between COURSE and STUDENT (one course can have many students).
>
> The DEPARTMENT and STUDENT tables are related using the DEPARTMENT_NUM columns. Because DEPARTMENT_NUM is the primary key for the DEPARTMENT table, this indicates a one-to-many relationship between DEPARTMENT and STUDENT (one department can have to many students).
>
> The E-R diagram for the design is as follows:
>
> ![figure-for-e-r-diagram-for-module-2-question-11](./images/figure-for-e-r-diagram-for-module-2-question-11.JPG)

> **Q-12**: Define first normal form. What types of problems might you encounter using tables that are not in first normal form??
> 
> **Answer**: 
> 
>  A table or relation is in the first normal form (1NF) when it does not contain a repeating group. Tables that are not in the first normal form (1NF) have no primary key column or a collection of columns. This may lead to the table have duplicate rows. The lack of a primary key may make the database difficult to query or update

> **Q-13**: Define second normal form. What types of problems might you encounter using tables that are not in second normal form?
> 
> **Answer**:
> - A table is in the second normal form (2NF) when it is in first normal form and no nonkey column (that is, a column that is not part of the primary key) is dependent on only a portion of the primary key. 
> - A table that is not in the second normal form has duplication or redundancy problem in which is wasteful of space. It also leads to an update anomalies. 

> **Q-14**: Define third normal form. What types of problems might you encounter using tables that are not in third normal form?
> 
> **Answer**:
> -  A table is in the third normal form (3NF) when it is in second normal form and the only determinants (that is, any column or a collection of columns that determines another column) it contains are candidate keys.
> - Using tables that are not in third normal form is wasteful of space and also leads to update anomalies because changing a value may require changing multiple rows in the table. It also leads to inconsistent data values because of the multiple entries.

> **Q-15**: Using the functional dependencies that you determined in Question 11, convert the following table to an equivalent collection of tables that are in third normal form.
> 
> <dl>
>   <dd>
>       STUDENT (STUDENT_NUM, STUDENT_LAST_NAME, STUDENT_FIRST_NAME, ADVISOR_NUM, ADVISOR_LAST_NAME, ADVISOR_FIRST_NAME, (COURSE_CODE, DESCRIPTION, GRADE))
>   </dd>
> </dl>
> 
> **Answer**:
>
> **Step 1**: Convert the STUDENT table to first normal form by removing the repeated groups:
>
> <dl>
>   <dd>
>       STUDENT (<ins>STUDENT_NUM</ins>, STUDENT_LAST_NAME, STUDENT_FIRST_NAME, ADVISOR_NUM, ADVISOR_LAST_NAME, ADVISOR_FIRST_NAME, <ins>COURSE_CODE</ins>, DESCRIPTION, GRADE)
>   </dd>
> </dl>
>
> The table is now in the first normal form with STUDENT_NUM and COURSE_CODE as the primary keys. However, it is not in the second normal form as some nonkey columns such as STUDENT_LAST_NAME are dependent only on STUDENT_NUM, which is a portion of the primary key.
>
> **Step 2**: Convert the tables to second normal form:
>
> <dl>
>   <dd>
>       STUDENT (STUDENT_NUM,  STUDENT_LAST_NAME, STUDENT_FIRST_NAME, ADVISOR_NUM, ADVISOR_LAST_NAME, ADVISOR_FIRST_NAME)
>       COURSE (COURSE_CODE, DESCRIPTION)
>       STUDENT_COURSE(STUDENT_NUM, COURSE_CODE, GRADE)
>   <dd>
> <dl>
>
> The COURSE and STUDENT_COURSE tables are in the third normal form because they do not have a determinant column that is a nonkey. However, the STUDENT table is in the second normal form but not in the third normal form because ADVISOR_NUM is a determinant of ADVISOR_LAST_NAME and ADVISOR_FIRST_NAME yet it's not a candidate key. 
>
> **Step 3**: Convert the STUDENT table to the third normal form by removing the columns that depends on the ADVISOR_NUM and placing it in a separate table:
>
> <dl>
>   <dd>
>       STUDENT (STUDENT_NUM,  STUDENT_LAST_NAME, STUDENT_FIRST_NAME, ADVISOR_NUM)
>       ADVISOR (ADVISOR_NUM, ADVISOR_LAST_NAME, ADVISOR_FIRST_NAME)
>   <dd>
> <dl>
>
> An equivalent collection of tables that are in third normal form is:
>
> <dl>
>   <dd>
>       STUDENT (STUDENT_NUM,  STUDENT_LAST_NAME, STUDENT_FIRST_NAME, ADVISOR_NUM)
>       ADVISOR (ADVISOR_NUM, ADVISOR_LAST_NAME, ADVISOR_FIRST_NAME)
>       COURSE (COURSE_CODE, DESCRIPTION)
>       STUDENT_COURSE(STUDENT_NUM, COURSE_CODE, GRADE)
>   <dd>
> <dl>

#### Critical Thinking

> **Q-1**: List the changes to your answer for Question 11 needed to make the requirements change so a student can have more than one advisor.
> 
> **Answer**:
> For a student to have more than one advisor, the STUDENT_NUM and ADVISOR_NUM columns must be the primary key of the STUDENT table. This will therefore create the following functional dependency:
> <dl>
>   <dd>
>      STUDENT_NUM, ADVISOR_NUM &rarr; FIRST_NAME, LAST_NAME, COURSE_CODE, COURSE_DESCRIPTION, GRADE, ADVISOR_LAST_NAME, ADVISOR_FIRST_NAME
>   </dd>
> </dl>
> 
> The student table will look as follows
>
> <dl>
>   <dd>
>      STUDENT (<ins>STUDENT_NUM</ins>, FIRST_NAME, LAST_NAME, COURSE_CODE, COURSE_DESCRIPTION, GRADE, <ins>ADVISOR_NUM</ins>, ADVISOR_LAST_NAME, ADVISOR_FIRST_NAME)
>   </dd>
> </dl>
>
> **Q-2**: List the changes to your answer for Question 11 needed to make the requirements change so that you must store the year and the semester in which a student took a course and received a grade.
> 
> **Answer**:
>
> To store the year and the semester in which a student took a course, you should add YEAR and SEMESTER in the STUDENT tables as column which will be dependent on STUDENT_NUM. The table will look as follows: 
>
> <ul style="list-style-type: none;">
>   <li>
>       STUDENT (<ins>STUDENT_NUM</ins>, FIRST_NAME, LAST_NAME, COURSE_CODE, COURSE_DESCRIPTION, YEAR, SEMESTER, GRADE, ADVISOR_NUM, ADVISOR_LAST_NAME, ADVISOR_FIRST_NAME)
> </ul>
>
> This assumes that one student is only allowed to take one course.

#### Case Exercises

##### KimTay Pet Supplies

- Answer each of the following questions using the KimTay Pet Supplies data shown in Figure 2-1.
- No computer work is required.

> **Q-1**: Indicate the changes (using the shorthand representation) that you would need to make to the original KimTay Pet Supplies database design (see Figure 2-1) to support the following requirements. A customer is not necessarily represented by a single sales rep, but they can be represented by several sales reps. When a customer places an order, the sales rep who gets the commission on the invoice must be in the collection of sales reps who represent the customer.
>
> **Answer**: 
> For a customer to be represented by several sales reps, the CUST_ID must be included as column in the SALES_REP table, and the primary key of the new SALES_REP table be REP_ID and CUST_ID. Since REP_ID and CUST_ID are the new primary key, the new table could be renamed as CUSTOMER_SALES_REP as shown below:
>
> <dl>
>   <dd>
>       CUSTOMER_SALES_REP (<ins>REP_ID</ins>, FIRST_NAME, LAST_NAME, ADDRESS, CITY, STATE, POSTAL_CELL_PHONE, COMMISSION, RATE, <ins>CUST_ID</ins>)
>   </dd>
> </dl>
>

> **Q-2**: Indicate the changes (using the shorthand representation) that you would need to make to the original KimTay Pet Supplies database design to support the following requirements. There is no relationship between customers and sales reps. When a customer places an order, any sales rep can process the order and create the invoice. On the invoice, you need to identify both the customer placing the order and the sales rep responsible for the invoice. Draw an E-R diagram for the new design.
>
> **Answer**:
>
> CUSTOMER and SALES_REP tables are connected using the REP_ID columns. To remove the relationship between customers and sales reps, we need to remove REP_ID column from the CUSTOMER table. The following is a shorthand representation of the new table:
>
> <dl>
>   <dd>
>       CUSTOMER (CUST_ID, FIRST_NAME, LAST_NAME, ADDRESS, CITY, STATE, POSTAL, EMAIL, BALANCE, CREDIT_LIMIT)
>   </dd>
> </dl>
> 
> To identify both the customer placing the order and the sales rep responsible for the invoice, we need to include REP_ID as a column of the INVOICE table. Since REP_ID is the primary key of the SALES_REP table, there will be a one-to-many relationship between SALES_REP and INVOICE (one sales rep can create many invoices)
>
> <dl>
>   <dd>
>       INVOICES (INVOICE_NUM, INVOICE_DATE, CUST_ID, REP_ID)
>   </dd>
> </dl>
>
> The new design is shown in the following E-R diagram:
> 
> ![Figure: E-R diagram showing the relationship between SALES_REP, INVOICES, and CUSTOMER](./images/Figure-e-r-diagram-showing-the-relationship-between-sales-rep-invoices-and-customer.JPG)
> 


> **Q-3**: Indicate the changes (using the shorthand representation) that you would need to make to the original KimTay Pet Supplies database design in the event that the original Requirement 3 is changed as follows. For an item, store the item’s ID, description, category, and price. In addition, for each location in which the item is located, store the value of the location, the description of the location, and the number of units of the item stored in the location. Draw an E-R diagram for the new design. 
>
> **Answer**:
>  You will need to come up with the ITEM table and the LOCATION table that are related using the LOCATION_ID columns. Since LOCATION_ID is the primary key of the LOCATION table, the ITEM and LOCATION have a one-to-many relationship (one location can have many items).
>
> <dl>
>   <dd>
>       ITEM (ITEM_ID, DESCRIPTION, CATEGORY, PRICE, LOCATION_ID)
>   </dd>
>   <dd>
>       LOCATION (LOCATION_ID, VALUE, DESCRIPTION, ON_HAND)
>   </dd>
> </dl>
>
> ![Figure: E-R diagram showing the relationship between ITEM and LOCATION](./images/Figure-E-R-diagram-showing-the-relationship-between-ITEM-and-LOCATION.JPG)

> **Q-4**: Using your knowledge of KimTay Pet Supplies, determine the functional dependencies that exist in the following table. After determining the functional dependencies, convert this table to an equivalent collection of tables that are in third normal form.
> <ul style="list-style-type: none">
>   <li>
>       ITEM (ITEM_ID, DESCRIPTION, ON_HAND, CATEGORY, LOCATION, PRICE, (INVOICE_NUM, INVOICE_DATE, CUST_ID, FIRST_NAME, LAST_NAME, QUANTITY, QUOTED_PRICE))
>   </li>
> </ul>
>
> **Answer**:
>
> The functional dependencies that exist in the above table are:
>
> <dl>
>   <dd>
>       ITEM_ID &rarr; DESCRIPTION, ON_HAND, CATEGORY, LOCATION, PRICE
>   </dd>
>   <dd>
>       INVOICE_NUM &rarr; INVOICE_DATE, CUST_ID
>   </dd>
>   <dd>
>       CUST_ID &rarr; FIRST_NAME, LAST_NAME
>   </dd>
>   <dd>
>       INVOICE_NUM, ITEM_ID &rarr; QUANTITY, QUOTED_PRICE
>   </dd>
> </dl>
>
> The equivalent collection of tables that are in third normal form are as follows:
>
> <dl>
>   <dd>
>       ITEM (<ins>ITEM_ID</ins>, DESCRIPTION, ON_HAND, CATEGORY, LOCATION, PRICE)
>   </dd>
>   <dd>
>       INVOICES (<ins>INVOICE_NUM</ins>, INVOICE_DATE, CUST_ID)
>   </dd>
>   <dd>
>       CUSTOMER (<ins>CUST_ID</ins>, FIRST_NAME, LAST_NAME)
>   </dd>
>   <dd>
>       INVOICE_LINE (<ins>INVOICE_NUM</ins>, <ins>ITEM_ID</ins>, QUANTITY, QUOTED_PRICE)
>   </dd>
> </dl>
>
> ##### Critical Thinking
>
> **Q-4**: Indicate the changes you need to make to the KimTay Pet Supplies database to support the following additional requirement. Each location has a manager who is identified by a manager ID, a manager first name, and a manager last name.
>
> **Answer**:
>
> You need to add an extra entity called MANAGER and a table called MANAGER to the KimTay Pet Supplies database. The shorthand representation for the MANAGER table is:
>
> <dl>
>   <dd>
>       MANAGER (<ins>MANAGER_ID</ins>, FIRST_NAME, LAST_NAME)
>   </dd>
> </dl>
>
> You also need to add an extra entity called LOCATION and a table called LOCATION to the KimTay Pet Supplies database with MANAGER_ID column as one of the columns in the LOCATION table. The shorthand representation for the LOCATION table is:
>
> <dl>
>   <dd>
>       LOCATION (LOCATION_ID, DESCRIPTION, MANAGER_ID)
>   </dd>
> </dl>
>
> ##### StayWell Student Accommodation
>
> Answer each of the following questions using the StayWell Student Accommodation data shown in Figures 1-4 through 1-9 in Module 1. No computer work is required.
>
> **Q-1**: Determine the functional dependencies that exist in the following table and then convert this table to an equivalent collection of tables that are in third normal form.
>
> <dl>
>   <dd>
>       OFFICE (OFFICE_NUM, OFFICE_NAME, (ADDRESS, SQR_FT, BDRMS, FLOORS, MONTHLY_RENT, OWNER_NUM))
>   </dd>
> </dl>
>
> **Answer**:
>
> The functional dependencies that exist are:
> <dl>
>   <dd>
>       OFFICE_NUM &rarr; OFFICE_NAME, ADDRESS
>   </dd>
>   <dd>
>       OFFICE_NUM, ADDRESS &rarr; SQR_FT, BDRMS, FLOORS, MONTHLY_RENT, OWNER_NUM
>   </dd>
> </dl>
>
> An equivalent collection of tables that are in third normal form are:
>
> <dl>
>   <dd>
>       OFFICE (<ins>OFFICE_NUM </ins>, OFFICE_NAME, ADDRESS)
>   </dd>
>   <dd>
>       OFFICE_ADDRESS (<ins>OFFICE_NUM</ins>, <ins>ADDRESS</ins>, SQR_FT, BDRMS, FLOORS, MONTHLY_RENT, OWNER_NUM)
>   </dd>
> </dl>
>
>
> **Q-2**: Determine the functional dependencies that exist in the following table and then convert this table to an equivalent collection of tables that are in third normal form.
>
> <dl>
>   <dd>
>       PROPERTY (PROPERTY_ID, OFFICE_NUM, ADDRESS, SQR_FT, BDRMS, FLOORS, MONTHLY_RENT, OWNER_NUM, LAST_NAME, FIRST_NAME)
>   </dd>
> </dl>
>
> **Answer**:
>
> The functional dependencies that exist are:
>
> <dl>
>   <dd>
>       PROPERTY_ID &rarr; OFFICE_NUM, ADDRESS, SQR_FT, BDRMS, FLOORS, MONTHLY_RENT, OWNER_NUM
>   </dd>
>   <dd>
>       OWNER_NUM &rarr; LAST_NAME, FIRST_NAME
>   </dd>
> </dl>
>
> An equivalent collection of tables that are in third normal form are:
>
> <dl>
>   <dd>
>       PROPERTY (<ins>PROPERTY_ID</ins>, OFFICE_NUM, ADDRESS, SQR_FT, BDRMS, FLOORS, MONTHLY_RENT, OWNER_NUM)
>   </dd>
>   <dd>
>       OWNER (<ins>OWNER_NUM</ins>, LAST_NAME, FIRST_NAME)
>   </dd>
> </dl>
>
> **Q-3**: StayWell also rents out properties on a weekly basis to students attending summer school in the Seattle area. Design a database to meet the following requirements, using the shorthand representation and a diagram of your choice.
> <ol style="list-style-type:lower-alpha;">
>   <li>
>       For each student renter, list his or her number, first name, middle initial, last name, address, city, state, postal code, telephone number, and e-mail address.
>   </li>
>   <li>
>       For each property, list the office number, property address, city, state, postal code, square footage, number of bedrooms, number of floors, maximum number of persons that can sleep in the unit, and the base weekly rate.
>   </li>
>   <li>
>       For each rental agreement, list the renter number, first name, middle initial, last name, address, city, state, postal code, telephone number, start date of the rental, end date of the rental, and the weekly rental amount. The rental period is one or more weeks.
>   </li>
> </ol>
>
> **Answer**:
>
> From the first requirement, we can come up with the following table:
>
> <dl>
>   <dd>
>       STUDENT (STUDENT_NUM, FIRST_NAME, MIDDLE_INITIAL, LAST_NAME, ADDRESS, CITY, STATE, POSTAL_CODE, TELEPHONE_NUMBER, EMAIL_ADDRESS)
>   </dd>
> </dl>
>
> From the second requirement, we can come up with the following table:
>
> <dl>
>   <dd>
>       PROPERTY(PROPERTY_ID, OFFICE_NUMBER, ADDRESS, CITY, STATE, POSTAL_CODE, SQUARE_FOOTAGE, NUMBER_OF_BEDROOMS, NUMBER_OF_FLOORS, NUMBER_OF_PERSONS, BASE_WEEEKLY_RATE)
>   </dd>
> </dl>
>
> From the third requirement, we can come up with the following table:
>
> <dl>
>   <dd>
>       RENTAL_AGREEMENT (STUDENT_NUM, STUDENT_FIRST_NAME, STUDENT_MIDDLE_INITIAL, STUDENT_LAST_NAME, STUDENT_ADDRESS, STUDENT_CITY, STUDENT_STATE, STUDENT_POSTAL_CODE, STUDENT_TELEPHONE_NUMBER, START_DATE, END_DATE, WEEKLY_RENTAL_AMOUNT)
>   </dd>
> </dl>
> 
> The RENTAL_AGREEMENT table will be related to the STUDENT table using the STUDENT_NUM columns, and to the PROPERTY table using the PROPERTY_ID columns. There will be a one-to-many relationship between RENTAL_AGREEMENT and STUDENT (one student can have many rental agreements), and between RENTAL_AGREEMENT and PROPERTY (one property can have many agreements.)
>
> The relationships between the STUDENT, PROPERTY, and RENTAL AGREEMENT entities can be represented by using the following E-R diagram.
>
> ![Figure: E-R diagram showing the relationship between STUDENT, PROPERTY, and RENTAL AGREEMENT](./images/figure-e-r-diagram-showing-the-relationship-between-student-property-and-rental-agreement.JPG)


## MODULE 3: CREATING TABLES

### INTRODUCTION

- In this module, you begin your study of **Structured Query Language (SQL)**, which is one of the most popular and widely used languages for retrieving and manipulating database data.
- In the mid-1970s, SQL was developed as the data manipulation language for IBM’s prototype relational model DBMS, System R, under the name SEQUEL at IBM's San Jose research facilities. In 1980, the language was renamed SQL (but still pronounced sequel although the equally popular pronunciation of S-Q-L [ess-cue-ell] is preferable) to avoid confusion with an unrelated hardware product named SEQUEL. Most DBMSs use a version of SQL as their data manipulation language.
- In this module, you learn: 
    - the basics of working in SQL.
    - how to create tables and assign data types to columns.
    - about a special type of value, called a null value, and learn how to manage these values in tables. 
    - how to insert data into your tables after you create them. 
    - how to describe a table’s layout using SQL.

### CREATING AND RUNNING SQL COMMANDS

- You accomplish tasks in SQL by creating and running commands using a DBMS that
supports SQL. This text uses MySQL to create and run SQL commands. The text also
indicates differences you find if you are using Oracle or Microsoft SQL Server.
- The version of MySQL used in this text is MySQL 8.0 (specifically MySQL Community
Server 8.0.18). You can download and install the latest version, and previous versions, of MySQL 8.0 edition for free from the MySQL Web site (https://dev.mysql.com). Although you may choose any of the setup types during installation dependent upon your needs, to be able to perform operations presented in this text, it is suggested you choose the Developer Default setup type or the Full option. Either of these options include the installation of the MySQL Workbench. MySQL Workbench contains many powerful tools that allows developers and database administrators to visually design, develop, and administer MySQL databases. The MySQL Workbench also contains an SQL editor that is used throughout the text to enter commands and view the results of the commands entered. Be sure to remember the password selected during installation.

#### Using MySQL Workbench

- After installing MySQL 8.0, run the MySQL Workbench 8.0 CE app using whatever method you prefer for running an app (You can download it from https://dev.mysql.com/downloads/workbench/). On the MySQL Workbench opening window, you notice links where you may browse MySQL documentation, access a MySQL blog, and participate in forums related to MySQL. On this main window, you also see a list of the MySQL connections currently available to you. The one connection listed is to the server created during the installation of MySQL. See Figure 3-1.

![FIGURE 3-1 MySQL Workbench opening window](./images/FIGURE-3-1-MySQL-Workbench-opening-window.JPG)


- Click on the connection box Local instance *MySQL80*. MySQL80 was the default name given during installation if you accepted the defaults. The name may be different if you changed the name during installation. Next provide the password to access the server you created during installation. See Figure 3-2.

![FIGURE 3-2 Entering password for server](./images/FIGURE-3-2-Entering-password-for-server.JPG)

- Once you have successfully submitted the password for the connection, you are given
access to the main MySQL Workbench environment for that connection. See Figure 3-3.

![FIGURE 3-3 Main MySQL Workbench environment](./images/FIGURE-3-3-Main-MySQL-Workbench-environment.JPG)

- Remember that MySQL Workbench is a very powerful tool that contains many features. We only use the SQL editor within the MySQL Workbench for our purposes. Therefore, we can simplify, or unclutter, the window by hiding some of the panes. The two panes we would like to hide are the Navigation pane and the MySQL Additions pane. To hide these two panes, click on their corresponding toggle button as show in Figure 3-3. The result of hiding the Navigator pane and the SQL Additions pane gives more room for the Query pane and the Output pane. Each pane expands to fill the original window as shown in Figure 3-4.

![FIGURE 3-4 Outcome of hiding the Navigator and SQL Additions panes](./images/FIGURE-3-4-Outcome-of-hiding-the-Navigator-and-SQL-Additions-panes.JPG)

The next step is to begin entering SQL commands in the MySQL Workbench
environment. 

#### Entering Commands

- Before creating a database on our own, we can first get used to the MySQL Workbench environment by entering a simple SQL command and going through the process to have it executed. MySQL has internal databases it uses to handle its internal processing. These databases will be separate from the database we will be creating; however, they are viewable. Because we have not yet created any databases on our own, and just installed MySQL, any databases listed will be internal to MySQL. To show the databases on a MySQL server host you use the SHOW DATABASES command followed by a semicolon. A semicolon ends a statement in SQL. The syntax is shown in Figure 3-5.

![FIGURE 3-5 Syntax of the SHOW DATABASES command](./images/FIGURE-3-5-Syntax-of-the-SHOW-DATABASES-command.JPG)

- The next step is to enter the `SHOW DATABASES;`command into the MySQL Workbench SQL editor. Enter the command on the first line as show in Figure 3-6. Be sure to enter the semicolon after the command.

![FIGURE 3-6 Enter SHOW DATABASES command](./images/FIGURE-3-6-Enter-SHOW-DATABASES-command.JPG)

- Notice as you entered the command, the keywords of <span style="color: blue">SHOW DATABASES</span> turn blue.
This color of blue is used to represent keywords in the SQL editor within the MySQL
Workbench. This color scheme is the Microsoft Windows default scheme and can be modified if preferred; however, for the remainder of the text we continue using this color of blue for keywords.
- The next step is to execute the command entered. On the main menu, select the Query menu and select Execute Current Statement as shown in Figure 3-7. This executes the statement you just entered. Note that you could have also selected Execute (All or Selected) because there was only one SQL statement entered.

![FIGURE 3-7 Execute the query](./images/FIGURE-3-7-Execute-the-query.JPG)

> **HELPFUL HINT**
> Although some environments may not require a semicolon to end an SQL statement, it is always good practice to do so. For in the event you are using an environment in which it is required and do not include the semicolon, an error will occur. Always follow proper coding practice for any language you are using, regardless of whether the environment is forgiving or not.

- Once the command is executed, a result grid is displayed between the query pane and output pane. Note on the right-hand side of the result grid there are other options available; however, we will not be using them at present. The result of the command SHOW DATABASES lists the databases available in the MySQL server connection. Note we did not create any of these databases; instead, these six internal databases are used by MySQL for its purposes. You may need to use the vertical scroll bar on the right side of the result grid, or adjust the vertical size of the grid, to view all of the databases. Also note in the output pane there is information pertaining to the execution of the statement, such as the time of day it was executed, general description of the processing, outcome, and the time it took for the processing to occur. Note under the message column in the output pane that six rows were returned, which corresponds to the six databases listed. The green circle with a checkmark indicates the command executed successfully. See Figure 3-8.

![FIGURE 3-8 Outcome of SHOW DATABASES command](./images/FIGURE-3-8-Outcome-of-SHOW-DATABASES-command.JPG)

> **HELPFUL HINT**
> - Note that your specific version of MySQL may have a different number of internal databases listed. This presents no issues.

- To clear the result grid, click on the "x" located on the bottom left of the result grid after "Result #." The grid is removed, and the query and output panes remain. To remove the details from output pane, you may right-click anywhere while the cursor is on the row or pane pertaining to the action. When the menu appears, select the Clear option from the menu, and the information is removed. If you wish to review any history of processing commands, you can click the drop-down arrow beside Action Output in the output pane and select History Output. See Figure 3-9.

![FIGURE 3-9 To clear results of the SHOW DATABASES command](./images/FIGURE-3-9-To-clear-results-of-the-SHOW-DATABASES-command.JPG)

- Now that you have entered and executed an SQL command in MySQL Workbench, the next step is to create your own database. Prior to creating your own database, you can clear the query pane by simply highlighting the command and deleting it, or any other method you prefer. You should now have a MySQL Workbench window similar to Figure 3-4, prior to entering any commands and only the query and output panes showing.

> **HELPFUL HINT**
> - Although it is not necessary to clear the query and output panes as you progress to creating a database of your own, it is cleared during the presentation in the textbook to make the examples more readable and easier to understand. This way you can focus on one command, or group of commands, at a time and not constantly viewing previous commands or results.

### CREATING A DATABASE

- There are many objects within a database, including tables and fields. All of these objects have identifiers, or names, associated with them. DBMS rules for naming identifiers vary dependent upon the DBMS. For example, in the version of MySQL used in this text, identifier names for a database, table, or a field can be up to 64 characters; however, that doesnot mean that you should give your identifiers names of that length. It is simply permitted if the need arises to properly describe the object. If you want to name identifiers very uniquely in any DBMS, you should consult the documentation for that specific DMBS. The documentation for naming identifiers in the version of MySQL used in this text can be found at https://dev.mysql.com/doc/refman/8.0/en/identifiers.html. General guidelines that are acceptable to most DBMS are given below. If you adhere to these guidelines for naming identifiers when using a DBMS, it is rare that you will have an issue.

  1. The identifier name cannot exceed 30 characters.
  2. The identifier name must start with a letter.
  3. The identifier name can contain letters, numbers, and underscores (_).
  4. The identifier name cannot contain spaces.

- Prior to defining the objects within a database, the first step is to create the database itself. The command in MySQL to create a database is **CREATE DATABASE** followed by the name of the database. To create a database named KIMTAY, for example, the command is <span style="color: blue">CREATE DATABASE</span> KIMTAY; as shown in Figure 3-10. Note that a semicolon ends the command.

![FIGURE 3-10 Syntax of the CREATE DATABASE command](./images/FIGURE-3-10-Syntax-of-the-CREATE-DATABASE-command.JPG)

Enter the command to create the KimTay database into the MySQL Workbench SQL editor. Execute the command similar to how you executed the SHOW DATABASES command and view the results. See Figure 3-11.

![FIGURE 3-11 Enter SHOW DATABASES command](./images/FIGURE-3-11-Enter-SHOW-DATABASES-command.JPG)

- Execute the <span style="color: blue">SHOW DATABASES</span>; command as you did previously and view the results in Figure 3-12. The results are now different because the KimTay database has been added, with seven databases now listed. Six of the databases will be internal to MySQL; however, the one additional database is the one you just created.

![FIGURE 3-12 Outcome of SHOW DATABASES command after creating the KimTay database](./images/figure-3-12-outcome-of-show-databases-command-after-creating-the-kimtay-database.JPG)

- Now the KimTay database has been created, you need to create the tables that will reside within the database. In addition, you need to populate the tables with the data from the previous modules. First, we begin by creating the table that holds the sales reps.

#### Changing the Default Database

- To work with a database, you must change the default database to the one you need to use. The default database is the database to which all subsequent commands pertain. To activate the default database, execute the USE command followed by the name of the database. For example, to change the default database to the one you just created for KimTay Pet Supplies, the command would be USE KIMTAY;, as shown in Figure 3-13. Changing the default database is also known as activating or using the database.

![FIGURE 3-13 Syntax of the USE command](./images/figure-3-13-syntax-of-the-use-command.JPG)

- Execute the command to activate the KIMTAY database and see the results in
Figure 3-14.

![FIGURE 3-14 Enter USE command to activate the KIMTAY database](./images/figure-3-14-enter-use-command-to-activate-the-kimtay-database.JPG)

- Now that the default database has been set to the KIMTAY database, you can now
begin to add the tables to the database.

### CREATING A TABLE

- The first step in creating a table is to describe the layout of the table to the DBMS.

**EXAMPLE 1: Describe the layout of the SALES_REP table to the DBMS.**

- You use the **CREATE TABLE** command to describe the layout of a table. The word TABLE is followed by the name of the table to be created and then by the names and data types of the columns that the table contains (for example, characters, numbers, or dates) as well as the maximum number of characters or digits that the column can store.
- In the previous modules we chose the name SALES_REP to contain the information
pertaining to sales reps employed by KimTay Pet Supplies. The SQL command that creates the SALES_REP table is shown in Figure 3-15.

![FIGURE 3-15 CREATE TABLE command to create the SALES_REP table](./images/figure-3-15-create-table-command-to-create-the-sales_rep-table.JPG)

- This CREATE TABLE command, which uses the data definition features of SQL, describes a table named SALES_REP. The table contains ten columns: REP_ID, FIRST_NAME, LAST_NAME, ADDRESS, CITY, STATE, POSTAL, CELL_PHONE, COMMISSION, and RATE. The REP_ID column can store two characters and is the table’s primary key. The FIRST_NAME and LAST_NAME columns can store 20 characters each, and the STATE column can store two characters. The COMMISSION column can store only numbers, and those numbers are limited to seven digits, including two decimal places. Similarly, the RATE column can store three-digit numbers, including two decimal places. You can think of the SQL command shown in Figure 3-15 as creating an empty table with column headings for each column name.
- In SQL, commands are free format; that is, no rule says that a particular word
must begin in a particular position on the line. For example, you could have written the CREATE TABLE command shown in Figure 3-15 as follows:

```sql
CREATE TABLE SALES_REP (REP_ID CHAR(2) PRIMARY KEY, FIRST_NAME CHAR(20), 
LAST_NAME CHAR(20), ADDRESS CHAR(20), CITY CHAR(15), STATE CHAR(2), 
POSTAL CHAR(5), CELL_PHONE CHAR(12), COMMISSION DECIMAL(7,2), RATE DECIMAL(3,2));
```
- It should be noted that the PRIMARY KEY clause in the previous statement specifies that REP_ID will be the unique identifier to the row meaning "No Duplicate" are allowed for the column.
- The manner in which the CREATE TABLE command shown in Figure 3-15 was
written makes the command more readable. This text strives for such readability when writing SQL commands.

> **HELPFUL HINT**
> - Making code readable is extremely important. The more readable the code, the easier it is to understand and modify. Proper indentation can make code much more readable compared to code that is not indented properly. There is no one way to indent code to make it more readable, each coder will have his/her on way of indenting code for readability. This text attempts to make code much more readable through proper indentation and spacing to maximize readability.
>
> **HELPFUL HINT**
> - SQL is not case sensitive; you can type commands using uppercase or lowercase letters. There is one exception to this rule, however. When you are inserting character values into a table, you must use the correct case.
>
> - To create the SALES_REP table in MySQL Workbench, enter and execute the command shown in Figure 3-15 as you did with the previous commands. Once again, there is a different color scheme for various parts of the command as you enter it. Figure 3-16 shows the executed command and results. The figures in this text may show the panes resized so that more of the command or results is visible to the user.

![FIGURE 3-16 Enter CREATE TABLE command to create the SALES_REP table](./images/figure-3-16-enter-create-table-command-to-create-the-sales_rep-table.JPG)

![ORACLE FIGURE 3-1 CREATE TABLE statement to create SALES_REP table using Oracle](./images/oracle-figure-3-1-create-table-statement-to-create-sales_rep-table-using-oracle.JPG)

![SQL SERVER FIGURE 3-1 CREATE TABLE statement to create SALES_REP table using SQL Server](./images/sql-server-figure-3-1-create-table-statement-to-create-sales_rep-table-using-sql-server%20(2).JPG)

- Although there was verification from MySQL that the table was created, you may view the list of tables within an activated database by using the SHOW TABLES; command. This command is similar to the SHOW DATABASES command you used previously, but instead it gives you a list of tables residing in the current database in use. In our case, this results in a list of the tables residing in the KIMTAY database. See Figure 3-17 for the results of the command.

![FIGURE 3-17 Outcome of SHOW TABLES command listing the tables in the KIMTAY database](./images/figure-3-17-outcome-of-show-tables-command-listing-the-tables-in-the-kimtay-database.JPG)

#### Correcting Errors in SQL Commands

- Suppose that you attempted to create the SALES_REP table using the CREATE TABLE command shown in Figure 3-18, which contains several mistakes. Instead of displaying a message that the table was created successfully, MySQL displays an error message about a problem that it encountered. In reviewing the command, you see that CHAR is misspelledon line 5, the CITY column was omitted, and line 8 should be deleted. If you run a command and MySQL Workbench displays an error, you can use the mouse and the arrow keys on the keyboard to position the insertion point in the correct position so you can correct these errors using the same techniques that you might use in a word processor. For example, you can use the pointer to select the word CHR on line 5 and type CHAR, and then you can use the pointer to move the insertion point to the end of line 5 so you can press Enter to insert the missing information to create the CITY column. You can use the pointer to select the contents of line 8 and then press Delete to remove it. After making these changes, you can click the Run button to execute the command again. If the command contains additional errors, you see an error message again. If the command is correct, you see the message that the table was created.

![FIGURE 3-18 CREATE TABLE command with errors](./images/figure-3-18-create-table-command-with-errors.JPG)

You may have also noticed that the SQL editor within the MySQL Workbench indicated there was a syntax error in the command on line 5 prior to executed, as indicated by the small red box with an X in it beside the line. The SQL editor is quite advanced and understands the correct syntax as you enter the commands. In addition, note that omitting the CITY column and inserting a XYZ column do not produce syntax errors. Instead, they are considered logic errors on your part.

#### Dropping a Table

- After creating a table, you might notice that you added a column that you do not need or that you assigned the wrong data type or size to a column. One way to correct such errors in a table is simply to delete (drop) the table and start over. For example, suppose you wrote a CREATE TABLE command that contained a column named LST instead of LAST or defined a column as CHAR(5) instead of CHAR(15). Suppose you do not discover the rror and you execute the command, creating a table with these problems. In this case, you can delete the entire table using the **DROP TABLE** command and then re-create the table using the correct CREATE TABLE command.
- To drop a table, execute the **DROP TABLE** command, followed by the name of the table you want to delete and a semicolon. To delete the SALES_REP table, for example, you would enter and execute the following command:

```sql
DROP TABLE SALES_REP
```

- Dropping a table also deletes any data that you entered into the table. It is a good idea to check your CREATE TABLE commands carefully before executing them and to correct any problems before adding data. Later in this text, you learn how to change a table’s structure without having to delete the entire table.

> **Q & A**
> - **Question**: How can I correct a mistake that I made when I created a table?
> - **Answer**: Later in the text, you see how to alter a table to make any necessary corrections. For now, the easiest way is to drop the table using the DROP TABLE command and then to execute the correct CREATE TABLE command.

### USING DATA TYPES

- For each column in a table, you must specify the data type to use to store the type of data that the column contains. Figure 3-19 describes some common data types used in databases.

| DataType | Description |
| --- | --- |
| CHAR(n) | Stores a character string n characters long. You use the CHAR data type for columns that contain letters and special characters, and for columns containing numbers that will not be used in any calculations. Because neither sales rep ID numbers nor customer ID numbers will be used in any calculations, for example, the REP_ID and CUST_ID columns are both assigned the CHAR data type. |
| VARCHAR(n) | An alternative to CHAR that stores a character string up to n characters long. Unlike CHAR, only the actual character string is stored. If a character string 20 characters long is stored in a CHAR(30) column, for example, it will occupy 30 characters (20 characters plus 10 blank spaces). If it is stored in a VARCHAR(30) column, it will only occupy 20 spaces. In general, tables that use VARCHAR instead of CHAR occupy less space, but the DBMS does not process them as rapidly during queries and updates. However, both are legitimate choices. This text uses CHAR, but VARCHAR works equally well.
| DATE | Stores date data. The specific format in which dates are stored varies from one SQL implementation to another. In MySQL and SQL Server, dates are enclosed in single quotation marks and have the format YYYY-MM-DD (for example, ‘2020-10-23’ is October 23, 2020). In Oracle, dates are enclosed in single quotation marks and have the format DD-MON-YYYY (for example, '23-OCT-2020' is October 23, 2020). |
| DECIMAL(p,q) | Stores a decimal number p digits long with q of the digits being decimal places to the right of the decimal point. For example, the data type DECIMAL(5,2) represents a number with three places to the left and two places to the right of the decimal (for example, 123.45). You can use the contents of DECIMAL columns in calculations. You also can use the NUMERIC(p,q) data type in MySQL to store a decimal number. Oracle and SQL Server also use NUMBER(p, q) to store a decimal number. |
| INT | Stores integers, which are numbers without a decimal part. The valid range is –2147483648 to 2147483647. You can use the contents of INT columns in calculations. If you follow the word INT with AUTO_INCREMENT, you create a column for which SQL will automatically generate a new sequence number for each time you add a new row. This would be the appropriate choice, for example, when you want the DBMS to generate a value for a primary key.|
| SMALLINT | Stores integers but uses less space than the INT data type. The valid range is –32768 to 32767. SMALLINT is a better choice than INT when you are certain that the column will store numbers within the indicated range. You canuse the contents of SMALLINT columns in calculations.|

FIGURE 3-19 Commonly used data type

### USING NULLS

- Occasionally, when you enter a new row into a table or modify an existing row, the values for one or more columns are unknown or unavailable. For example, you can add a customer’s name and address to a table even though the customer does not have an assigned sales rep or an established credit limit. In other cases, some values might never be known—perhaps there is a customer that does not have a sales rep. In SQL, you handle this situation by using a special value to represent cases in which an actual value is unknown, unavailable, or not applicable. This special value is called a null data value, or simply a null. When creating a table, you can specify whether to allow nulls in the individual columns.

**Q & A**
- **Question**: Should a user be allowed to enter null values for the primary key?
- **Answer**: No. The primary key is supposed to uniquely identify a given row, and this would be impossible if nulls were allowed. For example, if you stored two customer records without values in the primary key column, you would have no way to tell them apart.
- In SQL, you use the **NOT NULL** clause in a CREATE TABLE command to indicate columns that cannot contain null values. The default is to allow nulls; columns for which you do not specify NOT NULL can accept null values.
- For example, suppose that the FIRST_NAME and LAST_NAME columns in the SALES_REP table cannot accept null values, but all other columns in the SALES_REP table can. The CREATE TABLE command in Figure 3-20 accomplishes this goal.

![FIGURE 3-20 CREATE TABLE command with NOT NULL clauses](./images/figure-3-20-create-table-command-with-not-null-clauses.JPG)

- If you created the SALES_REP table with this CREATE TABLE command, the DBMS would reject any attempt to store a null value in either the FIRST_NAME or LAST_NAME column. The database allows storing NULL values in the ADDRESS column because it was created without specifying NOT NULL when the table was created. Because the primary key column cannot accept null values, you do not need to specify the REP_ID column as NOT NULL.

### ADDING ROWS TO A TABLE

- After you have created a table in a database, you can load data into the table by using the INSERT command.

#### The INSERT Command

- The **INSERT** command adds rows to a table. You type <span style="color: blue">INSERT INTO<span> followed by the name of the table into which you are adding data. Then you type the word <span style="color: blue">VALUES<span> followed by the specific values to be inserted in parentheses. When adding rows to character columns, make sure you enclose the values in single quotation marks (for example, "Susan"). You also must enter the values in the appropriate case, because character data is stored exactly as you enter it.

> **HELPFUL HINT**
> - You must enclose values in single quotation marks for any column whose type is character (CHAR), even when the data contains numbers. Because the POSTAL column in the SALES_REP table has a CHAR data type, for example, you must enclose postal codes in single quotation marks, even though they are numbers.
> - If you need to enter an apostrophe (single quotation mark) into a column, you type two single quotation marks. For example, to enter the name O'Toole in the LAST_NAME column, you would type "O'Toole" as the value in the INSERT command.

**EXAMPLE 2: Add sales rep 05 to the SALES_REP table.**

- The command for this example is shown in Figure 3-21. Note that the character strings ("05," "Susan," "Garcia," and so on) are enclosed in single quotation marks. When you execute the command, the record is added to the SALES_REP table.

![FIGURE 3-21 INSERT command to add sales rep 05 to the SALES_REP table](./images/figure-3-21-insert-command-to-add-sales-rep-05-to-the-sales_rep-table.JPG)

- The result of the command being entered and executed is shown in Figure 3-22.

![FIGURE 3-22 INSERT command executed for the first record in the SALES_REP table](./images/figure-3-22-insert-command-executed-for-the-first-record-in-the-sales_rep-table.JPG)

> - **HELPFUL HINT**
> - Make sure that you type the values in the same case as those shown in the figures to avoid problems later when retrieving data from the database.

**EXAMPLE 3: Add sales reps 10 and 15 to the SALES_REP table.**

- You could enter and execute new INSERT commands to add the new rows to the table. However, an easier and faster way to add these new rows to the table is to use the mouse and the keyboard to modify the previous INSERT command and execute it to add the record for the second sales rep. Figure 3-23 shows the new command to add the second record containing the data for sales rep 10. Simply use the mouse and keyboard to modify the command and execute it. Note that if it is easier for you to delete the previous command and enter the new command from the beginning, it is absolutely fine.

![FIGURE 3-23 INSERT command to add sales rep 10 to the SALES_REP table](./images/figure-3-23-insert-command-to-add-sales-rep-10-to-the-sales_rep-table.JPG)

- Figure 3-24 shows the results of the command being entered and executed to add the second record to the SALES_REP table, containing the data for sales rep 10.

![FIGURE 3-24 INSERT command executed for the second record in the SALES_REP table](./images/figure-3-24-insert-command-executed-for-the-second-record-in-the-sales_rep-table.JPG)

- The next command to add the third record, containing the data for sales rep 15, is shown in Figure 3-25. Enter the command by modifying the previous command, or deleting the previous command and entering the new command from the beginning. Once entered, execute the command.

![FIGURE 3-25 INSERT command to add sales rep 15 to the SALES_REP table](./images/figure-3-25-insert-command-to-add-sales-rep-15-to-the-sales_rep-table.JPG)

- Figure 3-26 shows the results of the command being entered and executed to add the third record to the SALES_REP table, containing the data for sales rep 15.

![FIGURE 3-26 INSERT command executed for the third record in the SALES_REP table](./images/figure-3-26-insert-command-executed-for-the-third-record-in-the-sales_rep-table.JPG)

- The next command to add the fourth record, containing the data for sales rep 20, is shown in Figure 3-27. Enter the command by modifying the previous command or by deleting the previous command and entering the new command from the beginning. Once entered, execute the command.

![FIGURE 3-28 INSERT command executed for the fourth record in the SALES_REP table](./images/figure-3-28-insert-command-executed-for-the-fourth-record-in-the-sales_rep-table.JPG)

#### Inserting a Row that Contains Nulls

- To enter a null value into a table, you use a special form of the INSERT command in which you identify the names of the columns that accept non-null values and then list only these non-null values after the VALUES command, as shown in Example 4.

![FIGURE-3-29-INSERT-command-to-add-sales-rep-25-to-the-SALES_REP-table](./images/FIGURE-3-29-INSERT-command-to-add-sales-rep-25-to-the-SALES_REP-table.JPG)

Figure 3-30 shows the results of the command being entered and executed to add the fifth record to the SALES_REP table, containing the data for sales rep 25; however, only the REP_ID, FIRST_NAME, and LAST_NAME fields are added. The remaining fields contain null values. The order of the data aligns with the order of the fields. The value of "25" is inserted into the REP_ID field, the value of "Donna" is inserted into the FIRST_NAME field, and the value of "Sanchez" is inserted into the LAST_NAME field.

![FIGURE 3-30 INSERT command executed for the fifth record in the SALES_REP table containing null values](./images/figure-3-30-insert-command-executed-for-the-fifth-record-in-the-sales_rep-table-containing-null-values.JPG)

### VIEWING TABLE DATA

-To view the data in a table, you use the **SELECT** command, which is described in more detail in Modules 4 and 5. 

**EXAMPLE 5: Display all the rows and columns in the SALES_REP table.**

- You can use a simple version of the SELECT command to display all the rows and columns in a table by typing the word <span style="color: blue">SELECT</span>, followed by an asterisk (*), followed by the keyword FROM and the name of the table containing the data you want to view. Just as with other SQL commands, the command ends with a semicolon. In MySQL, you type the command shown in Figure 3-31.

![FIGURE 3-31 Select command to list all records in the SALES_REP table](./images/figure-3-31-select-command-to-list-all-records-in-the-sales_rep-table.JPG)

- Figure 3-32 shows the results of the command being entered and executed, along with the results shown in the results grid. As you can see, in the fifth record the data for the REP_ID, FIRST_NAME, and LAST_NAME fields have been inserted as you wanted. The remaining fields in the fifth record contain null values.

 ![FIGURE 3-32 Using a SELECT command to view a table](./images/figure-3-32-using-a-select-command-to-view-a-table.JPG)

 ![ORACLE FIGURE 3-2 SELECT statement showing all rows in SALES_REP table using Oracle](./images/oracle-figure-3-2-select-statement-showing-all-rows-in-sales_rep-table-using-oracle.JPG)

 ![![SQL SERVER FIGURE 3-2 SELECT statement showing all rows in SALES_REP table using SQL Server]()](./images/sql-server-figure-3-2-select-statement-showing-all-rows-in-sales_rep-table-using-sql-server.JPG)


 ### CORRECTING ERRORS IN A TABLE

 - After executing a SELECT command to view a table’s data, you might find that you need to change the value in a column. You can use the UPDATE command to change a value in a table. The UPDATE command shown in Figure 3-33 changes the last name in the row on which the sales rep ID is 25 to Salinas.

![FIGURE 3-33 UPDATE command to change the LAST_NAME for sales rep 25](./images/figure-3-33-update-command-to-change-the-last_name-for-sales-rep-25.JPG)

- Figure 3-34 shows the results of the command being enter and executed. Note the message in the output gives further detail that one row was affected, with one row matching the criteria and one row being changed.
- The same SELECT command used in Figure 3-31 to list all of the records in the SALES_REP table can be used again to show the results of the UPDATE command just executed in Figure 3-34. Figure 3-35 shows the SELECT command being entered and executed, along with displaying the results of the UPDATE command from Figure 3-34, in which the last name for rep number 25 is Salinas.

![figure-3-34-using-an-update-command-to-change-a-value](./images//figure-3-34-using-an-update-command-to-change-a-value.JPG)

![FIGURE 3-35 Using a SELECT command to view a table](./images/figure-3-35-using-a-select-command-to-view-a-table.JPG)

![figure-3-36-delete-command-to-delete-all-records-where-the-sales-rep-id-is-25](./images/figure-3-36-delete-command-to-delete-all-records-where-the-sales-rep-id-is-25.JPG)

- Figure 3-37 shows the results of the command being entered and executed. Note the message in the output gives further detail in that one row was affected, or in this case deleted.

![FIGURE 3-37 Using the DELETE command to delete a row](./images/figure-3-37-using-the-delete-command-to-delete-a-row.JPG)

- The SELECT command can once again be used to display the records in the SALES_REP table. Figure 3-38 shows the command entered and executed, and it displays the updated data in the table. Note that the data associated with sales rep ID 25 no longer resides in the table.

![FIGURE 3-38 Using a SELECT command to view a table](./images/figure-3-38-using-a-select-command-to-view-a-table.JPG)

> **Q & A**
> Question: How do I correct errors in my data?
> Answer: The method you use to correct an error depends on the type of error you need to correct. If you added a row that should not be in the table, use a DELETE command to remove it. If you forgot to add a row, you can use an INSERT command to add it. If you added a row that contains incorrect data, you can use an UPDATE command to make the necessary corrections. Alternatively, you could use a DELETE command to remove the row containing the error and then use an INSERT command to insert the correct row.

### SAVING SQL COMMANDS

- MySQL lets you save SQL commands so you can use them again without retyping them. In MySQL, as well as in many other DBMSs, you save commands in a script file, or simply a script, which is a text file. In MySQL, script files have the .sql filename extension. Some DBMSs, such as Oracle, have a special location called the script repository to store the scripts. With MySQL, you can save your scripts in the location of your choice on your local file system (such as on a hard drive or USB flash drive), therefore, creating your own repository. The following steps describe how to create and use scripts in the MySQL Workbench. If you are using a different version of MySQL or another DBMS, use Help, consult the system documentation, or search the Internet to determine how to accomplish the same tasks.

> **Q & A**'
> **Question**: What are advantages of creating scripts?
> **Answer**: Creating a script offers some distinct advantages. You can create or edit a script using a text editor or word processor and save the script into your own script repository to be used in MySQL. A script can be created separately from the MySQL Workbench environment. Scripts allow you to create a group of SQL commands you would like to execute regularly and have them ready for use without rekeying them. Additionally, there are some advanced features you see later in this text that are only available when using scripts.

- To create a script in MySQL:
    1. Enter the command, or commands, you would like to comprise the script in the query pane.
    2. On the MySQL Workbench main menu, click on the File menu and select the Save Script As option.
    3. You may now navigate to a location in your file system you would like to save the script.
    4. Enter a name for your script in the File name: text box. Note the file type is an SQL file with an extension of .sql.
    5. When you are finished, click the Save button. You return to the query pane with the name of the tab being the name of your script.

- To view or edit a script in MySQL:
    1. On the MySQL Workbench main menu, click on the File menu and select
    Open SQL Script. 
    2. Navigate to the location in your file system where the script is saved.
    3. Select the script and click Open.
    4. Your script is now in a new tab in the query pane with the name being the
    same name as your script.
    5. You may now edit the script.

- To run an existing script in MySQL (Option #2):
    1. On the MySQL Workbench main menu, click on the File menu and select
    Run SQL Script.
    2. Navigate to the location in your file system where the script is saved.
    3. Select the script and click Open.
    4. In the Run SQL Script dialog box, select the Default Schema Name from the
    drop-down menu and click Run.
    5. After the results are displayed, you click on Close to close the Run SQL
    Script dialog box.

- When you are finished using a script and no longer need to store it, you can delete it.
- To delete a script in MySQL:
    1. Navigate to the location in your file system where the script is saved.
    2. Delete the file containing the script by the normal methods for your file
    system.

> **ORACLE USER NOTE**
> Oracle SQL Developer allows to save scripts any folder on your local system. All scripts created in Oracle SQL Developer are text files with the .sql filename extension. To create a script file in Oracle SQL Developer:
> 1. Load the Oracle SQL Developer tool, under Oracle Connections pane click on the desired database. (Note: Initially, you must create a connection entering account credentials as shown in Oracle Figure 3-3.)
> 2. Enter query statement you desire to store and execute the statement to validate it is syntactically correct and it returns the expected results.
> 3. Click the Save button and then enter a name for the script. 
> 
> To view, edit, or run an existing script:
> 1. Load Oracle SQL Developer and double click on Database Connection created previously.
> 2. Click the Open File button on the toolbar.
> 3. Navigate to the folder containing the script file and then click the Open button in the Open File dialog box. The script appears in the Query Editor window. You can view the content of the script to make changes to it by editing the commands. If you want to save your edits to a script, click the Save button to save your changes.
> 4. To run a script, click the Execute button.

![ORACLE FIGURE 3-3 Create Database Connection using Oracle SQL Developer](./images/oracle-figure-3-3-create-database-connection-using-oracle-sql-developer.JPG)

> **SQL SERVER USER NOTE**
> SQL Server can store scripts in any folder on your local system. All scripts created in SQL Server are text files with the .sql filename extension. To create a script file in SQL Server:
>   1. Load SQL Server Management Studio and then click the Connect button in the Connect to Server dialog box.
>   2. Open the appropriate database and then click the New Query button.
>   3. Type the command or commands to save in the script. When necessary, click the Execute button to execute the commands saved in the script.
>   4. When you are finished, click the Save button and then enter a name for the script.
> 
> To view, edit, or run an existing script:
>   1. Load SQL Server Management Studio and then click the Connect button in the Connect to Server dialog box.
>   2. Open the appropriate database and then click the New Query button.
>   3. Click the Open File button on the toolbar.
>   4. Navigate to the folder containing the script file and then click the Open button in the Open File dialog box. The script appears in the Query Editor window. You can view the content of the script to make changes to it by editing the commands. If you want to save your edits to a script, click the Save button to save your changes.
>   5. To run a script, click the Execute button.

### CREATING THE REMAINING DATABASE TABLES

- To create the remaining tables in the KimTay Pet Supplies database (KIMTAY), you need to execute the appropriate CREATE TABLE and INSERT commands. You should save these commands as scripts so you can re-create your database, if necessary, by running the scripts.

> **HELPFUL HINT**
> Your instructor might give you the script files to use to create the tables for KimTay Pet Supplies and StayWell Student Accommodation databases and to insert data into them.

- Figure 3-39 shows the CREATE TABLE command for the CUSTOMER table. Notice that the FIRST_NAME and LAST_NAME columns are specified as NOT NULL. Additionally, the CUST_ID column is the table’s primary key, indicating that the CUST_ID column is the unique identifier of rows in the table. With this column designated as the primary key, the DBMS rejects any attempt to store a customer ID that already exists in the table.

![FIGURE 3-39 CREATE TABLE command for the CUSTOMER table](./images/figure-3-39-create-table-command-for-the-customer-table.JPG)

- After creating the CUSTOMER table, you can create another file containing the
INSERT commands to add the customer rows to the table. When a script file contains
more than one command, each command must end with a semicolon. Figure 3-40 shows
the INSERT commands to add rows to the CUSTOMER table.

![FIGURE 3-40 INSERT commands for the CUSTOMER table](./images/figure-3-40-insert-commands-for-the-customer-table.JPG)

- Figures 3-41 through 3-46 show the scripts for the CREATE TABLE and INSERT commands for creating and inserting data into the INVOICES, ITEM, and INVOICE_LINE tables in the KimTay Pet Supplies database. Figure 3-41 contains the CREATE TABLE command for the INVOICES table.

![FIGURE 3-41 CREATE TABLE command for the INVOICES table](./images/figure-3-41-create-table-command-for-the-invoices-table.JPG)

- Figure 3-42 contains the INSERT commands to load data into the INVOICES table.
Notice the way that dates are entered.

![FIGURE 3-42 INSERT commands for the INVOICES table](figure-3-42-insert-commands-for-the-invoices-table)

- Figure 3-43 contains the CREATE TABLE command for the ITEM table.

![FIGURE 3-43 CREATE TABLE command for the ITEM table](./images/figure-3-43-create-table-command-for-the-item-table.JPG)

- Figure 3-44 contains the INSERT commands to load data into the ITEM table.

![FIGURE 3-44 INSERT commands for the ITEM table](./images/figure-3-44-insert-commands-for-the-item-table.JPG)

![FIGURE 3-44 INSERT commands for the ITEM table (Continued)](./images/figure-3-44-insert-commands-for-the-item-table-continued.JPG)

- Figure 3-45 contains the CREATE TABLE command for the INVOICE_LINE table. Notice the way that the primary key is defined when it consists of more than one column.

![FIGURE 3-45 CREATE TABLE command for the INVOICE_LINE table](./images/figure-3-45-create-table-command-for-the-invoice_line-table.JPG)

Figure 3-46 contains the INSERT commands to load data into the INVOICE_LINE
table.

![figure-3-46-insert-commands-for-the-invoice_line-table](./images/figure-3-46-insert-commands-for-the-invoice_line-table.JPG)

### DESCRIBING A TABLE

- The CREATE TABLE command defines a table’s structure by listing its columns, datatypes, and column lengths. The CREATE TABLE command also indicates which columns cannot accept nulls. When you work with a table, you might not have access to the CREATE TABLE command that was used to create it. For example, another programmer might have created the table, or perhaps you created the table several months ago but did not save the command. You might want to examine the table’s structure to see the details about the columns in the table. Each DBMS provides a method to examine a table’s structure.

**EXAMPLE 6: Describe the SALES_REP table.**

- In MySQL, you can use the DESCRIBE command to list all the columns in a table and their properties. Figure 3-47 shows the DESCRIBE command for the SALES_REP table, note that DESC, the abbreviated form of the DESCRIBE command, is accepted in MySQL and Oracle. The result indicates the name of each column in the table, along with its data type and length. The Null column indicates whether the field can accept a value of null. The Key column indicates which fields are part of the primary key.

![FIGURE 3-47 DESCRIBE command for the SALES_REP table](./images/figure-3-47-describe-command-for-the-sales_rep-table.JPG)

![ORACLE FIGURE 3-4 List of table columns using Oracle](./images/oracle-figure-3-4-list-of-table-columns-using-oracle.JPG)

![SQL SERVER FIGURE 3-3 List of table columns using SQL Server](./images/sql-server-figure-3-3-list-of-table-columns-using-sql-server.JPG)

### Module Summary

- Use the CREATE TABLE command to create a table by typing the table name and then
listing within a single set of parentheses the columns in the table.
- Use the DROP TABLE command to delete a table and all its data from the database.
- Some commonly used data types in are INT, SMALLINT, DECIMAL, CHAR, VARCHAR, and DATE.
- A null data value (or null) is a special value that is used when the actual value for a column is unknown, unavailable, or not applicable.
- Use the NOT NULL clause in a CREATE TABLE command to identify columns that cannot accept null values.
- Use the INSERT command to insert rows into a table.
- Use the SELECT command to view the data in a table.
- Use the UPDATE command to change the value in a column.
- Use the DELETE command to delete a row from a table.
- You can save SQL commands in a script file in MySQL, Oracle, and SQL Server.
- You can use the DESCRIBE command in MySQL and Oracle to display a table’s structure and layout. In SQL Server, execute the SP_COLUMNS stored procedure to display the structure and layout of a table.

### Key Terms

- CREATE DATABASE
- CREATE TABLE
- data type
- default database
- DELETE
- DESCRIBE
- DROP TABLE
- INSERT
- NOT NULL
- null
- null data value
- script
- script file
- script repository
- SELECT
- SHOW DATABASES
- Structured Query Language (SQL)
- UPDATE
- USE