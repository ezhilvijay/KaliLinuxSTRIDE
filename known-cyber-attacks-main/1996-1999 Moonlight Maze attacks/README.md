# Introduction

Moonlight Maze was a cyber-espionage campaign that started in 1996, with the aim of stealing sensitive information from Government, Military, and Academic organisations in the United States and United Kingdom.
[[8](https://en.wikipedia.org/wiki/Moonlight_Maze)] Each attack would typically leverage publicly available exploits as well as heavily modified variants of publicly available malware.

Targets of Moonlight Maze include:
- NASA
- US Department of Energy
- US Navy
- US Army
- US Air Force
- US Department of Defense
- US National Oceanic and Atmospheric Administration
- UK Institute of Personnel and Development
- Various universities, research organisations, and academic organisations in the USA and UK
- Various public libraries in the USA
- Various organisations and businesses in Canada, Brazil, Germany, Norway, and Thailand [[10](https://medium.com/@chris_doman/the-first-sophistiated-cyber-attacks-how-operation-moonlight-maze-made-history-2adb12cc43f7)]

# Modus operandi of the attackers

The attackers would start by targeting specific web servers with an exploit against the vulnerable PHF binary, which was commonly located in the 'cgi-bin' directory of the web server. [[2](https://insecure.org/sploits/phf-cgi.html)]

This exploit allowed the attackers to exfiltrate the credentials of users [[2](https://insecure.org/sploits/phf-cgi.html)], usually via an FTP connection. [[3](https://securelist.com/penquins-moonlit-maze/77883/)]

Once the attackers gained access to the server using stolen credentials, they would attempt to gain root permissions by running various escalation of privilege exploits.

Once the attackers had root privileges, they would typically deploy network sniffers, exfiltration tools, and other malware onto the compromised server for several months. [[4](https://www.youtube.com/watch?v=jgTDvvl_j5Y)]

After exfiltrating as much data as possible for several weeks / months, the attackers would then survey the network of the compromised machine, in the hope of discovering more vulnerable servers on the network.

Typically, each server they compromised would be leveraged as a proxy / staging server for the attackers to tunnel their malicious activity through. [[3](https://securelist.com/penquins-moonlit-maze/77883/)] [[4](https://www.youtube.com/watch?v=jgTDvvl_j5Y)]

# Impact of the attack

Thousands of documents were stolen from dozens of organisations in the USA and UK.
These documents usually contained sensitive information relating to national security, military technologies, and encryption techniques. [[8](https://en.wikipedia.org/wiki/Moonlight_Maze)]

Not much is publicly known about exactly what information was stolen, due to the fact that the FBI has kept this information classified despite multiple Freedom of Information requests. [[1](https://www.youtube.com/watch?v=zSrjkWDXSS8)]

# Categorisation in the STRIDE Model
### Spoofing
The attackers used stolen credentials in order to imitate government personnel, military personnel, university students, and others. [[4](https://www.youtube.com/watch?v=jgTDvvl_j5Y)]

The attackers compromised servers in various countries (UK, Canada, Brazil, Germany, Norway, Thailand) and turned them into proxies for the purpose of spoofing malicious traffic to appear as if it was coming from a legitimate source.
### Tampering
The attackers used kernel patchers for SunOS systems in order to gain low level access to the system. (Probably for the purpose of hiding malicious activity) [[5](https://media.kasperskycontenthub.com/wp-content/uploads/sites/43/2018/03/07180254/Penquins_Moonlit_Maze_AppendixB.pdf)]
### Repudiation
The attackers used log cleaners in order to wipe traces of malicious activity [[5](https://media.kasperskycontenthub.com/wp-content/uploads/sites/43/2018/03/07180254/Penquins_Moonlit_Maze_AppendixB.pdf)]
### Information Disclosure
The attackers used network sniffers, keyloggers, and exfiltration scripts to steal thousands of documents over a period of 4 years [[1](https://www.youtube.com/watch?v=zSrjkWDXSS8)] [[4](https://www.youtube.com/watch?v=jgTDvvl_j5Y)]
### Denial of Service
N/A
### Escalation of Privilege
The attackers used various exploit bundles for SunOS and IRIX systems in order to gain root privileges [[5](https://media.kasperskycontenthub.com/wp-content/uploads/sites/43/2018/03/07180254/Penquins_Moonlit_Maze_AppendixB.pdf)]

# CVEs
### CVE-1999-0025 (Buffer overflow vulnerability against IRIX systems)
This is a buffer overflow vulnerability in the 'df' program, which allows an attacker to run arbitrary commands with root privileges [[6](https://www.exploit-db.com/exploits/19274)]

The 'df' program was designed for IRIX 5.x and IRIX 6.x systems.

The Moonlight Maze attackers used this exploit for escalation of privilege. [[5](https://media.kasperskycontenthub.com/wp-content/uploads/sites/43/2018/03/07180254/Penquins_Moonlit_Maze_AppendixB.pdf)]

### CVE-1999-0067 (RCE vulnerability in the PHF binary in httpd web servers)
This vulnerability allows an attacker to remotely execute commands by using shell metacharacters in a malicious url string [[2](https://insecure.org/sploits/phf-cgi.html)] [[7](https://www.cvedetails.com/cve/CVE-1999-0067/)]

The Moonlight Maze attackers used this exploit for compromising specific web servers. [[3](https://securelist.com/penquins-moonlit-maze/77883/)] [[4](https://www.youtube.com/watch?v=jgTDvvl_j5Y)]

# What measures have been put in place as a result of the attack
The FBI attempted to mitigate this attack by removing the vulnerable PHF binary from publicly available government and military web servers. [[4](https://www.youtube.com/watch?v=jgTDvvl_j5Y)]

The Metropolitan Police turned one of the infected servers in London against the attackers in an attempt to collect intelligence about the attack. [[3](https://securelist.com/penquins-moonlit-maze/77883/)] [[4](https://www.youtube.com/watch?v=jgTDvvl_j5Y)] [[9](https://www.zdnet.com/article/ancient-moonlight-maze-backdoor-remerges-as-modern-apt/)]

It was later revealed in the Snowden leaks that both Canadian and American authorities had conducted counter-intelligence operations against Moonlight Maze [[4](https://www.youtube.com/watch?v=jgTDvvl_j5Y)]
(Note: In the Snowden leaks, Moonlight Maze is referenced under the codenames "Storm Cloud" & "MAKERSMARK") [[9](https://www.zdnet.com/article/ancient-moonlight-maze-backdoor-remerges-as-modern-apt/)]

# Summary video
[Here is a video](https://www.youtube.com/watch?v=9RorL9y70GU) that summarises the Moonlight Maze attack.

# References

[1] Thomas Rid (2016) Back to the future - moonlight maze, YouTube. Available at: https://www.youtube.com/watch?v=zSrjkWDXSS8 (Accessed: October 24, 2022).

[2] /cgi-bin/phf vulnerability (no date). Available at: https://insecure.org/sploits/phf-cgi.html (Accessed: October 24, 2022).

[3] Costin Raiu, Thomas Rid, Juan Andres Guerrero-Saade, Daniel Moore (2017) Penquin's Moonlit Maze, Securelist. Kaspersky Lab. Available at: https://securelist.com/penquins-moonlit-maze/77883/ (Accessed: October 24, 2022).

[4] Costin Raiu, Thomas Rid, Juan Andres Guerrero-Saade, Daniel Moore (2017) A LINK TO THE PAST: CONNECTING THE BIRTH OF CYBERESPIONAGE Available at: https://www.youtube.com/watch?v=jgTDvvl_j5Y (Accessed: October 24, 2022).

[5] Costin Raiu, Thomas Rid, Juan Andres Guerrero-Saade, Daniel Moore (2017) Moonlight Maze Technical Report. Available at: https://media.kasperskycontenthub.com/wp-content/uploads/sites/43/2018/03/07180254/Penquins_Moonlit_Maze_AppendixB.pdf (Accessed: October 24, 2022).

[6] David Hedley (1997) SGI IRIX 6.3 - 'df' Local Privilege Escalation Available at: https://www.exploit-db.com/exploits/19274 (Accessed: October 24, 2022).

[7] (no author) (1996) Remote Command Execution Vulnerability in PHF CGI program Available at: https://www.cvedetails.com/cve/CVE-1999-0067/ (Accessed: October 24, 2022).

[8] Moonlight Maze - Wikipedia Available at: https://en.wikipedia.org/wiki/Moonlight_Maze (Accessed: October 24, 2022).

[9] Charlie Osborne (2017) Ancient Moonlight Maze backdoor remerges as modern APT Available at: https://www.zdnet.com/article/ancient-moonlight-maze-backdoor-remerges-as-modern-apt/ (Accessed: October 24, 2022).

[10] Chris Doman (2016) The First Cyber Espionage Attacks: How Operation Moonlight Maze made history Available at: https://medium.com/@chris_doman/the-first-sophistiated-cyber-attacks-how-operation-moonlight-maze-made-history-2adb12cc43f7 (Accessed: October 01, 2023)