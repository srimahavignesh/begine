import random
import string

def generate_password(username, birthdate, length=12):
    # Character sets
    characters = string.ascii_letters + string.digits + string.punctuation

    # Mix username + birthdate into the pool
    extra = username + str(birthdate)
    all_chars = characters + extra  

    # Generate password (shuffled mix of random + user info)
    password = ''.join(random.choice(all_chars) for _ in range(length))

    return password

def main():
    print("Welcome to the Password Generator!")
    username = input("Enter your username: ")
    birthdate = input("Enter your birthdate (e.g., 1998): ")
    length = int(input("Enter the length of the password (default is 12): ") or 12)

    password = generate_password(username, birthdate, length)

    # Shuffle again so username/birthdate chars don’t stay in one place
    password = ''.join(random.sample(password, len(password)))

    print("Generated Password:", password)

if __name__ == "__main__":
    main()
