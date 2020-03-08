# Why
Microsoft's team puts in a great deal of effort to produce their security baselines. Published on the [Microsoft Security Baselines Blog](https://techcommunity.microsoft.com/t5/microsoft-security-baselines/bg-p/Microsoft-Security-Baselines), these form a solid foundation on which to operate your Windows environment. Part of their stated goals, however, is to minimize impact of the policies as a way to help keep them fairly universal. This projects sheds that goal to instead create an even higher security standard. Use this project as an aspirational guide or for brand new AD implementations where there is no risk of breaking existing processes. If you just try to slap these into an already established environment you're likely going to break things.

# File structure
There are two main folders, the "gpos" folder and the "scripts" folder. In some cases, enacting certain policies will require scripts which will be placed in the "scripts" folder. The GPOs are split into several individual policies to either account for different needs (workstation vs server) or grouping themes so there isn't one single, massive policy.

# Fill in the blank policies
Certain policies require adding security groups from your environment to enforce them. You will find them in `gpos\fill_in_the_blank.xlsx` and you'll need to manually add them into your GPOs.

# ADMX templates
Releases will be tagged for the OS version being targeted, just like Microsoft's security baselines. Make sure you have the ADMX templates released for the same version installed and that your AD forest is running the highest functional levels. Also make sure you have the Microsoft Office ADMX templates.

# Remember, this is a starting point!
These policies don't make any assumption about organizational structure, team size, or really anything about how your organization operates. There may be some things in here that don't make sense for your organization and that's expected and ok. Use your organizational knowledge to adapt these policies to fit your needs. 

# Other recommendedations
This only covers one small piece of endpoint and identity security. There are many more things you should look into deploying within your environment to better your security.
* [Fine-Grained Password Policies](https://docs.microsoft.com/en-us/prhttps://docs.microsoft.com/en-us/windows-server/security/group-managed-service-accounts/group-managed-service-accounts-overview)evious-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc770394(v=ws.10))
* [Group Managed Service Accounts](https://docs.microsoft.com/en-us/windows-server/security/group-managed-service-accounts/group-managed-service-accounts-overview)
* [Local Administrator Password Solution](https://docs.microsoft.com/en-us/windows/security/identity-protection/access-control/local-accounts#sec-create-unique-passwords)
* [Azure AD Password Protection](https://docs.microsoft.com/en-us/azure/active-directory/authentication/concept-password-ban-bad-on-premises)
* [Privileged Access Management](https://docs.microsoft.com/en-us/microsoft-identity-manager/pam/privileged-identity-management-for-active-directory-domain-services)
* [Sysmon](https://docs.microsoft.com/en-us/sysinternals/downloads/sysmon) and check out [sysmon-config](https://github.com/SwiftOnSecurity/sysmon-config) by @SwiftOnSecurity

# Things known to break
* Doens't support operating systems older than Windows 8/Server 2012
* Cannot use SMB versions <3.0
