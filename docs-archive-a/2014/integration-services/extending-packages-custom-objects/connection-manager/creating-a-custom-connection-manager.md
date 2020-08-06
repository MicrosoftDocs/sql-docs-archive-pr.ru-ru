---
title: Создание пользовательского диспетчера подключений | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- custom connection managers [Integration Services], creating
ms.assetid: e83f8e02-ace4-42e0-b979-2f6be1460985
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 857efebbe311e5510e15cae9e78a2b424559ded7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87751312"
---
# <a name="creating-a-custom-connection-manager"></a>Создание пользовательского диспетчера соединений
  Создание пользовательского диспетчера соединений осуществляется за несколько шагов, аналогично созданию любого другого пользовательского объекта служб [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]:  
  
-   Создайте новый класс, наследующий базовый класс. Для диспетчера соединений базовым классом является <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase>.  
  
-   Примените к классу атрибут, определяющий тип объекта. Для диспетчера соединений используется атрибут <xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute>.  
  
-   Переопределите реализацию методов и свойств базового класса. Для диспетчера соединений это свойство <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ConnectionString%2A>, методы <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.AcquireConnection%2A> и <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ReleaseConnection%2A>.  
  
-   При необходимости разработайте настраиваемый пользовательский интерфейс. В случае с диспетчером соединений для этого необходимо использовать класс, реализующий интерфейс <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI>.  
  
> [!NOTE]  
>  Большая часть задач, источников и назначений в службах [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] работает только с определенными типами встроенных диспетчеров соединений. Поэтому данные образцы нельзя протестировать с помощью встроенных задач и компонентов.  
  
## <a name="getting-started-with-a-custom-connection-manager"></a>Приступая к работе над пользовательским диспетчером соединений  
  
### <a name="creating-projects-and-classes"></a>Создание проектов и классов  
 Так как все управляемые диспетчеры соединений являются производными от базового класса <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase>, на первом шаге создания пользовательского диспетчера соединений необходимо создать проект библиотеки классов на предпочитаемом языке программирования управляемого кода, а затем создать класс, наследующий от базового класса. В этом производном классе будут переопределены методы и свойства базового класса, чтобы реализовать пользовательские функциональные возможности.  
  
 Создайте в том же решении второй проект библиотеки классов для собственного пользовательского интерфейса. Для пользовательского интерфейса рекомендуется использовать отдельную сборку, что позволяет обновлять и заново развертывать диспетчер соединений или его пользовательский интерфейс независимо друг от друга.  
  
 Настройте в обоих проектах подписывание сборок, которые будут создаваться во время построения, с помощью файла ключа для строгого имени.  
  
### <a name="applying-the-dtsconnection-attribute"></a>Применение атрибута DtsConnection  
 Примените к созданному классу атрибут <xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute>, чтобы определить его в качестве диспетчера соединений. Этот атрибут содержит сведения для времени разработки, например, имя, описание и тип соединения диспетчера соединений. <xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute.ConnectionType%2A>Свойства и `Description` соответствуют **типу** и `Description` столбцам, отображаемым в диалоговом окне **Добавление диспетчера соединений со службами SSIS** , которое отображается при настройке соединений для пакета в [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] .  
  
 Используйте свойство <xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute.UITypeName%2A>, чтобы связать диспетчер соединений с его пользовательским интерфейсом. Чтобы получить токен открытого ключа, необходимый для этого свойства, можно использовать команду **sn.exe -t**, отображающую токен открытого ключа из SNK-файла пары ключей, который предназначен для подписывания сборки пользовательского интерфейса.  
  
```vb  
<DtsConnection(ConnectionType:="SQLVB", _  
  DisplayName:="SqlConnectionManager (VB)", _  
  Description:="Connection manager for Sql Server", _  
  UITypeName:="SqlConnMgrUIVB.SqlConnMgrUIVB,SqlConnMgrUIVB,Version=1.0.0.0,Culture=neutral,PublicKeyToken=<insert public key token here>")> _  
Public Class SqlConnMgrVB  
  Inherits ConnectionManagerBase  
  . . .  
End Class  
```  
  
```csharp  
[DtsConnection(ConnectionType = "SQLCS",  
  DisplayName = "SqlConnectionManager (CS)",  
  Description = "Connection manager for Sql Server",  
  UITypeName = "SqlConnMgrUICS.SqlConnMgrUICS,SqlConnMgrUICS,Version=1.0.0.0,Culture=neutral,PublicKeyToken=<insert public key token here>")]  
public class SqlConnMgrCS :  
ConnectionManagerBase  
{  
  . . .  
}  
```  
  
## <a name="building-deploying-and-debugging-a-custom-connection-manager"></a>Построение, развертывание и отладка пользовательского диспетчера соединений  
 Построение, развертывание и отладка пользовательского диспетчера соединений в службах [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] осуществляется в несколько шагов, аналогичных используемым при работе с другими типами пользовательских объектов. Дополнительные сведения см. в разделе [Сборка, развертывание и отладка пользовательских объектов](../building-deploying-and-debugging-custom-objects.md).  
  
![Значок Integration Services (маленький)](../../media/dts-16.gif "Значок служб Integration Services (маленький)")  **следит за обновлениями Integration Services**<br /> Чтобы загрузить новейшую документацию, статьи, образцы и видеоматериалы корпорации Майкрософт, а также лучшие решения участников сообщества, посетите страницу служб [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] на сайте MSDN:<br /><br /> [Посетить страницу «Службы Integration Services» на сайте MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Чтобы получать автоматические уведомления об этих обновлениях, подпишитесь на RSS-каналы, предлагаемые на этой странице.  
  
## <a name="see-also"></a>См. также:  
 [Написание кода пользовательского диспетчера соединений](coding-a-custom-connection-manager.md)   
 [Разработка пользовательского интерфейса для пользовательского диспетчера соединений](developing-a-user-interface-for-a-custom-connection-manager.md)  
  
  
