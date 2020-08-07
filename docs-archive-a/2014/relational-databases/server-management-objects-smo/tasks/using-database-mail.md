---
title: Использование Database Mail | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- e-mail [SMO]
- Database Mail [SMO]
- mail [SMO]
ms.assetid: 7605390f-b485-48cc-8d97-e364a066067b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 86ceec7417638f53427ed5a62101f2fdb6d7440a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732486"
---
# <a name="using-database-mail"></a>Использование компонента Database Mail
  В SMO подсистема компонента Database Mail представлена объектом <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail>, на который ссылается свойство <xref:Microsoft.SqlServer.Management.Smo.Server.Mail%2A>. С помощью объекта SMO <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail> можно настраивать подсистему компонента Database Mail и управлять профилями и учетными записями почты. Объект SMO <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail> принадлежит объекту `Server`, и это означает, что область действия учетных записей почты соответствует уровню сервера.  
  
## <a name="examples"></a>Примеры  
 Чтобы использовать какой-либо из представленных примеров кода, нужно выбрать среду, шаблон и язык программирования, с помощью которых будет создаваться приложение. Дополнительные сведения см. в статьях [Создание проекта Visual Basic SMO в Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) или [Создание проекта Visual C&#35; SMO в Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
 Для программ, использующих [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Database Mail, необходимо включить `Imports` инструкцию для определения пространства имен почты. Вставьте инструкцию после других инструкций `Imports` и перед любыми декларациями в приложении.  
  
 `Imports Microsoft.SqlServer.Management.Smo`  
  
 `Imports Microsoft.SqlServer.Management.Common`  
  
 `Imports Microsoft.SqlServer.Management.Smo.Mail`  
  
## <a name="creating-a-database-mail-account-by-using-visual-basic"></a>Создание учетной записи для компонента Database Mail на языке Visual Basic  
 В этом примере кода демонстрируется создание учетной записи электронной почты в объектах SMO. Компонент Database Mail представлен объектом <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail>, и на него ссылается свойство <xref:Microsoft.SqlServer.Management.Smo.Server.Mail%2A> объекта <xref:Microsoft.SqlServer.Management.Smo.Server>. Объекты SMO можно использовать для программной настройки компонента Database Mail, но не для отправления или обработки полученной почты.  
  
 VB.NET  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBMail1](SMO How to#SMO_VBMail1)]  -->  
  
## <a name="creating-a-database-mail-account-by-using-visual-c"></a>Создание учетной записи для компонента Database Mail на языке Visual C#  
 В этом примере кода демонстрируется создание учетной записи электронной почты в объектах SMO. Компонент Database Mail представлен объектом <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail>, и на него ссылается свойство <xref:Microsoft.SqlServer.Management.Smo.Server.Mail%2A> объекта <xref:Microsoft.SqlServer.Management.Smo.Server>. Объекты SMO можно использовать для программной настройки компонента Database Mail, но не для отправления или обработки полученной почты.  
  
```csharp  
{  
         //Connect to the local, default instance of SQL Server.  
         Server srv = default(Server);   
           srv = new Server();   
           //Define the Database Mail service with a SqlMail object variable   
           //and reference it using the Server Mail property.   
           SqlMail sm;   
           sm = srv.Mail;   
           //Define and create a mail account by supplying the Database Mail  
           //service, name, description, display name, and email address  
           //arguments in the constructor.   
           MailAccount a = default(MailAccount);   
           a = new MailAccount(sm, "AdventureWorks2012 Administrator", "AdventureWorks2012 Automated Mailer", "Mail account for administrative e-mail.", "dba@Adventure-Works.com");   
           a.Create();    
}  
```  
  
## <a name="creating-a-database-mail-account-by-using-powershell"></a>Создание учетной записи для компонента Database Mail в PowerShell  
 В этом примере кода демонстрируется создание учетной записи электронной почты в объектах SMO. Компонент Database Mail представлен объектом <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail>, и на него ссылается свойство <xref:Microsoft.SqlServer.Management.Smo.Server.Mail%2A> объекта <xref:Microsoft.SqlServer.Management.Smo.Server>. Объекты SMO можно использовать для программной настройки компонента Database Mail, но не для отправления или обработки полученной почты.
  
```powershell  
#Connect to the local, default instance of SQL Server.  
  
#Get a server object which corresponds to the default instance  
$srv = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Server  
  
#Define the Database Mail; reference it using the Server Mail property.  
$sm = $srv.Mail  
  
#Define and create a mail account by supplying the Database Mail service,  
#name, description, display name, and email address arguments in the constructor.  
$a = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Mail.MailAccount -ArgumentList $sm, `  
"Adventure Works Administrator", "Adventure Works Automated Mailer",`  
 "Mail account for administrative e-mail.", "dba@Adventure-Works.com"  
$a.Create()  
```  
