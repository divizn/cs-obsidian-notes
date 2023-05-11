
> The science or study of the techniques of secret writing; especially code and cipher systems; methods; and the like.

# Cryptography terms

## Encryption

- The process of encoding a message in a way that the information can not be accessed by unauthorised parties

## Decryption

- Is the process of decoding a message using a key

## Cipher (or cypher)

- An algorithm used to perform encryption/decryption (e.g. Caesar Cypher)

## Plaintext

- Original message (unencrypted)

## Ciphertext

- Coded message (encrypted)

### Cryptosystem (or cipher system)

- Is a set of algorithms for performing cryptography actions (e.g. encryption, decryption, key generation)

## Cryptanalysis

- The study of how to crack encryption algorithms


# Why do we need Cryptography?

- In a computer
	- Source and destination of messaged can be known and protected
- In a network of computers
	- No immediate and reliable way of determining the sender (machine or process) or the receiver
	- No way of knowing if there is an eavesdropper
- In a network, IP addresses are used to identify senders and receivers of messages
	- e.g. a request message arrived with a source IP address; a response message is sent to this IP address
- IP addresses can be spoofed
	- Cannot reliably determine who has sent the request
	- Cannot reliably determine who will receive the response
- If source IP addresses can not be trusted, how can an operating system:
	- Decide whether to grant a request
	- Provide protection for a request or data when it cannot determine who will receive the response