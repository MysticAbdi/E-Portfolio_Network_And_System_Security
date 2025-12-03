# Lab 3 - Authentication and Access Control - Reflection

This week showed how easy it is to get password storage wrong and why simple hashing is not enough.
Before this lab I knew that "you must not store plaintext passwords", but now I better understand what a safe alternative looks like in code.

Seeing bcrypt in action and noticing how slow it is by design helped me appreciate the trade off between user experience and security.
In a real system I would need to choose a cost factor that is high enough to slow attackers but still acceptable for users.

The TOTP exercise also reinforced the idea that strong authentication is a combination of several factors:
something you know, something you have, and sometimes something you are.
Being able to prototype a minimal 2FA flow in Python makes me more confident that I could integrate a real identity provider or authenticator service later on.
