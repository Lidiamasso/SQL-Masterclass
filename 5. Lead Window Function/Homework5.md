### **HOMEWORK 4** ###

**WE HAVE DATA FROM VISITS AND PURCHASES FROM AN ECOMMERCE WEBSITE. ASSIGN A VISIT TO EVERY TRANSACTION**

```
with my_visits as (
select
	visit_id,
	user_id,
	visit_time,
	nvl(lead(visit_time)over(partition by user_id
order by
	visit_time),
	'2009-01-01') as next_visit
from
	sql_masterclass.visits ) 
select
	v.user_id,
	t.transaction_id,
	v.visit_id,
	t.transaction_time,
	v.visit_time
from
	sql_masterclass.transactions t
left join my_visits v on
	t.user_id = v.user_id
	and t.transaction_time between v.visit_time and v.next_visit ;
```
![](https://github.com/Lidiamasso/SQL-Masterclass/blob/master/5.%20Lead%20Window%20Function/LEAD%20WINDOW%20FUNCTION.PNG?raw=true)




