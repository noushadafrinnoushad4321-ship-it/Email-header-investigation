**# Email-header-investigation**
A detailed analysis of a phishing email sample as part of a cybersecurity internship task. This project includes header analysis, SPF/DKIM/DMARC verification, link inspection, and identification of phishing indicators using MXToolbox and manual examination.

**1. Phishing Email Sample**

A publicly available phishing email sample (SBI-themed) was used for analysis.
This email claims that the recipient’s bank account has been temporarily locked and urges immediate verification.

**Email Body (Simplified)**

Subject: Urgent: Your Account Has Been Temporarily Locked

Dear Customer,
We detected unusual login activity on your SBI NetBanking account.
Please verify to restore access.

Click here to Verify Now:
https://sbi.verify-secure-login247.com/update

Failure to verify within 24 hours will result in permanent suspension.
Attachment: SBI_Account_Verification_Form.htm

**🧪 2. Tools Used**

MXToolbox Header Analyzer

Email header (text format) from the phishing sample

**🧵 3. Header Analysis Results (from MXToolbox)**
📌 DMARC
Status: No DMARC Record Found
dmarc = fail (p=reject)

📌 SPF
Received-SPF: fail
Domain does not designate 185.203.112.55 as a permitted sender

📌 DKIM
dkim = none (no signature)
No aligned DKIM-Signature header found

📌 Sender Details
Return-Path: alerts@sbi-secureverify.com
From: SBI Online <alerts@sbi-secureverify.com>

📌 Server & Routing
Received from: unknown (185.203.112.55)
By: smtp.gmail.com (ESMTPS)

📌 Link & Attachment

Link: https://sbi.verify-secure-login247.com/update

Attachment: SBI_Account_Verification_Form.htm

**🚨 4. Phishing Indicators Identified**
🔴 1. Spoofed Sender Address

The email claims to be from SBI, but the domain used is:
sbi-secureverify.com   (FAKE domain)

Legitimate SBI emails use:
sbi.co.in

🔴 2. SPF Authentication Failed

The sending server IP:
185.203.112.55
is NOT allowed to send emails for the domain:
sbi-secureverify.com
This indicates sender spoofing.

🔴 3. No DKIM Signature

There is no DKIM-Signature header, meaning the email has no cryptographic proof that it was sent by a legitimate server.

🔴 4. DMARC Failed

DMARC = fail, indicating the domain owner has not published protection records.
Attackers can easily impersonate this domain.

🔴 5. Suspicious URL

The verification link points to:

sbi.verify-secure-login247.com/update
This domain is not related to SBI and is designed to steal credentials.

.

🔴 6. Urgent / Threatening Language

“Your account has been temporarily locked”

“Verify within 24 hours”

“Permanent suspension”

These are classic phishing pressure tactics.

🔴 7. Dangerous Attachment

Attachment:

SBI_Account_Verification_Form.htm


HTML attachments are commonly used to:

Steal login credentials

Load malicious scripts

🔴 8. Technical Header Discrepancy

The email was sent from a server identified only as:

HELO mail.sbi-secureverify.com (unknown)


Not an official banking server.

**🛡️ 5. Conclusion**

This email is confirmed to be a phishing attempt.

✔ Indicators of compromise:

Spoofed email address

SPF/DKIM/DMARC failures

Fake domain

Malicious link

Threatening language

Suspicious attachment

Final Assessment: HIGH-RISK PHISHING

The attacker’s intent is to steal SBI NetBanking credentials.

**6.Screenshots**

<img width="1899" height="786" alt="image" src="https://github.com/user-attachments/assets/afacc007-98f1-434f-ad8b-d9f92f79981e" />

<img width="1844" height="771" alt="image" src="https://github.com/user-attachments/assets/b301d20e-04e0-4e23-9cd9-97a3f6b50c12" />


