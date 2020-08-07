---
title: Сопоставление типов данных для издателей Oracle | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Oracle publishing [SQL Server replication], data type mapping
- data types [SQL Server replication], Oracle publishing
- mapping data types [SQL Server replication]
ms.assetid: 6da0e4f4-f252-4b7e-ba60-d2e912aa278e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 587aeff9d69dfac959329b6efc2c7a7f1eea715f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733938"
---
# <a name="data-type-mapping-for-oracle-publishers"></a>Сопоставление типов данных для издателей Oracle
  Типы данных Oracle и типы данных [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] не всегда полностью совпадают. Там, где это возможно, выбор подходящего типа данных при публикации таблицы Oracle осуществляется автоматически. В случаях, когда выбор однозначного соответствия типов данных не очевиден, предлагаются альтернативные сопоставления типов данных. Сведения о выборе альтернативных соответствий типов данных см. ниже в разделе «Указание альтернативных сопоставлений типов данных».  
  
 Следующая таблица показывает, как по умолчанию осуществляется преобразование типов данных между Oracle и [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , когда данные передаются издателем Oracle распространителю [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . В столбце «Альтернатива» показано, допустимы ли альтернативные соответствия.  
  
|Тип данных Oracle|Тип данных SQL Server|Альтернативные варианты|  
|----------------------|--------------------------|------------------|  
|BFILE|VARBINARY(MAX)|Да|  
|BLOB|VARBINARY(MAX)|Да|  
|CHAR([1-2000])|CHAR([1-2000])|Да|  
|CLOB|VARCHAR(MAX)|Да|  
|DATE|DATETIME|Да|  
|FLOAT|FLOAT|Нет|  
|FLOAT([1-53])|FLOAT([1-53])|Нет|  
|FLOAT([54-126])|FLOAT|Нет|  
|INT|NUMERIC(38)|Да|  
|INTERVAL|DATETIME|Да|  
|LONG|VARCHAR(MAX)|Да|  
|LONG RAW|IMAGE|Да|  
|NCHAR([1-1000])|NCHAR([1-1000])|Нет|  
|NCLOB|NVARCHAR(MAX)|Да|  
|NUMBER|FLOAT|Да|  
|NUMBER([1-38])|NUMERIC([1-38])|Нет|  
|NUMBER([0-38],[1-38])|NUMERIC([0-38],[1-38])|Да|  
|NVARCHAR2([1-2000])|NVARCHAR([1-2000])|Нет|  
|RAW([1-2000])|VARBINARY([1-2000])|Нет|  
|real|FLOAT|Нет|  
|ROWID|CHAR(18)|Нет|  
|timestamp|DATETIME|Да|  
|TIMESTAMP(0-7)|DATETIME|Да|  
|TIMESTAMP(8-9)|DATETIME|Да|  
|TIMESTAMP(0-7) WITH TIME ZONE|VARCHAR(37)|Да|  
|TIMESTAMP(8-9) WITH TIME ZONE|VARCHAR(37)|Нет|  
|TIMESTAMP(0-7) WITH LOCAL TIME ZONE|VARCHAR(37)|Да|  
|TIMESTAMP(8-9) WITH LOCAL TIME ZONE|VARCHAR(37)|Нет|  
|UROWID|CHAR(18)|Нет|  
|VARCHAR2([1-4000])|VARCHAR([1-4000])|Да|  
  
## <a name="considerations-for-data-type-mapping"></a>Вопросы сопоставления типов данных  
 При репликации данных из базы данных Oracle нужно помнить о следующих особенностях типов данных.  
  
### <a name="unsupported-data-types"></a>Неподдерживаемые типы данных  
 Следующие типы данных не поддерживаются; столбцы, имеющие эти типы, невозможно реплицировать.  
  
-   Типы Object  
  
-   Типы XML  
  
-   Типы Varray  
  
-   Вложенные таблицы;  
  
-   Столбцы, использующие REF  
  
### <a name="the-date-data-type"></a>Тип данных DATE  
 Даты в диапазоне [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] от 1753 нашей эры. до 9999 г. нашей эры, тогда как даты в Oracle распределяются в диапазоне от 4712 г. до нашей эры до 4712 г. нашей эры. Если столбец, имеющий тип DATE, содержит значения, выходящие за диапазон SQL Server, выберите для столбца альтернативный тип данных, которым является VARCHAR(19).  
  
### <a name="float-and-number-types"></a>Типы FLOAT и NUMBER  
 Масштаб и точность, задаваемые при сопоставлении типов данных FLOAT и NUMBER, зависят от масштаба и точности, указанных для столбца, использующего этот тип данных в базе данных Oracle. Точность представляет собой количество цифр в числе. Масштаб представляет собой количество цифр справа от десятичной запятой в числе. Например, у числа 123,45 точность равна 5, а масштаб равен 2.  
  
 Oracle позволяет определять числа, имеющие масштаб больший, чем точность, например NUMBER(4,5), в то время как [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] требует, чтобы точность была не меньше масштаба. Чтобы исключить усечение данных, когда в данных издателя Oracle масштаб больше, чем точность, при преобразовании данных точность приравнивается к масштабу: тип данных NUMBER(4,5) преобразуется в NUMERIC(5,5).  
  
> [!NOTE]  
>  Если для типа NUMBER не указать масштаб и точность, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] будет использовать по умолчанию максимальные масштаб (8) и точность (38). Для оптимизации хранения данных и производительности при репликации данных рекомендуется установить специальные значения масштаба и точности в Oracle.  
  
### <a name="large-object-types"></a>Типы больших объектов  
 Oracle поддерживает до 4 гигабайт (ГБ), в то время как SQL Server поддерживает до 2 ГБ. Реплицируемые данные свыше 2 ГБ усекаются.  
  
 Если таблица Oracle включает столбец типа BFILE, данные для этого столбца хранятся в файловой системе. Административной учетной записи репликации должно быть предоставлено право доступа в каталог, в котором хранятся данные. С этой целью должно использоваться следующее синтаксическое выражение:  
  
 `GRANT READ ON DIRECTORY <directory_name> TO <replication_administrative_user_schema>`  
  
 Дополнительные сведения о типах больших объектов см. в разделе с рекомендациями по большим объектам статьи [Рекомендации по структуре и ограничения для издателей Oracle](design-considerations-and-limitations-for-oracle-publishers.md).  
  
## <a name="specifying-alternative-data-type-mappings"></a>Указание альтернативных сопоставлений типов данных  
 Обычно целесообразно использовать сопоставление типов данных по умолчанию, но для многих типов данных Oracle вместо сопоставления по умолчанию можно выбрать тип данных из набора альтернативных вариантов. Существует два способа указания альтернативных сопоставлений:  
  
-   Переопределяйте значения по умолчанию для каждой статьи отдельно, используя хранимые процедуры или мастер создания публикаций.  
  
-   Глобальная замена значений по умолчанию для всех последующих статей с помощью хранимых процедур (значения по умолчанию для существующих статей не изменяются).  
  
 Чтобы указать альтернативные сопоставления типов данных, см. раздел [Указание сопоставления типов данных для издателя Oracle](../publish/specify-data-type-mappings-for-an-oracle-publisher.md).  
  
## <a name="see-also"></a>См. также:  
 [Настройка издателя Oracle](configure-an-oracle-publisher.md)   
 [Рекомендации по структуре и ограничения для издателей Oracle](design-considerations-and-limitations-for-oracle-publishers.md)   
 [Обзор публикации Oracle](oracle-publishing-overview.md)  
  
  
