### Experiment: Implementing Authentication Using Any Library  

#### **Aim**  
Implementing Authentication using any library.  

---

#### **Theory**  
Authentication is a critical aspect of modern applications to ensure secure access to resources. Using libraries for authentication simplifies the process by providing pre-built functions for password hashing, salting, and verification. One such library, `bcryptjs`, offers secure methods to hash passwords with salts, which protects against common vulnerabilities like dictionary attacks and rainbow table attacks.  

---

#### **Procedure**  
1. **Setup Environment:**  
   - Install Node.js and `bcryptjs` using the command:  
     ```bash
     npm install bcryptjs
     ```

2. **Code**

   
   

   ```javascript
   const bcrypt = require("bcryptjs");
   const readline = require("readline");

   const r1 = readline.createInterface({
       input: process.stdin,
       output: process.stdout,
   });

   const userDatabase = {}; // Simulated database

   const registerUser = async (username, password) => {
       if (userDatabase[username]) {
           console.log("Username Already Taken!");
           return;
       }
       const saltRounds = 10;
       const hashedPassword = await bcrypt.hash(password, saltRounds);
       userDatabase[username] = hashedPassword;
       console.log(`User ${username} Registered Successfully!`);
   };

   const authenticateUser = async (username, password) => {
       const hashedPassword = userDatabase[username];
       if (!hashedPassword) {
           console.log("Authentication Failed!");
           return;
       }
       const match = await bcrypt.compare(password, hashedPassword);
       if (match) {
           console.log("Authorization Successful! Logged In Successfully!");
           console.log(`Stored Hashed Password: ${hashedPassword}`);
       } else {
           console.log("Authorization Failed!");
       }
   };

   const displayMenu = () => {
       console.log("-Menu-");
       console.log("1. Register");
       console.log("2. Login");
       console.log("3. Exit");

       r1.question("Choose Option [1, 2, 3]: ", async (choice) => {
           switch (choice) {
               case "1":
                   r1.question("Enter a Username: ", (username) => {
                       r1.question("Enter a Password: ", async (password) => {
                           await registerUser(username, password);
                           displayMenu();
                       });
                   });
                   break;
               case "2":
                   r1.question("Enter Username: ", (username) => {
                       r1.question("Enter the Password: ", async (password) => {
                           await authenticateUser(username, password);
                           displayMenu();
                       });
                   });
                   break;
               case "3":
                   console.log("Exiting the Menu!");
                   r1.close();
                   break;
               default:
                   console.log("Invalid Option! Try Again.");
                   displayMenu();
           }
       });
   };

   displayMenu(); 
```


```plaintexf
Enter Username: user1  
Enter the Password: password123  
Authorization Successful! Logged In Successfully!  
Stored Hashed Password: $2a$10$abc123...