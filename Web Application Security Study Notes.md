**Web Application Security**

1. Explain the difference between a GET and a POST request

In web development, both HTTP GET and POST are methods used to request and send data between a client (usually a web browser) and a server. They serve different purposes and have distinct characteristics:

GET Request:

Purpose: GET requests are used to retrieve data from the server. They are primarily meant for reading information and should not have any significant side effects on the server or data.
Data Handling: Data is appended to the URL as query parameters. For example: https://example.com/page?param1=value1&param2=value2.
Visibility: GET parameters are visible in the URL, which makes them less secure for sensitive information.
Caching: GET requests can be cached by browsers and proxies, making them suitable for idempotent operations (operations that produce the same result regardless of the number of times they're executed).
Bookmarking: GET requests can be bookmarked, as they are part of the URL.

POST Request:

Purpose: POST requests are used to send data to the server to be processed or stored. They are suitable for operations that modify data or have side effects on the server.
Data Handling: Data is sent in the request body, which can include various types of data, such as form data, JSON, XML, etc.
Visibility: POST data is not visible in the URL, making it more secure for sensitive information.
Caching: POST requests are not cached by browsers or proxies by default. They are considered non-idempotent.
Bookmarking: POST requests cannot be bookmarked directly.


2. What is Cross-Site Scripting (XSS), and how can it be mitigated?

Cross site scripting is a security vulnerability commonly found in web applications. It occurs when an attacker is able to inject malicious scripts (usually written in JavaScript) into web pages viewed by other users. When a victim user loads the affected web page, the malicious script is executed in their browser, allowing the attacker to steal sensitive information, manipulate the appearance of the webpage or perform actions on behalf of the user without their consent.

Types of Cross Site Scripting attacks:
- Stored XSS: In this, the malicious script is permanently stored on the target server (for ex. a database). When a user visits the affected page, the script is served from the server and executes in their browser.
- Reflected XSS: Here, the injected script is embedded in a URL and is only served when a victim clicks on a malicious link. 
- Dom-based XSS: This occurs when the attacker modifies the Document Object Model (DOM) of a web page in an unexpected way leading to a security vulnerability.

Exploitation Impacts:
- Session Hijacking: User's session cookies (or nonces or session tokens) can be stolen allowing attackers to impersonate victims and perform actions on their behalf
- Phishing: Malicious scripts can create realistic looking login forms or other fields, tricking users into providing sensitive information. 
- Defacement
- Malware dsitribution: Attackers can redirect users to websites hosting malware, leading to the infection of their systems

Mitigations:
- Input validation : Validate (regex) and sanitize all user inputs, both on the client and server sides to ensure they do not contain executable scripts
- Output encoding: Encode any content provided by users such as form inputs, comments etc. before showing it on web pages. for eg. <script> should be encoded as &lt;script&gt;. Libraries like OWASP's Java Encoder or PHP's htmlentities can be used for this purpose
- Content Security Policy (CSP): Implement CSP headers specifying which resources are allowed to be loaded - this helps prevent xss by disallowing the execution of inline scripts
- HttpOnly and Secure Flags: Set the following on session cookies to prevent JavaScript access and to ensure cookies are only transmitted over HTTPS connections
- Regular Security Audits and Code Reviews for SAST and SCA - identify and fix vulnerabilities in the codebase

3. Explain the concept of SQL Injection. How can developers prevent SQL Injection attacks?
4. What is Cross-Site Request Forgery (CSRF), and how can it be prevented?
5. Describe the difference between authentication and authorization. How can these be implemented securely in web applications?
6. What is HTTPS, and why is it important for web security? How does SSL/TLS work?

7. Explain the Same-Origin Policy (SOP) and its role in web security. How can Cross-Origin Resource Sharing (CORS) be used to relax SOP restrictions?

The Same-Origin Policy (SOP) is a fundamental security concept in web browsers that enforces restrictions on how web pages from different origins (domains) can interact with each other. The goal of SOP is to prevent malicious websites from accessing sensitive data or executing actions on behalf of the user without their consent. This policy plays a crucial role in maintaining web security.

Same-Origin Policy (SOP):

The Same-Origin Policy dictates that a web page served from one origin (domain, protocol, and port) is restricted from accessing data or interacting with resources on a different origin. The policy prevents scenarios like a malicious script on one website stealing data from another website that the user is simultaneously logged into.

SOP rules include:
- Origin Comparison: Two URLs are considered from the same origin if they have the same protocol (http/https), domain, and port.
- Access Restrictions: JavaScript code running in the context of one origin cannot read or modify properties of a document from a different origin. This applies to accessing cookies, local storage, and DOM elements.
- Cross-Origin Requests: XMLHttpRequest and Fetch API requests from JavaScript are subject to SOP, meaning that you cannot make direct requests to resources on a different origin.

Cross-Origin Resource Sharing (CORS):

Cross-Origin Resource Sharing (CORS) is a security feature that allows web servers to specify which origins are permitted to access their resources. It's a mechanism for relaxing the strict restrictions of the Same-Origin Policy in controlled ways.

With CORS, a server can include special HTTP headers in its responses to indicate which origins are allowed to access its resources. This enables a web application running at one origin to request and access resources (such as APIs, fonts, images, or other data) from a different origin. Without proper CORS configuration, browsers would block such requests.

To implement CORS, a server can include specific response headers like:

Access-Control-Allow-Origin: This header specifies which origins are allowed to access the resource. It can be a single origin, "*", or a list of allowed origins.
Access-Control-Allow-Methods: This header specifies the HTTP methods (such as GET, POST, PUT, DELETE) that are permitted for cross-origin requests.
Access-Control-Allow-Headers: This header specifies which HTTP headers can be used during the actual request.
Access-Control-Allow-Credentials: This header indicates whether the browser should include credentials (like cookies) in cross-origin requests.

CORS configuration is done on the server side, and proper setup is essential to prevent unauthorized access to sensitive data while still allowing legitimate cross-origin requests.


8. What is a Web Application Firewall (WAF), and how does it help protect web applications?
9. Describe the concept of Clickjacking and methods to prevent it.


10. How can you secure sensitive data in transit and at rest within a web application?

Securing sensitive data in transit and at rest within a web application is crucial to protect user information and maintain the confidentiality and integrity of the data. Here are best practices for achieving security in both these scenarios:

1. Secure Data in Transit:

When data is transmitted between a user's browser and your web application's server, it's susceptible to interception. To secure data in transit, follow these practices:

- Transport Layer Security (TLS)/Secure Sockets Layer (SSL): Implement TLS/SSL to encrypt data during transmission. This prevents eavesdropping and ensures that data remains confidential. Use HTTPS for all communication between the client and server.
- Use Strong Encryption Protocols: Ensure that your server supports modern and secure encryption protocols like TLS 1.3. Avoid outdated and insecure protocols like SSL.
- Use Strong Cipher Suites: Configure your server to use strong cipher suites to ensure the encryption's integrity and confidentiality.
- HSTS (HTTP Strict Transport Security): Enforce HTTPS usage by setting up HSTS headers, which instruct the browser to always use a secure connection for a specific domain.
- Certificate Management: Properly manage SSL/TLS certificates, keeping them up to date and renewing them before they expire.

2. Secure Data at Rest:

When data is stored on your servers or databases, it needs to be protected against unauthorized access. Here's how to secure data at rest:

- Encryption: Encrypt sensitive data stored in databases. Use strong encryption algorithms and key management practices. Depending on your database system, you might use built-in encryption features or external encryption solutions.
- Key Management: Safeguard encryption keys and manage them using dedicated key management systems. Never store encryption keys alongside the encrypted data.
- Database Security: Implement proper access controls and authentication mechanisms for your database. Regularly update your database software and apply security patches.
- Database Auditing and Monitoring: Implement auditing and monitoring of database activities. This helps you detect and respond to any unauthorized access or suspicious activities.
- Data Redundancy and Backup: Implement regular data backups and store backups securely. Ensure that your backup copies are also encrypted.
- Use Parameterized Queries: When interacting with databases, use parameterized queries or prepared statements to prevent SQL injection attacks.
- Masking and Tokenization: For certain types of sensitive data, consider using data masking or tokenization techniques. These methods replace sensitive data with fake values or tokens, making it difficult for unauthorized users to understand the original data.

11. Discuss the importance of input validation and output encoding in web security. Provide examples of how inadequate validation and encoding can lead to vulnerabilities.


**ML and LLM Security Resources**

1. Stanford Course on Language Models: https://stanford-cs324.github.io/winter2022/lectures/introduction/
2. Threat modelling LLM applications: http://aivillage.org/large%20language%20models/threat-modeling-llm/
3. OWASP Top 10 for LLM Applications: https://www.llmtop10.com/assets/downloads/OWASP-Top-10-for-LLM-Applications-v101.pdf


