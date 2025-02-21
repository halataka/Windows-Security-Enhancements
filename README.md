# Windows-Security-Enhancements

## Objective

This project focuses on securing Windows Server 2019 by implementing essential security measures, including enforcing automatic updates and configuring audit policies. The goal is to minimize security vulnerabilities, enhance system monitoring, and ensure compliance with security best practices through structured configurations.

### Skills Learned

- Configuring Windows Group Policy for security enhancements
- Enabling and enforcing automatic updates on Windows Server 2019
- Implementing security auditing policies for compliance and monitoring
- Using PowerShell and Command Prompt for system administration
- Strengthening system security using industry best practices
- Applying security best practices to enterprise environments

### Tools Used

- Windows Group Policy Management Console (GPMC)
- PowerShell and Command Prompt
- Windows Server 2019
- VMware

## Procedures

### Enforce Automatic Updates Across All Systems in The Domain 

#### Purpose: Ensure all Windows systems within the domain receive security patches automatically through Group Policy. 

#### Steps:
Accessed Group Policy Management Console (GPMC) to manage update policies.

Edited Default Domain Policy under Computer Configuration → Administrative Templates → Windows Update.

Enabled Configure Automatic Updates and set updates to Auto Download & Schedule Install (Daily at 7:00 PM).

![Screenshot 2025-02-20 190022](https://github.com/user-attachments/assets/7c1c582a-e786-44e0-bd75-b29dbce4b404)
*Ref 1: Enabled Automatic Updates in the Default Domain Policy*

![Screenshot 2025-02-20 190632](https://github.com/user-attachments/assets/6b99dc5c-d6e1-4500-8ac6-b67f515e132d)
*Ref 2: Automatic Update Schedule in the Default Domain Policy*

Enforced the policy updates by running gpupdate /force in PowerShell 

Verified configurations by running gpresult in PowerShell

![Screenshot 2025-02-20 190632](https://github.com/user-attachments/assets/e8e10486-da7b-4c88-aabf-1de7b4566e24)
 *Ref 3: Output of gpresult Showing the Default Domain Policy has Been Updated*

Verified the policy had been applied across the domain by running rsop.msc on a Windows client within the domain.
 
![Screenshot 2025-02-20 191913](https://github.com/user-attachments/assets/a34e81bc-5371-4afc-ada0-8a63b9180c86)
*Ref 4: Windows Client Computer Configuration Reflecting the Updated Default Domain Policy*

 ### Audit Policy Configuration 
 #### Purpose: Enable security event logging across all domain-joined systems for compliance and incident monitoring.

#### Steps:
Accessed Group Policy Management Console (GPMC) to configure audit policies.

Edited Default Domain Policy under Computer Configuration → Windows Settings → Security Settings → Local Policies → Audit Policy.

Enabled Auditing for: 
- Logon Events
- Account Logon Events
- Object Access
- Policy Changes
- System Events

Enforced the policy updates by running gpupdate /force in PowerShell 

![Screenshot 2025-02-20 191533](https://github.com/user-attachments/assets/3470eb97-3c9b-4fae-b278-0291dd881036)
*Ref 4: Configured Audit Policy in the Default Domain Policy*

Verified the policy had been applied across the domain by running rsop.msc on a Windows client within the domain.

![Screenshot 2025-02-20 192422](https://github.com/user-attachments/assets/66bc48aa-3c9d-4107-894d-02a0d6c39f2e)
*Ref 5: Windows Client Computer Configuration Reflecting the Updated Default Domain Policy*

## Results
- Enforced Automatic Updates on Windows Server 2019: Ensured all domain-joined machines receive timely security patches, reducing vulnerabilities.

- Configured Audit Policies on Windows Server 2019: Improved security monitoring, compliance, and event logging across all systems.




