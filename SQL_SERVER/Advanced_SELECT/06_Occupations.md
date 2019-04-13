## Problem

Pivot the Occupation column in **OCCUPATIONS** so that each Name is sorted alphabetically and displayed underneath its corresponding Occupation. The output column headers should be Doctor, Professor, Singer, and Actor, respectively.

**Note**: Print **NULL** when there are no more names corresponding to an occupation.

**Input Format**

The **OCCUPATIONS** table is described as follows:

![](https://s3.amazonaws.com/hr-challenge-images/12889/1443816414-2a465532e7-1.png)

Occupation will only contain one of the following values: **Doctor**, **Professor**, **Singer** or **Actor**.

**Sample Input**

![](https://s3.amazonaws.com/hr-challenge-images/12890/1443817648-1b2b8add45-2.png)

**Sample Output**

    Jenny    Ashley     Meera  Jane
    Samantha Christeen  Priya  Julia
    NULL     Ketty      NULL   Maria
    
**Explanation**

The first column is an alphabetically ordered list of Doctor names. 

The second column is an alphabetically ordered list of Professor names. 

The third column is an alphabetically ordered list of Singer names. 

The fourth column is an alphabetically ordered list of Actor names. 

The empty cell data for columns with less than the maximum number of names per occupation (in this case, the Professor and Actor columns) are filled with **NULL** values.
    
## CODE:
- Cách 1:

        SELECT
        [Doctor], [Professor], [Singer], [Actor]
        FROM
        (
          SELECT ROW_NUMBER() OVER (PARTITION BY OCCUPATION ORDER BY NAME) [RowNumber], * FROM OCCUPATIONS
        ) 
        AS tempTable
        PIVOT(MAX(NAME) FOR OCCUPATION IN ([Doctor], [Professor], [Singer], [Actor])) AS pivotTable;

- Cách 2:

        select min(Doctor), min(Professor),min(Singer),  min(Actor)
        from(
        select ROW_NUMBER() OVER(PARTITION By Doctor,Actor,Singer,Professor order by name asc) AS Rownum, 
        case when Doctor=1 then name else Null end as Doctor,
        case when Actor=1 then name else Null end as Actor,
        case when Singer=1 then name else Null end as Singer,
        case when Professor=1 then name else Null end as Professor
        from occupations
        pivot
        ( count(occupation)
        for occupation in(Doctor, Actor, Singer, Professor)) as p

        ) temp

        group by Rownum  ;
    
## Output:
Your Output (stdout)

    Aamina Ashley Christeen Eve 
    Julia Belvet Jane Jennifer 
    Priya Britney Jenny Ketty 
    NULL Maria Kristeen Samantha 
    NULL Meera NULL NULL 
    NULL Naomi NULL NULL 
    NULL Priyanka NULL NULL 

## DISCUSS:
### Yêu cầu của bài: 
- **Tư duy:** 
- **Phân tích:**
- **Kiến thức áp dụng:**
- **Lưu ý:**

