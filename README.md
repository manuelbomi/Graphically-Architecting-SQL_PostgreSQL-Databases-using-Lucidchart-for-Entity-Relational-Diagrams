# Graphically Architecting SQL (PostgreSQL) Databases using Lucidchart for Entity Relational Diagrams



### **OVERVIEW**
Reliably architecting databases is very crucial for designing efficient data analytics systems. After selecting the software and the database to be used for a system, the next important question is to decide on how to architect the database, and how to correctly specify the relationships between the entities in the database. To do this all-important architecting task, entity relationship diagrams (ERDs) are often used. 

After the data/system architect have specified the tables and their relationships, the modeler, database engineer, software engineer and/or the data engineer will then translate the ERD into SQL codes to create the desired database and tables for the target database.  

> [!NOTE]
> In some companies, the duties or tasks assigned to the data architect, system architect, data modeler, database engineer, data engineer or software engineer may ovelap. In most cases however, these engineers must often work hand-in-hand to achieve the desired objectives. 
---

### **Benefits of Using Lucidchart for Entity Relationship Diagrams**
For very complex systems, due to system intricacies and the number of engineers that may be involved in the system design, there may be errors, bugs or mismatches that are not easily detected between the architected system  and the final designed database. This is where the benefit(s) of using Lucidchart for architecting complex can be realized. Lucidchart is a visual collaborative software that everyone within a project can access, contribute to the ERDs and share the ERD updates among the team members.

In addition, Lucidchart can be used to shrink or eliminate an important step between architecting the system using ERDs and translating the archittected system to SQL codes for the target database. Eliminating this step can lead to reduction in mismatches or errors between the architected system and the final designed database. 

---

> [!IMPORTANT]
After using Lucidchart to architect the system using ERDs, Lucidchart can then be used to automatically generate SQL codes relating to the ERD for the target database. This step can serve to reduce errors or mismatches between the architected system and the designed database.
>

---
In this discourse, we will show (using infographs) how to use Lucidchart to architect an e-commerce database comprising of four tables viz: customers, products, orders and order_details tables.

We shall then show how to use Lucidchart to translate the e-commerce ERD to a database by using Lucidchart to automatically generate SQL codes for PostgreSQL database. 

---
> [!IMPORTANT]
Here, we have shown the steps needed to efficiently architect an e-commerce database for PostgreSQL database.
>
---


Step 1: Register free version LucidChart
---
![Image](https://github.com/user-attachments/assets/0d68a670-3833-448f-ba65-add57af15568)


---
Step 2: Click on 'Documents'. Click New, LucidChart, Start Diagramming.
---
![Image](https://github.com/user-attachments/assets/8ca6e2a8-2bec-4360-98c8-60c48fc26b9d)

---
Step 3:  Click New, LucidChart, Start Diagramming.
![Image](https://github.com/user-attachments/assets/049f1541-fb2a-4972-b2cf-02257a967879)
---

![Image](https://github.com/user-attachments/assets/600b3c3c-6095-4ab5-964b-759f2cde5d6b)

---
![Image](https://github.com/user-attachments/assets/72808a07-1297-4b10-8f0d-a38b4ca9e5e5)

---
Step 4: Search for ERD
---
![Image](https://github.com/user-attachments/assets/aba67e24-7349-43e4-b338-e6b771a01171)
---

Step 5: The Lucidchart ERD will reveal four ways to create an ERD. 
---
![Image](https://github.com/user-attachments/assets/74299c57-c31f-4821-960a-bd2ebba1b9da)

---
Step 6: The 'Key', 'Field', 'Type' (3 columns) ERD type is selected for our e-commerce use case. 
---
In this use case, four tables viz: customers, products, orders, and order_details were created. 
Relationship links such as one-to-many and many-to-one are used extensively to establish relationships between the tables. 
---

![Image](https://github.com/user-attachments/assets/75cf861e-9fb6-4ab1-952f-2b569dc626ec)

---
You can export the created ERD as png, jpeg, svg etc; to include in your report, slide or repository
---
![Image](https://github.com/user-attachments/assets/011480b1-7946-4561-a911-162fbaf412b9)
---

Step 7: After creating the ERD and establishing links, select all the tables and relations links in the ERD. 
Click on 'Export ERD'
---
![Image](https://github.com/user-attachments/assets/b481af2f-be10-457e-9f62-64e2d97ce019)

---
Step 8: Click on 'Export ERD'. In the current Lucidchart version, SQL codes for the ERD can only be generated for PostgreSQL, MySQL, Quickbase, Microsoft SQL Server and Oracle Database. For other relational type databases such as Teradata, Snowflakes etc, slight tweeks can be made to the generated SQL codes to create the tables in the desired database.
You can then copy the code for your target database, create the database, paste the code into the query run tab of your target database, and use the SQL code to create the tables.
---
![Image](https://github.com/user-attachments/assets/46c897e4-3c68-4500-a640-140271ca95e9)

---


> [!TIP]
> Here, we have shown the e-commerce use case SQL code generated by Lucidchart for PostgreSQL database.

> PostgreSQL Implementation

```ruby
'CREATE TABLE `customers` (
  `customer_id` INT ,
  `last_name` VARCHAR(255),
  `first_name` VARCHAR(255),
  `phone_nos` VARCHAR(20),
  `email` VARCHAR(255),
  `street` VARCHAR(255),
  `city` VARCHAR(255),
  `zip` VARCHAR(255),
  `is_active` BOOLEAN,
  PRIMARY KEY (`customer_id`)
);

CREATE TABLE `product` (
  `product_id` INT,
  `product_name` VARCHAR(255),
  `price` DECIMAL,
  PRIMARY KEY (`product_id`)
);

CREATE TABLE `orders` (
  `id` INT,
  `customer_id` INT,
  `date` DATE,
  PRIMARY KEY (`id`),
  FOREIGN KEY (`customer_id`) REFERENCES `customers`(`customer_id`)
);

CREATE TABLE `order_details` (
  `id` INT,
  `order_id` INT,
  `product_id` INT,
  `quantity` INT,
  `price` DECIMAL(12, 2),
  `to_street` VARCHAR(255),
  `to_city` VARCHAR(255),
  `to_zip` VARCHAR(255),
  `ship_date` varchar,
  PRIMARY KEY (`id`),
  FOREIGN KEY (`product_id`) REFERENCES `product`(`product_id`),
  FOREIGN KEY (`order_id`) REFERENCES `orders`(`id`)
);

```
Step 9: Using pgAdmin (for PostgreSQL database), create a database and name it
---

![Image](https://github.com/user-attachments/assets/094279d8-8526-4113-9acd-05fac5fd5f3d)

---
Step 10: Navigate to schemas, right click on Tables, and select Query Tools
---
![Image](https://github.com/user-attachments/assets/47a2f1d1-bd56-46a2-a9f4-c4157dd61778)

---
Step 11: Paste the SQL code generated by LucidChart ERD on the pgAdmin Query Tools to generate the tables for the named database
---
![Image](https://github.com/user-attachments/assets/3d642112-1b7a-482f-bea5-9d2fe1d194f3)
---

Step 12: You may insert some data into your database
---
![Image](https://github.com/user-attachments/assets/9f014a22-230f-4f5f-a79a-6b579669b311)
---
Step 13: Query the database for its content
---
![Image](https://github.com/user-attachments/assets/50fec327-0343-4510-983e-de91b47fbd5b)
---


### **AUTHOR'S BACKGROUND**

```

Author's Name:  Emmanuel Oyekanlu
Skillset:   I have experience spanning several years in developing scalable enterprise data pipelines, architecting enterprise data solutions,
data engineering, high performance computing (GPU, CUDA), machine learning, NLP and LLM applications as well as deploying scalable solutions (apps) on-prem and in the cloud.
I can be reached through: manuelbomi@yahoo.com
Website:  http://emmanueloyekanlu.com/
Publications:  https://scholar.google.com/citations?user=S-jTMfkAAAAJ&hl=en
LinkedIn:  https://www.linkedin.com/in/emmanuel-oyekanlu-6ba98616
Github:  https://github.com/manuelbomi

```
[![Icons](https://skillicons.dev/icons?i=aws,azure,gcp,scala,mongodb,redis,cassandra,kafka,anaconda,matlab,nodejs,django,py,c,anaconda,git,github,mysql,docker,kubernetes&theme=dark)](https://skillicons.dev)



