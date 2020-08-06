---
title: И изменения, внесенные в журнал | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- text columns [ODBC]
- SQL Server Native Client ODBC driver, image columns
- SQL Server Native Client ODBC driver, text columns
- data types [ODBC], image
- data types [ODBC], text
- logged vs. nonlogged modifications [SQL Server Native Client]
- columns [ODBC]
- ODBC data types, image columns
- nonlogged vs. logged modifications
- ODBC data types, text columns
- image columns [ODBC]
ms.assetid: 20aa5b27-4a2c-46e7-8356-beb0eebf4b7e
author: rothja
ms.author: jroth
ms.openlocfilehash: 8768acc75d18ea2236f0e9280e5d0c805e688107
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87750839"
---
# <a name="logged-vs-unlogged-modifications"></a>Изменения с ведением журнала и без ведения журнала
  Приложение может запрашивать, что [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента не регистрирует изменения типа **Text**, **ntext**и **Image** . Однако этот режим следует использовать очень осторожно. Его следует использовать только в тех случаях, когда данные типа **Text**, **ntext**или **Image** не являются критически важными, а владельцы данных готовы выдавать возможность восстанавливать данные для повышения производительности.  
  
 Ведение журнала изменений типа **Text**, **ntext**и **Image** контролируется путем вызова [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md) с параметром *атрибута* , для которого задано значение SQL_SOPT_SS_ TEXTPTR_LOGGING и *ValuePtr* задано значение либо SQL_TL_ON, либо SQL_TL_OFF.  
  
## <a name="see-also"></a>См. также:  
 [Управление столбцами text и image](managing-text-and-image-columns.md)  
  
  
