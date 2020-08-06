---
title: Свойства сети | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- LingerTimeout property
- EnableNagleAlgorithm property
- MinPendingAcceptExCount property
- MaxPendingSendCount property
- EnableBinaryXML property
- MinPendingReceiveCount property
- MaxCompletedReceiveCount property
- DisableNonblockingMode property
- RequestSizeThreshold property
- CompressionLevel property
- ReceiveBufferSize property
- EnableCompression property
- ServerSendTimeout property
- IPV4Support property
- MaxPendingReceiveCount property
- MaxPendingAcceptExCount property
- IPV6Support property
- MaxAllowedRequestSize property
- ServerReceiveTimeout property
- EnableLingerOnClose property
- InitialConnectTimeout property
- SendBufferSize property
- ScatterReceiveMultiplier property
- network properties [Analysis Services]
ms.assetid: ef4251e2-abe5-4c5b-9868-7549782d0244
author: minewiskan
ms.author: owend
ms.openlocfilehash: 10ad5bbbcffdfc3d3c4fefe3111e4c4425919915
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659022"
---
# <a name="network-properties"></a>Свойства сети
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] поддерживают свойства сервера, перечисленные в следующих таблицах. Дополнительные сведения о дополнительных свойствах сервера и об их настройке см. в разделе [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md).  
  
 **Область применения:** многомерный и табличный режим сервера  
  
## <a name="general"></a>Общие сведения  
 `ListenOnlyOnLocalConnections`  
 Логическое свойство, указывающее прослушивание только локальных соединений, например локального сервера.  
  
## <a name="listener"></a>Прослушиватель  
 `IPV4Support`  
 Свойство с 32-разрядным целочисленным значением со знаком, определяющее поддержку протокола IPv4. Это свойство имеет одно из значений, содержащихся в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*0*|Протокол IPv4 отключен; подключение клиентов невозможно.|  
|*1*|(По умолчанию) необходим протокол IPv4; сервер невозможно запустить без прослушивания по IPv4.|  
|*2*|Дополнительный протокол IPv4; сервер пытается прослушать по протоколу IPv4, но запускается в любом случае.|  
  
 `IPV6Support`  
 Свойство с 32-разрядным целочисленным значением со знаком, определяющее поддержку протокола IPv6. Это свойство имеет одно из значений, содержащихся в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|*0*|Протокол IPv6 отключен; подключение клиентов невозможно.|  
|*1*|(По умолчанию) необходим протокол IPv6; сервер невозможно запустить без прослушивания по IPv6.|  
|*2*|Дополнительный протокол IPv6; сервер пытается прослушать по протоколу IPv6, но запускается в любом случае.|  
  
 `MaxAllowedRequestSize`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `RequestSizeThreshold`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `ServerReceiveTimeout`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `ServerSendTimeout`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
## <a name="requests"></a>Requests  
 `EnableBinaryXML`  
 Логическое свойство, определяющее, распознает ли сервер запросы в двоичном XML-формате.  
  
 `EnableCompression`  
 Логическое свойство, определяющее сжатие запросов.  
  
## <a name="responses"></a>Ответы  
 `CompressionLevel`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `EnableBinaryXML`  
 Логическое свойство, определяющее включение на сервере двоичных XML-ответов.  
  
 `EnableCompression`  
 Логическое свойство, определяющее сжатие ответов клиентам.  
  
## <a name="tcp"></a>TCP  
 `InitialConnectTimeout`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `MaxCompletedReceiveCount`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `MaxPendingAcceptExCount`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `MaxPendingReceiveCount`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `MaxPendingSendCount`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `MinPendingAcceptExCount`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `MinPendingReceiveCount`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `ScatterReceiveMultiplier`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `SocketOptions\ DisableNonblockingMode`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `SocketOptions\ EnableLingerOnClose`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `SocketOptions\EnableNagleAlgorithm`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `SocketOptions\ LingerTimeout`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `SocketOptions\ ReceiveBufferSize`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `SocketOptions\ SendBufferSize`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
## <a name="see-also"></a>См. также:  
 [Настройка свойств сервера в Analysis Services](server-properties-in-analysis-services.md)   
 [Определение режима работы сервера экземпляра служб Analysis Services](../instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
