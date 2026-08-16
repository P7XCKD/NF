next practical, make your own database and save your work

> [!attention] Note
> ![image](.attachments/f7343552969685efb63d2bbb44b86fdac752d11a.png) 
>click on this button at start for above
> login password for mysql = toor
> ![image](.attachments/dbe4758670f79d1ee1d14c203a6acdc47e02fe1c.png) 
> click on that flash sign to multi run lines from selected portion


create , insert , select
```sql
USE dummy;
CREATE table student(
ROLLNO integer primary key,
S_NAME text,
AGE integer,
ADDRESS varchar(69),
PHONE DOUBLE);

insert into student VALUES (1,'morty',15,'earth',9283339);
insert into student VALUES (2,'percy',16,'earth',9285553);
insert into student VALUES (3,'andrew',17,'earth',null);
insert into student VALUES(4,'mike',18,null,null);
insert into student values(5,'john',19,'notearth',949433);
insert into student values(6,'chris',17,'notearth',null);
insert into student values(7,'nate',16,'mars',929222);

select * from student;

```