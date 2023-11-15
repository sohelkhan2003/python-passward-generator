import random
import string

def generate_password(length=12):
    # Define the character sets
    uppercase_letters = string.ascii_uppercase
    lowercase_letters = string.ascii_lowercase
    digits = string.digits
    special_characters = string.punctuation

    # Combine all character sets
    all_characters = uppercase_letters + lowercase_letters + digits + special_characters

    # Ensure the password length is at least 4 characters for each character set
    if length < 4:
        print("Password length must be at least 4.")
        return None

    # Generate the password by randomly selecting characters from the combined set
    password = (
        random.choice(uppercase_letters) +
        random.choice(lowercase_letters) +
        random.choice(digits) +
        random.choice(special_characters) +
        ''.join(random.choice(all_characters) for _ in range(length - 4))
    )

    # Shuffle the password to make it more random
    password_list = list(password)
    random.shuffle(password_list)
    shuffled_password = ''.join(password_list)

    return shuffled_password

# Test the password generator
password_length = int(input("Enter the desired password length: "))
generated_password = generate_password(password_length)

if generated_password:
    print(f"Generated Password: {generated_password}")
