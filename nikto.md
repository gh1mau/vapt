### Setup Nikto in Ubuntu 18.04

1. Setup:
   
   ```
   git clone https://github.com/sullo/nikto
   
   cd nikto/program
   
   # run nikto:
   ./nikto.pl
   ```

2. Cheat Sheet:
   
   | Scanning a host               |
   | ----------------------------- |
   | `./nikto.pl -h <Hostname/IP>` |
   
   | Scanning specific ports                                         |
   | --------------------------------------------------------------- |
   | `./nikto.pl -h <Hostname/IP> -port <Port Number>,<Port Number>` |
   
   | Disable SSL                          |
   | ------------------------------------ |
   | `./nikto.pl -h <Hostname/IP> -nossl` |
   
   | Force SSL                          |
   | ---------------------------------- |
   | `./nikto.pl -h <Hostname/IP> -ssl` |
   
   | Specify Host Header                  |
   | ------------------------------------ |
   | `./nikto.pl -h <Hostname/IP> -vhost` |
   
   | Output Results                                    |
   | ------------------------------------------------- |
   | `./nikto.pl -h  <Hostname/IP> -output <filename>` |
   
   Output Formats:
   
   | Syntax | Format                |
   | ------ | --------------------- |
   | csv    | Comma-separated-value |
   | htm    | HTML Format           |
   | msf+   | Log to Metaspoloit    |
   | nbe    | Nessus NBE            |
   | txt    | Plain text            |
   | xml    | XML Format            |
   
   | Scanning through a proxy                           |
   | -------------------------------------------------- |
   | `./nikto.pl -h <Hostname/IP> -useproxy <Proxy IP>` |
   
   | Database Check                         |
   | -------------------------------------- |
   | `./nikto.pl -h <Hostname/IP> -dbcheck` |
   
   | Display Options (verbose)                |
   | ---------------------------------------- |
   | `./nikto.pl -h <Hostname/IP> -Display V` |
   
   | Evasion Options                              |
   | -------------------------------------------- |
   | `./nikto -h <Hostname/IP> -evasion <Option>` |
   
   Evasion Options:
   
   | Options | Description                                      |
   |:-------:| ------------------------------------------------ |
   | 1       | Random URI Encoding                              |
   | 2       | Directory Self-Reference /./                     |
   | 3       | Premature URL ending                             |
   | 4       | Prepend long random string                       |
   | 5       | Fake parameter                                   |
   | 6       | TAB as request spacer                            |
   | 7       | Change the case of the URL                       |
   | 8       | Used windows directory separator \               |
   | A       | Use a carriage return (0x0d) as a request spacer |
   | B       | Use binary value (0x0b) as a request spacer      |


