---
title: Массовый импорт данных большого объекта с помощью поставщика больших наборов строк OPENROWSET (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- SINGLE_NCLOB option
- bulk rowset providers [SQL Server]
- bulk importing [SQL Server], data formats
- OPENROWSET function, bulk importing large data
- SINGLE_CLOB option
- data formats [SQL Server], large-object data
- large data, bulk imports
- SINGLE_BLOB option
ms.assetid: 171cdd5c-1e47-4bd7-b99a-4f0fd4e10526
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0f43aa2fa5e7f7ef0b2c8f1f6e5e6ff28e02f9f1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87658710"
---
# <a name="bulk-import-large-object-data-by-using-the-openrowset-bulk-rowset-provider-sql-server"></a>Массовый импорт данных больших объектов при помощи поставщика больших наборов строк OPENROWSET (SQL Server)
  Поставщик больших наборов строк OPENROWSET в среде [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] позволяет выполнять массовый импорт файла данных как большого объекта данных.  
  
 Поставщик больших наборов строк OPENROWSET поддерживает следующие типы больших объектов данных: **varbinary**(max) или **image**, **varchar**(max) или **text**и **nvarchar**(max) или **ntext**.  
  
> [!NOTE]  
>  Типы данных **image**, **text** и **ntext** считаются устаревшими.  
  
 В предложении OPENROWSET BULK поддерживаются три параметра для импорта содержимого файла данных в виде однострочного набора строк с одним столбцом. Вместо файла форматирования можно указать один из данных параметров для больших объектов. Это следующие параметры:  
  
 SINGLE_BLOB  
 Считывает содержимое файла *data_file* в одну строку и возвращает его в виде набора строк, состоящего из одного столбца типа **varbinary(max)** .  
  
 SINGLE_CLOB  
 Считывает содержимое указанного файла данных в виде символов и возвращает его в виде набора строк, состоящего из одной строки и одного столбца типа **varchar(max)** , с параметрами сортировки текущей базы данных; это может быть, например, текстовый документ или документ [!INCLUDE[msCoName](../../includes/msconame-md.md)] Word.  
  
 SINGLE_NCLOB  
 Считывает содержимое указанного файла данных в кодировке Юникод и возвращает содержимое в виде набора строк, состоящего из одной строки и одного столбца типа **varchar(max)** , с параметрами сортировки текущей базы данных.  
  
## <a name="see-also"></a>См. также:  
 [Массовый импорт данных при помощи инструкции BULK INSERT или OPENROWSET(BULK...) (SQL Server)](import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md)   
 [BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql)   
 [OPENROWSET (Transact-SQL)](/sql/t-sql/functions/openrowset-transact-sql)   
 [Сохранение значений NULL или использование значений по умолчанию при массовом импорте данных (SQL Server)](keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)   
 [bcp Utility](../../tools/bcp-utility.md)   
 [BULK INSERT (Transact-SQL)](/sql/t-sql/statements/bulk-insert-transact-sql)  
  
  
