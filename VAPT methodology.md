### Vulnerability Assessment and Penetration Testing Management Methodology

![](https://raw.githubusercontent.com/gh1mau/vapt/main/image/VAPT%20methodology.png)

#### Scanning Phase:

1. Run Nessus scan and export the xml file.

2. Run nikto and export the xml file (refer to [Setup Nikto in Ubuntu 18.04](https://github.com/gh1mau/vapt/blob/main/nikto.md#setup-nikto-in-ubuntu-1804) for setup and cheat sheet)
   
   | Instructions                                                                                                                 |
   | ---------------------------------------------------------------------------------------------------------------------------- |
   | Run nikto and save xml results:<br/>`./nikto.pl -h target -o target.xml`                                                     |
   | Import nikto xml output to defectDojo:<br/>![](https://raw.githubusercontent.com/gh1mau/vapt/main/image/import_findings.PNG) |

3. Run arachni and export the xml fie

4. Run OWASP ZAP and export the xml file
