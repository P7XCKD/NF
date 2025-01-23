```python
print("Testing")

def suml(a):
    return sum(a)

# sum of all items in a list
wow = [1,2,3,4,5]
print("sum of all items in a list is",suml(wow))

def mull(numbers):
    result = 1
    for num in numbers:
        result *= num
    return result

# multiplication of all items in a list
print("multiplication of all items in a list is",mull(wow))
def maxl(a):
    return max(a)

# max of all items in a list
print("max of all items in a list is",maxl(wow))

def revl(a):
    return a[::-1]

# reversed list
print("reversed list is",revl(wow))

def sln(a):
    if len(a) < 2:
        return None
    max1, max2 = a[0], a[1]  
    for x in a:
        if x > max1:
            max2 = max1
            max1 = x
        elif x > max2 and x < max1:
            max2 = x
    return max2

# second largest item in a list
print("second largest item in list is",sln(wow))

def mullo3and5(a):
    return [i for i in a if i % 3 == 0 or i % 5 == 0]

# list of numbers divisible by 3 or 5

print("numbers divisible by 3 or 5 are",mullo3and5(wow))

def eml(a):
    for x in a:
        if(x < 1):
            return "list is empty"
        else:
            
            print("content of list are",a)
            return "list is not empty"
        
# check if list is empty
print(eml(wow))

def ems(a):
    for i in a:
        if i == " " or i == "":
            a.remove(i)
    return a

# remove empty items from list

how = ["hello","bello","","cello",""]
print("list without empty items is",ems(how))


def dupl(a):
    return list(set(a))  

# remove duplicates from list
now = [1,22,44,33,22,44,30]
print("remove duplicate elements",dupl(now))
```