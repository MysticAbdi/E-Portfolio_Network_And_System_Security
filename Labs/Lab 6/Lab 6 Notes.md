# Lab 6 - Static Binary Analysis - Lab Notes

## Learning goals

- Carry out safe static analysis on Windows PE executables.
- Use hashes as indicators of compromise.
- Extract printable strings to get quick hints about binary behaviour.
- Inspect PE header fields and imports.
- Use simple YARA rules to match suspicious patterns.

## Activities

1. Hashing a binary:

   - Implemented a `compute_hash(path, algorithm)` helper function in the notebook.
   - Calculated MD5, SHA-1, and SHA-256 hashes for a chosen executable.
   - Noted that these hashes can be shared as indicators of compromise (IOCs) with security teams or threat intelligence feeds.
   - Discussed the risk of hash collisions for weaker algorithms like MD5 and why SHA-256 is preferred.

2. Extracting strings:

   - Implemented an `extract_strings(path, min_length=4)` function to scan the binary for sequences of printable ASCII characters.
   - Ran it against the sample executable to list strings such as:
     - File paths.
     - Domain names or URLs.
     - Error messages and debug text.
   - Used these strings to infer possible behaviour (for example, network communication or file system access).

3. Inspecting PE structure and imports:

   - Used the `pefile` library to parse the PE header.
   - Looked at key fields such as:
     - Entry point.
     - Section names and sizes.
   - Examined the import table to see which DLLs and APIs the binary relies on.
   - Paid attention to suspicious imports such as:
     - Networking APIs like `Wininet` or `Ws2_32`.
     - Process or memory manipulation APIs.

4. YARA rule matching:

   - Wrote a small YARA rule in the notebook as a string describing simple string or hex patterns.
   - Compiled it with `yara.compile(source=...)`.
   - Ran `rules.match(sample_path)` to see whether the sample matched the rule.
   - Discussed how, in practice, YARA rules are used to flag malware families or specific behaviours across many files.

## Key points noted

- Static analysis can reveal a lot about a binary without executing it, which makes it safer for initial triage.
- Hashes are useful identifiers for known files but are fragile: any change to the file produces a different hash.
- Extracted strings and imported APIs give quick, cheap hints about what a program might be doing.
- YARA provides a flexible way to express patterns that can identify suspicious or known-bad files.
- Static analysis has limitations and should be combined with dynamic analysis for a fuller understanding of behaviour.
