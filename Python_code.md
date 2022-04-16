```.py
from datetime import date
from kivy.core.window import Window
from kivy.metrics import dp
from kivymd.app import MDApp
from kivymd.uix.datatables import MDDataTable
from kivymd.uix.screen import MDScreen
import sqlite3
import random
from passlib.context import CryptContext
from kivymd.uix.picker import MDDatePicker
Window.size = (600, 700)

# configuration
pwd_context = CryptContext(
    schemes=["pbkdf2_sha256"],
    default = 'pbkdf2_sha256',
    pbkdf2_sha256__default_rounds=3000
)
# encrypting password

def encrypt_password(password):
    return pwd_context.hash(password)
# function to check if a password is correct

def check_password(password, hashed):
    return pwd_context.verify(password, hashed)

class database:
    # connection to sqlite
    def __init__(self, name):
        self.name = name
        self.connection = sqlite3.connect(self.name)
        self.cursor = self.connection.cursor()

    def close(self):
        self.connection.close()
    # Function to create a table that includes the login details of a user

    def create(self):
        # Declaring the attributes of the Users table
        self.cursor.execute("""
        CREATE TABLE if not exists Users(
        id INTEGER primary key,
        username VARCHAR(200),
        email VARCHAR(255) not null unique,
        password VARCHAR(256) not null
        );
        """)
        # Declaring the attributes of the nutrient table
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
    # function to see is a user's email exists

    def query_user(self, email):
        # checks whether the inputted email is in the database
        results = self.cursor.execute(f"SELECT * from Users where email='{email}';")
        if results:
            return results.fetchone()
        else:
            return ["", "", "", ""]
    # query function for the table screen

    def query_nutrient(self):
        # gets all the data from the nutrient table
        results = self.cursor.execute(f"SELECT * from nutrient;").fetchall()
        if results:
            print(len(results))
            if len(results)<2:
                results.append(["","","",""])
            return results
        else:
            return ["", "", "", ""]
    # Function to create a new log of nutrients

    def create_new_input(self, protein, fats, carbohydrates, calories, date_picked):
        self.cursor.execute(f"INSERT into nutrient values('{protein}','{fats}','{carbohydrates}','{calories}','{date_picked}');")
        self.connection.commit()
    # function to create a new user in the database

    def create_new_user(self, username, password, email):
        self.cursor.execute("INSERT into Users values(?,?,?,?)", (random.randint(1,1000000), username, email, encrypt_password(password)))
        self.connection.commit()

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
# Class for the input screen

class InputScreen(MDScreen):

    select_date = None

    # Function for the screen to change to the home page
    def go_to_HomePage(self):
        self.parent.current = "HomePage"

    def on_save(self, instance, value, date_range):
        InputScreen.select_date = value

    # Click cancel
    def on_cancel(self):
        pass
    # Inputting a date from the calendar

    def input_date(self):
        date_dialog = MDDatePicker()
        date_dialog.bind(on_save=self.on_save, on_cancel=self.on_cancel)
        date_dialog.open()
    # Inputting all the nutrient and date data into the nutrient table

    def input_data(self):
        enter_protein = self.ids.input_protein.text
        enter_fat = self.ids.input_fat.text
        enter_carb = self.ids.input_carb.text
        enter_calorie = self.ids.input_calorie.text
        # taking an object from another method in the same class
        enter_date = InputScreen.select_date
        # The name of the database
        db = database("app_database.db")
        db.create_new_input(protein=enter_protein, fats=enter_fat, carbohydrates=enter_carb, calories=enter_calorie, date_picked=enter_date)
        db.close()
        self.parent.current = "HomePage"

# Class for the register screen

class RegisterScreen(MDScreen):
    # Function to save the registered information in the database

    def register(self):
        email_entered = self.ids.email_register.text
        username_entered = self.ids.username_register.text
        password_entered = self.ids.password_register.text
        print(email_entered, password_entered)
        db = database("app_database.db")
        db.create_new_user(username=username_entered, email=email_entered, password=password_entered)
        db.close()
        self.parent.current = "HomePage"
# Class for the login screen

class LoginScreen(MDScreen):
    # Function to see if the login information is in the database

    def try_login(self):
        print("Trying logging")
        input_email = self.ids.email.text
        input_password = self.ids.password.text
        print(input_email, input_password)
        db = database("app_database.db")
        user = db.query_user(email=input_email)
        if user:
            id, username, email, hashed_pwd = user
            if check_password(password = input_password, hashed = hashed_pwd):
                self.parent.current = "HomePage"
            else:
                print("password is incorrect")
        else:
            self.ids.login_label.text = "User does not exist"
    # Function for the screen to change to the register screen

    def go_to_register(self):
        self.parent.current = "RegisterScreen"
# The application class

class draft4(MDApp):
    def build(self):
        return
# Class for the table screen

class TableScreen(MDScreen):
    # class attribute
    data_tables = None
    # Get data from database
    def on_pre_enter(self, *args):
        db = database("app_database.db")
        query = db.query_nutrient()
        print("here",query)
        db.close()

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
        self.data_tables.bind(on_row_press=self.on_row_press)
        self.data_tables.bind(on_check_press=self.on_check_press)
        self.add_widget(self.data_tables)

    def on_check_press(self, table, current_row):
        print("row pressed", current_row)
        id, username, email, password = current_row

    def on_row_press(self, table, row):
        print("row was clicked",row)
        print(row.text)

    #The function to calculate the total and average calories
    def calculations(self):
        db = database("app_database.db")
        query = db.query_nutrient()
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

# db = database("app_database.db")
# db.create()
# db.close()


m = draft4()
m.run()
```
