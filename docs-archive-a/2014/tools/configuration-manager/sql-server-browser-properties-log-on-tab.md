---
title: Свойства браузера SQL Server (вкладка "Вход в систему") | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: c77871ec-c2f4-4e4a-9a10-5aeb4ae70507
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0c1f7d0cfd9e9b05a2a04f3c3e9efba687522298
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727698"
---
# <a name="sql-server-browser-properties-log-on-tab"></a>Свойства браузера SQL Server (вкладка «Вход в систему»)
  Программа браузера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] работает в качестве службы на сервере. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] прослушивает входящие запросы к ресурсам [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и предоставляет сведения об экземплярах [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], установленных на компьютере.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Браузер прослушивает UDP-порт и принимает запросы без проверки подлинности с использованием протокола разрешения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SSRP).  
  
 Изменение пароля учетной записи вступает в силу немедленно, без перезапуска службы.  
  
## <a name="options"></a>Параметры  
 **Локальная системная учетная запись**  
 Запустите службу « [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , браузер» в контексте безопасности локальной системной учетной записи. По возможности используйте учетную запись с небольшим набором прав.  
  
 **Эта учетная запись**  
 Укажите локальную или доменную учетную запись, использующую аутентификацию Windows. Для служб рекомендуется использовать доменную учетную запись с минимальными правами. Дополнительные сведения о выборе учетной записи см. в разделе «Настройка учетных записей служб Windows» электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Обзор**  
 Выберите пользователя или встроенного субъекта безопасности.  
  
> [!IMPORTANT]  
>  Используйте учетную запись с минимальными правами. Дополнительные сведения о разрешениях, необходимых для службы браузера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , см. в разделе "Безопасность" статьи [Служба обозревателя SQL Server](../../../2014/tools/configuration-manager/sql-server-browser-service.md).  
  
 **Пароль**  
 Введите пароль субъекта безопасности.  
  
 **Подтверждение пароля**  
 Подтвердите пароль субъекта безопасности.  
  
 **Состояние службы**  
 Указывает, была ли служба запущена, остановлена или отключена. **…** указывает, что ожидается изменение состояния.  
  
 **Начало**  
 Запустить службу браузера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Остановить**  
 Остановить службу браузера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Приостановить**  
 Приостановить службу браузера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Возобновить**  
 Возобновить работу приостановленной службы браузера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="see-also"></a>См. также:  
 [Служба обозревателя SQL Server](../../../2014/tools/configuration-manager/sql-server-browser-service.md)  
  
  
