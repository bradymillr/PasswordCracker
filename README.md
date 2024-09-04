# Password Cracker
This is a simple bruteforce password cracker I made in Python. You input your password, and it generates a password, checks if it is correct, stores incorrect guesses, and repeats until it finds your password.

## Important
Bruteforce methods take a VERY long time. So if you are interesting in testing the code, only use 1 or two characters. Even 2 characters takes more than 1000 guesses. 

## Code

``` Python
import random

user_password = input('Please enter your password: ') #User input
upper_case = ['A','B','C','D','E','F','G','H','I','J','K','L','M','N','O','P','Q','R','S','T','U','V','W','X','Y','Z']
lower_case = ['a','b','c','d','e','f','g','h','i','j','k','l','m','n','o','p','q','r','s','t','u','v','w','x','y','z']
numbers = ['0','1','2','3','4','5','6','7','8','9']
symbols = ['!', '@', '#', '$', '%', '^', '&', '*', '(', ')', '-', '_', '=', '+', '[', ']', '{', '}', '|', '\\', ':', ';', '"', '\'', '<', '>', ',', '.', '?', '/']
# Definining possible values in password

bruteforce_count = 0 #guess counter
all_characters = upper_case + lower_case + numbers + symbols #combining all lists for easy generation
guessed_passwords = set() #creating empty set for guessed passwords to reduce redundancy

def guess_password(length):   #defining the guess loop
    random_chars = [random.choice(all_characters) for _ in range(length)]

    computer_guess = ''.join(random_chars)

    while computer_guess in guessed_passwords:  #checks if generated guess is in the already guessed list
        
        random_chars = [random.choice(all_characters) for _ in range(length)] 
        computer_guess = ''.join(random_chars) #combines characters to form a password guess

    print(computer_guess)
    guessed_passwords.add(computer_guess)  #adds password to guessed list if it does not match user password

    return computer_guess


length = len(user_password)
computer_guess = guess_password(length)

while computer_guess != user_password:
    computer_guess = guess_password(length)
    bruteforce_count = bruteforce_count + 1
  


else:
    print(f'I have your password. Your password is {computer_guess} and it only took {bruteforce_count:,} attempts.')

```
