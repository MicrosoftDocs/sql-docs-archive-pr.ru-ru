---
title: Создание проекта SMO в Visual C# в Visual Studio .NET | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- Visual C# [SMO]
ms.assetid: 1e7abb16-23a0-4a18-91ad-253261e6bf84
author: stevestein
ms.author: sstein
ms.openlocfilehash: b78820fafd37675332e6703cabbb87e78bde5864
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87665983"
---
# <a name="create-a-visual-c-smo-project-in-visual-studio-net"></a>создание проекта SMO на языке Visual C# в среде Visual Studio .NET
  В данном разделе описывается, как построить простое консольное приложение командной строки SMO.  
  
 В этом примере импортируются пространства имен, что позволяет программе ссылаться на типы объектов SMO. Импорт пространства имен `Agent` необязателен. Его следует выполнить при написании программы, в которой используется агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Пространство имен `Common` требуется для установления безопасного соединения с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Пространство имен `SqlClient` используется для обработки ошибок, связанных с исключениями SQL.  
  
### <a name="creating-a-visual-c-smo-project-in-visual-studionet"></a>Создание проекта SMO на языке Visual C# в среде Visual Studio.NET  
  
1.  Запустите среду [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)] (или [!INCLUDE[vsprvslong](../../includes/vsprvslong-md.md)]).  
  
2.  В меню **Файл** выберите пункт **Создать проект**. Откроется диалоговое окно **Создание проекта** .  
  
3.  В диалоговом окне **типы проектов** выберите **Visual C#**, а затем выберите **Windows**. В [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] области Установленные шаблоны выберите **приложение Windows**.  
  
4.  Используемых В поле **имя** введите имя нового приложения.  
  
5.  Выберите тип приложения Visual C#. Для приведенных ниже примеров выберите **консольное приложение**.  
  
6.  В меню **Проект** выберите пункт **Добавить ссылку**. Откроется диалоговое окно **Добавление ссылки**.  
  
7.  Нажмите кнопку **Обзор**, найдите сборки SMO в [!INCLUDE[ssSampPathSDK](../../includes/sssamppathsdk-md.md)] папке, а затем выберите следующие файлы. Для построения приложения SMO необходимы как минимум следующие файлы:  
  
     Microsoft.SqlServer.ConnectionInfo.dll  
  
     Microsoft.SqlServer.Smo.dll  
  
     Microsoft.SqlServer.Management.Sdk.Sfc.dll  
  
     Microsoft.SqlServer.SqlEnum.dll  
  
    > [!NOTE]  
    >  Используйте клавишу `Ctrl`, чтобы выбрать несколько файлов.  
  
8.  Добавьте все дополнительные сборки SMO, которые могут потребоваться. Например, если программа предназначена для компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)], добавьте следующие сборки:  
  
     Microsoft.SqlServer.ServiceBrokerEmum.dll  
  
9. Нажмите кнопку **Открыть**.  
  
10. В меню **вид** выберите пункт **код**.-или-выберите PROGRAM1.cs [Design] Windows и дважды щелкните Windows Form, чтобы открыть окно кода.  
  
11. В коде перед инструкцией пространства имен введите следующие инструкции `using` для определения типов в пространстве имен объектов SMO.  
  
    ```  
    using Microsoft.SqlServer.Management.Smo;  
    using Microsoft.SqlServer.Management.Common;  
    ```  
  
12. В SMO имеются различные пространства имен в узле Microsoft.SqlServer.Management.Smo, такие как Microsoft.SqlServer.Management.Smo.Agent. Добавьте эти пространства имен при необходимости.  
  
13. Теперь можно добавить свой код SMO.  
  
  
