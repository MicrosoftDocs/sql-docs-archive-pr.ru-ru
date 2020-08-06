---
title: Новые возможности установки SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- installing SQL Server, what's new
- SQL Server, what's new
- SQL Server, installing
ms.assetid: c8642a96-3a09-4ec7-a9c3-c539147e6330
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d34085e320cd8ca0b82d382d6d49eaa303086114
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659102"
---
# <a name="what39s-new-in-sql-server-installation"></a>Новые возможности установки SQL Server
  Windows Vista не является поддерживаемой операционной системой для [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]. Пакет обновления 1 (SP1) остается минимальным требованием для операционных систем [!INCLUDE[win7](../../includes/win7-md.md)] и [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)]. Дополнительные сведения о требованиях к операционной системе см. в разделе [требования к оборудованию и программному обеспечению для установки SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md).  
  
 При установке [!INCLUDE[ssExpCurrent](../../includes/ssexpcurrent-md.md)] будет предложено указать каталог для сохранения извлеченного пакета. Если местоположение не указано, то [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] будет использовать системный диск компьютера как значение по умолчанию. Извлеченные файлы после завершения установки [!INCLUDE[ssExpCurrent](../../includes/ssexpcurrent-md.md)] останутся на диске.  
  
 В [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] SysPrep поддерживается для всех установок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. SysPrep теперь поддерживает установки кластеров отработки отказа. Дополнительные сведения см. в разделе [рекомендации по установке SQL Server с помощью Sysprep](../../database-engine/install-windows/considerations-for-installing-sql-server-using-sysprep.md) и [установке SQL Server 2014 с помощью Sysprep](../../database-engine/install-windows/install-sql-server-using-sysprep.md).  
  
 Обновление от [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] поддерживается, но не поддерживается параллельная установка. Дополнительные сведения о поддержке [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] в [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]см. в разделе [Поддерживаемые обновления версий и выпусков](../../database-engine/install-windows/supported-version-and-edition-upgrades.md).  
  
 Начиная с версии [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], компонент Database Engine в выпусках Standard имеет объем памяти 128 ГБ. В [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] ядро СУБД в выпусках Standard имело объем памяти 64 ГБ.  
  
## <a name="see-also"></a>См. также:  
 [Новые возможности SQL Server 2014](../what-s-new-in-sql-server-2016.md)   
 [Спецификации продуктов для SQL Server 2014](../../../2014/getting-started/sql-server-2014-product-specifications.md)   
 [Планирование установки SQL Server](../../../2014/sql-server/install/planning-a-sql-server-installation.md)   
 [Требования к аппаратному и программному обеспечению для установки SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md)  
  
  
