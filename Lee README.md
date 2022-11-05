- 👋 Hi, I’m @Rockleewu
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
Rockleewu/Rockleewu is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
def register(): 
     db = open("access_register.txt", "r") 
     username = input("Create your email id in format __@__.__: ") 
     user = [] 
     for i in db: 
         x = i.split(",") 
         user.append(x[0]) 
  
     if username in user: 
         print("Try another username") 
         register() 
  
     elif username.count('@') != 1 and username.count('.') !=1: 
         print("Enter Username in proper format") 
         register() 
  
     elif username.index("@") - username.index('.') == 1: 
         print("enter the propre format") 
         register() 
  
  
     elif username[0] in range(0, 9): 
         print("Start with characters only") 
         register() 
  
     elif (username[0] == '@' or username[0] == '$' or username[0] == '_' or username[0] == '%' or 
           username[0] == '!' or username[0] == '#' or username[0] == '*' or username[0] == '&'): 
         print("Start with only characters") 
         register() 
  
     else: 
         print("Username created Succefully") 
  
     password = input("Create your password with atleast one capital letter one integer and one special character: ") 
     s = False 
  
     if len(password) < 5 and len(password) > 16: 
         print("Create Password with length between 5 an 16, Try Again") 
         register() 
  
     if len(password) > 5 and len(password) < 16: 
         l, u, p, d = 0, 0, 0, 0 
         for i in password: 
             if i.isdigit(): 
                 d += 1 
             if i.islower(): 
                 l += 1 
             if i.isupper(): 
                 u += 1 
             if (i == '@' or i == '$' or i == '_' or i == '%' or i == '!' or i == '#' or i == '*' or i == '&'): 
                 p += 1 
             if (l >= 1 and u >= 1 and p >= 1 and d >= 1 and l + p + u + d == len(password)): 
                 s = True 
  
     if s: 
         c = input("Confirm Password: ") 
         while (c != password): 
             print("Password not match, Try Again") 
             c = input("Try Again: ") 
  
     else: 
         print("Try again") 
         register() 
  
     file = open("access_register.txt", "a") 
     file.write(username+ "," + password + "\n") 
     file.close() 
     login() 
  
 def login(): 
     X=input("Enter your username to login: ") 
     X = X.strip() 
     db = open("access_register.txt", "r") 
     d = [] 
     for line in db: 
         x = line.split(",") 
         d.append(x[0]) 
  
     if X in d: 
         Y=input("Please Enter your password: ") 
         Y=Y.strip() 
         file1=open("access_register.txt","r").readlines() 
         for x in file1: 
             x=x.strip() 
             info=x.split(",") 
             if X==info[0] and Y==info[1]: 
                 print("Welcome in the digital world") 
             else: 
                 F = input("Forgot Password [Y/N] : ") 
  
                 if F == "N": 
                     print("try") 
                     login() 
  
                 if F == "Y": 
                     b = input("Create your new password with atleast one capital letter one integer and one special character: ") 
                     s = False 
  
                     if len(b) < 5 and len(b) > 16: 
                         print("Create Password with length between 5 an 16, Try Again") 
                         register() 
  
                     if len(b) > 5 and len(b) < 16: 
                         l, u, p, d = 0, 0, 0, 0 
                         for i in b: 
                             if i.isdigit(): 
                                 d += 1 
                             if i.islower(): 
                                 l += 1 
                             if i.isupper(): 
                                 u += 1 
                             if ( 
                                     i == '@' or i == '$' or i == '_' or i == '%' or i == '!' or i == '#' or i == '*' or i == '&'): 
                                 p += 1 
                             if (l >= 1 and u >= 1 and p >= 1 and d >= 1 and l + p + u + d == len(b)): 
                                 s = True 
  
                     if s: 
                         c = input("Confirm Password: ") 
                         while (c != b): 
                             print("Password not match, Try Again") 
                             c = input("Try Again: ") 
  
                     else: 
                         print("Sorry,Try again to login") 
                         login() 
  
                     file = open("access_register.txt", "w") 
                     file.write(X + "," + b + "\n") 
                     file.close() 
  
     else: 
         print("Unregister user you need to register first") 
         register() 
  
 def welcome(): 
     print("Login and New Registration") 
     W=input("Login|Register[L/R]: ") 
     if W=="L": 
         login() 
     elif W=="R": 
         register() 
     else: 
         print("Enter in proper way") 
         welcome() 
 welcome() 
  
  
 ***************************************Registration*************************************************************** 
 Login and New Registration 
 Login|Register[L/R]: R 
 Create your email id in format __@__.__: saranya123@gmail.com 
 Username created Succefully 
 Create your password with atleast one capital letter one integer and one special character: S@ranya123 
 Confirm Password: S@ranya123 
  
 ***************************************Login*************************************************************** 
 Enter your username to login: saranya123@gmail.com 
 Please Enter your password: S@ranya123 
      
  
 ***************************************Password Change***************************************************************     
 Forgot Password [Y/N] : Y 
 Create your new password with atleast one capital letter one integer and one special character: S@thish8687 
 Confirm Password: S@thish8687 
 Forgot Password [Y/N] : N 
 try 
 ***************************************Login succefully*************************************************************** 
 Enter your username to login: saranya123@gmail.com 
 Please Enter your password: S@thish8687 
 Welcome in the digital world
