# Description

This tool provides a simple solution for encrypting and decrypting files using the AES-256 algorithm in CBC mode. It's designed to showcase the application of cryptographic principles, ensuring data confidentiality and integrity by protecting sensitive information against unauthorized access and modifications.


## Dependencies

This script relies on Python's cryptography library for performing cryptographic operations. Ensure you have Python installed on your system (Python 3.6 or newer is recommended).

### Installing Dependencies

Before running the script, you must install the required Python cryptography library. You can install this dependency using pip, Python's package installer. 
Run the following command in your terminal:

<sub>pip install cryptography</sub>

## Usage Instructions
### Setting Up

    1. Ensure Python and pip are installed on your system.
    2. Install the cryptography library using the pip command provided above.
    3. Save the script provided in the previous messages as a .py file, for example, encrypt_decrypt_tool.py.

## Running the Tool

To run the tool, navigate to the directory containing the script using your terminal or command prompt, and then execute the script with Python:

<sub>python encrypt_decrypt_tool.py</sub>

Upon running the script, you will be prompted with the following options:

<sub>Do you want to (E)ncrypt or (D)ecrypt a file?</sub>

    Enter E to encrypt a file. You will then be asked to provide the path to the file you wish to encrypt. After encryption, the encrypted file will be saved in the same directory with an .enc extension, and the encryption key will be displayed. Important: Save this key securely, as you will need it for decryption.

    Enter D to decrypt a file. You will need to provide the path to the encrypted file and the hexadecimal representation of the encryption key. After decryption, the decrypted file will be saved in the same directory, replacing the encrypted one.

## Security Note

The security of your encrypted data is only as secure as the key you use. Keep your encryption key in a safe place. If you lose the key, you will not be able to decrypt your files.

### Limitations
**This tool does not delete the original plaintext file after encryption or the encrypted file after decryption. It's recommended to securely delete these files if they are no longer needed. The encryption key is crucial for decryption. Losing the key means losing access to the encrypted data.**

## Contributing

Contributions to this project are welcome! Please feel free to fork the repository, make your changes, and submit a pull request.
