---
title: Управление доступом для кода в службах Reporting Services | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- code groups [Reporting Services]
- code access security [Reporting Services]
- permission sets [Reporting Services]
- evidence [Reporting Services]
- code access security [Reporting Services], about code access security
- named permission sets [Reporting Services]
ms.assetid: 97480368-1fc3-4c32-b1b0-63edfb54e472
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ebe023b13a003895845bbb119f0bc93a0d01203a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87669287"
---
# <a name="code-access-security-in-reporting-services"></a>Управление доступом для кода в службах Reporting Services
  Управление доступом для кода основывается на следующих базовых понятиях: свидетельство, группы кода и именованные наборы разрешений. В службах [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] каждый из компонентов (диспетчер отчетов, конструктор отчетов и сервер отчетов) имеет файл политики, в котором задана конфигурация управления доступом для кода для пользовательских сборок, а также для модулей обработки данных, доставки, подготовки отчетов и безопасности. В следующих разделах приведены общие сведения об управлении доступом для кода. Дополнительные сведения по темам, рассматриваемым в этом разделе, см. в разделе о модели политики безопасности в документации по пакету SDK для [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].  
  
 В службах [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] используется управление доступом для кода, поскольку, несмотря на то, что сервер отчетов основан на технологии [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)], имеется существенное различие между типичным приложением [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] и сервером отчетов. В типичном приложении [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] не выполняется пользовательский код. В отличие от этого, в службах [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] используется открытая и расширяемая архитектура, которая позволяет пользователям писать программы с использованием файлов определения отчетов, применяя элемент **Code** языка определения отчетов, а также разрабатывать специализированные функции в составе пользовательских сборок для применения в отчетах. Кроме того, разработчики могут проектировать и развертывать мощные модули, которые расширяют возможности сервера отчетов. Это увеличение мощности и гибкости приводит к необходимости обеспечить настолько полную защиту и безопасность, насколько это возможно.  
  
 Разработчики служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] могут использовать любую сборку [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] в своих отчетах и вызывать непосредственно в коде все функции сборок, развернутых в глобальном кэше сборок. Сервер отчетов может управлять только разрешениями, предоставляемыми для выражений отчета и загруженных пользовательских сборок. В службах [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] пользовательские сборки по умолчанию получают разрешения только на **выполнение**.  
  
## <a name="evidence"></a>Свидетельство  
 Свидетельство представляет собой информацию, которая используется в среде CLR для определения политики безопасности для сборок кода. Свидетельство указывает среде выполнения, что код имеет конкретные характеристики. Чаще всего в качестве свидетельства применяются цифровые подписи и данные о расположении сборки. Свидетельство может быть также сконструировано специально для представления другой информации, которая является значимой для приложения.  
  
 И сборки, и домены приложений получают разрешения на основе свидетельства. Например, информация о местоположении сборки, к которой пытаются получить доступ службы [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], является одной из общих форм свидетельства для сборок со слабыми именами. Такие свидетельства принято называть свидетельствами URL-адреса. Примером свидетельства URL-адреса для пользовательского модуля обработки данных, развернутого на сервере отчетов, может быть «C:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer\bin\Microsoft.Samples.ReportingServices.FsiDataExtension.dll». Еще одной широко применяемой формой свидетельства является строгое имя или цифровая подпись сборки. В этом случае свидетельством является информация открытого ключа для сборки.  
  
## <a name="code-groups"></a>Группы кода  
 Группа кода представляет собой логическое группирование кода, для определения принадлежности к который применяется определенное условие. Любой код, который соответствует условию членства, включается в группу. Администраторы настраивают политику безопасности для управления группами кода и связанными с ними наборами разрешений.  
  
 Условие членства для группы кода основано на свидетельстве. Например, членство URL-адреса для группы кода основано на свидетельстве URL-адреса. В среде CLR для описания кода и определения того, соблюдено ли условие членства в группе, применяются такие идентифицирующие характеристики, как свидетельство URL-адреса. Например, если условием членства в группе кода является то, что «код находится в сборке C:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer\bin\Microsoft.Samples.ReportingServices.FsiDataExtension.dll», среда выполнения проверяет это свидетельство и определяет, действительно ли код получен из этого местоположения. Пример записи конфигурации для группы кода этого типа может выглядеть примерно так:  
  
```  
<CodeGroup class="UnionCodeGroup"  
   version="1"  
   PermissionSetName="FullTrust"  
   Name="MyCodeGroup"  
   Description="Code group for my data processing extension">  
      <IMembershipCondition class="UrlMembershipCondition"  
         version="1"  
         Url="C:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer\bin\Microsoft.Samples.ReportingServices.FsiDataExtension.dll"  
       />  
</CodeGroup>  
```  
  
 Необходимо работать совместно с системным администратором или экспертом по развертыванию приложений, чтобы определить тип управления доступом для кода и групп кода, которые требуются для пользовательских сборок или модулей служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].  
  
## <a name="named-permission-sets"></a>Именованные наборы разрешений  
 Именованный набор разрешений представляет собой множество разрешений, которые администраторы могут связать с группой кода. Большинство именованных наборов разрешений состоит, по меньшей мере, из одного разрешения, имени и описания для набора разрешений. Администраторы могут использовать именованные наборы разрешений для установки или изменения политики безопасности для групп кода. С одним и тем же именованным набором разрешений может быть связано несколько групп кода. В среде CLR предусмотрены встроенные именованные наборы разрешений. В их число входят **Nothing**, **Execution**, **Internet**, **LocalIntranet**, **Everything** и **FullTrust**.  
  
> [!NOTE]  
>  Пользовательские модули обработки данных, доставки, подготовки отчетов и безопасности в службах [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] должны запускаться с набором разрешений **FullTrust**. Необходимо работать совместно с системным администратором, чтобы добавить соответствующие группы кода и условия членства для пользовательских модулей служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].  
  
 Можно связать собственные пользовательские уровни разрешений с пользовательскими сборками, применяемыми в отчетах. Например, если требуется предоставить доступ какой-то сборке к конкретному файлу, можно создать новый именованный набор разрешений с конкретным файловым доступом для ввода-вывода, а затем назначить этот набор разрешений применяемой группе кода. В следующем наборе разрешений предоставляется доступ только для чтения к файлу MyFile.xml:  
  
```  
<PermissionSet class="NamedPermissionSet"  
   version="1"  
   Name="MyNewFilePermissionSet"  
   Description="A special permission set that grants read access to my file.">  
    <IPermission class="FileIOPermission"  
       version="1"  
       Read="C:\MyFile.xml"/>  
    <IPermission class="SecurityPermission"  
       version="1"  
       Flags="Assertion, Execution"/>  
</PermissionSet>  
```  
  
 Группа кода, которой предоставляется этот набор разрешений, может выглядеть примерно так:  
  
```  
<CodeGroup class="UnionCodeGroup"  
   version="1"  
   PermissionSetName="MyNewFilePermissionSet"  
   Name="MyNewCodeGroup"  
   Description="A special code group for my custom assembly.">  
   <IMembershipCondition class="UrlMembershipCondition"  
      version="1"  
      Url="C:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer\bin\MyCustomAssembly.dll"/>  
</CodeGroup>  
```  
  
## <a name="see-also"></a>См. также:  
 [Разработка безопасных приложений (службы Reporting Services)](secure-development-reporting-services.md)  
  
  
