```python 
# pattern
for x in range(4):
    space = x
    star = 3-x
    print(" " * space + "*" * star)
```
![image](.attachments/3cc656586621573af9d8de33507086cc7c1bceeb.png) 
***
```python
# pattern 3
r = 4
for x in range(r):
    space = r - x -1 
    
    star = 2 * x + 1
    print(" " * space +"*" * star)
   
```
![image](.attachments/c6dd1212ed9718cdf61d9427be83c850427586e1.png) 
***
```python
# pattern 5
r = 3
for x in range(r):
  
    star =  x + 1
    print( "*" * star)
   
for w in range(r -1):
  
    star = r - 2 - w
    print( "*" * (star+1))
```
![image](.attachments/e6d8ec4652ff47f9c3b337aa89e1a960c0733932.png) 