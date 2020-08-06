---
title: Практическое руководство. Развертывание модуля обработки данных на сервере отчетов | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- data processing extensions [Reporting Services], deploying
- assemblies [Reporting Services], data processing extension deployments
ms.assetid: e00dface-70f8-434b-9763-8ebee18737d2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d606096b9f2060d3cf5b9cea1f95a5345e592383
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87750512"
---
# <a name="how-to-deploy-a-data-processing-extension-to-a-report-server"></a>Руководство. Развертывание модуля обработки данных на сервере отчетов
  Серверы отчетов используют модули обработки данных для получения и обработки данных в отчетах, готовых для просмотра. Сборка модуля обработки данных развертывается на сервере отчетов как закрытая сборка. Нужно также внести запись в файл конфигурации сервера отчетов RSReportServer.config.  
  
## <a name="procedures"></a>Процедуры  
  
#### <a name="to-deploy-a-data-processing-extension-assembly"></a>Развертывание сборки модуля обработки данных  
  
1.  Скопируйте сборку из промежуточной папки в каталог bin сервера отчетов, на котором будет использоваться модуль обработки данных. По умолчанию каталог bin сервера отчетов находится в папке%ProgramFiles%\Microsoft SQL Server \ MSRS10_50. \<*Instance Name*> \Reporting Services\ReportServer\bin.  
  
    > [!NOTE]  
    >  Этот шаг предотвратит обновление до более нового экземпляра SQL Server. Дополнительные сведения см. в разделе [Upgrade and Migrate Reporting Services](../../install-windows/upgrade-and-migrate-reporting-services.md).  
  
2.  Скопировав файл сборки, откройте файл RSReportServer.config. Файл RSReportServer.config расположен в каталоге ReportServer. Необходимо внести запись в этот файл конфигурации для файла сборки развертываемого модуля обработки данных. Файл конфигурации можно открыть с помощью среды Visual Studio или простого текстового редактора (такого как Блокнот).  
  
3.  Найдите в файле RSReportServer.config элемент `Data`. Запись для вновь созданного модуля обработки данных необходимо создать в месте, указанном ниже.  
  
    ```  
    <Extensions>  
       <Data>  
          <Your extension configuration information goes here>  
       </Data>  
    </Extensions>  
    ```  
  
4.  Добавьте запись для развертываемого модуля обработки данных. В новую запись должен входить элемент `Extension` со значениями параметров `Name` и `Type`. Запись может выглядеть, например, следующим образом:  
  
    ```  
    <Extension Name="ExtensionName" Type="CompanyName.ExtensionName.MyConnectionClass, MyExtensionAssembly" />  
    ```  
  
     По умолчанию `Name` — уникальное имя модуля обработки данных. Значение параметра `Type` представляет собой список с разделителями-запятыми, включающий полное имя пространства имен для класса, реализующего интерфейсы <xref:Microsoft.ReportingServices.Interfaces.IExtension> и <xref:Microsoft.ReportingServices.DataProcessing.IDbConnection>, а затем имя сборки поставщика (без расширения DLL). По умолчанию модули обработки данных являются видимыми. Чтобы скрыть модуль от пользовательских интерфейсов, таких как диспетчер отчетов, добавьте атрибут `Visible` к элементу `Extension` и задайте для него значение `false`.  
  
5.  Необходимо создать для пользовательской сборки группу кода, которая предоставляет разрешение `FullTrust` для конкретного модуля. Это можно сделать, добавив группу кода в файл rssrvpolicy.config, расположенный по умолчанию в%ProgramFiles%\Microsoft SQL Server \\<MSRS10_50. \<*Instance Name*> \Reporting Services\ReportServer. Пример группы кода показан ниже.  
  
    ```  
    <CodeGroup class="UnionCodeGroup"  
       version="1"  
       PermissionSetName="FullTrust"  
       Name="MyExtensionCodeGroup"  
       Description="Code group for my data processing extension">  
          <IMembershipCondition class="UrlMembershipCondition"  
             version="1"  
             Url="C:\Program Files\Microsoft SQL Server\MSRS10_50.<Instance Name>\Reporting Services\ReportServer\bin\MyExtensionAssembly.dll"  
           />  
    </CodeGroup>  
    ```  
  
 URL-членство — это лишь одно из множества условий членства, которые могут быть заданы для модуля обработки данных. Дополнительные сведения об управлении доступом для кода в [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] см. в статье [Разработка безопасных приложений (службы Reporting Services)](../secure-development/secure-development-reporting-services.md).  
  
## <a name="verifying-the-deployment"></a>Проверка развертывания  
 Проверить, успешно ли был развернут модуль обработки данных на сервере отчетов, можно с помощью метода веб-службы <xref:ReportService2010.ReportingService2010.ListExtensions%2A>. Можно также открыть диспетчер отчетов и убедиться, что модуль включен в список доступных источников данных. Дополнительные сведения о диспетчере отчетов и источниках данных см. в разделе [Создание, изменение и удаление общих источников данных (службы SSRS)](../../report-data/create-modify-and-delete-shared-data-sources-ssrs.md).  
  
## <a name="see-also"></a>См. также:  
 [Развертывание модуля обработки данных](deploying-a-data-processing-extension.md)   
 [Модули служб Reporting Services](../reporting-services-extensions.md)   
 [Реализация модуля обработки данных](implementing-a-data-processing-extension.md)   
 [Библиотека модулей Reporting Services](../reporting-services-extension-library.md)  
  
  
