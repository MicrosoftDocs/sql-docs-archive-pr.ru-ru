---
title: Доступ к данным FILESTREAM с помощью Transact-SQL | Документация Майкрософт
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], Transact-SQL
ms.assetid: a6bf0ce7-7e5e-4a07-8917-ee526c9d0a05
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 06d395f1acc3723fc6b45fdfa08efbae354d8014
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734169"
---
# <a name="access-filestream-data-with-transact-sql"></a>Доступ к данным FILESTREAM с помощью Transact-SQL
  В этом разделе описаны способы использования инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)] INSERT, UPDATE и DELETE для управления данными FILESTREAM.  
  
> [!NOTE]  
>  Для примеров в этом разделе требуется база данных с поддержкой FILESTREAM и таблица, которая создана в разделе [Создание базы данных с поддержкой FILESTREAM](create-a-filestream-enabled-database.md) и [Создание таблицы для хранения данных FILESTREAM](create-a-table-for-storing-filestream-data.md).  
  
##  <a name="inserting-a-row-that-contains-filestream-data"></a><a name="ins"></a> Вставка строки, содержащей данные FILESTREAM  
 Чтобы вставить строку в таблицу, которая поддерживает данные FILESTREAM, используйте инструкцию [!INCLUDE[tsql](../../includes/tsql-md.md)] INSERT. Значение, вставляемое в столбец FILESTREAM, может быть либо значением NULL, либо значением типа `varbinary(max)`.  
  
### <a name="inserting-null"></a>Вставка значения NULL  
 Следующий пример иллюстрирует порядок вставки значения `NULL`. Если значение FILESTREAM равно `NULL`, компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] не создает файл в файловой системе.  
  
 [!code-sql[FILESTREAM#FS_InsertNULL](../../snippets/tsql/SQL15/tsql/filestream/transact-sql/filestream.sql#fs_insertnull)]  
  
### <a name="inserting-a-zero-length-record"></a>Вставка записи с нулевой длиной  
 В следующем примере показано, как использовать инструкцию `INSERT` для создания записи с нулевой длиной. Это бывает полезно в случае, если нужно получить дескриптор файла, работать с которым предполагается с помощью API-интерфейсов Win32.  
  
 [!code-sql[FILESTREAM#FS_InsertZero](../../snippets/tsql/SQL15/tsql/filestream/transact-sql/filestream.sql#fs_insertzero)]  
  
### <a name="creating-a-data-file"></a>Создание файла данных  
 В следующем примере кода показывается, как использовать инструкцию `INSERT` для создания файла, содержащего данные. Компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] преобразует строку `Seismic Data` в значение типа `varbinary(max)` . FILESTREAM создает файл Windows, если он еще не был создан. Затем данные добавляются в файл данных.  
  
 [!code-sql[FILESTREAM#FS_InsertData](../../snippets/tsql/SQL15/tsql/filestream/transact-sql/filestream.sql#fs_insertdata)]  
  
 При выборке всех данных в таблице `Archive`.`dbo.Records` результат напоминает тот, который приведен в следующей таблице. Однако столбец `Id` будет содержать разные идентификаторы GUID.  
  
|Идентификатор|SerialNumber|Возобновить|  
|--------|------------------|------------|  
|`C871B90F-D25E-47B3-A560-7CC0CA405DAC`|`1`|`NULL`|  
|`F8F5C314-0559-4927-8FA9-1535EE0BDF50`|`2`|`0x`|  
|`7F680840-B7A4-45D4-8CD5-527C44D35B3F`|`3`|`0x536569736D69632044617461`|  
  
##  <a name="updating-filestream-data"></a><a name="upd"></a> Обновление данных FILESTREAM  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] можно использовать для обновления данных файла, хотя это может быть нежелательным при потоковой записи в файл больших объемов данных.  
  
 В следующем примере любой текст в записи файла заменяется текстом `Xray 1`.  
  
 [!code-sql[FILESTREAM#FS_UpdateData](../../snippets/tsql/SQL15/tsql/filestream/transact-sql/filestream.sql#fs_updatedata)]  
  
##  <a name="deleting-filestream-data"></a><a name="del"></a> Удаление данных FILESTREAM  
 При удалении строки, содержащей поле FILESTREAM, также удаляются и связанные с ней файлы файловой системы. Единственным способом удаления строки и, как следствие, файла является использование инструкции DELETE языка [!INCLUDE[tsql](../../includes/tsql-md.md)] .  
  
 В следующем примере показано, как удалить строку и связанный с ней файл файловой системы.  
  
 [!code-sql[FILESTREAM#FS_DeleteData](../../snippets/tsql/SQL15/tsql/filestream/transact-sql/filestream.sql#fs_deletedata)]  
  
 При выборке всех данных в таблице `dbo.Archive` строка удаляется. Связанный с ней файл больше нельзя использовать.  
  
> [!NOTE]  
>  Базовые файлы удаляются сборщиком мусора FILESTREAM.  
  
## <a name="see-also"></a>См. также:  
 [Включение и настройка FILESTREAM](enable-and-configure-filestream.md)   
 [Избегание конфликтов в операциях баз данных в приложениях FILESTREAM](avoid-conflicts-with-database-operations-in-filestream-applications.md)  
  
  
