---
title: Доступ к файлам, используемым пакетами | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SSIS packages, security
- packages [Integration Services], security
- configuration files [Integration Services]
- checkpoint files
- Integration Services packages, security
- logs [Integration Services], security
- files [Integration Services], security
- SQL Server Integration Services packages, security
ms.assetid: 2e3ddea9-5289-4289-a70e-11c018f34977
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8db9511c91c9f229b7002f5b16cf077910a4ccf0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87656542"
---
# <a name="access-to-files-used-by-packages"></a>Доступ к файлам, используемым пакетами
  Уровень защиты пакета не способен защитить файлы, хранимые вне пределов пакета. Эти файлы включают в себя:  
  
-   Файлы конфигурации.  
  
-   файлы контрольных точек  
  
-   Файлы журнала  
  
 Эти файлы должны быть защищены отдельно, особенно если они содержат конфиденциальные сведения.  
  
## <a name="configuration-files"></a>Файлы конфигурации  
 Если в файле конфигурации хранятся конфиденциальные сведения, такие как данные об имени входа и пароле, то следует сохранить файл в [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]или использовать список управления доступом (ACL), чтобы защитить расположение или папку, где хранится этот файл, и разрешить доступ только для определенных учетных записей. Обычно предоставляется доступ для тех учетных записей, которым разрешено запускать пакеты, управлять пакетами и разрешать проблемы, связанные с пакетами, в том числе проверять содержимое файла настройки, контрольные точки и файлы журнала. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] обеспечивает более безопасное хранение, так как предлагает защиту на уровне сервера и базы данных. Чтобы сохранить конфигурации в [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], следует использовать тип конфигурации [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Чтобы сохранить в файловую систему, следует использовать тип конфигурации XML.  
  
 Дополнительные сведения см. в разделах [Конфигурации пакетов](../../2014/integration-services/package-configurations.md), [Создание конфигураций пакетов](../../2014/integration-services/create-package-configurations.md)и [Вопросы безопасности при установке SQL Server](../../2014/sql-server/install/security-considerations-for-a-sql-server-installation.md).  
  
## <a name="checkpoint-files"></a>файлы контрольных точек  
 Таким же образом, если используемый пакетом файл контрольных точек содержит конфиденциальные сведения, то следует использовать список управления доступом (ACL) для защиты расположения или папки, где хранится этот файл. Файлы контрольных точек сохраняют данные как о текущем состоянии пакета, так и о текущих значениях переменных. Например, пакет может включать в себя пользовательскую переменную, содержащую номер телефона. Дополнительные сведения см. в разделе [Restart Packages by Using Checkpoints](packages/restart-packages-by-using-checkpoints.md).  
  
## <a name="log-files"></a>Файлы журнала  
 Записи журнала, сохраненные в файловой системе, также должны быть защищены с использованием списка управления доступом (ACL). Записи журнала также могут храниться в таблицах [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] и быть защищены системой безопасности [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Записи журнала могут содержать конфиденциальные сведения, например если пакет содержит задачу «Выполнение SQL», которая создает инструкцию SQL, ссылающуюся на номер телефона, то запись журнала для инструкции SQL содержит и номер телефона. Инструкция SQL также может раскрыть закрытые данные об именах таблиц и столбцов данных. Дополнительные сведения см. в разделе [Ведение журналов в службах Integration Services (SSIS)](performance/integration-services-ssis-logging.md).  
  
  
