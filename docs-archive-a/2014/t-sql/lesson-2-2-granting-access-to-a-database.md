---
title: Предоставление доступа к базе данных | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- database access
ms.assetid: 686edfe2-3650-48a6-a2da-9d46fa211ad8
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 45b6d6c8dcd9c04d18489807271802aafee785b9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87667998"
---
# <a name="granting-access-to-a-database"></a>Предоставление доступа к базе данных
  Теперь Mary имеет доступ к данному экземпляру [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], но не имеет разрешения на доступ к базе данных. У нее даже нет доступа к своей базе данных по умолчанию **TestData** , пока вы не авторизируете ее в качестве пользователя базы данных.  
  
 Чтобы предоставить Mary доступ, переключитесь на базу данных **TestData** и при помощи инструкции CREATE USER сопоставьте ее имя входа с именем пользователя «Mary».  
  
### <a name="to-create-a-user-in-a-database"></a>Создание пользователя в базе данных  
  
1.  Введите и выполните следующие инструкции (заменяя `computer_name` на имя компьютера), чтобы предоставить пользователю `Mary` доступ к базе данных `TestData` .  
  
    ```  
    USE [TestData];  
    GO  
  
    CREATE USER [Mary] FOR LOGIN [computer_name\Mary];  
    GO  
  
    ```  
  
     Теперь пользователь Mary имеет доступ к [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] и к базе данных `TestData` .  
  
## <a name="next-task-in-lesson"></a>Следующая задача занятия  
 [Создание представлений и хранимых процедур](lesson-2-3-creating-views-and-stored-procedures.md)  
  
  
