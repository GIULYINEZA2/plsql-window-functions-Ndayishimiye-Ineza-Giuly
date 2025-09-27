Student: Ndayishimiye Ineza Giuly


Course: Database Development with PL/SQL (INSY 8311)


Instructor: Eric Maniraguha


Date: September 2025

 Individual assignment 

 Step 1: Problem Definition 

 
Business Context


Company: Smart Reads Rwanda Ltd

Department: E-commerce Analytics & Customer Intelligence

Industry: Online Book Retail & Educational Resources

Data challenge


Smart Reads Rwanda Ltd bookstore aims to improve its inline sales across various book categories( Academic, Fiction, Non-Fiction and Children’s books) by identifying the best-selling books each quarter, studying customer reading habits and purchase frequency and using data to segment customers for personalized book suggestions. Currently, the company has limited insight into seasonal reading trends, customer value distribution, and monthly sales growth, which makes it difficult to plan inventory and run effective marketing campaigns. 



Expected outcome



Develop a complete analytical system that gives useful insights to help category managers manage book inventory efficiently, enable marketing teams to create targeted campaigns for different customer groups, assist content curators in spotting trending topics, and support executives in making strategic decisions based on sales patterns and customer reading behavior.

Step 2: Success Criteria (Measurable Goals)




1.	Top 5 Books per Category/Quarter → RANK(), DENSE_RANK()


	Determine the best-selling books in each category based on sales and revenue.
Help category managers optimize inventory and focus on promotions.
2.	Running Monthly Sales Totals → SUM() OVER()


	Track cumulative sales month by month.
Give real-time insights on progress toward yearly sales targets.
3.	Month-over-Month Growth → LAG(), LEAD()


	Calculate monthly growth percentages and identify seasonal reading trends.
	Assist in proactive inventory planning and predicting trends.

4.Customer Value Quartiles → NTILE(4)

   
	Divide customers into four groups: Bibliophile, Premium Reader, Regular Reader, and Casual Reader.
	Enable targeted recommendations and loyalty programs.


5.3-Month Moving Averages → AVG() OVER()



	Smooth out seasonal variations for clearer trend analysis.
	Improve accuracy in inventory forecasting.

Step 3: Database Schema 



Table Design
Table	Purpose	Key Columns	Example Row



customers	 Customer information and reading preferences	customer_id (PK), name, region	1, Giuly Ineza, Kigali
products	Catalog of books 	poduct_id (PK), name,  category	1,Learn SQL in24 hours, Education
Sales_transactions 	sales records	transaction_id (PK), customer_id (FK), product-id(FK),sale_date,amount	1,1,1, 2024-01-15, 25000


ER Diagram 


Step 4: Window Functions Implementation

1.Ranking: ROW_NUMBER(), RANK(), DENSE_RANK(), PERCENT_RANK() 

Interpretation:



This query ranks customers by total revenue from book sales. ROW_NUMBER assigns a unique order, RANK allows ties, DENSE_RANK avoids gaps, and PERCENT_RANK shows each customer’s relative position. We can easily spot the top N customers and see their contribution compared to others.


2.Aggregate: SUM(), AVG(), MIN(), MAX() 

Interpretation:


This query calculates running totals of revenue over time, a moving average of the last 3 sales, and running min/max values. It helps detect sales growth trends, seasonal peaks, and whether transaction values are increasing or stabilizing over time.


3. Navigation: LAG(), LEAD()


Interpretation:


This query compares each sale with the previous and next transactions. The LAG function retrieves past sales, LEAD looks ahead, and we calculate a growth percentage. This shows whether sales are growing, declining, or fluctuating period-to-period.


 4. Distribution: NTILE(4), CUME_DIST()

 Interpretation:

 
This query segments customers into quartiles based on revenue. The top quartile (1) holds the most valuable customers, while quartile 4 represents the least. CUME_DIST shows the cumulative share of customers up to a certain revenue level. This is key for customer segmentation and designing targeted marketing strategies.

Step 6: Results Analysis



1. Descriptive – What happened?


   
The analysis shows that Kigali customers generated the highest revenue, followed by West region buyers, while North and South contributed the least. The ROW_NUMBER and RANK queries revealed a few top customers responsible for a large share of sales. Running totals showed a steady revenue increase from January to March. LAG/LEAD indicated some fluctuations, with February sales dipping compared to January. Customer segmentation with NTILE grouped buyers into quartiles, highlighting a small cluster of high spenders.


3. Diagnostic – Why?


Kigali leads because it has more active online customers and faster delivery access. West performed well due to bulk textbook purchases. Lower performance in North and South may be due to fewer online shoppers or limited awareness of the platform. Period-to-period analysis showed growth spikes driven by larger individual transactions (e.g., bulk orders by institutions). Segmentation confirmed that top 25% of customers drive most revenue, while the bottom tiers make smaller, occasional purchases.


4. Prescriptive – What next?



Smart Reads Rwanda Ltd should nurture Kigali and West customers with loyalty programs, discounts, and premium delivery services to keep them engaged. For North and South, targeted marketing (e.g., free delivery promotions, student discounts) could increase adoption. Customer segmentation suggests rewarding the top quartile with exclusive offers while encouraging lower-tier customers with affordable bundles. Tracking growth % (LAG/LEAD) monthly will help the business spot slowdowns early and adapt strategies quickly.




Step 7: References


1.	Savan, S. (2020, June 24). Rank functions in SQL: RANK, DENSE_RANK, ROW_NUMBER, NTILE(n). Medium. https://medium.com/@serasiyasavan14/rank-functions-in-sql-rank-dense-rank-row-number-n-6b0d9f8521dc
2.	GeeksforGeeks. (n.d.). SQL window functions in SQL. https://www.geeksforgeeks.org/sql/window-functions-in-sql
3.	SQLShack. (2020, June 11). Overview of SQL rank functions. https://www.sqlshack.com/overview-of-sql-rank-functions
4.	Krthiak. (2023, January 15). 30 SQL window function questions for interviews (Day 47 of 100 days of data engineering, AI, and SQL). Medium. https://medium.com/@krthiak/30-sql-window-functionion-questions-for-interviews-day-47-of-100-days-of-data-engineering-ai-and-638bef1af0f6
5.	Mew, D. [YouTube channel]. (2019, September 10). SQL window functions tutorial. YouTube. https://www.youtube.com/watch?v=Ww71knvhQ-s
6.	Data Engineer [YouTube channel]. (2020, November 12). Understanding window functions in SQL. YouTube. https://www.youtube.com/watch?v=rIcB4zMYMas
7.	SQL Academy [YouTube channel]. (2021, February 5). SQL window functions playlist. YouTube. https://www.youtube.com/watch?v=BsI_jp7CXXk&list=PLtgiThe4j67olcB82Fc3TT9q4cwWC3Is
8.	Mode. (n.d.). SQL window functions tutorial. https://mode.com/sql-tutorial/sql-window-functions
9.	DataCamp. (n.d.). SQL window functions cheat sheet. https://www.datacamp.com/cheat-sheet/sql-window-functions-cheat-sheet
10.	Datalemur. (n.d.). SQL aggregate window functions tutorial. https://datalemur.com/sql-tutorial/sql-aggregate-window-functions
11.	FreeCodeCamp. (2020, April 8). Window functions in SQL. https://www.freecodecamp.org/news/window-functions-in-sql
12.	PostgreSQL Global Development Group. (n.d.). PostgreSQL tutorial: Window functions. https://www.postgresql.org/docs/current/tutorial-window.html
13.	Alex [YouTube channel]. (2020, March 3). SQL window functions explained. YouTube. https://www.youtube.com/watch?v=cXhv4kmIzFw
14.	Code with Chris [YouTube channel]. (2020, May 15). SQL window functions for beginners. YouTube. https://www.youtube.com/watch?v=xMWEVFC4FOk
15.	SQL Academy. (n.d.). Types of window functions. https://sql-academy.org/en/guide/types-of-windows-functions



All sources were properly cited. Implementations and analysis represent original work. No AI generated content was copied without attribution or adaptation

   





