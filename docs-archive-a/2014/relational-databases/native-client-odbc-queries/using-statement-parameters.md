---
title: Использование параметров инструкции | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, parameters
- parameters [SQL Server Native Client], ODBC
- ODBC, parameters
- statements [ODBC], parameters
- parameter markers [ODBC]
- SQL Server Native Client ODBC driver, statements
- ODBC applications, statements
ms.assetid: 2427d886-ec6c-49d7-b0b6-0d998b64cdb9
author: rothja
ms.author: jroth
ms.openlocfilehash: 7b7e207416e60af94efd59555980a0edff68a38b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87655111"
---
# <a name="using-statement-parameters"></a>Использование параметров инструкции
  Параметр — это переменная в инструкции SQL, позволяющая в приложении ODBC осуществлять следующее.  
  
-   Эффективно передавать значения для столбцов таблицы.  
  
-   Повышать степень взаимодействия с пользователем при конструировании критериев запроса.  
  
-   Управление данными типа **Text**, **ntext**и **Image** и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] конкретными типами данных C.  
  
 Например, таблица **Parts** содержит столбцы с именами **PartID**, **Description**и **Price**. Для добавления компонента без параметров необходимо составить инструкцию SQL, например:  
  
```  
INSERT INTO Parts (PartID, Description, Price) VALUES (2100, 'Drive shaft', 50.00)  
```  
  
 Эта инструкция вполне подходит для вставки одной строки с заранее известным набором значений, но если в приложении необходимо вставить несколько строк, она становится менее приемлемой. Поэтому в ODBC разрешается заменять в приложении любое значение данных в инструкции SQL маркером параметра. Он обозначается вопросительным знаком (?). В следующем примере маркерами параметров заменены три значения данных.  
  
```  
INSERT INTO Parts (PartID, Description, Price) VALUES (?, ?, ?)  
```  
  
 Затем происходит привязка маркеров параметров к переменным приложения. Для вставки новой строки в приложении достаточно только задать значения параметров и выполнить инструкцию. После этого драйвер получает текущие значения переменных и передает их в источник данных. Если инструкция выполняется неоднократно, то в приложении можно дополнительно оптимизировать этот процесс с помощью подготовки инструкции.  
  
 Ссылка на каждый маркер параметра осуществляется по порядковому номеру; параметры нумеруются слева направо. Первый слева параметр в инструкции SQL имеет порядковый номер 1; следующий — 2 и т. д.  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Привязка параметров](using-statement-parameters-binding-parameters.md)  
  
## <a name="see-also"></a>См. также:  
 [Выполняя запросы &#40;ODBC&#41;](executing-queries-odbc.md)  
  
  
