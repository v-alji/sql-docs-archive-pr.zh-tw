---
title: '[傳送資料庫工作編輯器 (資料庫] 頁面) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transferdatabasetask.database.f1
helpviewer_keywords:
- Transfer Database Task Editor
ms.assetid: ccdb74d0-4bea-420c-a726-2e0eb8957e0a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: df4452e28a32463a7825e9c64cfd053f98c53ee8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686447"
---
# <a name="transfer-database-task-editor-databases-page"></a><span data-ttu-id="83e06-102">傳送資料庫工作編輯器 (資料庫頁面)</span><span class="sxs-lookup"><span data-stu-id="83e06-102">Transfer Database Task Editor (Databases Page)</span></span>
  <span data-ttu-id="83e06-103">使用 [傳送資料庫工作編輯器] 對話方塊的 [資料庫] 頁面，即可指定傳送資料庫工作中所含之來源和目的地資料庫的屬性。</span><span class="sxs-lookup"><span data-stu-id="83e06-103">Use the **Databases** page of the **Transfer Database Task Editor** dialog box to specify properties for the source and destination databases involved in the Transfer Database task.</span></span> <span data-ttu-id="83e06-104">傳送資料庫工作會在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的兩個執行個體間，複製或移動 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]資料庫。</span><span class="sxs-lookup"><span data-stu-id="83e06-104">The Transfer Database task copies or moves a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database between two instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="83e06-105">這項工作也可用來在同一部伺服器內複製資料庫。</span><span class="sxs-lookup"><span data-stu-id="83e06-105">This task can also be used to copy a database within the same server.</span></span> <span data-ttu-id="83e06-106">如需這項工作的詳細資訊，請參閱 [傳送資料庫工作](control-flow/transfer-database-task.md)。</span><span class="sxs-lookup"><span data-stu-id="83e06-106">For more information about this task, see [Transfer Database Task](control-flow/transfer-database-task.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="83e06-107">選項。</span><span class="sxs-lookup"><span data-stu-id="83e06-107">Options</span></span>  
 <span data-ttu-id="83e06-108">**SourceConnection**</span><span class="sxs-lookup"><span data-stu-id="83e06-108">**SourceConnection**</span></span>  
 <span data-ttu-id="83e06-109">在清單中選取一個 SMO 連線管理員，或按一下 **\<New connection...>** ，以建立新的來源伺服器連線。</span><span class="sxs-lookup"><span data-stu-id="83e06-109">Select a SMO connection manager in the list, or click **\<New connection...>** to create a new connection to the source server.</span></span>  
  
 <span data-ttu-id="83e06-110">**DestinationConnection**</span><span class="sxs-lookup"><span data-stu-id="83e06-110">**DestinationConnection**</span></span>  
 <span data-ttu-id="83e06-111">在清單中選取一個 SMO 連線管理員，或按一下 **\<New connection...>** ，以建立新的目的地伺服器連線。</span><span class="sxs-lookup"><span data-stu-id="83e06-111">Select a SMO connection manager in the list, or click **\<New connection...>** to create a new connection to the destination server.</span></span>  
  
 <span data-ttu-id="83e06-112">**DestinationDatabaseName**</span><span class="sxs-lookup"><span data-stu-id="83e06-112">**DestinationDatabaseName**</span></span>  
 <span data-ttu-id="83e06-113">指定目的地伺服器上之 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="83e06-113">Specify the name of the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database on the destination server.</span></span>  
  
 <span data-ttu-id="83e06-114">若要使用來源資料庫名稱來自動擴展此欄位，請先指定 **SourceConnection** 和 **SourceDatabaseName** 。</span><span class="sxs-lookup"><span data-stu-id="83e06-114">To automatically populate this field with the source database name, specify the **SourceConnection** and **SourceDatabaseName** first.</span></span>  
  
 <span data-ttu-id="83e06-115">若要重新命名目的地伺服器上的資料庫，請在此欄位中輸入新名稱。</span><span class="sxs-lookup"><span data-stu-id="83e06-115">To rename the database on the destination server, type the new name in this field.</span></span>  
  
 <span data-ttu-id="83e06-116">**DestinationDatabaseFiles**</span><span class="sxs-lookup"><span data-stu-id="83e06-116">**DestinationDatabaseFiles**</span></span>  
 <span data-ttu-id="83e06-117">指定目的地伺服器上之資料庫檔案的名稱和位置。</span><span class="sxs-lookup"><span data-stu-id="83e06-117">Specifies the names and locations of the database files on the destination server.</span></span>  
  
 <span data-ttu-id="83e06-118">若要使用來源資料庫檔案的名稱和位置來自動擴展此欄位，請先指定 **SourceConnection**、 **SourceDatabaseName**和 **SourceDatabaseFiles** 。</span><span class="sxs-lookup"><span data-stu-id="83e06-118">To automatically populate this field with the source database file names and locations, specify the **SourceConnection**, **SourceDatabaseName**, and **SourceDatabaseFiles** first.</span></span>  
  
 <span data-ttu-id="83e06-119">若要重新命名資料庫檔案，或要指定目的地伺服器上的新位置，請使用來源資料庫的資訊來擴展此欄位，然後按一下瀏覽按鈕。</span><span class="sxs-lookup"><span data-stu-id="83e06-119">To rename the database files or to specify the new locations on the destination server, populate this field with the source database information, and then click the browse button.</span></span> <span data-ttu-id="83e06-120">在 [目的地資料庫檔案]  對話方塊中，編輯 [目的地檔案]  、[目的資料夾]  或 [網路檔案共用]  。</span><span class="sxs-lookup"><span data-stu-id="83e06-120">In the **Destination database files** dialog box, edit the **Destination File**, **Destination Folder**, or **Network File Share**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="83e06-121">如果您是使用瀏覽按鈕找到資料庫檔案，就可以使用本機磁碟機代號來輸入檔案位置：例如 c:\\。</span><span class="sxs-lookup"><span data-stu-id="83e06-121">If you locate the database files by using the browse button, the file location is entered using the local drive notation: for example, c:\\.</span></span> <span data-ttu-id="83e06-122">您必須以網路共用標記來取代此檔案位置，其中包含電腦名稱和共用名稱。</span><span class="sxs-lookup"><span data-stu-id="83e06-122">You must replace this with the network share notation, including the computer name and share name.</span></span> <span data-ttu-id="83e06-123">如果使用預設管理共用，您就必須使用 $ 標記，並具有管理權限存取該共用。</span><span class="sxs-lookup"><span data-stu-id="83e06-123">If the default administrative share is used, you must use the $ notation, and have administrative access to the share.</span></span>  
  
 <span data-ttu-id="83e06-124">**DestinationOverwrite**</span><span class="sxs-lookup"><span data-stu-id="83e06-124">**DestinationOverwrite**</span></span>  
 <span data-ttu-id="83e06-125">指定是否可以覆寫目的地伺服器上的資料庫。</span><span class="sxs-lookup"><span data-stu-id="83e06-125">Specify whether the database on the destination server can be overwritten.</span></span>  
  
 <span data-ttu-id="83e06-126">此屬性具有下表所列的選項：</span><span class="sxs-lookup"><span data-stu-id="83e06-126">This property has the options listed in the following table:</span></span>  
  
|<span data-ttu-id="83e06-127">值</span><span class="sxs-lookup"><span data-stu-id="83e06-127">Value</span></span>|<span data-ttu-id="83e06-128">描述</span><span class="sxs-lookup"><span data-stu-id="83e06-128">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="83e06-129">**True**</span><span class="sxs-lookup"><span data-stu-id="83e06-129">**True**</span></span>|<span data-ttu-id="83e06-130">覆寫目的地伺服器資料庫。</span><span class="sxs-lookup"><span data-stu-id="83e06-130">Overwrite destination server database.</span></span>|  
|<span data-ttu-id="83e06-131">**False**</span><span class="sxs-lookup"><span data-stu-id="83e06-131">**False**</span></span>|<span data-ttu-id="83e06-132">請勿覆寫目的地伺服器資料庫。</span><span class="sxs-lookup"><span data-stu-id="83e06-132">Do not overwrite destination server database.</span></span>|  
  
> [!CAUTION]  
>  <span data-ttu-id="83e06-133">如果您為 **DestinationOverwrite** 指定了 **True**，此舉可能會造成資料遺失，且會覆寫目的地伺服器資料庫中的資料。</span><span class="sxs-lookup"><span data-stu-id="83e06-133">The data in the destination server database will be overwritten if you specify **True** for **DestinationOverwrite**, which may result in data loss.</span></span> <span data-ttu-id="83e06-134">為了避免此情形發生，在執行傳送資料庫工作之前，請先將目的地伺服器資料庫備份至其他位置。</span><span class="sxs-lookup"><span data-stu-id="83e06-134">To avoid this, back up the destination server database to another location before executing the Transfer Database task.</span></span>  
  
 <span data-ttu-id="83e06-135">**動作**</span><span class="sxs-lookup"><span data-stu-id="83e06-135">**Action**</span></span>  
 <span data-ttu-id="83e06-136">指定工作會將資料庫 [複製]  或 [移動]  至目的地伺服器。</span><span class="sxs-lookup"><span data-stu-id="83e06-136">Specify whether the task will **Copy** or **Move** the database to the destination server.</span></span>  
  
 <span data-ttu-id="83e06-137">**方法**</span><span class="sxs-lookup"><span data-stu-id="83e06-137">**Method**</span></span>  
 <span data-ttu-id="83e06-138">指定當來源伺服器上的資料庫處於線上或離線模式時，是否會執行工作。</span><span class="sxs-lookup"><span data-stu-id="83e06-138">Specify whether the task will be executed while the database on the source server is in online or offline mode.</span></span>  
  
 <span data-ttu-id="83e06-139">若要使用離線模式來傳送資料庫，執行封裝的使用者就必須是 **系統管理員** 固定伺服器角色的成員。</span><span class="sxs-lookup"><span data-stu-id="83e06-139">To transfer a database using offline mode, the user that runs the package must be a member of the **sysadmin** fixed server role.</span></span>  
  
 <span data-ttu-id="83e06-140">若要使用線上模式來傳送資料庫，執行封裝的使用者就必須是 **系統管理員** 固定伺服器角色的成員，或是選取之資料庫的資料庫擁有者 (**dbo**)。</span><span class="sxs-lookup"><span data-stu-id="83e06-140">To transfer a database using the online mode, the user that runs the package must be a member of the **sysadmin** fixed server role, or the database owner (**dbo**) of the selected database.</span></span>  
  
 <span data-ttu-id="83e06-141">**SourceDatabaseName**</span><span class="sxs-lookup"><span data-stu-id="83e06-141">**SourceDatabaseName**</span></span>  
 <span data-ttu-id="83e06-142">選取要複製或移動之資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="83e06-142">Select the name of the database to be copied or moved.</span></span>  
  
 <span data-ttu-id="83e06-143">**SourceDatabaseFiles**</span><span class="sxs-lookup"><span data-stu-id="83e06-143">**SourceDatabaseFiles**</span></span>  
 <span data-ttu-id="83e06-144">按一下瀏覽按鈕，即可選取資料庫檔案。</span><span class="sxs-lookup"><span data-stu-id="83e06-144">Click the browse button to select the database files.</span></span>  
  
 <span data-ttu-id="83e06-145">**ReattachSourceDatabase**</span><span class="sxs-lookup"><span data-stu-id="83e06-145">**ReattachSourceDatabase**</span></span>  
 <span data-ttu-id="83e06-146">指定失敗發生時，工作是否會嘗試重新附加來源資料庫。</span><span class="sxs-lookup"><span data-stu-id="83e06-146">Specify whether the task will attempt to reattach the source database if a failure occurs.</span></span>  
  
 <span data-ttu-id="83e06-147">此屬性具有下表所列的選項：</span><span class="sxs-lookup"><span data-stu-id="83e06-147">This property has the options listed in the following table:</span></span>  
  
|<span data-ttu-id="83e06-148">值</span><span class="sxs-lookup"><span data-stu-id="83e06-148">Value</span></span>|<span data-ttu-id="83e06-149">描述</span><span class="sxs-lookup"><span data-stu-id="83e06-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="83e06-150">**True**</span><span class="sxs-lookup"><span data-stu-id="83e06-150">**True**</span></span>|<span data-ttu-id="83e06-151">重新附加來源資料庫。</span><span class="sxs-lookup"><span data-stu-id="83e06-151">Reattach source database.</span></span>|  
|<span data-ttu-id="83e06-152">**False**</span><span class="sxs-lookup"><span data-stu-id="83e06-152">**False**</span></span>|<span data-ttu-id="83e06-153">請勿重新附加來源資料庫。</span><span class="sxs-lookup"><span data-stu-id="83e06-153">Do not reattach source database.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="83e06-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="83e06-154">See Also</span></span>  
 <span data-ttu-id="83e06-155">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="83e06-155">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="83e06-156">[Integration Services 工作](control-flow/integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="83e06-156">[Integration Services Tasks](control-flow/integration-services-tasks.md) </span></span>  
 <span data-ttu-id="83e06-157">[[傳送資料庫工作編輯器] &#40;一般頁面&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="83e06-157">[Transfer Database Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="83e06-158">[運算式頁面](expressions/expressions-page.md) </span><span class="sxs-lookup"><span data-stu-id="83e06-158">[Expressions Page](expressions/expressions-page.md) </span></span>  
 [<span data-ttu-id="83e06-159">SMO 連線管理員</span><span class="sxs-lookup"><span data-stu-id="83e06-159">SMO Connection Manager</span></span>](connection-manager/smo-connection-manager.md)  
  
  
