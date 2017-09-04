#### 데이터 관리



- 생성

  - ```sql
    CREATE DATABASE `데이터베이스명` CHARACTER SET utf8 COLLATE utf8_general_ci;
    ```

- 삭제

  - ```mysql
    DROP DATABASE `데이터베이스명`
    ```

- 열람

  - ```mysql
    SHOW DATABASES
    ```

- 선택

  - ```mysql
    USE `데이터베이스명`
    ```

- [php admin 사이트](https://demo.phpmyadmin.net/master-config/db_structure.php?server=2&db=class)



> database가 directory 라면
>
> table은 file



###### 스키마

> 테이블에 적재될 데이터의 구조와 형식을 정의하는 것
>
> e.g. 설계도?
>
> 컬럼을 지정하거나, 컬럼에 어떤 형식의 데이터가 올지 



Table

`show tables`

`creat table`

`insert into`

`select * from`