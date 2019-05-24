### **HOMEWORK 4** ###

**CALCULATE 30 DAYS DAILY RETENTION FOR THOSE WHO TRANSACT FOR THE FIRST TIME IN THE FIRST HALF OF 2017**

```
SELECT
    count(user_id) as total_users,
    datediff(day,first_transaction,transaction_timestamp)
FROM
    (select*,
    FIRST_VALUE(TRANSACTION_TIMESTAMP) over (PARTITION by user_id
    order by
    TRANSACTION_TIMESTAMP rows BETWEEN UNBOUNDED PRECEDING and UNBOUNDED FOLLOWING)as first_transaction
FROM
    tangarana.payment_transactions  
WHERE
    transaction_type = 'payment') 
WHERE 
    first_transaction >= '2017-01-01'
    AND first_transaction<'2017-07-01' 
GROUP BY 2
ORDER BY 2
limit 31;
```
![](https://github.com/Lidiamasso/SQL-Masterclass/blob/master/4.%20Window%20Functions/Window%20Functions.4.PNG?raw=true)




