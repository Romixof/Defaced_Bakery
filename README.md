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
