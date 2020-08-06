---
title: Обновление отчетов с использованием классов, созданных из RDL-схемы (учебник по службам SSRS) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- RDL [Reporting Services], generating
- RDL [Reporting Services], tutorials
- RDL [Reporting Services], serializing
ms.assetid: 8f81d48f-7ab9-4ef8-bce0-7d16d9a47fbd
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: f3972b8e1af6d50ccc6f5188c8f671fe333ebce8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87656077"
---
# <a name="updating-reports-using-classes-generated-from-the-rdl-schema-ssrs-tutorial"></a>Обновление отчетов с помощью классов, созданных из схемы языка определения отчетов (учебник по службам SSRS)
  В этом учебнике показано, как использовать средство определения схемы XML (Xsd.exe) для создания классов, позволяющих сериализовать и десериализовать файлы определения отчета (RDL и RDLC) с помощью [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] <xref:System.Xml.Serialization.XmlSerializer> класса.  
  
## <a name="what-you-will-learn"></a>Обзор учебника  
 В ходе работы с этим учебником предстоит выполнить следующие действия.  
  
-   Создайте приложение с помощью [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] шаблона проекта Консольное приложение.  
  
-   Создание классов из схемы языка определения отчетов (RDL) с помощью средства **XSD** .  
  
-   Подключиться к серверу отчетов и получить определение отчета.  
  
-   Написать код для обновления файла определения отчета.  
  
-   Сохранить обновленное определение отчета на сервере отчетов.  
  
-   Выполнение приложения схемы языка определения отчетов (VB/C#).  
  
> [!NOTE]  
>  Образцы кода, приведенные в этом учебнике, могут не работать в отчетах, у которых нет описания. Происходит это потому, что у отчетов, для которых не задано описание, отсутствует свойство описания.  
  
## <a name="requirements"></a>Требования  
 Для работы с учебником необходимо наличие следующих компонентов.  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)].  
  
-   Необходимые разрешения для доступа к отчетам и публикации их в веб-службе сервера отчетов SQL Server на компьютере, на котором размещен сервер отчетов.  
  
-   Образец базы данных [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)], установленный на экземпляре [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
-   Отчет, установленный на сервере отчетов. Этот учебник основывается на образце отчета Company Sales 2012. Дополнительные сведения об образцах отчетов см. в разделе [SQL Server Reporting Services примеров продуктов](https://go.microsoft.com/fwlink/?LinkId=177889).  
  
> [!NOTE]  
>  Образцы не устанавливаются автоматически в процессе установки, но их можно установить в любое время. Дополнительные сведения о примерах см. в разделе [SQL Server Product Samples](https://go.microsoft.com/fwlink/?LinkId=182887).  
  
 **Предполагаемое время выполнения учебника:** 30 минут  
  
## <a name="tasks"></a>Задания  
 [Урок 1. Создание проекта схемы языка определения отчетов в Visual Studio](../../2014/tutorials/lesson-1-create-the-rdl-schema-visual-studio-project.md)  
  
 [Урок 2. Формирование классов из схемы языка определения отчетов с помощью инструмента xsd](../../2014/tutorials/lesson-2-generate-classes-from-the-rdl-schema-using-the-xsd-tool.md)  
  
 [Урок 3. Загрузка определения отчета с сервера отчетов](../../2014/tutorials/lesson-3-load-a-report-definition-from-the-report-server.md)  
  
 [Занятие 4: Обновление определения отчета программным способом](../../2014/tutorials/lesson-4-update-the-report-definition-programmatically.md)  
  
 [Занятие 5.: Публикация определения отчета на сервере отчетов](../../2014/tutorials/lesson-5-publish-the-report-definition-to-the-report-server.md)  
  
 [Занятие 6. Запуск приложения схемы языка определения отчетов &#40;VB-C&#35;&#41;](../../2014/tutorials/lesson-6-run-the-rdl-schema-application-vb-csharp.md)  
  
## <a name="see-also"></a>См. также:  
 [Язык определения отчетов (службы SSRS)](../reporting-services/reports/report-definition-language-ssrs.md)  
  
  
