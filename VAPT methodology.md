## Web Application Vulnerability Assessment and Penetration Testing Management Methodology Simplified (Web-VAPT-MMS)

1. [Introduction](https://github.com/gh1mau/vapt/blob/main/VAPT%20methodology.md#introduction)

2. [VA Scanning Tools](https://github.com/gh1mau/vapt/blob/main/VAPT%20methodology.md#va-scanning-tools)

3. [Methodology](https://github.com/gh1mau/vapt/blob/main/VAPT%20methodology.md#methodology)

4. [BlackBox Scanning Phase](https://github.com/gh1mau/vapt/blob/main/VAPT%20methodology.md#blackbox-scanning-phase)

5. [Massaging Phase (BlackBox Findings)](https://github.com/gh1mau/vapt/blob/main/VAPT%20methodology.md#massaging-phase-blackbox-findings)

6. PoC Phase 1 (BlackBox Findings)

7. 

---

### Introduction

> A **Vulnerability Assessment** provides organizations with the <u>knowledge, awareness, and risk background necessary to understand threats to their environment and react accordingly</u>.
> 
> A **Penetration test (Pen-Test)** <u>attempts to exploit the vulnerabilities identified during Vulnerability Assessment to determine whether unauthorized access or other malicious activity is possible</u>.
> 
> As part of Vulnerability Assessment and Penetration Testing, a detailed analysis on the current architecture, internal security of system components and identify all vulnerabilities by using a phased approach to ensure that malicious intruders do not gain the access to critical assets stored, processed or transmitted should be conducted

To simplify the definitions:

![](https://raw.githubusercontent.com/gh1mau/vapt/main/image/VAPT%20Intro.png)

| Assessment               | Descriptions                                                                                                                                                                                                                                                                                                             |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Vulnerability Assessment | Automated Scanning your assets to find potential, possible known vulnerabilities and take proper security measures accordingly.                                                                                                                                                                                          |
| Penetration Test         | Based on the Vulnerability Assessment findings, we need to provide **Proof of Concept** to simulate the possible attempts of **exploit** that could happen, we also could identify **false positive**, **false negative**, **true positive** and **true negative** issues based on the Vulnerability Assessment findings |

To make things simpler yet comprehensive, I'll share the **Web Application Vulnerability Assessment and Penetration Testing Management Methodology Simplified** that I used for VAPT Assessements on common Web Applications.

The assessment would be divided into two(2) main approach:

| #   | Assessment | Approach            |
|:---:| ---------- | ------------------- |
| 1   | BlackBox   | Without credentials |
| 2   | WhiteBox   | With credentials    |

<u>The VAPT assessment flow diagram:</u>

![](https://raw.githubusercontent.com/gh1mau/vapt/main/image/VAPT%20testing.png)

| Assessment       | Descriptions                                                                                                                                                                                                                                                                                                            |
| ---------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| BlackBox Testing | VAPT assessement is conducted **without any knowledge** of the  Web Application's credential(s)                                                                                                                                                                                                                         |
| WhiteBox Testing | VAPT assessment is conducted **with the knowledge** of the Web Application's credential(s). The credentials are either found during the BlackBox testing or given by the client.<br/><br/>We will be using the lowest privillege user for testing, trying to escalate the privilege and do more 'damage' to the target. |

<sub>[toc](https://github.com/gh1mau/vapt/blob/main/VAPT%20methodology.md#web-application-vulnerability-assessment-and-penetration-testing-management-methodology-simplified-web-vapt-mms)</sub>

---

### VA Scanning Tools

There a many tools that can be use to accomplish this assessment, both commercial or open source tools. For this **Simplified Methodology** I am going to suggest and use the following:

| Tools             | Focus                | BlackBox | WhiteBox |
| ----------------- | -------------------- |:--------:|:--------:|
| Nessus Essentials | OS / Host Assessment | Yes      | Yes      |
| Nikto             | Web Application      | Yes      | No       |
| Arachni           | Web Application      | Yes      | Yes      |
| OWASP ZAP         | Web Application      | Yes      | Yes      |

<sub>Note : Arachni development has stopped and they are going commercial soon :(</sub>

<sub>[toc](https://github.com/gh1mau/vapt/blob/main/VAPT%20methodology.md#web-application-vulnerability-assessment-and-penetration-testing-management-methodology-simplified-web-vapt-mms)</sub>

---

### 

### Methodology

Following diagram shows the **General Overview** for Web Application Vulnerability Assessment and Penetration Testing Management Methodology Simplified (**Web-VAPT-MMS**)

![](https://raw.githubusercontent.com/gh1mau/vapt/main/image/VAPT%20methodology.png)

We will discuss briefly every phase involves in Web-VAPT-MMS and will go deeper in later sections.

| Scanning Phase                                                                                                                                                                                                                                                                           |
|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| This phase will cover both the **BlackBox** and **WhiteBox** assessments using the tools mentioned in the [VA Scanning Tools](https://github.com/gh1mau/vapt/blob/main/VAPT%20methodology.md#va-scanning-tools) section. Later we'll need to import the report/result to the next phase. |

| Massaging Phase                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| In this phase we will be using defectDojo ([defectDojo docker setup (ubuntu 18.04](https://github.com/gh1mau/vapt/blob/main/defectDojo.md#defectdojo-docker-setup-ubuntu-1804)) as our VAPT Management Platform.  Several processes involves in this phase:<br/>    - Import Findings from VA SCanning Tools<br/>    - Integrations and Merging the findings to defectDojo<br/>    - Verifications and analysis of findings, false positive indentifications<br/>    - Vulnerabilty Assessment Reporting<br/>    - Security Metrics |

| PoC Phase                                                                                                                                                                                                                                                                                                              |
|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| In this phase we will do the actual exploit, trying to dig and poke as deep as we can to compromise the system/target, findings from this phase will be presented in the Penetration Testing report. We will be using multiple exploitation tools, exploit code accordingly based on the Massaging Phase reports/data. |

| Reporting Phase                                                                                                                                                                                                                                                                |
|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| The last phase of the Web-VAPT-MMS first cycle. We will be using pwndoc ([pwndoc docker setup (ubuntu 18.04](https://github.com/gh1mau/vapt/blob/main/pwndoc.md)) for Penetration Testing report generator. We may need to start over the whole process for re-test if needed. |

At the end, the output of the Web-VAPT-MMS process will produce two(2) reports:

1. Vulnerability Assessment Report (**defectDojo**)

2. Penetration Testing Report (**pwndoc**)

<sub>[toc](https://github.com/gh1mau/vapt/blob/main/VAPT%20methodology.md#web-application-vulnerability-assessment-and-penetration-testing-management-methodology-simplified-web-vapt-mms)</sub>

---

### BlackBox Scanning Phase

As mentioned earlier, BlackBox Scanning in **Web-VAPT-MMS** context means as simple as scanning targets without credentials, put in your target ip/url and hit the scan button and buy your self a good cup of coffee. To save time, we might run the scanners simultaneously. 

The objective of this phase would be:

1. Perform common Vulnerability Scanning against target

2. Saving the results, later will import to defectDojo

During the Massaging Phase later, we will correlate and analyze the findings/scanning results to find potential entry point(s) to exploit.

![](https://raw.githubusercontent.com/gh1mau/vapt/main/image/blackbox_scanning_phase.png)

While here is the basic steps to BlackBox Scanning

| Nessus                                                                                                                                                                                         |
|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Run **nessus scan** to the target without providing any credentials.<br/><br/>![](https://raw.githubusercontent.com/gh1mau/vapt/main/image/nessus_blackbox_1.PNG)                              |
| Save the report in **CSV** with the following naming format:<br/>`nessus_<target>_dd-mm-yyyy.csv`<br/><br/>![](https://raw.githubusercontent.com/gh1mau/vapt/main/image/nessus_blackbox_2.PNG) |

| Nikto                                                                                                                                                                                                                                                                      |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Run nikto and save **xml** result. You can refer [Setup Nikto in Ubuntu 18.04](https://github.com/gh1mau/vapt/blob/main/nikto.md#setup-nikto-in-ubuntu-1804) for setup and cheat sheet.<br/><br/>`./nikto.pl -h target -maxtime 3600s -o nikto_target_dd-mm-yyyy.xml`<br/> |
| ![](https://raw.githubusercontent.com/gh1mau/vapt/main/image/nikto_blackbox_1.png)                                                                                                                                                                                         |

| Arachni                                                                                                                                                                                  |
|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Run arachni scan without providing any recorded login<br/>![](https://raw.githubusercontent.com/gh1mau/vapt/main/image/arachni_blackbox_1.png)                                           |
| Save arachni's **JSON** result by with this naming format:<br/>`arachni_target_dd-mm-yyyy.json`<br/>![](https://raw.githubusercontent.com/gh1mau/vapt/main/image/arachni_blackbox_2.png) |

| OWASP ZAP                                                                                                                                                                |
|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Run ZAP Scan without providing any recorded login, just hit the Start Attack button<br/>![](https://raw.githubusercontent.com/gh1mau/vapt/main/image/zap_blackbox_1.PNG) |
| Save the **XML** result. Save in `zap_target_dd-mm-yyyy.xml` format. <br/>![](https://raw.githubusercontent.com/gh1mau/vapt/main/image/zap_blackbox_2.PNG)               |

Here is the summary of report format that should be saved as:

| Tool      | Format | Naming Format                    |
|:--------- |:------:|:-------------------------------- |
| nessus    | CSV    | `nessus_<target>_dd-mm-yyyy.csv` |
| nikto     | XML    | `nikto_target_dd-mm-yyyy.xml`    |
| arachni   | JSON   | `arachni_target_dd-mm-yyyy.json` |
| owasp zap | XML    | `zap_target_dd-mm-yyyy.xml`      |

Next would be Massaging Phase (BlackBox Findings), here we'll start **importing**, **integrating** and **analyzing** the BlackBox Scanning Findings.

[toc](https://github.com/gh1mau/vapt/blob/main/VAPT%20methodology.md#web-application-vulnerability-assessment-and-penetration-testing-management-methodology-simplified-web-vapt-mms)

---

### Massaging Phase (BlackBox Findings)

1. [Import Findings](https://github.com/gh1mau/vapt/blob/main/VAPT%20methodology.md#import-findings)

2. [Integrations and Merging](https://github.com/gh1mau/vapt/blob/main/VAPT%20methodology.md#integrations-and-merging)

3. [Verifications](https://github.com/gh1mau/vapt/blob/main/VAPT%20methodology.md#verifications)

4. [Verifications Level 1](https://github.com/gh1mau/vapt/blob/main/VAPT%20methodology.md#verifications-level-1)

5. [Threat Modeling](https://github.com/gh1mau/vapt/blob/main/VAPT%20methodology.md#threat-modelling)

6. [Verifications Level 2](https://github.com/gh1mau/vapt/blob/main/VAPT%20methodology.md#verifications-level-2)

        

![](https://raw.githubusercontent.com/gh1mau/vapt/main/image/Massaging_Phase_Black%20Box.png)

In **Massaging Phase (BlackBox Findings)**, we are going to import the findings from the [BlackBox Scanning Phase](https://github.com/gh1mau/vapt/blob/main/VAPT%20methodology.md#blackbox-scanning-phase) to defectDojo.

### Import Findings

The flow to import findings to defectDojo is ilustrated in the diagram below:

![](https://raw.githubusercontent.com/gh1mau/vapt/main/image/massaging_blackbox/import_dojo_flow.png)

| Import Nessus Findings                                                                                                                                                                                  |
|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Add nessus findings, and click the Import button. You will be redirected to the Engagement page.<br/>![](https://raw.githubusercontent.com/gh1mau/vapt/main/image/massaging_blackbox/nessus_import.PNG) |
| Engagement Page<br/>![](https://raw.githubusercontent.com/gh1mau/vapt/main/image/massaging_blackbox/nessus_engagement_1.png)                                                                            |
| Edit the Engagement Test, later we will start Verifying and and Analyzing the findings<br/>![](https://raw.githubusercontent.com/gh1mau/vapt/main/image/massaging_blackbox/nessus_engagement_2.png)     |

| Import Nikto Findings                                                                                                                                                                                 |
|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Add nikto findings, and click the Import button. You will be redirected to the Engagement page.<br/>![](https://raw.githubusercontent.com/gh1mau/vapt/main/image/massaging_blackbox/nikto_import.png) |
| Engagement Page<br/>![](https://raw.githubusercontent.com/gh1mau/vapt/main/image/massaging_blackbox/nikto_engagement_1.png)                                                                           |
| Edit the Engagement Test, later we will start Verifying and and Analyzing the findings<br/>![](https://raw.githubusercontent.com/gh1mau/vapt/main/image/massaging_blackbox/nikto_engagement_2.png)    |

| Import Arachni Findings                                                                                                                                                                                   |
|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Add arachni findings, and click the Import button. You will be redirected to the Engagement page.<br/>![](https://raw.githubusercontent.com/gh1mau/vapt/main/image/massaging_blackbox/arachni_import.png) |
| Engagement Page<br/>![](https://raw.githubusercontent.com/gh1mau/vapt/main/image/massaging_blackbox/arachni_engagement_1.png)                                                                             |
| Edit the Engagement Test, later we will start Verifying and and Analyzing the findings<br/>![](https://raw.githubusercontent.com/gh1mau/vapt/main/image/massaging_blackbox/arachni_engagement_2.png)      |

| Import OWASP ZAP Findings                                                                                                                                                                               |
|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Add OWASP ZAP findings, and click the Import button. You will be redirected to the Engagement page.<br/>![](https://raw.githubusercontent.com/gh1mau/vapt/main/image/massaging_blackbox/zap_import.png) |
| Engagement Page<br/>![](https://raw.githubusercontent.com/gh1mau/vapt/main/image/massaging_blackbox/zap_engagement_1.png)                                                                               |
| Edit the Engagement Test, later we will start Verifying and and Analyzing the findings<br/>![](https://raw.githubusercontent.com/gh1mau/vapt/main/image/massaging_blackbox/zap_engagement_2.png)        |

---

### Integrations and Merging

We will have 4 engagements that need to verified, we can edit the Engagement's Descriptions as needed.

![](https://raw.githubusercontent.com/gh1mau/vapt/main/image/massaging_blackbox/engagements.png)

---

### Verifications

In this stage we will need to verify every findings from each engagements. Analyze each findings and determine whether it is **Active**, **Verified**, **False Positive**, **Out Of Scope** or **Mitigated**.

image??

---

### Verifications Level 1

First step would be to Set **Active Status** to coresponding findings, then we'll verify the **Open (active) findings**. Remaing findings will be left as **inactive**  for references .

![](https://raw.githubusercontent.com/gh1mau/vapt/main/image/massaging_blackbox/verification_active.png)

We can view all the active findings: Findings -> View Open Findings. Later we have to go through each active / open findings and do the verifications. (We may need chaning the status to **Verified**, **False Positive**, **Out Of Scope** ,**Mitigated** or **Inactive**)

![](https://raw.githubusercontent.com/gh1mau/vapt/main/image/massaging_blackbox/active_findings.png)

We can look the overview of the particular product.

![](https://raw.githubusercontent.com/gh1mau/vapt/main/image/massaging_blackbox/overview.png)

---

### Threat Modelling

It is advisable to create a Threat Model based on findings from Verifications Level 1 phase. I'm using OWASP Threat Dragon for this activity.

Create a simple and Generic Web Application Threat Diagram and make sure to auto suggest threats based on element, this will somehow help us creating baseline for conducting attacks during PoC Phase.

![](https://raw.githubusercontent.com/gh1mau/vapt/main/image/massaging_blackbox/threat_modelling_1.PNG)

Here is a sample of Generic Web Application Threat Diagram that can be imported to Threat Dragon.

[Download](https://github.com/gh1mau/vapt/blob/main/general_web_app.json)

---

### Verifications Level 2

In Verifications Level 2, we need to identify and clarify all the active findings and set the proper status : **Verified**, **False Positive**, **Out Of Scope**. Based on the Threat Modeling Diagram that we have created earier, we will conduct the PoC Phase to verify all the active findings.

![](https://raw.githubusercontent.com/gh1mau/vapt/main/image/massaging_blackbox/verifications_level2.png)

During this phase we might uncover False Negative findings by using several common fuzzing techniques.

> A false negative is the opposite of a false positive (go figure!). You may run a security scanner like Nessus and for one reason or another it may miss a vulnerability that may in fact exist. Possible reasons for a false negative include a check not yet being written (maybe the vulnerability is to new?), user error (maybe you didn't select the right policy, or maybe your configuration needs tweaking), or some other good explanation

[toc](https://github.com/gh1mau/vapt/blob/main/VAPT%20methodology.md#web-application-vulnerability-assessment-and-penetration-testing-management-methodology-simplified-web-vapt-mms)

---

### PoC Phase 1 (BlackBox Findings)

This is a list of common vulnerabilites that i found during my Penetration Testing activity, incuding fuzzing techniques, scripting and tools used, exploitation, description and general remediation. 

| #   | Issue             |
| --- | ----------------- |
| 1   | Directory Listing |
|     |                   |
|     |                   |
