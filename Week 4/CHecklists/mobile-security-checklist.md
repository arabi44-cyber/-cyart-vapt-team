# Mobile Application Penetration Testing Checklist

Target Application: InsecureBankv2.apk  
Tools Used: MobSF, Frida, Drozer  
Platform: Android

---

## 1. Environment Setup

- [✓] Install MobSF in Kali
- [✓] Setup Android emulator/Genymotion/AVD
- [✓] Enable APK installation & debugging
- [✓] Prepared Frida + Python environment
- [✓] Installed Drozer & dependencies

---

## 2. Static Analysis (MobSF)

- [✓] Uploaded **InsecureBankv2.apk**
- [✓] Verified application metadata (Package, SDK, Permissions)
- [✓] Checked exported activities/services/providers
- [✓] Reviewed manifest for insecure configurations
- [✓] Analyzed code for hardcoded credentials
- [✓] Identified SSL & network security issues
- [✓] Checked for trackers and permissions
- [✓] Downloaded Java/Smali for manual review

---

## 3. Dynamic Testing (Frida)

- [x] Setup Frida server & connect to device
- [x] Loaded Frida hooking script
- [x] Intercepted functions runtime
- [x] Bypassed login authentication successfully
- [x] Confirmed insecure logic flow & lack of tamper protection

---

## 4. Drozer Component Testing

- [x] Confirmed exported activities accessible
- [x] Launched internal activity without login
- [x] Enumerated content providers
- [x] Extracted user database via provider
- [x] IPC exposed — unauthorized component access

---

## 5. Result Documentation

- [✓] Created detailed vulnerability report
- [✓] Added screenshots & evidence
- [✓] Added security rating & risk analysis
- [✓] Added mitigation & recommendation section

---

## Final Status

**Testing Completed Successfully**  
Major vulnerabilities found: Exported components, authentication bypass, data leakage, insecure design
