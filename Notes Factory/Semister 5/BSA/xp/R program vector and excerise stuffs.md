```R
# factor
bg <- factor(c("a" ,"b" , "c"))
print(bg)

print(levels(bg))
bg[1]<-"d"
print(bg)

# create data frame

st_df = data.frame (
  name = c("ee","bb","cc","ff"),
  gender =c("M","F","M","F"),
  marks = c(55,23,22,12)
)

print(st_df)

id <- c(1:4)
name <-c("john","rob","mark","iris")
jt <- c("lead","assist","luke","co")
e <- data.frame(id,name,jt)
e

print(summary(st_df))

#accessing a column
print(st_df[1])
print(st_df[["name"]])
print(st_df[1])

# bind stuffs
st_df <- rbind(st_df,c("test","f",69))
print(st_df)
st_df <- cbind(st_df,city=c("mumbai","pune", "goa","lonava" , "delhi"))
print(st_df)


# excercise


# (1; 2; 3; : : : ; 19; 20)
a = c(1:20)
a

# b) (20; 19; : : : ; 2; 1)
b = c(20:1)
b

# (c) (1; 2; 3; : : : ; 19; 20; 19; 18; : : : ; 2; 1)
c = c(c(1:20),c(19:1))
c

tmp = c(4,6,3)
e = rep(tmp,10)
e

f = c(c(rep(tmp[1],11)),c(rep(tmp[3],10)))
f

g = c(c(rep(tmp[1],10)),c(rep(tmp[2],20),c(rep(tmp[3],3))))
g


```

***
```bash

C:\Users\sbmpc.student\Documents>Rscript we.R
[1] a b c
Levels: a b c
[1] "a" "b" "c"
Warning message:
In `[<-.factor`(`*tmp*`, 1, value = "d") :
  invalid factor level, NA generated
[1] <NA> b    c
Levels: a b c
  name gender marks
1   ee      M    55
2   bb      F    23
3   cc      M    22
4   ff      F    12
  id name     jt
1  1 john   lead
2  2  rob assist
3  3 mark   luke
4  4 iris     co
     name              gender              marks
 Length:4           Length:4           Min.   :12.0
 Class :character   Class :character   1st Qu.:19.5
 Mode  :character   Mode  :character   Median :22.5
                                       Mean   :28.0
                                       3rd Qu.:31.0
                                       Max.   :55.0
  name
1   ee
2   bb
3   cc
4   ff
[1] "ee" "bb" "cc" "ff"
  name
1   ee
2   bb
3   cc
4   ff
  name gender marks
1   ee      M    55
2   bb      F    23
3   cc      M    22
4   ff      F    12
5 test      f    69
  name gender marks   city
1   ee      M    55 mumbai
2   bb      F    23   pune
3   cc      M    22    goa
4   ff      F    12 lonava
5 test      f    69  delhi
 [1]  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20
 [1] 20 19 18 17 16 15 14 13 12 11 10  9  8  7  6  5  4  3  2  1
 [1]  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20 19 18 17 16 15
[26] 14 13 12 11 10  9  8  7  6  5  4  3  2  1
 [1] 4 6 3 4 6 3 4 6 3 4 6 3 4 6 3 4 6 3 4 6 3 4 6 3 4 6 3 4 6 3
 [1] 4 4 4 4 4 4 4 4 4 4 4 3 3 3 3 3 3 3 3 3 3
 [1] 4 4 4 4 4 4 4 4 4 4 6 6 6 6 6 6 6 6 6 6 6 6 6 6 6 6 6 6 6 6 3 3 3

C:\Users\sbmpc.student\Documents>^Z^Z^Z
C:\Users\sbmpc.student\Documents>Rscript we.R
[1] a b c
Levels: a b c
[1] "a" "b" "c"
Warning message:
In `[<-.factor`(`*tmp*`, 1, value = "d") :
  invalid factor level, NA generated
[1] <NA> b    c
Levels: a b c
  name gender marks
1   ee      M    55
2   bb      F    23
3   cc      M    22
4   ff      F    12
  id name     jt
1  1 john   lead
2  2  rob assist
3  3 mark   luke
4  4 iris     co
     name              gender              marks
 Length:4           Length:4           Min.   :12.0
 Class :character   Class :character   1st Qu.:19.5
 Mode  :character   Mode  :character   Median :22.5
                                       Mean   :28.0
                                       3rd Qu.:31.0
                                       Max.   :55.0
  name
1   ee
2   bb
3   cc
4   ff
[1] "ee" "bb" "cc" "ff"
  name
1   ee
2   bb
3   cc
4   ff
  name gender marks
1   ee      M    55
2   bb      F    23
3   cc      M    22
4   ff      F    12
5 test      f    69
  name gender marks   city
1   ee      M    55 mumbai
2   bb      F    23   pune
3   cc      M    22    goa
4   ff      F    12 lonava
5 test      f    69  delhi
 [1]  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20
 [1] 20 19 18 17 16 15 14 13 12 11 10  9  8  7  6  5  4  3  2  1
 [1]  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20 19 18 17 16 15
[26] 14 13 12 11 10  9  8  7  6  5  4  3  2  1
 [1] 4 6 3 4 6 3 4 6 3 4 6 3 4 6 3 4 6 3 4 6 3 4 6 3 4 6 3 4 6 3
 [1] 4 4 4 4 4 4 4 4 4 4 4 3 3 3 3 3 3 3 3 3 3
 [1] 4 4 4 4 4 4 4 4 4 4 6 6 6 6 6 6 6 6 6 6 6 6 6 6 6 6 6 6 6 6 3 3 3

C:\Users\sbmpc.student\Documents>

```