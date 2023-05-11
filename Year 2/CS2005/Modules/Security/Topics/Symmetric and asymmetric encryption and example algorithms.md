
# Contents

[Symmetric Encryption](#symmetric%20encryption)
[Asymmetric Encryption](#asymmetric%20encryption)

# Symmetric encryption

- In a symmetric encryption algorithm, the **same key is used to encrypt and to decrypt a message**
- Therefore, key $k$ must be kept secret between the two communicating entities (shared secret)
- Key exchange can take place **directly** between the two parties or via a **trusted third party** (e.g. certificate authority for SSL)

## Examples

- Block ciphers
	- Data-encryption standard (DES) cipher adopted by National Institution of Standards and Technology (NIST)
	- Triple DES
	- Advanced encryption standard (AES)
- Stream ciphers
	- RC4 - Rivest Cipher 4
		- Considered insecure

### Symmetric Encryption over an insecure channel

![symmetric diagram](symmetric.png)


# Asymmetric Encryption

- Also known as public-key encryption
- In an asymmetric encryption algorithm, there are **different encryption and decryption keys**
- For example
	- One who receives encrypted messages generates a pair of private and public keys
	- The **public key** is made available
	- This key can be used by anyone to encrypt messages
	- **Only** the private key holder can decrypt these messages


## Examples

### RSA Algorithm

- The most widely used public-key algorithm, based on the difficulty of the factorisation of the product of two large prime numbers
- A user of RSA creates and then publishes a public key based on two large prime numbers and an auxiliary value
- Anyone can then use the public key to encrypt a message
- The prime numbers **must be kept secret** - if the public key is large enough, only knowing the prime numbers enables decoding the message feasibly
- RSA is a relatively slow algorithm and often used for exchanging encrypted shared keys for symmetric key cryptography