---
title: Закладки | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- bookmarks [OLE DB]
- SQL Server Native Client OLE DB provider, bookmarks
- rowsets [OLE DB], bookmarks
- OLE DB rowsets, bookmarks
ms.assetid: 7d9076f2-bf9c-452e-b816-70371a0c1644
author: rothja
ms.author: jroth
ms.openlocfilehash: be8e5486e5a442ddafa133a9cbd3f408d30a50d7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738255"
---
# <a name="bookmarks"></a>Закладки
  Закладки позволяют потребителю быстро вернуться к конкретной строке. Потребитель может получать доступ к произвольной строке с помощью закладок. Столбец закладок является столбцом номер 0 в наборе строк. Потребитель присваивает полю dwFlag в структуре привязки значение DBCOLUMNSINFO_ISBOOKMARK, чтобы указать, что столбец используется как закладка. Пользователь также присваивает свойству набора строк DBPROP_BOOKMARKS значение VARIANT_TRUE. Это позволяет столбцу с номером 0 присутствовать в наборе строк.  Затем для получения строк, начиная со строки, заданной отступом от закладки, используется метод **IRowsetLocate::GetRowsAt**.  
  
## <a name="see-also"></a>См. также:  
 [Наборы строк](rowsets.md)  
  
  
