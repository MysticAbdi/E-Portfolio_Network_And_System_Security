# Lab 5 - Web Security and Wapiti - Lab Notes

## Learning goals

- Get hands on experience with a web vulnerability scanner.
- Understand what it means to do black box testing of a web application.
- Learn how to read an automated vulnerability report.

## Activities

1. Prepared a target:

   - Used a deliberately vulnerable training application such as Google Gruyere or OWASP Juice Shop.
   - Ensured it was running in a controlled environment where scanning is allowed.

2. Ran Wapiti from the command line:

   - Used a command similar to:

     ```bash
     wapiti -u https://example-test-app/ -o gruyere_scan -f html
     ```

   - Wapiti crawled the target application, discovered input points, and sent test payloads for issues like XSS and SQL injection.
   - The tool generated an HTML report in the specified output directory.

3. Opened the report with a helper function:

   - Used a small Python helper that opens the `index.html` report file in a browser.
   - Navigated through the sections that list vulnerabilities and the HTTP requests that triggered them.

4. Reviewed some of the findings:

   - Looked at example reflected XSS findings and noted which parameters were not properly filtered.
   - Compared different severity levels reported by the tool.
   - Discussed which findings would need manual verification.

## Key points noted

- Black box scanning treats the web app as an opaque target and does not require source code.
- Automated scanners are good at coverage but can generate false positives or miss logic flaws.
- The report is the start of the manual testing process, not the final answer.
