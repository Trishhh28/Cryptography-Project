# Cryptography Project

## Objective

This project aims to develop a Python-based application to demonstrate fundamental cryptography principles. The application focuses on encrypting, decrypting, and securing data using various cryptographic algorithms. The primary goal is to enhance understanding of encryption techniques, secure key management, and data confidentiality.

### Skills Learned

- Proficiency in Python's cryptography libraries (e.g., `cryptography`, `PyCrypto`).
- Understanding of symmetric and asymmetric encryption methods.
- Hands-on experience with hashing techniques and digital signatures.
- Knowledge of secure key management and implementation best practices.
- Ability to design secure applications and protect sensitive information.

### Tools Used

- Python 3 for development.
- Libraries:
  - `cryptography` for encryption and decryption.
  - `hashlib` for hashing algorithms (e.g., SHA-256).
  - `os` and `secrets` for secure random number generation.
- Jupyter Notebook for testing and documenting the project.

---

## Steps

1. **Set Up the Environment:**
   - Installed Python 3 and required libraries (`cryptography`, `hashlib`, etc.).
   - Created a virtual environment to manage dependencies.

2. **Implement Symmetric Encryption:**
   - Used AES (Advanced Encryption Standard) to encrypt and decrypt data.
   - Implemented secure key storage and management.

3. **Implement Asymmetric Encryption:**
   - Used RSA (Rivest-Shamir-Adleman) for public/private key encryption.
   - Created digital signatures for verifying message integrity.

4. **Hashing and Integrity Checks:**
   - Used `hashlib` to generate and verify SHA-256 hashes.
   - Developed a file integrity checker to identify tampered files.

5. **Generate Secure Keys:**
   - Used the `secrets` library for generating cryptographically secure keys.
   - Implemented a password-based key derivation function (PBKDF2) for user-provided keys.

6. **Test Encryption and Decryption:**
   - Encrypted and decrypted text files and images to validate functionality.
   - Simulated secure message exchange using both symmetric and asymmetric encryption.

7. **Create a CLI Tool:**
   - Developed a command-line interface for users to select encryption modes, input data, and retrieve results.

8. **Documentation and Examples:**
   - Documented use cases, algorithms, and examples in a README file.
   - Provided sample scripts for common cryptographic operations.

---

## Example Code

Here’s a snippet showcasing AES encryption:

```python
from cryptography.hazmat.primitives.ciphers import Cipher, algorithms, modes
from cryptography.hazmat.primitives import padding
from cryptography.hazmat.backends import default_backend
import os

# Generate a random key and IV
key = os.urandom(32)  # AES-256
iv = os.urandom(16)

# Encrypt the data
def encrypt_data(data, key, iv):
    padder = padding.PKCS7(128).padder()
    padded_data = padder.update(data) + padder.finalize()
    cipher = Cipher(algorithms.AES(key), modes.CBC(iv), backend=default_backend())
    encryptor = cipher.encryptor()
    ciphertext = encryptor.update(padded_data) + encryptor.finalize()
    return ciphertext

# Example usage
plaintext = b"Sensitive information"
ciphertext = encrypt_data(plaintext, key, iv)
print(f"Ciphertext: {ciphertext}")