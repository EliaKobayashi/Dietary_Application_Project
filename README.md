# Unit 3 Project: PFC (Protein, Fat, and Calories) Application Documentation

![](Unit3_Pic1.png)

## Criteria A: Planning

### Problem Definition:
 
The client for this project is Kojiro Matsumoto. He is interested in keeping account of his nutrients intake per meal. Specifically, the intake of protein, fat, carbohydrates, and calories. Due to this, he would like an application that would allow him to keep track of his protein, fat, and calories intake per day.

### Success Criteria:

1. The application should have a log in system that checks if the email and password is correct
2. The application should have a register system that registers the inputted username, email, and password.
3. The passwords of users should be encoded in a secure manner.
4. After the user logs in, the user should be able to pick whether they want to log their nutrients intake or monitor their nutrients intakes.
5. The application should include cartoon drawings of food for aesthetic purposes.
6. When the "calculate calories" button is clicked, the average and total calories of the table should show up.
7. When inputting the date, a calendar should appear.
8. When inputting nutrients intakes, it should be saved and appear on the table screen

### Design Statement

I will design and make an application for a client who is interested in keeping track of his protein, fat, carbohydrates and calories intakes per day. The application will allow the client to log in, log their PFC (protein, fat, carbohydrates, and calories) intakes, and monitor their PFC intakes per day. Additionally, the log in system will ensure passwords to be encoded and secure. The application will be constructed using Pycharm, the Python language, and the KivyMD Language. This project will take 4 weeks and will be evaluated according to the criteria set above.

### Rationale for Proposed Solution

For the application, we will be using the Python language, as according to CodingNomads, is the most used language used coding language in the world and the langauge I am most comfortable with. If I were to use another language, I would have to learn the new language, slowing the process of creating the application. Additionally, Python is compatible with the library that is being used (KivyMD). Therefore, using Python is most appropriate for this project compared to alternatives such as JavaScript or C. The library I will be using is KivyMD. KivyMD is a library that can be used with Python. According to Analytics Vidhya, KivyMD is extremely easy to use. Therefore, learning the functions of it will not take long. Furthermore, it facilitates cross-platform applications that can run on Windows, Linux, Android, OSX, IOS, and Rasberry Pi as well. Due to its versatilities, I will be using KivyMD instead of alternatives such as Libavg or PyQT. The database I will be using is SQLite. According to SQLitetutorial, SQLite allows  a single database connection to access multiple database files simultaneously. Furthermore, is capable of creating in-memory databases that are fast to work with (SQLite tutorial). Due to this, I have chosen SQLite rather than alternatives such as Oracle Database, MariaDB, or IMB db2.

### Citations

1. Wali, K., Ramnani, M., Krishna, S., &amp; Chatterjee, P. (2021, May 29). 8 python GUI frameworks for developers. Analytics India Magazine. Retrieved February 24, 2022,
2. What is KivyMD: Creating android machine learning apps using KivyMD. Analytics Vidhya. (2021, July 6). Retrieved February 24, 2022,
3. What is sqlite? top sqlite features you should know. SQLite Tutorial. (2020, July 8). Retrieved March 9, 2022
4. Why learn python? 6 reasons why it's so hot right now. CodingNomads. (2022, January 19). Retrieved February 24, 2022, 

## Criteria B: Solution Overview

### System Diagram

![](systemdiagram.png)

Figure 1. The System Diagram For the Application

As shown in Fig.1, the proposed solution runs on Python and a KivyMD library. Furthermore, it is developed using Pycharm. The proposed application has 12 inputs which vary from personal information, login information, and daily nutrients information. The application will use SQLite as the database. The output will be a calender screen. If the user clicks on a date, the nurtients information of the date will be displayed.

### Wireframe

Change the wireframe
![](wireframe2.jpeg)

Figure 2. The Wire Frame For the Application

As shown in Fig.2, the wire frame details the plan as to how the application will look. The app will open with a log in page. If the register button is clicked, the user will be able to register by inputing their chosen username, email, and password. Once the register button is clicked, it will redirect the user to the home page. Next, the user can pick to input their nutrients intake, monitor their daily intake, or log out. Once the input button is clicked, the user logs the date, protein, fats, carbohydrates, and calories intakes. Once the user clicks the log button, they are redirected to the home page. If the table screen is selected where users can see all the logged nutrients informations. Users also have the option to calculate the total and average calories. Then, users can click the back button where they are directed to the homepage.

### ER Diagram

![](erdiagram3.jpeg)

Figure 3. ER Diagram For the Attributes Requested By the Client

As shown in figure 3, in the "nutrients" table, the attributes are "protein", "fats", "calories", "carbohydrates", "day_picked". This table details all the nutrients that the client would like to log into the application. The second class which is "User" has the attributes "id", "username", "email", "password". This class details the email and information as well as log in information of the users.

### Table of Data

![](table_comp.jpeg)

Figure 4. A Table Representing the Data In the ER Diagram

As shown in figure 4, the two tables represent the two classes and the attributes in the classes shown in the ER diagram. Furthermore, the data in the second row of each table showcase all the inputs of each attribute, such as the personal information, the log in information, and the nutrients infomration of logged in March 2 of the client. 

### UML Diagram

![](umldiagram.jpeg)

Figure 5. The UML Diagram For the Classes In the Application

As shown in figure 5. the UML diagram shows the attribuites and the methods for the two classes. There are only "get" methods as the application's function is only to store data display it at the request of the users.

### Flow Diagrams

![](3_flowdiagram.jpeg)

Figure 6. The flow diagram for when users try loggin in. If the password is correct, they are directed to the home page. On the other hand, if the password is incorrect, it prints out "User does not exist".

![](3_flowdiagram2.jpeg)

Figure 7. The flow diagram is for calculating the average and total calories according to the database. There is a button on the screen titled "calculate calories". When pressed, the total and average calories poop up.

![](3_flowdiagram3.jpeg)

Figure 8. The flow diagram is for the query functions. "query_user" is for verifying if the password entered in the login screen is correct to their email. Meanwhile, "query_files" is for fetching all the data from the "nutrient" table and will be put in the Table Screen.

### Test Plan

| Description                                                                                                                                                                           | Type                            | Testing steps                                                                                                                                                                                                                                              | Output                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Testing if the login works                                                                                                                                                            | Functional: Integration testing | 1.Open the application 2.Input the registered email 3.Input the registered password 4.Click the "login" button 5.End the program                                                                                                                           | The screen should change to a screen titled "Home Page" without bugs.                                                                                                                                                                                                                                                                                                                                                                                               |
| Testing if the registry works                                                                                                                                                         | Functional: Integration testing | 1.Open the application 2.Click on the button titled "Register" 3.Input username 4.Input email 5.Input password 6.End the program                                                                                                                           | The screen should change from the login screen to a screen titled "Register Screen"  when the register button is clicked. After inputting all necessary informations, the  screen should change to a screen titled "Home Page" after the register button is clicked.  After closing and re-openning the application, the user should be able to log in with the registered information.                                                                             |
| Testing if inputting nutrients information works                                                                                                                                      | Functional: Integration testing | 1.Open the application 2.Log in 3.Click on the "Input" button in the home page 4.Input information about nutrients and date 5.Click the "Input" button 6.Click on the "Table" button 7.Check if the inputted information is on the table 8.End the program | The screen should change from the home page screen to a screen titled "Home Page". After inputting nutrients informations, the screen should change to the home page screen after the input button is clicked. To check if the inputted information is logged in the  database, click on the button on the home page called table. After doing so, the screen should be changed to a screen titled "Table Screen". The inputted information should be on the table. |
| Testing if the table screen works                                                                                                                                                     | Functional: Integration testing | 1.Open the application 2.Log in 3.Click on the "Table" button 4.Click on the "Calculate calories" button 5.End the program                                                                                                                                 | The table in the table screen should have six columns. The first being a box that the user can check. Then, protein, fats, carbs, calories, and then date_picked. Additionally, when the "calculate calories" button is clicked, the texts that were written as "Total calories" and "Average Calories" should change to the total and average calories of all informatioin on the table.                                                                           |
| Reviewing if the code has adequate comments, function name,  and variable name.                                                                                                       | Non-functional: Code review     | As this reviews the quality of the code, there are no inputs.                                                                                                                                                                                              | The code will contain comments to explain what is going on in the code. Furthermore, names  of variables are simple.                                                                                                                                                                                                                                                                                                                                                |
| Testing if the table in the table screen shows the appropriate  nutrients informations without glitches or bugs. Additionally, all newly inputted informations should pop up as well. | Non-functional: Load testing    | 1. Open the application 2. Log in 3. Click on the "Table" button                                                                                                                                                                                           | All informations on the table should be appropriate to which column it falls under. Furthermore, if nutrients information is newly added, it should appear on the table.                                                                                                                                                                                                                                                                                            |

### Record of Tasks
| Task No. | Planned Action                                           | Time Estimate  | Target Completion Date | Criteria |
|----------|----------------------------------------------------------|----------------|------------------------|----------|
| 1        | Brainstorm and write the problem definition              | 15 mins        | February 28            | A        |
| 2        | Brainstorm and write the success criteria                | 15 mins        | February 28            | A        |
| 3        | Brainstorm and write the design statement                | 20 mins        | March 2                | A        |
| 4        | Brainstorm and write the rationale for proposed solution | 30 mins        | March 2                | A        |
| 5        | Write citations                                          | 15 mins        | March 2                | A        |
| 6        | Write the details of the application                     | 20 mins        | March 2                | A        |
| 7        | Draw and describe the ER diagram                         | 20 mins        | March 4                | B        |
| 8        | Draw and describe the table of data                      | 15 mins        | March 4                | B        |
| 9        | Draw and describe the UML diagram                        | 15 mins        | March 4                | B        |
| 10       | Code the log in screen                                   | 1 hour         | March 7                | C        |
| 11       | Code the register screen                                 | 1 hour         | March 9                | C        |
| 12       | Meeting with client                                      | 5 minutes      | March 10               | A        |
| 13       | Code switches between screens                            | 30 mins        | March 10               | C        |
| 14       | Code inserting inputs of the user to the databse         | 50 mins        | March 10               | C        |
| 15       | Code the encryption of passwords using hash              | 40 mins        | March 28               | C        |
| 16       | Meeting with client                                      | 5 minutes      | March 28               | A        |
| 17       | Fix up the register screen                               | 15 mins        | March 30               | C        |
| 18       | Fix up the hash password encryption                      | 15 mins        | March 30               | C        |
| 18       | Draw and describe the flow diagrams                      | 20 mins        | March 31               | A        |
| 19       | Create the Input screen                                  | 30 minutes     | April 2                | C        |
| 20       | Create the nutrient table                                | 30 minutes     | April 2                | C        |
| 21       | Create the Table screen                                  | 45 minutes     | April 8                | C        |
| 22       | Fix the Table Screen                                     | 2 hours        | April 10               | C        |
| 23       | Create a calendar for the date                           | 25 mins        | April 11               | C        |
| 24       | Create the calculation for calories                      | 30 mins        | April 13               | C        |
| 25       | Write the test plans                                     | 30 mins        | April 13               | C        |
| 26       | Meeting with client for final product                    | 15 mins        | April 13               | A        |
| 27       | Finish Criteria C                                        | 2 hours        | April 14               | C        |
| 28       | Finish video for Criteria D                              | 1 hour 30 mins | April 15               | D        |

## Criteria C: Development

### Techniques Used

1. For loops
2. If function
3. Building UI through the KivyMD library
4. OOP coding with Python
5. Working with database from SQLite
6. Connecting KivyMD, Python, and SQLite

### UI Creating Using KivyMD

```.py
ScreenManager:
    id: screen_manager
    # Names of each screen
    LoginScreen:
        id: LoginScreen
        name: "LoginScreen"

    RegisterScreen:
        name: "RegisterScreen"

    HomePage:
        name: "HomePage"

    InputScreen:
        name: "InputScreen"

    TableScreen:
        id: TableScreen
        name: "TableScreen"
```
The first part of creating the application is to design and code the user interface (UI). The UI allows users to access the program. In the Kivy language (which is what is being used as the KivyMD library is utilized) objects are relative and are layered on top of each other. The code above is to set up all the screens that will be used in the program. 

```.py
# The build for the register screen
<RegisterScreen>
    FitImage:
        source: 'veg_pic.jpg'
    # The layout of the screen
    MDBoxLayout:
        orientation: "vertical"
        size_hint: 1,1
        pos_hint: {"center_x": 0.5, "center_y": 0.5}
```
The code above is an example of how the design of the screen is first set up. The register screen is one of the 5 screens I have created. Firstly, I refer to the file name of the image I want to set as the background. After placing the jpg file as the background, I create the orientation of the entire screen. The orientation is how objects will be placed in relation to each other. For this application, a vertical orientation is preferred as objects can go below each other.

```.py
        # A white rectangle to put the buttons, labels, etc.
        MDCard:
            size_hint: .5, .5
            pos_hint: {"center_x": 0.5, "center_y": 0.5}
            elevation: 10
            padding: 25
            padding: 25
            halign: 'center'

            # The layout inside the card
            MDBoxLayout:
                size_hint: 0.8,0.8
                orientation: "vertical"
                pos_hint: {"center_y":0.5, "center_x":0.5}
                ```
After setting up the layout of the screen, I added a white rectangle on the screen where I will be placing objects to make it organized. Furthermore, I added a layout inside the card as objects will only be placed inside the MDCard.
```.py
                # Title of the screen
                MDLabel:
                    id: register_label
                    text: "Register"
                    font_size: 60
```
Now that the basics of the screen is created, I created the title of the screen ("Register").
```.py
                # Text field to input username
                MDTextField:
                    id: username_register
                    hint_text: "username"

                # Text field to input email
                MDTextField:
                    id: email_register
                    hint_text: "email"

                # Text field to input password
                MDTextField:
                    id: password_register
                    hint_text: "password"
```
In order for users to register, they would need to input information they will need to log in with. To do so, I am using test field as the place for users input such information. "hint_text" is used to indicate which information users should input in which text field.
```.py
                # button to go to the register screen
                MDRaisedButton:
                    text: "Register"
                    size_hint: 1, 0.8
                    on_release:
                        root.register()
                        
```
After all the necessary information is inputted, it must be saved on a database. To do so, there is a button called register. The register button will save all the inputted information into a database. To do so, I created a method in Python titled "register()". After the button is clicked, not only will the inputted information be saved into a database, but the screen will also change to the home page.

```.py
class RegisterScreen(self):
    pass
    
class MainApp(MDApp):
    def build(self):
        pass
```
Although the UI is designed, logic is necessary to make all the functions work. To do so, I created a Python file that compliments the KivyMD file. You need a class for each screen and a class for the app itself. The class names of the screens must match the names of the screens written in the KivyMD file. Meanwhile, the name of the app class must be the same as the name of the KivyMD file. The code above does not include all the methods and objects in my RegisterScreen file. I wrote pass simply to show the logic of the Python file.

### Creating Tables
 
 ```.py
 # connection to sqlite
    def __init__(self, name):
        self.name = name
        self.connection = sqlite3.connect(self.name)
        self.cursor = self.connection.cursor()
     def close(self):
        self.connection.close()
```  
To create tables, I am using sqlite3 as the database. The code above is the conncetion between Python and the sqlite database. The benefits of using sqlite is that it is really easy to use with Python. I simply have to create a class with their attributes in it which will be shown in the next piece of code.

```.py
   # Function to create a table that includes the login details of a user

    def create(self):
        self.cursor.execute("""
        CREATE TABLE if not exists Users(
        id INTEGER primary key,
        username VARCHAR(200),
        email VARCHAR(255) not null unique,
        password VARCHAR(256) not null
        );
        """)
        self.cursor.execute("""
        CREATE TABLE if not exists nutrient(
        protein INTEGER,
        fats INTEGER,
        carbohyrdates INTEGER,
        calories INTEGER,
        date_picked day
        );
        """)
        self.connection.commit()
```
The function above is to create the two tables ("Users", "nutrient") I need based on my diagrams. Each row after inside the paranthesis of a table represents an attribute in the table. The first word is the name of the attribute. After the names of the attributes, the type of attribute is declared. The values are inputted in the LoginScreen class and the InputScreen class.
### Saving Values Into Tables

```.py
    def create_new_user(self, username, password, email):
        self.cursor.execute("INSERT into Users values(?,?,?,?)", (random.randint(1,1000000), username, email, encrypt_password(password)))
        self.connection.commit()
```
The method create_new_user is used later in the register screen to input new values into the Users table

```.py
    # Function to save the registered information in the database
    def register(self):
        email_entered = self.ids.email_register.text
        username_entered = self.ids.username_register.text
        password_entered = self.ids.password_register.text
        db = database("app_database.db")
        db.create_new_user(username=username_entered, email=email_entered, password=password_entered)
        db.close()
        self.parent.current = "HomePage"
```
After setting up the tables in the database, we have to put values inside. For the User table, this is done in the register method. This is so that when users click the button called register in the Register Screen, the inputted values will be saved in the Users table. By inputting the information inputted by the users in the paranthesis next to "db.create_new_user", values will be saved in the database. 

```.py
    def create_new_input(self, protein, fats, carbohydrates, calories, date_picked):
        self.cursor.execute(f"INSERT into nutrient values('{protein}','{fats}','{carbohydrates}','{calories}','{date_picked}');")
        self.connection.commit()
```
The method create_new_input is used later in the input screen to input new values into the nutrient table.

```.py
    def on_save(self, value):
        InputScreen.select_date = value

    # Click cancel
    def on_cancel(self):
        pass

    def input_date(self):
        from datetime import datetime
        date_dialog = MDDatePicker()
        date_dialog.bind(on_save=self.on_save, on_cancel=self.on_cancel)
        date_dialog.open()

    def input_data(self):
        enter_protein = self.ids.input_protein.text
        enter_fat = self.ids.input_fat.text
        enter_carb = self.ids.input_carb.text
        enter_calorie = self.ids.input_calorie.text
        enter_date = InputScreen.select_date
        db = database("app_database.db")
        db.create_new_input(protein=enter_protein, fats=enter_fat, carbohydrates=enter_carb, calories=enter_calorie, date_picked=enter_date)
        db.close()
        self.parent.current = "HomePage"
```
For the nutrient table, I am saving the values inputted by the users in the input screen. To input dates, a calendar will appear when the "date" button is clicked. This is done through using MDDatePicker() in the input_date method. Once a date is clicked, its value (date) will be saved in the date_picked attribute. By using "InputScreen.select_date" I am able to use a value from another method. Values are placed in the paranthesis next to "db.create_new_input" to save it in the table.
### Creating the Login System

```.py
# Function to see if the login information is in the database
    def try_login(self):
        input_email = self.ids.email.text
        input_password = self.ids.password.text
        db = database("app_database.db")
        user = db.query_user(email=input_email)
        if user:
            id, username, email, hashed_pwd = user
            if check_password(password = input_password, hashed = hashed_pwd):
                self.parent.current = "HomePage"
            else:
                self.ids.login_label.text = "password is incorrect"
        else:
            self.ids.login_label.text = "User does not exist"
```
To log in, I created a system so that the method checks whether the inputted email is in the database. If it is not, the title text changed to "User does not exist". If the email is correct, the method checks if the password is correct and corresponding to the email. If it does not, the title text changes to "password is incorrect", If the password is correct, the screen changed to the home page.
### Creating the Home Page

```.py
# Class for home page screen
class HomePage(MDScreen):
    # Function for the screen to change to the login screen

    def go_to_login(self):
        self.parent.current = "LoginScreen"
    # Function for the screen to change to the input screen

    def go_to_InputScreen(self):
        self.parent.current = "InputScreen"
    # Function for the screen to change to the monitor screen

    def go_to_MonitorScreen(self):
        self.parent.current = "MonitorScreen"
    # Function for the screen to change to the table screen

    def go_to_TableScreen(self):
        self.parent.current = "TableScreen"
```
The home page is quite simple with only four buttons. The first changing the screen to the Login screen. The second changing the screen to the Input screen. The third changing the screen to the Monitor screen. Lastly, changing the screen to the Table screen.
### Creating the Table Screen

```.py
class TableScreen(MDScreen):
    # class attribute
    data_tables = None
    # Get data from database
    def on_pre_enter(self, *args):
        db = database("app_database.db")
        query = db.query_files()
        db.close()
```
The code above is to connect the class with the database. Additionally, the query object retrieves all the data from the databases.

```.py
        #The first part is the size and position of the table on the screen
        self.data_tables = MDDataTable(
            size_hint=(1, 0.6),
            pos_hint={"center_x": .5, "top": 0.9},
            use_pagination=True,
            check=True,
            # name column, width column, sorting function column(optional)
            column_data=[
                ("protein", 50),
                ("fats", 30),
                ("carbohydrates", 50),
                ("calories", 40),
                ("date_picked", 60)
            ],
            row_data=query
        )
```
Using MDDataTable, the position and size of the table on the screen is determined first. Then, the attributes of the nutrient table is written inside the [] next to the "column_date=". The attributes wrriten above should match the spelling and the order of the attributes in the table. The data in the rows of the table in the screen should match all the values of the nutrient table. To do so, I put all query information in the "row_data".

```.py
    #The function to calculate the total and average calories
    def calculations(self):
        db = database("app_database.db")
        query = db.query_files()
        total_calories = 0
        # If not all attributes need to be used you can use _.
        for row in query:
            _, _, _, calories, _ = row
            total_calories += calories
        average_calories = total_calories/len(query)
        
        #To change the texts on the screen
        self.ids.average_calories.text = f"average: {average_calories} kcal"
        self.ids.total_calories.text = f"total: {total_calories} kcal"

        db.close()
``` 
The last part of the Table Screen is the calculation of the average and total calories. To do so, a for loop is used. If attributes are not being used, you can use an underline. After the calculation is done, the texts on the screen titled "Average calories" and "Total calories" change to numbers.

![](loginscreen.png)
Figure 9. The login screen

![](registerscreen.png)
Figure 10. The register screen 

![](homepage.png)
Figure 11. The home page

![](inputscreen.png)
Figure 12. The input screen

![](calendar.png)
Figure 13. The calendar to input dates

![](table_screenpic.png)
Figure 14. The table screen

## Criteria D: Functionality

https://www.youtube.com/watch?v=x0dyokWELlg
