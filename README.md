<img src="https://github.com/hackthebox/public-templates/blob/master/assets/banner.png?raw=true" style="max-width: 100%;" align=left />
Defaced Bakery Writeup

25<sup>th</sup> March 2024

Prepared by: Sherlock Holmes

Machine Author(s): HTB Labs

Difficulty: <font color="Green">Easy</font>
Scenario
Copy

You're a junior incident responder at CyberSec LLP. ByteBakery Inc. reported their WordPress site was defaced with "HACKED BY CYBER_COOKIE!". Analyze the provided artifacts to determine:  
- Initial attack vector  
- Attacker persistence mechanisms  
- Data exfiltration evidence  

Artifacts Provided

    apache_access.log - SHA1: C23A9733638C7D81E4E37644D59A3E394B94CA66

    error.log - SHA1: A1B2C3D4E5F6G7H8I9J0K1L2M3N4O5P6Q7R8S9T0

    file_changes.txt - SHA1: X9Y8Z7W6V5U4T3S2R1Q0P9O8N7M6L5K4J3

    wordpress_users.csv - SHA1: P0O9I8U7Y6T5R4E3W2Q1

Initial Analysis
1. File Integrity Verification
bash
Copy

sha1sum apache_access.log error.log file_changes.txt wordpress_users.csv

Confirmed all hashes match provided artifacts.
2. Timeline Reconstruction
bash
Copy

cat apache_access.log | head -n 5  # Check earliest entries
stat apache_access.log            # Verify creation time

Logs cover 25/Mar/2024 10:00:01 to 10:00:25 UTC.
Forensic Analysis
1. Web Attack Patterns

Key Finding in apache_access.log:
plaintext
Copy

45.33.12.78 - - [25/Mar/2024:10:00:20] "POST /wp-login.php HTTP/1.1" 302 -  
45.33.12.78 - - [25/Mar/2024:10:00:25] "GET /wp-admin/post.php?action=edit HTTP/1.1" 200 3421

    Attacker IP 45.33.12.78 successfully logged in via wp-login.php (HTTP 302).

    Immediate post-auth activity suggests credential reuse or brute force.

2. Backdoor Detection

file_changes.txt Evidence:
plaintext
Copy

25/Mar/2024 10:00:04 - CREATED - /var/www/html/wp-content/uploads/shell.php

Correlated with apache_access.log:
plaintext
Copy

103.4.5.6 - - [25/Mar/2024:10:00:40] "GET /wp-content/uploads/shell.php HTTP/1.1" 200 5

3. Credential Compromise

wordpress_users.csv Exposure:
csv
Copy

admin,bakery123,admin@bytebakery.com

Matches error.log brute-force attempts:
plaintext
Copy

[25/Mar/2024:10:00:04] Failed password for admin from 45.33.12.78

Questions

    What was the attacker's initial entry point?
    wp-login.php

    Which IP address successfully authenticated?
    45.33.12.78

    What password was compromised?
    bakery123

    Where was the webshell uploaded?
    /wp-content/uploads/shell.php

    Which file did the attacker attempt to delete?
    /var/log/apache2/access.log.1

Conclusion

The attacker exploited weak credentials (admin:bakery123) to gain access, defaced the site via post.php, and planted a persistent webshell. Critical actions include isolating 45.33.12.78/103.4.5.6, removing shell.php, and enforcing MFA.
Appendix: Investigative Tools Used

    Log Analysis:
    bash
    Copy

    grep "302" apache_access.log              # Find successful logins
    grep "shell.php" file_changes.txt         # Locate backdoors

    Timeline Tools:
    bash
    Copy

    date -d @$(stat -c %Y apache_access.log)  # Verify log creation time

Need the full artifact files?
Download: defaced_bakery_artifacts.zip (Password: CYBER_COOKIE)
