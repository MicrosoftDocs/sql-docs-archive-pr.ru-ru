---
title: План обслуживания, страница "Отчеты и ведение журнала" | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.reportinglogging.f1
ms.assetid: 3a30b17a-3deb-446f-900a-62f88934a90f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 7c7a95a7092ce2cdac4aa0540a5cb57d86b48497
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87658241"
---
# <a name="maintenance-plan-reporting-and-logging-page"></a>План обслуживания (страница «Отчеты и ведение журнала»)
  Диалоговое окно **Отчеты и ведение журнала** используется для настройки отчетов и журналов, созданных при выполнении планов обслуживания.  
  
## <a name="options"></a>Параметры  
 **Сформировать текстовый файл отчета**  
 Задайте это значение, если требуется, чтобы [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] записал отчет в текстовом файле.  
  
 **Создать новый файл**  
 Создайте новый файл отчета для каждого выполнения плана обслуживания. По умолчанию файлы отчетов записываются на тот компьютер, где установлен экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , содержащий план обслуживания, в папку, указанную во время настройки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в качестве папки журналов по умолчанию. Чтобы указать другую папку, введите полный путь папки в поле **Папка** или нажмите кнопку "Обзор" ( **...** ) и перейдите в нужную папку.  
  
 **Добавить к файлу**  
 Добавлять отчет после каждого выполнения плана к файлу, заданному в текстовом поле **Имя файла** . Также можно задать файл, нажав кнопку обзора и выбрав файл из диалогового окна.  
  
 **Отправить отчет адресату по электронной почте**  
 Передайте результат выполнения плана обслуживания по электронной почте. Данный параметр доступен только, если включен и надлежащим образом настроен компонент Database Mail.  
  
 **Оператор агента**  
 Выберите из списка агента оператора, который будет являться получателем электронной почты. Данный параметр доступен, только если включена и надлежащим образом настроена почта.  
  
 **Записывать подробные данные в журнал**  
 Включите дополнительные данные в журнал. Включение данного параметра приведет к увеличению размера хранимого журнала планов обслуживания.  
  
 **Войти на удаленный сервер**  
 Записывает журнал плана обслуживания на удаленном сервере.  
  
 **Соединение**  
 Задает сведения о соединении, которые записываются в журнал плана обслуживания на удаленном сервере.  
  
 **Создать**  
 Вызывает диалоговое окно **Свойства соединения** . Используется для указания новых сведений о соединении, которые записываются в журнал плана обслуживания на удаленном сервере.  
  
## <a name="see-also"></a>См. также:  
 [Планы обслуживания](maintenance-plans.md)   
 [Database Mail](../database-mail/database-mail.md)  
  
  
