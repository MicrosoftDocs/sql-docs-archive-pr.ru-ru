---
title: Использование System. Transactions | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TransactionScope class
- Dispose method
- System.Transactions namespace
ms.assetid: 79656ce5-ce46-4c5e-9540-cf9869bd774b
author: rothja
ms.author: jroth
ms.openlocfilehash: 277edd75ea0437dc532ed5672e3c7b8a0569af8b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87751183"
---
# <a name="using-systemtransactions"></a>Использование System.Transactions
  Пространство имен `System.Transactions` предоставляет новую платформу транзакций, полностью интегрированную с ADO.NET и со средой CLR [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Класс `System.Transactions.TransactionScope` делает блок кода транзакционным, неявно прикрепляя соединения к распределенной транзакции. В конце блока `Complete`, перед тем, как выйти из него, необходимо вызвать метод `TransactionScope`. Когда выполнение программы покидает блок кода, вызывается метод `Dispose`, что вызывает прерывание транзакции, если не поддерживается метод `Complete`. При возникновении исключения, в результате которого исполнение кода выходит за пределы области действия, транзакция считается неподдерживаемой.  
  
 Рекомендуется использовать блок `using`, чтобы гарантировать вызов метода `Dispose` для объекта `TransactionScope` при выходе из блока `using`. Неудачная попытка зафиксировать или откатить незавершенные транзакции может значительно снизить производительность, поскольку время ожидания по умолчанию для объекта `TransactionScope` составляет одну минуту. Если инструкция `using` не используется, необходимо явно выполнить все действия в блоке `Try` и вызвать метод `Dispose` в блоке `Finally`.  
  
 Если в объекте `TransactionScope` возникает исключение, транзакция помечается как несогласованная и прерывается. При удалении объекта `TransactionScope` будет произведен ее откат. Если исключений не возникает, то участвующие транзакции будут зафиксированы.  
  
 Объект `TransactionScope` следует использовать только при осуществлении доступа к локальным и удаленным источникам данных или внешним диспетчерам ресурсов. Причина этого в том, что блок `TransactionScope` всегда вызывает повышение уровня транзакции, даже если его используют только внутри контекстного соединения.  
  
> [!NOTE]  
>  Класс `TransactionScope` создает транзакцию с уровнем изоляции `System.Transactions.Transaction.IsolationLevel`, равным `Serializable` по умолчанию. В зависимости от приложения уровень изоляции можно понижать во избежание большого количества состязаний данных в приложении.  
  
> [!NOTE]  
>  В рамках распределенных транзакций рекомендуется выполнять только операции обновления, вставки и удаления на удаленных серверах, поскольку они потребляют значительные ресурсы базы данных. Если операция будет выполняться на локальном сервере, использовать распределенную транзакцию не нужно, поскольку достаточно локальной. Инструкции SELECT могут без необходимости блокировать ресурсы базы данных, и в некоторых случаях для выборки может потребоваться использование транзакций. Любые не связанные с базой данных действия должны выполняться за пределами области транзакции, если только в ней не задействованы другие диспетчеры ресурсов транзакций. Хотя исключение в области транзакции препятствует фиксации транзакции, класс `TransactionScope` не имеет возможности отката каких-либо изменений, внесенных кодом за пределами области самой транзакции. При необходимости предпринять какие-либо действия при откате транзакции следует написать собственную реализацию интерфейса `System.Transactions.IEnlistmentNotification` и явно прикрепить его к транзакции.  
  
## <a name="example"></a>Пример  
 Для работы с `System.Transactions` необходима ссылка на файл System.Transactions.dll.  
  
 В приведенном примере программного кода демонстрируется создание транзакции, уровень которой может быть повышен в двух разных экземплярах [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Эти экземпляры представлены двумя различными объектами `System.Data.SqlClient.SqlConnection`, обернутыми в блок `TransactionScope`. В коде создается блок `TransactionScope` с инструкцией `using` и открывается первое соединение, которое автоматически прикрепляет транзакцию к блоку `TransactionScope`. Изначально транзакция прикрепляется как упрощенная, а не полностью распределенная транзакция. В коде предполагается существование условных операторов, которые для краткости опущены. При необходимости открывается второе соединение и также прикрепляется к блоку `TransactionScope`. При открытии второго соединения транзакция автоматически повышается до полностью распределенной. Затем в программе вызывается метод `TransactionScope.Complete`, который фиксирует транзакцию. При выходе из инструкций `using` для соединений эти соединения закрываются. При завершении блока `TransactionScope.Dispose` объекта `TransactionScope` в примере кода автоматически вызывается метод `using` класса `TransactionScope`. Если в любой точке блока `TransactionScope` возникло исключение, метод `Complete` вызван не будет и при удалении объекта `TransactionScope` будет произведен откат распределенной транзакции.  
  
 Visual Basic  
  
```  
Using transScope As New TransactionScope()  
    Using connection1 As New SqlConnection(connectString1)  
        ' Opening connection1 automatically enlists it in the   
        ' TransactionScope as a lightweight transaction.  
        connection1.Open()  
  
        ' Do work in the first connection.  
  
        ' Assumes conditional logic in place where the second  
        ' connection will only be opened as needed.  
        Using connection2 As New SqlConnection(connectString2)  
            ' Open the second connection, which enlists the   
            ' second connection and promotes the transaction to  
            ' a full distributed transaction.  
            connection2.Open()  
  
            ' Do work in the second connection.  
  
        End Using  
    End Using  
  
    ' Commit the transaction.  
    transScope.Complete()  
End Using  
```  
  
 C#  
  
```  
using (TransactionScope transScope = new TransactionScope())  
{  
    using (SqlConnection connection1 = new   
       SqlConnection(connectString1))  
    {  
        // Opening connection1 automatically enlists it in the   
        // TransactionScope as a lightweight transaction.  
        connection1.Open();  
  
        // Do work in the first connection.  
  
        // Assumes conditional logic in place where the second  
        // connection will only be opened as needed.  
        using (SqlConnection connection2 = new   
            SqlConnection(connectString2))  
        {  
            // Open the second connection, which enlists the   
            // second connection and promotes the transaction to  
            // a full distributed transaction.   
            connection2.Open();  
  
            // Do work in the second connection.  
        }  
    }  
    //  The Complete method commits the transaction.  
    transScope.Complete();  
}  
```  
  
## <a name="see-also"></a>См. также:  
 [Интеграция со средой CLR и транзакции](../native-client-ole-db-transactions/transactions.md)  
  
  
