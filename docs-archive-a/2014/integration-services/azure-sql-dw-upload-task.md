---
title: Задача отправки информации в хранилище данных SQL Azure | Документы Майкрософт
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL12.DTS.DESIGNER.AFPDWUPTASK.F1
- SQL11.DTS.DESIGNER.AFPDWUPTASK.F1
ms.assetid: 112cf764-f85a-4c1a-b732-d299d717c0d4
author: yualan
ms.author: chugu
ms.openlocfilehash: d90cc36b5e8beb35313b76ecef2ed95f065dcb89
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87656534"
---
# <a name="azure-sql-dw-upload-task"></a>Задача отправки информации в хранилище данных SQL Azure
**Задача отправки информации в хранилище данных SQL Azure** позволяет отправить локальные данные в таблицу хранилища данных SQL Azure с использованием пакета SSIS. В настоящее время в качестве формата исходного файла данных поддерживается текст с разделителями в кодировке UTF-8. Процесс передачи соответствует эффективному подходу Polybase. В частности, данные сначала будут переданы в хранилище BLOB-объектов Azure и лишь затем в хранилище данных SQL Azure. Поэтому для использования этой задачи требуется учетная запись хранилища BLOB-объектов Azure.

Чтобы добавить **задачу отправки информации в хранилище данных SQL Azure**, перетащите ее из панели элементов служб SSIS на холст конструктора и дважды щелкните ее (или щелкните ее правой кнопкой мыши), а затем выберите команду **Изменить** , чтобы открыть диалоговое окно редактора задач.

На странице **Общие** настройте следующие свойства.

Поле|Description
-----|-----------
LocalDirectory|Указывает локальный каталог с файлами данных для отправки.
Рекурсивно|Указывает, выполнять ли рекурсивный поиск в подкаталогах.
FileName|Указывает фильтр имен для выбора файлов с определенным именем. Пример: при указании MySheet*.xls\* будут выбраны такие файлы, как MySheet001.xls и MySheetABC.xlsx.
RowDelimiter|Указывает символы, обозначающие конец строки.
ColumnDelimiter|Указывает символы, обозначающие конец столбца. Пример: &#124; (вертикальная черта), \t (табуляция), ' (одинарная кавычка), " (двойная кавычка) и 0x5c (обратная косая черта).
IsFirstRowHeader|Указывает, содержит ли первая строка каждого файла данных названия столбцов, а не фактические данные.
AzureStorageConnection|Указывает диспетчер подключений службы хранилища Azure.
BlobContainer|Задает название контейнера больших двоичных объектов, в который будут переданы локальные данные (и который будет использоваться для их ретрансляции в хранилище данных Azure через PolyBase). Если контейнер не существует, он будет создан.
BlobDirectory|Задает название каталога больших двоичных объектов (виртуальной иерархической структуры), в который будут переданы локальные данные (и который будет использоваться для их ретрансляции в хранилище данных Azure через PolyBase).
RetainFiles|Указывает, следует ли сохранить файлы, переданные в службу хранилища Azure.
CompressionType|Указывает формат сжатия, используемый при передаче файлов в службу хранилища Azure. Сжатие не влияет на локальный источник.
CompressionLevel|Указывает уровень сжатия, используемый в рамках формата сжатия.
AzureDwConnection|Указывает диспетчер соединений ADO.NET для хранилища данных SQL Azure.
TableName|Указывает название целевой таблицы. Выберите существующую таблицу или создайте новую, выбрав пункт **\<New Table ...>** .
TableDistribution|Указывает метод распределения данных для новой таблицы. Применяется, если для **TableName**указано название новой таблицы.
HashColumnName|Указывает столбец, используемый для распределения данных посредством хэш-таблицы. Применяется, если для **TableDistribution** указано значение **HASH**.

Содержимое страницы **Сопоставления** изменяется в зависимости от того, отправляются ли данные в новую таблицу или существующую. В первом случае необходимо будет настроить сопоставляемые исходные столбцы и соответствующие им названия целевых столбцов в создаваемой целевой таблице. Во втором случае необходимо сопоставить исходные и целевые столбцы.

На странице **Столбцы** необходимо настроить свойства типов данных для каждого исходного столбца.

На странице **T-SQL** отображается код T-SQL, используемый для передачи данных из хранилища BLOB-объектов Azure в хранилище данных SQL Azure. Этот код создается автоматически на основе параметров конфигурации, выбранных на других страницах, и будет исполняться в ходе выполнения задачи. Вы можете вручную изменить созданный код T-SQL, если нужно, нажав кнопку **Изменить** . Чтобы позже вернуться к исходному коду (первоначально созданному автоматически), нажмите кнопку **Сброс** .
