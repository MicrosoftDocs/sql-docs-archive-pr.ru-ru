---
title: Функции с массовым копированием | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, bulk copy
- bulk copy [ODBC], functions
- ODBC, bulk copy operations
- functions [ODBC]
ms.assetid: 6526b892-1d58-4f55-8335-f09887f6ea02
author: rothja
ms.author: jroth
ms.openlocfilehash: 02dba8cf4d510d2ec5f20e600302bb692c749f97
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87665317"
---
# <a name="bulk-copy-functions"></a>Bulk Copy Functions
  Зависящее от [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] расширение API-интерфейса массового копирования драйвера ODBC собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] позволяет клиентскому приложению быстро добавлять или извлекать строки данных из таблицы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 При использовании [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client вы можете ссылаться на функции массового копирования (BCP), объявленные в файлах SQLNCLI11.LIB и SQLNCLI.H.  
  
 Приложение, использующее вызовы функции BCP API, необходимо связать с библиотекой (LIB-файлом), которая поставлялась с драйвером (DLL-файлом), используемым приложением. Приложение BCP не должно быть связано более чем с одной библиотекой драйвера.  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [bcp_batch](bcp-batch.md)  
  
-   [bcp_bind](bcp-bind.md)  
  
-   [bcp_colfmt](bcp-colfmt.md)  
  
-   [bcp_collen](bcp-collen.md)  
  
-   [bcp_colptr](bcp-colptr.md)  
  
-   [bcp_columns](bcp-columns.md)  
  
-   [bcp_control](bcp-control.md)  
  
-   [bcp_done](bcp-done.md)  
  
-   [bcp_exec](bcp-exec.md)  
  
-   [bcp_getcolfmt](bcp-getcolfmt.md)  
  
-   [bcp_gettypename](bcp-gettypename.md)  
  
-   [bcp_init](bcp-init.md)  
  
-   [bcp_moretext](bcp-moretext.md)  
  
-   [bcp_readfmt](bcp-readfmt.md)  
  
-   [bcp_sendrow](bcp-sendrow.md)  
  
-   [bcp_setbulkmode](bcp-setbulkmode.md)  
  
-   [bcp_setcolfmt](bcp-setcolfmt.md)  
  
-   [Функция bcp_writefmt](bcp-writefmt.md)  
  
## <a name="see-also"></a>См. также:  
 [Расширения драйверов SQL Server](../../database-engine/dev-guide/sql-server-driver-extensions.md)   
 [Выполнение операций с массовым копированием &#40;ODBC&#41;](../native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md)  
  
  
