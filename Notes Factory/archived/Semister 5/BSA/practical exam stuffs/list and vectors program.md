### list
```R
# --- CREATE (convert vector → list) ---
data_vec <- c("PROBZ", 21, "R", "Python", "Data Analytics")
student_list <- as.list(data_vec)   # conversion

# --- READ / ACCESS ---
print(student_list[[1]])   # name
print(student_list[[3]])   # first subject

# --- UPDATE ---
student_list[[2]] <- 22                      # change age
student_list[[6]] <- "Machine Learning"      # add new element

# --- DELETE ---
student_list[[2]] <- NULL                    # remove age element

# --- DISPLAY FINAL LIST ---
print(student_list)

# --- DICTIONARY (named conversion) ---
dict_data <- c(name="PROBZ", skill1="R", skill2="Python", skill3="ML")
dict_list <- as.list(dict_data)
print(dict_list)

# --- UNDICTIONARY (flatten list) ---
un_dict_list <- unlist(dict_list)
print(un_dict_list)
```
### Vector
```R



# --- CREATE (convert list → vector) ---
num_list <- as.list(c(10, 20, 30, 40, 50))
num_vec <- unlist(num_list)     # conversion to vector

# --- READ / ACCESS ---
print(num_vec[1])        # first element
print(num_vec[2:4])      # elements 2 to 4

# --- UPDATE ---
num_vec[3] <- 35         # modify value
num_vec <- c(num_vec, 60)  # append value

# --- DELETE ---
num_vec <- num_vec[-2]   # remove 2nd element

# --- DISPLAY FINAL VECTOR ---
print(num_vec)

# --- DICTIONARY (named vector from conversion) ---
dict_list <- list(a=10, b=20, c=30)
dict_vec <- unlist(dict_list)  # convert list → vector
print(dict_vec)

# --- UNDICTIONARY (remove names) ---
un_dict_vec <- unname(dict_vec)
print(un_dict_vec)