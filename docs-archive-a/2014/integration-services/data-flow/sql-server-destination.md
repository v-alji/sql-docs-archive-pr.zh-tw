---
title: SQL Server 目的地 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.sqlserverdest.f1
helpviewer_keywords:
- SQL Server destination
- loading data
- destinations [Integration Services], SQL Server
- inserting data
- bulk load [Integration Services]
ms.assetid: a0227cd8-6944-4547-87e8-7b2507e26442
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fcd65007e1e6af36386cb2ceba1f7242305b81a5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688074"
---
# <a name="sql-server-destination"></a><span data-ttu-id="c0780-102">SQL Server 目的地</span><span class="sxs-lookup"><span data-stu-id="c0780-102">SQL Server Destination</span></span>
  <span data-ttu-id="c0780-103">SQL Server 目的地會連接到本機 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫，並大量載入資料到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料表和檢視中。</span><span class="sxs-lookup"><span data-stu-id="c0780-103">The SQL Server destination connects to a local [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database and bulk loads data into [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tables and views.</span></span> <span data-ttu-id="c0780-104">如果封裝會存取遠端伺服器上的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫，您就無法在這種封裝中使用 SQL Server 目的地。</span><span class="sxs-lookup"><span data-stu-id="c0780-104">You cannot use the SQL Server destination in packages that access a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database on a remote server.</span></span> <span data-ttu-id="c0780-105">反之，這種封裝應該使用 OLE DB 目的地。</span><span class="sxs-lookup"><span data-stu-id="c0780-105">Instead, the packages should use the OLE DB destination.</span></span> <span data-ttu-id="c0780-106">如需詳細資訊，請參閱 [OLE DB Destination](ole-db-destination.md)。</span><span class="sxs-lookup"><span data-stu-id="c0780-106">For more information, see [OLE DB Destination](ole-db-destination.md).</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="c0780-107">權限</span><span class="sxs-lookup"><span data-stu-id="c0780-107">Permissions</span></span>  
 <span data-ttu-id="c0780-108">使用者必須擁有「建立全域物件」權限，才能執行包含 SQL Server 目的地的封裝。</span><span class="sxs-lookup"><span data-stu-id="c0780-108">Users who execute packages that include the SQL Server destination require the "Create global objects" permission.</span></span> <span data-ttu-id="c0780-109">您可以使用「本機安全性原則」工具 (從 [系統管理工具]  功能表中開啟) 將此權限授與使用者。</span><span class="sxs-lookup"><span data-stu-id="c0780-109">You can grant this permission to users by using the Local Security Policy tool opened from the **Administrative Tools** menu.</span></span> <span data-ttu-id="c0780-110">如果您在執行使用 SQL Server 目的地的封裝時收到錯誤訊息，請確定執行該封裝的帳戶是否擁有「建立全域物件」權限。</span><span class="sxs-lookup"><span data-stu-id="c0780-110">If you receive an error message when executing a package that uses the SQL Server destination, make sure that the account running the package has the "Create global objects" permission.</span></span>  
  
## <a name="bulk-inserts"></a><span data-ttu-id="c0780-111">大量插入</span><span class="sxs-lookup"><span data-stu-id="c0780-111">Bulk Inserts</span></span>  
 <span data-ttu-id="c0780-112">如果您嘗試使用 SQL Server 目的地將資料大量載入遠端 SQL Server 資料庫，可能會看到類似下面這樣的錯誤訊息：「有 OLE DB 記錄可用」。</span><span class="sxs-lookup"><span data-stu-id="c0780-112">If you attempt to use the SQL Server destination to bulk load data into a remote SQL Server database, you may see an error message similar to the following: "An OLE DB record is available.</span></span> <span data-ttu-id="c0780-113">來源："Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client" Hresult: 0x80040E14 描述: 「無法大量載入，因為無法開啟 SSIS 檔案對應物件 'Global\DTSQLIMPORT」。</span><span class="sxs-lookup"><span data-stu-id="c0780-113">Source: "Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client" Hresult: 0x80040E14 Description: "Could not bulk load because SSIS file mapping object 'Global\DTSQLIMPORT ' could not be opened.</span></span> <span data-ttu-id="c0780-114">作業系統錯誤碼 2 (系統找不到指定的檔案)。</span><span class="sxs-lookup"><span data-stu-id="c0780-114">Operating system error code 2 (The system cannot find the file specified.).</span></span> <span data-ttu-id="c0780-115">請確定是透過 Windows 安全性存取本機伺服器」。</span><span class="sxs-lookup"><span data-stu-id="c0780-115">Make sure you are accessing a local server via Windows security.""</span></span>  
  
 <span data-ttu-id="c0780-116">與「大量插入」工作一樣，SQL Server 目的地也可以對 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 進行相同的高速資料插入；不過，透過使用 SQL Server 目的地，在資料載入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]之前，封裝可以將轉換套用到資料行資料。</span><span class="sxs-lookup"><span data-stu-id="c0780-116">The SQL Server destination offers the same high-speed insertion of data into [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that the Bulk Insert task provides; however, by using the SQL Server destination, a package can apply transformations to column data before the data is loaded into [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="c0780-117">若要將資料載入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，您應該考慮使用 SQL Server 目的地，而不是 OLE DB 目的地。</span><span class="sxs-lookup"><span data-stu-id="c0780-117">For loading data into [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you should consider using the SQL Server destination instead of the OLE DB destination.</span></span>  
  
### <a name="bulk-insert-options"></a><span data-ttu-id="c0780-118">大量插入選項</span><span class="sxs-lookup"><span data-stu-id="c0780-118">Bulk Insert Options</span></span>  
 <span data-ttu-id="c0780-119">如果 SQL Server 目的地使用快速載入資料存取模式，則您可以指定下列快速載入選項：</span><span class="sxs-lookup"><span data-stu-id="c0780-119">If the SQL Server destination uses a fast-load data access mode, you can specify the following fast load options:</span></span>  
  
-   <span data-ttu-id="c0780-120">保留匯入資料檔中的識別值或使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]指派的唯一值。</span><span class="sxs-lookup"><span data-stu-id="c0780-120">Retain identity values from the imported data file, or use unique values assigned by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="c0780-121">大量載入作業期間保留 Null 值。</span><span class="sxs-lookup"><span data-stu-id="c0780-121">Retain null values during the bulk load operation.</span></span>  
  
-   <span data-ttu-id="c0780-122">大量匯入作業期間驗證目標資料表或檢視的條件約束。</span><span class="sxs-lookup"><span data-stu-id="c0780-122">Verify constraints on the target table or view during the bulk import operation.</span></span>  
  
-   <span data-ttu-id="c0780-123">大量載入作業期間需要資料表層級鎖定。</span><span class="sxs-lookup"><span data-stu-id="c0780-123">Acquire a table-level lock for the duration of the bulk load operation.</span></span>  
  
-   <span data-ttu-id="c0780-124">大量載入作業期間執行目的地資料表上定義的插入觸發器。</span><span class="sxs-lookup"><span data-stu-id="c0780-124">Execute insert triggers defined on the destination table during the bulk load operation.</span></span>  
  
-   <span data-ttu-id="c0780-125">在大量插入作業期間，指定輸入中要載入的第一個資料列編號。</span><span class="sxs-lookup"><span data-stu-id="c0780-125">Specify the number of the first row in the input to load during the bulk insert operation.</span></span>  
  
-   <span data-ttu-id="c0780-126">大量插入作業期間指定要載入之輸入的最後一個資料列編號。</span><span class="sxs-lookup"><span data-stu-id="c0780-126">Specify the number of the last row in the input to load during the bulk insert operation.</span></span>  
  
-   <span data-ttu-id="c0780-127">指定在取消大量載入作業之前，允許發生錯誤的最多數目。</span><span class="sxs-lookup"><span data-stu-id="c0780-127">Specify the maximum number of errors allowed before the bulk load operation is canceled.</span></span> <span data-ttu-id="c0780-128">每個無法匯入的資料列都將算為一個錯誤。</span><span class="sxs-lookup"><span data-stu-id="c0780-128">Each row that cannot be imported is counted as one error.</span></span>  
  
-   <span data-ttu-id="c0780-129">指定輸入中包含已排序資料的資料行。</span><span class="sxs-lookup"><span data-stu-id="c0780-129">Specify the columns in the input that contain sorted data.</span></span>  
  
 <span data-ttu-id="c0780-130">如需大量載入選項的詳細資訊，請參閱 [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="c0780-130">For more information about bulk load options, see [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql).</span></span>  
  
#### <a name="performance-improvements"></a><span data-ttu-id="c0780-131">效能改進</span><span class="sxs-lookup"><span data-stu-id="c0780-131">Performance Improvements</span></span>  
 <span data-ttu-id="c0780-132">若要提升大量插入以及大量插入作業期間存取資料表資料的效能，您應該變更預設選項，如下：</span><span class="sxs-lookup"><span data-stu-id="c0780-132">To improve the performance of a bulk insert and the access to table data during the bulk insert operation, you should change the default options as follows:</span></span>  
  
-   <span data-ttu-id="c0780-133">大量匯入作業期間不驗證目標資料表或檢視的條件約束。</span><span class="sxs-lookup"><span data-stu-id="c0780-133">Do not verify constraints on the target table or view during the bulk import operation.</span></span>  
  
-   <span data-ttu-id="c0780-134">大量載入作業期間不執行目的地資料表上定義的插入觸發器。</span><span class="sxs-lookup"><span data-stu-id="c0780-134">Do not execute insert triggers defined on the destination table during the bulk load operation.</span></span>  
  
-   <span data-ttu-id="c0780-135">不要將鎖定套用到資料表。</span><span class="sxs-lookup"><span data-stu-id="c0780-135">Do not apply a lock to the table.</span></span> <span data-ttu-id="c0780-136">這樣，在大量插入作業期間，其他使用者和應用程式依然可以使用該資料表。</span><span class="sxs-lookup"><span data-stu-id="c0780-136">That way, the table remains available to other users and applications during the bulk insert operation.</span></span>  
  
## <a name="configuration-of-the-sql-server-destination"></a><span data-ttu-id="c0780-137">SQL Server 目的地的組態</span><span class="sxs-lookup"><span data-stu-id="c0780-137">Configuration of the SQL Server Destination</span></span>  
 <span data-ttu-id="c0780-138">您可以利用下列方式設定 SQL Server 目的地：</span><span class="sxs-lookup"><span data-stu-id="c0780-138">You can configure the SQL Server destination in the following ways:</span></span>  
  
-   <span data-ttu-id="c0780-139">指定要大量載入資料的資料表或檢視。</span><span class="sxs-lookup"><span data-stu-id="c0780-139">Specify the table or view into which to bulk load the data.</span></span>  
  
-   <span data-ttu-id="c0780-140">透過指定一些選項 (例如是否要檢查條件約束的選項) 來自訂大量載入作業。</span><span class="sxs-lookup"><span data-stu-id="c0780-140">Customize the bulk load operation by specifying options such as whether to check constraints.</span></span>  
  
-   <span data-ttu-id="c0780-141">指定所有資料列是以一個批次認可，或設定每個批次所認可的最大資料列數。</span><span class="sxs-lookup"><span data-stu-id="c0780-141">Specify whether all rows commit in one batch or set the maximum number of rows to commit as a batch.</span></span>  
  
-   <span data-ttu-id="c0780-142">指定大量載入作業的逾時。</span><span class="sxs-lookup"><span data-stu-id="c0780-142">Specify a time-out for the bulk load operation.</span></span>  
  
 <span data-ttu-id="c0780-143">此目的地使用 OLE DB 連接管理員連接到資料來源，且連接管理員會指定要使用的 OLE DB 提供者。</span><span class="sxs-lookup"><span data-stu-id="c0780-143">This destination uses an OLE DB connection manager to connect to a data source, and the connection manager specifies the OLE DB provider to use.</span></span> <span data-ttu-id="c0780-144">如需相關資訊，請參閱 [OLE DB Connection Manager](../connection-manager/ole-db-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="c0780-144">For more information, see [OLE DB Connection Manager](../connection-manager/ole-db-connection-manager.md).</span></span>  
  
 <span data-ttu-id="c0780-145">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 專案還會提供資料來源物件，您可以從中建立 OLE DB 連接管理員。</span><span class="sxs-lookup"><span data-stu-id="c0780-145">An [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project also provides the data source object from which you can create an OLE DB connection manager.</span></span> <span data-ttu-id="c0780-146">這樣就可以向 SQL Server 目的地提供資料來源和資料來源檢視。</span><span class="sxs-lookup"><span data-stu-id="c0780-146">This makes data sources and data source views available to the SQL Server destination.</span></span>  
  
 <span data-ttu-id="c0780-147">SQL Server 目的地有一個輸入。</span><span class="sxs-lookup"><span data-stu-id="c0780-147">The SQL Server destination has one input.</span></span> <span data-ttu-id="c0780-148">它不支援錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="c0780-148">It does not support an error output.</span></span>  
  
 <span data-ttu-id="c0780-149">您可以透過 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="c0780-149">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="c0780-150">如需可以在 [SQL Server 目的地編輯器]\*\*\*\* 對話方塊中設定之屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="c0780-150">For more information about the properties that you can set in the **SQL Server Destination Editor** dialog box, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="c0780-151">SQL 目的地編輯器 &#40;連線管理員頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="c0780-151">SQL Destination Editor &#40;Connection Manager Page&#41;</span></span>](../sql-destination-editor-connection-manager-page.md)  
  
-   [<span data-ttu-id="c0780-152">SQL 目的地編輯器 &#40;對應頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="c0780-152">SQL Destination Editor &#40;Mappings Page&#41;</span></span>](../sql-destination-editor-mappings-page.md)  
  
-   [<span data-ttu-id="c0780-153">SQL 目的地編輯器 &#40;進階頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="c0780-153">SQL Destination Editor &#40;Advanced Page&#41;</span></span>](../sql-destination-editor-advanced-page.md)  
  
 <span data-ttu-id="c0780-154">**[進階編輯器]** 對話方塊會反映能以程式設計的方式設定之屬性。</span><span class="sxs-lookup"><span data-stu-id="c0780-154">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="c0780-155">如需有關可以在 **[進階編輯器]** 對話方塊中或以程式設計方式設定之屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="c0780-155">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="c0780-156">Common Properties</span><span class="sxs-lookup"><span data-stu-id="c0780-156">Common Properties</span></span>](../common-properties.md)  
  
-   [<span data-ttu-id="c0780-157">SQL Server 目的地自訂屬性</span><span class="sxs-lookup"><span data-stu-id="c0780-157">SQL Server Destination Custom Properties</span></span>](sql-server-destination-custom-properties.md)  
  
 <span data-ttu-id="c0780-158">如需有關如何設定屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="c0780-158">For more information about how to set properties, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="c0780-159">使用 SQL Server 目的地來大量載入資料</span><span class="sxs-lookup"><span data-stu-id="c0780-159">Bulk Load Data by Using the SQL Server Destination</span></span>](sql-server-destination.md)  
  
-   [<span data-ttu-id="c0780-160">設定資料流程元件的屬性</span><span class="sxs-lookup"><span data-stu-id="c0780-160">Set the Properties of a Data Flow Component</span></span>](set-the-properties-of-a-data-flow-component.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="c0780-161">相關工作</span><span class="sxs-lookup"><span data-stu-id="c0780-161">Related Tasks</span></span>  
  
-   [<span data-ttu-id="c0780-162">使用 SQL Server 目的地來大量載入資料</span><span class="sxs-lookup"><span data-stu-id="c0780-162">Bulk Load Data by Using the SQL Server Destination</span></span>](sql-server-destination.md)  
  
-   [<span data-ttu-id="c0780-163">設定資料流程元件的屬性</span><span class="sxs-lookup"><span data-stu-id="c0780-163">Set the Properties of a Data Flow Component</span></span>](set-the-properties-of-a-data-flow-component.md)  
  
## <a name="related-content"></a><span data-ttu-id="c0780-164">相關內容</span><span class="sxs-lookup"><span data-stu-id="c0780-164">Related Content</span></span>  
  
-   <span data-ttu-id="c0780-165">support.microsoft.com 上的技術文件： [您可能會在啟用 UAC 的系統上收到「無法準備 SSIS 大量插入來進行資料插入」錯誤](https://go.microsoft.com/fwlink/?LinkId=199482)。</span><span class="sxs-lookup"><span data-stu-id="c0780-165">Technical article, [You may get "Unable to prepare the SSIS bulk insert for data insertion" error on UAC enabled systems](https://go.microsoft.com/fwlink/?LinkId=199482), on support.microsoft.com.</span></span>  
  
-   <span data-ttu-id="c0780-166">msdn.microsoft.com 上的技術文章： [資料載入效能指南](https://go.microsoft.com/fwlink/?LinkId=233700)。</span><span class="sxs-lookup"><span data-stu-id="c0780-166">Technical article, [The Data Loading Performance Guide](https://go.microsoft.com/fwlink/?LinkId=233700), on msdn.microsoft.com.</span></span>  
  
-   <span data-ttu-id="c0780-167">simple-talk.com 上的技術文件： [Using SQL Server Integration Services to Bulk Load Data](https://go.microsoft.com/fwlink/?LinkId=233701)(使用 SQL Server Integration Services 大量載入資料)。</span><span class="sxs-lookup"><span data-stu-id="c0780-167">Technical article, [Using SQL Server Integration Services to Bulk Load Data](https://go.microsoft.com/fwlink/?LinkId=233701), on simple-talk.com.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0780-168">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c0780-168">See Also</span></span>  
 [<span data-ttu-id="c0780-169">資料流程</span><span class="sxs-lookup"><span data-stu-id="c0780-169">Data Flow</span></span>](data-flow.md)  
  
  
