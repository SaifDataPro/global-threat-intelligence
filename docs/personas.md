# SOC Team Personas

## User 1: The SOC Manager
### *The "Strategic Overseer" focused on risk and resources.*

* **Who they are:** Security Operations Center (SOC) Manager.
* **Context:** Leads a team of analysts; responsible for the overall security posture and budget of the organization.
* **Primary Daily Job:** 
  * Monitoring high-level threat trends.
  * Managing team workload.
  * Reporting the organization's "risk level" to leadership (CISO/CTO).
* **Data-Driven Decisions:** 
  * *"Where should I re-allocate my team today? (e.g., Are we seeing a spike in Phishing that requires everyone's attention?)"*
  * *"Which security tools or vendors are actually providing the most value based on the threats we are seeing?"*
* **What Failure Looks Like:** 
  * A major security breach that could have been predicted by trending data.
  * Having a "blind spot" where a known global threat (like a new Ransomware strain) was active in the wild, but the team was completely unaware of it.

---

## User 2: The SOC Analyst
### *The "Tactical Investigator" focused on accuracy and speed.*

* **Who they are:** L1/L2 Security Analyst (Threat Hunter).
* **Context:** The frontline defender who investigates every suspicious alert or "ping" on the network.
* **Primary Daily Job:** 
  * **Triaging alerts:** Analyzing a specific piece of data (an IP, a file, or a URL) to determine: *"Is this a real attack (True Positive) or a mistake (False Positive)?"*
* **Data-Driven Decisions:**
  * *"Is this specific IP address I see in our logs known to be malicious according to AlienVault?"*
  * *"If I block this one domain, what other related infrastructure (other IPs or URLs) do I also need to block to stop the attack completely?"*
* **What Failure Looks Like:** 
  * **Alert Fatigue:** Getting overwhelmed by thousands of lines of data and missing a real "needle in the haystack."
  * **Inefficiency:** Spending 30 minutes manually researching a single IP address while 200 more alerts are waiting in the queue.
