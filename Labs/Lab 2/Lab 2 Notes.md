# Lab 2 - RSA and Secure Messaging - Lab Notes

## Learning goals

- Review the difference between symmetric and asymmetric cryptography.
- Implement a small hybrid encryption demo using RSA and AES.
- Use Python sockets to send encrypted data between a client and a server.
- Understand how correct padding and cipher modes contribute to security.

## Activities

1. Generated an RSA key pair:

   - Used the `cryptography` library to create a 2048-bit RSA private key.
   - Exported the private key to `private_key.pem`.
   - Derived the corresponding public key and saved it to `public_key.pem`.
   - Confirmed that both keys were stored in standard PEM format.

2. Implemented AES encryption helpers:

   - Generated a random 256-bit AES key and a 16-byte IV using secure randomness.
   - Used AES-256 in CFB mode to encrypt and decrypt messages.
   - Implemented `encrypt_message(key, iv, plaintext)` and `decrypt_message(key, iv, ciphertext)`
     functions that worked with bytes and returned the resulting ciphertext or plaintext.

3. Built the client-side hybrid encryption:

   - Prompted the user for a plaintext message.
   - Generated a fresh random AES key and IV for each message.
   - Encrypted the message with AES-256/CFB.
   - Loaded the server’s RSA public key from `public_key.pem`.
   - Encrypted the AES key using RSA with OAEP padding and SHA-256.
   - Packaged `(encrypted_key, iv, encrypted_message)` using `pickle`.
   - Opened a TCP socket, connected to the server, and sent the pickled payload.

4. Implemented the server-side decryption:

   - Loaded the RSA private key from `private_key.pem`.
   - Listened for incoming TCP connections.
   - Received the pickled payload from the client.
   - Unpickled it into `encrypted_key`, `iv`, and `encrypted_message`.
   - Decrypted the AES key using RSA with OAEP and SHA-256.
   - Decrypted the message using AES-256 in CFB mode.
   - Printed out the recovered plaintext message.

5. Observed the result:

   - The client reported that the encrypted message had been sent.
   - The server printed the decrypted message, demonstrating that:
     - The symmetric key stayed secret in transit.
     - Only the holder of the private RSA key could recover the AES key and read the message.

## Key points noted

- RSA is relatively slow and best suited for small pieces of data such as keys, not large messages.
- AES-256 is fast and well suited to encrypting the bulk message data.
- Hybrid encryption (RSA plus AES) is standard in real-world protocols such as TLS.
- OAEP padding and a secure AES mode (CFB in this demo) are crucial; merely "encrypting with RSA or AES" without correct modes and padding can be insecure.
- Using PEM files for key storage makes it easier to separate key management from application logic and mirrors real-world tooling.
- Even in a small demo, it is important to think about not just confidentiality but also future extensions such as message authentication and identity verification.
