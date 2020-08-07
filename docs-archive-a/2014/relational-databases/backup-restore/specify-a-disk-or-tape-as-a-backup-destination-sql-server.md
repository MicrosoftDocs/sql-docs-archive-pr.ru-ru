---
title: Указание диска или ленты в качестве места назначения архивации (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- backup devices [SQL Server], tapes
- backing up databases [SQL Server], tapes
- database backups [SQL Server], tapes
- backup devices [SQL Server], disks
- disk backup devices [SQL Server]
- database backups [SQL Server], disks
- backing up databases [SQL Server], disks
- backups [SQL Server], creating
- tape backup devices, backing up
ms.assetid: e391f452-ed8c-4b40-b846-ac3881271b94
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8a0f8ec5d9741e42f3b7d8eda8ebdba23622982d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731733"
---
# <a name="specify-a-disk-or-tape-as-a-backup-destination-sql-server"></a>Указание в качестве назначения резервного копирования диска или ленты (SQL Server)
  В этом разделе описывается, как указать диск или ленту для резервного копирования в среде [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
> [!NOTE]  
>  Поддержка резервного копирования на ленточные устройства будет исключена в будущей версии SQL Server. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Безопасность](#Security)  
  
-   **Указание в качестве назначения резервного копирования диска или ленты с помощью.**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Разрешения BACKUP DATABASE и BACKUP LOG назначены по умолчанию членам предопределенной роли сервера **sysadmin** и предопределенным ролям базы данных **db_owner** и **db_backupoperator** .  
  
 Проблемы, связанные с владельцем и разрешениями у физических файлов на устройстве резервного копирования, могут помешать операции резервного копирования. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должен иметь возможность считывать и записывать данные на устройстве; учетная запись, от имени которой выполняется служба [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , должна иметь разрешения на запись. Однако процедура [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql), добавляющая запись для устройства резервного копирования в системные таблицы, не проверяет разрешения на доступ к файлу. Проблемы физического файла устройства резервного копирования могут не проявляться до момента доступа к физическому ресурсу во время операции резервного копирования или восстановления.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-specify-a-disk-or-tape-as-a-backup-destination"></a>Указание в качестве назначения резервного копирования диска или ленты.  
  
1.  После подключения к соответствующему экземпляру [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] в обозревателе объектов разверните дерево сервера, щелкнув его имя.  
  
2.  Раскройте узел **Базы данных**и в зависимости от типа восстанавливаемой базы данных выберите пользовательскую базу данных или раскройте узел **Системные базы данных** и выберите системную базу данных.  
  
3.  Щелкните правой кнопкой мыши базу данных, выберите пункт **Задачи**, а затем команду **Создать резервную копию**. Откроется диалоговое окно **Резервное копирование базы данных** .  
  
4.  В разделе **Назначение** страницы **Общее** выберите **Диск** или **Лента**. Чтобы выбрать пути к 64 (или менее) дискам или накопителям на магнитной ленте, содержащим один набор носителей, нажмите кнопку **Добавить**.  
  
     Чтобы удалить носитель резервной копии, выберите его и нажмите кнопку **Удалить**. Чтобы просмотреть содержимое носителя резервной копии, выберите его и щелкните **Содержимое**.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-specify-a-disk-or-tape-as-a-backup-destination"></a>Указание в качестве назначения резервного копирования диска или ленты.  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  В инструкции [BACKUP](/sql/t-sql/statements/backup-transact-sql) укажите этот файл или устройство и его физическое имя. В этом примере выполняется резервное копирование базы данных `AdventureWorks2012` в файл на диске `Z:\SQLServerBackups\AdventureWorks2012.Bak`.  
  
```  
USE AdventureWorks2012;  
GO  
BACKUP DATABASE AdventureWorks2012  
TO DISK = 'Z:\SQLServerBackups\AdventureWorks2012.Bak'  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Создание резервной копии журнала транзакций (SQL Server)](back-up-a-transaction-log-sql-server.md)   
 [Создание резервных копий файлов и файловых групп (SQL Server)](back-up-files-and-filegroups-sql-server.md)   
 [Определение логического устройства резервного копирования для дискового файла (SQL Server)](define-a-logical-backup-device-for-a-disk-file-sql-server.md)   
 [Создание разностной резервной копии базы данных (SQL Server)](create-a-differential-database-backup-sql-server.md)   
 [Определение логического устройства резервного копирования для ленточного накопителя (SQL Server)](define-a-logical-backup-device-for-a-tape-drive-sql-server.md)  
  
  
