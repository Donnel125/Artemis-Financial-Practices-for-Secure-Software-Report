# Artemis-Financial-Practices-for-Secure-Software-Report
Project Overview
For CS 305, I worked with a Java Spring Boot application for Artemis Financial, a financial services client seeking stronger software security. My work involved examining third-party dependency risks and modifying the application to support encrypted communication and a SHA-256 hashing demonstration.
Reflection
1. Client and software requirements
Artemis Financial needed to reduce risks to its application and the information it handles. The project called for a vulnerability assessment and security improvements, including HTTPS and a checksum generated with SHA-256.
2. Strengths of the vulnerability assessment and the value of secure coding
I used OWASP Dependency-Check to identify known vulnerabilities in the application's libraries and reviewed the findings rather than assuming that working code was automatically safe. Secure coding is important because it helps protect sensitive information, maintain customer confidence, and reduce the chance of service interruptions and costly security incidents.
3. Most challenging or helpful part
The most helpful part was seeing how dependencies could introduce risks even when the application's own features appeared to work. The challenging part was interpreting scan results: a flagged component requires investigation to determine whether the vulnerability applies, how serious it is, and what updates or other mitigations are appropriate.
4. Security layers and future assessment methods
I configured the application to use HTTPS on port 8443 with a PKCS12 keystore and an environment variable for the keystore password. I also added a /hash endpoint that calculates a SHA-256 digest for a fixed sample string. HTTPS protects network traffic in transit; the digest demonstrates a way to detect changes when compared with a trusted expected value. A plain hash by itself does not prove who supplied the data. In future projects, I would use dependency scans, code review, static analysis, and vendor advisories to select mitigations based on severity, exposure, and compatibility.
5. Functional and security verification
After refactoring, I checked the Spring Boot startup output to confirm that the HTTPS server started and tested the hashing endpoint. I also reran the dependency assessment to review known issues in the libraries. The scan still reported vulnerable components, so successful execution did not mean the application was fully secure. Before production use, I would update affected dependencies where feasible and repeat both functional and security tests.
6. Resources, tools, and practices for future work
This project gave me experience with Java, Spring Boot, Maven, OWASP Dependency-Check, Java MessageDigest, keytool, TLS configuration, and environment variables. I would carry forward the practice of making focused changes, checking application behavior afterward, and documenting unresolved risks.
7. What I would show future employers
I would share my completed Artemis Financial Practices for Secure Software Report as evidence that I can assess software risks, implement security controls, and explain the results of testing. I could also discuss the Java changes and how I distinguished a working application from one with outstanding security findings.

Security Note:
This project was configured for local development and is not presented as production-ready. The local certificate and its private key should not be published. Do not commit .p12 keystores, passwords, or other secrets. The dependency findings also require further remediation before production deployment.
