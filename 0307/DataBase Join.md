# Join
두 개 이상의 테이블을 서로 연결하여 데이터를 검색할 때 사용하는 방법입니다.
두 개의 테이블을 하나의 테이블인 것처럼 보여주는 효과를 얻을 수 있습니다.

# Join의 종류
>
1. Inner Join
2. Outer Join
3. Cross Join
4. Self Join


## Inner Join
![](https://velog.velcdn.com/images/zzckckck3/post/5823a8e6-1ede-433e-ae21-d5194dc693d0/image.png)
두 테이블의 교집합을 만족하는 행을 반환하는 방식입니다.

명시적 조인 표현
>
SELECT *
FROM EMPLOYEE 
INNER JOIN DEPARTMENT
ON EMPLOYEE.DepartmentID = DEPARTMENT.DepartmentID;

암시적 조인 표현
>
SELECT *
FROM EMPLOYEE, DEPARTMENT
WHERE EMPLOYEE.DepartmentID = DEPARTMENT.DepartmentID;


## Outer Join - Left Outer Join
![](https://velog.velcdn.com/images/zzckckck3/post/cac7b88d-c596-4d16-89ec-77ac50372524/image.png)
조인문의 왼쪽에 있는 테이블의 모든 결과를 가져온 후, 오른쪽 테이블의 데이터를 매칭하고, 매칭하는 데이터가 없는 경우 NULL을 반환하는 방식입니다.
>
SELECT *
FROM EMPLOYEE E LEFT OUTER JOIN DEPARTMENT D 
ON E.DEPARTMENTID = D.DEPARTMENTID;

## Outer Join - Right Outer Join
![](https://velog.velcdn.com/images/zzckckck3/post/2fc7a245-e586-4183-a61c-2dee97dfcaa7/image.png)
조인문의 오른쪽 있는 테이블의 모든 결과를 가져온 후, 왼쪽 테이블의 데이터를 매칭하고, 매칭하는 데이터가 없는 경우 NULL을 반환하는 방식입니다. Left의 반대 버전입니다.

## Outer Join - Full Outer Join
![](https://velog.velcdn.com/images/zzckckck3/post/42e110e7-2bbb-4c71-b896-5ff1e504437e/image.png)
LEFT OUTER JOIN과 RIGHT OUTER JOIN을 합친 것으로, 양쪽 모두 조건이 일치하지 않는 것들까지 모두 결합하여 출력합니다. 이것 역시 매칭되는 데이터가 없는 경우 NULL을 표시합니다.

## Cross Join
## Self Join
