---
title: Параметры команд | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- parameters [SQL Server Native Client]
- SQL Server Native Client OLE DB provider, parameters
- SQL Server Native Client OLE DB provider, commands
- parameters [SQL Server Native Client], OLE DB
- commands [OLE DB]
ms.assetid: 072ead49-ebaf-41eb-9a0f-613e9d990f26
author: rothja
ms.author: jroth
ms.openlocfilehash: 6c00250bac3504ffb06b37aeb8c4e7eaf583c987
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87669403"
---
# <a name="command-parameters"></a>Параметры команд
  Параметры помечаются в тексте команды знаками вопроса. Например, следующая инструкция SQL помечена для одного входного параметра:  
  
```  
{call SalesByCategory('Produce', ?)}  
```  
  
 Чтобы повысить производительность за счет снижения сетевого трафика, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB собственного клиента не получает сведения о параметрах автоматически, если только не вызывается метод **ICommandWithParameters:: GetParameterInfo** или **ICommandPrepare::P готовка** перед выполнением команды. Это означает, что [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик собственного клиента OLE DB не выполняется автоматически:  
  
-   не проверяет правильность типа данных, указанного с помощью **ICommandWithParameters::SetParameterInfo**;  
  
-   не сопоставляет тип DBTYPE, указанный в данных привязки метода доступа, с правильным типом данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для параметра.  
  
 Приложения будут получать возможные ошибки или потери точности одним из этих методов, если они указывают типы данных, несовместимые с типом данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для параметра.  
  
 Чтобы гарантировать, что подобная ситуация не произойдет, для приложения необходимо:  
  
-   Проверить, совпадает ли тип данных *pwszDataSourceType* с типом данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для параметра при жестком задании метода **ICommandWithParameters::SetParameterInfo**.  
  
-   Проверить, что тип значения DBTYPE, связанного с параметром, совпадает с типом данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для жестко запрограммированного метода доступа.  
  
-   Настроить приложение для вызова метода **ICommandWithParameters::GetParameterInfo** так, чтобы поставщик мог автоматически получать типы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для параметров. Обратите внимание, что это приведет к дополнительному обмену данными с сервером.  
  
> [!NOTE]  
>  Поставщик не поддерживает вызов метода **ICommandWithParameters::GetParameterInfo** для любой инструкции [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] UPDATE или DELETE, содержащей предложение FROM; для любой инструкции SQL, которая зависит от вложенного запроса, содержащего параметры; для инструкций SQL, содержащих маркеры параметров в обоих сравниваемых выражениях или предикат с квантором; или запросов, в которых один из параметров является параметром функции. При обработке пакета инструкций SQL поставщик также не поддерживает вызов метода **ICommandWithParameters::GetParameterInfo** для маркеров параметров в выражениях после обработки первой инструкции в пакете. В команде [!INCLUDE[tsql](../../includes/tsql-md.md)] не допускаются комментарии (/* \*/).  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Поставщик OLE DB собственного клиента поддерживает входные параметры в командах инструкции SQL. При вызове команд вызывается [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB собственного клиента, поддерживающий входные, выходные и входные параметры. Значения выходных параметров возвращаются приложению либо при выполнении (только если не возвращаются наборы строк), либо когда все возвращаемые наборы строк уже использованы приложением. Чтобы проверить допустимость возвращаемых значений, используется **IMultipleResults** для принудительного потребления набора строк.  
  
 Имена параметров хранимых процедур не обязательно указывать в структуре DBPARAMBINDINFO. Используйте NULL для значения элемента *pwszName* , чтобы указать, что [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB собственного клиента должен игнорировать имя параметра и использовать только порядковый номер, указанный в члене *Ргпарамординалс* **ICommandWithParameters:: SetParameterInfo**. Если текст команды содержит как именованные, так и неименованные параметры, все неименованные параметры должны быть указаны до именованных параметров.  
  
 Если указано имя параметра хранимой процедуры, то [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB собственного клиента проверяет это имя, чтобы убедиться, что оно является допустимым. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Поставщик OLE DB собственного клиента возвращает ошибку при получении от потребителя ошибочного имени параметра.  
  
> [!NOTE]  
>  Чтобы предоставить поддержку для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] XML и определяемых пользователем типов (UDT), [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщик OLE DB собственного клиента реализует новый интерфейс [ISSCommandWithParameters](../native-client-ole-db-interfaces/isscommandwithparameters-ole-db.md) .  
  
## <a name="see-also"></a>См. также:  
 [Команды](commands.md)  
  
  
