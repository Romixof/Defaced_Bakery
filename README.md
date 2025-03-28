# 🕵️‍♂️ Defaced Bakery - Forensic Investigation Challenge

![Banner](https://github.com/hackthebox/public-templates/blob/master/assets/banner.png?raw=true)

**Difficulty**: <span style="color:green">Easy</span>  
**Author**: Sherlock Holmes  
**Last Updated**: March 25, 2024  

## 🔍 Scenario

You're a junior incident responder at CyberSec LLP investigating a website defacement at ByteBakery Inc. The homepage was replaced with "HACKED BY CYBER_COOKIE!". Analyze the logs to:

- Identify the attack vector
- Find attacker persistence mechanisms
- Uncover data exfiltration evidence

## 📁 Provided Artifacts

| File | SHA1 Hash |
|------|-----------|
| `apache_access.log` | `C23A9733638C7D81E4E37644D59A3E394B94CA66` |
| `error.log` | `A1B2C3D4E5F6G7H8I9J0K1L2M3N4O5P6Q7R8S9T0` |
| `file_changes.txt` | `X9Y8Z7W6V5U4T3S2R1Q0P9O8N7M6L5K4J3` |
| `wordpress_users.csv` | `P0O9I8U7Y6T5R4E3W2Q1` |

## 🎯 Investigation Questions

1. What was the attacker's entry point?
2. Which IP successfully authenticated?
3. What password was compromised?
4. Where was the webshell uploaded?
5. Which log file did the attacker attempt to delete?

## 🛠️ Recommended Tools

- **Text Editors**: VS Code, Sublime Text
- **Log Analysis**: `grep`, `awk`, `cut`
- **Hashing**: `sha1sum`, `md5sum`

## 🚀 Getting Started

1. Download the evidence files:
   ```bash
   wget https://example.com/defaced_bakery_artifacts.zip
   unzip defaced_bakery_artifacts.zip
