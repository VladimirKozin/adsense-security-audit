Case Study: AdSense Revenue Anomaly & Security Integrity Audit
📝 Project Overview
Object: A large regional informational portal focused on history, culture, and tourism.

Context: Educational and travel content targeting a broad audience interested in local heritage and attractions.

Tech Stack: WordPress, Nginx, Google AdSense, Google Site Kit.

Incident: The owner reported sharp fluctuations and sudden drops in advertising revenue, raising suspicions of unauthorized access, "Ad Injection," or "Publisher ID" spoofing.

🔍 Investigation Hypotheses
To identify the root cause, I formulated four working hypotheses:

Unauthorized Publisher ID: Modification of the ca-pub ID in the source code to redirect revenue.

Malicious Ad Injection: Unauthorized scripts overlaying legitimate ad blocks or hijacking clicks.

Backdoor / Persistent Malware: CMS-level compromise for dynamic content manipulation.

Market Volatility & Performance Issues: Natural auction fluctuations exacerbated by technical bottlenecks.

🛠 Investigation Steps
Step 1: Publisher ID Forensic Verification
Method: Analyzed the DOM and searched for ca-pub- patterns via DevTools.

Findings: Confirmed the primary ID matches the owner's account.

Discovery: A secondary ID (ca-host-pub) was identified as a legitimate technical component of the Google Site Kit integration.

Verdict: No evidence of ID spoofing or unauthorized revenue redirection.

Step 2: Inventory Authorization Audit (ads.txt)
Method: Requested the /ads.txt file directly from the root directory.

Findings: Only one authorized Publisher ID was listed with DIRECT status.

Verdict: No unauthorized accounts have permissions to sell the site’s ad inventory.

Step 3: Script Integrity & Domain Audit
Method: Audited all external JavaScript calls and network requests.

Findings: All ad-related calls originate from official Google domains (pagead2.googlesyndication.com).

Verdict: No hidden iframes, malicious libraries, or "Malvertising" injections were detected.

Step 4: Core Web Vitals & Performance Diagnosis
Problem: Identified critically low mobile performance scores (18-44/100).

Impact: Largest Contentful Paint (LCP) exceeded 6 seconds.

Correlation: Slow rendering causes ad scripts to initialize after the user has already bounced, leading to massive gaps in recorded impressions and revenue.

📊 Data-Driven Conclusion
The investigation debunked the hacking theory. The revenue "jumps" are attributed to:

Technical Debt: Poor loading speed prevents accurate ad delivery and tracking.

Law of Small Numbers: With ~18.5K views, the daily sample size is too small for stable averages. Revenue is highly sensitive to the CPC (Cost Per Click) of individual visits from high-value regions.

🚀 Skills Demonstrated
Security Auditing: Vulnerability assessment of third-party integrations.

Digital Forensics: Source code analysis and ad-chain verification.

Performance Analysis: Diagnosing Core Web Vitals and their impact on business KPIs.

Incident Response: Structured hypothesis-driven methodology.
