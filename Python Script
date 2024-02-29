from cryptography.hazmat.backends import default_backend
from cryptography.hazmat.primitives import hashes, padding
from cryptography.hazmat.primitives.ciphers import Cipher, algorithms, modes
import os

def generate_key():
    # Generate a random 256-bit key
    return os.urandom(32)

def generate_iv():
    # Generate a random initialization vector (IV)
    return os.urandom(16)

def encrypt_file(file_path, key):
    iv = generate_iv()
    cipher = Cipher(algorithms.AES(key), modes.CBC(iv), backend=default_backend())
    encryptor = cipher.encryptor()
    
    with open(file_path, 'rb') as f:
        plaintext = f.read()
    
    padder = padding.PKCS7(algorithms.AES.block_size).padder()
    padded_plaintext = padder.update(plaintext) + padder.finalize()
    ciphertext = encryptor.update(padded_plaintext) + encryptor.finalize()
    
    with open(file_path + '.enc', 'wb') as f:
        f.write(iv + ciphertext)

def decrypt_file(file_path, key):
    with open(file_path, 'rb') as f:
        iv = f.read(16)
        ciphertext = f.read()
    
    cipher = Cipher(algorithms.AES(key), modes.CBC(iv), backend=default_backend())
    decryptor = cipher.decryptor()
    padded_plaintext = decryptor.update(ciphertext) + decryptor.finalize()
    
    unpadder = padding.PKCS7(algorithms.AES.block_size).unpadder()
    plaintext = unpadder.update(padded_plaintext) + unpadder.finalize()
    
    with open(file_path.replace('.enc', ''), 'wb') as f:
        f.write(plaintext)

if __name__ == "__main__":
    choice = input("Do you want to (E)ncrypt or (D)ecrypt a file? ").upper()
    if choice == 'E':
        file_path = input("Enter the path of the file to encrypt: ")
        key = generate_key()  # Remember to save this key for decryption
        encrypt_file(file_path, key)
        print(f"File encrypted successfully. Key for decryption: {key.hex()}")
    elif choice == 'D':
        file_path = input("Enter the path of the file to decrypt: ")
        key_hex = input("Enter the decryption key: ")
        key = bytes.fromhex(key_hex)
        decrypt_file(file_path, key)
        print("File decrypted successfully.")
    else:
        print("Invalid choice.")
