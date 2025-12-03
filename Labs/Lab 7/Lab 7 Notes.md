# Lab 7 - Penetration Testing Basics - Lab Notes

## Learning goals

- Practice early stages of a penetration test in a safe environment.
- Use Python to perform simple recon, HTTP header analysis, and port scanning.
- Understand ethical and legal boundaries around active scanning.

## Activities

1. Domain and IP reconnaissance:

   - Used `socket.gethostbyname` to resolve a domain name to an IP address.
   - Queried a public IP information service to see organisation, city, and country.
   - Only used domains that are allowed to be tested.

2. HTTP header reconnaissance:

   - Sent HTTP HEAD requests to a target URL with the `requests` library.
   - Printed the status code and response headers.
   - Looked for:
     - `Server` header and any version information,
     - security related headers like `X-Frame-Options`, `Content-Security-Policy`, or `Strict-Transport-Security`.

3. Simple port scanning:

   - Implemented a TCP connect scanner that tries to open a connection to a list of ports.
   - Marked ports as "open" when `connect_ex` returned zero.
   - Tested against `localhost` and other permitted test targets.
   - Talked about how this relates to tools like Nmap that do this at scale.

4. Ethics and scope:

   - Reviewed the idea of obtaining explicit permission before scanning.
   - Discussed the difference between legitimate testing and unauthorised probing.

## Key points noted

- Reconnaissance can reveal a lot of information before any exploits are attempted.
- Open ports and server banners are starting points for deeper investigation.
- It is easy to cross ethical boundaries with scanning tools, so strict respect for rules and scope is essential.
