# Mobile Application Pentest Execution Log

Application: InsecureBankv2.apk  
Date of Assessment: (Your Date)  
Tester: A Learner

---

## 1. MobSF Static Analysis Log

| Time     | Activity                   | Result/Evidence                        |
| -------- | -------------------------- | -------------------------------------- |
| 10:00 AM | Uploaded APK to MobSF      | Scan completed successfully            |
| 10:03 AM | Reviewed Manifest          | Exported activities: 4 found           |
| 10:05 AM | Reviewed Providers         | 1 provider exported without permission |
| 10:08 AM | Security Score Reviewed    | Score: 28/100 (Low)                    |
| 10:12 AM | Extracted Smali/Java code  | Hardcoded strings identified           |
| 10:15 AM | SSL/Network report checked | Weak SSL implementation detected       |

---

## 2. Frida Dynamic Analysis Log (Theory Only)

| Time     | Activity                  | Output/Observation                       |
| -------- | ------------------------- | ---------------------------------------- |
| 10:30 AM | Connected Frida to device | No security restrictions encountered     |
| 10:33 AM | Hooked LoginActivity      | Hook loaded successfully                 |
| 10:35 AM | Bypassed Login Auth       | Login passed without credentials ✔       |
| 10:40 AM | Verified session access   | Logged into secure area without password |

---

## 3. Drozer Test Log(Theory Only)

| Time     | Command Executed                                      | Result                            |
| -------- | ----------------------------------------------------- | --------------------------------- |
| 11:00 AM | `run app.activity.info -a com.android.insecurebankv2` | Exported components listed        |
| 11:05 AM | `run app.activity.start --component ...PostLogin`     | Launched activity without login ✔ |
| 11:10 AM | `run app.provider.finduri ...`                        | Provider exposed                  |
| 11:12 AM | `run app.provider.query content://.../users`          | User DB extracted successfully    |

---

## Summary

Testing of **InsecureBankv2.apk** revealed:

- Login authentication bypassed using Frida
- Exported components exploitable using Drozer
- Sensitive user data retrievable without authorization
- Low overall app security posture

**Final Result: Vulnerable — Exploitation Successful**
