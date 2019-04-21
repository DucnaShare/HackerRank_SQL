## Problem

A  [median](https://en.wikipedia.org/wiki/Median) is defined as a number separating the higher half of a data set from the lower half. Query the median of the Northern Latitudes (LAT_N) from **STATION** and round your answer to _4_ decimal places.

**Input Format**

The **STATION** table is described as follows:

![](https://s3.amazonaws.com/hr-challenge-images/9336/1449345840-5f0a551030-Station.jpg)

where LAT_N is the northern latitude and LONG_W is the western longitude.

## CODE:

    SELECT CAST(LAT_N AS DECIMAL(10,4) )
    FROM (SELECT LAT_N, ROW_NUMBER() OVER (ORDER BY LAT_N DESC ) AS RN FROM STATION) A
    WHERE RN = ( SELECT CEILING(count(lat_n)/2.0) FROM STATION);
    
## Output:
Your Output (stdout)

    83.8913  

## DISCUSS:
### Yêu cầu của bài: 
- **Tư duy:** 
- **Phân tích:**
- **Kiến thức áp dụng:**
- **Lưu ý:**


