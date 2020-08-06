---
title: Создание учетных данных | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- credentials [SQL Server], creating
- authentication [SQL Server], credentials
- logins [SQL Server], credentials
ms.assetid: c1e77e91-2a69-40d9-b8b3-97cffc710586
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 23221424699449ac3775b0e805bb02ae0ad233f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730393"
---
# <a name="create-a-credential"></a>Создание учетных данных
  В этом разделе описано, как создать учетные данные в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
 Учетные данные обеспечивают возможность проходить проверку подлинности [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] пользователям, имеющим удостоверение вне [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Это в первую очередь необходимо для выполнения программного кода в сборках с набором разрешений EXTERNAL_ACCESS. Учетные данные также применяются в случае, когда пользователям, использующим проверку подлинности [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , требуется доступ к ресурсам домена, например к хранилищу файлов для создания резервной копии.  
  
 Набор учетных данных может быть одновременно сопоставлен с несколькими именами входа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . С одним именем входа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] может одновременно быть сопоставлен только один набор учетных данных. После создания учетных данных в окне **Свойства имени входа (страница "Общие")** сопоставьте их с именем входа.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [Безопасность](#Security)  
  
-   **Создание учетных данных с помощью:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Ограничения  
  
-   При отсутствии учетных данных для поставщика, сопоставленных с именем входа, используются учетные данные, сопоставленные с учетной записью службы [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
-   Имени входа может быть сопоставлено несколько учетных данных, если они используются для отдельных поставщиков. У каждого поставщика должен быть только один набор учетных данных, сопоставленных одному имени входа. Одни и те же учетные данные могут быть сопоставлены нескольким именам входа.  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Требует разрешения ALTER ANY CREDENTIAL для создания или изменения учетных данных и разрешения ALTER ANY LOGIN для сопоставления имени входа с учетными данными.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-create-a-credential"></a>Создание учетных данных  
  
1.  В обозревателе объектов разверните папку **Безопасность** .  
  
2.  Щелкните правой кнопкой мыши папку **Учетные данные** и выберите команду **Создать учетные данные...** .  
  
3.  В диалоговом окне **Создание учетных данных** в поле **Учетное имя** введите имя для учетных данных.  
  
4.  В поле **Удостоверение** введите имя учетной записи, используемой для исходящих соединений (при выходе из контекста [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]). Как правило, это будет учетная запись пользователя Windows, но удостоверение может быть и учетной записью другого типа.  
  
     Либо нажмите кнопку с многоточием **(...)** , чтобы открыть диалоговое окно **Выбор пользователя или группы**.  
  
5.  В полях **Пароль** и **Подтверждение пароля** введите пароль учетной записи, указанной в поле **Удостоверение** . Если в поле **Удостоверение** указана учетная запись пользователя Windows, то это будет пароль Windows. Поле **Пароль** может быть пустым, если пароль не требуется.  
  
6.  Установите флажок **Использовать поставщика функций шифрования**, чтобы учетные данные проверялись поставщиком расширенного управления ключами. Дополнительные сведения см. в разделе [Расширенное управление ключами (EKM)](../encryption/extensible-key-management-ekm.md).  
  
7.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
  
###  <a name="to-create-a-credential"></a><a name="Credential"></a>Создание учетных данных  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    -- Creates the credential called "AlterEgo.".   
    -- The credential contains the Windows user "Mary5" and a password.  
    CREATE CREDENTIAL AlterEgo WITH IDENTITY = 'Mary5',   
        SECRET = '<EnterStrongPasswordHere>';  
    GO  
    ```  
  
 Дополнительные сведения см. в разделе [CREATE CREDENTIAL (Transact-SQL)](/sql/t-sql/statements/create-credential-transact-sql).  
  
  
