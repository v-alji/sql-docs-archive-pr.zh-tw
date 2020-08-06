---
title: 大量插入工作 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.bulkinserttask.f1
helpviewer_keywords:
- Bulk Insert task
- copying data [Integration Services]
ms.assetid: c5166156-6b4c-4369-81ed-27c4ce7040ae
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8f0b306af7a067e4dbd46bc8df7ca689770a3ce2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592803"
---
# <a name="bulk-insert-task"></a><span data-ttu-id="a9720-102">大量插入工作</span><span class="sxs-lookup"><span data-stu-id="a9720-102">Bulk Insert Task</span></span>
  <span data-ttu-id="a9720-103">「大量插入」工作提供有效的方式，將大量資料複製到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料表或檢視。</span><span class="sxs-lookup"><span data-stu-id="a9720-103">The Bulk Insert task provides an efficient way to copy large amounts of data into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table or view.</span></span> <span data-ttu-id="a9720-104">例如，假設您的公司將百萬個資料列的產品清單儲存在大型電腦系統上，但公司的電子商務系統是使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 擴展網頁。</span><span class="sxs-lookup"><span data-stu-id="a9720-104">For example, suppose your company stores its million-row product list on a mainframe system, but the company's e-commerce system uses [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to populate Web pages.</span></span> <span data-ttu-id="a9720-105">您必須在晚上以大型電腦的主產品清單更新 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 產品資料表。</span><span class="sxs-lookup"><span data-stu-id="a9720-105">You must update the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] product table nightly with the master product list from the mainframe.</span></span> <span data-ttu-id="a9720-106">若要更新資料表，請以 Tab 分隔的格式儲存產品清單，並使用「大量插入」工作將資料直接複製到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料表中。</span><span class="sxs-lookup"><span data-stu-id="a9720-106">To update the table, you save the product list in a tab-delimited format and use the Bulk Insert task to copy the data directly into the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span>  
  
 <span data-ttu-id="a9720-107">為了確保高速資料複製，從來源檔案將資料搬移到資料表或檢視時，無法執行資料的轉換。</span><span class="sxs-lookup"><span data-stu-id="a9720-107">To ensure high-speed data copying, transformations cannot be performed on the data while it is moving from the source file to the table or view.</span></span>  
  
## <a name="usage-considerations"></a><span data-ttu-id="a9720-108">使用狀況的考量</span><span class="sxs-lookup"><span data-stu-id="a9720-108">Usage Considerations</span></span>  
 <span data-ttu-id="a9720-109">使用「大量插入」工作之前，請考慮下列事項：</span><span class="sxs-lookup"><span data-stu-id="a9720-109">Before you use the Bulk Insert task, consider the following:</span></span>  
  
-   <span data-ttu-id="a9720-110">「大量插入」工作只能從文字檔將資料傳送到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料表或檢視。</span><span class="sxs-lookup"><span data-stu-id="a9720-110">The Bulk Insert task can transfer data only from a text file into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table or view.</span></span> <span data-ttu-id="a9720-111">若要使用「大量插入」工作傳輸來自其他資料庫管理系統 (DBMS) 的資料，您必須從來源將資料匯出到文字檔，然後從文字檔將資料匯入到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料表或檢視。</span><span class="sxs-lookup"><span data-stu-id="a9720-111">To use the Bulk Insert task to transfer data from other database management systems (DBMSs), you must export the data from the source to a text file and then import the data from the text file into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table or view.</span></span>  
  
-   <span data-ttu-id="a9720-112">目的地必須是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫中的資料表或檢視。</span><span class="sxs-lookup"><span data-stu-id="a9720-112">The destination must be a table or view in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span> <span data-ttu-id="a9720-113">若目的地資料表或檢視已經包含資料，則「大量插入」工作執行時，便會將新資料附加到現有資料中。</span><span class="sxs-lookup"><span data-stu-id="a9720-113">If the destination table or view already contains data, the new data is appended to the existing data when the Bulk Insert task runs.</span></span> <span data-ttu-id="a9720-114">如果您要取代資料，請在執行「大量插入」工作之前，先執行會執行 DELETE 或 TRUNCATE 陳述式的執行 SQL 工作。</span><span class="sxs-lookup"><span data-stu-id="a9720-114">If you want to replace the data, run an Execute SQL task that runs a DELETE or TRUNCATE statement before you run the Bulk Insert task.</span></span> <span data-ttu-id="a9720-115">如需相關資訊，請參閱 [Execute SQL Task](execute-sql-task.md)。</span><span class="sxs-lookup"><span data-stu-id="a9720-115">For more information, see [Execute SQL Task](execute-sql-task.md).</span></span>  
  
-   <span data-ttu-id="a9720-116">您可以在「大量插入」工作物件中使用格式檔案。</span><span class="sxs-lookup"><span data-stu-id="a9720-116">You can use a format file in the Bulk Insert task object.</span></span> <span data-ttu-id="a9720-117">如果您已經有 **bcp** 公用程式所建立的格式檔，就可以在「大量插入」工作中指定它的路徑。</span><span class="sxs-lookup"><span data-stu-id="a9720-117">If you have a format file that was created by the **bcp** utility, you can specify its path in the Bulk Insert task.</span></span> <span data-ttu-id="a9720-118">「大量插入」工作支援 XML 和非 XML 格式檔案。</span><span class="sxs-lookup"><span data-stu-id="a9720-118">The Bulk Insert task supports both XML and nonXML format files.</span></span> <span data-ttu-id="a9720-119">如需格式檔案的詳細資訊，請參閱[匯入或匯出資料的格式檔案 &#40;SQL Server&#41;](../../relational-databases/import-export/format-files-for-importing-or-exporting-data-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="a9720-119">For more information about format files, see [Format Files for Importing or Exporting Data &#40;SQL Server&#41;](../../relational-databases/import-export/format-files-for-importing-or-exporting-data-sql-server.md).</span></span>  
  
-   <span data-ttu-id="a9720-120">只有系統管理員 (sysadmin) 固定伺服器角色的成員才能執行包含「大量插入」工作的封裝。</span><span class="sxs-lookup"><span data-stu-id="a9720-120">Only members of the sysadmin fixed server role can run a package that contains a Bulk Insert task.</span></span>  
  
## <a name="bulk-insert-task-with-transactions"></a><span data-ttu-id="a9720-121">使用交易的大量插入工作</span><span class="sxs-lookup"><span data-stu-id="a9720-121">Bulk Insert Task with Transactions</span></span>  
 <span data-ttu-id="a9720-122">若未設定批次大小，則會將整個大量複製作業視為一項交易。</span><span class="sxs-lookup"><span data-stu-id="a9720-122">If a batch size is not set, the complete bulk copy operation is treated as one transaction.</span></span> <span data-ttu-id="a9720-123">批次大小 **0** 表示會將資料插入一個批次中。</span><span class="sxs-lookup"><span data-stu-id="a9720-123">A batch size of **0** indicates that the data is inserted in one batch.</span></span> <span data-ttu-id="a9720-124">若有設定批次大小，則每一個批次即代表批次完成時的一筆認可交易。</span><span class="sxs-lookup"><span data-stu-id="a9720-124">If a batch size is set, each batch represents a transaction that is committed when the batch finishes running.</span></span>  
  
 <span data-ttu-id="a9720-125">「大量插入」工作的行為與交易相關，端視工作是否聯結封裝交易而定。</span><span class="sxs-lookup"><span data-stu-id="a9720-125">The behavior of the Bulk Insert task, as it relates to transactions, depends on whether the task joins the package transaction.</span></span> <span data-ttu-id="a9720-126">若「大量插入」工作並未聯結封裝交易，在嘗試下一個批次之前，會將每一個無錯誤的 (Error-free) 批次視為一個單位進行認可。</span><span class="sxs-lookup"><span data-stu-id="a9720-126">If the Bulk Insert task does not join the package transaction, each error-free batch is committed as a unit before the next batch is tried.</span></span> <span data-ttu-id="a9720-127">如果「大量插入」工作與封裝交易聯結，那麼工作結束時，無錯誤批次仍會保留在交易中。</span><span class="sxs-lookup"><span data-stu-id="a9720-127">If the Bulk Insert task joins the package transaction, error-free batches remain in the transaction at the conclusion of the task.</span></span> <span data-ttu-id="a9720-128">這些批次是取決於封裝的認可或復原作業。</span><span class="sxs-lookup"><span data-stu-id="a9720-128">These batches are subject to the commit or rollback operation of the package.</span></span>  
  
 <span data-ttu-id="a9720-129">「大量插入」工作的錯誤不會自動復原已成功載入的批次；同樣地，如果工作成功，批次並不會自動認可。</span><span class="sxs-lookup"><span data-stu-id="a9720-129">A failure in the Bulk Insert task does not automatically roll back successfully loaded batches; similarly, if the task succeeds, batches are not automatically committed.</span></span> <span data-ttu-id="a9720-130">認可和復原作業只會發生於回應封裝以及工作流程屬性設定的時候。</span><span class="sxs-lookup"><span data-stu-id="a9720-130">Commit and rollback operations occur only in response to package and workflow property settings.</span></span>  
  
## <a name="source-and-destination"></a><span data-ttu-id="a9720-131">來源和目的地</span><span class="sxs-lookup"><span data-stu-id="a9720-131">Source and Destination</span></span>  
 <span data-ttu-id="a9720-132">當您指定文字來源檔的位置時，請考慮下列各項：</span><span class="sxs-lookup"><span data-stu-id="a9720-132">When you specify the location of the text source file, consider the following:</span></span>  
  
-   <span data-ttu-id="a9720-133">伺服器必須有權限，才能同時存取檔案和目的地資料庫。</span><span class="sxs-lookup"><span data-stu-id="a9720-133">The server must have permission to access both the file and the destination database.</span></span>  
  
-   <span data-ttu-id="a9720-134">伺服器會執行「大量插入」工作。</span><span class="sxs-lookup"><span data-stu-id="a9720-134">The server runs the Bulk Insert task.</span></span> <span data-ttu-id="a9720-135">因此，該工作使用的任何格式檔案都必須位於伺服器上。</span><span class="sxs-lookup"><span data-stu-id="a9720-135">Therefore, any format file that the task uses must be located on the server.</span></span>  
  
-   <span data-ttu-id="a9720-136">「大量插入」工作載入的來源檔所在伺服器，可以和要插入資料的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫所在的伺服器相同，或位於遠端伺服器上。</span><span class="sxs-lookup"><span data-stu-id="a9720-136">The source file that the Bulk Insert task loads can be on the same server as the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database into which data is inserted, or on a remote server.</span></span> <span data-ttu-id="a9720-137">如果檔案位於遠端伺服器上，則必須在路徑中指定使用「通用命名慣例」(UNC) 名稱的檔名。</span><span class="sxs-lookup"><span data-stu-id="a9720-137">If the file is on a remote server, you must specify the file name using the Universal Naming Convention (UNC) name in the path.</span></span>  
  
## <a name="performance-optimization"></a><span data-ttu-id="a9720-138">效能最佳化</span><span class="sxs-lookup"><span data-stu-id="a9720-138">Performance Optimization</span></span>  
 <span data-ttu-id="a9720-139">若要最佳化效能，請考慮下列各項：</span><span class="sxs-lookup"><span data-stu-id="a9720-139">To optimize performance, consider the following:</span></span>  
  
-   <span data-ttu-id="a9720-140">如果文字檔與要插入資料的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫位於同一台電腦上，則由於資料並非在網路上移動，因此複製作業進行的速度更快。</span><span class="sxs-lookup"><span data-stu-id="a9720-140">If the text file is located on the same computer as the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database into which data is inserted, the copy operation occurs at an even faster rate because the data is not moved over the network.</span></span>  
  
-   <span data-ttu-id="a9720-141">「大量插入」工作不會記錄導致錯誤的資料列。</span><span class="sxs-lookup"><span data-stu-id="a9720-141">The Bulk Insert task does not log error-causing rows.</span></span> <span data-ttu-id="a9720-142">如果您必須擷取這項資訊，請使用資料流程元件的錯誤輸出擷取例外狀況檔案中造成錯誤的資料列。</span><span class="sxs-lookup"><span data-stu-id="a9720-142">If you must capture this information, use the error outputs of data flow components to capture error-causing rows in an exception file.</span></span>  
  
## <a name="custom-log-entries-available-on-the-bulk-insert-task"></a><span data-ttu-id="a9720-143">大量插入工作上可用的自訂記錄項目</span><span class="sxs-lookup"><span data-stu-id="a9720-143">Custom Log Entries Available on the Bulk Insert Task</span></span>  
 <span data-ttu-id="a9720-144">下表列出「大量插入」工作的自訂記錄項目。</span><span class="sxs-lookup"><span data-stu-id="a9720-144">The following table lists the custom log entries for the Bulk Insert task.</span></span> <span data-ttu-id="a9720-145">如需詳細資訊，請參閱 [Integration Services &#40;SSIS&#41; 記錄](../performance/integration-services-ssis-logging.md)和[自訂訊息以進行記錄](../custom-messages-for-logging.md)。</span><span class="sxs-lookup"><span data-stu-id="a9720-145">For more information, see [Integration Services &#40;SSIS&#41; Logging](../performance/integration-services-ssis-logging.md) and [Custom Messages for Logging](../custom-messages-for-logging.md).</span></span>  
  
|<span data-ttu-id="a9720-146">記錄項目</span><span class="sxs-lookup"><span data-stu-id="a9720-146">Log entry</span></span>|<span data-ttu-id="a9720-147">描述</span><span class="sxs-lookup"><span data-stu-id="a9720-147">Description</span></span>|  
|---------------|-----------------|  
|`BulkInsertTaskBegin`|<span data-ttu-id="a9720-148">指出大量插入已經開始。</span><span class="sxs-lookup"><span data-stu-id="a9720-148">Indicates that the bulk insert began.</span></span>|  
|`BulkInsertTaskEnd`|<span data-ttu-id="a9720-149">指出大量插入已經完成。</span><span class="sxs-lookup"><span data-stu-id="a9720-149">Indicates that the bulk insert finished.</span></span>|  
|`BulkInsertTaskInfos`|<span data-ttu-id="a9720-150">提供有關工作的描述性資訊。</span><span class="sxs-lookup"><span data-stu-id="a9720-150">Provides descriptive information about the task.</span></span>|  
  
## <a name="bulk-insert-task-configuration"></a><span data-ttu-id="a9720-151">大量插入工作組態</span><span class="sxs-lookup"><span data-stu-id="a9720-151">Bulk Insert Task Configuration</span></span>  
 <span data-ttu-id="a9720-152">您可以利用下列方式設定「大量插入」工作：</span><span class="sxs-lookup"><span data-stu-id="a9720-152">You can configure the Bulk Insert task in the following ways:</span></span>  
  
-   <span data-ttu-id="a9720-153">指定讓 OLE DB 連接管理員連接到目的地 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫，以及要插入資料的資料表或檢視。</span><span class="sxs-lookup"><span data-stu-id="a9720-153">Specify the OLE DB connection manager to connect to the destination [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database and the table or view into which data is inserted.</span></span> <span data-ttu-id="a9720-154">「大量插入」工作只支援用於目的地資料庫的 OLE DB 連接。</span><span class="sxs-lookup"><span data-stu-id="a9720-154">The Bulk Insert task supports only OLE DB connections for the destination database.</span></span>  
  
-   <span data-ttu-id="a9720-155">指定「檔案」或「一般檔案」連接管理員存取來源檔案。</span><span class="sxs-lookup"><span data-stu-id="a9720-155">Specify the File or Flat File connection manager to access the source file.</span></span> <span data-ttu-id="a9720-156">「大量插入」工作僅針對來源檔案的位置，使用連接管理員。</span><span class="sxs-lookup"><span data-stu-id="a9720-156">The Bulk Insert task uses the connection manager only for the location of the source file.</span></span> <span data-ttu-id="a9720-157">此工作會忽略您在連接管理員編輯器中選取的其他選項。</span><span class="sxs-lookup"><span data-stu-id="a9720-157">The task ignores other options that you select in the connection manager editor.</span></span>  
  
-   <span data-ttu-id="a9720-158">以格式檔案或定義來源資料之資料行和資料列的分隔符號，定義「大量插入」工作所使用的格式。</span><span class="sxs-lookup"><span data-stu-id="a9720-158">Define the format that is used by the Bulk Insert task, either by using a format file or by defining the column and row delimiters of the source data.</span></span> <span data-ttu-id="a9720-159">如果使用格式檔案，請指定讓「檔案」連接管理員存取該格式檔案。</span><span class="sxs-lookup"><span data-stu-id="a9720-159">If using a format file, specify the File connection manager to access the format file.</span></span>  
  
-   <span data-ttu-id="a9720-160">指定當工作插入資料時，要在目的地資料表或檢視上執行的動作。</span><span class="sxs-lookup"><span data-stu-id="a9720-160">Specify actions to perform on the destination table or view when the task inserts the data.</span></span> <span data-ttu-id="a9720-161">這些選項包括是否檢查條件約束、啟用識別插入、保留 Null、引發觸發程序，或鎖定資料表。</span><span class="sxs-lookup"><span data-stu-id="a9720-161">The options include whether to check constraints, enable identity inserts, keep nulls, fire triggers, or lock the table.</span></span>  
  
-   <span data-ttu-id="a9720-162">提供要插入的資料批次相關資訊，例如批次大小、要插入的檔案中的第一個和最後一個資料列、在工作停止插入資料列之前容許發生的插入錯誤數目，以及將進行排序的資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="a9720-162">Provide information about the batch of data to insert, such as the batch size, the first and last row from the file to insert, the number of insert errors that can occur before the task stops inserting rows, and the names of the columns that will be sorted.</span></span>  
  
 <span data-ttu-id="a9720-163">如果「大量插入」工作使用「一般檔案」連接管理員存取來源檔案，則該工作不會使用「一般檔案」連接管理員中指定的格式。</span><span class="sxs-lookup"><span data-stu-id="a9720-163">If the Bulk Insert task uses a Flat File connection manager to access the source file, the task does not use the format specified in the Flat File connection manager.</span></span> <span data-ttu-id="a9720-164">而「大量插入」工作會使用格式檔案中指定的格式，或工作之 RowDelimiter 和 ColumnDelimiter 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="a9720-164">Instead, the Bulk Insert task uses either the format specified in a format file, or the values of the RowDelimiter and ColumnDelimiter properties of the task.</span></span>  
  
 <span data-ttu-id="a9720-165">您可以透過 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="a9720-165">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="a9720-166">如需有關可以在「 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師」中設定之屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="a9720-166">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="a9720-167">大量插入工作編輯器 &#40;一般頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="a9720-167">Bulk Insert Task Editor &#40;General Page&#41;</span></span>](../general-page-of-integration-services-designers-options.md)  
  
-   [<span data-ttu-id="a9720-168">大量插入工作編輯器 &#40;連接頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="a9720-168">Bulk Insert Task Editor &#40;Connection Page&#41;</span></span>](../bulk-insert-task-editor-connection-page.md)  
  
-   [<span data-ttu-id="a9720-169">大量插入工作編輯器 &#40;選項頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="a9720-169">Bulk Insert Task Editor &#40;Options Page&#41;</span></span>](../bulk-insert-task-editor-options-page.md)  
  
-   [<span data-ttu-id="a9720-170">運算式頁面</span><span class="sxs-lookup"><span data-stu-id="a9720-170">Expressions Page</span></span>](../expressions/expressions-page.md)  
  
 <span data-ttu-id="a9720-171">如需有關如何在「 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師」中設定這些屬性的詳細資訊，請按下列主題：</span><span class="sxs-lookup"><span data-stu-id="a9720-171">For more information about how to setthese properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="a9720-172">設定工作或容器的屬性</span><span class="sxs-lookup"><span data-stu-id="a9720-172">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
### <a name="programmatic-configuration-of-the-bulk-insert-task"></a><span data-ttu-id="a9720-173">大量插入工作的程式設計組態</span><span class="sxs-lookup"><span data-stu-id="a9720-173">Programmatic Configuration of the Bulk Insert Task</span></span>  
 <span data-ttu-id="a9720-174">如需有關以程式設計方式設定這些屬性的詳細資訊，請按下列主題：</span><span class="sxs-lookup"><span data-stu-id="a9720-174">For more information about programmatically setting these properties, click the following topic:</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.BulkInsertTask.BulkInsertTask>  
  
## <a name="related-tasks"></a><span data-ttu-id="a9720-175">相關工作</span><span class="sxs-lookup"><span data-stu-id="a9720-175">Related Tasks</span></span>  
 [<span data-ttu-id="a9720-176">設定工作或容器的屬性</span><span class="sxs-lookup"><span data-stu-id="a9720-176">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="related-content"></a><span data-ttu-id="a9720-177">相關內容</span><span class="sxs-lookup"><span data-stu-id="a9720-177">Related Content</span></span>  
  
-   <span data-ttu-id="a9720-178">support.microsoft.com 上的技術文件： [您可能會在啟用 UAC 的系統上收到「無法準備 SSIS 大量插入來進行資料插入」錯誤](https://go.microsoft.com/fwlink/?LinkId=233693)。</span><span class="sxs-lookup"><span data-stu-id="a9720-178">Technical article, [You may get "Unable to prepare the SSIS bulk insert for data insertion" error on UAC enabled systems](https://go.microsoft.com/fwlink/?LinkId=233693), on support.microsoft.com.</span></span>  
  
-   <span data-ttu-id="a9720-179">msdn.microsoft.com 上的技術文章： [資料載入效能指南](https://go.microsoft.com/fwlink/?LinkId=233700)。</span><span class="sxs-lookup"><span data-stu-id="a9720-179">Technical article, [The Data Loading Performance Guide](https://go.microsoft.com/fwlink/?LinkId=233700), on msdn.microsoft.com.</span></span>  
  
-   <span data-ttu-id="a9720-180">simple-talk.com 上的技術文件： [Using SQL Server Integration Services to Bulk Load Data](https://go.microsoft.com/fwlink/?LinkId=233701)(使用 SQL Server Integration Services 大量載入資料)。</span><span class="sxs-lookup"><span data-stu-id="a9720-180">Technical article, [Using SQL Server Integration Services to Bulk Load Data](https://go.microsoft.com/fwlink/?LinkId=233701), on simple-talk.com.</span></span>  
  
  
