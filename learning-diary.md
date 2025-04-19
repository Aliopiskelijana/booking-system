# Web Security Vulnerabilities: Practical Exploits and Lessons

## SQL Injection Vulnerabilities

### Exercise 1: Bypassing WHERE Clause Filtering
**Vulnerability**: SQL injection in category filtering
**Exploit Method**: Used `'+or+1=1--'` in the URL parameter to comment out parts of the query
**Attack Result**: Exposed hidden products by manipulating the query to `SELECT * FROM product WHERE category = '' OR 1=1--' AND released = 1`
**Key Lesson**: Never pass URL parameters directly into SQL queries without validation

### Exercise 2: Authentication Bypass
**Vulnerability**: SQL injection in login form
**Exploit Method**: Entered `administrator'--` in the username field
**Attack Result**: Commented out password verification and gained admin access
**Key Lesson**: Parameters must be sanitized before inclusion in authentication queries

## Access Control Vulnerabilities

### Exercise 3: Exposed Admin Functions
**Vulnerability**: Unprotected administrative features
**Exploit Method**: Located admin panel URL in robots.txt
**Attack Result**: Gained full administrative access with no authentication
**Key Lesson**: Sensitive functionality must be protected with proper access controls, not just obscurity

### Exercise 4: Predictable "Hidden" URLs
**Vulnerability**: Admin URL leaked in client-side code
**Exploit Method**: Found admin panel URL in JavaScript code within developer tools
**Attack Result**: Gained access to admin functions through unpredictable but exposed URL
**Key Lesson**: Client-side code should never contain sensitive URLs or access paths

### Exercise 7: Profile Modification Exploit
**Vulnerability**: Insecure user profile update
**Exploit Method**: Added `"roleid": 2` to the JSON body of an email change request
**Attack Result**: Elevated privileges to administrator status
**Key Lesson**: Always validate input parameters and restrict field updates based on user permissions

### Exercise 9: Cookie Manipulation
**Vulnerability**: Role-based authorization via client-controlled cookie
**Exploit Method**: Changed admin cookie value to "true" using browser developer tools
**Attack Result**: Gained administrative privileges
**Key Lesson**: Authorization states should never be controlled by client-side variables

### Exercise 10: Direct Parameter Access
**Vulnerability**: User data accessed via manipulable parameter
**Exploit Method**: Changed URL parameter to `my-account?id=carlos`
**Attack Result**: Accessed another user's API key without authentication
**Key Lesson**: Always verify user identity before serving account data

### Exercise 11: Enumeration via Predictable IDs
**Vulnerability**: User data accessible with discovered ID values
**Exploit Method**: Found user ID from blog post author link, then used in account access
**Attack Result**: Retrieved sensitive API key using harvested ID
**Key Lesson**: IDs should not be the sole protection mechanism for user data

### Exercise 12: Redirect Flaws
**Vulnerability**: Data leakage during redirect
**Exploit Method**: Changed user ID in URL, viewed response before redirect completed
**Attack Result**: Captured API key from response before redirection
**Key Lesson**: Validate authorization before processing any data, not just after

### Exercise 13: Password Exposure
**Vulnerability**: Cleartext password in HTML source
**Exploit Method**: Viewed source of password field after loading administrator profile
**Attack Result**: Retrieved administrator password and gained full access
**Key Lesson**: Never include sensitive data in HTML, even in masked password fields

### Exercise 14: Insecure File References
**Vulnerability**: Direct object reference to protected files
**Exploit Method**: Changed transcript filename in URL to access other user conversations
**Attack Result**: Downloaded conversations containing password information
**Key Lesson**: File access must verify authorization for the specific resource

## Authentication Vulnerabilities

### Exercise 5: Username Enumeration
**Vulnerability**: Different response behaviors for valid vs. invalid usernames
**Exploit Method**: Automated testing of username list, looking for length variations in responses
**Attack Result**: Identified valid username, then bruteforced password
**Key Lesson**: Authentication responses should be consistent regardless of input validity

### Exercise 6: 2FA Bypass
**Vulnerability**: Incomplete two-factor authentication flow
**Exploit Method**: Skipped second authentication step by directly navigating to account URL
**Attack Result**: Bypassed email verification completely
**Key Lesson**: All authentication steps must be validated before granting access

### Exercise 8: Password Reset Weakness
**Vulnerability**: Broken password reset logic
**Exploit Method**: Modified password reset token and username in request
**Attack Result**: Reset another user's password without proper verification
**Key Lesson**: Password reset tokens must be single-use and linked to specific users

## Path Traversal Vulnerabilities

### Exercise 15: Directory Traversal
**Vulnerability**: Inadequate file path validation
**Exploit Method**: Used `../../../../etc/passwd` as filename parameter
**Attack Result**: Accessed system files outside web root directory
**Key Lesson**: Validate file paths and restrict access to specific directories

## Information Disclosure Vulnerabilities

### Exercise 16: Error Message Leakage
**Vulnerability**: Verbose error messages
**Exploit Method**: Triggered error by sending invalid product ID
**Attack Result**: Obtained framework version from error message
**Key Lesson**: Sanitize error messages in production environments

### Exercise 17: Debug Information Exposure
**Vulnerability**: Accessible debug page
**Exploit Method**: Found debug page URL in HTML comments
**Attack Result**: Retrieved SECRET_KEY and technology information
**Key Lesson**: Remove debugging interfaces before production deployment

### Exercise 18: Backup File Discovery
**Vulnerability**: Accessible source code backups
**Exploit Method**: Located backup file reference in robots.txt
**Attack Result**: Accessed database connection code with credentials
**Key Lesson**: Keep source code, backups, and configuration files inaccessible to users

## Vulnerability Category Summary

| Category | Count | Key Mitigation Strategies |
|----------|-------|--------------------------|
| SQL Injection | 2 | Use parameterized queries, ORM frameworks, input validation |
| Access Control | 9 | Implement role-based access control, server-side validation, least privilege principle |
| Authentication | 3 | Multi-factor authentication, consistent responses, secure password management |
| Path Traversal | 1 | Input sanitization, whitelisting allowed paths, directory restrictions |
| Information Disclosure | 3 | Error handling, removal of debug information, secure file management |

## Security Implementation Checklist

- ✅ Validate all user inputs server-side
- ✅ Use parameterized queries for database operations
- ✅ Implement proper access control on all endpoints
- ✅ Store authentication state server-side
- ✅ Sanitize error messages in production
- ✅ Remove debugging interfaces before deployment
- ✅ Restrict file access with proper authorization
- ✅ Implement secure password reset mechanisms
- ✅ Protect all admin functionality with strong authentication
- ✅ Use HTTPS for all communications