---
title: Ключи шифрования (собственный режим служб SSRS) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.encryptionkeypanel.F1
ms.assetid: cc7e6f84-80e1-4b5e-9409-d0e074edd147
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 78e9816a9e779459cd1388c1f7f10257c89b1ae5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87666408"
---
# <a name="encryption-keys-ssrs-native-mode"></a><span data-ttu-id="7f03e-102">Ключи шифрования (службы Reporting Services в собственном режиме)</span><span class="sxs-lookup"><span data-stu-id="7f03e-102">Encryption Keys (SSRS Native Mode)</span></span>
  <span data-ttu-id="7f03e-103">Используйте страницу «Ключи шифрования», чтобы управлять симметричным ключом, используемым для шифрования и дешифрования данных на сервере отчетов.</span><span class="sxs-lookup"><span data-stu-id="7f03e-103">Use the Encryption Keys page to manage the symmetric key that is used to encrypt and decrypt data in a report server.</span></span> <span data-ttu-id="7f03e-104">Управление ключами шифрования является важной частью настройки сервера отчетов.</span><span class="sxs-lookup"><span data-stu-id="7f03e-104">Managing the encryption keys is an important part of report server configuration.</span></span> <span data-ttu-id="7f03e-105">Симметричный ключ создается и применяется автоматически при создании базы данных сервера отчетов.</span><span class="sxs-lookup"><span data-stu-id="7f03e-105">The symmetric key is created and applied automatically when you create the report server database.</span></span> <span data-ttu-id="7f03e-106">Создайте резервную копию симметричного ключа, чтобы можно было выполнять обычные операции по обслуживанию.</span><span class="sxs-lookup"><span data-stu-id="7f03e-106">Create a backup copy of the symmetric key so that you can perform routine maintenance operations.</span></span> <span data-ttu-id="7f03e-107">Для выполнения следующих задач обслуживания потребуется действительная копия симметричного ключа:</span><span class="sxs-lookup"><span data-stu-id="7f03e-107">The following maintenance tasks require that you have a valid copy of the symmetric key:</span></span>  
  
-   <span data-ttu-id="7f03e-108">Изменение учетной записи службы для службы сервера отчетов.</span><span class="sxs-lookup"><span data-stu-id="7f03e-108">Changing the service account for the Report Server service.</span></span>  
  
-   <span data-ttu-id="7f03e-109">Перенос установки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] на другой компьютер.</span><span class="sxs-lookup"><span data-stu-id="7f03e-109">Migrating a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation to a different computer.</span></span>  
  
-   <span data-ttu-id="7f03e-110">Настройка нового экземпляра сервера отчетов для монопольного или совместного использования существующей базы данных сервера отчетов.</span><span class="sxs-lookup"><span data-stu-id="7f03e-110">Configuring a new report server instance to share or use an existing report server database.</span></span>  
  
 [!INCLUDE[applies](../../includes/applies-md.md)]<span data-ttu-id="7f03e-111">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Собственный режим.</span><span class="sxs-lookup"><span data-stu-id="7f03e-111">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="7f03e-112">Рекомендацией по безопасности является периодическая смена ключа шифрования служб Reporting Services.</span><span class="sxs-lookup"><span data-stu-id="7f03e-112">Periodically changing the Reporting Services encryption key is a security best practice.</span></span> <span data-ttu-id="7f03e-113">Рекомендуется менять ключ после каждого существенного обновления версии служб Reporting Services.</span><span class="sxs-lookup"><span data-stu-id="7f03e-113">A recommended time to change the key is immediately following a major version upgrade of Reporting Services.</span></span> <span data-ttu-id="7f03e-114">Смена ключа после обновления способствует снижению до минимума дополнительного прерывания в обслуживании, которое может быть вызвано сменой ключа шифрования служб Reporting Services вне цикла обновления.</span><span class="sxs-lookup"><span data-stu-id="7f03e-114">Changing the key after an upgrade minimizes additional service interruption caused by changing the Reporting Services encryption key outside of the upgrade cycle.</span></span>  
  
 <span data-ttu-id="7f03e-115">Восстановление симметричного ключа необходимо после обновления учетной записи службы сервера отчетов (если для смены учетной записи использовалось средство, отличное от диспетчера конфигурации служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ) или после переноса установки сервера отчетов на новый сервер.</span><span class="sxs-lookup"><span data-stu-id="7f03e-115">Restoring the symmetric key is necessary if you updated the user account of the Report Server service (and you used a tool other than the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager to change the account), or if you are migrating a report server installation to a new server.</span></span>  
  
 <span data-ttu-id="7f03e-116">Для защиты от несанкционированного доступа симметричный ключ шифруется при помощи закрытого ключа службы сервера отчетов.</span><span class="sxs-lookup"><span data-stu-id="7f03e-116">To protect the symmetric key from unauthorized access, the symmetric key is encrypted using the private key of the Report Server service.</span></span> <span data-ttu-id="7f03e-117">Только служба сервера отчетов имеет доступ к симметричному ключу и возможность пользоваться им для сохранения в базе данных сервера отчетов конфиденциальных данных.</span><span class="sxs-lookup"><span data-stu-id="7f03e-117">Only the Report Server service is able to unlock and use the symmetric key to store sensitive data in the report server database.</span></span> <span data-ttu-id="7f03e-118">После изменения удостоверения службы сервера отчетов или при переносе сервера отчетов на новый компьютер расшифровать симметричный ключ с помощью закрытого ключа службы сервера отчетов становится невозможно.</span><span class="sxs-lookup"><span data-stu-id="7f03e-118">If you change the identity of the Report Server service, or if you migrate the report server to a new computer, the private key of the Report Server service will no longer be able to unlock the symmetric key.</span></span> <span data-ttu-id="7f03e-119">Чтобы восстановить доступ к симметричному ключу, его необходимо заново зашифровать с помощью закрытого ключа из нового удостоверения службы сервера отчетов.</span><span class="sxs-lookup"><span data-stu-id="7f03e-119">To restore access to the symmetric key, re-encrypt the symmetric key using the private key of the new Report Server service identity.</span></span> <span data-ttu-id="7f03e-120">Восстановление симметричного ключа является процессом, при котором происходит повторное шифрование.</span><span class="sxs-lookup"><span data-stu-id="7f03e-120">Restoring the symmetric key is the process by which the re-encryption occurs.</span></span>  
  
 <span data-ttu-id="7f03e-121">Симметричный ключ необходимо восстанавливать только в том случае, если такой ключ на данный момент используется для шифрования и дешифрования данных в базе данных сервера отчетов.</span><span class="sxs-lookup"><span data-stu-id="7f03e-121">Only restore a symmetric key if it is the same key that is currently used to encrypt and decrypt data in the report server database.</span></span> <span data-ttu-id="7f03e-122">После восстановления недействительного симметричного ключа доступ к конфиденциальным данным будет закрыт.</span><span class="sxs-lookup"><span data-stu-id="7f03e-122">If you restore a symmetric key that is not valid, you can no longer access sensitive data.</span></span> <span data-ttu-id="7f03e-123">В этом случае необходимо удалить ключ и создать его повторно.</span><span class="sxs-lookup"><span data-stu-id="7f03e-123">In this case, delete and re-create the key.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="7f03e-124">Действие по удалению и повторному созданию симметричного ключа нельзя произвести в обратном направлении или отменить.</span><span class="sxs-lookup"><span data-stu-id="7f03e-124">The action of deleting and recreating the symmetric key cannot be reversed or undone.</span></span> <span data-ttu-id="7f03e-125">Удаление и повторное создание ключей может иметь важные последствия, влияющие на текущую установку.</span><span class="sxs-lookup"><span data-stu-id="7f03e-125">Deleting or recreating the key can have important ramifications on your current installation.</span></span> <span data-ttu-id="7f03e-126">При удалении ключа любые существующие данные, которые шифруются симметричным ключом, будут также удалены.</span><span class="sxs-lookup"><span data-stu-id="7f03e-126">If you delete the key, any existing data encrypted by the symmetric key will also deleted.</span></span> <span data-ttu-id="7f03e-127">Удаленные данные включают в себя строки соединения с внешними источниками данных отчетов, сохраненные строки соединения и некоторые сведения о подписках.</span><span class="sxs-lookup"><span data-stu-id="7f03e-127">Deleted data includes connection strings to external report data sources, stored connection strings, and some subscription information.</span></span>  
  
 <span data-ttu-id="7f03e-128">Чтобы открыть эту страницу, запустите диспетчер конфигурации служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] и выберите ссылку на панели навигации.</span><span class="sxs-lookup"><span data-stu-id="7f03e-128">To open this page, start the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager and select the link in the navigation pane.</span></span> <span data-ttu-id="7f03e-129">Дополнительные сведения см. в разделе [Использование диспетчера конфигурации служб Reporting Services (собственный режим)](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).</span><span class="sxs-lookup"><span data-stu-id="7f03e-129">For more information, see [Reporting Services Configuration Manager &#40;Native Mode&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="7f03e-130">Варианты</span><span class="sxs-lookup"><span data-stu-id="7f03e-130">Options</span></span>  
 <span data-ttu-id="7f03e-131">**Azure Backup**</span><span class="sxs-lookup"><span data-stu-id="7f03e-131">**Backup**</span></span>  
 <span data-ttu-id="7f03e-132">Копирует симметричный ключ в указанный файл.</span><span class="sxs-lookup"><span data-stu-id="7f03e-132">Copies the symmetric key to a file that you specify.</span></span> <span data-ttu-id="7f03e-133">Симметричный ключ никогда не хранится в виде простого текста.</span><span class="sxs-lookup"><span data-stu-id="7f03e-133">The symmetric key is never stored in plain text.</span></span> <span data-ttu-id="7f03e-134">Необходимо ввести пароль для защиты файла.</span><span class="sxs-lookup"><span data-stu-id="7f03e-134">You must type a password to protect the file.</span></span>  
  
 <span data-ttu-id="7f03e-135">**Восстановить**</span><span class="sxs-lookup"><span data-stu-id="7f03e-135">**Restore**</span></span>  
 <span data-ttu-id="7f03e-136">Применяет ранее сохраненную копию симметричного ключа к базе данных сервера отчетов.</span><span class="sxs-lookup"><span data-stu-id="7f03e-136">Applies a previously saved copy of the symmetric key to the report server database.</span></span> <span data-ttu-id="7f03e-137">Следует ввести пароль, чтобы разблокировать файл.</span><span class="sxs-lookup"><span data-stu-id="7f03e-137">You must provide the password to unlock the file.</span></span>  
  
 <span data-ttu-id="7f03e-138">Предыдущая копия симметричного ключа для экземпляра сервера отчетов, с которым в настоящий момент установлено соединение, перезаписывается восстановленной версией.</span><span class="sxs-lookup"><span data-stu-id="7f03e-138">The previous copy of the symmetric key for the report server instance you are currently connected to is overwritten by the restored version.</span></span> <span data-ttu-id="7f03e-139">После восстановления симметричного ключа необходимо инициализировать все серверы отчетов, использующие базу данных сервера отчетов.</span><span class="sxs-lookup"><span data-stu-id="7f03e-139">After you restore the symmetric key, you must initialize all the report servers that use the report server database.</span></span> <span data-ttu-id="7f03e-140">Дополнительные сведения об инициализации серверов отчетов см. [в разделе Initialize a Report Server &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-initialize-a-report-server.md).</span><span class="sxs-lookup"><span data-stu-id="7f03e-140">For more information about initializing report servers, see [Initialize a Report Server &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-initialize-a-report-server.md).</span></span>  
  
 <span data-ttu-id="7f03e-141">**Изменение**</span><span class="sxs-lookup"><span data-stu-id="7f03e-141">**Change**</span></span>  
 <span data-ttu-id="7f03e-142">Воссоздает симметричный ключ и заново зашифровывает все зашифрованные значения в базе данных сервера отчетов.</span><span class="sxs-lookup"><span data-stu-id="7f03e-142">Recreates the symmetric key and re-encrypts all encrypted values in the report server database.</span></span> <span data-ttu-id="7f03e-143">Прежде чем повторно создавать симметричный ключ, убедитесь, что служба сервера отчетов остановлена.</span><span class="sxs-lookup"><span data-stu-id="7f03e-143">Be sure to stop the Report Server service before recreating the symmetric key.</span></span>  
  
 <span data-ttu-id="7f03e-144">В конфигурации с масштабным развертыванием все копии симметричного ключа заменяются новейшими версиями.</span><span class="sxs-lookup"><span data-stu-id="7f03e-144">In a scale-out deployment, all copies of the symmetric key are replaced with newer versions.</span></span> <span data-ttu-id="7f03e-145">Прежде чем изменить симметричный ключ, заново просмотрите список серверов, присоединенных к конфигурации с масштабным развертыванием, чтобы убедиться в том, что только действительные экземпляры сервера отчетов получают доступ к новому ключу.</span><span class="sxs-lookup"><span data-stu-id="7f03e-145">Before changing the symmetric key, be sure to review the list of servers that are joined to the scale-out deployment to verify that only valid report server instances are given access to the new key.</span></span> <span data-ttu-id="7f03e-146">Серверы, входящие в состав масштабного развертывания, перечислены на странице **Масштабное развертывание** .</span><span class="sxs-lookup"><span data-stu-id="7f03e-146">The servers that are part of a scale-out deployment are listed in the **Scale-out Deployment** page.</span></span> <span data-ttu-id="7f03e-147">Прежде чем приступать к повторному созданию ключа, остановите службу на каждом из серверов отчетов, входящих в развертывание.</span><span class="sxs-lookup"><span data-stu-id="7f03e-147">Stop the service on each report server in the deployment before recreating the key.</span></span>  
  
 <span data-ttu-id="7f03e-148">Обратите внимание на то, что воссоздание симметричного ключа может быть длительным процессом, если имеется много источников данных и подписок.</span><span class="sxs-lookup"><span data-stu-id="7f03e-148">Note that regenerating the symmetric key can be a long-running process if you have many data sources and subscriptions.</span></span>  
  
 <span data-ttu-id="7f03e-149">**Удалить**</span><span class="sxs-lookup"><span data-stu-id="7f03e-149">**Delete**</span></span>  
 <span data-ttu-id="7f03e-150">Удаляет симметричный ключ и все зашифрованное содержимое, включая строки соединения и сохраненные учетные данные.</span><span class="sxs-lookup"><span data-stu-id="7f03e-150">Deletes the symmetric key and all encrypted content, including connection strings and stored credentials.</span></span> <span data-ttu-id="7f03e-151">Удалять симметричный ключ следует только в том случае, если восстановить его невозможно.</span><span class="sxs-lookup"><span data-stu-id="7f03e-151">You should only delete the symmetric key if you cannot restore it.</span></span>  
  
 <span data-ttu-id="7f03e-152">После удаления симметричного ключа необходимо заново ввести недостающие строки соединения, хранимые учетные данные в отчеты и общие источники данных, потерявшие эти значения.</span><span class="sxs-lookup"><span data-stu-id="7f03e-152">Once you delete the symmetric key, you must re-enter the missing connection strings and stored credentials in the reports and shared data sources that no longer have these values.</span></span> <span data-ttu-id="7f03e-153">Следует также обновить все подписки, которые используют модули доставки, хранящие зашифрованные данные.</span><span class="sxs-lookup"><span data-stu-id="7f03e-153">You must also update all subscriptions that use delivery extensions that store encrypted data.</span></span> <span data-ttu-id="7f03e-154">Сюда входят модули доставки в общую папку и любые модули доставки от сторонних разработчиков, использующие зашифрованное значение.</span><span class="sxs-lookup"><span data-stu-id="7f03e-154">This includes the file share delivery extension and any third-party delivery extension that use encrypted value.</span></span>  
  
 <span data-ttu-id="7f03e-155">Автоматизированного способа обновлять эти данные не существует.</span><span class="sxs-lookup"><span data-stu-id="7f03e-155">There is no automated way to update this information.</span></span> <span data-ttu-id="7f03e-156">Необходимо вручную обновить все отчеты, подписки и общие источники данных, которые используют сохраненные учетные данные и строки соединения.</span><span class="sxs-lookup"><span data-stu-id="7f03e-156">Each report, subscription, and shared data source that uses stored credentials and connection strings must be updated one at a time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f03e-157">См. также:</span><span class="sxs-lookup"><span data-stu-id="7f03e-157">See Also</span></span>  
 <span data-ttu-id="7f03e-158">[Диспетчер конфигурации служб Reporting Services разделы справки F1 &#40;служб SSRS в собственном режиме&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="7f03e-158">[Reporting Services Configuration Manager F1 Help Topics &#40;SSRS Native Mode&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="7f03e-159">[Резервное копирование и восстановление ключей шифрования служб Reporting Services](../../reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md) </span><span class="sxs-lookup"><span data-stu-id="7f03e-159">[Back Up and Restore Reporting Services Encryption Keys](../../reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md) </span></span>  
 <span data-ttu-id="7f03e-160">[Удаление и повторное создание ключей шифрования (диспетчер конфигурации служб SSRS)](../../reporting-services/install-windows/ssrs-encryption-keys-delete-and-re-create-encryption-keys.md) </span><span class="sxs-lookup"><span data-stu-id="7f03e-160">[Delete and Re-create Encryption Keys  &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-delete-and-re-create-encryption-keys.md) </span></span>  
 <span data-ttu-id="7f03e-161">[Инициализация сервера отчетов &#40;диспетчер конфигурации служб SSRS&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-initialize-a-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="7f03e-161">[Initialize a Report Server &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-initialize-a-report-server.md) </span></span>  
 [<span data-ttu-id="7f03e-162">Хранение зашифрованных данных сервера отчетов &#40;диспетчер конфигурации служб SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="7f03e-162">Store Encrypted Report Server Data &#40;SSRS Configuration Manager&#41;</span></span>](../../reporting-services/install-windows/ssrs-encryption-keys-store-encrypted-report-server-data.md)  
  
  