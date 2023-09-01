Privilege escalation techniques, and prevention.

Privilege Escalation Techniques:

Exploiting Vulnerabilities: Attackers can exploit software vulnerabilities to gain elevated privileges. It can be kernel vulnerabilities, misconfigured services, or application-level weaknesses.

Abusing Sudo Access: If a user has sudo privileges, attackers can misuse this access to execute commands with elevated privileges.

Weak Passwords: Weak or easily guessable passwords can be exploited through brute-force attacks, enabling unauthorized access to accounts with higher privileges.

Misconfigured Permissions: Poorly configured file and directory permissions can allow unauthorized users to access or modify sensitive system files.

Exploiting Set-UID/GID Binaries: Set-UID and Set-GID programs run with elevated privileges. If attackers find vulnerabilities in these programs, they can use them to escalate their own privileges.

Privilege Escalation Prevention:

Regular Patching and Updates: Keep the system up-to-date with security patches and updates to mitigate known vulnerabilities.

Least Privilege Principle: Limit user privileges to the minimum necessary for their tasks. Avoid granting unnecessary root or sudo access.

Strong Authentication: Enforce strong password policies, consider multi-factor authentication, and implement secure authentication methods like SSH keys.

File and Directory Permissions: Regularly audit and set proper permissions on files and directories, following the principle of least privilege.

Monitoring and Auditing: Implement system monitoring and auditing tools to detect unusual activities and privilege escalations in real-time.

Regular Security Audits: Conduct regular security audits and vulnerability assessments to identify and fix weaknesses proactively.

Sudo Configuration: Carefully configure sudo to restrict which commands users can execute with elevated privileges.

AppArmor or SELinux: Use Mandatory Access Control (MAC) mechanisms like AppArmor or SELinux to confine processes and limit potential damage from exploits.

Kernel Hardening: Apply kernel hardening techniques such as grsecurity/PaX to protect against kernel-level vulnerabilities.

User Training and Awareness: Train users and administrators about security best practices, social engineering risks, and how to recognize and report potential threats.

Zero Trust Architecture: Implement a zero-trust network architecture, where trust is never assumed, and authentication and authorization are required for every access request.






Buffer Overflows.

Directory traversal (prevention).

Remote Code Execution / getting shells.

Local databases

Some messaging apps use sqlite for storing messages.
Useful for digital forensics, especially on phones.


Windows

Windows registry and group policy.
Active Directory (AD).


Bloodhound tool.

BloodHound is a powerful open-source tool used for analyzing and visualizing the Active Directory (AD) and Azure AD environments in Windows networks. It's a security tool that helps both attackers and defenders assess and improve the security of their AD infrastructure. Here's what BloodHound can do:

Graphical Visualization: BloodHound provides a graphical representation of an organization's AD structure, showing relationships between users, groups, computers, and other objects.

Attack Path Analysis: One of its primary use cases is to identify and map out potential attack paths that an attacker could use to escalate privileges or move laterally within the network. It does this by analyzing AD permissions, group memberships, and trust relationships.

Risk Assessment: BloodHound can help organizations identify and mitigate security risks within their AD environment. It can highlight overly permissive access control configurations and misconfigurations that could lead to security breaches.

Credential Theft Path Detection: BloodHound can identify paths within the network where an attacker with limited access could potentially steal credentials or escalate their privileges.

Adversary Simulation: Security professionals and red teams often use BloodHound to simulate attacks on an AD environment, helping organizations understand their vulnerabilities and develop effective defense strategies.

Query Language: BloodHound includes a query language that allows users to create custom queries to identify specific security risks or patterns within the AD environment.

Data Collection: BloodHound collects data from various sources within the AD environment, including Active Directory, LDAP, SMB, and others. This data is used to build the graph and perform analysis.

It's important to note that while BloodHound can be a valuable tool for security professionals to assess and improve the security of AD environments, it can also be misused by malicious actors. Therefore, its use should be carefully controlled and monitored within an organization.

BloodHound is typically used in combination with other security tools and practices as part of a comprehensive security strategy to protect Windows-based networks.


Kerberos authentication with AD.
Windows SMB.
Samba (with SMB).
Buffer Overflows.
ROP.

*nix

SELinux.
Kernel, userspace, permissions.
MAC vs DAC.
/proc
/tmp - code can be saved here and executed.
/shadow
LDAP - Lightweight Directory Browsing Protocol. Lets users have one password for many services. This is similar to Active Directory in windows.

MacOS

Gotofail error (SSL).
MacSweeper.
Research Mac vulnerabilities.
