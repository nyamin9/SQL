# 🐬 집계함수  



<br>  

데이터의 크기가 커지면, SELECT 문을 통해 모든 데이터를 가져오기보다는 집계함수를 통해 요약통계량을 가져오는 경우가 많습니다.  

SQL에서 요약통계량을 구하기 위해 사용하는 함수들을 집계함수라고 합니다.  


<br>  

***  

<br>  

## COUNT  


<br>  

Products 테이블에 있는 행의 수, 즉 데이터 레코드의 수를 세줍니다.  

<br>  


```sql
SELECT COUNT(*) FROM Products;
```  
```
>> 77
```  


<br> 

##  

<br>  


또한, COUNT( ) 구문 안에 * 가 아닌 열의 이름을 넣어주면, 해당 열에 있는 레코드의 수를 세줍니다.  

만약 해당 열에 NULL 값이 있다면 NULL이 있는 레코드의 수는 제외하고 개수를 반환합니다.  

예를 들어서, DATA 라는 테이블에 `NUMBER` 라는 열에 [1, 2, 3, 4, NULL] 이라는 데이터가 들어가 있을 때에는 다음과 같은 결과가 나올 것입니다.  

<br>  

```sql
SELECT COUNT(NUMBER) FROM DATA;
```  
```
>> 4
```  
   
<br>  

##  

<br>  

COUNT 함수는 DISTINCT 함수와도 자주 사용합니다.  

DISTINCT 함수는 유니크한 값만을 가져오는 함수인데요, 이를 COUNT 함수 안에 넣어주면 유니크한 데이터의 수만을 카운트합니다.  

예를 들어서, DATA 라는 테이블의 `ID` 라는 열에 [1, 1, 2, 3, 3] 이라는 데이터가 들어가 있을 때에는 다음과 같은 결과가 나올 것입니다.  

<br>  

```sql
SELECT COUNT(DISTINCT ID) FROM DATA;
```  
```
>> 3
```  

<br>  

***  

<br>    

## SUM  

<br>  

SUM() 함수는 단순 합연산에 사용하는 함수입니다.  

예를 들어, Products 테이블에서 모든 제품들의 가격의 합을 알고 싶다면 다음의 쿼리를 작성하면 됩니다.  

<br>  

```sql
SELECT SUM(Price)
FROM Products;  
```  
```
>>

SUM(Price)
2222.71
```  

<br>  

***  

<br>  

## AVG  

<br>  

AVG() 함수는 평균 연산에 사용하는 함수입니다.  

예를 들어, Products 테이블에서 모든 제품들의 가격의 평균을 알고 싶다면 다음의 쿼리를 작성하면 됩니다.  

<br>  

```sql
SELECT AVG(Price)
FROM Products;  
```  
```
>>

AVG(Price)
28.866363636363637
```  

<br>  

##  

<br>  

하지만 평균을 구할 때 주의해야 할 점이 있습니다. 바로 NULL 값의 유무입니다.  

만약 NULL 값이 있는 데이터에 대해서 AVG() 함수를 적용하게 되면, 해당 NULL 값은 그냥 없는 데이터로 간주합니다.  

예를 들어서, DATA 라는 테이블에 `NUMBER` 라는 열에 [1, 2, 3, 4, NULL] 이라는 데이터가 들어가 있을 때에는 다음과 같은 결과가 나올 것입니다.  

<br>  

```sql
SELECT AVG(NUMBER) FROM DATA;
```  
```
>> 2.5
```  

<br>  

##  

<br>  

반면에, NULL 값을 0으로 간주하고 계산해야 하는 경우에는 AVG 함수를 사용하면 안됩니다.  

그 대신 총합을 전체 레코드의 수로 나눠서 NULL 데이터를 0으로 처리해줍니다.  

예를 들어서, DATA 라는 테이블에 `NUMBER` 라는 열에 [1, 2, 3, 4, NULL] 이라는 데이터가 들어가 있을 때에는 다음과 같은 결과가 나올 것입니다.  

<br>  

```sql
SELECT SUM(NUMBER) / COUNT(*) FROM DATA;
```  
```
>> 2.0
```  

<br>  

***  

<br> 

## MIN / MAX  

<br>  

최소값을 구할 때는 MIN 함수를, 최대값을 구할 때는 MAX 함수를 사용하면 됩니다.  

<br>  

```sql
SELECT MIN(Price) FROM Products;
```  
```
>>

MIN(Price)
2.5
```

<br>  

##  

<br>   

```sql
SELECT MAX(Price) FROM Products;
```  
```
>>

MAX(Price)
263.5
```  

<br>  


  

***  
