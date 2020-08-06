---
title: Функция LookupSet (построитель отчетов и службы SSRS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 7685acfd-1c8d-420c-993c-903236fbe1ff
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4edc7a17f2aa3813e8aa73e538594b5df3aeabc1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659426"
---
# <a name="lookupset-function-report-builder-and-ssrs"></a>Функция LookupSet (построитель отчетов и службы SSRS)
  Возвращает набор совпадающих значений для заданного имени из набора данных, содержащего пары «имя-значение».  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
LookupSet(source_expression, destination_expression, result_expression, dataset)  
```  
  
#### <a name="parameters"></a>Параметры  
 *source_expression*  
 (`Variant`) Выражение, вычисляемое в текущей области и указывающее имя или ключ для поиска. Например, `=Fields!ID.Value`.  
  
 *destination_expression*  
 (`Variant`) Выражение, вычисляемое для каждой строки в наборе данных и указывающее имя или ключ для сопоставления. Например, `=Fields!CustomerID.Value`.  
  
 *result_expression*  
 ( `Variant` ) Выражение, вычисляемое для строки в наборе данных, где *source_expression*  =  *destination_expression*, который указывает извлекаемое значение. Например, `=Fields!PhoneNumber.Value`.  
  
 *набор данных*  
 Константа, задающая имя набора данных в отчете. Например, «ContactInformation».  
  
## <a name="return"></a>Возвращает  
 Возвращает значение `VariantArray` или `Nothing`, если совпадения нет.  
  
## <a name="remarks"></a>Remarks  
 Функция `LookupSet` служит для извлечения набора значений из указанного набора данных, состоящего из пар «имя-значение» со связью «один ко многим». Например, функция `LookupSet` позволяет извлечь по идентификатору пользователя в таблице все связанные с ним телефонные номера из набора данных, не привязанного к этой области данных.  
  
 Функция `LookupSet` выполняет следующие действия.  
  
-   Вычисляет исходное выражение в текущей области.  
  
-   Вычисляет целевое выражение для каждой строки указанного набора данных после применения фильтров с учетом заданных для него параметров сортировки.  
  
-   При каждом совпадении исходного и целевого выражений вычисляет результирующее выражение для этой строки в наборе данных.  
  
-   Возвращает набор результирующих значений выражения.  
  
 Для извлечения единственного значения для указанного имени из набора данных, состоящего из пар "имя-значение" со связью "один к одному", используйте [функцию Lookup (построитель отчетов и службы SSRS)](report-builder-functions-lookup-function.md). Для вызова `Lookup` набора значений используйте [функцию много&#40;построитель отчетов и службы SSRS&#41;](report-builder-functions-multilookup-function.md).  
  
 Применяются следующие ограничения:  
  
-   Функция `LookupSet` вычисляется после применения всех выражений фильтров.  
  
-   Поддерживается только один уровень уточняющего запроса. Исходное, целевое и результирующее выражения не могут включать в себя ссылки на функцию уточняющего запроса.  
  
-   Исходное и результирующее выражения должны возвращать один и тот же тип данных.  
  
-   Исходное, целевое и результирующее выражения не могут включать в себя ссылки на переменные отчета или группы.  
  
-   Функцию `LookupSet` нельзя использовать в качестве выражения для следующих элементов отчета:  
  
    -   динамические строки соединения для источника данных;  
  
    -   вычисляемые поля в наборе данных;  
  
    -   параметры запроса в наборе данных;  
  
    -   фильтры в наборе данных;  
  
    -   параметры отчета;  
  
    -   Свойство Report.Language.  
  
 Дополнительные сведения см. в разделах [Справочник по агрегатным функциям (построитель отчетов и службы SSRS)](report-builder-functions-aggregate-functions-reference.md) и [Область выражения для суммирования, агрегатных функций и встроенных коллекций (построитель отчетов и службы SSRS)](expression-scope-for-totals-aggregates-and-built-in-collections.md).  
  
## <a name="example"></a>Пример  
 В следующем примере предположим, что таблица привязана к набору данных, включающему идентификатор территории продаж TerritoryGroupID. Отдельный набор данных с именем Stores содержит список всех складов на данной территории и включает идентификатор ID и название склада StoreName.  
  
 В следующем выражении функция `LookupSet` сравнивает значение TerritoryGroupID со значением ID для каждой из строк набора данных Stores. Для каждого совпадения значение поля StoreName в этой строке добавляется в результирующий набор.  
  
```  
=LookupSet(Fields!TerritoryGroupID.Value, Fields!ID.Value, Fields!StoreName.Value, "Stores")  
```  
  
## <a name="example"></a>Пример  
 Поскольку функция `LookupSet` возвращает коллекцию объектов, результирующее выражение невозможно непосредственно отобразить в текстовом поле. Значения объектов коллекции можно склеить в одну строку.  
  
 Функция [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]`Join` позволяет создать из набора объектов строку с разделителями. Для объединения объектов в одну строку используйте в качестве разделителя запятую. В некоторых модулях подготовки можно использовать в качестве разделителя перевод строки [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] (`vbCrLF`).  
  
 Следующее выражение, когда оно используется как свойство Value для текстового поля, использует `Join` для создания списка.  
  
```  
=Join(LookupSet(Fields!TerritoryGroupID.Value, Fields!ID.Value, Fields!StoreName.Value, "Stores"),",")  
```  
  
## <a name="example"></a>Пример  
 Для текстовых полей, подготовка которых к просмотру выполняется лишь несколько раз, можно добавить пользовательский код формирования HTML для отображения значений в текстовом поле. HTML в текстовом поле требует дополнительной обработки, поэтому плохо подходит для текстовых полей, подготовка которых выполняется тысячи раз.  
  
 Скопируйте следующие функции [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] в блок кода. Функция**MakeList** принимает массив объектов, возвращаемый из *result_expression* , и строит неупорядоченный список с помощью тегов HTML. Свойство**Length** возвращает число элементов в массиве объектов.  
  
```  
Function MakeList(ByVal items As Object()) As String  
   If items Is Nothing Then  
      Return Nothing  
   End If  
  
   Dim builder As System.Text.StringBuilder =   
      New System.Text.StringBuilder()  
   builder.Append("<ul>")  
  
   For Each item As Object In items  
      builder.Append("<li>")  
      builder.Append(item)  
   Next  
   builder.Append("</ul>")  
  
   Return builder.ToString()  
End Function  
  
Function Length(ByVal items as Object()) as Integer  
   If items is Nothing Then  
      Return 0  
   End If  
   Return items.Length  
End Function  
```  
  
## <a name="example"></a>Пример  
 Для формирования HTML необходимо вызвать функцию. Вставьте следующее выражение в свойство Value текстового поля и задайте для типа разметки текста значение HTML. Дополнительные сведения см. в разделе [Добавление HTML в отчет (построитель отчетов и службы SSRS)](add-html-into-a-report-report-builder-and-ssrs.md).  
  
```  
=Code.MakeList(LookupSet(Fields!TerritoryGroupID.Value, Fields!ID.Value, Fields!StoreName.Value, "Stores"))  
```  
  
## <a name="see-also"></a>См. также:  
 [Использование выражений в отчетах (построитель отчетов и службы SSRS)](expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Примеры выражений (построитель отчетов и службы SSRS)](expression-examples-report-builder-and-ssrs.md)   
 [Типы данных в выражениях (построитель отчетов и службы SSRS)](expressions-report-builder-and-ssrs.md)   
 [Область выражения для суммирования, агрегатных функций и встроенных коллекций (построитель отчетов и службы SSRS)](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
