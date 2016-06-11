---
title: Merge AppLocker Policies by Using Set-ApplockerPolicy
ms.custom: na
ms.prod: windows-server-2012
ms.reviewer: na
ms.suite: na
ms.technology: 
  - techgroup-security
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f8bb7eda-ae62-47fb-b672-1d816374b494
---
# Merge AppLocker Policies by Using Set-ApplockerPolicy
This topic describes the steps to merge AppLocker policies by using Windows PowerShell in  Windows Server 2012  and Windows 8.

The **Set\-AppLockerPolicy** cmdlet sets the specified Group Policy Object \(GPO\) to contain the specified AppLocker policy. If no Lightweight Directory Access Protocol \(LDAP\) is specified, the local GPO is the default. When the Merge parameter is used, rules in the specified AppLocker policy will be merged with the AppLocker rules in the target GPO specified in the LDAP path. The merging of policies will remove rules with duplicate rule IDs, and the enforcement setting specified by the AppLocker policy in the target GPO will be preserved. If the Merge parameter is not specified, then the new policy will overwrite the existing policy.

For information about using **Set\-AppLockerPolicy**, including syntax descriptions and parameters, see [Set\-AppLockerPolicy](http://go.microsoft.com/fwlink/?LinkId=169167) \(http:\/\/go.microsoft.com\/fwlink\/?LinkId\=169167\).

For information about using Windows PowerShell for AppLocker, including how to import the AppLocker cmdlets into Windows PowerShell, see [Use the AppLocker Windows PowerShell Cmdlets]().

You can also manually merge AppLocker policies. For the procedure to do this, see [Merge AppLocker Policies Manually](Merge-AppLocker-Policies-Manually.md).

#### To merge a local AppLocker policy with another AppLocker policy by using LDAP paths

1.  Open the PowerShell command window. For information about performing Windows PowerShell commands for AppLocker, see [Use the AppLocker Windows PowerShell Cmdlets]().

2.  At the command prompt, type **C:\\PS>Get\-AppLockerPolicy \-Local | Set\-AppLockerPolicy \-LDAP "LDAP: \/\/***<string>***" \-Merge** where *<string>* specifies the LDAP path of the unique GPO.

## Example
Gets the local AppLocker policy, and then merges the policy with the existing AppLocker policy in the GPO specified in the LDAP path.

```
C:\PS>Get-AppLockerPolicy -Local | Set-AppLockerPolicy -LDAP "LDAP://DC13.Contoso.com/CN={31B2F340-016D-11D2-945F-00C044FB984F9},CN=Policies,CN=System,DC=Contoso,DC=com" -Merge
```

