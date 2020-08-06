---
title: Требования к оборудованию и программному обеспечению для Analysis Services Server в режиме интеграции с SharePoint (SQL Server 2014) | Документация Майкрософт
ms.prod: sql-server-2014
ms.technology: database-engine
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.topic: conceptual
ms.custom: ''
ms.date: 06/13/2017
ms.openlocfilehash: ac169a334c2f375afb08ba9fdba4306ba11fd29e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87668065"
---
# <a name="hardware-and-software-requirements-for-analysis-services-server-in-sharepoint-mode-sql-server-2014"></a>Требования к оборудованию и программному обеспечению для сервера служб Analysis Services в режиме интеграции с SharePoint (SQL Server 2014)

[!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]поддерживает SharePoint 2010 и SharePoint 2013. [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]2013 выполняется за пределами фермы SharePoint, хотя ее можно установить на серверах SharePoint. [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]2010 работает на серверах приложений в ферме SharePoint 2010 и использует функции и инфраструктуру SharePoint для поддержки операций сервера. Чтобы установить [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] для любой версии SharePoint, воспользуйтесь мастером установки [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. После установки выполните следующие действия.  
  
- Запустите версию средства настройки [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)], соответствующую версии SharePoint.  
  
- Для SharePoint 2013 установите [или удалите надстройку PowerPivot для SharePoint &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013).  

##  <a name="sql-server-edition-requirements"></a><a name="bkmk_sqleditions"></a>Требования к выпуску SQL Server  
 Не все функции бизнес-аналитики доступны во всех выпусках [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Дополнительные сведения см. [в разделе функции, поддерживаемые различными Выпусками SQL Server 2014](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md) и [выпусками и компонентами SQL Server 2014](../editions-and-components-of-sql-server-2016.md).  
  
 Текущие заметки о выпуске можно найти в [примечаниях к Выпуску Microsoft SQL Server 2014](https://go.microsoft.com/fwlink/?LinkID=296445).  
  

  
##  <a name="sql-server-licensing"></a><a name="bkmk_sqllicense"></a>Лицензирование SQL Server  
 Дополнительные сведения о лицензировании SQL Server см. в следующих источниках:  
  
-   [Таблица лицензирования SQL Server 2014](https://download.microsoft.com/download/6/6/F/66FF3259-1466-4BBA-A505-2E3DA5B2B1FA/SQL_Server_2014_Licensing_Datasheet.pdf) ( https://download.microsoft.com/download/6/6/F/66FF3259-1466-4BBA-A505-2E3DA5B2B1FA/SQL_Server_2014_Licensing_Datasheet.pdf) .  
  
-   [Как купить: SQL Server поддержка моделей лицензирования](https://www.microsoft.com/licensing/product-licensing/sql-server-2014?activetab=sql-server-2014-pivot%3aprimaryr2) ( https://www.microsoft.com/licensing/product-licensing/sql-server-2014?activetab=sql-server-2014-pivot%3aprimaryr2) .  
  
##  <a name="analysis-services-installed-on-sharepoint-2013"></a><a name="bkmk_ssas__sharepoint_2013"></a>Analysis Services, установленные на сервере SharePoint 2013  
 Если сервер служб Analysis Services в режиме интеграции SharePoint устанавливается на сервере отдельно, то минимальные требования к системе основываются на требованиях к [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], а не SharePoint Server.  
  
 [Требования к аппаратному и программному обеспечению для установки SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md)  
  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint рекомендуется запускать на бизнес-серверах нового поколения, которые имеют более высокие пороговые значения ОЗУ и обладают большими вычислительными мощностями. Для хранения данных [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] в памяти используются большие объемы ОЗУ. ОЗУ поддерживает возможность адаптироваться к структурным изменениям. Дополнительные процессоры поддерживают выполнение длительных сканирований необработанных и необъединенных данных. Предполагается, что данные формируют свою структуру в динамической среде в ответ на определяемый пользователем анализ данных, который инициируется с помощью клиента или интерфейса Excel для клиентских запросов.  
  
> [!TIP]  
>  [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint использует кэши L2 и L3. Для повышения производительности рекомендуется использовать процессоры с большими кэшами L2 и L3.  
  
 В следующей таблице приведены минимальная и рекомендуемая конфигурации оборудования для изолированного сервера [!INCLUDE[ssGeminiShortvnext](../../includes/ssgeminishortvnext-md.md)], не входящего в состав фермы SharePoint.  
  
|Компонент|Минимальные|Рекомендуется|  
|---------------|-------------|-----------------|  
|Процессор|64-разрядный двухъядерный процессор с тактовой частотой 3 ГГц.|16 ядер|  
|ОЗУ|8 гигабайт ОЗУ|64 гигабайта ОЗУ|  
|Память|80 ГБ|80 гигабайт или больше|  
  
 Если сервер служб Analysis Services в режиме интеграции с SharePoint установлен на сервере фермы SharePoint, то сведения о минимальных требованиях к системе для [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и сервера SharePoint см. по следующим ссылкам:  
  
-   [Требования к аппаратному и программному обеспечению для установки SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md)  
  
-   [Требования к оборудованию и программному обеспечению для SharePoint 2013](https://technet.microsoft.com/library/cc262485\(office.15\).aspx).  
  
 Стандартные рекомендации по оборудованию и программному обеспечению для SharePoint 2013 применимы к решению по управлению документами для рабочей группы или команды, основанному на веб-технологиях. Обработка [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] требует много ресурсов, поэтому рекомендуемых аппаратных средств достаточно, если рабочая нагрузка невелика, например менее 100 пользователей или книг. При более крупномасштабном развертывании [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] требуются большие вычислительные мощности.  
  
##  <a name="analysis-services-installed-on-a-sharepoint-2010-server"></a><a name="bkmk_ssas__sharepoint_2010"></a>Analysis Services, установленные на сервере SharePoint 2010  
 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]2010 работает на серверах приложений в ферме SharePoint 2010 и использует функции и инфраструктуру SharePoint для поддержки операций сервера. В следующей таблице перечислены системные требования, относящиеся к развертываниям SharePoint 2010.  
  
|Компонент|Требование|  
|---------------|-----------------|  
|Версия SharePoint|Выпуск SharePoint 2010 Enterprise со службами Excel, службой Secure Store и службой Claims to Windows Token, настроенный на той же ферме серверов приложений, что и PowerPivot для SharePoint.<br /><br /> Сервер SharePoint должен быть установлен с параметром «Ферма серверов» в программе установки SharePoint (параметр отдельной установки SharePoint не поддерживается). Для [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] требуется инфраструктура фермы серверов для поддержки административного доступа и доступа к данным. Автономная установка не предоставляет эти службы.<br /><br /> Выпуск Developer Edition, который выполняется в ОС Windows 7 или Windows Vista, не поддерживается для установки сервера [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)].|  
|Пакеты обновления|Требуется пакет обновления 1 (SP1) для SharePoint Server 2010.<br /><br /> Для работы компонентов [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)][!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] необходимо установить пакет обновления 1 (SP1) для SharePoint 2010.<br /><br /> Накопительное обновление SharePoint 2010 за август 2010 года или более позднее является обязательным для обновления с предыдущей версии [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] до [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]. Накопительное обновление за август 2010 года или более позднее должно быть установлено после установки пакета обновления 1 (SP1) SharePoint. Для новой установки не [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] требуется накопительное обновление. Дополнительные сведения см. в разделе [накопительное обновление для SharePoint за август 2010](https://blogs.technet.com/b/stefan_gossner/archive/2010/09/02/august-2010-cumulative-update-for-sharepoint-has-been-released.aspx).|  
|Веб-приложение SharePoint|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]для SharePoint 2010 поддерживает только веб-приложения SharePoint, настроенные для проверки подлинности в классическом режиме. Если [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint добавляется в существующую ферму, убедитесь, что веб-приложение, которое планируется использовать, настроено для проверки подлинности в классическом режиме. Инструкции по проверке режима проверки подлинности см. в подразделе «Проверка того, что веб-приложение использует классический режим проверки подлинности» раздела [Развертывание решений PowerPivot в SharePoint](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/deploy-power-pivot-solutions-to-sharepoint).|  
|Поставщики данных, необходимые для обновления данных [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] на стороне сервера|При обновлении данных на стороне сервера повторяются те же шаги извлечения данных, которые первоначально используются для импорта данных. Это означает, что поставщики данных, используемые для импорта данных на клиентской рабочей станции, также должны присутствовать на сервере [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint.<br /><br /> Кроме того, для использования веб-каналов данных на сервере SharePoint требуется наличие служб данных ADO.NET Data Services. Установщик компонентов, необходимых для SharePoint, не устанавливает эти компоненты. Следующие приложения необходимо установить вручную.<br /><br /> Сборки среды выполнения ADO.NET Data Services 3.5 с пакетом обновления 1 (SP1), используемые для экспорта списка SharePoint как веб-канала данных. Загрузите и установите версию, соответствующую операционной системе.<br /><br /> Для Windows Server 2008 R2 используйте [обновление ADO.NET Data Services для .NET Framework 3,5 SP1 для Windows 7 и Windows Server 2008 R2](https://www.microsoft.com/download/details.aspx?id=2343). Windows Server 2008 R2 **с пакетом обновления 1 (SP1)** уже содержит обновленный поставщик.<br /><br /> Для Windows Server 2008 используйте [Обновление служб ADO.NET Data Services для .NET Framework 3,5 SP1 для windows 2000, Windows server 2003, Windows XP, Windows Vista и Windows server 2008 ( https://go.microsoft.com/fwlink/?LinkId=158125) ](https://www.microsoft.com/download/details.aspx?id=22734).|  
  
 [Определение требований к оборудованию и программному обеспечению (SharePoint 2010) (https://go.microsoft.com/fwlink/?LinkId=169734)](https://go.microsoft.com/fwlink/?LinkId=169734)  
  
## <a name="additional-information"></a>Дополнительные сведения  

