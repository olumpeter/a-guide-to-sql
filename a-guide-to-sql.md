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
> **Answer**: Billy Rufton, James Gonzalez, Angie Hendricks, Leslie Smith

> **Q-2**: List the invoice numbers for invoices placed by customer ID 435 on November 18, 2021.
> **Answer**: 14228, 14233

> **Q-3**: List the item ID, item description, and on-hand value for each item in category HOR. (Hint: On-hand value is the result of multiplying the number of units on hand by the price.)
> **Answer**:
> | item ID | item description       | on-hand value  |
> | ---     | ---                    | ---            |
> | FM23    | Fly Mask with Ears     | $(41*24.95)    |
> | FS39    | Folding Saddle Stand   | $(12*39.99)    |
> | QB92    | Quilted Stable Blanket | $(32*119.99)   |
> | WB49    | Insulated Water Bucket | $(34*79.99)    |

> **Q-4**: List the item ID and item description of all items that are in category DOG.
> **Answer**:
> | item ID | item description         |
> | ---     | ---                      |
> | AD72    | Dog Feeding Station      |
> | DT12    | Dog Toy Gift Set         |
> | LD14    | Locking Small Dog Door   |
> | LP73    | Large Pet Carrier        |
> | UF39    | Underground Fence System |

> **Q-5**: How many customers have a balance that exceeds their credit limit?
> **Answer**: 1  Customer. Customer 375 (Melanie, Jackson).

> **Q-6**: What is the item ID, description, and price of the least expensive item in the database?
> **Answer**:
> | item ID | description            | price          |
> | ---     | ---                    | ---            |
> | KH81    | Wild Bird Food (25 lb) | $19.99         |

> **Q-7**: For each invoice, list the invoice number, invoice date, customer ID, and customer first and last names.
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
> **Answer**:
> | Invoice number | customer ID | customer first and last names| 
> | ---   | --- | ---            |
> | 14222 | 294 | Samantha Smith |
> | 14224 | 182 | Billy Rufton   |

> **Q-9**: 
> List the sales rep ID, and first and last names, for every sales rep who represents at least one customer with a credit limit of $1,000.
> **Answer**:
> | sales rep ID | first and last names |
> | --- | ---            | 
> | 15  | James Gonzalez | 
> | 10  | Leslie Smith   | 

> **Q-10**: For each invoice placed on November 15, 2021, list the invoice number, item ID, item description, and category for each item ordered.
> **Answer**:
> | Invoice number | Item ID | Item description | Category |
> | ---   | ---  | ---                          | --- |
> | 14216 | CA75 | Enclosed Cat Litter Station  | CAT |
> | 14219 | AD72 | Dog Feeding Station          | DOG |
> | 14219 | DT12 | Dog Toy Gift Set             | DOG |

- Critical Thinking
> **Q-1**: KimTay Pet Supplies needs to be able to contact customers when problems arise concerning an invoice. What other types of data could KimTay include in the CUSTOMER table to assist in contacting customers?
> **Answer**: Phone number

#### StayWell Student Accomodation

Answer each of the following questions using the StayWell data shown in Figures 1-4
through 1–9. No computer work is required.

> **Q-1.** List the owner number, last name, and first name of every property owner.
> **Answer**:
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
> **Answer**:
> | last name | first name |
> | --- | --- |
> | Patel | Makesh |
> | Aksoy | Ceyda |
> | Redman | Seth |
> | Jones | Ammarah |

> **Q-3.** List the property ID for each condo that is smaller than 1,600 square feet.
> **Answer**: 1, 3, 5, 9, 11

> **Q-4.** List the last name, first name, and city of every owner who owns more than one property in the database.
> **Answer**:
> | last name | first name | city |
> | --- | --- | --- |
> | Kowalczyk | Jakub | Bellingham |

> **Q-5.** List the last name, first name, and city of every owner with a property that has a monthly rent of less than $1,400 per month.
> **Answer**:
> | last name | first name | city |
> | --- | --- | --- |
> | Bianchi | Nicole | New York |
> | Sims | Haydon | Portland |
> | Patel | Makesh | Seattle |
> | Jones | Ammarah | Seattle |

> **Q-6.** List all the residents staying at 782 Queen Ln.
> **Answer**: Milosz Polansky, Ashanti Lucas, Randy Woodrue

> **Q-7.** How many properties have two floors?
> **Answer**: 5 (Property ID 2, 6, 7, 8, and 12)

> **Q-8.** How many owners live outside of Washington state (WA)?
> **Answer**: 4 owners. (Moore Elle-May, Sims Haydon, Burke Ernest, Bianchi Nicole)

> **Q-9.** List the owner’s last and first names and property IDs for each property that has a scheduled or open service request.
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
> **Answer**:
> | Property ID | Office number |
> | --- | --- |
> | 10 | 2 |
> | 8 | 2 |

> **Q-12.** What is the average rent for all three-bedroom properties?
> **Answer**:
>  (1400 + 1650 + 1700 + 1600 + 1700) / 5
