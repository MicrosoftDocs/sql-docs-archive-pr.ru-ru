---
title: Установка Reporting Services режиме интеграции с SharePoint и в основном режиме в командной строке | Документация Майкрософт
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 048169b3-512c-41e4-895a-0416eff41268
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2b2101c40c5136e89d4e30d9551187a2b63672da
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728065"
---
# <a name="command-prompt-installation-of-reporting-services-sharepoint-mode-and-native-mode"></a>Установка режима интеграции с SharePoint и собственного режима для служб Reporting Services из командной строки
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] поддерживают установку из командной строки с помощью программы установки SQL Server. В этом разделе приведено несколько примеров установки из командной строки, характерных для служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Полное описание параметров командной строки, доступных для всех компонентов SQL Server, см. [в разделе Install SQL Server 2014 в командной строке](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md). Параметры командной строки для надстройки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] для продуктов SharePoint в этом разделе не описываются. Дополнительные сведения об установке этой надстройки из командной строки см. в разделе [Установка надстройки с помощью файла rsSharePoint.msi](install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md#bkmk_install_rssharepoint).  
  
 **[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Режим интеграции с SharePoint | [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Собственный режим  
  
## <a name="rsinstallmode-native-mode"></a>RSINSTALLMODE (Собственный режим)  
 Главный входной параметр для установки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] — это **/RSINSTALLMODE** . Он имеет два значения: **DefaultNativeMode** и **FilesOnlyMode**  
  
 Если установка включает компонент SQL Server Database Engine, то по умолчанию RSINSTALLMODE имеет значение DefaultNativeMode. В противном случае параметр RSINSTALLMODE по умолчанию имеет значение FilesOnlyMode. Если выбран режим DefaultNativeMode, но установка не включает компонент SQL Server Database Engine, то параметр RSINSTALLMODE автоматически примет значение FilesOnlyMode. Дополнительные сведения о параметрах ввода см. в разделе [Install SQL Server 2014 из командной строки](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md).  
  
## <a name="rsshpinstallmode-sharepoint-mode"></a>RSSHPINSTALLMODE (режим интеграции с SharePoint)  
 Входной параметр для установки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в режиме интеграции с SharePoint — это **/RSSHPINSTALLMODE**. Входной параметр имеет одно значение: SharePointFilesOnlyMode. Данный параметр дает указание к установке всех файлов, необходимых для режима интеграции с SharePoint, но по завершении процесса установки потребуется настройка. Дополнительная настройка осуществляется через центр администрирования SharePoint. Дополнительные сведения см. в статье [Установка служб Reporting Services в режиме SharePoint для SharePoint 2010](../../sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md).  
  
## <a name="examples-of-sharepoint-mode-installation"></a>Примеры установки в режиме интеграции с SharePoint  
 В следующем примере рассматривается установка службы компонента SQL Server Database Engine и служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в режиме интеграции с SharePoint, а также надстройки [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] для SharePoint (RS_SHPWFE).  
  
```  
setup /q /ACTION=install /FEATURES=SQL, RS_SHP, RS_SHPWFE,TOOLS /INSTANCENAME=MSSQLSERVER /SQLSYSADMINACCOUNTS="BUILTIN\ADMINISTRATORS" /RSSVCACCOUNT="NT AUTHORITY\NETWORK SERVICE" /SQLSVCACCOUNT="NT AUTHORITY\NETWORK SERVICE" /AGTSVCACCOUNT="NT AUTHORITY\NETWORK SERVICE"  
```  
  
 В следующем примере рассматривается только установка служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в режиме интеграции с SharePoint.  
  
```  
Setup.exe /q /ACTION="Install" /IACCEPTSQLSERVERLICENSETERMS /FEATURES="RS_SHP" /INSTANCEDIR="C:\Program Files\Microsoft SQL Server" /INSTALLSHAREDDIR="C:\Program Files\Microsoft SQL Server" /INSTALLSHAREDWOWDIR="C:\Program Files (x86)\Microsoft SQL Server" /INSTALLSQLDATADIR="C:\Program Files\Microsoft SQL Server" /SECURITYMODE="SQL" /SAPWD="*****" /PID="[Your PID Value]" /SQLSYSADMINACCOUNTS="[Account Name]" "AutoSql Admin Group" /ASSYSADMINACCOUNTS="[Account Name]" /UPDATEENABLED="False"  
  
```  
  
 В следующем примере рассматривается установка всех компонентов SQL Server, включая службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], как в собственном режиме, так и в режиме интеграции с SharePoint.  
  
```  
Setup.exe /q /ACTION="Install" /INSTANCENAME="MSSQLSERVER" /FEATURES="SQLEngine,Replication,SNAC,SNAC_SDK,Browser,Writer,AS,IS,MDS,Adv_SSMS,BC,BOL,Conn,SDK,DReplay_CTLR,DReplay_CLT, RS_SHP,RS_SHPWFE,DQC,BIDS,FullText, RS,DQ,SSMS" /INSTANCEDIR="C:\Program Files\Microsoft SQL Server" /INSTALLSHAREDDIR="C:\Program Files\Microsoft SQL Server" /INSTALLSHAREDWOWDIR="C:\Program Files (x86)\Microsoft SQL Server" /INSTALLSQLDATADIR="C:\Program Files\Microsoft SQL Server" /SQLSVCACCOUNT="[Account Name]" /SQLSVCPASSWORD="********" /AGTSVCACCOUNT="[Account Nam]" /AGTSVCPASSWORD="********" /CTLRSVCACCOUNT="[Account Nam]" /CTLRSVCPASSWORD="********" /CLTSVCACCOUNT="[Account Nam]" /CLTSVCPASSWORD="********" /ASSVCACCOUNT="[Account Nam]" /ASSVCPASSWORD="********" /RSSVCACCOUNT="[Account Nam]" /RSSVCPASSWORD="********" /FTSVCACCOUNT="[Account Nam]" /FTSVCPASSWORD="********" /SECURITYMODE="SQL" /SAPWD="********" /PID="[Your PID Value]" /SQLSYSADMINACCOUNTS="[Account Nam]" "AutoSql Admin Group" /ASSYSADMINACCOUNTS="BUILTIN\ADMINISTRATORS" /UPDATEENABLED="False" /IACCEPTSQLSERVERLICENSETERMS /RSSHPINSTALLMODE="SharePointFilesOnlyMode" /RSINSTALLMODE="DefaultNativeMode"  
```  
  
## <a name="examples-of-sharepoint-mode-upgrade"></a>Примеры обновления режима интеграции с SharePoint  
 В следующем примере выполняется обновление служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в режиме интеграции с SharePoint. **RSUPGRADEPASSWORD** — это пароль существующей учетной записи службы сервера отчетов. Поле RSUPGRADEPASSWORD является обязательным для обновления, если только учетная запись служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] не является встроенной.  
  
```  
Setup.exe /q /ACTION="Upgrade" /INSTANCENAME="MSSQLSERVER" /PID="[PID value]" /FTSVCACCOUNT="[DOMAIN\ACCOUNT]" /FTSVCPASSWORD="[ACCOUNTPASSSWORD]" /UPDATEENABLED="False" /IACCEPTSQLSERVERLICENSETERMS /RSUPGRADEPASSWORD="******"  
```  
  
 Далее приведен пример, с помощью которого можно обновить установку в режиме интеграции с SharePoint, в основе которой лежит архитектура общей службы SharePoint. В этом примере используется параметр ALLOWUPGRADEFORSSRSSHAREPOINTMODE. Этот параметр не требуется для обновления предыдущих версий, не основанных на архитектуре общих служб.  
  
-   [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]  
  
-   [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]  
  
```  
Setup.exe /q /ACTION="Upgrade" /INSTANCENAME="MSSQLSERVER" /PID="[Your PID Value]" /FTSVCACCOUNT="[ACCOUNT Name]" /FTSVCPASSWORD="****" /UPDATEENABLED="False" /IACCEPTSQLSERVERLICENSETERMS /ALLOWUPGRADEFORSSRSSHAREPOINTMODE="True"  
```  
  
## <a name="examples-of-native-mode-installation"></a>Примеры установки в собственном режиме  
  
```  
Setup.exe /q /ACTION="Install" /INSTANCENAME="MSSQLSERVER" /FEATURES="SQLEngine,Replication,SNAC,SNAC_SDK,Browser,Writer,AS,IS,MDS,Adv_SSMS,BC,BOL,Conn,SDK,DReplay_CTLR,DReplay_CLT,DQC,BIDS,FullText, RS,DQ,SSMS" /INSTANCEDIR="C:\Program Files\Microsoft SQL Server" /INSTALLSHAREDDIR="C:\Program Files\Microsoft SQL Server" /INSTALLSHAREDWOWDIR="C:\Program Files (x86)\Microsoft SQL Server" /INSTALLSQLDATADIR="C:\Program Files\Microsoft SQL Server" /SQLSVCACCOUNT="[Account Name]" /SQLSVCPASSWORD="********" /AGTSVCACCOUNT="[Account Nam]" /AGTSVCPASSWORD="********" /CTLRSVCACCOUNT="[Account Nam]" /CTLRSVCPASSWORD="********" /CLTSVCACCOUNT="[Account Nam]" /CLTSVCPASSWORD="********" /ASSVCACCOUNT="[Account Nam]" /ASSVCPASSWORD="********" /RSSVCACCOUNT="[Account Nam]" /RSSVCPASSWORD="********" /FTSVCACCOUNT="[Account Nam]" /FTSVCPASSWORD="********" /SECURITYMODE="SQL" /SAPWD="********" /PID="[Your PID Value]" /SQLSYSADMINACCOUNTS="[Account Nam]" "AutoSql Admin Group" /ASSYSADMINACCOUNTS="BUILTIN\ADMINISTRATORS" /UPDATEENABLED="False" /IACCEPTSQLSERVERLICENSETERMS /RSINSTALLMODE="DefaultNativeMode"  
```  
  
## <a name="see-also"></a>См. также:  
 [Установка SQL Server 2014 из командной строки](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md)   
 [Параметры SysPrep](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md#SysPrep)   
 [Установка PowerPivot из командной строки](../../sql-server/install/install-powerpivot-from-the-command-prompt.md)  
  
  
