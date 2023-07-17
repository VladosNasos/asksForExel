# asksForExel[xyexel.txt](https://github.com/VladosNasos/asksForExel/files/12071908/xyexel.txt)
--Task 1 хлеба да молока нет, будет пиво и ламинария
SELECT name,price, rating [ammount],discount,(price*rating)*(100-discount)/100[навар]FROM dbo.Table_1
WHERE name like '%шуменско%' or name like '%Ламинария%'
--Task 4 тут нужно кондитерские изделия, не рошен. Я решил сделать НЕ ПИВО,но производитель не лейс
SELECT name FROM Table_1
WHERE is_beer = 0 and manufacturer!='Lays'

--task 5
Select *
FROM Table_1
WHERE name LIKE 'K%' and type like 'т%'
--таск 6
SELECT name 
FROM Table_1 
WHERE name BETWEEN 'в' AND 'л' AND (name LIKE 'в%' OR name LIKE 'л%');
--task 7 так как нет даты поставки, поставлю дату придатности до сегодня до вчерашнего дня
SELECT name,expire_date
FROM Table_1 
WHERE expire_date < DATEADD(day, -1, GETDATE());
--task 8 количества у меня нет, за то есть рейтинг. Сделаю где альколь = 0 и рейтинг >80
SELECT name,alcohol,rating
FROM Table_1 
where alcohol=0 and rating>80
--task 9
SELECT *
FROM Table_1 
WHERE price<200 and price>100
order by price 
--task 10 
UPDATE Table_1 SET price =price * 0.95
SELECT *
FROM Table_1 

--таск 11
UPDATE Table_1
set expire_date =DATEADD(day, 1, GETDATE())
where expire_date=NULL

--12 Удалю где рейтинг менее 70 и цена более 70 грн
--DELETE FROM Table_1
--where rating<70 and price>70

--13 удалю все алкоголь>0 и is_beer(типо кондитерки). Закоменчу, ибо рука дрогнет
--DELETE FROM Table_1
--where alcohol>0 or is_beer =1

--14 task
--DELETE FROM Table_1
--where LEN(name)=5

--15 task
--DELETE FROM Table_1
--WHERE expire_date> DATEADD(MONTH, 3, GETDATE()) 

--16 TASK

SELECT top 5 price, name
FROM Table_1 
order by price desc

--17 task
--DELETE FROM Table_1
--where manufacturer=NULL OR discount>10
