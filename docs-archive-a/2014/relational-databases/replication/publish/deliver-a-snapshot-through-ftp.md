---
title: Доставка моментального снимка через FTP | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- snapshots [SQL Server replication], FTP snapshots
- FTP snapshots [SQL Server replication]
- snapshot replication [SQL Server], FTP
ms.assetid: 99872c4f-40ce-4405-8fd4-44052d3bd827
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2e6700e6989a5a7e32202a0710bc663978a136cf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87656329"
---
# <a name="deliver-a-snapshot-through-ftp"></a>Доставка моментального снимка через FTP
  В этом разделе описывается доставка моментального снимка по протоколу FTP в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
##  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Ограничения  
  
-   Агент моментальных снимков должен иметь разрешения на запись в указанный каталог, а агент распространителя или агент слияния должен иметь разрешения на чтение из этого каталога. При использовании подписок по запросу следует указать в качестве пути, соответствующего соглашению об универсальном назначении имен (UNC), общий каталог, например \\\ftpserver\home\snapshots. Дополнительные сведения см. в статье [Организация безопасности папки моментальных снимков](../security/secure-the-snapshot-folder.md).  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> Предварительные требования  
  
-   Для передачи файлов моментальных снимков с использованием протокола FTP (File Transfer Protocol) необходимо настроить FTP-сервер. Дополнительные сведения см. в документации служб IIS [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
 В целях повышения безопасности рекомендуется реализовать частную виртуальную сеть (VPN) при доставке моментальных снимков по протоколу FTP через Интернет. Дополнительные сведения см. в статье [Публикация данных через Интернет с помощью виртуальных частных сетей](../publish-data-over-the-internet-using-vpn.md).  
  
 Для обеспечения безопасности рекомендуется запретить анонимный вход на FTP-сервер. Агент моментальных снимков должен иметь разрешения на запись в указанный каталог, а агент распространителя или агент слияния должен иметь разрешения на чтение из этого каталога. При использовании подписок по запросу следует указать в качестве пути, соответствующего соглашению об универсальном назначении имен (UNC), общий каталог, например \\\ftpserver\home\snapshots. Дополнительные сведения см. в статье [Организация безопасности папки моментальных снимков](../security/secure-the-snapshot-folder.md).  
  
 По возможности запрашивайте у пользователей учетные данные в среде выполнения приложения. Если учетные данные хранятся в файле скрипта, необходимо защитить этот файл.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 После настройки FTP-сервера укажите каталог и сведения безопасности для этого сервера в диалоговом окне **Свойства публикации — \<Publication>** . Дополнительные сведения о доступе к этому диалоговому окну см. в разделе [Просмотр и изменение свойств публикации](view-and-modify-publication-properties.md).  
  
#### <a name="to-specify-ftp-information"></a>Указание сведений FTP  
  
1.  В диалоговом окне **Свойства публикации — \<Publication>** установите флажок **Разрешить подписчикам загружать файлы моментальных снимков по протоколу FTP** на одной из следующих страниц.   
    -   Страница **Моментальный снимок FTP** для публикаций моментальных снимков, публикаций транзакций и публикаций слиянием с издателей, использующих версии, предшествующие [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].    
    -   Страница **Моментальный снимок FTP и Интернет** для публикаций слиянием с издателей, использующих [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] или более позднюю версию.    
2.  Укажите значения для свойств **Имя FTP-сервера**, **Номер порта**, **Путь из корневой папки FTP**, **Имя входа**и **Пароль**.    
     Например, если корневой каталог FTP-сервера является \\\ftpserver\home и нужно, чтобы моментальные снимки хранились в \\\ftpserver\home\snapshots, укажите значение \snapshots\ftp для свойства **Путь из корневой папки FTP** (репликация присоединяет ftp к пути папки моментальных снимков при создании файлов моментальных снимков).    
3.  Укажите, что агент моментальных снимков должен записывать файлы моментальных снимков в каталог, указанный на шаге 2. Например, чтобы агент моментальных снимков записывал файлы моментальных снимков в \\\ftpserver\home\snapshots\ftp, следует указать путь \\\ftpserver\home\snapshots в одном из двух мест:    
    -   Расположение моментальных снимков по умолчанию для распространителя, связанного с этой публикацией.    
         Дополнительные сведения об указании расположения моментальных снимков по умолчанию см. [в разделе Указание расположения моментальных снимков по умолчанию](../snapshot-options.md#snapshot-folder-locations).    
    -   Альтернативное расположение папки моментальных снимков для данной публикации. Если моментальный снимок сжимается, необходимо альтернативное расположение папки.    
         Введите путь в текстовое поле **Размещение файлов в следующей папке** на странице моментальный снимок страницы **Свойства публикации — \<Publication> ** диалоговое окно.   
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
 Можно установить параметр, который сделает доступными файлы моментальных снимков на сервере, а настройки FTP можно изменить программно с помощью хранимых процедур репликации. Эта процедура зависит от типа публикации. Доставка моментальных снимков по протоколу FTP используется только с подписками по запросу.  
  
#### <a name="to-enable-ftp-snapshot-delivery-for-a-snapshot-or-transactional-publication"></a>Включение доставки моментальных снимков по протоколу FTP для публикации моментальных снимков или публикации транзакций  
  
1.  На издателе в базе данных публикации выполните хранимую процедуру [sp_addpublication](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql). Укажите **@publication** , значение `true` для **@enabled_for_internet** и соответствующие значения для следующих параметров:    
    -   **@ftp_address**— адрес FTP-сервера, используемого для доставки моментального снимка.    
    -   (Необязательно) **@ftp_port** — порт, используемый FTP-сервером.    
    -   (Необязательно) **@ftp_subdirectory** — подкаталог FTP-каталога по умолчанию, назначенный имени входа FTP. Например, если корневой каталог FTP-сервера — \\ \ftpserver\home и требуется хранить моментальные снимки в \\ \ftpserver\home\snapshots, укажите **значение \snapshots\ftp** для **@ftp_subdirectory** (репликация добавляет "FTP" в путь к папке моментальных снимков при создании файлов моментальных снимков).    
    -   (Необязательно) **@ftp_login** — Учетная запись входа, используемая при соединении с FTP-сервером.    
    -   (Необязательно) **@ftp_password** — пароль для имени входа FTP.  
  
     Таким образом создается публикация, использующая протокол FTP. Дополнительные сведения см. в разделе [Create a Publication](create-a-publication.md).  
  
#### <a name="to-enable-ftp-snapshot-delivery-for-a-merge-publication"></a>Включение доставки моментальных снимков по протоколу FTP для публикации слиянием  
  
1.  На издателе в базе данных публикации выполните процедуру [sp_addmergepublication](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql). Укажите **@publication** значение `true` для параметра **@enabled_for_internet** и соответствующие значения для следующих параметров:  
  
    -   **@ftp_address**— адрес FTP-сервера, используемого для доставки моментального снимка.    
    -   (Необязательно) **@ftp_port** — порт, используемый FTP-сервером.    
    -   (Необязательно) **@ftp_subdirectory** — подкаталог FTP-каталога по умолчанию, назначенный имени входа FTP. Например, если корневой каталог FTP-сервера — \\ \ftpserver\home и требуется хранить моментальные снимки в \\ \ftpserver\home\snapshots, укажите **значение \snapshots\ftp** для **@ftp_subdirectory** (репликация добавляет "FTP" в путь к папке моментальных снимков при создании файлов моментальных снимков).    
    -   (Необязательно) **@ftp_login** — Учетная запись входа, используемая при соединении с FTP-сервером.    
    -   (Необязательно) **@ftp_password** — пароль для имени входа FTP.  
  
     Таким образом создается публикация, использующая протокол FTP. Дополнительные сведения см. в разделе [Create a Publication](create-a-publication.md).  
  
#### <a name="to-create-a-pull-subscription-to-a-snapshot-or-transactional-publication-that-uses-ftp-snapshot-delivery"></a>Создание подписки по запросу на публикацию моментальных снимков или публикацию транзакций, использующую доставку моментальных снимков по протоколу FTP  
  
1.  На подписчике в базе данных подписки выполните хранимую процедуру [sp_addpullsubscription](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql). Укажите **@publisher** и **@publication** .  
  
    -   На подписчике в базе данных подписки выполните хранимую процедуру [sp_addpullsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql). Укажите **@publisher** , **@publisher_db** , **@publication** , [!INCLUDE[msCoName](../../../includes/msconame-md.md)] учетные данные Windows, с которыми выполняется агент распространения на подписчике **@job_login** **@job_password** , и значение `true` для **@use_ftp** .  
  
2.  Чтобы зарегистрировать подписку по запросу, выполните на издателе в базе данных публикации хранимую процедуру [sp_addsubscription](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql) . Дополнительные сведения см. в статье [Создание подписки по запросу](../create-a-pull-subscription.md).  
  
#### <a name="to-create-a-pull-subscription-to-a-merge-publication-that-uses-ftp-snapshot-delivery"></a>Создание подписки по запросу на публикацию слиянием, использующую доставку моментальных снимков по протоколу FTP  
  
1.  В базе данных подписки на издателе выполните процедуру [sp_addmergepushsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql). Укажите **@publisher** и **@publication** .   
2.  На подписчике в базе данных подписки выполните хранимую процедуру [sp_addmergepullsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql). Укажите **@publisher** , **@publisher_db** , **@publication** , учетные данные Windows, с которыми выполняется агент распространения на подписчике **@job_login** **@job_password** , и значение `true` для **@use_ftp** .    
3.  Чтобы зарегистрировать подписку по запросу, выполните на издателе в базе данных публикации хранимую процедуру [sp_addmergesubscription](/sql/relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql) . Дополнительные сведения см. в статье [Создание подписки по запросу](../create-a-pull-subscription.md).  
  
#### <a name="to-change-one-or-more-ftp-snapshot-delivery-settings-for-a-snapshot-or-transactional-publication"></a>Изменение одной или нескольких доставок моментальных снимков по протоколу FTP для публикации моментальных снимков или публикации транзакций  
  
1.  На издателе в базе данных публикации выполните процедуру [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql). Укажите одно из следующих значений для **@property** и новое значение этого параметра в параметре **@value** :    
    -   `ftp_address` — адрес FTP-сервера, который используется для доставки моментального снимка;    
    -   `ftp_port` — порт FTP-сервера;    
    -   `ftp_subdirectory` — подкаталог FTP-каталога по умолчанию, в котором хранится моментальный снимок;    
    -   `ftp_login` — имя входа для подключения к FTP-серверу;    
    -   `ftp_password` — пароль для имени входа.  
  
2.  Повторите шаг 1 для каждого изменяемого параметра FTP-соединения (необязательно).    
3.  Чтобы отключить доставку моментальных снимков по протоколу FTP, выполните на издателе в базе данных публикации хранимую процедуру [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql) (необязательно). Укажите значение в параметре `enabled_for_internet` **@property** и значение в параметре `false` **@value** .  
  
#### <a name="to-change-ftp-snapshot-delivery-settings-for-a-merge-publication"></a>Изменение настроек доставки моментальных снимков по протоколу FTP для публикации слиянием  
  
1.  В базе данных публикации на издателе выполните процедуру [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql). Укажите одно из следующих значений для **@property** и новое значение этого параметра в параметре **@value** :  
  
    -   `ftp_address` — адрес FTP-сервера, который используется для доставки моментального снимка;    
    -   `ftp_port` — порт FTP-сервера;    
    -   `ftp_subdirectory` — подкаталог FTP-каталога по умолчанию, в котором хранится моментальный снимок;   
    -   `ftp_login` — имя входа для подключения к FTP-серверу;    
    -   `ftp_password` — пароль для имени входа.    
2.  Повторите шаг 1 для каждого изменяемого параметра FTP-соединения (необязательно).    
3.  Чтобы отключить доставку моментальных снимков по протоколу FTP, выполните на издателе в базе данных публикации хранимую процедуру [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql) (необязательно). Укажите значение в параметре `enabled_for_internet` **@property** и значение в параметре `false` **@value** .  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> Примеры (Transact-SQL)  
 В следующем примере создается публикация слиянием, позволяющая подписчикам получить доступ к данным моментального снимка с помощью протокола FTP. Для доступа к общей папке FTP подписчик должен использовать защищенное VPN-соединение. Для передачи значений имени входа и пароля используются переменные скриптов**sqlcmd** . Дополнительные сведения см. в статье [Использование программы sqlcmd с переменными скрипта](../../scripting/sqlcmd-use-with-scripting-variables.md).  
  
 [!code-sql[HowTo#sp_createmergepub_ftp](../../../snippets/tsql/SQL15/replication/howto/tsql/createmergepubftp.sql#sp_createmergepub_ftp)]  
  
 В следующем примере создается подписка на публикацию слиянием, в которой подписчик получает моментальный снимок с помощью протокола FTP. Для доступа к общей папке FTP подписчик должен использовать защищенное VPN-соединение. Для передачи значений имени входа и пароля используются переменные скриптов**sqlcmd** . Дополнительные сведения см. в статье [Использование программы sqlcmd с переменными скрипта](../../scripting/sqlcmd-use-with-scripting-variables.md).  
  
 [!code-sql[HowTo#sp_createmergepullsub_ftp](../../../snippets/tsql/SQL15/replication/howto/tsql/createmergepullsubftp.sql#sp_createmergepullsub_ftp)]  
  
 [!code-sql[HowTo#sp_createmergepullsubagent_ftp](../../../snippets/tsql/SQL15/replication/howto/tsql/createmergepullsubftp.sql#sp_createmergepullsubagent_ftp)]  
  
## <a name="see-also"></a>См. также:  
 [Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md)   
 [Передавать моментальные снимки по протоколу FTP](../transfer-snapshots-through-ftp.md)   
 [Изменение свойств публикации и статьи](change-publication-and-article-properties.md)   
 [Инициализация подписки с помощью моментального снимка](../initialize-a-subscription-with-a-snapshot.md)  
  
  
