---
title: Просмотр размера разреженного файла снимка базы данных (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- snapshots [SQL Server database snapshots], sparse files
- space [SQL Server], sparse files
- sparse files [SQL Server]
- size [SQL Server], sparse files
- maximum sparse file size
- database snapshots [SQL Server], sparse files
- space [SQL Server], database snapshots
ms.assetid: 1867c5f8-d57c-46d3-933d-3642ab0a8e24
author: stevestein
ms.author: sstein
ms.openlocfilehash: 424399b9915c8e7e26e1076fd2e553aafe06fcf0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735310"
---
# <a name="view-the-size-of-the-sparse-file-of-a-database-snapshot-transact-sql"></a>Просмотр размера разреженного файла снимка базы данных (Transact-SQL)
  В этом разделе описывается использование [!INCLUDE[tsql](../../includes/tsql-md.md)] для проверки того, является ли файл базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] разреженным файлом, и для определения фактического и максимального размеров. Разреженные файлы, которые являются средством файловой системы NTFS, используются моментальными снимками базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
> [!NOTE]  
>  При создании моментального снимка базы данных разреженные файлы создаются с помощью имен файлов, указанных в инструкции CREATE DATABASE. Эти имена файлов хранятся в таблице **sys.master_files** в столбце **physical_name** . В таблице **sys.database_files** (в базе данных-источнике или в моментальном снимке) столбец **physical_name** всегда содержит имена файлов базы данных-источника.  
  
## <a name="verify-that-a-database-file-is-a-sparse-file"></a>Убедитесь, что файл базы данных является разреженным файлом  
  
1.  В экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
     Выберите столбец **is_sparse** в таблице **sys.database_files** в моментальном снимке базы данных или в таблице **sys.master_files**. Значение указывает, является ли файл разреженным, следующим образом:  
  
     1 = разреженный файл.  
  
     0 = неразреженный файл.  
  
## <a name="find-out-the-actual-size-of-a-sparse-file"></a>Определение фактического размера разреженного файла  
  
> [!NOTE]  
>  Разреженные файлы каждый раз увеличиваются в размере на 64 килобайта (КБ); таким образом, размер разреженного файла на диске всегда кратен 64 КБ.  
  
 Чтобы просмотреть число байтов, которые в настоящее время используются каждым разреженным файлом моментального снимка на диске, запросите столбец **size_on_disk_bytes** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] динамического административного представления [sys. dm_io_virtual_file_stats](/sql/relational-databases/system-dynamic-management-views/sys-dm-io-virtual-file-stats-transact-sql) .  
  
 Чтобы увидеть место на диске, занимаемое разреженным файлом, можно щелкнуть правой кнопкой мыши файл в Microsoft Windows, выбрать пункт **Свойства**и просмотреть значение **Место на диске** .  
  
## <a name="find-out-the-maximum-size-of-a-sparse-file"></a>Определение максимального размера разреженного файла  
 Максимальный размер, до которого может увеличиться разреженный файл, равен размеру соответствующего файла базы данных-источника на момент создания моментального снимка. Чтобы узнать этот размер, можно использовать один из следующих способов.  
  
-   Использование командной строки Windows.  
  
    1.  Использование команд Windows **dir** .  
  
    2.  Выбор разреженного файла, открытие диалогового окна **Свойства** в Windows и просмотр значения **Размер** .  
  
-   В экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
     Выбрать столбец **size** из таблицы **sys.database_files** в моментальном снимке базы данных или из таблицы **sys.master_files**. Значение столбца **size** отражает максимальный объем пространства (в страницах SQL), который может когда-либо использоваться моментальным снимком; это значение эквивалентно значению поля Windows **Size** , за исключением того, что оно представлено в терминах количества страниц SQL в файле; размер в байтах равен:  
  
     ( *число_страниц* * 8192)  
  
## <a name="see-also"></a>См. также:  
 [Моментальные снимки базы данных (SQL Server)](database-snapshots-sql-server.md)   
 [sys.fn_virtualfilestats (Transact-SQL)](/sql/relational-databases/system-functions/sys-fn-virtualfilestats-transact-sql)   
 [sys.database_files (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql)   
 [sys.master_files (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql)  
  
  
