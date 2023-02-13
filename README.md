# SQL---Projects-Dump

-- Check for Null values in column 1
Select member_number from grocery_table
where grocery_table.member_number is null;

--- Alter table grocery_table
--- rename column date to purchase_date

-- Check for Null values in column 2
Select purchase_date from grocery_table
where grocery_table.purchase_date is null

-- Check for Null values in column 3
Select itemdescription from grocery_table
where grocery_table.itemdescription is null


-- Count distinct member numbers.
Select count(distinct member_number) from grocery_table

-- Count distinct items
Select count(distinct itemdescription) from grocery_table


Select min(purchase_date) from grocery_table                                                  
Select max(purchase_date) from grocery_table.member_number

Select 
itemdescription,
count(*) as ItemsSold
from grocery_table 
group by itemdescription
order by ItemsSold desc

Alter Table grocery_table
add purchase_year int

Alter Table grocery_table
add purchase_month int

Alter Table grocery_table
add purchase_day INT

Alter Table grocery_table
add purchase_dow INT 

update grocery_table 
set purchase_year = extract(year from purchase_date)

update grocery_table 
set purchase_month = extract(month from purchase_date)

update grocery_table 
set purchase_day = extract(DAY from purchase_date)

update grocery_table 
set purchase_dow = extract(DOW from purchase_date)

Select * from grocery_table

Select 
purchase_year,
itemdescription,
count(*) as Total
from grocery_table
group by 1,2
order by 3 desc

Select 
purchase_year as Year,
itemdescription,
count(itemdescription) as Total
from grocery_table
where purchase_year = 2014
group by 1,2
order by 3 desc

Select 
purchase_year as Year,
itemdescription,
count(itemdescription) as Total
from grocery_table
where purchase_year = 2015
group by 1,2
order by 3 desc


Select 
purchase_year as Year,
count(itemdescription) as Total
from grocery_table
group by 1
order by 2 desc


Select 
purchase_month as Month,
count(itemdescription) as Total
from grocery_table
group by 1
order by 2 desc

Select 
purchase_month as Month,
count(itemdescription) as Total
from grocery_table
where purchase_year =2014
group by 1
order by 2 desc

Select 
purchase_month as Month,
count(itemdescription) as Total
from grocery_table
where purchase_year =2015
group by 1
order by 2 desc

Alter Table grocery_table
add price DECIMAL

update grocery_table 
set price = random() from generate_series(1,38765)


With GrocerySales
as
(
Select 
member_number,
item_no,
purchase_date,
item_info.item_description,
item_info.price,
purchase_year,
purchase_month
price
from grocery_table
left join item_info
on grocery_table.itemdescription=item_info.item_description
order by 1,3
)

Select * from grocerySales
