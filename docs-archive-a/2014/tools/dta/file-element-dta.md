---
title: Элемент File (DTA) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- File element
ms.assetid: 73dce835-9a80-4aef-8e0f-9dcf07dd5b80
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0eeb2bdcc9513ca6283447daca63c8bbc4fa1726
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735750"
---
# <a name="file-element-dta"></a>Элемент File (DTA)
  Служит для указания файла рабочей нагрузки. Рабочая нагрузка представляет собой набор инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)] , выполняемый в одной или нескольких базах данных, которые необходимо настроить. Файлы рабочей нагрузки могут представлять собой скрипты [!INCLUDE[tsql](../../includes/tsql-md.md)] (SQL) или файлы трассировки (TRC). Дополнительные сведения см. в разделе [Запуск и использование помощника по настройке ядра СУБД](../../relational-databases/performance/start-and-use-the-database-engine-tuning-advisor.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
<DTAInput>  
  <Server>...</Server>  
  <Workload>  
    <File>...</File>  
  </Workload>  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|**Тип данных и длина**|Для задания пути к каталогу, в котором находится файл рабочей загрузки, используется тип данных `string`. Пример:<br /><br /> `<File>C:\Tuning\tun.sql</File>`<br /><br /> Ограничение на длину устанавливается сервером.|  
|**Значение по умолчанию**|Нет.|  
|**Наличие**|Необходимо наличие одного такого элемента, если не задан никакой другой тип рабочей нагрузки. Для родительского элемента **EventString**необходимо задать дочерний элемент **File**, **Database** или **Workload** , однако одновременно может использоваться только один из них. Например, если рабочая нагрузка задана элементом **File** , то в том же входном XML-файле уже нельзя задать рабочую нагрузку элементом **Database** .|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элементы|  
|------------------|--------------|  
|**Родительский элемент**|[Элемент Workload (DTA)](workload-element-dta.md)|  
|**Дочерние элементы**|Нет.|  
  
## <a name="example"></a>Пример  
 Пример использования этого элемента см. в разделе [Образец простого входного файла XML (DTA)](simple-xml-input-file-sample-dta.md).  
  
## <a name="see-also"></a>См. также:  
 [Справочник по входным XML-файлам (помощник по настройке ядра СУБД)](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
