---
title: Определение сопоставителя статей публикации слиянием | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- articles [SQL Server replication], conflict resolution
- conflict resolution [SQL Server replication], merge replication
- merge replication conflict resolution [SQL Server replication], merge article resolvers
ms.assetid: a40083b3-4f7b-4a25-a5a3-6ef67bdff440
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ca32ef4936f31ca5c75dfc2df1eb965d17f7b039
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733878"
---
# <a name="specify-a-merge-article-resolver"></a>Определение сопоставителя статей публикации слиянием
  В этом разделе описывается определение арбитра статей публикации слиянием в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Рекомендации](#Recommendations)  
  
-   **Для определения арбитра статей публикации слиянием используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> Рекомендации  
  
-   Репликация слиянием допускает следующие типы сопоставителей статей:  
  
    -   Сопоставитель по умолчанию. Поведение сопоставителя по умолчанию зависит от того, является подписка клиентской или серверной. Дополнительные сведения об указании типа подписки см. в статье [Указание типа подписки слиянием и приоритета устранения конфликтов](../specify-a-merge-subscription-type-and-conflict-resolution-priority.md).  
  
    -   Пользовательский сопоставитель, который может быть обработчиком бизнес-логики (написанным на управляемом коде), или пользовательским, основанным на технологии COM. Дополнительные сведения см. в разделе [Advanced Merge Replication Conflict Detection and Resolution](../merge/advanced-merge-replication-conflict-detection-and-resolution.md). Если требуется применить пользовательскую логику, исполняемую для каждой реплицируемой строки, а не только для конфликтующих строк, см. раздел [Реализация обработчика бизнес-логики для статьи публикации слиянием](../implement-a-business-logic-handler-for-a-merge-article.md).  
  
    -   Стандартный арбитр, основанный на COM, который входит в состав [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   Чтобы использовать сопоставитель, отличный от сопоставителя по умолчанию, необходимо скопировать сопоставитель на компьютер, на котором выполняется агент слияния, и зарегистрировать его (если используется обработчик бизнес-логики, он также должен быть зарегистрирован на издателе). Агент слияния выполняется на:  
  
    -   распространителе для принудительной подписки;  
  
    -   подписчике для подписки по запросу;  
  
    -   IIS-сервер [!INCLUDE[msCoName](../../../includes/msconame-md.md)] для подписки по запросу, которая использует веб-синхронизацию  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 После регистрации сопоставителя дайте указание статье использовать сопоставитель на вкладке **Сопоставитель** диалогового окна **Свойства статьи — \<Article>** , которое доступно в мастере создания публикаций и в диалоговом окне **Свойства публикации — \<Publication>** . Дополнительные сведения об использовании мастера и доступе к этому диалоговому окну см. в статьях [Создание публикации](create-a-publication.md) и [Просмотр и изменение свойств публикации](view-and-modify-publication-properties.md).  
  
#### <a name="to-specify-a-resolver"></a>Указание сопоставителя  
  
1.  На странице **Статьи** мастера создания публикаций или в диалоговом окне **Свойства публикации — \<Publication>** выберите таблицу.  
  
2.  Щелкните **Свойства статьи**, затем щелкните **Указать свойства выделенной статьи таблицы**.  
  
3.  На странице **Свойства статьи — \<Article>** щелкните вкладку **Сопоставитель**.  
  
4.  Выберите **Использовать пользовательский сопоставитель (зарегистрированный на распространителе):** , затем щелкните в списке сопоставитель.  
  
5.  Если сопоставитель запрашивает входные данные (такие, как имя столбца), укажите их в текстовом поле **Введите данные, необходимые сопоставителю** .  
  
6.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
7.  Повторите этот процесс для каждой статьи, которая запрашивает сопоставитель.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-register-a-custom-conflict-resolver"></a>Регистрация пользовательского сопоставителя конфликтов  
  
1.  Если планируется зарегистрировать собственный пользовательский сопоставитель конфликтов, создайте один из следующих типов.  
  
    -   Сопоставитель на основе управляемого кода в качестве обработчика бизнес-логики. Дополнительные сведения см. в статье [Реализация обработчика бизнес-логики для статьи публикации слиянием](../implement-a-business-logic-handler-for-a-merge-article.md).  
  
    -   Арбитр на основе хранимых процедур и арбитр на основе COM. Дополнительные сведения см. в разделе [Реализация пользовательского арбитра конфликтов для статьи публикации слиянием](../implement-a-custom-conflict-resolver-for-a-merge-article.md).  
  
2.  Чтобы определить, зарегистрирован ли нужный сопоставитель, выполните хранимую процедуру [sp_enumcustomresolvers (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql) на издателе для любой базы данных. Будет выведено описание пользовательского сопоставителя, а также идентификатор класса (CLSID) для каждого сопоставителя на основе COM, зарегистрированного на распространителе, или сведения об управляемой сборке для каждого обработчика бизнес-логики, зарегистрированного на распространителе.  
  
3.  Если нужный пользовательский сопоставитель еще не зарегистрирован, выполните хранимую процедуру [sp_registercustomresolver (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-registercustomresolver-transact-sql) на распространителе. Укажите имя распознавателя **@article_resolver** ; для обработчика бизнес-логики это понятное имя сборки. Для арбитров конфликтов на основе COM укажите CLSID библиотеки DLL для **@resolver_clsid** , а для обработчика бизнес-логики укажите значение `true` для, **@is_dotnet_assembly** имя сборки для **@dotnet_assembly_name** и полное имя класса, переопределяющий <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> для **@dotnet_class_name** .  
  
    > [!NOTE]  
    >  Если сборка обработчика бизнес-логики не развернута в том же каталоге, что и исполняемый файл агент слияния, в том же каталоге, что и приложение, синхронно запускающее агент слияния, или в глобальном кэше сборок (GAC), необходимо указать полный путь с именем сборки для **@dotnet_assembly_name** .  
  
4.  Если сопоставитель является сопоставителем на основе COM, сделайте следующее.  
  
    -   Скопируйте DLL-библиотеку пользовательского сопоставителя на распространитель для принудительных подписок либо на подписчик для подписок по запросу.  
  
        > [!NOTE]  
        >  Пользовательские сопоставители[!INCLUDE[msCoName](../../../includes/msconame-md.md)] можно найти в каталоге COM [!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)].  
  
    -   Используйте файл regsvr32.exe, чтобы зарегистрировать DLL-библиотеку пользовательского сопоставителя в операционной системе. Например, чтобы зарегистрировать аддитивный сопоставитель конфликтов [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , введите в командной строке следующее.  
  
        ```  
        regsvr32 ssradd.dll  
        ```  
  
5.  Если сопоставитель является обработчиком бизнес-логики, разверните сборку в той же папке, где находится агент слияния исполняемый файл (replmerg.exe), в той же папке, что и приложение, вызывающее агент слияния, или в папке, указанной для **@dotnet_assembly_name** параметра на шаге 3.  
  
    > [!NOTE]  
    >  Местом установки по умолчанию исполняемого файла агента слияния является [!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)]COM.  
  
#### <a name="to-specify-a-custom-resolver-when-defining-a-merge-article"></a>Указание пользовательского сопоставителя при определении статьи публикации слиянием  
  
1.  Если планируется использовать собственный пользовательский сопоставитель конфликтов, создайте и зарегистрируйте сопоставитель с помощью описанной выше процедуры.  
  
2.  На издателе выполните хранимую процедуру [sp_enumcustomresolvers (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql) и запомните имя нужного пользовательского сопоставителя в поле **value** результирующего набора.  
  
3.  В базе данных публикации на издателе выполните процедуру [sp_addmergearticle (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql). Укажите имя распознавателя из шага 2 для **@article_resolver** и все необходимые входные данные для пользовательского сопоставителя с помощью **@resolver_info** параметра. Для пользовательских арбитров конфликтов на основе хранимых процедур **@resolver_info** — это имя хранимой процедуры. Дополнительные сведения о необходимых входных данных для сопоставителей, предоставляемых [!INCLUDE[msCoName](../../../includes/msconame-md.md)], см. в статье о [сопоставителях на базе технологии Microsoft COM](../merge/advanced-merge-replication-conflict-com-based-resolvers.md).  
  
#### <a name="to-specify-or-change-a-custom-resolver-for-an-existing-merge-article"></a>Указание или изменение пользовательского сопоставителя для существующей статьи публикации слиянием  
  
1.  Чтобы выяснить, был ли пользовательский сопоставитель определен для статьи, или чтобы получить имя арбитра, выполните хранимую процедуру [sp_helpmergearticle (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql). Если для статьи был определен пользовательский сопоставитель, его имя отобразится в поле **article_resolver** . Любые входные данные, переданные сопоставителю, будут отображены в поле **resolver_info** результирующего набора.  
  
2.  На издателе выполните хранимую процедуру [sp_enumcustomresolvers (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql) и запомните имя нужного пользовательского сопоставителя в поле **value** результирующего набора.  
  
3.  В базе данных публикации на издателе выполните процедуру [sp_changemergearticle (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql). Укажите значение для **article_resolver**, включая полный путь к обработчику бизнес-логики, в параметре **@property**, и имя нужного пользовательского сопоставителя из шага 2 в параметре **@value**.  
  
4.  Чтобы изменить какие-либо необходимые входные данные для пользовательского сопоставителя, выполните хранимую процедуру [sp_changemergearticle (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql) еще раз. Укажите значение для **resolver_info** в параметре **@property** и любые необходимые входные данные для пользовательского сопоставителя в параметре **@value**. Для пользовательских арбитров конфликтов на основе хранимых процедур **@resolver_info** — это имя хранимой процедуры. Дополнительные сведения о необходимых входных данных см. в статье о [сопоставителях на базе технологии Microsoft COM](../merge/advanced-merge-replication-conflict-com-based-resolvers.md).  
  
#### <a name="to-unregister-a-custom-conflict-resolver"></a>Отмена регистрации пользовательского сопоставителя конфликтов  
  
1.  На издателе выполните хранимую процедуру [sp_enumcustomresolvers (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql) и запомните имя пользовательского сопоставителя, которое нужно удалить, в поле **value** результирующего набора.  
  
2.  Выполните процедуру [sp_unregistercustomresolver (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-unregistercustomresolver-transact-sql) на распространителе. Укажите полное имя пользовательского сопоставителя из шага 1 в параметре **@article_resolver** .  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> Примеры (Transact-SQL)  
 В этом примере создается новая статья и указывается, что усредняющий сопоставитель конфликтов [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] при возникновении конфликта должен использоваться для вычисления среднего значения в столбце **UnitPrice** .  
  
 [!code-sql[HowTo#sp_addmerge_resolver](../../../snippets/tsql/SQL15/replication/howto/tsql/mergearticleresolvers.sql#sp_addmerge_resolver)]  
  
 В этом примере изменяется статья и указывается, что аддитивный сопоставитель конфликтов [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] при возникновении конфликта должен использоваться для вычисления суммы значений в столбце **UnitsOnOrder** .  
  
 [!code-sql[HowTo#sp_changemerge_resolver](../../../snippets/tsql/SQL15/replication/howto/tsql/mergearticleresolvers.sql#sp_changemerge_resolver)]  
  
## <a name="see-also"></a>См. также:  
 [Advanced Merge Replication Conflict Detection and Resolution](../merge/advanced-merge-replication-conflict-detection-and-resolution.md)   
 [Реализация обработчика бизнес-логики для статьи публикации слиянием](../implement-a-business-logic-handler-for-a-merge-article.md)  
  
  
