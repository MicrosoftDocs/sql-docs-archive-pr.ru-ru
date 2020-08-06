---
title: Развертывание решений PowerPivot в SharePoint | Документация Майкрософт
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: f202a2b7-34e0-43aa-90d5-c9a085a37c32
author: minewiskan
ms.author: owend
ms.openlocfilehash: 043647988598f932b70cc06e6bb5492d66864372
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87666231"
---
# <a name="deploy-powerpivot-solutions-to-sharepoint"></a>Развертывание решений PowerPivot в SharePoint
  Используйте следующие инструкции для выполнения вручную развертывания двух пакетов решений, добавляющих функции PowerPivot в среде SharePoint Server 2010. Развертывание решений — это обязательный шаг настройки PowerPivot для SharePoint на сервере SharePoint 2010. Полный список необходимых шагов см. [в разделе Администрирование и настройка сервера PowerPivot в центре администрирования](power-pivot-server-administration-and-configuration-in-central-administration.md).  
  
 Кроме того, для развертывания решений можно использовать средство настройки PowerPivot. При установке одиночного сервера проще и удобнее использовать средство настройки, однако если вы предпочитаете знакомое средство или если требуется настроить несколько компонентов одновременно, то лучше пользоваться центром администрирования и PowerShell. Дополнительные сведения об использовании средства настройки см. в разделе [PowerPivot средства настройки](power-pivot-configuration-tools.md).  
  
 Перед развертыванием решения необходимо установить PowerPivot для SharePoint с установочного носителя SQL Server 2012. Программа установки SQL Server устанавливает пакеты решения, которое вы собираетесь развертывать.  
  
 Этот раздел состоит из следующих подразделов.  
  
 [Необходимое условие: Убедитесь, что веб-приложение использует классический режим проверки подлинности.](#bkmk_classic)  
  
 [Шаг 1. Развертывание решения фермы](#bkmk_farm)  
  
 [Шаг 2. Развертывание решения веб-приложения PowerPivot в центре администрирования](#deployCA)  
  
 [Шаг 3. Развертывание решения веб-приложения PowerPivot для других веб-приложений](#deployUI)  
  
 [Повторное развертывание или отзыв решения](#retract)  
  
 [О решениях PowerPivot](#intro)  
  
##  <a name="prerequisite-verify-the-web-application-uses-classic-mode-authentication"></a><a name="bkmk_classic"></a> Обязательное условие: убедитесь, что в веб-приложении используется классический режим проверки подлинности.  
 PowerPivot для SharePoint поддерживается только в тех веб-приложениях, которые используют классическую проверку подлинности Windows. Чтобы проверить, использует ли приложение классический режим, выполните следующий командлет PowerShell из **командной консоли sharepoint 2010**, заменив `http://<top-level site name>` именем своего сайта SharePoint:  
  
```powershell
Get-SPWebApplication http://<top-level site name> | Format-List UseClaimsAuthentication  
```  
  
 Должно быть возвращено значение **false**. Если **это так, вы**не сможете получить доступ к данным PowerPivot с помощью этого веб-приложения.  
  
##  <a name="step-1-deploy-the-farm-solution"></a><a name="bkmk_farm"></a>Шаг 1. Развертывание решения фермы  
 В этом разделе показано, как развертывать решения с помощью PowerShell, но для этой задачи можно использовать и средство PowerPivot Configuration Tool. Дополнительные сведения см. в разделе [Настройка или восстановление PowerPivot для SharePoint 2010 &#40;средства настройки PowerPivot&#41;](../configure-repair-powerpivot-sharepoint-2010.md).  
  
 Эта задача выполняется один раз после установки PowerPivot для SharePoint.  
  
1.  На сервере с установленным PowerPivot для SharePoint откройте консоль управления SharePoint 2010 с помощью команды **Запуск от имени администратора** .  
  
2.  Для добавления решения фермы выполните следующий командлет.  
  
    ```powershell
    Add-SPSolution -LiteralPath "C:\Program Files\Microsoft SQL Server\110\Tools\PowerPivotTools\ConfigurationTool\Resources\PowerPivotFarm.wsp"  
    ```  
  
     Командлет возвратит имя решения, его идентификатор, а также атрибут Deployed=False. На следующем шаге будет выполнено развертывание решения.  
  
3.  Выполните следующий командлет, чтобы развернуть решение фермы.  
  
    ```powershell
    Install-SPSolution -Identity PowerPivotFarm.wsp -GACDeployment -Force  
    ```  
  
##  <a name="step-2-deploy-the-powerpivot-web-application-solution-to-central-administration"></a><a name="deployCA"></a>Шаг 2. Развертывание решения веб-приложения PowerPivot в центре администрирования  
 После развертывания решения фермы следует развернуть решение веб-приложения для центра администрирования. Этот шаг добавляет в центр администрирования панель управления PowerPivot.  
  
1.  Откройте консоль управления SharePoint 2010, выбрав команду **Запуск от имени администратора** .  
  
2.  Выполните следующий командлет, чтобы создать ссылку на центр администрирования.  
  
    ```powershell
    $centralAdmin = $(Get-SPWebApplication -IncludeCentralAdministration | Where { $_.IsAdministrationWebApplication -eq $TRUE})  
    ```  
  
3.  Для добавления решения фермы выполните следующий командлет.  
  
    ```powershell
    Add-SPSolution -LiteralPath "C:\Program Files\Microsoft SQL Server\110\Tools\PowerPivotTools\ConfigurationTool\Resources\PowerPivotWebApp.wsp"  
    ```  
  
     Командлет возвратит имя решения, его идентификатор, а также атрибут Deployed=False. На следующем шаге будет выполнено развертывание решения.  
  
4.  Выполните следующий командлет для установки решения веб-приложения в центре администрирования.  
  
    ```powershell
    Install-SPSolution -Identity PowerPivotWebApp.wsp -GACDeployment -Force -WebApplication $centralAdmin  
    ```  
  
 Теперь, когда решение веб-приложения развернуто в центре администрирования, оставшиеся шаги конфигурации можно выполнить с помощью центра администрирования.  
  
##  <a name="step-3-deploy-the-powerpivot-web-application-solution-to-other-web-applications"></a><a name="deployUI"></a>Шаг 3. Развертывание решения веб-приложения PowerPivot для других веб-приложений  
 В предыдущей задаче решение powerpivotwebapp.wsp было развернуто в центре администрирования. В этом разделе описано развертывание решения powerpivotwebapp.wsp для каждого веб-приложения, поддерживающего доступ к данным PowerPivot. При добавлении других веб-приложений в дальнейшем необходимо будет повторить для них этот шаг.  
  
1.  В разделе «Системные параметры» центра администрирования выберите **Управление решениями фермы**.  
  
2.  Щелкните **powerpivotwebapp. wsp**.  
  
3.  Нажмите **Развернуть решение**.  
  
4.  В разделе **Deploy to? (развертывание в**) выберите веб-приложение SharePoint, для которого требуется добавить поддержку функций PowerPivot.  
  
5.  Нажмите кнопку **ОК**.  
  
6.  Повторите процедуру для других веб-приложений SharePoint, которые тоже будут поддерживать доступ к данным PowerPivot.  
  
##  <a name="redeploy-or-retract-the-solution"></a><a name="retract"></a>Повторное развертывание или отзыв решения  
 Хотя центр администрирования SharePoint позволяет отзывать решения, для файла powerpivotwebapp.wsp это следует делать только тогда, когда систематически проводится диагностика проблем установки или развертывания обновлений.  
  
1.  В разделе «Системные параметры» центра администрирования SharePoint 2010 выберите **Управление решениями фермы**.  
  
2.  Щелкните **Powerpivotwebapp.wsp**.  
  
3.  Нажмите **Отозвать решение**.  
  
 При возникновении проблем с развертыванием сервера, которые можно перевернуть в решение фермы, можно повторно развернуть его, запустив параметр **восстановления** в средстве настройки PowerPivot. Предпочтительнее выполнять операции восстановления с помощью PowerPivot Configuration Tool, так как они включают меньше шагов. Дополнительные сведения см. в разделе [Настройка или восстановление PowerPivot для SharePoint 2010 &#40;средства настройки PowerPivot&#41;](../configure-repair-powerpivot-sharepoint-2010.md).  
  
 Если же необходимо повторное развертывание всех решений, обязательно выполните его в следующем порядке:  
  
1.  Отзыв решения для веб-приложений PowerPivot из всех веб-приложений SharePoint, которые его используют.  
  
2.  Отзыв решения для фермы PowerPivot.  
  
3.  Повторное развертывание решения для фермы PowerPivot.  
  
4.  Повторное развертывание решения для веб-приложений PowerPivot для всех веб-приложений SharePoint.  
  
##  <a name="about-the-powerpivot-solutions"></a><a name="intro"></a>О решениях PowerPivot  
 PowerPivot для SharePoint использует два пакета решений для развертывания страниц своего приложения и программных файлов в ферме и в отдельных веб-приложениях.  
  
-   Решение фермы является глобальным. Оно развертывается один раз и автоматически становится доступным для любого нового сервера PowerPivot для SharePoint, который будет добавлен в ферму в будущем.  
  
-   Решение веб-приложения для каждого приложения свое и должно развертываться для каждого приложения на ферме, включая веб-приложение центра администрирования (Central Administration).  
  
 Каждое решение развертывается индивидуально.  Решение фермы развертывается один раз после установки первого экземпляра PowerPivot для SharePoint. Для развертывания решения фермы используется средство PowerPivot Configuration Tool или командлеты PowerShell.  
  
 Решение веб-приложения сначала развертывается для центра администрирования, а затем для любых дополнительных веб-приложений, поддерживающих запросы к данным PowerPivot. Чтобы развернуть решение веб-приложения для центра администрирования, необходимо использовать средство настройки PowerPivot или командлет PowerShell. Решение веб-приложения для других веб-приложений можно развернуть вручную с помощью центра администрирования или PowerShell.  
  
|Решение|Описание|  
|--------------|-----------------|  
|Powerpivotfarm.wsp|Добавляет файл Microsoft.AnalysisServices.SharePoint.Integration.dll к глобальной сборке.<br /><br /> Добавляет файл Microsoft.AnalysisServices.ChannelTransport.dll к глобальной сборке.<br /><br /> Устанавливает функции и файлы ресурсов, а также регистрирует типы содержимого.<br /><br /> Добавляет шаблоны библиотек PowerPivot Gallery и Data Feed.<br /><br /> Добавляет страницы приложений для настройки приложений службы, панели управления PowerPivot, обновления данных и галереи PowerPivot.|  
|powerpivotwebapp.wsp|Добавляет файлы ресурсов Microsoft.AnalysisServices.SharePoint.Integration.dll в папку расширений веб-сервера на сервере клиентского веб-интерфейса.<br /><br /> Добавляет веб-службу PowerPivot к серверу клиентского веб-интерфейса.<br /><br /> Добавляет возможность формирования эскизов для галереи PowerPivot.|  
  
## <a name="see-also"></a>См. также:  
 [PowerPivot для SharePoint обновления](../../database-engine/install-windows/upgrade-power-pivot-for-sharepoint.md)   
 [Администрирование и настройка сервера PowerPivot в центре администрирования](power-pivot-server-administration-and-configuration-in-central-administration.md)   
 [Настройка PowerPivot с помощью Windows PowerShell](power-pivot-configuration-using-windows-powershell.md)  
