# password-gen
A Python password generator creates secure, random passwords to enhance online security. Users can specify password length and character sets, including uppercase, lowercase, digits, and special characters. 
import random
import string

def generate_password(length, use_uppercase=True, use_lowercase=True, use_digits=True, use_special=True):
    # Define the character sets to be used
    characters = ''
    if use_uppercase:
        characters += string.ascii_uppercase
    if use_lowercase:
        characters += string.ascii_lowercase
    if use_digits:
        characters += string.digits
    if use_special:
        characters += string.punctuation

    # Ensure there is at least one character type selected
    if not characters:
        raise ValueError("At least one character type must be selected")

    # Generate the password
    password = ''.join(random.choice(characters) for _ in range(length))
    return password

# User input
length = int(input("Enter the desired length of the password: "))
use_uppercase = input("Include uppercase letters? (y/n): ").lower() == 'y'
use_lowercase = input("Include lowercase letters? (y/n): ").lower() == 'y'
use_digits = input("Include digits? (y/n): ").lower() == 'y'
use_special = input("Include special characters? (y/n): ").lower() == 'y'

# Generate and display the password
password = generate_password(length, use_uppercase, use_lowercase, use_digits, use_special)
print(f"Generated password: {password}")
