# Lab 6 - Static Binary Analysis - Reflection

Static analysis felt less intimidating once I broke it down into small, repeatable steps like hashing, string extraction, and header inspection. Seeing each of these steps implemented in the notebook made it clear that you do not need a full reverse-engineering toolkit to learn something useful about an unknown executable.

The combination of imports and strings was particularly interesting. When I saw network-related APIs together with suspicious domain names or URLs in the strings, it immediately suggested possible behaviours, such as beaconing to a command-and-control server. At the same time, the lab reinforced the need to be cautious: static clues can be incomplete or misleading, especially if the binary uses obfuscation or encryption.

The brief YARA exercise also gave me a sense of how malware analysts scale their work. Instead of manually inspecting every file, they can write rules that capture patterns and run them across large collections of binaries or on live systems.

Going forward, I can use these techniques as a first pass whenever I encounter an unknown executable. Even if I never become a full-time malware analyst, being able to run basic static triage is a valuable skill in many security roles, from incident response to threat hunting and even secure software development.
