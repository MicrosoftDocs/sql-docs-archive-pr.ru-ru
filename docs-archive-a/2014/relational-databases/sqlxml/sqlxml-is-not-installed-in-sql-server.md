---
title: SQLXML не установлен в SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
ms.assetid: 3dbb4f65-41de-48b8-ad62-47c9d7932de3
author: rothja
ms.author: jroth
ms.openlocfilehash: ffa4cfd8b18dbfd9b4ba05599e2a973ac5f6e888
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87665922"
---
# <a name="sqlxml-is-not-installed-in-sql-server"></a>SQLXML не установлен в SQL Server
  До версии [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] компонент SQLXML 4.0 распространялся с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и входил в состав установки по умолчанию всех версий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], кроме [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]. Начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], последняя версия SQLXML (SQLXML 4.0 с пакетом обновления 1 (SP1)) больше не включается в состав [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Чтобы установить SQLXML 4,0 с пакетом обновления 1 (SP1), когда он доступен, скачайте его из [папки установки для SQLXML SP1](https://www.microsoft.com/download/details.aspx?id=44272).  
  
 Если приложение выполняется в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и требует SQLXML 4.0, а на компьютере не установлен [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], необходимо загрузить и установить SQLXML 4.0 с пакетом обновления 1 (SP1).  
  
## <a name="sqlxml-40-sp1-behavior-with-new-data-types-using-sqloledb-and-sql-server-native-client-ole-db-provider"></a>Поведение SQLXML 4.0 при работе с новыми типами данных с помощью SQLOLEDB и поставщика OLE DB для собственного клиента SQL Server  
 В [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] добавлены следующие типы данных, которые могут использовать разработчики, применяющие SQLXML.  
  
-   `Date`  
  
-   `Time`  
  
-   `DateTime2`  
  
-   `DateTimeOffset`  
  
 При использовании SQLXML 4.0 с пакетом обновления 1 (SP1) совместно с SQLOLEDB (из компонентов Windows DAC, ранее известных как компоненты MDAC) или совместно с поставщиком [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE DB для собственного клиента [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] эти новые типы будут доступны разработчику в виде строк. SQLXML 4.0 с пакетом обновления 1 (SP1) позволяет использовать эти четыре новых типа данных в качестве встроенных скалярных типов в поставщике OLE DB версии 11.0 для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Без загрузки SQLXML 4.0 с пакетом обновления 1 (SP1) при сопоставлении этих типов с нестроковыми типами может происходить усечение и потеря части данных. Например, сопоставление `DateTime2` с `xsd:date` приведет к усечению данных до [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] `DateTime` точности 3,33 миллисекунд.  
  
## <a name="see-also"></a>См. также:  
 [Основные понятия о программировании для SQLXML 4.0](sqlxml-4-0-programming-concepts.md)  
  
  
