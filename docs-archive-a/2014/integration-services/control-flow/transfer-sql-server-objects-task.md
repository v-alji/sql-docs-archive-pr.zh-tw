---
title: 傳送 SQL Server 物件工作 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transfersqlserverobjectstask.f1
helpviewer_keywords:
- Transfer SQL Server Objects task [Integration Services]
ms.assetid: fe86d6e5-e415-406c-88f3-dc3ef71bd5f0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 281acb189e8f4dcfde9dc7ad1d2a74525236d28d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584655"
---
# <a name="transfer-sql-server-objects-task"></a><span data-ttu-id="77bf1-102">傳送 SQL Server 物件工作</span><span class="sxs-lookup"><span data-stu-id="77bf1-102">Transfer SQL Server Objects Task</span></span>
  <span data-ttu-id="77bf1-103">「傳送 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 物件」工作會在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體之間，傳送 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]資料庫中的一個或多個類型物件。</span><span class="sxs-lookup"><span data-stu-id="77bf1-103">The Transfer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Objects task transfers one or more types of objects in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database between instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="77bf1-104">例如，該工作可以複製資料表和預存程序。</span><span class="sxs-lookup"><span data-stu-id="77bf1-104">For example, the task can copy tables and stored procedures.</span></span> <span data-ttu-id="77bf1-105">因用作來源的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本不同，可複製不同類型的物件。</span><span class="sxs-lookup"><span data-stu-id="77bf1-105">Depending on the version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that is used as a source, different types of objects are available to copy.</span></span> <span data-ttu-id="77bf1-106">例如，只有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫包含結構描述和使用者定義彙總。</span><span class="sxs-lookup"><span data-stu-id="77bf1-106">For example, only a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database includes schemas and user-defined aggregates.</span></span>  
  
## <a name="objects-to-transfer"></a><span data-ttu-id="77bf1-107">要傳送的物件</span><span class="sxs-lookup"><span data-stu-id="77bf1-107">Objects to Transfer</span></span>  
 <span data-ttu-id="77bf1-108">可以複製指定資料庫中的伺服器角色、角色和使用者，也可以複製所傳送物件的權限。</span><span class="sxs-lookup"><span data-stu-id="77bf1-108">Server roles, roles, and users from the specified database can be copied, as well as the permissions for the transferred objects.</span></span> <span data-ttu-id="77bf1-109">透過將相關聯的使用者、角色和權限與物件一起複製，可以讓所傳送物件立即可以在目的地伺服器上進行運作。</span><span class="sxs-lookup"><span data-stu-id="77bf1-109">By copying the associated users, roles, and permissions together with the objects, you can make the transferred objects immediately operable on the destination server.</span></span>  
  
 <span data-ttu-id="77bf1-110">下表列出可複製的物件類型。</span><span class="sxs-lookup"><span data-stu-id="77bf1-110">The following table lists the type of objects that can be copied.</span></span>  
  
|<span data-ttu-id="77bf1-111">Object</span><span class="sxs-lookup"><span data-stu-id="77bf1-111">Object</span></span>|  
|------------|  
|<span data-ttu-id="77bf1-112">資料表</span><span class="sxs-lookup"><span data-stu-id="77bf1-112">Tables</span></span>|  
|<span data-ttu-id="77bf1-113">檢視</span><span class="sxs-lookup"><span data-stu-id="77bf1-113">Views</span></span>|  
|<span data-ttu-id="77bf1-114">預存程序</span><span class="sxs-lookup"><span data-stu-id="77bf1-114">Stored Procedures</span></span>|  
|<span data-ttu-id="77bf1-115">使用者定義的函式</span><span class="sxs-lookup"><span data-stu-id="77bf1-115">User-Defined Functions</span></span>|  
|<span data-ttu-id="77bf1-116">Defaults</span><span class="sxs-lookup"><span data-stu-id="77bf1-116">Defaults</span></span>|  
|<span data-ttu-id="77bf1-117">使用者自訂資料類型</span><span class="sxs-lookup"><span data-stu-id="77bf1-117">User-Defined Data Types</span></span>|  
|<span data-ttu-id="77bf1-118">資料分割函數</span><span class="sxs-lookup"><span data-stu-id="77bf1-118">Partition Functions</span></span>|  
|<span data-ttu-id="77bf1-119">資料分割配置</span><span class="sxs-lookup"><span data-stu-id="77bf1-119">Partition Schemes</span></span>|  
|<span data-ttu-id="77bf1-120">結構描述</span><span class="sxs-lookup"><span data-stu-id="77bf1-120">Schemas</span></span>|  
|<span data-ttu-id="77bf1-121">組件</span><span class="sxs-lookup"><span data-stu-id="77bf1-121">Assemblies</span></span>|  
|<span data-ttu-id="77bf1-122">使用者定義彙總</span><span class="sxs-lookup"><span data-stu-id="77bf1-122">User-Defined Aggregates</span></span>|  
|<span data-ttu-id="77bf1-123">使用者定義類型</span><span class="sxs-lookup"><span data-stu-id="77bf1-123">User-Defined Types</span></span>|  
|<span data-ttu-id="77bf1-124">XML 結構描述集合</span><span class="sxs-lookup"><span data-stu-id="77bf1-124">XML Schema Collection</span></span>|  
  
 <span data-ttu-id="77bf1-125">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 之執行個體中建立的使用者定義類型 (UDT) 相依於 Common Language Runtime (CLR) 組件。</span><span class="sxs-lookup"><span data-stu-id="77bf1-125">User-defined types (UDTs) that were created in an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] have dependencies on common language runtime (CLR) assemblies.</span></span> <span data-ttu-id="77bf1-126">如果使用「傳送 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 物件」工作傳送 UDT，您也必須設定該工作以傳送相依物件。</span><span class="sxs-lookup"><span data-stu-id="77bf1-126">If you use the Transfer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Objects task to transfer UDTs, you must also configure the task to transfer dependent objects.</span></span> <span data-ttu-id="77bf1-127">若要傳送相依物件，請將 `IncludeDependentObjects` 屬性設定為 `True`。</span><span class="sxs-lookup"><span data-stu-id="77bf1-127">To transfer dependent objects, set the `IncludeDependentObjects` property to `True`.</span></span>  
  
### <a name="table-options"></a><span data-ttu-id="77bf1-128">資料表選項</span><span class="sxs-lookup"><span data-stu-id="77bf1-128">Table Options</span></span>  
 <span data-ttu-id="77bf1-129">複製資料表時，您可以指出要在複製處理中包含之資料表相關項目的類型。</span><span class="sxs-lookup"><span data-stu-id="77bf1-129">When copying tables, you can indicate the types of table-related items to include in the copy process.</span></span> <span data-ttu-id="77bf1-130">您可以在複製相關資料表時一併複製下列類型的項目：</span><span class="sxs-lookup"><span data-stu-id="77bf1-130">The following types of items can be copied together with the related table:</span></span>  
  
-   <span data-ttu-id="77bf1-131">索引</span><span class="sxs-lookup"><span data-stu-id="77bf1-131">Indexes</span></span>  
  
-   <span data-ttu-id="77bf1-132">觸發程序</span><span class="sxs-lookup"><span data-stu-id="77bf1-132">Triggers</span></span>  
  
-   <span data-ttu-id="77bf1-133">全文檢索索引</span><span class="sxs-lookup"><span data-stu-id="77bf1-133">Full-text indexes</span></span>  
  
-   <span data-ttu-id="77bf1-134">主索引鍵</span><span class="sxs-lookup"><span data-stu-id="77bf1-134">Primary keys</span></span>  
  
-   <span data-ttu-id="77bf1-135">外部索引鍵</span><span class="sxs-lookup"><span data-stu-id="77bf1-135">Foreign keys</span></span>  
  
 <span data-ttu-id="77bf1-136">您還可以指出工作所產生的指令碼是否為 Unicode 格式。</span><span class="sxs-lookup"><span data-stu-id="77bf1-136">You can also indicate whether the script that the task generates is in Unicode format.</span></span>  
  
## <a name="destination-options"></a><span data-ttu-id="77bf1-137">目的地選項</span><span class="sxs-lookup"><span data-stu-id="77bf1-137">Destination Options</span></span>  
 <span data-ttu-id="77bf1-138">您可以設定「傳送 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 物件」工作在傳送中包含結構描述名稱、資料、所傳送物件的擴充屬性和相依物件。</span><span class="sxs-lookup"><span data-stu-id="77bf1-138">You can configure the Transfer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Objects task to include schema names, data, extended properties of transferred objects, and dependent objects in the transfer.</span></span> <span data-ttu-id="77bf1-139">如果複製資料，則它可以取代或附加現有資料。</span><span class="sxs-lookup"><span data-stu-id="77bf1-139">If data is copied, it can replace or append existing data.</span></span>  
  
 <span data-ttu-id="77bf1-140">部分選項只適用於 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="77bf1-140">Some options apply only to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="77bf1-141">例如，僅 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 支援結構描述。</span><span class="sxs-lookup"><span data-stu-id="77bf1-141">For example, only [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supports schemas.</span></span>  
  
## <a name="security-options"></a><span data-ttu-id="77bf1-142">安全性選項</span><span class="sxs-lookup"><span data-stu-id="77bf1-142">Security Options</span></span>  
 <span data-ttu-id="77bf1-143">「傳送 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 物件」工作可以包含來源的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫層級使用者和角色、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入，以及所傳送物件的權限。</span><span class="sxs-lookup"><span data-stu-id="77bf1-143">The Transfer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Objects task can include [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database-level users and roles from the source, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] logins, and the permissions for transferred objects.</span></span> <span data-ttu-id="77bf1-144">例如，傳送可以包含所傳送資料表的權限。</span><span class="sxs-lookup"><span data-stu-id="77bf1-144">For example, the transfer can include the permissions on the transferred tables.</span></span>  
  
## <a name="transfer-objects-between-instances-of-sql-server"></a><span data-ttu-id="77bf1-145">在 SQL Server 的執行個體之間傳送物件</span><span class="sxs-lookup"><span data-stu-id="77bf1-145">Transfer Objects Between Instances of SQL Server</span></span>  
 <span data-ttu-id="77bf1-146">「傳送 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 物件」工作可支援 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的來源和目的地。</span><span class="sxs-lookup"><span data-stu-id="77bf1-146">The Transfer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Objects task supports a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] source and destination.</span></span>  
  
## <a name="events"></a><span data-ttu-id="77bf1-147">事件</span><span class="sxs-lookup"><span data-stu-id="77bf1-147">Events</span></span>  
 <span data-ttu-id="77bf1-148">該工作會引發報告已傳送物件的資訊事件，並在覆寫物件時引發警告事件。</span><span class="sxs-lookup"><span data-stu-id="77bf1-148">The task raises an information event that reports the object transferred and a warning event when an object is overwritten.</span></span> <span data-ttu-id="77bf1-149">還會為動作 (例如，截斷資料庫資料表) 引發資訊事件。</span><span class="sxs-lookup"><span data-stu-id="77bf1-149">An information event is also raised for actions such as the truncation of database tables.</span></span>  
  
 <span data-ttu-id="77bf1-150">「傳送 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 物件」工作並不報告物件傳送的累加進度，它只報告 0% 和 100 % 完成。</span><span class="sxs-lookup"><span data-stu-id="77bf1-150">The Transfer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Objects task does not report incremental progress of the object transfer; it reports only 0% and 100 % completion.</span></span>  
  
## <a name="execution-value"></a><span data-ttu-id="77bf1-151">執行值</span><span class="sxs-lookup"><span data-stu-id="77bf1-151">Execution Value</span></span>  
 <span data-ttu-id="77bf1-152">工作之 `ExecutionValue` 屬性中儲存的執行值會傳回已傳送的物件數目。</span><span class="sxs-lookup"><span data-stu-id="77bf1-152">The execution value, stored in the `ExecutionValue` property of the task, returns the number of objects transferred.</span></span> <span data-ttu-id="77bf1-153">透過將使用者自訂變數指派給「傳送 SQL Server 物件」工作的 `ExecValueVariable` 屬性，可將與物件傳送相關的資訊用於封裝中的其他物件。</span><span class="sxs-lookup"><span data-stu-id="77bf1-153">By assigning a user-defined variable to the `ExecValueVariable` property of the Transfer SQL Server Objects task, information about the object transfer can be made available to other objects in the package.</span></span> <span data-ttu-id="77bf1-154">如需詳細資訊，請參閱 [Integration Services &#40;SSIS&#41; 變數](../integration-services-ssis-variables.md)和[在封裝中使用變數](../use-variables-in-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="77bf1-154">For more information, see [Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md) and [Use Variables in Packages](../use-variables-in-packages.md).</span></span>  
  
## <a name="log-entries"></a><span data-ttu-id="77bf1-155">記錄項目</span><span class="sxs-lookup"><span data-stu-id="77bf1-155">Log Entries</span></span>  
 <span data-ttu-id="77bf1-156">「傳送 SQL Server 物件」工作包含下列自訂記錄項目：</span><span class="sxs-lookup"><span data-stu-id="77bf1-156">The Transfer SQL Server Objects task includes the following custom log entries:</span></span>  
  
-   <span data-ttu-id="77bf1-157">TransferSqlServerObjectsTaskStartTransferringObjects：此記錄項目報告傳送已開始。</span><span class="sxs-lookup"><span data-stu-id="77bf1-157">TransferSqlServerObjectsTaskStartTransferringObjects   This log entry reports that the transfer has started.</span></span> <span data-ttu-id="77bf1-158">記錄項目會包含開始時間。</span><span class="sxs-lookup"><span data-stu-id="77bf1-158">The log entry includes the start time.</span></span>  
  
-   <span data-ttu-id="77bf1-159">TransferSqlServerObjectsTaskFinishedTransferringObjects：此記錄項目報告傳送已完成。</span><span class="sxs-lookup"><span data-stu-id="77bf1-159">TransferSqlServerObjectsTaskFinishedTransferringObjects    This log entry reports that the transfer has completed.</span></span> <span data-ttu-id="77bf1-160">記錄項目會包含結束時間。</span><span class="sxs-lookup"><span data-stu-id="77bf1-160">The log entry includes the end time.</span></span>  
  
 <span data-ttu-id="77bf1-161">此外，`OnInformation` 事件的記錄項目會報告已為傳送選取之物件類型的物件數目、已傳送的物件數目，以及動作 (例如，隨資料表一同傳送資料時截斷資料表)。</span><span class="sxs-lookup"><span data-stu-id="77bf1-161">In addition, a log entry for an `OnInformation` event reports the number of objects of the object types that have been selected for transfer, the number of objects that were transferred, and actions such as the truncation of tables when data is transferred with tables.</span></span> <span data-ttu-id="77bf1-162">為在目的地上覆寫的每個物件寫入 `OnWarning` 事件的記錄項目。</span><span class="sxs-lookup"><span data-stu-id="77bf1-162">A log entry for the `OnWarning` event is written for each object on the destination that is overwritten.</span></span>  
  
## <a name="security-and-permissions"></a><span data-ttu-id="77bf1-163">安全性和權限</span><span class="sxs-lookup"><span data-stu-id="77bf1-163">Security and Permissions</span></span>  
 <span data-ttu-id="77bf1-164">使用者必須具有在來源伺服器上瀏覽物件的權限，且必須具有在目的地伺服器上卸除和建立物件的權限，此外，使用者還必須能夠存取指定的資料庫和資料庫物件。</span><span class="sxs-lookup"><span data-stu-id="77bf1-164">The user must have permission to browse objects on the source server, and must have permission to drop and create objects on the destination server; moreover, the user must have access to the specified database and database objects.</span></span>  
  
## <a name="configuration-of-the-transfer-sql-server-objects-task"></a><span data-ttu-id="77bf1-165">設定傳送 SQL Server 物件工作</span><span class="sxs-lookup"><span data-stu-id="77bf1-165">Configuration of the Transfer SQL Server Objects Task</span></span>  
 <span data-ttu-id="77bf1-166">可以設定「傳送 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 物件」工作傳送所有物件、同一類型的所有物件，或只傳送同一類型的指定物件。</span><span class="sxs-lookup"><span data-stu-id="77bf1-166">The Transfer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Objects task can be configured to transfer all objects, all objects of a type, or only specified objects of a type.</span></span> <span data-ttu-id="77bf1-167">例如，您可以選擇只複製 AdventureWorks 資料庫中已選取的資料表。</span><span class="sxs-lookup"><span data-stu-id="77bf1-167">For example, you can choose to copy only selected tables in the AdventureWorks database.</span></span>  
  
 <span data-ttu-id="77bf1-168">如果「傳送 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 物件」工作傳送資料表，則您可指定要隨該資料表一同複製之資料表相關物件的類型。</span><span class="sxs-lookup"><span data-stu-id="77bf1-168">If the Transfer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Objects task transfers tables, you can specify the types of table-related objects to copy with the tables.</span></span> <span data-ttu-id="77bf1-169">例如，您可以指定隨資料表一同複製的主索引鍵。</span><span class="sxs-lookup"><span data-stu-id="77bf1-169">For example, you can specify that primary keys are copied with tables.</span></span>  
  
 <span data-ttu-id="77bf1-170">若要進一步加強所傳送物件的功能，您可以設定「傳送 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 物件」工作在傳送中包含結構描述名稱、資料、所傳送物件的擴充屬性和相依物件。</span><span class="sxs-lookup"><span data-stu-id="77bf1-170">To further enhance functionality of transferred objects, you can configure the Transfer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Objects task to include schema names, data, extended properties of transferred objects, and dependent objects in the transfer.</span></span> <span data-ttu-id="77bf1-171">複製資料時，您可以指定是取代還是附加現有資料。</span><span class="sxs-lookup"><span data-stu-id="77bf1-171">When copying data, you can specify whether to replace or append existing data.</span></span>  
  
 <span data-ttu-id="77bf1-172">在執行階段，「傳送 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 物件」工作會使用兩個 SMO 連線管理員，連接到來源和目的地伺服器。</span><span class="sxs-lookup"><span data-stu-id="77bf1-172">At run time, the Transfer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Objects task connects to the source and destination servers by using two SMO connection managers.</span></span> <span data-ttu-id="77bf1-173">SMO 連接管理員會在「傳送 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 物件」工作以外另行設定，然後在「傳送 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 物件」工作中參考。</span><span class="sxs-lookup"><span data-stu-id="77bf1-173">The SMO connection managers are configured separately from the Transfer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Objects task, and then referenced in the Transfer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Objects task.</span></span> <span data-ttu-id="77bf1-174">存取伺服器時，SMO 連接管理員會指定要使用的伺服器和驗證模式。</span><span class="sxs-lookup"><span data-stu-id="77bf1-174">The SMO connection managers specify the server and the authentication mode to use when accessing the server.</span></span> <span data-ttu-id="77bf1-175">如需詳細資訊，請參閱 [SMO Connection Manager](../connection-manager/smo-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="77bf1-175">For more information, see [SMO Connection Manager](../connection-manager/smo-connection-manager.md).</span></span>  
  
 <span data-ttu-id="77bf1-176">您可以透過 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="77bf1-176">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="77bf1-177">如需有關可以在「 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師」中設定之屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="77bf1-177">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="77bf1-178">傳送 SQL Server 物件工作編輯器 &#40;一般頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="77bf1-178">Transfer SQL Server Objects Task Editor &#40;General Page&#41;</span></span>](../general-page-of-integration-services-designers-options.md)  
  
-   [<span data-ttu-id="77bf1-179">傳送 SQL Server 物件工作編輯器 &#40;物件頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="77bf1-179">Transfer SQL Server Objects Task Editor &#40;Objects Page&#41;</span></span>](../transfer-sql-server-objects-task-editor-objects-page.md)  
  
-   [<span data-ttu-id="77bf1-180">運算式頁面</span><span class="sxs-lookup"><span data-stu-id="77bf1-180">Expressions Page</span></span>](../expressions/expressions-page.md)  
  
 <span data-ttu-id="77bf1-181">如需有關如何在「 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師」中設定這些屬性的詳細資訊，請按下列主題：</span><span class="sxs-lookup"><span data-stu-id="77bf1-181">For more information about how to set these properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="77bf1-182">設定工作或容器的屬性</span><span class="sxs-lookup"><span data-stu-id="77bf1-182">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="programmatic-configuration-of-the-transfer-sql-server-objects-task"></a><span data-ttu-id="77bf1-183">以程式設計方式設定傳送 SQL Server 物件工作</span><span class="sxs-lookup"><span data-stu-id="77bf1-183">Programmatic Configuration of the Transfer SQL Server Objects Task</span></span>  
 <span data-ttu-id="77bf1-184">如需有關以程式設計方式設定這些屬性的詳細資訊，請按下列主題：</span><span class="sxs-lookup"><span data-stu-id="77bf1-184">For more information about programmatically setting these properties, click the following topic:</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.TransferSqlServerObjectsTask.TransferSqlServerObjectsTask>  
  
  
