---
title: Установка распределенное воспроизведение из командной строки | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: ea1171da-f50e-4f16-bedc-5e468a46477f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: be7c950b886356c08050e37825d5215b62aeb8cd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659034"
---
# <a name="install-distributed-replay-from-the-command-prompt"></a>Установка распределенного воспроизведения из командной строки
  При установке нового экземпляра программы распределенного воспроизведения из командной строки можно указать устанавливаемые компоненты и способ их настройки. Установка из командной строки поддерживает установку, восстановление, обновление и удаление компонентов распределенного воспроизведения. При установке из командной строки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает полностью тихий режим (включается параметром /Q).  
  
> [!NOTE]  
>  Для локальных установок необходимо запускать программу установки с правами администратора. При установке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] из удаленной общей папки необходимо использовать учетную запись домена с разрешениями на чтение и выполнение для удаленной общей папки.  
  
## <a name="installation-parameters"></a>Параметры установки  
 В список компонентов верхнего уровня входят [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]и средства. Компонент «Инструменты» устанавливает средства управления [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , электронную документацию по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , среду [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]и другие общие компоненты. Чтобы установить компоненты программы распределенного воспроизведения, укажите следующие параметры:  
  
|Компонент|Параметр|  
|---------------|---------------|  
|Контроллер распределенного воспроизведения|**DREPLAY_CTLR**|  
|Клиент распределенного воспроизведения|**DREPLAY_CLT**|  
|Средство администрирования|**Инструменты**|  
  
> [!IMPORTANT]  
>  После установки компонентов распределенного воспроизведения необходимо создать правила брандмауэра на компьютерах контроллера и клиента и предоставить каждому из клиентских компьютеров разрешения на целевом сервере. Дополнительные сведения см. в статье [Выполнение действий после установки](complete-the-post-installation-steps.md).  
  
 При разработке скриптов установки из командной строки можно использовать параметры, приведенные в следующей таблице.  
  
|Параметр|Описание|Поддерживаемые значения|  
|---------------|-----------------|----------------------|  
|/CTLRSVCACCOUNT<br /><br /> **Необязательно**|Учетная запись службы контроллера распределенного воспроизведения.|Проверяет учетную запись и пароль|  
|/CTLRSVCPASSWORD<br /><br /> **Необязательно**|Пароль учетной записи службы контроллера распределенного воспроизведения.|Проверяет учетную запись и пароль|  
|/CTLRSTARTUPTYPE<br /><br /> **Необязательно**|Тип запуска службы контроллера распределенного воспроизведения.|Автоматически<br /><br /> Выключено<br /><br /> Вручную|  
|/CTLRUSERS<br /><br /> **Необязательно**|Укажите, какие пользователи имеют разрешения на службу контроллера распределенного воспроизведения.|Строка, содержащая коллекцию учетных записей пользователей, использует в качестве разделителя " " (пробел)<br /><br /> **Важно!** При настройке службы контроллера распределенного воспроизведения можно указать одну или несколько учетных записей, которые будут использоваться для запуска служб клиента распределенного воспроизведения. Далее представлен список поддерживаемых учетных записей.<br /><br /> Учетная запись пользователя домена<br /><br /> Пользователь, который создал учетную запись локального пользователя<br /><br /> Администратор<br /><br /> Виртуальная учетная запись и управляемая учетная запись службы (MSA)<br /><br /> Сетевые службы, локальные службы и система<br /><br /> <br /><br /> Учетные записи групп (локальные или доменные) и другие встроенные учетные записи (например, «Все») не принимаются.|  
|/CLTSVCACCOUNT<br /><br /> **Необязательно**|Учетная запись службы клиента распределенного воспроизведения.|Проверяет учетную запись и пароль|  
|/CLTSVCPASSWORD<br /><br /> **Необязательно**|Пароль учетной записи службы клиента распределенного воспроизведения.|Проверяет учетную запись и пароль|  
|/CLTSTARTUPTYPE<br /><br /> **Необязательно**|Тип запуска службы клиента распределенного воспроизведения.|Автоматически<br /><br /> Выключено<br /><br /> Вручную|  
|/CLTCTLRNAME<br /><br /> **Необязательно**|Введите имя компьютера, с которым взаимодействует клиент с помощью службы контроллера распределенного воспроизведения.||  
|/CLTWORKINGDIR<br /><br /> **Необязательно**|Рабочий каталог для службы клиента распределенного воспроизведения.|Верный путь|  
|/CLTRESULTDIR<br /><br /> **Необязательно**|Каталог результатов для службы клиента распределенного воспроизведения.|Верный путь|  
  
### <a name="sample-syntax"></a>Образец синтаксиса  
 **Установка контроллера распределенного воспроизведения**  
  
```  
setup /q /ACTION=Install /FEATURES=DREPLAY_CTLR /IAcceptSQLServerLicenseTerms /CTLRUSERS="domain\user1" "domain\user2" /CTLRSVCACCOUNT="domain\svcuser" /CTLRSVCPASSWORD="password" /CTLRSTARTUPTYPE=Automatic  
```  
  
 **Установка клиента распределенного воспроизведения**  
  
```  
setup /q /ACTION=Install /FEATURES=DREPLAY_CLT /IAcceptSQLServerLicenseTerms /CLTSVCACCOUNT="domain\svcuser" /CLTSVCPASSWORD="password" /CLTSTARTUPTYPE=Automatic /CLTCTLRNAME=ControllerMachineName /CLTWORKINGDIR="C:\WorkingDir" /CLTRESULTDIR="C:\ResultDir  
```  
  
  
