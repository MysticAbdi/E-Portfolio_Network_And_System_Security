# Lab 4 - Malicious Software and File Integrity - Reflection

Implementing the integrity monitoring functions made the idea of file integrity monitoring much more concrete. Instead of seeing it as a mysterious security feature, I now understand it as a straightforward process of walking a directory, hashing files, and comparing those hashes to a stored baseline.

Writing the baseline and check logic myself also highlighted the limits of such tools. If an attacker can modify both the files and the baseline or log files, then the monitoring can be bypassed. That means the integrity system itself needs protection, such as secure storage, restricted permissions, or even hardware-backed trust anchors.

The worm simulation was surprisingly powerful despite being just a few lines of Python. Once the number of scans per step increased, the infection counts grew very quickly. This helped me understand why patch management, network segmentation, and rate limiting are so important in real networks. It is easy to underestimate how fast malware can propagate when many vulnerable systems are reachable.

Overall, this lab connected theoretical discussions about malware spreading and file integrity monitoring to practical mechanisms. I now have a better feel for what tools like Tripwire or host intrusion detection systems are doing under the hood, and I am more aware of both their strengths and their blind spots.
