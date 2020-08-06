---
title: Удаление объектов служб Data Quality Services | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 1b7c6dbb-b40e-4822-9caa-608e1056af8e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 86ff3558430bdbc501b1d04fe13c6db886c34092
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735877"
---
# <a name="remove-data-quality-server-objects"></a>Удаление объектов служб Data Quality Services
  При удалении [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] с экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]или при полном удалении экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , содержащего [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] , некоторые объекты [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] сохраняются, в том числе базы данных служб DQS. Это означает, что при удалении сервера служб DQS с помощью программы установки SQL Server данные [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] не теряются. После завершения процесса удаления эти объекты [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] необходимо удалить вручную.  
  
> [!NOTE]
>  -   Перед удалением [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)]рассмотрите возможность создания резервных копий всех имеющихся баз знаний путем их экспорта в файл DQSB, который впоследствии можно будет использовать для импорта всех баз знаний в новую установку [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] . Экспорт и импорт всех баз знаний служб DQS можно выполнить только с помощью программы DQSInstaller.exe, запускаемой из командной строки с соответствующими параметрами. Дополнительные сведения см. в статье [Экспорт и импорт баз знаний DQS с помощью DQSInstaller.exe](../../data-quality-services/install-windows/export-and-import-dqs-knowledge-bases-using-dqsinstaller-exe.md).  
> -   Перед удалением баз данных служб DQS, возможно, следует создать их резервную копию для последующего восстановления. Дополнительные сведения об этой процедуре см. в разделе [Управление базами данных DQS](../../../2014/data-quality-services/manage-dqs-databases.md).  
  
## <a name="uninstall-data-quality-server-from-a-sql-server-instance"></a>Удаление сервера DQS с экземпляра SQL Server  
 После удаления сервера [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] с экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]необходимо вручную удалить следующие объекты сервера [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] с экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] после того, как процесс удаления сервера [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] будет завершен:  
  
-   Базы данных DQS_MAIN, DQS_PROJECTS и DQS_STAGING_DATA.  
  
-   \#Имена для входа ##MS_dqs_db_owner_login## и ##MS_dqs_service_login##.  
  
-   Хранимая процедура DQInitDQS_MAIN из базы данных master.  
  
 Эти объекты можно удалить в среде SQL Server Management Studio, щелкнув правой кнопкой мыши объект и выбрав в контекстном меню пункт **Удалить** .  
  
> [!IMPORTANT]  
>  Если сервер [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] удаляется с экземпляра SQL Server с помощью параметра командной строки `-uninstall` , то в рамках процесса удаления будут удалены все объекты служб DQS. Удалять данные объекты вручную после удаления сервера [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)]не потребуется. Для удаления [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] из командной строки введите следующую команду в командной строке и нажмите клавишу ВВОД:   
> `dqsinstaller.exe -uninstall`  
  
## <a name="uninstall-sql-server-instance-containing-data-quality-server"></a>Удаление экземпляра SQL Server, содержащего сервер DQS  
 При полном удалении экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , содержащего сервер [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)], необходимо вручную удалить базы данных DQS_MAIN, DQS_PROJECTS и DQS_STAGING_DATA с компьютера после завершения процесса удаления. В установке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] по умолчанию файлы баз данных DQS_MAIN, DQS_PROJECTS и DQS_STAGING_DATA находятся в папке «C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA».  
  
## <a name="see-also"></a>См. также:  
 [Удаление существующего экземпляра SQL Server (программа установки)](../../../2014/sql-server/install/uninstall-an-existing-instance-of-sql-server-setup.md)   
 [Удаление SQL Server 2014](uninstall-sql-server.md)  
  
  
