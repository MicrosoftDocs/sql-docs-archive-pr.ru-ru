---
title: Подключение к редактору запросов | Документы Майкрософт
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 48725f54-a7b6-4b79-948e-965c1fe4eef1
author: stevestein
ms.author: sstein
ms.openlocfilehash: b50783450dfb9516c78a465806ee322d7a575377
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87665726"
---
# <a name="connecting-with-query-editor"></a>Соединение с редактором запросов
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] можно писать или изменять код без соединения с сервером. Это может оказаться полезным в том случае, если сервер недоступен или требуется экономить ограниченные ресурсы сервера или сети. Можно заменить соединение с редактором запросов на соединение с новым экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , не открывая нового окна редактора запросов и не вводя код повторно.  
  
## <a name="coding-offline"></a>Программирование в режиме «вне сети»  
  
#### <a name="to-write-code-offline-and-then-connect-to-different-servers"></a>Написание программы в режиме «вне сети» с последующим подключением к различным серверам  
  
1.  На панели инструментов среды [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] нажмите кнопку **Запрос к ядру СУБД** , чтобы открыть редактор запросов.  
  
2.  В диалоговом окне **Подключиться к компоненту Database Engine** нажмите кнопку **Отмена**. Будет открыт редактор запросов, в строке заголовка которого будет указано, что соединение с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]не установлено.  
  
3.  В панели кода введите следующие инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] :  
  
    ```  
    SELECT * FROM Production.Product;  
    GO  
    ```  
  
     На этом этапе можно подключиться к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , выбрав команды **Подключиться**, **Выполнить**, **Выполнить анализ**или **Показать предполагаемый план выполнения**, которые доступны в меню **Запрос** , на панели инструментов редактора запросов или в контекстном меню, открывающемся при щелчке правой кнопкой мыши в окне редактора запросов. В этом практическом занятии будет использована панель инструментов.  
  
4.  На панели инструментов нажмите кнопку **Выполнить** , чтобы открыть диалоговое окно **Подключиться к компоненту Database Engine** .  
  
5.  В текстовом поле **Имя сервера** введите имя сервера, а затем нажмите кнопку **Параметры**.  
  
6.  На вкладке **Свойства соединения** в списке **Соединение с базой данных** найдите на сервере базу данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] и нажмите кнопку **Соединить**.  
  
7.  Чтобы открыть другое окно редактора запросов для того же соединения, на панели инструментов нажмите кнопку **Создать запрос**.  
  
8.  Чтобы сменить соединения, щелкните правой кнопкой мыши окно редактора запросов, наведите указатель на пункт **Соединение**и выберите команду **Изменить соединение**.  
  
9. В диалоговом окне **Подключение к SQL Server** выберите другой экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при его наличии, а затем нажмите кнопку **Соединить**.  
  
 Эта новая возможность, предоставляемая редактором запросов, позволяет легко запускать один и тот же код на нескольких серверах. Это может быть полезно при обслуживании нескольких схожих серверов.  
  
## <a name="next-task-in-lesson"></a>Следующая задача занятия  
 [Добавление отступов](lesson-2-2-adding-indentation.md)  
  
  