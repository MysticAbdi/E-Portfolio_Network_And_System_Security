# Lab 4 - Malicious Software and File Integrity - Lab Notes

## Learning goals

- Understand how file integrity monitoring can reveal tampering or malware.
- Implement a simple baseline and change-detection system using SHA-256 hashes.
- Try a very basic signature-based detection approach.
- Visualise how a worm can spread across hosts in a simple model.

## Activities

1. Created an integrity baseline:

   - Implemented a `create_baseline(root_dir, out_file)` function in the notebook.
   - Walked a `watched_folder` directory recursively.
   - For each file, calculated a SHA-256 hash and stored:
     - the file path
     - the file size
     - the last modification time
     - the SHA-256 hash
   - Wrote this information into a CSV file called `baseline.csv`.

2. Implemented an integrity check:

   - Implemented a `check(root_dir, baseline_file)` function in the notebook.
   - Reloaded `baseline.csv` into a structure keyed by file path.
   - Walked the current directory again and recomputed SHA-256 hashes.
   - Classified changes into:
     - Modified files: present in the baseline, but with a different hash.
     - New files: not present in the baseline.
     - Missing files: present in the baseline, but no longer on disk.
   - Printed a simple report listing each category of change.

3. Added simple signature-based detection:

   - Created a small list of "known-bad" SHA-256 hashes to act as malware signatures.
   - During the integrity check, compared computed hashes against this list.
   - Flagged any matches as potentially malicious.
   - Discussed limitations: an attacker can evade this by changing the file slightly, and the signature list must be maintained and distributed.

4. Worm propagation simulation:

   - Represented each host as a Boolean value in a Python list (`True` = infected).
   - Started with one initially infected host.
   - On each step:
     - Each infected host randomly selected a number of other hosts to scan.
     - Any vulnerable, uninfected hosts found in these scans became infected.
   - Counted and printed the number of infected hosts at each step to see how quickly the infection could spread.

## Key points noted

- Hashes provide a compact fingerprint of a file and are very sensitive to changes.
- Integrity monitoring is conceptually straightforward: compare stored hashes with current hashes and alert on differences.
- For integrity tools to be trustworthy, the baseline and logs must themselves be protected from tampering.
- Signature-based detection is reactive and can be easily evaded, but it is still widely used as one layer in a defence-in-depth strategy.
- Even a simple worm model shows how quickly malware can spread when many vulnerable systems are connected and scan rates are high.
