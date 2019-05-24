### **HOMEWORK 4** ###

**CALCULATE 30 DAYS DAILY RETENTION FOR THOSE WHO TRANSACT FOR THE FIRST TIME IN THE FIRST HALF OF 2017**

```
SELECT
	*,
	round(100.0 * cnt / max(cnt)OVER(), 2)
FROM
	(
	SELECT
		datediff(DAY,
		is_first_payment,
		transaction_timestamp)date_diff,
		COUNT(distinct user_id) cnt
	FROM
		(
		SELECT
			*,
			first_value(TRANSACTION_TIMESTAMP) OVER (PARTITION BY user_id
		ORDER BY
			TRANSACTION_TIMESTAMP ROWS BETWEEN UNBOUNDED PRECEDING AND UNBOUNDED FOLLOWING) is_first_payment
		FROM
			(
			SELECT
				user_id,
				date(transaction_timestamp)transaction_timestamp
			FROM
				tangarana.payment_transactions
			WHERE
				transaction_type = 'payment' )t)t2
	WHERE
		is_first_payment >= '2017-01-01'
		AND is_first_payment <= '2017-06-30'
		AND date_diff <= 30
	GROUP BY
		1
	ORDER BY
		2 ASC);

```
![]()




