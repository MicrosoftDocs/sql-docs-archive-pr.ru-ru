---
title: Передача параметров в диаграмм обновления (SQLXML 4,0) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- nullvalue attribute
- passing parameters [SQLXML]
- parameters [SQLXML]
- updategrams [SQLXML], passing parameters
- null values [SQLXML]
ms.assetid: 2354e6e7-1860-471f-8711-4e374c5a4ed2
author: rothja
ms.author: jroth
ms.openlocfilehash: 4bc29de2dab3d0bc3587cb21b7005c0c23dcf7c5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87665959"
---
# <a name="passing-parameters-to-updategrams-sqlxml-40"></a>Передача параметров для диаграмм обновления (SQLXML 4.0)
  Диаграммы обновления представляют собой шаблоны; следовательно, им можно передавать параметры. Дополнительные сведения о передаче параметров в шаблоны см. в разделе [Диаграмма обновления Security соображения &#40;SQLXML 4,0&#41;](../security/updategram-security-considerations-sqlxml-4-0.md).  
  
 Диаграммы обновления позволяют передавать значение NULL в качестве значения параметра. Для передачи значения NULL в качестве значения параметра нужно задать атрибут `nullvalue`. После этого в качестве значения параметра передается значение, присвоенное атрибуту `nullvalue`. В диаграммах обновления это значение рассматривается как NULL.  
  
> [!NOTE]  
>  В `<sql:header>` и `<updg:header>` следует задавать `nullvalue` как неполное имя; однако в `<updg:sync>` следует задавать `nullvalue` в виде полного имени (например, `updg:nullvalue`).  
  
## <a name="examples"></a>Примеры  
 Чтобы создать рабочие образцы с помощью следующих примеров, необходимо выполнить требования, указанные в [требованиях к запуску примеров SQLXML](../../sqlxml/requirements-for-running-sqlxml-examples.md).  
  
 При использовании примеров диаграмм обновления необходимо учитывать следующие моменты.  
  
-   В примерах используется сопоставление по умолчанию (т. е. в диаграмме обновления не задана схема сопоставления). Дополнительные примеры диаграмм обновления, в которых используются схемы сопоставления, см. [в разделе Указание схемы сопоставления с заметками в диаграмма обновления &#40;SQLXML 4,0&#41;](specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md).  
  
### <a name="a-passing-parameters-to-an-updategram"></a>A. Передача параметров диаграмме обновления  
 В данном примере диаграмма обновления применяется для изменения фамилии сотрудника в таблице HumanResources.Shift. Диаграмма обновления передается два параметра: Шифтид, который используется для уникальной идентификации сдвига и имени.  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:header>  
  <updg:param name="ShiftID"/>  
  <updg:param name="Name" />  
</updg:header>  
  <updg:sync >  
    <updg:before>  
       <HumanResources.Shift ShiftID="$ShiftID" />  
    </updg:before>  
    <updg:after>  
      <HumanResources.Shift Name="$Name" />  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
##### <a name="to-test-the-updategram"></a>Тестирование диаграммы обновления  
  
1.  Скопируйте приведенную выше диаграмму обновления в блокнот и сохраните как файл с именем UpdategramWithParameters.xml.  
  
2.  Подготовка тестового скрипта SQLXML 4,0 (Sqlxml4test. vbs) в [с помощью ADO для выполнения запросов SQLXML 4,0](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md) для выполнения диаграмма обновления путем добавления следующих строк после `cmd.Properties("Output Stream").Value = outStream` :  
  
    ```  
    cmd.NamedParameters = True  
    ' CreateParameter arguments: Name, Type, Direction, Size, Value  
    cmd.Parameters.Append cmd.CreateParameter("@ShiftID",  2, 1,  0, 1)  
    cmd.Parameters.Append cmd.CreateParameter("@Name",   200, 1, 50, "New Name")  
    ```  
  
### <a name="b-passing-null-as-a-parameter-value-to-an-updategram"></a>Б. Передача NULL в качестве значения параметра для диаграммы обновления  
 При выполнении диаграммы обновления тому параметру, для которого нужно задать значение NULL, присваивается значение «isnull». Диаграмма обновления преобразовывает значение параметра «isnull» в NULL и обрабатывает соответствующим образом.  
  
 Следующая диаграмма обновления устанавливает значение NULL для названия должности сотрудника.  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:header nullvalue="isnull" >  
  <updg:param name="EmployeeID"/>  
  <updg:param name="ManagerID" />  
</updg:header>  
  <updg:sync >  
    <updg:before>  
       <HumanResources.Employee EmployeeID="$EmployeeID" />  
    </updg:before>  
    <updg:after>  
      <HumanResources.Employee ManagerID="$ManagerID" />  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
##### <a name="to-test-the-updategram"></a>Тестирование диаграммы обновления  
  
1.  Скопируйте приведенную выше диаграмму обновления в блокнот и сохраните как файл с именем UpdategramPassingNullvalues.xml.  
  
2.  Подготовка тестового скрипта SQLXML 4,0 (Sqlxml4test. vbs) в [с помощью ADO для выполнения запросов SQLXML 4,0](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md) для выполнения диаграмма обновления путем добавления следующих строк после `cmd.Properties("Output Stream").Value = outStream` :  
  
    ```  
    cmd.NamedParameters = True  
    ' CreateParameter arguments: Name, Type, Direction, Size, Value   
    cmd.Parameters.Append cmd.CreateParameter("@EmployeeID", 3, 1, 0, 1)  
    cmd.Parameters.Append cmd.CreateParameter("@ManagerID",  3, 1, 0, Null)  
    ```  
  
## <a name="see-also"></a>См. также:  
 [Вопросы безопасности диаграмма обновления &#40;SQLXML 4,0&#41;](../security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
