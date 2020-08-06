---
title: Выгрузка DLL-библиотеки расширенной хранимой процедуры | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], unloading
- unloading extended stored procedures
ms.assetid: 4c75ab14-af54-4965-b376-8d75d385c941
author: rothja
ms.author: jroth
ms.openlocfilehash: 7bd4855390e95d949ab769d6567d6f106959dcde
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87654280"
---
# <a name="unloading-an-extended-stored-procedure-dll"></a>Выгрузка DLL-библиотеки расширенной хранимой процедуры
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Пользуйтесь вместо этого интеграцией со средой CLR.  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]загружает БИБЛИОТЕКУ DLL расширенной хранимой процедуры, как только выполняется вызов одной из функций библиотеки DLL. DLL-библиотека остается загруженной до тех пор, пока не выключается сервер или системный администратор не выгружает ее с помощью инструкции DBCC. Например, эта команда выгружает **xp_hello.dll**, позволяя системному администратору Копировать более новую версию этого файла в каталог без выключения сервера.  
  
```  
DBCC xp_hello(FREE)  
```  
  
## <a name="see-also"></a>См. также:  
 [DBCC dllname &#40;бесплатный&#41; &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-dllname-free-transact-sql)  
  
  
