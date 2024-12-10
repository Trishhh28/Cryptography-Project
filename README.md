# **Cryptography Project: Caesar Cipher Implementation**

## **Objective**  
This project demonstrates the use of the **Caesar Cipher**, a fundamental cryptographic technique, to encrypt and decrypt messages. The primary focus is on understanding substitution ciphers, character manipulation, and the basics of cryptography, providing a strong foundation for more advanced encryption methods.

---

### **Skills Learned**  
- Mastery of string manipulation for cryptographic purposes.  
- Understanding the principles of substitution ciphers and their applications.  
- Implementation of modular arithmetic for encryption and decryption.  
- Hands-on experience in Python programming and text processing.  
- Knowledge of key-based encryption and its limitations.  

---

### **Tools Used**  
- **Python** for development.  
- **`string` library** for character sets (uppercase and lowercase alphabets).  
- **Translation tables** (`str.maketrans`) for efficient character substitution.

---

## **Steps**  

### 1. **Set Up the Environment**  
- Installed Python 3.  
- Used the built-in `string` library for character manipulation.

---

### 2. **Implement Caesar Cipher Encryption**  
- Developed the `caesar_encrypt` function.  
- Utilized translation tables to shift characters based on a user-defined key.

---

### 3. **Implement Caesar Cipher Decryption**  
- Designed the `caesar_decrypt` function to reverse the encryption process.  
- Applied modular arithmetic to handle key shifts within the alphabet range.

---

### 4. **Test the Cipher**  
- Inputted a sample message (`"Subscribe To W J Pearce"`) and key (`3`) for demonstration.  
- Verified the encrypted and decrypted outputs matched expectations.

---

### 5. **Enhance Understanding**  
- Explored the strengths and limitations of substitution ciphers in cryptography.  
- Highlighted the importance of key secrecy and its impact on encryption security.
- 
---

## Results  
![cryptography 3](https://github.com/user-attachments/assets/42c30426-4993-4f30-8ce6-bba8e40a331b)

---

## **Example Code**  

```python
import string

# Function for Caesar Cipher encryption
def caesar_encrypt(message, key):
    shift = key % 26
    # Create a translation table for the shift
    cipher = str.maketrans(
        string.ascii_lowercase + string.ascii_uppercase,
        string.ascii_lowercase[shift:] + string.ascii_lowercase[:shift] +
        string.ascii_uppercase[shift:] + string.ascii_uppercase[:shift]
    )
    # Encrypt the message using the translation table
    encrypted_message = message.translate(cipher)
    return encrypted_message

# Function for Caesar Cipher decryption
def caesar_decrypt(message, key):
    shift = 26 - (key % 26)
    # Create a translation table for the reverse shift
    cipher = str.maketrans(
        string.ascii_lowercase + string.ascii_uppercase,
        string.ascii_lowercase[shift:] + string.ascii_lowercase[:shift] +
        string.ascii_uppercase[shift:] + string.ascii_uppercase[:shift]
    )
    # Decrypt the message using the translation table
    decrypted_message = message.translate(cipher)
    return decrypted_message

# Example usage
message = 'I am a Cybersecurity Analyst'
key = 3

# Encrypting the message
encrypted_message = caesar_encrypt(message, key)
print(f'Encrypted message: {encrypted_message}')

# Decrypting the message
decrypted_message = caesar_decrypt(encrypted_message, key)
print(f'Decrypted message: {decrypted_message}')


