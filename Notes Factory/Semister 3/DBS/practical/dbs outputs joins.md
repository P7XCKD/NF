

```sql
create table DEPT(
dept_no int,
 d_name text,
city text
);
create table CUSTOMER(
cust_no int,
cust_name text,
dept_no int
);
insert into DEPT values(1,"Production","Mumbai");
insert into DEPT values(2,"Marketing","Nasik");
insert into DEPT values(3,"Sales","Pune");
insert into DEPT values(4,"Design","Aurangabad");
insert into DEPT values(6,"Finance","Nagpur");
insert into DEPT values(7,"IT","Baramati");

insert into CUSTOMER values(101,"A",1);
insert into CUSTOMER values(102,"B",2);
insert into CUSTOMER values(103,"C",3);
insert into CUSTOMER values(104,"D",4);
insert into CUSTOMER values(105,"E",5);

select * from DEPT;

select * from CUSTOMER;

drop table DEPT;
drop table CUSTOMER;

select cust_no,cust_name,CUSTOMER.dept_no,d_name from CUSTOMER INNER JOIN DEPT on CUSTOMER.dept_no = DEPT.dept_no;

select CUSTOMER.cust_no,cust_name,DEPT.d_name from CUSTOMER left join dept on CUSTOMER.dept_no = DEPT.dept_no;

select CUSTOMER.cust_no,cust_name,DEPT.dept_no,DEPT.d_name from CUSTOMER right join dept on CUSTOMER.dept_no = DEPT.dept_no;

select CUSTOMER.cust_no,cust_name,DEPT.d_name from CUSTOMER full outer join dept on CUSTOMER.dept_no = DEPT.dept_no;


```

***
output
![image](.attachments/4bff15643ff60f5d192ae512c76793e6b8b56fd2.png) 

![image](.attachments/bc619de3daf4b29dc1bd4717fc6758b19d60d8e6.png) 

![image](.attachments/25e4be2bc623fcfb16357b3954243c090314c419.png) 

### self join
```sql
create table Employee(
emp_no int,
emp_name text,
salary int,
commodity int
);

insert into Employee values(105,"Ram",15000,20000);
insert into Employee values(106,"Neha",20000,10000);
insert into Employee values(107,"Nitin",25000,23000);
insert into Employee values(108,"Dev",30000,10928);

select * from Employee;

select a.emp_no,a.emp_name, a.salary from Employee a, Employee b 
where a.commodity + 15000 > b.salary and a.emp_no = b.emp_no;
```
***
output
![image](.attachments/ca9c51f523b3e82046b7e5bd49271fa780d5b6c0.png) 
