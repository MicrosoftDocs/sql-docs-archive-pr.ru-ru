---
title: Основные понятия объектов RMO | Документация Майкрософт
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- replication [SQL Server], RMO
- programming interfaces [SQL Server replication]
- replication [SQL Server], how-to topics
- RMO [SQL Server]
- Replication Management Objects
- programming [SQL Server replication], RMO
ms.assetid: 37476d50-fb47-49e3-9504-3b163ac381d8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0dc41416e0fb585db376c6b72f28f7c30cfff052
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87664138"
---
# <a name="replication-management-objects-concepts"></a>Replication Management Objects Concepts
  Объекты RMO представляют собой сборку управляемого кода, которая инкапсулирует функциональные средства репликации для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Объекты RMO реализованы в пространстве имен <xref:Microsoft.SqlServer.Replication>.  
  
 Следующие разделы описывают использование объектов RMO для программного управления задачами репликации.  
  
 [Настройка распространения](../configure-distribution.md)  
 В подразделах этого раздела показано, как использовать объекты RMO для настройки публикации и распределения.  
  
 [Create a Publication](../publish/create-a-publication.md)  
 В подразделах этого раздела показано, как использовать объекты RMO для создания, удаления и изменения публикаций и статей.  
  
 [Подписка на публикации](../subscribe-to-publications.md)  
 В подразделах этого раздела показано, как использовать объекты RMO для создания, удаления и изменения подписок.  
  
 [Secure a Replication Topology](../security/view-and-modify-replication-security-settings.md) (Защита топологии репликации)  
 В подразделах этого раздела показано, как использовать объекты RMO для просмотра и изменения параметров безопасности.  
  
 [Synchronize Subscriptions (Replication)](../synchronize-data.md) (Синхронизация подписок (репликация))  
 В подразделах этого раздела показано, как синхронизировать подписки.  
  
 [Наблюдение за репликацией](../monitoring-replication.md)  
 В подразделах этого раздела показано, как программным путем осуществлять наблюдение за топологией репликации.  
  
## <a name="introduction-to-rmo-programming"></a>Введение в программирование объектов RMO  
 Объекты RMO предназначены для программирования всех аспектов репликации [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Пространством имен объекта RMO является <xref:Microsoft.SqlServer.Replication>, а для его реализации применяется библиотека Microsoft.SqlServer.Rmo.dll, представляющая собой сборку [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework. Сборка Microsoft.SqlServer.Replication.dll, которая также принадлежит пространству имен <xref:Microsoft.SqlServer.Replication>, реализует интерфейс управляемого кода для программирования различных агентов репликации (агента моментальных снимков, агента распространителя и агента слияния). Доступ к ее классам может быть получен из объектов RMO для синхронизации подписок. Классы в пространстве имен <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport>, реализованном с помощью сборки Microsoft.SqlServer.Replication.BusinessLogicSupport.dll, используются для создания пользовательской бизнес-логики для репликации слиянием. Эта сборка является независимой от объектов RMO.  
  
## <a name="deploying-applications-based-on-rmo"></a>Развертывание приложений на основе объектов RMO  
 Функционирование объектов RMO зависит от компонентов репликации и компонентов обмена данными с клиентом, которые включены во все версии [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], кроме SQL Server Compact. Чтобы иметь возможность развернуть приложение на основе объектов RMO, необходимо установить на компьютере, предназначенном для эксплуатации приложения, версию [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], которая включает компоненты репликации и компоненты обмена данными с клиентом.  
  
## <a name="getting-started-with-rmo"></a>Приступая к работе с объектами RMO  
 В настоящем разделе приведено описание того, как создать простой проект объекта RMO с использованием [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Studio.  
  
#### <a name="to-create-a-new-microsoft-visual-c-project"></a>Создание нового проекта Microsoft Visual C#  
  
1.  Запустите среду Visual Studio.  
  
2.  В меню **Файл** выберите пункт **Создать проект**. Откроется диалоговое окно **Создание проекта** .  
  
3.  В диалоговом окне **Типы проектов** выберите **Проекты Visual C#** . На панели **Шаблоны** выберите пункт **Приложение Windows**.  
  
4.  В поле **Имя** введите имя нового приложения (необязательно).  
  
5.  Нажмите кнопку **ОК**, чтобы загрузить шаблон Visual C# Windows.  
  
6.  В меню **Проект** выберите пункт **Добавить ссылку**. Откроется диалоговое окно **Добавление ссылки**.  
  
7.  Выберите следующие сборки из списка на вкладке **.NET**, а затем нажмите кнопку **ОК**.  
  
    -   Microsoft.SqlServer.Replication .NET Programming Interface  
  
    -   Microsoft.SqlServer.ConnectionInfo  
  
    -   Библиотека агента репликации  
  
    > [!NOTE]  
    >  Чтобы выбрать несколько файлов, удерживайте клавишу CTRL.  
  
8.  (Необязательно) Повторите шаг 6. Щелкните вкладку **Обзор[!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)], перейдите в каталог **COM, выберите файл Microsoft.SqlServer.Replication.BusinessLogicSupport.dll и нажмите кнопку **ОК**.  
  
9. В меню **Вид** выберите пункт **Код**.  
  
10. В коде перед инструкцией пространства имен введите следующие инструкции `using` для определения типов в пространстве имен RMO:  
  
    ```  
    // These namespaces are required.  
    using Microsoft.SqlServer.Replication;  
    using Microsoft.SqlServer.Management.Common;  
    // This namespace is only used when creating custom business  
    // logic for merge replication.  
    using Microsoft.SqlServer.Replication.BusinessLogicSupport;   
    ```  
  
#### <a name="to-create-a-new-microsoft-visual-basic-net-project"></a>Создание нового проекта Microsoft Visual Basic .NET  
  
1.  Запустите среду Visual Studio.  
  
2.  В меню **Файл** выберите пункт **Создать проект**. Откроется диалоговое окно **Создание проекта** .  
  
3.  На панели типов проекта выберите **Visual Basic**. На панели "Шаблоны" выберите пункт **Приложение Windows**.  
  
4.  (Необязательно.) В поле **Имя** введите имя нового приложения.  
  
5.  Нажмите кнопку **ОК**, чтобы загрузить шаблон Visual Basic Windows.  
  
6.  В меню **Проект** выберите пункт **Добавить ссылку**. Откроется диалоговое окно **Добавление ссылки**.  
  
7.  Выберите следующие сборки из списка на вкладке **.NET**, а затем нажмите кнопку **ОК**.  
  
    -   Microsoft.SqlServer.Replication .NET Programming Interface  
  
    -   Microsoft.SqlServer.ConnectionInfo  
  
    -   Библиотека агента репликации  
  
    > [!NOTE]  
    >  Чтобы выбрать несколько файлов, удерживайте клавишу CTRL.  
  
8.  (Необязательно) Повторите шаг 6. Щелкните вкладку **Обзор[!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)], перейдите в каталог **COM, выберите файл Microsoft.SqlServer.Replication.BusinessLogicSupport.dll и нажмите кнопку **ОК**.  
  
9. В меню **Вид** выберите пункт **Код**.  
  
10. В коде перед декларациями введите следующие инструкции `Imports` для определения типов в пространстве имен RMO.  
  
    ```  
    ' These namespaces are required.  
    Imports Microsoft.SqlServer.Replication  
    Imports Microsoft.SqlServer.Management.Common  
    ' This namespace is only used when creating custom business  
    ' logic for merge replication.  
    Imports Microsoft.SqlServer.Replication.BusinessLogicSupport   
    ```  
  
## <a name="connecting-to-a-replication-server"></a>Соединение с сервером репликации  
 Для программных объектов RMO требуется, чтобы соединение с экземпляром [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] было выполнено с использованием экземпляра класса <xref:Microsoft.SqlServer.Management.Common.ServerConnection>. Это соединение с сервером выполняется независимо от каких-либо программных объектов RMO. После этого соединение передается объекту RMO либо во время создания экземпляра, либо в результате присваивания свойства <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> объекту. Это позволяет создать экземпляр объекта программирования RMO независимо от объекта соединения и разделить задачи их управления. Один объект соединения можно использовать с несколькими объектами программирования RMO. Для соединений с сервером репликации действуют следующие правила.  
  
-   Все свойства соединения определяются применительно к данному конкретному объекту <xref:Microsoft.SqlServer.Management.Common.ServerConnection>.  
  
-   Соединение с каждым экземпляром [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] должно иметь свой собственный объект <xref:Microsoft.SqlServer.Management.Common.ServerConnection>.  
  
-   Объект <xref:Microsoft.SqlServer.Management.Common.ServerConnection> назначается свойству <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> программного объекта RMO, создаваемого или применяемого для доступа на сервере.  
  
-   Метод <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Connect%2A> открывает соединение с сервером. Этот метод должен быть вызван перед вызовом любых методов любых программных объектов RMO, использующих соединение, которые получают доступ к серверу.  
  
-   В объектах RMO и управляющих объектах [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (объектах SMO) используется класс <xref:Microsoft.SqlServer.Management.Common.ServerConnection> для создания соединений с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], поэтому одно и то же соединение может использоваться и объектами RMO, и объектами SMO. Дополнительные сведения см. в статье [Connecting to an Instance of SQL Server](../../server-management-objects-smo/create-program/connecting-to-an-instance-of-sql-server.md) (Соединение с экземпляром SQL Server).  
  
-   Все данные проверки подлинности, необходимые для установления соединения и входа на сервер, передаются в объекте <xref:Microsoft.SqlServer.Management.Common.ServerConnection>.  
  
-   По умолчанию используется проверка подлинности Windows. Чтобы можно было использовать проверку подлинности [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], в качестве <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.LoginSecure%2A> должно быть задано значение `false`, а свойствам <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.Login%2A> и <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.Password%2A> должны быть присвоены допустимое имя входа и пароль [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Учетные данные безопасности должны всегда храниться и обрабатываться с учетом требований безопасности и при любой возможности предоставляться только во время выполнения.  
  
-   Для многопоточных приложений в каждом потоке должен использоваться отдельный объект <xref:Microsoft.SqlServer.Management.Common.ServerConnection>.  
  
 Вызовите метод <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Disconnect%2A> объекта <xref:Microsoft.SqlServer.Management.Common.ServerConnection>, чтобы закрыть активные соединения сервера, используемые объектами RMO.  
  
## <a name="setting-rmo-properties"></a>Задание свойств объектов RMO  
 Свойства программных объектов RMO представляют свойства этих объектов репликации на сервере. При создании новых объектов репликации на сервере для определения этих объектов используются свойства объектов RMO. Для существующих объектов все свойства объектов RMO представляют свойства существующего объекта, подлежащие изменению только в части тех свойств, которым требуется установка или запись значения. Свойства могут быть заданы для новых объектов или существующих объектов.  
  
### <a name="setting-properties-for-new-replication-objects"></a>Задание свойств для новых объектов репликации  
 При создании новых объектов репликации на сервере необходимо указывать все обязательные свойства перед вызовом метода `Create` объекта. Дополнительные сведения о задании свойств для нового объекта репликации см. в статье [Настройка публикации и распространения](../configure-publishing-and-distribution.md).  
  
### <a name="setting-properties-for-existing-replication-objects"></a>Задание свойств для существующих объектов репликации  
 Применительно к объектам репликации, существующим на сервере (в зависимости от объекта), объекты RMO могут поддерживать возможность изменения некоторых или всех свойств. Могут быть изменены только свойства, предназначенные для записи или доступные для задания. Прежде чем появится возможность изменить свойства, необходимо вызвать метод `Load` или <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A>, чтобы получить текущие значения свойств с сервера. Вызов этих методов становится указанием на то, что существующий объект подлежит изменению.  
  
 По умолчанию при изменении свойства объекта в технологии RMO осуществляется фиксация этих изменений на сервере с учетом используемого режима выполнения <xref:Microsoft.SqlServer.Management.Common.ServerConnection>. Метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> может применяться для проверки того, существует ли объект на сервере, перед осуществлением попытки получения или изменения его свойств. Дополнительные сведения о свойствах объекта репликации см. в статье [Просмотр и изменение свойств издателя и распространителя](../view-and-modify-distributor-and-publisher-properties.md).  
  
> [!NOTE]  
>  Если доступ к одному и тому же объекту репликации на сервере осуществляется несколькими клиентами RMO или несколькими экземплярами одного из программных объектов RMO, то может быть вызван метод `Refresh` объекта RMO для обновления свойств с учетом текущего состояния объекта на сервере.  
  
### <a name="caching-property-changes"></a>Кэширование изменений свойств  
 Если свойство <xref:Microsoft.SqlServer.Management.Common.SqlExecutionModes> имеет значение <xref:Microsoft.SqlServer.Management.Common.SqlExecutionModes.CaptureSql>, то происходит перехват всех инструкций [!INCLUDE[tsql](../../../includes/tsql-md.md)], выработанных объектами RMO, чтобы эти инструкции можно было выполнить вручную в одном пакете с использованием одного из методов выполнения. Технология RMO позволяет кэшировать изменения свойств и фиксировать их вместе в одном пакете с использованием метода <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> объекта. Чтобы обеспечить кэширование изменений свойств, необходимо задать свойству <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> объекта значение `true`. При кэшировании изменений свойств в технологии RMO объект <xref:Microsoft.SqlServer.Management.Common.ServerConnection> по-прежнему управляет тем, когда происходит передача изменений на сервер. Дополнительные сведения о кэшировании изменений свойств объекта репликации см. в статье [Просмотр и изменение свойств издателя и распространителя](../view-and-modify-distributor-and-publisher-properties.md).  
  
> [!IMPORTANT]  
>  Безусловно, класс <xref:Microsoft.SqlServer.Management.Common.ServerConnection> поддерживает объявление явных транзакций при задании свойств, но такие транзакции могут препятствовать выполнению внутренних транзакций и вырабатывать непредвиденные результаты, поэтому не должны использоваться с объектами RMO.  
  
## <a name="example"></a>Пример  
 В этом примере демонстрируется кэширование изменений свойств. Изменения, внесенные в атрибуты публикации транзакций, кэшируются до тех пор, пока не происходит их явная отправка на сервер.  
  
 [!code-csharp[HowTo#rmo_ChangeTranPub_cached](../../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_ChangeTranPub_cached)]  
  
## <a name="see-also"></a>См. также:  
 [Replication System Stored Procedures Concepts](replication-system-stored-procedures-concepts.md)   
 [Основные понятия программирования репликации](replication-programming-concepts.md)  
  
  
