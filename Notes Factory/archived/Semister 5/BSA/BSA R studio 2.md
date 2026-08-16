```R
> num1<-c(1,2,3,4,5)
> print(num)
[1]  TRUE FALSE  TRUE FALSE  TRUE
> print(num[c(1,3)])
[1] TRUE TRUE
> typeof(num)
[1] "logical"
> 
> language<-c("C"=10,"C++"=20,"Java"=30,"Python"=40,"C#"=50)
> print(language)
     C    C++   Java Python     C# 
    10     20     30     40     50 
> print(language[1:3])
   C  C++ Java 
  10   20   30 
> typeof(num)
[1] "logical"
> 
> n<-c(10L,20L,30L)
> print(n)
[1] 10 20 30
> print(n[2])
[1] 20
> typeof(n)
[1] "integer"
> 
> seq1<-1:10
> print(seq1)
 [1]  1  2  3  4  5  6  7  8  9 10
> print(seq1[-2])
[1]  1  3  4  5  6  7  8  9 10
> seq1<-NULL
> print(seq1)
NULL
> 
> #arithmetic operation 
> print(sum(num))
[1] 3
> print(mean(num))
[1] 0.6
> print(prod(num))
[1] 0
> print(min(num))
[1] 0
> print(max(num))
[1] 1
> print(length(num))
[1] 5
> 
> num2<-c(6,7,8,9,10)
> print(num1+num2)
[1]  7  9 11 13 15
> print(num1-num2)
[1] -5 -5 -5 -5 -5
> print(num1*num2)
[1]  6 14 24 36 50
> print(num1/num2)
[1] 0.1666667 0.2857143 0.3750000 0.4444444 0.5000000
> 
> names(n)<-c("int1","int2","int3")
> print(n["int3"])
int3 
  30 
> 
> #accessing by key
> language["C"]
 C 
10 
> 
> #printing TRUE elements 
> num1[c(TRUE,FALSE,TRUE,FALSE,TRUE)]
[1] 1 3 5
> print(num1)
[1] 1 2 3 4 5
> 
> #repeat function
> rep(num2,time=2) 
 [1]  6  7  8  9 10  6  7  8  9 10
> rep(num2,each=5)
 [1]  6  6  6  6  6  7  7  7  7  7  8  8  8  8  8  9  9  9  9  9 10 10 10 10 10
> rep(c(10,20),time=c(3,4))
[1] 10 10 10 20 20 20 20
> rep(1:4,length.out=10)
 [1] 1 2 3 4 1 2 3 4 1 2
> seq(from=1,to=5,by=.5)
[1] 1.0 1.5 2.0 2.5 3.0 3.5 4.0 4.5 5.0
> 
> 
> #any function 
> any(num2>8)
[1] TRUE
> #all function
> all(num2>8)
[1] FALSE
> num1<-c(1,2,3,4,5)
> print(num)
[1]  TRUE FALSE  TRUE FALSE  TRUE
> print(num[c(1,3)])
[1] TRUE TRUE
> typeof(num)
[1] "logical"
> 
> language<-c("C"=10,"C++"=20,"Java"=30,"Python"=40,"C#"=50)
> print(language)
     C    C++   Java Python     C# 
    10     20     30     40     50 
> print(language[1:3])
   C  C++ Java 
  10   20   30 
> typeof(num)
[1] "logical"
> 
> n<-c(10L,20L,30L)
> print(n)
[1] 10 20 30
> print(n[2])
[1] 20
> typeof(n)
[1] "integer"
> 
> seq1<-1:10
> print(seq1)
 [1]  1  2  3  4  5  6  7  8  9 10
> print(seq1[-2])
[1]  1  3  4  5  6  7  8  9 10
> seq1<-NULL
> print(seq1)
NULL
> 
> #arithmetic operation 
> print(sum(num))
[1] 3
> print(mean(num))
[1] 0.6
> print(prod(num))
[1] 0
> print(min(num))
[1] 0
> print(max(num))
[1] 1
> print(length(num))
[1] 5
> 
> num2<-c(6,7,8,9,10)
> print(num1+num2)
[1]  7  9 11 13 15
> print(num1-num2)
[1] -5 -5 -5 -5 -5
> print(num1*num2)
[1]  6 14 24 36 50
> print(num1/num2)
[1] 0.1666667 0.2857143 0.3750000 0.4444444 0.5000000
> 
> names(n)<-c("int1","int2","int3")
> print(n["int3"])
int3 
  30 
> 
> #accessing by key
> language["C"]
 C 
10 
> 
> #printing TRUE elements 
> num1[c(TRUE,FALSE,TRUE,FALSE,TRUE)]
[1] 1 3 5
> print(num1)
[1] 1 2 3 4 5
> 
> #repeat function
> rep(num2,time=2) 
 [1]  6  7  8  9 10  6  7  8  9 10
> rep(num2,each=5)
 [1]  6  6  6  6  6  7  7  7  7  7  8  8  8  8  8  9  9  9  9  9 10 10 10 10 10
> rep(c(10,20),time=c(3,4))
[1] 10 10 10 20 20 20 20
> rep(1:4,length.out=10)
 [1] 1 2 3 4 1 2 3 4 1 2
> seq(from=1,to=5,by=.5)
[1] 1.0 1.5 2.0 2.5 3.0 3.5 4.0 4.5 5.0
> 
> 
> #any function 
> any(num2>8)
[1] TRUE
> #all function
> all(num2>8)
[1] FALSE
```
***
```R
list1 <- list(c("A021", "A022", "A025"), c("Aryan", "Heramb", "Dev"))
print(list1)

list2<-list("C","C++",10,-5,TRUE)
list2[2]
print(list2)

v<-c(1,2,3,4,5,6,7,8,9)
list3<-list(v,9,TRUE,"C++")
print(list3)

names(list1)<-c("RollNo","Names")
list1["Names"]

list4=list("CSE","IT","EXEC")
print(list4)
print(list4[3])
print("IT" %in% list4)
list5=append(list4,"CS")
print(list5)
list5=append(list5,"CIVIL",after=1)
print(list5)

for(i in list5)
{
  print(i)
}

list6<-c(list1,list4)
list6

list7<-list(50,40,10,20,30)
v2<-unlist(list7)
sort(v2)
```
