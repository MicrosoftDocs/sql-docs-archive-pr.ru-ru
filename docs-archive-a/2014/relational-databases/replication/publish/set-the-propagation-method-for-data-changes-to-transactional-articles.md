---
title: Задание метода распространения изменений данных в транзакционные статьи | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- transactional replication, propagation methods
- propagating data changes [SQL Server replication]
ms.assetid: 0a291582-f034-42da-a1a3-29535b607b74
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a3f8be8b6df1034b06d0aaff6ee61c0c494833c5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733874"
---
# <a name="set-the-propagation-method-for-data-changes-to-transactional-articles"></a>Задание метода распространения изменений данных в транзакционные статьи
  В этом разделе описывается задание метода распространения изменений данных в транзакционных статьях в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
 По умолчанию репликация транзакций передает изменения подписчикам при помощи набора хранимых процедур для каждой статьи. Эти процедуры можно заменить на пользовательские процедуры. Дополнительные сведения см. в статье [Указание способа распространения изменений для статей транзакций](../transactional/transactional-articles-specify-how-changes-are-propagated.md).  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
-   **Для задания метода распространения изменений данных в транзакционных статьях используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
## <a name="before-you-begin"></a>Перед началом  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Ограничения  
  
-   Необходимо соблюдать осторожность при изменении любого файла моментального снимка, созданного репликацией. Необходимо тестировать и поддерживать пользовательскую логику в пользовательских хранимых процедурах. [!INCLUDE[msCoName](../../../includes/msconame-md.md)] не поддерживает настраиваемую логику.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 Укажите метод распространения на вкладке **Свойства** диалогового окна **Свойства статьи — \<Article>** , которое доступно в мастере создания публикаций и диалоговом окне **Свойства публикации — \<Publication>** . Дополнительные сведения об использовании мастера и доступе к этому диалоговому окну см. в статьях [Создание публикации](create-a-publication.md) и [Просмотр и изменение свойств публикации](view-and-modify-publication-properties.md).  
  
#### <a name="to-specify-the-propagation-method"></a>Указание метода распространения  
  
1.  На странице **Статьи** мастера создания публикаций или в диалоговом окне **Свойства публикации — \<Publication>** выберите таблицу и щелкните **Свойства статьи**.  
  
2.  Щелкните **Указать свойства выделенной статьи таблицы**.  
  
3.  На вкладке **Свойства** диалогового окна **Свойства статьи — \<Article>** в разделе **Доставка инструкций** укажите метод распространения каждой операции с помощью меню **Формат доставки инструкций INSERT**, **Формат доставки инструкций UPDATE** и **Формат доставки инструкций DELETE**.  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  Если вы находитесь в диалоговом окне **Свойства публикации — \<Publication>** , нажмите кнопку **OK**, чтобы сохранить результаты и закрыть диалоговое окно.  
  
#### <a name="to-generate-and-use-custom-stored-procedures"></a>Создание и использование пользовательских хранимых процедур  
  
1.  На странице **Статьи** мастера создания публикаций или в диалоговом окне **Свойства публикации — \<Publication>** выберите таблицу и щелкните **Свойства статьи**.  
  
2.  Щелкните **Указать свойства выделенной статьи таблицы**.  
  
     На вкладке **Свойства** диалогового окна **Свойства статьи — \<Article>** в разделе **Доставка инструкций** выберите синтаксис инструкции CALL из соответствующего меню формата доставки (**Формат доставки инструкций INSERT**, **Формат доставки инструкций UPDATE** или **Формат доставки инструкций DELETE**), а затем введите имя процедуры, чтобы использовать его в параметре **Хранимая процедура INSERT**, **Хранимая процедура DELETE** или **Хранимая процедура UPDATE**. Дополнительные сведения о синтаксисе инструкции CALL см. в разделе "Синтаксис вызова для хранимых процедур" статьи [Указание способа распространения изменений для статей транзакций](../transactional/transactional-articles-specify-how-changes-are-propagated.md).  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
4.  Если вы находитесь в диалоговом окне **Свойства публикации — \<Publication>** , нажмите кнопку **OK**, чтобы сохранить результаты и закрыть диалоговое окно.  
  
5.  Моментальный снимок, созданный для публикации, включает процедуру, заданную вами на предыдущем шаге. Процедуры будут использовать заданный вами синтаксис инструкции CALL, но при этом будут включать логику по умолчанию, используемую репликацией.  
  
     После создания моментального снимка перейдите в папку моментальных снимков, относящуюся к публикации, которой принадлежит данная статья, затем найдите файл с расширением **.sch** и с таким же именем, что и статья. Откройте этот файл при помощи программы «Блокнот» или другого текстового редактора, найдите команду CREATE PROCEDURE для вставки, обновления или удаления хранимых процедур и измените определение процедуры, чтобы указать пользовательскую логику для распространения изменений данных. Если моментальный снимок восстановлен, создайте заново пользовательскую процедуру.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
 Репликация транзакций позволяет управлять процессом распространения изменений от издателя к подписчику. Метод распространения может быть задан программным путем при создании и последующем изменении статей с помощью хранимых процедур репликации.  
  
> [!NOTE]  
>  Разным операциям DML (вставка, обновление или удаление), выполняемым над строками опубликованных данных, могут быть назначены различные методы распространения.  
  
 Дополнительные сведения см. в статье [Указание способа распространения изменений для статей транзакций](../transactional/transactional-articles-specify-how-changes-are-propagated.md).  
  
#### <a name="to-create-an-article-that-uses-transact-sql-commands-to-propagate-data-changes"></a>Создание статьи, использующей команды Transact-SQL для распространения изменений данных  
  
1.  Выполните процедуру [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql)на издателе в базе данных публикации. В параметре **\@publication** задайте имя публикации, которой принадлежит статья, в параметре **\@article** — имя статьи, в параметре **\@source_object** — базу данных, на которой опубликован объект, а для одного из следующих параметров задайте значение **SQL**.  
  
    -   **\@ins_cmd** — управляет репликацией команд [INSERT](/sql/t-sql/statements/insert-transact-sql).  
  
    -   **\@upd_cmd** — управляет репликацией команд [UPDATE](/sql/t-sql/queries/update-transact-sql).  
  
    -   **\@del_cmd** — управляет репликацией команд [DELETE](/sql/t-sql/statements/delete-transact-sql).  
  
    > [!NOTE]  
    >  При указании значения **SQL** для одного из перечисленных выше параметров репликация этого типа на подписчик будет производиться соответствующими командами [!INCLUDE[tsql](../../../includes/tsql-md.md)] .  
  
     Дополнительные сведения см. в статье [определить статью](define-an-article.md).  
  
#### <a name="to-create-an-article-that-does-not-propagate-data-changes"></a>Создание статьи, не распространяющей изменения данных  
  
1.  Выполните процедуру [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql)на издателе в базе данных публикации. В параметре **\@publication** укажите имя публикации, которой принадлежит статья, в параметре **\@article** — имя статьи, в параметре **\@source_object** — базу данных, на которой опубликован объект, а для одного из следующих параметров задайте значение **NONE**.  
  
    -   **\@ins_cmd** — управляет репликацией команд [INSERT](/sql/t-sql/statements/insert-transact-sql).  
  
    -   **\@upd_cmd** — управляет репликацией команд [UPDATE](/sql/t-sql/queries/update-transact-sql).  
  
    -   **\@del_cmd** — управляет репликацией команд [DELETE](/sql/t-sql/statements/delete-transact-sql).  
  
    > [!NOTE]  
    >  При указании значения **NONE** для одного из перечисленных выше параметров репликация команд указанного на подписчик производиться не будет.  
  
     Дополнительные сведения см. в статье [определить статью](define-an-article.md).  
  
#### <a name="to-create-an-article-with-user-modified-custom-stored-procedures"></a>Создание статьи с изменяемыми пользовательскими хранимыми процедурами  
  
1.  Выполните процедуру [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql)на издателе в базе данных публикации. В параметре **\@publication** задайте имя публикации, которой принадлежит статья, в параметре **\@article** — имя статьи, в параметре **\@source_object** — базу данных, на которой опубликован объект, а в параметре **\@schema_option** задайте битовую маску, содержащую значение **0x02** (для включения автоматического режима создания пользовательской хранимой процедуры), и хотя бы один из следующих параметров.  
  
    -   ** \@ ins_cmd** — укажите значение <strong>Call sp_MSins_*article_name*</strong>, где **_article_name_** — это значение, указанное для ** \@ статьи**.  
  
    -   ** \@ del_cmd** — укажите значение <strong>Call sp_MSdel_*article_name* </strong> или <strong>XCALL sp_MSdel_*article_name*</strong>, где **_article_name_** — это значение, заданное для _ * \@ статьи * *.  
  
    -   ** \@ upd_cmd** — укажите значение параметра <strong>*article_name*масштабируемого sp_MSupd_</strong>, <strong>вызовите sp_MSupd_*article_name*</strong>, <strong>XCALL sp_MSupd__article_name *</strong> или <strong>MCALL sp_MSupd_* article_name *</strong>, где _**article_name**_ — это значение, указанное для ** \@ статьи**.  
  
    > [!NOTE]  
    >  Для каждой из приведенных выше команд в качестве параметров можно указать собственное имя хранимых процедур, создаваемых репликацией.  
  
    > [!NOTE]  
    >  Подробные сведения о синтаксисе инструкций CALL, SCALL, XCALL и MCALL см. в статье [Указание способа распространения изменений для статей транзакций](../transactional/transactional-articles-specify-how-changes-are-propagated.md).  
  
     Дополнительные сведения см. в статье [определить статью](define-an-article.md).  
  
2.  После создания моментального снимка перейдите в папку моментальных снимков, относящуюся к публикации, которой принадлежит данная статья, затем найдите файл с расширением **.sch** и с таким же именем, что и статья. Откройте этот файл в блокноте, найдите инструкцию CREATE PROCEDURE для хранимой процедуры вставки, обновления или удаления и измените ее определение, задав пользовательскую логику распространения изменений данных. Дополнительные сведения см. в статье [Указание способа распространения изменений для статей транзакций](../transactional/transactional-articles-specify-how-changes-are-propagated.md).  
  
#### <a name="to-create-an-article-with-custom-scripting-in-the-custom-stored-procedures-to-propagate-data-changes"></a>Создание статьи, использующей пользовательские скрипты в пользовательских хранимых процедурах для распространения изменений данных  
  
1.  Выполните процедуру [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql)на издателе в базе данных публикации. В параметре **\@publication** задайте имя публикации, которой принадлежит статья, в параметре **\@article** — имя статьи, в параметре **\@source_object** — базу данных, на которой опубликован объект, а в параметре **\@schema_option** задайте битовую маску, содержащую значение **0x02** (для включения автоматического режима создания пользовательской хранимой процедуры), и хотя бы один из следующих параметров.  
  
    -   ** \@ ins_cmd** — укажите значение <strong>Call sp_MSins_*article_name*</strong>, где _**article_name**_ — это значение, указанное для ** \@ статьи**.  
  
    -   ** \@ del_cmd** — укажите значение <strong>Call sp_MSdel_*article_name* </strong> или <strong>XCALL sp_MSdel_*article_name*</strong>, где _**article_name**_ — это значение, указанное для ** \@ статьи**.  
  
    -   ** \@ upd_cmd** — укажите значение параметра <strong>масштабируемое sp_MSupd_*article_name*</strong>, <strong>вызовите sp_MSupd_*article_name*</strong>article_name, <strong>XCALL sp_MSupd_*article_name*</strong>, <strong>MCALL sp_MSupd_*article_name*</strong>, где _**article_name**_ — значение, указанное для ** \@ статьи**.  
  
    > [!NOTE]  
    >  Для каждой из приведенных выше команд в качестве параметров можно указать собственное имя хранимых процедур, создаваемых репликацией.  
  
    > [!NOTE]  
    >  Подробные сведения о синтаксисе инструкций CALL, SCALL, XCALL и MCALL см. в статье [Указание способа распространения изменений для статей транзакций](../transactional/transactional-articles-specify-how-changes-are-propagated.md).  
  
     Дополнительные сведения см. в статье [определить статью](define-an-article.md).  
  
2.  В базе данных публикации на издателе при помощи инструкции [ALTER PROCEDURE](/sql/t-sql/statements/alter-procedure-transact-sql) измените хранимую процедуру [sp_scriptpublicationcustomprocs](/sql/relational-databases/system-stored-procedures/sp-scriptpublicationcustomprocs-transact-sql) таким образом, чтобы она возвращала скрипт [CREATE PROCEDURE](/sql/t-sql/statements/create-procedure-transact-sql) пользовательских хранимых процедур для вставки, обновления и удаления. Дополнительные сведения см. в статье [Указание способа распространения изменений для статей транзакций](../transactional/transactional-articles-specify-how-changes-are-propagated.md).  
  
#### <a name="to-change-the-method-of-propagating-changes-for-an-existing-article"></a>Изменение метода распространения изменений для существующей статьи  
  
1.  Выполните процедуру [sp_changearticle](/sql/relational-databases/system-stored-procedures/sp-changearticle-transact-sql)на издателе в базе данных публикации. Задайте значения параметров **\@publication** и **\@article**, укажите значение **ins_cmd**, **upd_cmd** или **del_cmd** в параметре **\@property**, а в параметре **\@value** — необходимый метод распространения.  
  
2.  Повторите шаг 1 для каждого изменяемого метода распространения.  
  
## <a name="see-also"></a>См. также:  
 [Указание способа распространения изменений для статей транзакций](../transactional/transactional-articles-specify-how-changes-are-propagated.md)   
 [Создание публикации](create-a-publication.md)  
  
  
