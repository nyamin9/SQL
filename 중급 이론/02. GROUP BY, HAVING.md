# 🐬 GROUP BY, HAVING  



<br>  

보통 데이터를 요약하거나, 어떤 통계량으로 나타낼 때 테이블 전체에 대한 집계를 하지는 않습니다.  

오히려, 어떠한 열의 범주를 기준으로 이에 해당하는 행에 대해 요약하는 경우가 더욱 많습니다.  

이때 사용하는 구문이 바로 GROUP BY 구문과 HAVING 구문입니다.  


<br>  

***  

<br>  

## GROUP BY  



<br>  

Products 테이블의 SupplierID 열을 기준으로 그룹화한 후, 각 그룹의 Price에 대해 평균을 계산하는 쿼리입니다.  

GROUP BY 절을 사용할 때 유의할 점은, 해당 절을 통해 그룹화한 열이 반드시 SELECT 절 안에 포함되어 있어야 한다는 점입니다!!  

<br>  


```sql
SELECT SupplierID, AVG(Price)
FROM Products
GROUP BY SupplierID;
```  

<br>  

![image](https://github.com/nyamin9/SQL/assets/65170165/37bbefc4-c843-4649-a326-a8a95f4db31f)  


<br>  

##  

<br>  


또한 `,`를 사용해서 GROUP BY 절의 기준에 두 가지 열을 사용할 수도 있습니다.  

<br>  

```sql
SELECT SupplierID, CategoryID, AVG(Price) 
FROM Products
GROUP BY SupplierID, CategoryID;  
```  

<br>  

![image](https://github.com/nyamin9/SQL/assets/65170165/689043fc-91e0-4ce7-9658-9e704adb8abf)  

<br>  

##  

<br>  


ORDER BY 절을 사용해서 결과를 오름차순/내림차순으로 정렬하는 것도 데이터 파악에 큰 도움이 됩니다!!  

ORDER BY 절의 위치는 GROUP BY 절의 아래쪽입니다.  


<br>  

```sql
--내림차순정렬

SELECT SupplierID, CategoryID, AVG(Price) 
FROM Products
GROUP BY SupplierID, CategoryID
ORDER BY AVG(Price) DESC;   
```  

<br>  

![image](https://github.com/nyamin9/SQL/assets/65170165/c86f9d17-53c1-4a7b-9617-40a894df9d8c)  


<br>  

***  


<br>  

## HAVING  


<br>  

쿼리에 WHERE 절을 사용해서 조건을 만족하는 데이터만 추출할 수 있습니다.  

이때 GROUP BY 절을 사용한다고 가정하며, 쿼리 작성 순서는 `SELECT -> FROM -> WHERE -> GROUP BY` 입니다.  

하지만 GROUP BY 절을 사용하는 경우 WHERE 절과 함께 사용하면 쿼리 실행 순서에 따라 원하는 결과가 나오지 않을 가능성이 큽니다.  

그 대신, GROUP BY 절을 사용할 때에는 HAVING 절을 뒤에 작성해 조건문을 만들어 줍니다.  


<br>  

```sql
SELECT SupplierID, CategoryID, AVG(Price)
FROM Products
GROUP BY SupplierID, CategoryID
HAVING AVG(Price) >= 100  


/*
SELECT SupplierID, CategoryID, AVG(Price) AS avg_price
FROM Products
GROUP BY SupplierID, CategoryID
HAVING avg_price >= 100  
*/
```  

<br>  

![image](https://github.com/nyamin9/SQL/assets/65170165/97c2880e-2313-463a-823c-d543e30a3c23)  



<br>  

***  
