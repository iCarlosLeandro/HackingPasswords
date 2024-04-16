#HackingTroll friends. Very simple and efective, but with work around :D



import random
import string
import time

def generate_random_password(length):
    return ''.join(random.choices(string.ascii_letters + string.digits + string.punctuation, k=length))

def crack_password(password):
    attempts = 0
    start_time = time.time()  # Captura o tempo de início

    while True:
        chars_left = list(string.ascii_letters + string.digits + string.punctuation)
        guess = ''.join(random.sample(chars_left, k=len(password)))
        attempts += 1
        if guess == password:
            return attempts, time.time() - start_time

while True:
    password_length_input = input("Enter the length of the password to crack (integer or string): ")
    try:
        password_length = len(password_length_input)
        if password_length > 0:
            break
        else:
            print("Invalid input. Please enter a non-empty value.")
    except ValueError:
        print("Invalid input. Please enter a non-empty value.")

target_password = generate_random_password(password_length)

print("Target password:", target_password)

print("Cracking password...")

attempts, elapsed_time = crack_password(target_password)

print(f'The password was cracked in {attempts} attempts and {elapsed_time:.2f} seconds.')
