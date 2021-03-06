---
title: Свойства базы данных (страница "Параметры") | Документация Майкрософт
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.databaseproperties.options.f1
ms.assetid: a3447987-5507-4630-ac35-58821b72354d
author: stevestein
ms.author: sstein
ms.openlocfilehash: e856e820719054ad1f01fe0e0306aa278d62ec2c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731713"
---
# <a name="database-properties-options-page"></a>Свойства базы данных (страница «Параметры»)
  Эта страница используется для изменения параметров выделенной базы данных. Дополнительные сведения о параметрах, доступных на этой странице, см. в разделе [Параметры ALTER DATABASE SET &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options).  
  
## <a name="page-header"></a>Заголовок страницы  
 **Параметры сортировки**  
 Задайте параметры сортировки для базы данных, выбрав из списка. Дополнительные сведения см. в разделе [Set or Change the Database Collation](../collations/set-or-change-the-database-collation.md).  
  
 **Модель восстановления**  
 Укажите одну из следующих моделей для восстановления базы данных: **Полная**, **С неполным протоколированием** или **Простая**. Дополнительные сведения о моделях восстановления см. в разделе [Модели восстановления (SQL Server)](../backup-restore/recovery-models-sql-server.md).  
  
 **Уровень совместимости**  
 Укажите последнюю версию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , которую поддерживает база данных. Возможные значения:  **SQL Server 2014 (120)**,  **SQL Server 2012 (110)** и **SQL Server 2008 (100)**. При обновлении базы данных SQL Server 2005 до версии SQL Server 2014 уровень совместимости для этой базы данных изменяется от 90 до 100.  Уровень совместимости 90 не поддерживается в SQL Server 2014. Дополнительные сведения см. в разделе [Уровень совместимости инструкции ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level).  
  
 **Тип включения**  
 Указывайте «none» или «partial», чтобы обозначить, что это автономная база данных. Дополнительные сведения об автономных базах данных см. в разделе [Автономные базы данных](contained-databases.md). Свойство сервера **Разрешить автономные базы данных** должно иметь значение **TRUE** , прежде чем базу данных можно будет настроить как автономную.  
  
> [!IMPORTANT]  
>  Включение частично автономных баз данных передает управление над доступом к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] владельцам базы данных. Дополнительные сведения см. в разделе [Security Best Practices with Contained Databases](security-best-practices-with-contained-databases.md).  
  
## <a name="automatic"></a>Автоматически  
 **Автоматическое закрытие**  
 Укажите, будет ли база данных закрываться полностью и освобождать ресурсы после выхода последнего пользователя. Возможные значения: `True` и `False`. При значении `True` база данных отключается и ее ресурсы освобождаются, как только последний пользователь выходит из системы.  
  
 Автоматическое добавочное создание статистики  
 Укажите, следует ли использовать добавочное создание при создании статистики для каждой секции. Сведения о добавочной статистике см. в разделе [CREATE STATISTICS (Transact-SQL)](/sql/t-sql/statements/create-statistics-transact-sql).  
  
 **Автоматическое создание статистики**  
 Укажите, будет ли база данных автоматически создавать отсутствующие статистические данные оптимизации. Возможные значения: `True` и `False`. При значении `True` любые статистические данные, необходимые для оптимизации запроса, автоматически выстраиваются в процессе оптимизации. Дополнительные сведения см. в статье [CREATE STATISTICS (Transact-SQL)](/sql/t-sql/statements/create-statistics-transact-sql).  
  
 **Автоматическое сжатие**  
 Укажите, будут ли файлы базы данных доступны для периодического сжатия. Возможные значения: `True` и `False`. Дополнительные сведения см. в разделе [Shrink a Database](shrink-a-database.md).  
  
 **Автоматическое обновление статистики**  
 Укажите, будет ли база данных автоматически обновлять устаревшие статистические данные оптимизации. Возможные значения: `True` и `False`. При значении `True` любые устаревшие статистические данные, необходимые для оптимизации запроса, автоматически выстраиваются в процессе оптимизации. Дополнительные сведения см. в статье [CREATE STATISTICS (Transact-SQL)](/sql/t-sql/statements/create-statistics-transact-sql).  
  
 **Асинхронное автоматическое обновление статистики**  
 При значении `True` запросы, инициирующие автоматическое обновление устаревшей статистики, не будут ждать обновления статистики перед компиляцией. Последующие запросы будут использовать обновленную статистику, когда она будет доступна.  
  
 Когда `False` , запросы, инициирующие автоматическое обновление устаревшей статистики, ожидают, пока обновленная статистика не будет использована в плане оптимизации запросов.  
  
 Установка этого параметра в значение `True` не оказывает влияния, если для параметра **Автоматическое обновление статистики** также не задано значение `True` .  
  
## <a name="containment"></a>Containment  
 В автономных базах данных некоторые параметры, обычно настраиваемые на уровне сервера, можно настроить на уровне базы данных.  
  
 **Код языка полнотекстового поиска по умолчанию**  
 Укажите язык, используемый по умолчанию для полнотекстовых индексированных столбцов. Лингвистический анализ полнотекстовых индексированных данных зависит от языка данных. Значением по умолчанию для этого параметра является язык сервера. Дополнительные сведения о языке, соответствующем отображаемой настройке, см. в разделе [sys.fulltext_languages (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql).  
  
 **Язык по умолчанию**  
 Язык по умолчанию для всех новых пользователей автономной базы данных, если не указано иное.  
  
 **Включены вложенные триггеры**  
 Разрешает триггерам вызывать срабатывание других триггеров. Вложенность триггеров может достигать максимум 32 уровня. Дополнительные сведения см. в подразделе "Вложенные триггеры" раздела [CREATE TRIGGER (Transact-SQL)](/sql/t-sql/statements/create-trigger-transact-sql).  
  
 **Преобразование пропускаемых слов**  
 Подавляет сообщение об ошибке, если логическая операция по полнотекстовому запросу возвращает нулевые значения из-за пропускаемых слов (стоп-слов). Дополнительные сведения см. в разделе [transform noise words Server Configuration Option](../../database-engine/configure-windows/transform-noise-words-server-configuration-option.md).  
  
 **Отсечение двух цифр года**  
 Указывает максимальное значение года, которое можно задать двумя цифрами. Указанный год и предыдущие 99 лет можно задавать двумя цифрами. Все другие года нужно вводить четырьмя цифрами.  
  
 Например, значение по умолчанию 2049 указывает, что дата, введенная в виде «3/14/49», будет интерпретироваться как 14 марта 2049, а дата, введенная в виде «3/14/50» будет интерпретироваться как 14 марта 1950. Дополнительные сведения см. в статье [Настройка параметра конфигурации сервера two digit year cutoff](../../database-engine/configure-windows/configure-the-two-digit-year-cutoff-server-configuration-option.md).  
  
## <a name="cursor"></a>Курсор  
 **Закрывать курсор при разрешении фиксации**  
 Укажите, будет ли курсор закрываться после фиксации транзакции, открывшей этот курсор. Возможные значения: `True` и `False`. При значении `True` любые курсоры, открытые на момент фиксации или отката транзакции, закрываются. При значении `False` такие курсоры остаются открытыми после фиксации транзакции. При значении `False` откат транзакции вызывает закрытие любых курсоров, за исключением тех, что определены как INSENSITIVE или STATIC. Дополнительные сведения см. в разделе [SET CURSOR_CLOSE_ON_COMMIT (Transact-SQL)](/sql/t-sql/statements/set-cursor-close-on-commit-transact-sql).  
  
 **Курсор по умолчанию**  
 Задайте поведение курсора по умолчанию. При значении `True` при объявлении курсоров им по умолчанию присваивается состояние LOCAL. Когда `False` , [!INCLUDE[tsql](../../includes/tsql-md.md)] курсоры по умолчанию имеют значение Global.  
  
## <a name="filestream"></a>FILESTREAM  
 **Имя каталога FILESTREAM**  
 Укажите имя каталога для данных FILESTREAM, связанных с выбранной базой данных.  
  
 **Нетранзакционный доступ к файловому потоку**  
 Укажите один из следующих параметров для нетранзакционного доступа через файловую систему к данным FILESTREAM, хранящимся в FileTables: **OFF**, **READ_ONLY** или **FULL**. Если на сервере не включена поддержка FILESTREAM, это значение устанавливается в OFF и отключается. Дополнительные сведения см в разделе [FileTables (SQL Server)](../blob/filetables-sql-server.md).  
  
## <a name="miscellaneous"></a>Разное  
 **ANSI NULL по умолчанию**  
 Разрешение применять значения NULL для всех определяемых пользователем типов данных или столбцов, которые не определены явно как `NOT NULL` в инструкции `CREATE TABLE` или `ALTER TABLE` (состояние по умолчанию). Дополнительные сведения см. в разделах [SET ANSI_NULL_DFLT_ON (Transact-SQL)](/sql/t-sql/statements/set-ansi-null-dflt-on-transact-sql) и [SET ANSI_NULL_DFLT_OFF (Transact-SQL)](/sql/t-sql/statements/set-ansi-null-dflt-off-transact-sql).  
  
 **Включены ANSI NULL**  
 Задание поведения операторов сравнения «равно» (`=`) и «не равно» (`<>`) при использовании со значениями NULL. Возможные значения: `True` (on) и `False` (OFF). При значении `True` все сравнения со значением NULL вычисляются в UNKNOWN. При `False` сравнении значений, отличных от Юникода, со значением NULL вычисляется `True` , если оба значения равны NULL. Дополнительные сведения см. в разделе [SET ANSI_NULLS (Transact-SQL)](/sql/t-sql/statements/set-ansi-nulls-transact-sql).  
  
 **Включено заполнение ANSI**  
 Укажите, включено ли заполнение ANSI. Допустимые значения: `True` (on) и `False` (OFF). Дополнительные сведения см. в разделе [SET ANSI_PADDING (Transact-SQL)](/sql/t-sql/statements/set-ansi-padding-transact-sql).  
  
 **Включены предупреждения ANSI**  
 Укажите поведение по стандарту ISO для некоторых условий возникновения ошибок. При значении `True` создается предупреждающее сообщение, если в агрегатных функциях (например, Sum, AVG, Max, min, STDEV, STDEVP, var, ДИСПР или Count) отображаются значения NULL. Если `False` задано, предупреждение не выдается. Дополнительные сведения см. в разделе [SET ANSI_WARNINGS (Transact-SQL)](/sql/t-sql/statements/set-ansi-warnings-transact-sql).  
  
 **Включено прерывание при делении на ноль**  
 Укажите, включен ли параметр, разрешающий аварийное прерывание арифметических действий. Возможные значения: `True` и `False`. При значении `True` переполнение или ошибка деления на ноль приводит к прекращению выполнения запроса или пакета. Если произошла ошибка в транзакции, для этой транзакции выполняется откат. При значении `False` предупреждающее сообщение отображается, но запрос, пакет или транзакция продолжают выполняться, как если бы ошибки не произошло. Дополнительные сведения см. в разделе [SET ARITHABORT (Transact-SQL)](/sql/t-sql/statements/set-arithabort-transact-sql).  
  
 **Объединение со значением NULL дает NULL**  
 Задайте способ объединения значений NULL. Если свойство имеет значение `True` , `string` + NULL возвращает значение null. Если `False` значение равно, то результатом является `string` . Дополнительные сведения см. в разделе [SET CONCAT_NULL_YIELDS_NULL (Transact-SQL)](/sql/t-sql/statements/set-concat-null-yields-null-transact-sql).  
  
 **Включены межбазовые цепочки владения**  
 Это значение только для чтения указывает, включен ли параметр межбазовых цепочек владения. При `True` этом база данных может быть источником или целевым объектом межбазовой цепочки владения. Чтобы установить этот параметр, используйте инструкцию ALTER DATABASE.  
  
 **Включена оптимизация корреляции дат**  
 При `True` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] этом поддерживает статистику корреляции между любыми двумя таблицами в базе данных, которые связаны ограничением внешнего ключа и имеют `datetime` столбцы.  
  
 При `False` этом статистика корреляции не сохраняется.  
  
 **Автоокругление чисел**  
 Задайте способ обработки ошибок округления базой данных. Возможные значения: `True` и `False`. При значении `True` выдается ошибка, если происходит потеря точности в выражении. Когда `False` , потери точности не создают сообщений об ошибках, а результат округляется до точности столбца или переменной, в которой хранится результат. Дополнительные сведения см. в разделе [SET NUMERIC_ROUNDABORT (Transact-SQL)](/sql/t-sql/statements/set-numeric-roundabort-transact-sql).  
  
 **Определение параметров**  
 Если выбрано значение **SIMPLE**, параметризация запросов выполняется на основе режима базы данных по умолчанию. Если выбрано значение **FORCED**, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполняет параметризацию всех запросов в базе данных.  
  
 **Включены заключенные в кавычки идентификаторы**  
 Укажите, можно ли использовать ключевые слова [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] как идентификаторы (имена объектов или переменных), если они заключены в кавычки. Возможные значения: `True` и `False`. Дополнительные сведения см. в статье [SET QUOTED_IDENTIFIER (Transact-SQL)](/sql/t-sql/statements/set-quoted-identifier-transact-sql).  
  
 **Включены рекурсивные триггеры**  
 Укажите, могут ли триггеры запускаться другими триггерами. Возможные значения: `True` и `False`. Если задано значение `True` , это обеспечивает рекурсивное срабатывание триггеров. Если задано значение `False` , запрещается только прямая рекурсия. Чтобы отключить косвенную рекурсию, присвойте параметру сервера вложенные триггеры значение 0, используя процедуру sp_configure. Дополнительные сведения см. в разделе [Создание вложенных триггеров](../triggers/create-nested-triggers.md).  
  
 `Trustworthy`  
 При отображении `True` этот параметр только для чтения указывает, что [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] разрешает доступ к ресурсам за пределами базы данных в контексте олицетворения, установленном в базе данных. Контекст олицетворения для базы данных можно установить при помощи пользовательской инструкции EXECUTE AS или предложения EXECUTE AS в модулях базы данных.  
  
 Чтобы получить доступ, владелец базы данных также должен иметь разрешение AUTHENTICATE SERVER на уровне сервера.  
  
 Это свойство также разрешает создание и выполнение небезопасных и внешних сборок в базе данных. Владелец базы данных должен задать для этого свойства значение `True`. В дополнение к этому, он должен обладать разрешением EXTERNAL ACCESS ASSEMBLY или UNSAFE ASSEMBLY на уровне сервера.  
  
 По умолчанию все пользовательские базы данных и все системные базы данных (за исключением **msdb**) имеют для этого свойства значение `False` . Оно не изменяется для баз данных **model** и **tempdb** .  
  
 TRUSTWORTHY устанавливается в значение `False` всякий раз, когда база данных присоединяется к серверу.  
  
 Для получения доступа к ресурсам вне базы данных в контексте олицетворения рекомендуется использовать сертификаты и подписи вместе с параметром `Trustworthy`.  
  
 Это свойство задается с помощью инструкции ALTER DATABASE.  
  
 **Включен формат хранения VarDecimal**  
 Этот параметр доступен только для чтения, начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] версии и более поздних версий. для всех баз данных включен формат хранения vardecimal. Для этого параметра используется хранимая процедура [sp_db_vardecimal_storage_format](/sql/relational-databases/system-stored-procedures/sp-db-vardecimal-storage-format-transact-sql).  
  
## <a name="recovery"></a>Восстановление  
 **Проверка страниц**  
 Задайте параметр, использующийся для обнаружения незавершенных транзакций ввода-вывода, вызванных ошибками ввода-вывода диска, и уведомления о таких транзакциях. Возможные значения: **None**, **TornPageDetection**и **Checksum**. Дополнительные сведения см. в разделе [Управление таблицей suspect_pages (SQL Server)](../backup-restore/manage-the-suspect-pages-table-sql-server.md).  
  
 **Целевое время восстановления (в секундах)**  
 Указывает максимальное время, выраженное в секундах, для восстановления определенной базы данных в случае сбоя. Дополнительные сведения см. в разделе [Контрольные точки базы данных (SQL Server)](../logs/database-checkpoints-sql-server.md).  
  
## <a name="state"></a>Состояние  
 **База данных только для чтения**  
 Укажите, будет ли база данных доступна только для чтения. Возможные значения: `True` и `False`. При значении `True` пользователи могут только считывать данные в базе данных. Им не разрешается изменять данные или объекты базы данных. Тем не менее саму базу данных можно удалить, используя инструкцию DROP DATABASE. Базу данных нельзя использовать, когда задается новое значение параметра **База данных только для чтения** . Исключением является база данных master, и только системный администратор может использовать базу данных master во время задания параметра.  
  
 **Состояние базы данных**  
 Выводит текущее состояние базы данных. Она не подлежит редактированию. Дополнительные сведения о параметре **Состояние базы данных**см. в разделе [Database States](database-states.md).  
  
 **Ограничение доступа**  
 Укажите, какие пользователи имеют доступ к базе данных. Возможны следующие значения:  
  
-   **несколько**  
  
     Нормальное состояние производственной базы данных, позволяет нескольким пользователям получать одновременный доступ к базе данных.  
  
-   **Один**  
  
     Используется для операций обслуживания, одновременный доступ к базе данных получает только один пользователь.  
  
-   **Ограниченный**  
  
     Базу данных могут использовать только члены ролей db_owner, dbcreator или sysadmin.  
  
 **Шифрование включено**  
 При `True` этом для этой базы данных включено шифрование базы данных. Ключ шифрования базы данных необходим для шифрования. Дополнительные сведения см. в статье [Прозрачное шифрование данных (TDE)](../security/encryption/transparent-data-encryption.md).  
  
## <a name="see-also"></a>См. также:  
 [ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql)   
 [CREATE DATABASE (SQL Server Transact-SQL)](/sql/t-sql/statements/create-database-sql-server-transact-sql)  
  
  
