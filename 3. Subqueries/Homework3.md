### **HOMEWORK 3** ###

**GET TOTAL NUMBER OF UNSOLD TICKETS PER VENUE IN OHIO STATE**

```
SELECT
	v.venuename,
	sum(l.numtickets) - sum(s.qtysold) AS UNSOLD_tickets
FROM
	sql_masterclass.venue v
INNER JOIN sql_masterclass.event e on
	v.venueid = e.venueid
INNER JOIN (
		select eventid,
		sum(numtickets) as numtickets
	from
		sql_masterclass.listing
	group by
		1) l on
	l.eventid = e.eventid
left join (
		select eventid,
		sum(qtysold) as qtysold
	from
		sql_masterclass.sales
	group by
		1) s on
	s.eventid = e.eventid
where
	v.venuestate = 'OH'
group by 1;
```
![]()




