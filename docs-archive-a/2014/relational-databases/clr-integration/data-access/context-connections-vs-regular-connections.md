---
title: Обычные и контекстные соединения | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- context connections [CLR integration]
- regular connections [CLR integration]
ms.assetid: a1dead02-be88-4b16-8cb2-db1284856764
author: rothja
ms.author: jroth
ms.openlocfilehash: ce531129099a8f4908bdc4b29920696d4ba3c505
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87668922"
---
# <a name="regular-vs-context-connections"></a>Обычные и Контекстные соединения
  При соединении с удаленным сервером всегда пользуйтесь обычными, а не контекстными соединениями. Если нужно подключиться к тому же серверу, на котором выполняется хранимая процедура или функция, в большинстве случаев используется контекстное соединение. Преимущества заключаются в выполнении приложений в одной области транзакций и отсутствии необходимости повторной проверки подлинности имени входа.  
  
 Кроме того, использование контекстного соединения обычно приводит к повышению производительности при меньшем потреблении ресурсов. Контекстное соединение является подключением только для обработки, поэтому оно может напрямую связаться с сервером, обходя сетевой протокол и транспортные уровни, чтобы отправлять инструкции Transact-SQL и получать результаты. Также обходится процесс проверки подлинности. На следующем рисунке показаны основные компоненты управляемого поставщика `SqlClient`, а также взаимодействие разных компонентов друг с другом при использовании обычного и контекстного соединения.  
  
 ![Кодовые пути контекстного и обычного соединений.](../../../database-engine/dev-guide/media/clrintdataaccess.gif "Кодовые пути контекстного и обычного соединений.")  
  
 Контекстное соединение требует более короткого кода и меньшего числа компонентов, поэтому запрос к серверу, как и получение результатов, происходит быстрее, чем при обычном соединении. Время выполнение запроса на сервере остается одинаковым для контекстных и обычных соединений.  
  
 В некоторых случаях, возможно, потребуется открыть отдельное обычное соединение с тем же сервером. Например, существуют определенные ограничения на использование контекстного соединения, описанные в разделе [ограничения для обычных и контекстных соединений](context-connections-and-regular-connections-restrictions.md).  
  
## <a name="see-also"></a>См. также:  
 [Контекстное соединение](context-connection.md)  
  
  
