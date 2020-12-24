## Vulnerability Assessment and Penetration Testing Management Methodology Simplified

![](https://raw.githubusercontent.com/gh1mau/vapt/main/image/VAPT%20methodology.png)

1. [Scanning Phase](https://github.com/gh1mau/vapt/blob/main/VAPT%20methodology.md#scanning-phase)
   
   

### Scanning Phase:

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
