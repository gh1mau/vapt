## Web Application Vulnerability Assessment and Penetration Testing Management Methodology Simplified (Web-VAPT-MMS)

1. [Introduction](https://github.com/gh1mau/vapt/blob/main/VAPT%20methodology.md#introduction)

2. [VA Scanning Tools](https://github.com/gh1mau/vapt/blob/main/VAPT%20methodology.md#va-scanning-tools)

3. [Methodology](https://github.com/gh1mau/vapt/blob/main/VAPT%20methodology.md#methodology)

4. BlackBox Scanning Phase

5. WhiteBox Scanning Phase

6. Massaging Phase

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



During the Massaging Phase later, we will corelate and analyze the findings/scanning results to find potential entry point(s) to exploit.







![](https://raw.githubusercontent.com/gh1mau/vapt/main/image/scanning_phase.png)

1. Run **Nessus** scan and export the xml file.
   
   | Instructions                                                                                                                                                                                                                                                                                                                                                                                                                      |
   | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
   | Run **nessus scan** (set the corresponding profile) and save the **CSV** result.<br/>![](https://raw.githubusercontent.com/gh1mau/vapt/main/image/nessus_report_1.png)<br/><br/>**Select All** Columns and **Generate Report**. Save in `nessus_target_dd-mm-yyyy.csv` format.<br/><br/>Example:<br/>`nessus_www.gh1mau.com_22-12-2020.csv`<br/>![](https://raw.githubusercontent.com/gh1mau/vapt/main/image/nessus_report_2.png) |
   | Import nessus csv report to defectDojo<br/>![](https://raw.githubusercontent.com/gh1mau/vapt/main/image/nessus_import_dojo.png)                                                                                                                                                                                                                                                                                                   |
   | You will be redirected to **Engagements** area, we will be touching this during the **Verification of the Findings Phase**.<br/>![](https://raw.githubusercontent.com/gh1mau/vapt/main/image/nessus_import_dojo_engagement.png)                                                                                                                                                                                                   |

2. Run **nikto** and export the xml file (refer to [Setup Nikto in Ubuntu 18.04](https://github.com/gh1mau/vapt/blob/main/nikto.md#setup-nikto-in-ubuntu-1804) for setup and cheat sheet).
   
   | Instructions                                                                                                                                                                                                                                                                                             |
   | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
   | Run nikto and save xml results:<br/>`./nikto.pl -h target -maxtime 3600s -o nikto_target_dd-mm-yyyy.xml`<br/><br/>Example:<br/>`./nikto.pl -h http://www.gh1mau.com -maxtime 3600s -o nikto_www.gh1mau.com_22-12-2020.xml`                                                                               |
   | Import nikto xml output to defectDojo (refer to [defectDojo docker setup (ubuntu 18.04)](https://github.com/gh1mau/vapt/blob/main/defectDojo.md#defectdojo-docker-setup-ubuntu-1804) for setup and run command) ):<br/>![](https://raw.githubusercontent.com/gh1mau/vapt/main/image/import_findings.PNG) |
   | You will be redirected to **Engagements** area, we will be touching this during the **Verification of the Findings Phase**.<br/>![](https://raw.githubusercontent.com/gh1mau/vapt/main/image/nikto_import_dojo_engagement.png)                                                                           |

3. Run **arachni scan** and export the report (JSON format)
   
   | Instructions                                                                                                                                                                                                                                                                          |
   | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
   | Run **arachni scan** (set the corresponding profile) and save the **JSON** result. Save in `arachni_target_dd-mm-yyyy.json` format. <br/><br/>Example:<br/>`arachni_www.gh1mau.com_22-12-2020.json`![](https://raw.githubusercontent.com/gh1mau/vapt/main/image/arachni_report_1.png) |
   | Import arachni report to defectDojo<br/>![](https://raw.githubusercontent.com/gh1mau/vapt/main/image/arachni_import_dojo.png)                                                                                                                                                         |
   | You will be redirected to **Engagements** area, we will be touching this during the **Verification of the Findings Phase**.<br/>![](https://raw.githubusercontent.com/gh1mau/vapt/main/image/arachni_import_dojo_engagement.png)                                                      |

4. Run **OWASP ZAP** and export the xml file
   
   | Instructions                                                                                                                                                                                                                 |
   | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
   | Run **OWASP ZAP** and save the **XML** result. Save in `zap_target_dd-mm-yyyy.json` format. <br/>![](https://raw.githubusercontent.com/gh1mau/vapt/main/image/zap_report.png)                                                |
   | Import OWASP ZAP report to defectDojo<br/>![](https://raw.githubusercontent.com/gh1mau/vapt/main/image/zap_import_dojo.png)                                                                                                  |
   | You will be redirected to **Engagements** area, we will be touching this during the **Verification of the Findings Phase**.<br/>![](https://raw.githubusercontent.com/gh1mau/vapt/main/image/zap_import_dojo_engagement.png) |
