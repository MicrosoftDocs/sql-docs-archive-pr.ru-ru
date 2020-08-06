---
title: Диалоговое окно "Свойства набора данных", "Параметры" | Документация Майкрософт
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10130"
- sql12.rtp.rptdesigner.datasetproperties.options.f1
ms.assetid: 95299049-71ba-427f-b723-775cb696243f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 778365e8fc7f40700b0f8c1683260f15c860a32a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87668667"
---
# <a name="dataset-properties-dialog-box-options"></a>Диалоговое окно «Свойства набора данных» — «Настройки»
  Выберите **Параметры** в диалоговом окне **датасетпропертиес** , чтобы изменить параметры данных, такие как параметры сортировки и подытоги, для запроса. Дополнительные сведения см. в статье [Collation and Unicode Support](../relational-databases/collations/collation-and-unicode-support.md).  
  
## <a name="options"></a>Варианты  
 **Параметры сортировки**  
 Выберите локаль, который определяет параметры сортировки, используемые при сортировке данных. Значение**По умолчанию** указывает, что сервер отчетов при запуске отчета должен попытаться получить значение от поставщика данных. Если значение не удается получить, по умолчанию принимается значение, соответствующее локали компьютера.  
  
 **Учет регистра букв**  
 Выберите значение, которое определяет, учитывается ли регистр. Этот параметр указывает, учитывают ли данные регистр. Можно задать **чувствительность к регистру символов** **true**, **false**или **Auto**. Значение по умолчанию **Auto**указывает, что сервер отчетов должен попытаться получить значение от поставщика данных при выполнении отчета. Если поставщик данных не поддерживает данный тип учета регистра, то запрос выполняется, как если бы значением было **False**. Если известно значение и известно, что оно поддерживается, выберите значение **True**.  
  
 **Учитывать диакритические знаки**  
 Выберите значение, которое определяет учет диакритических знаков. **Чувствительность к диакритическим** знакам указывает, учитывают ли данные диакритические знаки, и может принимать значения **true**, **false**или **Auto**. Значение по умолчанию **Auto**указывает, что сервер отчетов должен попытаться получить значение от поставщика данных при выполнении отчета. Если поставщик данных не поддерживает данный тип учета диакритических знаков, то запрос выполняется, как если бы значением было **False**. Если известно значение и известно, что оно поддерживается, выберите значение **True**.  
  
 **Учитывать японскую азбуку**  
 Выберите значение, которое определяет, учитывать ли японскую азбуку. Этот параметр указывает, учитывают ли данные тип японской азбуки. для него можно задать значение **true**, **false**или **Auto**. Значение по умолчанию **Auto**указывает, что сервер отчетов должен попытаться получить значение от поставщика данных при выполнении отчета. Если поставщик данных не поддерживает данный тип учета типа японской азбуки, то запрос выполняется, как если бы значением было **False**. Если известно значение и известно, что оно поддерживается, выберите значение **True**.  
  
 **Учитывать ширину символов**  
 Выберите значение, которое определяет учет ширины символов. Этот параметр указывает, учитывают ли данные ширину, и может принимать значения **true**, **false**или **Auto**. Значение по умолчанию **Auto**указывает, что сервер отчетов должен попытаться получить значение от поставщика данных при выполнении отчета. Если поставщик данных не поддерживает данный тип учета ширины, то запрос выполняется, как если бы значением было **False**. Если известно значение и известно, что оно поддерживается, выберите значение **True**.  
  
 **Рассматривать подытоги как строки детализации**  
 Выберите значение, которое указывает, должны ли строки промежуточных итогов интерпретироваться как строки детализации, а не как строки со статистическими результатами. Значение по умолчанию **Auto**указывает, что строки промежуточных итогов должны рассматриваться как строки детализации, если в отчете не используется `Aggregate` функция () для доступа к каким-либо полям в наборе данных. Если требуется, чтобы строки промежуточных итогов интерпретировались как строки со статистическими результатами, выберите **False**. Если необходимо, чтобы строки промежуточных итогов считались строками подробностей, и вы уверены, что они не используют `Aggregate` функцию (), выберите **значение true**.  
  
## <a name="see-also"></a>См. также:  
 [Задайте языковой стандарт для отчета или текстового поля &#40;Reporting Services&#41;](report-design/set-the-locale-for-a-report-or-text-box-reporting-services.md)   
 [Добавление данных в построитель отчетов &#40;отчетов и SSRS&#41;](report-data/report-datasets-ssrs.md)   
 [Имя параметров сортировки Windows (Transact-SQL)](/sql/t-sql/statements/windows-collation-name-transact-sql)   
 [Имя параметров сортировки SQL Server (Transact-SQL)](/sql/t-sql/statements/sql-server-collation-name-transact-sql)   
 [Агрегатная функция (построитель отчетов и службы SSRS)](report-design/report-builder-functions-aggregate-function.md)  
  
  