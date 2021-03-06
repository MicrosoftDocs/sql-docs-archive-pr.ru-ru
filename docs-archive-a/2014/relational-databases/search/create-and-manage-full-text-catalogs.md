---
title: Создание полнотекстовых каталогов и управление ими | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- full-text catalogs [SQL Server], creating
- full-text search [SQL Server], using SQL Server Management Studio
ms.assetid: 824b7131-44a6-4815-89e6-62b7bab060e3
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 18efd79bc34beee94d4edc61e9165a986edba90b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87668735"
---
# <a name="create-and-manage-full-text-catalogs"></a>Создание и управление полнотекстовыми каталогами
  Полнотекстовый каталог теперь является виртуальным объектом, не принадлежащим ни к одной файловой группе. Он является логическим понятием, ссылающимся на группу полнотекстовых индексов.  
  
##  <a name="creating-a-full-text-catalog"></a><a name="creating"></a>Создание полнотекстового каталога  
  
#### <a name="to-create-a-full-text-catalog"></a>Создание полнотекстового каталога  
  
1.  В обозревателе объектов разверните сервер, затем узел **Базы данных**, а затем — базу данных, в которой необходимо создать полнотекстовый каталог.  
  
2.  Разверните узел **Хранилище**, затем щелкните правой кнопкой мыши **Полнотекстовые каталоги**.  
  
3.  Выберите **Создание полнотекстового каталога**.  
  
4.  В диалоговом окне **Создание полнотекстового каталога** укажите сведения о вновь создаваемом каталоге. Дополнительные сведения см. в разделе [Создание полнотекстового каталога (страница "Общие")](../../integration-services/general-page-of-integration-services-designers-options.md).  
  
    > [!NOTE]  
    >  Идентификаторы полнотекстовых каталогов начинаются с 00005 и увеличиваются на единицу для каждого вновь создаваемого каталога.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
  
  
##  <a name="viewing-the-properties-of-a-full-text-catalog"></a><a name="props"></a>Просмотр свойств полнотекстового каталога  
 Для получения значений различных свойств полнотекстового индексирования можно использовать некоторые функции [!INCLUDE[tsql](../../includes/tsql-md.md)], например FULLTEXTCATALOGPROPERTY. Эти сведения полезны для администрирования и устранения нарушений в работе средств полнотекстового поиска.  
  
 В следующей таблице перечислены свойства, о которых сообщается в полнотекстовых каталогах.  
  
|Свойство|Описание|Компонент|  
|--------------|-----------------|--------------|  
|`AccentSensitivity`|Настройка учета диакритических знаков:|[FULLTEXTCATALOGPROPERTY](/sql/t-sql/functions/fulltextcatalogproperty-transact-sql)|  
|`ImportStatus`|Выполняется ли в настоящее время импорт полнотекстового каталога.|FULLTEXTCATALOGPROPERTY|  
|`IndexSize`|Размер полнотекстового каталога в мегабайтах (МБ).|FULLTEXTCATALOGPROPERTY|  
|`ItemCount`|Количество полнотекстовых индексированных элементов в полнотекстовом каталоге.|FULLTEXTCATALOGPROPERTY|  
|`MergeStatus`|Выполняется ли слияние в единый файл.|FULLTEXTCATALOGPROPERTY|  
|`PopulateCompletionAge`|Разница в секундах между завершением последнего заполнения полнотекстового индекса и 01/01/1990 00:00:00.|FULLTEXTCATALOGPROPERTY|  
|`PopulateStatus`|Состояние заполнения.<br /><br /> [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]|FULLTEXTCATALOGPROPERTY|  
|`UniqueKeyCount`|Количество уникальных ключей в полнотекстовом каталоге.|FULLTEXTCATALOGPROPERTY|  
  
  
  
##  <a name="rebuilding-a-full-text-catalog"></a><a name="rebuildone"></a>Перестроение полнотекстового каталога  
  
#### <a name="to-rebuild-a-full-text-catalog"></a>Перестроение полнотекстового каталога  
  
1.  В обозревателе объектов последовательно разверните узел сервера, затем **Базы данных**, а затем — базу данных, содержащую полнотекстовый каталог, который необходимо перестроить.  
  
2.  Разверните узел **Хранилище**, а затем **Полнотекстовые каталоги**.  
  
3.  Щелкните правой кнопкой мыши имя полнотекстового каталога, который необходимо перестроить, и выберите **Перестроить**.  
  
4.  На вопрос **Удалить полнотекстовый каталог и перестроить его?** нажмите кнопку **ОК**.  
  
5.  В диалоговом окне **Перестроить полнотекстовый каталог** нажмите кнопку **Закрыть**.  
  
  
  
##  <a name="rebuilding-all-full-text-catalogs-for-a-database"></a><a name="rebuildall"></a>Перестроение всех полнотекстовых каталогов для базы данных  
  
#### <a name="to-rebuild-the-full-text-catalogs-for-a-database"></a>Перестроение полнотекстовых каталогов базы данных  
  
1.  В обозревателе объектов последовательно разверните узел сервера, затем **Базы данных**, а затем базу данных, содержащую полнотекстовые каталоги, которые необходимо перестроить.  
  
2.  Разверните узел **Хранилище**, затем щелкните правой кнопкой мыши **Полнотекстовые каталоги**.  
  
3.  Выберите **Перестроить все**.  
  
4.  В ответ на запрос **Удалить все полнотекстовые каталоги и перестроить их?** нажмите кнопку **ОК**.  
  
5.  В диалоговом окне **Перестроить все полнотекстовые каталоги** нажмите **Закрыть**.  
  
  
  
##  <a name="removing-a-full-text-catalog-from-a-database"></a><a name="removing"></a>Удаление полнотекстового каталога из базы данных  
  
#### <a name="to-remove-a-full-text-catalog-from-a-database"></a>Удаление полнотекстового каталога из базы данных  
  
1.  В обозревателе объектов разверните узел сервера, затем **Базы данных**, а затем — базу данных, содержащую полнотекстовый каталог, который необходимо удалить.  
  
2.  Разверните узел **Хранилище**, а затем **Полнотекстовые каталоги**.  
  
3.  Щелкните правой кнопкой мыши полнотекстовый каталог, который необходимо удалить, и выберите в меню пункт **Удалить**.  
  
4.  В диалоговом окне **Удаление объектов** нажмите кнопку **ОК**.  
  
  
  
## <a name="see-also"></a>См. также:  
 [CREATE FULLTEXT CATALOG (Transact-SQL)](/sql/t-sql/statements/create-fulltext-catalog-transact-sql)  
  
  
