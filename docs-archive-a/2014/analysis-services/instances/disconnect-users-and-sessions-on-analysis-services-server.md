---
title: Отключить пользователей и сеансы на Analysis Services сервере | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- ending user activity [Analysis Services]
- connections [Analysis Services]
- sessions [Analysis Services]
ms.assetid: 3b0145a2-f21d-4dd0-a09e-83afeb2ff4a9
author: minewiskan
ms.author: owend
ms.openlocfilehash: bac20b663b0a65902c70e7a3c3bfe3f27b7bf061
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731069"
---
# <a name="disconnect-users-and-sessions-on-analysis-services-server"></a>Отключение пользователей и сеансов на сервере служб Analysis Services
  Администратору служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] может понадобиться завершить пользовательские операции в процессе управления рабочей нагрузкой. Это производится путем отмены сеансов и соединений. Сеансы могут формироваться автоматически при запуске запроса (неявно) или именоваться в момент создания администратором (явно). Соединения представляют собой открытые каналы, по которым запускаются запросы. Как сеансы, так и соединения можно завершать, пока они активны. Например, администратору может потребоваться прекратить обработку для сеанса, если эта обработка продолжается слишком долго или возникли сомнения в правильности написания выполняемой команды.  
  
## <a name="ending-sessions-and-connections"></a>Завершение сеансов и соединений  
 Для управления сеансами и соединениями можно использовать динамические административные представления (DMV) и XML для аналитики (XMLA):  
  
1.  В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]подключитесь к экземпляру служб Analysis Services.  
  
2.  Вставьте один из следующих запросов к динамическим административным представлениям (DMV) в окно запроса MDX, чтобы получить список всех активных в настоящее время сеансов, соединений и выполняющихся команд.  
  
     `Select * from $System.Discover_Sessions`  
  
     `Select * from $System.Discover_Connections`  
  
     `Select * from $System.Discover_Commands`  
  
3.  Нажмите клавишу F5, чтобы выполнить запрос.  
  
     Запрос DMV возвращает информацию о сеансе и соединении в виде табличного результирующего набора, что облегчает ее чтение и копирование.  
  
 Не закрывайте окно запроса. На следующем этапе вам может понадобиться вернуться на эту страницу, чтобы скопировать SPID сеанса, который требуется отключить.  
  
 Чтобы завершить сеанс, откройте второе окно запроса XML для аналитики (XMLA).  
  
1.  Вставьте следующий синтаксис в окне запроса MDX, заменив заполнители ConnectionID, SessionID или SPID на допустимые значения, скопированные из предыдущего этапа.  
  
    ```  
    <Cancel xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
  
       <ConnectionID>111</ConnectionID>  
       <SessionID>222</SessionID>  
       <SPID>333</SPID>  
  
    <CancelAssociated>1</CancelAssociated>  
    </Cancel>  
  
    ```  
  
2.  Нажмите клавишу F5, чтобы выполнить команду отмены.  
  
 При закрытии соединения отменяются все сеансы и SPID, закрывая сеанс узла.  
  
 Завершение сеанса останавливает все команды (SPID), которые выполняются в рамках этого сеанса.  
  
 Завершение SPID отменяет определенную оценку.  
  
 В редких случаях [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] не закроет сеанс, если не сможет отследить все сеансы и SPID, связанные с соединением (например, когда несколько сеансов открыто в сценарии HTTP).  
  
 Дополнительную информацию о XMLA, упомянутом в данном разделе, см. в разделах [Метод Execute (XMLA)](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) и [Элемент Cancel (XMLA)](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/cancel-element-xmla).  
  
## <a name="see-also"></a>См. также:  
 [Управление подключениями и сеансами &#40;XMLA&#41;](../multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [Элемент BeginSession &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-headers/beginsession-element-xmla)   
 [Элемент EndSession &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-headers/endsession-element-xmla)   
 [Элемент Session (XMLA)](https://docs.microsoft.com/bi-reference/xmla/xml-elements-headers/session-element-xmla)  
  
  
