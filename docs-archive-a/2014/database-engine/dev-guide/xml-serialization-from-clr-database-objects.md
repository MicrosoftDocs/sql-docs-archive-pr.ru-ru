---
title: Сериализация XML из объектов базы данных CLR | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
helpviewer_keywords:
- serialization
- XML serialization [CLR integration]
- common language runtime [SQL Server], XML serialization
- XmlSerializer class
ms.assetid: ac84339b-9384-4710-bebc-01607864a344
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: ee93ee4b7bf9cba3f11b329244d4523636cb7704
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732974"
---
# <a name="xml-serialization-from-clr-database-objects"></a>Сериализация XML из объектов базы данных CLR
  XML-сериализация используется в двух случаях:  
  
-   при вызове веб-служб из объектов среды CLR;  
  
-   для преобразования определяемого пользователем типа данных в XML.  
  
 Выполнение XML-сериализации с помощью вызова класса `XmlSerializer` обычно создает дополнительную сборку сериализации, перегружаемую в проект, содержащий исходную сборку.  Однако в целях безопасности в CLR эта перегрузка отключена. Таким образом, чтобы вызвать веб-службу или выполнить преобразование из определяемого пользователем типа в XML внутри [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , сборка должна быть создана вручную с помощью средства с именем **Sgen.exe** , предоставляемого .NET Framework, который создает необходимые сборки сериализации. При вызове класса `XmlSerializer` следует создать сборку сериализации вручную, проделав следующие шаги:  
  
1.  Запустите средство **Sgen.exe** , предоставляемое вместе с пакетом SDK для .NET Framework, чтобы создать сборку, содержащую сериализаторы XML для исходной сборки.  
  
2.  Зарегистрируйте созданную сборку в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью инструкции `CREATE ASSEMBLY`.  
  
 Сведения об ошибках, которые могут быть получены при выполнении сериализации XML, см. в следующей служба поддержки Майкрософт статье ["не удается загрузить динамически созданную сборку сериализации"](https://support.microsoft.com/kb/913668).  
  
 Сведения о типах данных, не поддерживаемых классом XMLSerializer, см. в разделе о поддержке привязки к схеме XML на платформе .NET Framework в документации по платформе .NET Framework.  
  
## <a name="see-also"></a>См. также:  
 [Доступ к данным из объектов базы данных CLR](../../relational-databases/clr-integration/data-access/data-access-from-clr-database-objects.md)   
 [CREATE ASSEMBLY (Transact-SQL)](/sql/t-sql/statements/create-assembly-transact-sql)  
  
  
