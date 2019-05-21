### **HOMEWORK 2** ###

**CALCULATE DISTANCE IN KM BETWEEN MADRID AND BARCELONA**

```
Set @Lat1 = 40.4168;
Set @Lng1 = -3.7028;
Set @Lat2 = 41.3851;
Set @Lng2 = 2.1734;
 
SELECT 
    (acos(sin(radians(@Lat1)) * sin(radians(@Lat2)) + 
    cos(radians(@Lat1)) * cos(radians(@Lat2)) * 
    cos(radians(@Lng1) - radians(@Lng2))) * 6371) AS Distance_Km;
```

|Distance Madrid-Barcelona|
|-|
|505.3614042637432 km|



