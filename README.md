# BACKUP-OF-DNS-DATABASE-ACTIVE-DIR-INT.-ZONES-PRIMARY-ZONES
***********************

**Backing Up the DNS Database**

How you back up the DNS database depends on how DNS was implemented into your organization. If your DNS zone was implemented as an Active Directory–integrated zone, then your DNS zone is included in the Active Directory database ntds.dit file. If the DNS zone is a primary zone and is not stored in AD DS, then the file is stored as 

a .dns file in the %SystemRoot%\System32\Dns folder.

***********************

**Backing Up Active Directory–Integrated Zones**

Active Directory-integrated zones are stored in AD DS and are backed up as part of a System State or a full server backup. Additionally, you can back up just the Active Directory–integrated zone by using the dnscmd command-line tool.

To back up an Active Directory–integrated zone, perform the following steps:

1. Launch an elevated command prompt.
 Run the following command:

**dnscmd /ZoneExport zone name zone file name**   
3. where "zone name" is the name of your DNS zone, and "zone file name" is the file that you want to create to hold the backup information.
   
The dnscmd tool exports the zone data to the file name that you designate in the command, to the %windir%\System32\DNS directory.

You can also use Windows PowerShell® to perform the same task. In Windows PowerShell, you use the **Export-DnsServerZone** cmdlet. For example, if you want to export a zone named contoso.com, type the following command: 

**Export-DnsServerZone –Name contoso.com –Filename contoso**
***********************

**Backing Up Primary Zones**

Backing up a primary zone that is not stored in AD DS is simply a matter of copying or backing up the individual zone file, zonename.dns, which is located in the %windir%\System32\DNS directory. For example, if your DNS primary zone is named Adatum.com, then the DNS zone file will be named Adatum.com.dns.

***********************
