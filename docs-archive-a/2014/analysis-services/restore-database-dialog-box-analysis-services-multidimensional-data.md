---
title: Диалоговое окно «Восстановление базы данных» (Analysis Services-многомерные данные) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.Restore.f1
ms.assetid: a3990d47-55e2-424e-8eac-87edc937e806
author: minewiskan
ms.author: owend
ms.openlocfilehash: f45a41eb10e81e1cfe1100045cc4d00353cb11fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87752424"
---
# <a name="restore-database-dialog-box-analysis-services---multidimensional-data"></a>Диалоговое окно «Восстановление базы данных» (службы Analysis Services — многомерные данные)
  Диалоговое окно **Восстановление базы данных** используется в среде [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] для восстановления базы данных служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] из файла резервной копии служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] (ABF).  
  
> [!IMPORTANT]  
>  Пользователь, выполняющий команду восстановления, должен иметь разрешение на чтение из папки резервного копирования, указанной для каждого восстанавливаемого файла. Чтобы восстановить базу данных служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , которая не установлена на сервере, пользователь также должен быть членом роли сервера для этого экземпляра служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] . Чтобы перезаписать базу данных служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , пользователь должен быть членом одной из следующих ролей: роль сервера для экземпляра служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] или роль базы данных с разрешениями "Полный доступ (администратор)" в восстанавливаемой базе данных.  
  
> [!NOTE]  
>  После восстановления существующей базы данных пользователь, выполнявший восстановление, может утратить доступ к этой базе данных. Потеря доступа может произойти в случае, если на время создания резервной копии этот пользователь не был членом роли сервера и роли базы данных с разрешением «Полный доступ (Администратор)».  
  
 **Отображение диалогового окна «Восстановление базы данных»**  
  
-   В среде [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]щелкните правой кнопкой мыши папку **Базы данных** экземпляра [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] или базу данных в **обозревателе объектов**, а затем выберите **Восстановить**.  
  
 Диалоговое окно **Восстановление базы данных** содержит следующие страницы.  
  
## <a name="pages"></a>Страницы  
 **Общие**  
 Эта страница используется для выбора базы данных, подлежащей восстановлению, файла резервной копии, а также общих параметров и пароля, который будет использоваться для восстановления базы данных. Дополнительные сведения об этой странице см. в разделе [Общие (диалоговое окно "Восстановление базы данных") (службы Analysis Services — многомерные данные)](general-restore-database-dialog-box-analysis-services-multidimensional-data.md).  
  
 **Секции**  
 Эта страница используется для восстановления локальных секций в заданном расположении и для восстановления удаленных секций из удаленных файлов резервных копий. Дополнительные сведения об этой странице см. в разделе [Секции (диалоговое окно "Восстановление базы данных") (службы Analysis Services — многомерные данные)](partitions-restore-database-dialog-box-analysis-services-multidimensional-data.md).  
  
## <a name="see-also"></a>См. также:  
 [Analysis Services конструкторов и диалоговых окон &#40;многомерных данных&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Создание и восстановление резервных копий баз данных служб Analysis Services](multidimensional-models/backup-and-restore-of-analysis-services-databases.md)  
  
  
