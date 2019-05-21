### **HOMEWORK 3** ###

**GET TOTAL NUMBER OF UNSOLD TICKETS PER VENUE IN OHIO STATE**

```
SELECT
	venueid,
	sum(l.numtickets) as TOTAL_TICKETS,
	sum(s.qtysold) as TOTAL_SOLD,
	sum(l.numtickets) - sum(s.qtysold) AS UNSOLD_tickets
FROM
	sql_masterclass.event e
INNER JOIN sql_masterclass.listing l on
	e.eventid = l.eventid
INNER JOIN sql_masterclass.sales s ON
	l.eventid = s.eventid
GROUP BY
	1
HAVING
	venueid IN (
	select DISTINCT (venueid)
	from
		sql_masterclass.venue
	where
		venuestate = 'OH')
ORDER BY venueid;
```
![](https://github.com/Lidiamasso/SQL-Masterclass/blob/master/3.%20Subqueries/Subqueries.3.PNG?raw=true)




