---
title: Поддержка локальных транзакций | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- autocommit mode
- transactions [OLE DB]
- ITransactionLocal interface
- SQL Server Native Client OLE DB provider, transactions
- local transactions [OLE DB]
ms.assetid: 78f2e5fc-b6fb-4eda-9f71-991a4d6c4902
author: rothja
ms.author: jroth
ms.openlocfilehash: a9bc11a038e56517aa42619117c371c1319b9ffe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87667043"
---
# <a name="supporting-local-transactions"></a>Поддержка локальных транзакций
  Сеанс разделяет область действия транзакции для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента OLE DB локальной транзакции поставщика. Если, в направлении потребителя, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB собственного клиента отправляет запрос к подключенному экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , запрос создает единицу работы для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика собственного клиента OLE DB. Локальные транзакции всегда заключают одну или несколько единиц работы на один [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственный клиент OLE DBного сеанса поставщика.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]При использовании режима автоматической фиксации поставщика OLE DB собственного клиента по умолчанию одна единица работы рассматривается как область локальной транзакции. В локальной транзакции участвует только одна единица работы. При создании сеанса [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB собственного клиента начинает транзакцию для сеанса. При успешном завершении единицы работы выполненная работа фиксируется. При сбое выполняется откат всей начатой работы; потребителю сообщается об ошибке. В любом случае [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB собственного клиента начинает новую локальную транзакцию для сеанса, чтобы вся работа выполнялась в рамках транзакции.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Потребитель поставщика OLE DB собственного клиента может направить более точный контроль над областью локальной транзакции с помощью интерфейса **ITransactionLocal** . Если сеанс потребителя инициирует транзакцию, все рабочие единицы сеанса между точкой начала транзакции и последующими неизбежными вызовами методов **Commit** или **Abort** рассматриваются как единая операция. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Поставщик OLE DB собственного клиента неявным образом начинает транзакцию, когда она направляется потребителю. Если потребитель не запрашивает хранения, сеанс восстанавливает режим родительской транзакции. Как правило, это режим автозавершения.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Поставщик OLE DB собственного клиента поддерживает параметры **ITransactionLocal:: StartTransaction** , как показано ниже.  
  
|Параметр|Описание|  
|---------------|-----------------|  
|*isoLevel*[in]|Уровень изоляции, который должен использоваться с этой транзакцией. В локальных транзакциях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик собственного клиента OLE DB поддерживает следующие действия:<br /><br /> — ISOLATIONLEVEL_UNSPECIFIED<br />— ISOLATIONLEVEL_CHAOS<br />— ISOLATIONLEVEL_READUNCOMMITTED<br />— ISOLATIONLEVEL_READCOMMITTED<br />— ISOLATIONLEVEL_REPEATABLEREAD<br />— ISOLATIONLEVEL_CURSORSTABILITY<br />— ISOLATIONLEVEL_REPEATABLEREAD<br />— ISOLATIONLEVEL_SERIALIZABLE<br />— ISOLATIONLEVEL_ISOLATED<br />-ISOLATIONLEVEL_SNAPSHOT **Примечание.** начиная с [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] версии, ISOLATIONLEVEL_SNAPSHOT является допустимым для аргумента *isoLevel* , независимо от того, включено ли управление версиями для базы данных. Однако произойдет ошибка, если пользователь попытается выполнить инструкцию, когда управление версиями не включено, а база данных предназначена не только для чтения. Кроме того, ошибка XACT_E_ISOLATIONLEVEL возникнет, если для *isoLevel* задано значение ISOLATIONLEVEL_SNAPSHOT при соединении с версией [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ранее [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].|  
|*isoFlags*[in]|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Поставщик OLE DB собственного клиента возвращает ошибку для любого значения, отличного от нуля.|  
|*pOtherOptions*[in]|Если значение не равно NULL, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB собственного клиента запрашивает объект параметров из интерфейса. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Поставщик OLE DB собственного клиента возвращает XACT_E_NOTIMEOUT, если элемент *ултимеаут* объекта параметров не равен нулю. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Поставщик OLE DB собственного клиента игнорирует значение элемента *сздескриптион* .|  
|*pulTransactionLevel*[out]|Если значение не равно NULL, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB собственного клиента возвращает вложенный уровень транзакции.|  
  
 Для локальных транзакций [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB собственного клиента реализует параметры **ITransaction:: Abort** , как показано ниже.  
  
|Параметр|Описание|  
|---------------|-----------------|  
|*pboidReason*[in]|При установке не учитывается. Может иметь значение NULL.|  
|*fRetaining*[in]|Если задано значение TRUE, то для сеанса неявным образом запускается новая транзакция. Эта транзакция должна быть зафиксирована или завершена объектом-получателем. Если значение равно "FALSE", [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB собственного клиента возвращается в режим автоматической фиксации для сеанса.|  
|*fAsync*[in]|Асинхронное прерывание не поддерживается [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщиком собственного клиента OLE DB. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Поставщик OLE DB собственного клиента возвращает XACT_E_NOTSUPPORTED, если значение не равно false.|  
  
 Для локальных транзакций [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик собственного клиента OLE DB реализует параметры **ITransaction:: Commit** , как показано ниже.  
  
|Параметр|Описание|  
|---------------|-----------------|  
|*fRetaining*[in]|Если задано значение TRUE, то для сеанса неявным образом запускается новая транзакция. Эта транзакция должна быть зафиксирована или завершена объектом-получателем. Если значение равно "FALSE", [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB собственного клиента возвращается в режим автоматической фиксации для сеанса.|  
|*grfTC*[in]|Асинхронные и одноэтапные возвраты не поддерживаются [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщиком собственного клиента OLE DB. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Поставщик OLE DB собственного клиента возвращает XACT_E_NOTSUPPORTED для любого значения, кроме XACTTC_SYNC.|  
|*grfRM*[in]|Должно быть равно 0.|  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Наборы строк поставщика собственного клиента OLE DB в сеансе сохраняются в локальной операции фиксации или прерывания на основе значений свойств набора строк DBPROP_ABORTPRESERVE и DBPROP_COMMITPRESERVE. По умолчанию эти свойства VARIANT_FALSE и все [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] наборы строк поставщика собственного клиента OLE DB в сеансе теряются после операции прерывания или фиксации.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Поставщик OLE DB собственного клиента не реализует интерфейс **итрансактионобжект** . При попытке потребителя получить ссылку на интерфейс возвращается E_NOINTERFACE.  
  
 В этом примере используется интерфейс **ITransactionLocal**.  
  
```  
// Interfaces used in the example.  
IDBCreateSession*   pIDBCreateSession   = NULL;  
ITransaction*       pITransaction       = NULL;  
IDBCreateCommand*   pIDBCreateCommand   = NULL;  
IRowset*            pIRowset            = NULL;  
  
HRESULT             hr;  
  
// Get the command creation and local transaction interfaces for the  
// session.  
if (FAILED(hr = pIDBCreateSession->CreateSession(NULL,  
     IID_IDBCreateCommand, (IUnknown**) &pIDBCreateCommand)))  
    {  
    // Process error from session creation. Release any references and  
    // return.  
    }  
  
if (FAILED(hr = pIDBCreateCommand->QueryInterface(IID_ITransactionLocal,  
    (void**) &pITransaction)))  
    {  
    // Process error. Release any references and return.  
    }  
  
// Start the local transaction.  
if (FAILED(hr = ((ITransactionLocal*) pITransaction)->StartTransaction(  
    ISOLATIONLEVEL_REPEATABLEREAD, 0, NULL, NULL)))  
    {  
    // Process error from StartTransaction. Release any references and  
    // return.  
    }  
  
// Get data into a rowset, then update the data. Functions are not  
// illustrated in this example.  
if (FAILED(hr = ExecuteCommand(pIDBCreateCommand, &pIRowset)))  
    {  
    // Release any references and return.  
    }  
  
// If rowset data update fails, then terminate the transaction, else  
// commit. The example doesn't retain the rowset.  
if (FAILED(hr = UpdateDataInRowset(pIRowset, bDelayedUpdate)))  
    {  
    // Get error from update, then terminate.  
    pITransaction->Abort(NULL, FALSE, FALSE);  
    }  
else  
    {  
    if (FAILED(hr = pITransaction->Commit(FALSE, XACTTC_SYNC, 0)))  
        {  
        // Get error from failed commit.  
        }  
    }  
  
if (FAILED(hr))  
    {  
    // Update of data or commit failed. Release any references and  
    // return.  
    }  
  
// Release any references and continue.  
```  
  
## <a name="see-also"></a>См. также:  
 [Транзакции](transactions.md)   
 [Работа с изоляцией моментального снимка](../native-client/features/working-with-snapshot-isolation.md)  
  
  
