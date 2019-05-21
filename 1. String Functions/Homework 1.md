### **HOMEWORK 1** ###

**GET FIRST NAME, LAST NAME, AND INITIALS (FIRST LETTER OF THE FIRST NAME AND FIRSTLETTER OF LAST NAME) FROM 10  USERS**
:::mysql 
```
SELECT
	firstname,
	lastname,
	left(firstname, 1)|| left(lastname, 1) AS initials
FROM
    sql_masterclass.users
LIMIT 10;
```

![](https://raw.githubusercontent.com/Lidiamasso/SQL-Masterclass/master/1.%20String%20Functions/StringFunctions.PNG)



