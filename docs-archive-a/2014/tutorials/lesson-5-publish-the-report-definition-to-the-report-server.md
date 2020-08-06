---
title: Занятие 5. Публикация определения отчета на сервере отчетов | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 57fab70f-4a72-4413-a0ad-d0525caca3f7
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 54c2bad9f5b11e5ea72036fed9f60371ba9c593c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87657426"
---
# <a name="lesson-5-publish-the-report-definition-to-the-report-server"></a><span data-ttu-id="c8b59-102">Занятие 5.: Публикация определения отчета на сервере отчетов</span><span class="sxs-lookup"><span data-stu-id="c8b59-102">Lesson 5: Publish the Report Definition to the Report Server</span></span>
  <span data-ttu-id="c8b59-103">Последним шагом обновления определения отчета является его публикация на сервере отчетов.</span><span class="sxs-lookup"><span data-stu-id="c8b59-103">The last step for updating the report definition is to publish it back to the report server.</span></span>  
  
### <a name="to-publish-the-report-to-the-report-catalog"></a><span data-ttu-id="c8b59-104">Публикация отчета в каталоге отчетов</span><span class="sxs-lookup"><span data-stu-id="c8b59-104">To publish the report to the report catalog</span></span>  
  
1.  <span data-ttu-id="c8b59-105">Замените код `PublishReportDefinition()` метода в файле Program.cs (Module1. vb для [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ) следующим кодом:</span><span class="sxs-lookup"><span data-stu-id="c8b59-105">Replace the code for the `PublishReportDefinition()` method in your Program.cs file (Module1.vb for [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) with the following code:</span></span>  
  
    ```csharp  
    private void PublishReportDefinition()  
    {  
        System.Console.WriteLine("Publishing Report Definition");  
  
        string reportPath =  
            "/AdventureWorks 2012 Sample Reports/Company Sales 2012";  
  
        XmlSerializer serializer =  
            new XmlSerializer(typeof(Report));  
  
        using (MemoryStream stream = new MemoryStream())  
        {  
            // Serialize the report into the MemoryStream  
            serializer.Serialize(stream, _report);  
            stream.Position = 0;  
  
            byte[] bytes = stream.ToArray();  
  
            // Update the report on the report server  
            Warning[] warnings =   
                _reportService.SetItemDefinition(reportPath, bytes, null);  
        }  
    }  
    ```  
  
    ```vb  
    Private Sub PublishReportDefinition()  
  
        System.Console.WriteLine("Publishing Report Definition")  
  
        Dim reportPath As String = _  
            "/AdventureWorks 2012 Sample Reports/Company Sales 2012"  
        Dim serializer As XmlSerializer = _  
            New XmlSerializer(GetType(Report))  
  
        Using stream As MemoryStream = New MemoryStream  
  
            'Serialize the report into the MemoryStream  
            serializer.Serialize(stream, m_report)  
            stream.Position = 0  
  
            'Update the report on the report server  
            Dim bytes As Byte() = stream.ToArray  
            Dim warnings As Warning() = _  
                m_reportService.SetItemDefinition(reportPath, bytes, Nothing)  
  
        End Using  
  
    End Sub  
    ```  
  
## <a name="next-lesson"></a><span data-ttu-id="c8b59-106">Следующее занятие</span><span class="sxs-lookup"><span data-stu-id="c8b59-106">Next Lesson</span></span>  
 <span data-ttu-id="c8b59-107">На следующем занятии будет выполнена компиляция и запуск `SampleRDLSchema` приложения.</span><span class="sxs-lookup"><span data-stu-id="c8b59-107">In the next lesson, you will compile and run the `SampleRDLSchema` application.</span></span> <span data-ttu-id="c8b59-108">См. [занятие 6. Запуск приложения схемы RDL &#40;&#35;&#41;VB-C ](../../2014/tutorials/lesson-6-run-the-rdl-schema-application-vb-csharp.md).</span><span class="sxs-lookup"><span data-stu-id="c8b59-108">See [Lesson 6: Run the RDL Schema Application &#40;VB-C&#35;&#41;](../../2014/tutorials/lesson-6-run-the-rdl-schema-application-vb-csharp.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8b59-109">См. также:</span><span class="sxs-lookup"><span data-stu-id="c8b59-109">See Also</span></span>  
 <span data-ttu-id="c8b59-110">[Обновление отчетов с использованием классов, созданных из учебника по схеме языка определения отчетов &#40;SSRS&#41;](../../2014/tutorials/updating-reports-using-classes-generated-from-the-rdl-schema-ssrs-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="c8b59-110">[Updating Reports Using Classes Generated from the RDL Schema &#40;SSRS Tutorial&#41;](../../2014/tutorials/updating-reports-using-classes-generated-from-the-rdl-schema-ssrs-tutorial.md) </span></span>  
 [<span data-ttu-id="c8b59-111">Язык определения отчетов (службы SSRS)</span><span class="sxs-lookup"><span data-stu-id="c8b59-111">Report Definition Language &#40;SSRS&#41;</span></span>](../reporting-services/reports/report-definition-language-ssrs.md)  
  
  
