---
title: Место хранения базы данных | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- databases [Analysis Services], storage location
ms.assetid: cf88c62e-581e-42f2-846f-a9bf1d7c3292
author: minewiskan
ms.author: owend
ms.openlocfilehash: ab370889396f40f52a348523e7f268892f549192
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730966"
---
# <a name="database-storage-location"></a>Место хранения базы данных
  Часто администратору базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] необходимо расположить определенную базу данных вне папки данных сервера. Обычно это связано с производственной необходимостью (например, чтобы повысить производительность или расширить хранилище). В этих ситуациях `DbStorageLocation` свойство Database позволяет [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] администратору базы данных указать расположение базы на локальном диске или сетевом устройстве.  
  
## <a name="dbstoragelocation-database-property"></a>Свойство DbStorageLocation базы данных  
 Свойство `DbStorageLocation` базы данных указывает папку, в которой службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] создают и хранят все файлы данных и метаданных, входящие в базу данных. Все файлы метаданных хранятся в папке `DbStorageLocation`, за исключением файла метаданных базы данных, который хранится в папке данных сервера. При изменении свойства `DbStorageLocation` базы данных следует руководствоваться следующими двумя важными соображениями.  
  
-   В свойстве базы данных `DbStorageLocation` должен быть задан путь к существующей папке в формате UNC или пустая строка. Пустая строка по умолчанию указывает на папку данных сервера. Если папка не существует, при выполнении команды `Create`, `Attach` или `Alter` возникнет ошибка.  
  
-   Свойство `DbStorageLocation` базы данных не может указывать на папку данных сервера или любую вложенную в нее папку. В противном случае при выполнении команды `Create`, `Attach` или `Alter` возникнет ошибка.  
  
> [!IMPORTANT]  
>  При использовании сети хранения данных (SAN), сети на основе iSCSI или локально подключенного диска рекомендуется указывать путь в формате UNC. Указание пути в формате UNC к сетевой папке или любым хранилищам с высокой задержкой сделает установку неподдерживаемой.  
  
### <a name="dbstoragelocation-compared-to-storagelocation"></a>Сравнение свойств DbStorageLocation и StorageLocation  
 Свойство `DbStorageLocation` указывает на папку, в которой находятся все файлы данных и метаданных, относящиеся к базе данных, тогда как свойство `StorageLocation` указывает на папку, в которой находятся одна или несколько секций куба. Свойство `StorageLocation` можно задать независимо от свойства `DbStorageLocation`. Администратор базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] принимает решение исходя из поставленной задачи, и зачастую применение того или иного свойства даст одни и те же результаты.  
  
## <a name="dbstoragelocation-usage"></a>Использование свойства DbStorageLocation  
 `DbStorageLocation`Свойство базы данных используется как часть `Create` команды базы данных в `Detach` / `Attach` последовательности команд базы данных, в `Backup` / `Restore` последовательности команд базы данных или в `Synchronize` команде базы данных. Изменение свойства `DbStorageLocation` связано со структурными изменениями объекта базы данных. Это означает, что все метаданные будут созданы повторно, а данные повторно обработаны.  
  
> [!IMPORTANT]  
>  Место хранения базы данных не следует изменять командой `Alter`. Вместо этого рекомендуется использовать последовательность `Detach` / `Attach` команд базы данных (см. раздел [Перемещение базы данных Analysis Services](move-an-analysis-services-database.md), [Присоединение и отсоединение Analysis Services баз данных](attach-and-detach-analysis-services-databases.md)).  
  
## <a name="see-also"></a>См. также:  
 [Microsoft. AnalysisServices. Database. DbStorageLocation *](/dotnet/api/microsoft.analysisservices.core.database.dbstoragelocation)   
 [Присоединение и отсоединение баз данных Analysis Services](attach-and-detach-analysis-services-databases.md)   
 [Перемещение базы данных Analysis Services](move-an-analysis-services-database.md)   
 [DbStorageLocation, элемент](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/dbstoragelocation-element)   
 [Создание элемента &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/create-element-xmla)   
 [Элемент Attach](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/attach-element)   
 [Элемент Synchronize (XMLA)](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/synchronize-element-xmla)  
  
  
