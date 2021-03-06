---
title: MSSQLSERVER_833 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 833 (Database Engine error)
ms.assetid: 14129cc4-be80-4772-9e3f-0e5da4d0696b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8e20018c0fe1cd0748f4930e0022622adcbfad10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87664205"
---
# <a name="mssqlserver_833"></a>MSSQLSERVER_833
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|833|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|BUF_LONG_IO|  
|Текст сообщения|В SQL Server обнаружено% d запросов ввода-вывода, для выполнения которых в файле [% ls] в базе данных требуется больше% d секунд `[%ls] (%d)` .  Дескриптором файла ОС является 0x%p.  Смещение последней длительной операции ввода-вывода: %#016I64x.|  
  
## <a name="explanation"></a>Объяснение  
 Это сообщение указывает, что [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издал запрос чтения или записи на диск, и выполнение запроса заняло более 15 секунд. Данная ошибка возвращается [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и говорит о проблеме с подсистемой ввода-вывода.  
  
### <a name="possible-causes"></a>Возможные причины  
 Причиной этой ошибки могут быть проблемы с производительностью системы, ошибки оборудования, ошибки встроенного ПО, проблемы с драйверами устройств или вмешательство фильтров в процессы ввода-вывода.  
  
## <a name="user-action"></a>Действие пользователя  
 Для устранения этой ошибки найдите в журнале системных событий сообщения об ошибках, связанных с оборудованием. Также изучите журналы оборудования, если они доступны.  
  
 При помощи системного монитора проверьте следующие счетчики.  
  
-   **Среднее время обращения к диску (сек)**  
  
-   **Средняя длина очереди диска**  
  
-   **Текущая длина очереди диска**  
  
 Например, на компьютере, где выполняется [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], значение **среднего времени обращения к диску** обычно не превышает 15 миллисекунд. Если значение **среднего времени обращения к диску** увеличивается, значит подсистема ввода-вывода не справляется с числом запросов на операции ввода-вывода.  
  
> [!NOTE]  
>  Доступ к диску может замедляться антивирусной программой. Чтобы увеличить скорость доступа, исключите из активных заданий сканирования на вирусы файлы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], указанные в сообщении об ошибке.  
  
 Дополнительные сведения об ошибках ввода-вывода см. в [главе 2 документации Microsoft SQL Server по основным операциям ввода-вывода](/previous-versions/sql/sql-server-2005/administrator/cc917726(v=technet.10)) и в статье базы знаний по адресу [https://support.microsoft.com/kb/897284](https://support.microsoft.com/kb/897284).  
  
  
