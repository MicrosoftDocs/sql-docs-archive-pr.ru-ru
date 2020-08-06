---
title: Параметры сортировки и типы данных интеграции со средой CLR | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- data types [CLR integration]
- parameter collation [CLR integration]
- collations [CLR integration]
ms.assetid: 6ebaed8e-2e2b-4f6d-bf4b-bc25452de441
author: rothja
ms.author: jroth
ms.openlocfilehash: 1a5b0367487aeb80355b8c5c976818e1b6c1ac04
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87751184"
---
# <a name="collation-and-clr-integration-data-types"></a>Параметры сортировки и типы данных интеграции со средой CLR
  В [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] объект `CompareInfo` обрабатывает параметры сортировки. Строковые API-интерфейсы платформы [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] используют свойство `CompareInfo`, связанное с объектом `CultureInfo` текущего потока, для сравнения строк. Значение по умолчанию для `CultureInfo` объекта основано на [!INCLUDE[msCoName](../../includes/msconame-md.md)] параметрах локали Windows для компьютера, на котором [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] работает. Она определяет семантику сравнения по умолчанию для сравнения значений типа `CultureInfo`, если свойство `System.String` не задано явно. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не изменяет явно свойство `CompareInfo` на параметры сортировки базы данных или сервера. При необходимости пользователи должны самостоятельно устанавливать свойство `CompareInfo` в своих программах.  
  
## <a name="parameter-collation"></a>Параметр с параметрами сортировки  
 При создании программы CLR, если параметр метода CLR, связанного с программой, имеет тип `SQLString`, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] создает экземпляр параметра с параметрами сортировки по умолчанию базы данных, содержащей вызывающую программу. Если параметр имеет тип, отличный от `SqlType` (например, `String`, а не `SQLString`), сведения о параметрах сортировки из базы данных с этим параметром не связываются.  
  
## <a name="see-also"></a>См. также:  
 [Типы данных SQL Server в платформе .NET Framework](sql-server-data-types-in-the-net-framework.md)  
  
  
