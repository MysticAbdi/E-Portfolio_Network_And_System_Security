# Lab 3 - Authentication and Access Control - Lab Notes

## Learning goals

- Understand what makes passwords weak or strong.
- Practice hashing passwords safely with bcrypt, including the idea of salt and pepper.
- Add a simple form of two factor authentication using TOTP codes.

## Activities

1. Wrote a password strength function:

   - Checked length thresholds at 8 and 12 characters.
   - Checked whether lower case, upper case, digits, and special characters were used.
   - Estimated entropy in bits using `entropy = length * log2(pool_size)`.
   - Flagged obviously bad choices like "password" and "123456".

2. Experimented with different passwords:

   - Tested short simple passwords and saw that they scored low and had low entropy.
   - Tried long passphrases and saw higher scores and much higher entropy.

3. Implemented password hashing with bcrypt:

   - Used an application wide secret pepper that is prepended to the password.
   - Used `bcrypt.gensalt()` so that each hash gets a unique salt automatically.
   - Implemented `hash_password()` and `verify_password()` helper functions.
   - Observed that the salt is stored as part of the bcrypt hash string.

4. Added TOTP based two factor authentication:

   - Generated a random base32 TOTP secret with `pyotp.random_base32()`.
   - Used `pyotp.TOTP(secret)` to create a TOTP object.
   - Simulated a registration step where the secret would be added to an authenticator app.
   - In a login simulation, first verified the password hash, then asked the user for the 6 digit TOTP code and verified it.

## Key points noted

- Passwords should ideally be long and unpredictable, and users need help to choose good ones.
- Hashing passwords with a slow algorithm limits the speed of offline guessing.
- Salts prevent the use of precomputed rainbow tables and ensure that equal passwords have different hashes.
- A pepper adds another layer of defense if the database is leaked but the application secret is kept safe.
- Two factor authentication adds a second barrier even if a password is compromised.
