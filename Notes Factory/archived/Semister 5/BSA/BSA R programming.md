### code
```R
print("Hellow World")
a='5'
b<-'5'
c=as.integer(a)+as.integer(b)
print(paste("The value is:",c,sep='-'))
d="Hellow World"
e=TRUE
f=5+3i
typeof(f)

num1<-as.integer(readline(prompt = "Enter 1st number: "))
num2<-as.integer(readline(prompt = "Enter 2nd number: "))
num3<-num1+num2
num3

age <- 22

if (age >= 18 && age<=60) {
  print("Eligible to drive")
} else{
  print("Not eligible to drive")
}

index<-as.integer(readline("Enter the index: "))
sub<- switch(
  index,
  "C",
  "C++",
  "Java",
  "Python",
)
print(sub)

num <- 5
factorial <- 1
while(num > 0) {
  factorial <- factorial * num
  num <- num - 1
}
print(factorial)

functionname<-function(){
  print("Hellow World")
}
functionname()

#paramaterized function
add<-function(x,y){
  print(x+y)
}
add(10,20)

x<-5
repeat{
  x<-x+1
  if(x==8){
    break
  }
  print(x)
}

```
***
### output
```R
[1] "Hellow World"
[1] "The value is:-10"
[1] "complex"
[1] 20
[1] "Eligible to drive"
[1] "Java"
[1] 120
[1] "Hellow World"
[1] 30
[1] 6
[1] 7


```