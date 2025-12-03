# Lab 2 - RSA and Secure Messaging - Reflection

This lab was the first time I properly combined cryptography with networking code. Seeing a decrypted message appear on the server after travelling over an untrusted network made hybrid encryption feel much more real than any diagram in a textbook.

The main realisation was that secure systems are built from several ideas working together. Public key cryptography is used to exchange secrets, symmetric cryptography handles high-speed data encryption, and a protocol ties them together with the right padding, modes, and message structure. It is not enough to just call an `encrypt()` function and hope for the best; the details matter.

Working directly with RSA keys, AES-256 in CFB mode, and OAEP gave me a much clearer mental model:
- Keys are generated locally and kept safe.
- Public keys can be shared freely.
- Private keys must never leave the owner’s system.
- Random session keys and IVs are used once and then discarded.

This experience will help me in future when I read documentation for cryptographic libraries and protocols. Instead of treating terms like "hybrid encryption", "OAEP", or "session key" as abstract jargon, I can connect them to the code I wrote in this lab. I also gained more respect for why it is risky to design your own protocol; even a simple demo already has many moving parts that must be used correctly to avoid weakening the security guarantees.
