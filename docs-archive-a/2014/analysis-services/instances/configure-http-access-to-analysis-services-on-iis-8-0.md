---
title: Настройка доступа по протоколу HTTP к Analysis Services на службы IIS (IIS) 8,0 | Документация Майкрософт
ms.custom: ''
ms.date: 06/19/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: cf2e2c84-0a69-4cdd-90a1-fb4021936513
author: minewiskan
ms.author: owend
ms.openlocfilehash: 00fc6fcdf059bb26602e20d4c7fc8fb46edcfb9c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731129"
---
# <a name="configure-http-access-to-analysis-services-on-internet-information-services-iis-80"></a>Настройка HTTP-доступа к службам Analysis Services в службах Internet Information Services (IIS) 8.0
  В этой статье объясняется, как настроить конечную точку HTTP для доступа к экземпляру служб Analysis Services. Доступ по протоколу HTTP к службам Analysis Services можно включить путем настройки MSMDPUMP.dll — расширения ISAPI, которое работает на сервере IIS и переносит данные между клиентским приложением и сервером служб Analysis Services. Такой подход предоставляет альтернативные способы подключения к службам Analysis Services, если применяемое решение бизнес-аналитики требует получения следующих возможностей.  
  
-   Доступ клиентов осуществляется по Интернету или экстрасети, с учетом ограничений на то, какие порты могут быть включены.  
  
-   Клиентские запросы на установление соединений поступают из не заслуживающих доверия доменов, находящихся в той же сети.  
  
-   Клиентское приложение работает в сетевой среде, где разрешены соединения HTTP, но не разрешены соединения TCP/IP.  
  
-   Клиентские приложения не могут использовать клиентские библиотеки служб Analysis Services (в качестве примера можно указать приложение Java, работающее на сервере UNIX). Если нет возможности использовать для доступа к данным клиентские библиотеки служб Analysis Services, то можно использовать для доступа SOAP и XML/A по прямому HTTP-соединению с экземпляром служб Analysis Services.  
  
-   Требуются методы проверки подлинности, отличные от встроенной безопасности Windows. В частности, при настройке служб Analysis Services для доступа по протоколу HTTP можно использовать анонимные соединения и обычную проверку подлинности. Проверка подлинности с помощью дайджестов, форм и ASP.NET не поддерживается. Требование для обычной проверки подлинности является одной из основных причин для включения доступа по протоколу HTTP. Подробнее см. в разделе [Проверка подлинности для бизнес-аналитики Майкрософт и делегирование удостоверений](https://go.microsoft.com/fwlink/?LinkId=286576).  
  
 Доступ по протоколу HTTP можно настроить для любой поддерживаемой версии или выпуска служб Analysis Services, работающих в табличном или многомерном режиме. Исключением являются локальные кубы. Установить подключение к локальному кубу через конечную точку HTTP нельзя.  
  
 Настройка доступа по протоколу HTTP является задачей, выполняемой после установки. Сначала необходимо установить службы Analysis Services, а затем их можно настроить для доступа по протоколу HTTP. Администратор служб Analysis Services должен предоставить разрешения учетным записям Windows перед активацией доступа по протоколу HTTP. Кроме того, сначала рекомендуется проверить установку, чтобы убедиться в ее полной функциональности, и только после этого выполнять дальнейшие действия по настройке сервера. После настройки доступа по протоколу HTTP можно использовать и конечную точку HTTP, и обычное сетевое имя сервера по протоколу TCP/IP. Настройка доступа по протоколу HTTP не отменяет других способов доступа к данным.  
  
 Выполняя дальнейшую настройку MSMDPUMP, необходимо принять во внимание наличие двух типов подключения: подключение клиента к службам IIS и подключение служб IIS к службам SSAS. Приведенные в данной статье инструкции относятся к подключению служб IIS к SSAS. Перед подключением к серверу IIS может потребоваться дополнительная настройка клиентского приложения. Вопросы о том, почему следует использовать протокол SSL и как настроить привязки, выходят за рамки данной статьи. Подробнее о службах IIS см. в разделе [Веб-сервер (IIS)](https://technet.microsoft.com/library/hh831725.aspx) .  
  
 Этот раздел включает следующие подразделы:  
  
-   [Обзор](#bkmk_overview)  
  
-   [Предварительные требования](#bkmk_prereq)  
  
-   [Копирование MSMDPUMP.dll в папку на веб-сервере](#bkmk_copy)  
  
-   [Создайте пул приложений и виртуальный каталог на сервере IIS](#bkmk_appPool)  
  
-   [Настройка аутентификации IIS и добавление расширения](#bkmk_auth)  
  
-   [В файле MSMDPUMP.INI укажите целевой сервер](#bkmk_edit)  
  
-   [Проверка конфигурации](#bkmk_test)  
  
##  <a name="overview"></a><a name="bkmk_overview"></a> Обзор  
 MSMDPUMP является расширением ISAPI, которое загружается в службы IIS и обеспечивает перенаправление на локальный или удаленный экземпляр служб Analysis Services. В процессе настройки данного расширения ISAPI создается конечная точка HTTP для экземпляра служб Analysis Services.  
  
 Для каждой конечной точки HTTP необходимо создать и настроить по одному виртуальному каталогу. Для каждой конечной точки потребуется собственный набор файлов MSMDPUMP, для каждого экземпляра служб Analysis Services, соединение с которым требуется обеспечить. В файле конфигурации из этого набора файлов задается имя экземпляра служб Analysis Services, используемого для каждой конечной точки HTTP.  
  
 При работе с сервером IIS MSMDPUMP обеспечивает подключение к службам Analysis Services с помощью поставщика OLE DB служб Analysis Services по протоколу TCP/IP. Хотя клиентские запросы могут исходить и не от надежных доменов, для успешного выполнения собственного соединения службы Analysis Services и IIS должны находиться в одном и том же домене или в надежных доменах.  
  
 Когда MSMDPUMP подключается к службам Analysis Services, используется идентификатор пользователя Windows. Эта учетная запись должна быть либо анонимной учетной записью (если выполнена настройка виртуального каталога для анонимных соединений), либо учетной записью пользователя Windows. Эта учетная запись должна иметь соответствующие права доступа к данным на сервере и в базе данных служб Analysis Services.  
  
 ![Диаграмма, показывающая соединения между компонентами](../media/ssas.gif "Диаграмма, показывающая соединения между компонентами")  
  
 В следующей таблице приведены дополнительные соображения, касающиеся разрешения доступа по протоколу HTTP в различных сценариях.  
  
|Сценарий|Параметр Configuration|  
|--------------|-------------------|  
|Размещение служб IIS и Analysis Services на одном и том же компьютере|Это простейший вариант настройки конфигурации, поскольку позволяет использовать конфигурацию по умолчанию (где именем сервера является localhost), локальный поставщик OLE DB служб Analysis Services и встроенную безопасность Windows с NTLM. При условии, что клиент находится в том же домене, проверка подлинности становится прозрачной для пользователя, без каких-либо дополнительных действий с вашей стороны.|  
|Размещение служб IIS и Analysis Services на разных компьютерах|Для реализации этой топологии необходимо установить поставщик OLE DB для служб Analysis Services на веб-сервере. Необходимо также изменить файл msmdpump.ini, чтобы указать местоположение экземпляра служб Analysis Services на удаленном компьютере.<br /><br /> В этой топологии происходит добавление шага проверки подлинности в виде двойного транзитного перехода, при котором учетные данные должны передаваться от клиента к веб-серверу, а затем к внутреннему серверу служб Analysis Services. При использовании учетных данных Windows и NTLM возвращается ошибка, поскольку NTLM не допускает делегирования учетных данных клиента второму серверу. Чаще всего используемое решение заключается в использовании обычной проверки подлинности по протоколу SSL, но для этого при доступе к виртуальному каталогу MSMDPUMP пользователь должен указывать имя пользователя и пароль. Более простой подход может состоять во включении протокола Kerberos и настройке ограниченного делегирования служб Analysis Services, чтобы пользователи могли получать прозрачный доступ к службам Analysis Services. Дополнительные сведения см. в разделе [Configure Analysis Services for Kerberos constrained delegation](configure-analysis-services-for-kerberos-constrained-delegation.md) .<br /><br /> Обдумайте, какие порты следует разблокировать в брандмауэре Windows. Необходимо открыть порты на обоих серверах, чтобы разрешить доступ к веб-приложению на сервере IIS, а также доступ к службам Analysis Services на удаленном сервере.|  
|Клиентские соединения осуществляются из недоверенных доменов или из соединений экстрасети.|Клиентские соединения из недоверенных доменов влекут дополнительные ограничения на процесс проверки подлинности. По умолчанию в службах Analysis Services используется встроенная проверка подлинности Windows, которая требует, чтобы пользователи находились в том же домене, что и сервер. Если имеются пользователи экстрасети, подключающиеся к серверу IIS из-за пределов домена, то при настройке сервера с параметрами по умолчанию для таких пользователей будет выводиться сообщение об ошибке.<br /><br /> В качестве обходного пути решения проблемы можно настроить подключение пользователей из экстрасети по виртуальной частной сети (VPN) с использованием учетных данных домена. Однако лучшим вариантом может быть включение обычной проверки подлинности и SSL на веб-сайте служб IIS.|  
  
##  <a name="prerequisites"></a><a name="bkmk_prereq"></a> Предварительные требования  
 В инструкциях данной статьи предполагается, что службы IIS уже настроены, а службы Analysis Services уже установлены. Windows Server 2012 поставляется с IIS 8.x в виде роли сервера, которую можно включить в системе.  
  
 **Дополнительная настройка в IIS 8.0**  
  
 В конфигурациях по умолчанию служб IIS 8.0 отсутствуют компоненты, необходимые для доступа к службам Analysis Services по протоколу HTTP. В число таких компонентов, которые находятся в областях компонентов **Безопасность** и **Разработка приложений** роли **Веб-сервер (IIS)** , входят следующие.  
  
-   **Безопасность**  |  **Проверка подлинности Windows**, **Обычная проверка подлинности**и другие функции безопасности, необходимые для сценария доступа к данным.  
  
-   **Разработка приложений**  |  **CGI**  
  
-   **Разработка приложений**  |  **Расширения ISAPI**  
  
 Чтобы проверить или добавить эти компоненты, используйте **Диспетчер сервера**  |  **Управление**  |  **добавлением ролей и компонентов**. Выполните все шаги мастера, пока не дойдете до страницы **Роли сервера**. Прокрутите вниз, чтобы найти пункт **Веб-сервер (IIS)**.  
  
1.  Откройте **безопасность веб-сервера**  |  **Security** и выберите методы проверки подлинности.  
  
2.  Откройте разработку приложений **веб-сервера**  |  **Application Development** и выберите расширения **CGI** и **ISAPI**.  
  
     ![Добавление страницы функций для роли веб-сервера](../media/ssas-httpaccess-isapicgi.png "Добавление страницы функций для роли веб-сервера")  
  
 **Если службы IIS запущены на удаленном сервере**  
  
 Для удаленного подключения между службами IIS и Analysis Services необходимо установить поставщик OLE DB служб Analysis Services (MSOLAP) на сервере Windows, где запущены службы IIS.  
  
1.  Перейдите на страницу загрузки [пакета дополнительных компонентов SQL Server 2014](https://www.microsoft.com/download/details.aspx?id=42295)  
  
2.  Щелкните красную кнопку "Скачать".  
  
3.  Прокрутите вниз, чтобы найти ENU\x64\SQL_AS_OLEDB.msi  
  
4.  Выполните инструкции мастера, чтобы завершить установку.  
  
> [!NOTE]  
>  Не забудьте разблокировать порты в брандмауэре Windows, чтобы он разрешал клиентские подключения к удаленному серверу служб Analysis Services. Дополнительные сведения см. в статье [Configure the Windows Firewall to Allow Analysis Services Access](configure-the-windows-firewall-to-allow-analysis-services-access.md).  
  
##  <a name="step-1-copy-the-msmdpump-files-to-a-folder-on-the-web-server"></a><a name="bkmk_copy"></a>Шаг 1. копирование файлов MSMDPUMP в папку на веб-сервере  
 Каждая создаваемая конечная точка HTTP должна иметь собственный набор файлов MSMDPUMP. На этом этапе необходимо скопировать исполняемый файл MSMDPUMP, файл конфигурации и папку ресурсов из папок программ служб Analysis Services в новую папку виртуального каталога. Эта папка будет создана в файловой системе компьютера, на котором выполняется служба IIS.  
  
 Диск должен быть отформатирован для работы с файловой системой NTFS. Путь к создаваемой папке не должен содержать пробелов.  
  
1.  Скопируйте следующие файлы, расположенные в \<drive> папке: \Program Files\Microsoft SQL Server \\<instance \> \OLAP\bin\isapi: MSMDPUMP.DLL, MSMDPUMP.INI и папку ресурсов.  
  
     ![Файлы в проводнике для копирования](../media/ssas-httpaccess-msmdpumpfilecopy.PNG "Файлы в проводнике для копирования")  
  
2.  На веб-сервере создайте новую папку: \<drive> : \Inetpub\wwwroot \\ **OLAP**  
  
3.  Вставьте ранее скопированные файлы в эту новую папку.  
  
4.  Проверьте, чтобы в папке \inetpub\wwwroot\OLAP на веб-сервере содержалось следующее: файлы MSMDPUMP.DLL, MSMDPUMP.INI и папка Resources. Структура папки должна выглядеть следующим образом:  
  
    -   \<drive>:\inetpub\wwwroot\OLAP\MSMDPUMP.dll  
  
    -   \<drive>:\inetpub\wwwroot\OLAP\MSMDPUMP.ini  
  
    -   \<drive>: \Инетпуб\ввврут\олап\ресаурцес  
  
##  <a name="step-2-create-an-application-pool-and-virtual-directory-in-iis"></a><a name="bkmk_appPool"></a> Шаг 2. Создание пула приложений и виртуального каталога на сервере IIS  
 Затем создайте пул приложений и конечную точку для средства переноса.  
  
#### <a name="create-an-application-pool"></a>Создание пула приложений  
  
1.  Запустите диспетчер IIS.  
  
2.  Откройте папку сервера, щелкните правой кнопкой мыши **Пулы приложений** и выберите пункт **Добавить пул приложений**. Используя .NET Framework, создайте пул приложений с именем **OLAP**, а для управляемого конвейера установите режим **Классический**.  
  
     ![Снимок экрана: диалоговое окно «Добавление пула приложений»](../media/ssas-httpaccess.PNG "Снимок экрана: диалоговое окно «Добавление пула приложений»")  
  
3.  По умолчанию службы IIS создают пулы приложений с использованием **ApplicationPoolIdentity** в качестве удостоверения безопасности, которое является допустимым выбором для доступа к службам Analysis Services по протоколу HTTP. Если вам по какой-либо причине нужно изменить удостоверение, щелкните правой кнопкой мыши **OLAP**и выберите пункт **Дополнительные параметры**. Выберите **ApplicationPoolIdentity**. Нажмите кнопку **Изменить** , относящуюся к этому свойству, чтобы заменить встроенную учетную запись пользовательской учетной записью, которая будет использоваться.  
  
     ![Снимок экрана: страница свойств «Дополнительные параметры»](../media/ssas-httpaccess-advsettings.PNG "Снимок экрана: страница свойств «Дополнительные параметры»")  
  
4.  По умолчанию в 64-разрядной версии операционной системы служба IIS присваивает свойству **Разрешить 32-разрядные приложения** значение **false**. Если файл msmdpump.dll скопирован из 64-разрядной установки служб Analysis Services, то настройка модуля MSMDPUMP на 64-разрядном сервере IIS уже выполнена правильно. Если двоичные файлы MSMDPUMP скопированы из 32-разрядной установки, присвойте этому параметру значение **true**. Проверьте это свойство в разделе **Дополнительные параметры** , чтобы убедиться, что оно задано правильно.  
  
#### <a name="create-an-application"></a>Создание приложения  
  
1.  В диспетчере IIS откройте **Сайты**, а затем откройте **Веб-сайт по умолчанию**. Должна появиться папка с именем **Olap**. Это ссылка на папку OLAP, созданную в каталоге \inetpub\wwwroot.  
  
     ![Папка OLAP на веб-узле по умолчанию](../media/ssas-httpaccess-convertfolderbefore.png "Папка OLAP на веб-узле по умолчанию")  
  
2.  Щелкните правой кнопкой мыши папку и выберите пункт **Преобразовать в приложение**.  
  
3.  В окне "Добавление приложения" введите **OLAP** для псевдонима. Щелкните **Выбрать** , чтобы выбрать пул приложений OLAP. Физический путь должен иметь значение C:\inetpub\wwwroot\OLAP  
  
     ![Диалоговое окно «Добавление приложения»](../media/ssas-httpaccess-convertedapp.png "Диалоговое окно «Добавление приложения»")  
  
4.  Нажмите кнопку **ОК**. Обновите веб-сайт и обратите внимание, что теперь папка OLAP является приложением на веб-сайте по умолчанию. Виртуальный путь к файлу MSMDPUMP установлен.  
  
     ![Папка OLAP после преобразования приложения](../media/ssas-httpaccess-convertfolderafter.png "Папка OLAP после преобразования приложения")  
  
> [!NOTE]  
>  В предыдущие версии этих инструкций входили действия по созданию виртуального каталога. Теперь они не требуются.  
  
##  <a name="step-3-configure-iis-authentication-and-add-the-extension"></a><a name="bkmk_auth"></a> Шаг 3. Настройка аутентификации IIS и добавление расширения  
 В этом шаге продолжается настройка только что созданного виртуального каталога SSAS. Должен быть указан метод проверки подлинности, а затем добавлена схема скриптов. Поддерживаемые методы проверки подлинности для доступа к службам Analysis Services по протоколу HTTP:  
  
-   Проверка подлинности Windows (Kerberos или NTLM)  
  
-   Обычная проверка подлинности  
  
-   анонимная аутентификация;  
  
 **Проверка подлинности Windows** считается наиболее безопасной и предусматривает применение существующей инфраструктуры для сетей, в которых используется Active Directory. Чтобы проверка подлинности Windows использовалась эффективно, ее должны поддерживать все браузеры, клиентские и серверные приложения. Это — наиболее безопасный режим, который рекомендуется использовать. Но для этого серверу IIS требуется доступ к контроллеру домена Windows, который может проверить подлинность идентификатора пользователя, запрашивающего подключение.  
  
 В таких топологиях, которые предусматривают размещение служб Analysis Services и IIS на разных компьютерах, приходится решать проблемы двойного транзитного перехода, которые возникают в связи с необходимостью делегировать проверку учетных данных пользователя второй службе на удаленном компьютере, как правило, путем включения служб Analysis Services для ограниченного делегирования Kerberos. Дополнительные сведения см. в разделе [Configure Analysis Services for Kerberos constrained delegation](configure-analysis-services-for-kerberos-constrained-delegation.md).  
  
 **Обычная проверка подлинности** используется при наличии идентификаторов Windows, но пользовательские запросы на подключение поступают из недоверенных доменов, что не позволяет устанавливать делегированные или олицетворяемые подключения. Обычная проверка подлинности позволяет указать учетные данные пользователя и пароль в строке подключения. Для подключения к службам Analysis Services вместо контекста безопасности текущего пользователя применяются учетные данные из строки подключения. Службы Analysis Services поддерживают только проверку подлинности Windows, поэтому любые передаваемые им учетные данные должны представлять пользователя (или группу) Windows, который является членом домена, где размещены службы Analysis Services.  
  
 **Анонимная проверка подлинности** часто используется во время начального тестирования, поскольку при этом настройка является несложной и это позволяет быстро проверить возможность подключения к службам Analysis Services по протоколу HTTP. С помощью всего лишь нескольких шагов можно назначить уникальную учетную запись пользователя в качестве идентификатора, предоставить этой учетной записи разрешения в службах Analysis Services, воспользоваться учетной записью для проверки возможности доступа к данным в клиентском приложении, а затем отключить анонимную проверку подлинности по завершении тестирования.  
  
 Анонимную проверку подлинности можно также использовать в рабочей среде, если у пользователей нет учетных записей Windows, но они следуют рекомендациям (блокируют распространение разрешений на хост-систему), приведенным в статье [Включение анонимной проверки подлинности (IIS 7)](https://technet.microsoft.com/library/cc731244\(v=ws.10\).aspx). Проверка подлинности должна задаваться применительно к виртуальному каталогу, а не к родительскому веб-сайту, что позволяет дополнительно понизить уровень доступа учетной записи.  
  
 Если включена анонимная проверка подлинности, то любое пользовательское соединение с конечной точкой HTTP получает разрешение на подключение в качестве анонимного пользователя. Вы не сможете проводить аудит подключений отдельных пользователей, а также использовать удостоверение пользователя для выбора данных из модели. Вполне очевидно, что применение анонимной проверки подлинности затрагивает все, начиная от проектирования модели и заканчивая обновлением данных и доступом к ним. Но если пользователи не имеют имен входа пользователей Windows, с которых можно было бы начать, то единственным вариантом становится применение анонимной учетной записи.  
  
#### <a name="set-the-authentication-type-and-add-a-script-map"></a>Задание типа проверки подлинности и добавление сопоставления скриптов  
  
1.  В диспетчере служб IIS откройте **Веб-сайты**, откройте **Веб-сайт по умолчанию**и выберите виртуальный каталог **OLAP** .  
  
2.  Дважды щелкните элемент **Проверка подлинности** в разделе IIS на главной странице.  
  
     ![Снимок экрана: главная страница диспетчера служб IIS](../media/ssas-httpaccess-iis.png "Снимок экрана: главная страница диспетчера служб IIS")  
  
3.  Если используется встроенная безопасность Windows, выберите пункт **Проверка подлинности Windows** .  
  
     ![Снимок экрана: параметры проверки подлинности Vdir](../media/ssas-httpaccess-iisauth.png "Снимок экрана: параметры проверки подлинности Vdir")  
  
4.  Или включите **обычную проверку подлинности** , если клиентские и серверные приложения находятся в разных доменах. В этом режиме пользователь должен вводить имя пользователя и пароль. Имя пользователя и пароль передаются через HTTP-соединение в службы IIS. При подключении к MSMDPUMP в службах IIS предпринимается попытка олицетворения пользователя с применением предоставленных учетных данных, но эти учетные данные не будут делегированы в службы Analysis Services. Вместо этого необходимо передать через подключение допустимое имя пользователя и пароль, как описано в шаге 6 этого документа.  
  
    > [!IMPORTANT]  
    >  Следует учитывать, что при построении системы, в которой пароль передается по каналу связи, необходимо предусмотреть способ защиты этого канала. Службы IIS предоставляют набор средств, помогающих защитить канал. Дополнительные сведения см. в разделе [Настройка SSL в IIS 7](https://go.microsoft.com/fwlink/?LinkId=207562).  
  
5.  Отключите **анонимную проверку подлинности** , если используется проверка подлинности Windows или обычная проверка подлинности. Если включена анонимная проверка подлинности, в службах IIS она всегда используется в первую очередь, даже если включены другие методы проверки подлинности.  
  
     При анонимной проверке подлинности средство ввода-вывода (msmdpump.dll) работает в качестве учетной записи пользователя, установленной для анонимного пользователя. Нет никакого различия между пользователем, подключающимся к службам IIS, и пользователем, подключающимся к службам Analysis Services. По умолчанию в службах IIS используется учетная запись IUSR, но можно сменить ее на учетную запись пользователя домена, которая имеет разрешения в сети. Эта возможность необходима, если службы IIS и Analysis Services находятся на разных компьютерах.  
  
     Инструкции по настройке учетных данных для анонимной проверки подлинности см. в разделе [Анонимная проверка подлинности](http://www.iis.net/configreference/system.webserver/security/authentication/anonymousauthentication).  
  
    > [!IMPORTANT]  
    >  Наиболее велика вероятность того, что с анонимной проверкой подлинности придется столкнуться в чрезвычайно строго контролируемой среде, где предоставление доступа или отказ в доступе для пользователей осуществляются с помощью списков управления доступом в файловой системе. Рекомендации см. в статье [Включение анонимной проверки подлинности (IIS 7)](https://technet.microsoft.com/library/cc731244\(v=ws.10\).aspx).  
  
6.  Щелкните виртуальный каталог **OLAP** , чтобы открыть главную страницу. Дважды щелкните элемент **Сопоставления обработчика**.  
  
     ![Значок сопоставления обработчика на странице компонента](../media/ssas-httpaccess-handlermapping.png "Значок сопоставления обработчика на странице компонента")  
  
7.  Щелкните правой кнопкой мыши в любом месте страницы и выберите пункт **Добавить карту скриптов**. В диалоговом окне Добавление схемы скрипта в качестве пути запроса укажите ** \* . dll** , укажите c:\inetpub\wwwroot\OLAP\msmdpump.dll в качестве исполняемого файла и введите в качестве имени **OLAP** . Сохраните все ограничения по умолчанию, связанные с этой картой скриптов.  
  
     ![Снимок экрана: диалоговое окно «Добавление карты скрипта»](../media/ssas-httpaccess-addscript.png "Снимок экрана: диалоговое окно «Добавление карты скрипта»")  
  
8.  При запросе на включение расширения ISAPI нажмите кнопку **Да**.  
  
     ![Снимок экрана: подтверждение добавления расширения ISAPI](../media/ssas-httpaccess-isapiprompt.png "Снимок экрана: подтверждение добавления расширения ISAPI")  
  
##  <a name="step-4-edit-the-msmdpumpini-file-to-set-the-target-server"></a><a name="bkmk_edit"></a> Шаг 4. Указание целевого сервера в файле MSMDPUMP.INI  
 В файле MSMDPUMP.INI указан экземпляр служб Analysis Services, к которому подключается MSMDPUMP.DLL. Этот экземпляр может быть локальным или удаленным, установленным как применяемый по умолчанию или как именованный.  
  
 Откройте файл msmdpump.ini, расположенный в папке «C:\inetpub\wwwroot\OLAP», и изучите содержимое этого файла. Это должно выглядеть примерно так:  
  
```  
<ConfigurationSettings>  
<ServerName>localhost</ServerName>  
<SessionTimeout>3600</SessionTimeout>  
<ConnectionPoolSize>100</ConnectionPoolSize>  
</ConfigurationSettings>  
  
```  
  
 Если экземпляр служб Analysis Services, для которого настраивается доступ через HTTP, расположен на локальном компьютере и является экземпляром по умолчанию, нет причин для изменения этого параметра. В противном случае необходимо указать имя сервера (например, \<ServerName> ADWRKS-SRV01 \</ServerName> ). Для сервера, установленного как именованный экземпляр, обязательно добавьте имя экземпляра (например, \<ServerName> ADWRKS-SRV01\Tabular \</ServerName> ).  
  
 По умолчанию экземпляр служб Analysis Services прослушивает TCP/IP-порт 2383. Если вы установили Analysis Services в качестве экземпляра по умолчанию, вам не нужно указывать какой-либо порт, \<ServerName> так как Analysis Services знает, как прослушивать порт 2383 автоматически. Тем не менее необходимо разрешить входящие соединения с этим портом в брандмауэре Windows. Дополнительные сведения см. в статье [Configure the Windows Firewall to Allow Analysis Services Access](configure-the-windows-firewall-to-allow-analysis-services-access.md).  
  
 Если вы настроили именованный или заданный по умолчанию экземпляр Analysis Services для прослушивания фиксированного порта, необходимо добавить номер порта к имени сервера (например, \<ServerName> AW-SRV01:55555 \</ServerName> ) и разрешить входящие подключения в брандмауэре Windows к этому порту.  
  
## <a name="step-5-grant-data-access-permissions"></a>Шаг 5. Предоставление разрешений на доступ к данным  
 Как было отмечено выше, необходимо предоставить разрешения на доступ к экземпляру служб Analysis Services. Каждый объект базы данных имеет роли, предоставляющие заданный уровень разрешений (на чтение или чтение и запись), а каждая роль имеет членов, состоящих из учетных данных пользователей Windows.  
  
 Для задания разрешений можно использовать среду SQL Server Management Studio. В папке "роли **базы данных**"  |  **Roles** можно создавать роли, задавать разрешения базы данных, назначать членство в учетных записях пользователей или групп Windows, а затем предоставлять разрешения на чтение или запись для конкретных объектов. Как правило, для клиентских подключений, в которых используются, но не обновляются, данные модели, достаточно разрешений **на чтение** применительно к кубу.  
  
 Назначение ролей зависит от того, как настроена проверка подлинности.  
  
|||  
|-|-|  
|Анонимный|Добавьте к списку Membership учетную запись, указанную в окне **Редактирование учетных данных анонимной проверки подлинности** в службах IIS. Дополнительные сведения см. в разделе [Анонимная проверка подлинности](http://www.iis.net/configreference/system.webserver/security/authentication/anonymousauthentication),|  
|Проверка подлинности Windows|Добавьте к списку Membership учетные записи пользователей или групп Windows, запрашивающих данные служб Analysis Services с помощью олицетворения или делегирования.<br /><br /> Если используется ограниченное делегирование Kerberos, единственными учетными записями, которым требуются разрешения, являются учетные записи пользователей и групп Windows, запрашивающие доступ. Для удостоверения пула приложений разрешения не нужны.|  
|Обычная проверка подлинности|Добавьте к списку Membership учетные записи пользователей или групп Windows, которые будут передаваться в строке подключения.<br /><br /> Кроме того, если учетные данные передаются через `EffectiveUserName` в строке подключения, удостоверение пула приложений должно иметь права администратора в экземпляре служб Analysis Services. В среде SSMS щелкните правой кнопкой мыши экземпляр &#124; **свойства** &#124; **Безопасность** &#124; **добавить**. Введите удостоверение пула приложений. Если используется встроенное удостоверение по умолчанию, то учетная запись указывается как **IIS AppPool\DefaultAppPool**.<br /><br /> ![](../media/ssas-httpaccess-iisapppoolidentity.png)|  
  
 Дополнительные сведения см. в разделе [Предоставление доступа к объектам и операциям (службы Analysis Services)](../multidimensional-models/authorizing-access-to-objects-and-operations-analysis-services.md).  
  
##  <a name="step-6-test-your-configuration"></a><a name="bkmk_test"></a> Шаг 6. Проверка конфигурации  
 Синтаксис строки подключения для MSMDPUMP определен — это URL-адрес файла MSMDPUMP.dll.  
  
 Если веб-приложение прослушивает фиксированный порт, добавьте номер порта к имени или IP-адресу сервера, например, `http://my-web-srv01:8080/OLAP/msmdpump.dll` или `http://123.456.789.012:8080/OLAP/msmdpump.dll` .  
  
 Чтобы быстро проверить подключение, можно открыть его с помощью Microsoft Excel или среды SQL Server Management Studio.  
  
 **Тестирование подключений с использованием среды SQL Server Management Studio**  
  
1.  В диалоговом окне «Подключение к серверу» среды Management Studio в качестве типа сервера выберите **Службы Analysis Services** . В поле "Имя сервера" введите адрес HTTP расширения msmdpump: `http://my-web-srv01/OLAP/msmdpump.dll`.  
  
     HTTP-подключение отображается в обозревателе объектов.  
  
     ![HTTP-соединение с SSAS в обозревателе объектов](../media/ssas-httpaccess-ssms.PNG "HTTP-соединение с SSAS в обозревателе объектов")  
  
2.  Проверка подлинности должна быть задана как проверка подлинности Windows, а лицом, использующим среду Management Studio, должен быть администратор служб Analysis Services. Администратор может предоставить дополнительные разрешения для доступа других пользователей.  
  
 **Тестирование подключений с использованием Excel**  
  
1.  На вкладке "Данные" в Excel в группе "Получить внешние данные" нажмите кнопку **Из других источников**, а затем выберите **Из служб аналитики** , чтобы запустить мастер подключения данных.  
  
2.  В поле "Имя сервера" введите адрес HTTP расширения msmdpump: `http://my-web-srv01/OLAP/msmdpump.dll`.  
  
3.  В качестве значения «Учетные данные входа в систему» выберите **Проверка подлинности Windows** , если применяется встроенная безопасность Windows, NTLM или анонимный пользователь.  
  
     Применительно к обычной проверке подлинности выберите **Использовать следующее имя пользователя и пароль**, затем укажите учетные данные, применяемые для входа в систему. Предоставленные вами учетные данные будут переданы в службы Analysis Services в строке подключения.  
  
 **Тестирование подключений с использованием AMO**  
  
 Можно проверить доступ по HTTP программным путем с использованием AMO, подставляя URL-адрес конечной точки вместо имени сервера. Дополнительные сведения см. в записи форума [How to sync SSAS 2008 R2 databases via HTTPS across domain/forest and firewall boundaries](https://social.msdn.microsoft.com/Forums/en/sqlanalysisservices/thread/c4249d55-914d-4c81-9980-44d0b8df9c3e)(Как синхронизировать базы данных SSAS 2008 R2 по HTTPS через границы домена или леса и брандмауэра).  
  
 Ниже приведен пример строки подключения, который иллюстрирует синтаксис для доступа по HTTP(S) с использованием обычной проверки подлинности:  
  
 `Data Source=https://<servername>/olap/msmdpump.dll; Initial Catalog=AdventureWorksDW2012; Integrated Security=Basic; User ID=XXXX; Password=XXXXX;`  
  
 Дополнительные сведения о настройке подключения программным путем см. в разделе [Establishing Secure Connections in ADOMD.NET](https://docs.microsoft.com/analysis-services/adomd/multidimensional-models-adomd-net-client/connections-in-adomd-net-establishing-secure-connections).  
  
 В качестве конечного шага следует обязательно провести более строгое тестирование с использованием клиентского компьютера, эксплуатируемого в сетевой среде, из которого исходят запросы на подключение.  
  
## <a name="see-also"></a>См. также:  
 [Сообщение на форуме (доступ по протоколу HTTP с использованием MSMDPUMP и обычной проверки подлинности)](https://social.msdn.microsoft.com/Forums/en/sqlanalysisservices/thread/79d2f225-df35-46da-aa22-d06e98f7d658)   
 [Настройка брандмауэра Windows на разрешение доступа к Analysis Services](configure-the-windows-firewall-to-allow-analysis-services-access.md)   
 [Авторизация доступа к объектам и операциям &#40;Analysis Services&#41;](../multidimensional-models/authorizing-access-to-objects-and-operations-analysis-services.md)   
 [Методы проверки подлинности IIS](https://go.microsoft.com/fwlink/?LinkdID=208461)   
 [Как выполнить настройку SSL для работы с IIS 7](https://go.microsoft.com/fwlink/?LinkId=207562)  
  
