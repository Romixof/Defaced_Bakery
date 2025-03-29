# 🕵️‍♂️ Defaced Bakery - Forensic Investigation Challenge

![Banner](https://github.com/hackthebox/public-templates/blob/master/assets/banner.png?raw=true)

**Difficulty**: <span style="color:green">Easy</span>  
**Author**: Romix0ff  
**Last Updated**: March 25, 2024  

## 🔍 Scenario

You're a junior incident responder at CyberSec LLP investigating a website defacement at ByteBakery Inc. The homepage was replaced with "HACKED BY CYBER_COOKIE!". Analyze the logs to:

- Identify the attack vector
- Find attacker persistence mechanisms
- Uncover data exfiltration evidence

## 📁 Provided Artifacts

| File | SHA1 Hash |
|------|-----------|
| `apache_access.log` | `CD300E83FEC3367EAD9716BAC72D237FA7893DC9` |
| `error.log` | `9E820806C3E0A622B38D874A995B9261B9DED426` |
| `file_changes.txt` | `270FC7422D788EBD74FAD2AA08ED22396264125B` |
| `wordpress_users.csv` | `2E809A45F690D1FFBA95EFF371884A8E1A3F0312` |

## 🎯 Investigation Questions

    1. First malicious IP in the logs?

    2. Username used in brute-force attack?

    3. Password found in the leaked database?

    4. HTTP status code of successful admin login?

    5. Full path of the uploaded webshell?

    6. Command used to wipe logs?

    7. Database table dumped (from error.log)?

    8. Filename of the stolen backup?

    9. Modified config file (from file_changes.txt)?
    
    10. Parent process of the webshell (from error.log)?
    

## 🛠️ Recommended Tools

- **Text Editors**: VS Code, Sublime Text
- **Log Analysis**: `grep`, `awk`, `cut`
- **Hashing**: `sha1sum`, `md5sum`

## 🚀 Getting Started

1. Download the evidence files:
   ```
   git clone https://github.com/Romixof/Defaced_Bakery
   unzip Defaced_Bakery_Sherlock.zip
