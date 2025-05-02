# Python-Project-Password-Processing
Utilized Python to retrieve Password Data.
\This project was completed as part of my Codecademy curriculum, focusing on processing password data using Python.

### Project Overview
In this project, I created a Python script that processes a CSV of compromised passwords, extracts usernames, and writes them to a text file. Additionally, the script generates a JSON message for a boss and includes a placeholder for new passwords.

import csv
import json

compromised_users = []

# Open the passwords.csv file
with open("passwords.csv") as password_file:
    password_csv = csv.DictReader(password_file)
    for password_row in password_csv:
        print(f"Adding {password_row['Username']} to compromised_users")  # Debugging line
        compromised_users.append(password_row['Username'])

# Create the compromised_users.txt file
with open('compromised_users.txt', 'w') as compromised_user_file:
    for compromised_user in compromised_users:
        compromised_user_file.write(compromised_user + "\n")

# Create the boss_message.json file
with open('boss_message.json', 'w') as boss_message:
    boss_message_dict = {"recipient": "The Boss", "message": "Mission Success"}
    json.dump(boss_message_dict, boss_message)

# Create the new_passwords.csv file with ASCII art
with open('new_passwords.csv', 'w') as new_passwords_obj:
    slash_null_sig = """
    _  _     ___   __  ____             
    / )( \   / __) /  \(_  _)            
    ) \/ (  ( (_ \(  O ) )(              
    \____/   \___/ \__/ (__)             
     _  _   __    ___  __ _  ____  ____  
    / )( \ / _\  / __)(  / )(  __)(    \ 
    ) __ (/    \( (__  )  (  ) _)  ) D ( 
    \_)(_/\_/\_/ \___)(__\_)(____)(____/ 
            ____  __     __   ____  _  _ 
     ___   / ___)(  )   / _\ / ___)/ )( \
    (___)  \___ \/ (_/\/    \\___ \) __ (
           (____/\____/\_/\_/(____/\_)(_/
     __ _  _  _  __    __                
    (  ( \/ )( \(  )  (  )               
    /    /) \/ (/ (_/\/ (_/\             
    \_)__)\____/\____/\____/
    """
    new_passwords_obj.write(slash_null_sig)



