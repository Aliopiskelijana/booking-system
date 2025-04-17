# GDPR Compliance Checklist – Web-based Booking System

| **Result** | **Personal data mapping and minimization** |
| :----: | :--- |
| ✅ | Have all personal data collected and processed in the system been<br> identified? (e.g., name, email, age, username) |
| ✅ | Have you ensured that only necessary personal data is collected (data minimization)? |
| ✅ *Note 1 | Is user age recorded to verify that the booker is over 15 years old? |

---

| **Result** | **User registration and management** |
| :----: | :--- |
| ⚠️ *Note 2 | Does the registration form (page) include GDPR-compliant consent for processing<br> personal data (e.g., acceptance of the privacy policy)?|
| ❌ *Note 3 | Can users view, edit, and delete their own personal data via their account? |
| ❌ | Is there a mechanism for the administrator to delete a reserver in<br> accordance with the "right to be forgotten"? |
| ✅| Is underage registration (under 15 years) and booking functionality restricted? |

---

| **Result** | **Booking visibility** |
| :----: | :--- |
| ✅ | Are bookings visible to non-logged-in users only at the resource level<br> (without any personal data)? |
| ✅ | Is it ensured that names, emails, or other personal data of bookers are not exposed<br> publicly or to unauthorized users? |

--- 

| **Result** | **Access control and authorization** |
| :----: | :--- |
| ❌ | Have you ensured that only administrators can add, modify, and delete<br> resources and bookings? |
| ❌ *Note 4| Is the system using role-based access control (e.g., reserver vs. administrator)? |
| ⚠️ *Note 5 | Are administrator privileges limited to ensure GDPR compliance (e.g., administrators<br> cannot use data for unauthorized purposes)? |

---

| **Result** | **Privacy by Design Principles** |
| :----: | :--- |
| ✅ | Has Privacy by Default been implemented (e.g., collecting the minimum data by default)? |
| ⚠️ *Note 6 | Are logs implemented without unnecessarily storing personal data? |
| ✅ | Are forms and system components designed with data protection in mind<br> (e.g., secured login, minimal fields)? |

---

| **Result** | **Data security** |
| :----: | :--- |
| ❌ *Note 7 | Are CSRF, XSS, and SQL injection protections implemented? |
| ✅ | Are passwords securely hashed using a strong algorithm (e.g., bcrypt, Argon2)? |
| ❌ | Are data backup and recovery processes GDPR-compliant? |
| ⚠️ *Note 8 | Is personal data stored in data centers located within the EU? |

---

| **Result** | **Data anonymization and pseudonymization** |
| :----: | :--- |
| ❌ *Note 9 | Is personal data anonymized where possible? |
| ❌ *Note 9 | Are pseudonymization techniques used to protect data while maintaining its utility? |

---

| **Result** | **Data subject rights** |
| :----: | :--- |
| ❌ | Can users download or request all personal data related to them (data access request)? |
| ❌ | Is there an interface or process for users to request the deletion of their personal data? |
| ❌ | Can users withdraw their consent for data processing? |

---

| **Result** | **Documentation and communication** |
| :----: | :--- |
| ⚠️ *Note 10 | Is there a privacy policy available to users during registration and easily accessible? |
| ❌ | Are administrators and developers provided with documented data protection practices <br>and processing activities? |
| ❌ | Is there a documented data breach response process (e.g., how to notify authorities <br>and users of a breach)? |

---

**Symbols used:**  
✅ Pass (a note can be added)  
❌ Fail (a note can be added)  
⚠️ Attention (a note can be added)

Note 1: Users under age 15 cannot register

Note 2: The terms of service is included to the form, but its there is no actual privacy policy yet

Note 3: Users can only view their profile via account

Note 4: Roles work in exact same way. The code doesn't make difference between roles

Note 5: +Note4. Administrator has no special rights implemented

Note 6: Logs are not implemented

Note 7: Its possible to inject SQL syntax to database

Note 8: Data is located to personal pc in the development phase

Note 9: Emails are in plain text format in the database

Note 10: There is a easily accessible privacy policy, but privacy policy contains nothing
