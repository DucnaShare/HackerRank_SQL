## Problem

Query the Western Longitude (LONG_W) for the largest Northern Latitude (LAT_N) in **STATION** that is less than _137.2345_. Round your answer to _4_ decimal places.

**Input Format**

The **STATION** table is described as follows:

![](https://s3.amazonaws.com/hr-challenge-images/9336/1449345840-5f0a551030-Station.jpg)

where LAT_N is the northern latitude and LONG_W is the western longitude.

## CODE:
    
    SELECT CAST(LONG_W AS DECIMAL(10,4)) 
    FROM STATION 
    WHERE LAT_N = (SELECT MAX(LAT_N) 
    FROM STATION 
    WHERE LAT_N<137.2345);
    
## Output:
Your Output (stdout)

    117.2465  

## DISCUSS:
### Yêu cầu của bài: 
- **Tư duy:** 
- **Phân tích:**
- **Kiến thức áp dụng:**
- **Lưu ý:**



