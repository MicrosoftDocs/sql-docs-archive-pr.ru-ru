---
title: Создание, изменение и удаление таблиц FileTable | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FileTables [SQL Server], altering
- FileTables [SQL Server], dropping
- FileTables [SQL Server], creating
ms.assetid: 47d69e37-8778-4630-809b-2261b5c41c2c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3a10e6333f6dd38a850a832b82a7cb7a0e0bf698
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87655782"
---
# <a name="create-alter-and-drop-filetables"></a>Создание, изменение и удаление таблиц FileTables
  Описывает способы создания новых таблиц FileTable и изменения или удаления существующих таблиц FileTable.  
  
##  <a name="creating-a-filetable"></a><a name="BasicsCreate"></a> Создание таблицы FileTable  
 Таблица FileTable является специализированной пользовательской таблицей с заранее заданной и фиксированной схемой. Эта схема содержит данные FILESTREAM, сведения о файлах и каталогах и атрибуты файлов. Сведения о данном образце схемы см. в разделе [FileTable Schema](filetable-schema.md).  
  
 Новую таблицу FileTable можно создать с помощью языка Transact-SQL или среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Поскольку таблица FileTable имеет фиксированную схему, нет необходимости указывать список столбцов. Простой синтаксис для создания таблицы FileTable позволяет указать следующее:  
  
-   Имя каталога. В иерархии папок FileTable этот каталог уровня таблицы становится дочерним для каталога базы данных, указанного на уровне базы данных, и родительским для файлов или каталогов, хранящихся в таблице.  
  
-   Имя параметров сортировки, используемое для имен файлов в столбце **Name** таблицы FileTable.  
  
-   Можно также указать имена, предназначенные для использования в трех первичных ключах и ограничениях уникальности, создаваемых автоматически.  
  
###  <a name="how-to-create-a-filetable"></a><a name="HowToCreate"></a> Как создать FileTable  
 **Создание таблицы FileTable с помощью Transact-SQL**  
 Создайте объект FileTable, вызвав инструкцию [CREATE TABLE (Transact-SQL)](/sql/t-sql/statements/create-table-transact-sql) с параметром **AS FileTable**. Поскольку таблица FileTable имеет фиксированную схему, нет необходимости указывать список столбцов. Можно указать следующие параметры для новой FileTable:  
  
1.  **FILETABLE_DIRECTORY**. Указывает каталог, выполняющий функции корневого каталога для всех файлов и каталогов, хранящихся в FileTable. Это имя должно быть уникальным среди всех имен каталогов FileTable в базе данных. Проверка уникальности выполняется без учета регистра, независимо от текущих параметров сортировки.  
  
    -   Это значение имеет тип данных **nvarchar(255)** и использует фиксированные параметры сортировки **Latin1_General_CI_AS_KS_WS**.  
  
    -   Указываемое имя каталога должно соответствовать требованиям файловой системы для допустимых имен каталогов.  
  
    -   Это имя должно быть уникальным среди всех имен каталогов FileTable в базе данных. Проверка уникальности выполняется без учета регистра, независимо от текущих параметров сортировки.  
  
    -   Если при создании таблицы FileTable не указано имя каталога, то в качестве имени каталога используется имя самой таблицы FileTable.  
  
2.  **FILETABLE_COLLATE_FILENAME**. Указывает имя параметров сортировки, применяемых к столбцу **Name** в таблице FileTable.  
  
    1.  Указанные параметры сортировки должны быть **нечувствительны к регистру** , чтобы соответствовать семантике имен файлов Windows.  
  
    2.  Если для параметра **FILETABLE_COLLATE_FILENAME**не указано значение или было задано значение **database_default**, столбец унаследует параметры сортировки текущей базы данных. Если в текущей базе данных используются параметры сортировки с учетом регистра, то операция **CREATE TABLE** завершится ошибкой.  
  
3.  Можно также указать имена, предназначенные для использования в трех первичных ключах и ограничениях уникальности, создаваемых автоматически. Если имена не будут предоставлены, то система сформирует имена, как описано ниже в этом разделе.  
  
    -   **FILETABLE_PRIMARY_KEY_CONSTRAINT_NAME**  
  
    -   **FILETABLE_STREAMID_UNIQUE_CONSTRAINT_NAME**  
  
    -   **FILETABLE_FULLPATH_UNIQUE_CONSTRAINT_NAME**  
  
 **Примеры**  
  
 В следующем примере рассмотрено создание новой таблицы FileTable с указанием значений, определяемых пользователем, для **FILETABLE_DIRECTORY** и **FILETABLE_COLLATE_FILENAME**.  
  
```sql  
CREATE TABLE DocumentStore AS FileTable  
    WITH (   
          FileTable_Directory = 'DocumentTable',  
          FileTable_Collate_Filename = database_default  
         );  
GO  
```  
  
 В следующем примере также создается новый FileTable. Определяемые пользователем значения не заданы, поэтому значение **FILETABLE_DIRECTORY** становится именем таблицы FileTable, значение **FILETABLE_COLLATE_FILENAME** становится равным database_default, а первичный ключ и ограничения уникальности принимают значения, сформированные системой.  
  
```sql  
CREATE TABLE DocumentStore AS FileTable;  
GO  
```  
  
 **Создание таблицы FileTable в среде SQL Server Management Studio**  
 В обозревателе объектов разверните объекты в выбранной базе данных, затем щелкните правой кнопкой мыши папку **Таблицы** и выберите **Создать FileTable**.  
  
 Этот параметр открывает новое окно скрипта, в котором содержится шаблон скрипта Transact-SQL, который можно настроить и выполнить с целью создания таблицы FileTable. Для простой настройки скрипта используйте параметр **Указать значения для параметров шаблона** в меню **Запрос** .  
  
###  <a name="requirements-and-restrictions-for-creating-a-filetable"></a><a name="ReqCreate"></a> Требования и ограничения для создания FileTable  
  
-   Существующую таблицу невозможно изменить, преобразовав ее в таблицу FileTable.  
  
-   Родительский каталог, предварительно указанный на уровне базы данных, должен иметь значение, отличное от NULL. Сведения об указании каталогов на уровне базы данных см. в разделе [Включение необходимых компонентов для таблицы FileTable](enable-the-prerequisites-for-filetable.md).  
  
-   Поскольку таблица FileTable содержит столбец FILESTREAM, требуется действующая файловая группа FILESTREAM. При необходимости можно указать действующую файловую группу FILESTREAM в команде **CREATE TABLE** для создания таблицы FileTable. Если файловая группа не указана, то таблица FileTable использует файловую группу FILESTREAM по умолчанию для базы данных. Если база данных не содержит файловую группу FILESTREAM, то возникнет ошибка.  
  
-   Невозможно создать ограничение таблицы в составе инструкции **CREATE TABLE…AS FILETABLE**. Однако можно добавить ограничение позже с помощью инструкции **ALTER TABLE** .  
  
-   Невозможно создать FileTable в базе данных **tempdb** или любой другой системной базе данных.  
  
-   Невозможно создать таблицу FileTable как временную таблицу.  
  
##  <a name="altering-a-filetable"></a><a name="BasicsAlter"></a> изменение таблицы FileTable  
 Поскольку FileTable имеет предопределенную и фиксированную схему, добавлять и изменять столбцы в ней нельзя. Тем не менее в таблицу FileTable можно добавлять пользовательские индексы, триггеры, ограничения и другие параметры.  
  
 Сведения об использовании инструкции ALTER TABLE для включения или отключения пространства имен FileTable, включая системные ограничения, см. в разделе [Управление объектами FileTable](manage-filetables.md).  
  
###  <a name="how-to-change-the-directory-for-a-filetable"></a><a name="HowToChange"></a> Как изменить каталог для таблицы FileTable  
 **Изменение каталога для таблицы FileTable с помощью Transact-SQL**  
 Вызовите инструкцию ALTER TABLE и задайте новое допустимое значение параметра **FILETABLE_DIRECTORY** SET.  
  
 **Пример**  
  
```sql  
ALTER TABLE filetable_name  
    SET ( FILETABLE_DIRECTORY = N'directory_name' );  
GO  
```  
  
 **Изменение каталога для таблицы FileTable с помощью среды SQL Server Management Studio**  
 Щелкните правой кнопкой мыши таблицу FileTable в обозревателе объектов и выберите пункт **Свойства** , чтобы открыть диалоговое окно **Свойства таблицы** . На странице **FileTable** введите новое значение для свойства **Имя каталога FileTable**.  
  
###  <a name="requirements-and-restrictions-for-altering-a-filetable"></a><a name="ReqAlter"></a> Требования и ограничения для изменения FileTable  
  
-   Изменить значение **FILETABLE_COLLATE_FILENAME**невозможно.  
  
-   Нельзя изменить, удалить или отключить системные столбцы в таблице FileTable.  
  
-   Нельзя добавлять новые пользовательские столбцы, вычисляемые или материализованные вычисляемые столбцы в таблицу FileTable.  
  
##  <a name="dropping-a-filetable"></a><a name="BasicsDrop"></a> удаление таблицы FileTable  
 Таблицу FileTable можно удалить с помощью обычного синтаксиса инструкции [DROP TABLE (Transact-SQL)](/sql/t-sql/statements/drop-table-transact-sql).  
  
 При удалении таблицы FileTable также удаляются следующие объекты:  
  
-   Все столбцы и объекты, связанные с таблицей, например индексы, ограничения и триггеры также удаляются.  
  
-   Каталог таблицы FileTable и вложенные каталоги удаляются из файла FILESTREAM и иерархии каталогов базы данных.  
  
 Команда DROP TABLE завершается ошибкой, если в пространстве имен файлов FileTable имеются открытые дескрипторы файлов. Сведения о закрытии открытых дескрипторов см. в разделе [Управление объектами FileTable](manage-filetables.md).  
  
##  <a name="other-database-objects-are-created-when-you-create-a-filetable"></a><a name="BasicsOtherObjects"></a> другие объекты базы данных, создаваемые при создании таблицы FileTable  
 При создании новой таблицы FileTable также создаются некоторые системные индексы и ограничения. Эти объекты нельзя изменять или удалять, они исчезают только после удаления самой таблицы FileTable. Чтобы просмотреть список этих объектов, отправьте запрос представлению каталога [sys.filetable_system_defined_objects (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-filetable-system-defined-objects-transact-sql).  
  
```sql  
--View all objects for all filetables, unsorted  
SELECT * FROM sys.filetable_system_defined_objects;  
GO  
  
--View sorted list with friendly names  
SELECT OBJECT_NAME(parent_object_id) AS 'FileTable', OBJECT_NAME(object_id) AS 'System-defined Object'  
    FROM sys.filetable_system_defined_objects  
    ORDER BY FileTable, 'System-defined Object';  
GO  
```  
  
 **Индексы, которые создаются при создании новой таблицы FileTable**  
 При создании новой таблицы FileTable также создаются следующие системные индексы.  
  
|||  
|-|-|  
|**Столбцы**|**Тип индекса**|  
|[path_locator] ASC|Первичный ключ, некластеризованный|  
|[parent_path_locator] ASC,<br /><br /> [name] ASC|Уникальный, некластеризованный|  
|[stream_id] ASC|Уникальный, некластеризованный|  
  
 **Ограничения, которые создаются при создании новой таблицы FileTable**  
 При создании новой таблицы FileTable также создаются следующие системные ограничения.  
  
|Ограничения|Принудительно применяет|  
|-----------------|--------------|  
|Ограничения по умолчанию для следующих столбцов:<br /><br /> **creation_time** <br /> **is_archive** <br /> **is_directory** <br /> **is_hidden** <br /> **is_offline** <br /> **is_readonly** <br /> **is_system** <br /> **is_temporary** <br /> **last_access_time** <br /> **last_write_time** <br /> **path_locator** <br /> **stream_id**|Системные ограничения по умолчанию используют значения по умолчанию для указанных столбцов.|  
|Проверочные ограничения|Системные проверочные ограничения обеспечивают следующие требования.<br /><br /> Допустимые имена файлов.<br /><br /> Допустимые атрибуты файлов.<br /><br /> Родительский объект должен быть каталогом.<br /><br /> При обработке файла иерархия пространств имен заблокирована.|  
  
 **Соглашение об именах для системных ограничений**  
 Системные ограничения, описанные выше, должны именоваться в формате **\<constraintType>_\<tablename>[\_\<columnname>]\_\<uniquifier>** , где:  
  
-   *<тип_ограничения>* может быть равен CK (проверочное ограничение), DF (ограничение по умолчанию), FK (внешний ключ), PK (первичный ключ) или UQ (ограничение уникальности).  
  
-   *\<uniquifier>*  — это формируемая системой строка, уникальным образом идентифицирующая ограничение. Эта строка может содержать имя таблицы FileTable и уникальный идентификатор.  
  
## <a name="see-also"></a>См. также:  
 [Управление таблицами FileTable](manage-filetables.md)  
  
  
