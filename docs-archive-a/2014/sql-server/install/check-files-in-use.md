---
title: Проверка используемых файлов | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: ccd65867-d4c0-43b2-8361-7fd41c6f79ac
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 51505b0dece146b7f6fcdf982e6f88a5715357e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659226"
---
# <a name="check-files-in-use"></a>Проверка используемых файлов
  Чтобы избежать необходимости перезагрузки Windows после установки обновлений для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , на странице «Проверка используемых файлов» можно найти процессы, которые блокируют файлы, необходимые программе установки обновлений [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Остановите все приложения и службы, которые соединяются с обновляемыми экземплярами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Это также касается среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] и среды [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
 Если программа установки обнаруживает заблокированные файлы во время установки, может возникнуть необходимость в перезагрузке компьютера после завершения установки. При необходимости программа установки запрашивает пользователя о перезагрузке компьютера. Если программе установки необходимо остановить работу службы во время установки, эта служба будет перезапущена после завершения установки.  
  
 Чтобы устранить необходимость в перезагрузке компьютера после установки, программа установки отобразит список процессов, блокирующих файлы. Остановите процессы или приложения, указанные в списке. После этого нажмите кнопку **Обновить проверку** , чтобы выполнить проверку повторно. Нажмите кнопку **Остановить проверку** , чтобы прервать выполнение проверки. Если заблокированные файлы не обнаружены, таблица будет пустой. После того как все заблокированные процессы были закрыты или остановлены, нажмите кнопку **Далее** , чтобы продолжить.  
  
 Программа установки записывает сведения в файлы журналов. Дополнительные сведения о просмотре файлов журналов см. в статьях [Просмотр и чтение файлов журнала настройки SQL Server](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md) и [Инструкция по чтению файла журнала настройки SQL Server](https://go.microsoft.com/fwlink/?LinkID=134490).  
  
 В файл журнала включается следующая информация.  
  
-   Имя процесса  
  
-   Имя компонента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
-   Тип процесса  
  
-   Учетная запись, под которой выполняется процесс  
  
-   ИД процесса  
  
-   Имя заблокированного файла  
  
## <a name="ui-element-list"></a>Список элементов пользовательского интерфейса  
  
|Имя|Описание|  
|----------|-----------------|  
|Процесс|Отображает полное имя процесса, использующего файлы, которые будут обновлены.|  
|Type|Отображает тип процесса.|  
|Учетная запись|Отображает учетную запись, под которой выполняется процесс.|  
|ИД процесса|Отображает идентификатор процесса.|  
  
  
