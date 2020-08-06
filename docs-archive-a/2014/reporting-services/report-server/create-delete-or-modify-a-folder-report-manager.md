---
title: Создание, изменение или удаление папки (диспетчер отчетов) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- removing folders
- modifying folders
- deleting folders
- folders [Reporting Services], creating
- folders [Reporting Services], deleting
- folders [Reporting Services], modifying
ms.assetid: d62159a8-ec67-4e28-a9f1-05a9250065bb
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9bd7d5ceebdb7b3a48ded66ed108bddda25d8a46
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87665804"
---
# <a name="create-delete-or-modify-a-folder-report-manager"></a>создать, изменить или удалить папку (диспетчер отчетов)
  Для упорядочения элементов и управления элементами, публикуемыми на сервере отчетов, можно создать папки. Создание папок поможет пользователям находить интересующие их отчеты. Для диспетчеров содержимого папки обеспечивают инфраструктуру для применения разрешений. Можно создать назначения ролей для определенных папок, чтобы ограничить доступ к отчетам, которые находятся на стадии разработки или не подлежат широкому распространению.  
  
### <a name="to-create-a-folder"></a>Создание папки  
  
1.  Запустите [Диспетчер отчетов (службы Reporting Services в основном режиме)](../report-manager-ssrs-native-mode.md).  
  
2.  В диспетчере отчетов выберите корневую папку, а затем нажмите **Создать папку**. Либо, чтобы создать папку внутри существующей папки, перейдите к этой папке на странице **Содержимое** , а затем щелкните папку, чтобы открыть ее. После этого нажмите **Создать папку**.  
  
     Откроется страница **Создание папки** .  
  
3.  Введите имя папки. Имя папки может включать пробелы, но не может содержать зарезервированные символы, используемые для кодирования URL-адреса: ; ? : \@ & = +, $/* \< > |. Нельзя указать последовательность имен папок, чтобы одновременно создать несколько папок.  
  
4.  При необходимости введите также описание.  
  
5.  Выберите пункт **Скрыть при отображении в виде списка** , если папка не должна отображаться в представлении по умолчанию страницы **Содержимое** . Она будет видна пользователям только после нажатия кнопки **Показать подробности** на странице **Содержимое** .  
  
6.  Нажмите кнопку **ОК**.  
  
### <a name="to-delete-a-folder"></a>Удаление папки  
  
1.  Перейдите в диспетчере отчетов на страницу **Содержимое** и найдите элемент, который нужно изменить.  
  
2.  Подведите курсор к элементу и щелкните стрелку раскрывающегося списка.  
  
3.  В раскрывающемся меню выберите **Удалить**.  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-modify-or-delete-a-folder"></a>Удаление или изменение папки  
  
1.  Перейдите в диспетчере отчетов на страницу **Содержимое** и найдите элемент, который нужно изменить.  
  
2.  Подведите курсор к элементу и щелкните стрелку раскрывающегося списка.  
  
3.  В раскрывающемся меню выберите **Управление**. Откроется страница «Общие свойства».  
  
4.  Для изменения местоположения папки нажмите кнопку **Переместить**. Введите путь к целевой папке или выберите место назначения в дереве папок, а затем нажмите кнопку **ОК**.  
  
5.  Или измените свойства папки одним из приведенных ниже способов.  
  
    -   Чтобы изменить отображаемые сведения о папке, введите имя или описание.  
  
    -   Чтобы папка отображалась в представлении по умолчанию страницы **Содержимое** , сбросьте флажок **Скрывать при просмотре списка**.  
  
6.  Или, если нужно удалить папку вместе с ее содержимым, нажмите кнопку **Удалить**.  
  
7.  Щелкните **Применить**, чтобы сохранить изменения.  
  
## <a name="see-also"></a>См. также:  
 [Страница "Создание папки" &#40;диспетчер отчетов&#41;](../new-folder-page-report-manager.md)   
 [Страница "содержимое" &#40;диспетчер отчетов&#41;](../contents-page-report-manager.md)   
 [Поиск, просмотр отчетов и управление ими (построитель отчетов и службы SSRS)](../report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md)  
  
  