---
title: OLE DB 目的地編輯器 (連線管理員頁面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.oledbdestadapter.connection.f1
helpviewer_keywords:
- OLE DB Destination Editor
ms.assetid: ae2200c6-8ba0-49b7-b01a-53425b84d2ed
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7217380d664ac5d20cf1ba7b437924ee3460841b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592761"
---
# <a name="ole-db-destination-editor-connection-manager-page"></a><span data-ttu-id="3a619-102">OLE DB 目的地編輯器 (連接管理員頁面)</span><span class="sxs-lookup"><span data-stu-id="3a619-102">OLE DB Destination Editor (Connection Manager Page)</span></span>
  <span data-ttu-id="3a619-103">使用 **[OLE DB 目的地編輯器]** 對話方塊的 **[連接管理員]** 頁面來選取目的地的 OLE DB 連接。</span><span class="sxs-lookup"><span data-stu-id="3a619-103">Use the **Connection Manager** page of the **OLE DB Destination Editor** dialog box to select the OLE DB connection for the destination.</span></span> <span data-ttu-id="3a619-104">這個頁面也可以讓您從資料庫中選取資料表或檢視。</span><span class="sxs-lookup"><span data-stu-id="3a619-104">This page also lets you select a table or view from the database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3a619-105">[ `CommandTimeout` **OLE DB 目的地編輯器**] 中無法使用 OLE DB 目的地的屬性，但可使用**進階編輯器**來設定。</span><span class="sxs-lookup"><span data-stu-id="3a619-105">The `CommandTimeout` property of the OLE DB destination is not available in the **OLE DB Destination Editor**, but can be set by using the **Advanced Editor**.</span></span> <span data-ttu-id="3a619-106">此外， **[進階編輯器]** 中只會有特定的快速載入選項。</span><span class="sxs-lookup"><span data-stu-id="3a619-106">In addition, certain fast load options are available only in the **Advanced Editor**.</span></span> <span data-ttu-id="3a619-107">如需有關這些屬性的詳細資訊，請參閱＜ [OLE DB Custom Properties](data-flow/ole-db-custom-properties.md)＞的＜OLE DB 目的地＞一節。</span><span class="sxs-lookup"><span data-stu-id="3a619-107">For more information on these properties, see the OLE DB Destination section of [OLE DB Custom Properties](data-flow/ole-db-custom-properties.md).</span></span>  
  
 <span data-ttu-id="3a619-108">若要深入了解 OLE DB 目的地，請參閱＜ [OLE DB Destination](data-flow/ole-db-destination.md)＞。</span><span class="sxs-lookup"><span data-stu-id="3a619-108">To learn more about the OLE DB destination, see [OLE DB Destination](data-flow/ole-db-destination.md).</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="3a619-109">靜態選項</span><span class="sxs-lookup"><span data-stu-id="3a619-109">Static Options</span></span>  
 <span data-ttu-id="3a619-110">**[無快取]**</span><span class="sxs-lookup"><span data-stu-id="3a619-110">**OLE DB connection manager**</span></span>  
 <span data-ttu-id="3a619-111">從清單中選取現有的連線管理員，或按一下 [新增]  來建立新的連線。</span><span class="sxs-lookup"><span data-stu-id="3a619-111">Select an existing connection manager from the list, or create a new connection by clicking **New**.</span></span>  
  
 <span data-ttu-id="3a619-112">**新增**</span><span class="sxs-lookup"><span data-stu-id="3a619-112">**New**</span></span>  
 <span data-ttu-id="3a619-113">使用 [設定 OLE DB 連線管理員]  對話方塊建立新的連線管理員。</span><span class="sxs-lookup"><span data-stu-id="3a619-113">Create a new connection manager by using the **Configure OLE DB Connection Manager** dialog box.</span></span>  
  
 <span data-ttu-id="3a619-114">**資料存取模式**</span><span class="sxs-lookup"><span data-stu-id="3a619-114">**Data access mode**</span></span>  
 <span data-ttu-id="3a619-115">指定將資料載入目的地的方法。</span><span class="sxs-lookup"><span data-stu-id="3a619-115">Specify the method for loading data into the destination.</span></span> <span data-ttu-id="3a619-116">請注意，雙位元組字集 (DBCS) 資料需要使用其中一種快速載入選項。</span><span class="sxs-lookup"><span data-stu-id="3a619-116">Loading double-byte character set (DBCS) data requires use of one of the fast load options.</span></span> <span data-ttu-id="3a619-117">如需有關快速載入資料存取模式 (已針對大量插入進行過最佳化) 的詳細資訊，請參閱＜ [OLE DB Destination](data-flow/ole-db-destination.md)＞。</span><span class="sxs-lookup"><span data-stu-id="3a619-117">For more information about the fast load data access modes, which are optimized for bulk inserts, see [OLE DB Destination](data-flow/ole-db-destination.md).</span></span>  
  
|<span data-ttu-id="3a619-118">選項</span><span class="sxs-lookup"><span data-stu-id="3a619-118">Option</span></span>|<span data-ttu-id="3a619-119">描述</span><span class="sxs-lookup"><span data-stu-id="3a619-119">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="3a619-120">資料表或檢視</span><span class="sxs-lookup"><span data-stu-id="3a619-120">Table or view</span></span>|<span data-ttu-id="3a619-121">將資料載入 OLE DB 目的地中的資料表或檢視。</span><span class="sxs-lookup"><span data-stu-id="3a619-121">Load data into a table or view in the OLE DB destination.</span></span>|  
|<span data-ttu-id="3a619-122">資料表或檢視 - 快速載入</span><span class="sxs-lookup"><span data-stu-id="3a619-122">Table or view - fast load</span></span>|<span data-ttu-id="3a619-123">將資料載入 OLE DB 目的地中的資料表或檢視，並使用快速載入選項。</span><span class="sxs-lookup"><span data-stu-id="3a619-123">Load data into a table or view in the OLE DB destination and use the fast load option.</span></span> <span data-ttu-id="3a619-124">如需有關快速載入資料存取模式 (已針對大量插入進行過最佳化) 的詳細資訊，請參閱＜ [OLE DB Destination](data-flow/ole-db-destination.md)＞。</span><span class="sxs-lookup"><span data-stu-id="3a619-124">For more information about the fast load data access modes, which are optimized for bulk inserts, see [OLE DB Destination](data-flow/ole-db-destination.md).</span></span>|  
|<span data-ttu-id="3a619-125">資料表名稱或檢視名稱變數</span><span class="sxs-lookup"><span data-stu-id="3a619-125">Table name or view name variable</span></span>|<span data-ttu-id="3a619-126">請在變數中指定資料表或檢視名稱。</span><span class="sxs-lookup"><span data-stu-id="3a619-126">Specify the table or view name in a variable.</span></span><br /><br /> <span data-ttu-id="3a619-127">**相關資訊**：[在套件中使用變數](../../2014/integration-services/use-variables-in-packages.md)</span><span class="sxs-lookup"><span data-stu-id="3a619-127">**Related information**: [Use Variables in Packages](../../2014/integration-services/use-variables-in-packages.md)</span></span>|  
|<span data-ttu-id="3a619-128">資料表名稱或檢視名稱變數 - 快速載入</span><span class="sxs-lookup"><span data-stu-id="3a619-128">Table name or view name variable - fast load</span></span>|<span data-ttu-id="3a619-129">在變數中指定資料表或檢視名稱，並使用快速載入選項來載入資料。</span><span class="sxs-lookup"><span data-stu-id="3a619-129">Specify the table or view name in a variable, and use the fast load option to load the data.</span></span> <span data-ttu-id="3a619-130">如需有關快速載入資料存取模式 (已針對大量插入進行過最佳化) 的詳細資訊，請參閱＜ [OLE DB Destination](data-flow/ole-db-destination.md)＞。</span><span class="sxs-lookup"><span data-stu-id="3a619-130">For more information about the fast load data access modes, which are optimized for bulk inserts, see [OLE DB Destination](data-flow/ole-db-destination.md).</span></span>|  
|<span data-ttu-id="3a619-131">SQL (命令)</span><span class="sxs-lookup"><span data-stu-id="3a619-131">SQL command</span></span>|<span data-ttu-id="3a619-132">使用 SQL 查詢，將資料載入到 OLE DB 目的地。</span><span class="sxs-lookup"><span data-stu-id="3a619-132">Load data into the OLE DB destination by using a SQL query.</span></span>|  
  
 <span data-ttu-id="3a619-133">**預覽**</span><span class="sxs-lookup"><span data-stu-id="3a619-133">**Preview**</span></span>  
 <span data-ttu-id="3a619-134">使用 [預覽查詢結果]  對話方塊來預覽結果。</span><span class="sxs-lookup"><span data-stu-id="3a619-134">Preview results by using the **Preview Query Results** dialog box.</span></span> <span data-ttu-id="3a619-135">預覽最多可顯示 200 個資料列。</span><span class="sxs-lookup"><span data-stu-id="3a619-135">Preview can display up to 200 rows.</span></span>  
  
## <a name="data-access-mode-dynamic-options"></a><span data-ttu-id="3a619-136">資料存取模式動態選項</span><span class="sxs-lookup"><span data-stu-id="3a619-136">Data Access Mode Dynamic Options</span></span>  
 <span data-ttu-id="3a619-137">**[資料存取模式]** 的每個設定都會顯示該設定專用的動態選項集。</span><span class="sxs-lookup"><span data-stu-id="3a619-137">Each of the settings for **Data access mode** displays a dynamic set of options specific to that setting.</span></span> <span data-ttu-id="3a619-138">下列章節將一一描述每個 **[資料存取模式]** 設定可用的動態選項。</span><span class="sxs-lookup"><span data-stu-id="3a619-138">The following sections describe each of the dynamic options available for each **Data access mode** setting.</span></span>  
  
### <a name="data-access-mode--table-or-view"></a><span data-ttu-id="3a619-139">資料存取模式 = 資料表或檢視</span><span class="sxs-lookup"><span data-stu-id="3a619-139">Data access mode = Table or view</span></span>  
 <span data-ttu-id="3a619-140">**資料表或檢視的名稱**</span><span class="sxs-lookup"><span data-stu-id="3a619-140">**Name of the table or the view**</span></span>  
 <span data-ttu-id="3a619-141">從資料來源中可用的清單中選取資料表或檢視名稱。</span><span class="sxs-lookup"><span data-stu-id="3a619-141">Select the name of the table or view from a list of those available in the data source.</span></span>  
  
 <span data-ttu-id="3a619-142">**新增**</span><span class="sxs-lookup"><span data-stu-id="3a619-142">**New**</span></span>  
 <span data-ttu-id="3a619-143">使用 [建立資料表]  對話方塊建立新的資料表。</span><span class="sxs-lookup"><span data-stu-id="3a619-143">Create a new table by using the **Create Table** dialog box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3a619-144">當您按一下 **[新增]** 時， [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 會根據連接的資料來源來產生預設 CREATE TABLE 陳述式。</span><span class="sxs-lookup"><span data-stu-id="3a619-144">When you click **New**, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] generates a default CREATE TABLE statement based on the connected data source.</span></span> <span data-ttu-id="3a619-145">這個預設 CREATE TABLE 陳述式將不會包含 FILESTREAM 屬性，即使來源資料表包含有宣告 FILESTREAM 屬性的資料行亦然。</span><span class="sxs-lookup"><span data-stu-id="3a619-145">This default CREATE TABLE statement will not include the FILESTREAM attribute even if the source table includes a column with the FILESTREAM attribute declared.</span></span> <span data-ttu-id="3a619-146">若要執行具有 FILESTREAM 屬性的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 元件，請先在目的地資料庫上實作 FILESTREAM 儲存體。</span><span class="sxs-lookup"><span data-stu-id="3a619-146">To run an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] component with the FILESTREAM attribute, first implement FILESTREAM storage on the destination database.</span></span> <span data-ttu-id="3a619-147">然後在 **[建立資料表]** 對話方塊中，將 FILESTREAM 屬性加入至 CREATE TABLE 陳述式。</span><span class="sxs-lookup"><span data-stu-id="3a619-147">Then, add the FILESTREAM attribute to the CREATE TABLE statement in the **Create Table** dialog box.</span></span> <span data-ttu-id="3a619-148">如需詳細資訊，請參閱[二進位大型物件 &#40;Blob&#41; 資料 &#40;SQL Server&#41;](../relational-databases/blob/binary-large-object-blob-data-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="3a619-148">For more information, see [Binary Large Object &#40;Blob&#41; Data &#40;SQL Server&#41;](../relational-databases/blob/binary-large-object-blob-data-sql-server.md).</span></span>  
  
### <a name="data-access-mode--table-or-view---fast-load"></a><span data-ttu-id="3a619-149">資料存取模式 = 資料表或檢視 - 快速載入</span><span class="sxs-lookup"><span data-stu-id="3a619-149">Data access mode = Table or view - fast load</span></span>  
 <span data-ttu-id="3a619-150">**資料表或檢視的名稱**</span><span class="sxs-lookup"><span data-stu-id="3a619-150">**Name of the table or view**</span></span>  
 <span data-ttu-id="3a619-151">使用此清單從資料庫選取資料表或檢視，或按一下 [新增]  建立新的資料表。</span><span class="sxs-lookup"><span data-stu-id="3a619-151">Select a table or view from the database by using this list, or create a new table by clicking **New**.</span></span>  
  
 <span data-ttu-id="3a619-152">**新增**</span><span class="sxs-lookup"><span data-stu-id="3a619-152">**New**</span></span>  
 <span data-ttu-id="3a619-153">使用 [建立資料表]  對話方塊建立新的資料表。</span><span class="sxs-lookup"><span data-stu-id="3a619-153">Create a new table by using the **Create Table** dialog box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3a619-154">當您按一下 **[新增]** 時， [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 會根據連接的資料來源來產生預設 CREATE TABLE 陳述式。</span><span class="sxs-lookup"><span data-stu-id="3a619-154">When you click **New**, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] generates a default CREATE TABLE statement based on the connected data source.</span></span> <span data-ttu-id="3a619-155">這個預設 CREATE TABLE 陳述式將不會包含 FILESTREAM 屬性，即使來源資料表包含有宣告 FILESTREAM 屬性的資料行亦然。</span><span class="sxs-lookup"><span data-stu-id="3a619-155">This default CREATE TABLE statement will not include the FILESTREAM attribute even if the source table includes a column with the FILESTREAM attribute declared.</span></span> <span data-ttu-id="3a619-156">若要執行具有 FILESTREAM 屬性的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 元件，請先在目的地資料庫上實作 FILESTREAM 儲存體。</span><span class="sxs-lookup"><span data-stu-id="3a619-156">To run an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] component with the FILESTREAM attribute, first implement FILESTREAM storage on the destination database.</span></span> <span data-ttu-id="3a619-157">然後在 **[建立資料表]** 對話方塊中，將 FILESTREAM 屬性加入至 CREATE TABLE 陳述式。</span><span class="sxs-lookup"><span data-stu-id="3a619-157">Then, add the FILESTREAM attribute to the CREATE TABLE statement in the **Create Table** dialog box.</span></span> <span data-ttu-id="3a619-158">如需詳細資訊，請參閱[二進位大型物件 &#40;Blob&#41; 資料 &#40;SQL Server&#41;](../relational-databases/blob/binary-large-object-blob-data-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="3a619-158">For more information, see [Binary Large Object &#40;Blob&#41; Data &#40;SQL Server&#41;](../relational-databases/blob/binary-large-object-blob-data-sql-server.md).</span></span>  
  
 <span data-ttu-id="3a619-159">**保留識別**</span><span class="sxs-lookup"><span data-stu-id="3a619-159">**Keep identity**</span></span>  
 <span data-ttu-id="3a619-160">指定載入資料時是否複製識別值。</span><span class="sxs-lookup"><span data-stu-id="3a619-160">Specify whether to copy identity values when data is loaded.</span></span> <span data-ttu-id="3a619-161">這個屬性只能搭配快速載入選項使用。</span><span class="sxs-lookup"><span data-stu-id="3a619-161">This property is available only with the fast load option.</span></span> <span data-ttu-id="3a619-162">此屬性的預設值為 `false`。</span><span class="sxs-lookup"><span data-stu-id="3a619-162">The default value of this property is `false`.</span></span>  
  
 <span data-ttu-id="3a619-163">**保留 Null**</span><span class="sxs-lookup"><span data-stu-id="3a619-163">**Keep nulls**</span></span>  
 <span data-ttu-id="3a619-164">指定載入資料時是否複製 Null 值。</span><span class="sxs-lookup"><span data-stu-id="3a619-164">Specify whether to copy null values when data is loaded.</span></span> <span data-ttu-id="3a619-165">這個屬性只能搭配快速載入選項使用。</span><span class="sxs-lookup"><span data-stu-id="3a619-165">This property is available only with the fast load option.</span></span> <span data-ttu-id="3a619-166">此屬性的預設值為 `false`。</span><span class="sxs-lookup"><span data-stu-id="3a619-166">The default value of this property is `false`.</span></span>  
  
 <span data-ttu-id="3a619-167">**資料表鎖定**</span><span class="sxs-lookup"><span data-stu-id="3a619-167">**Table lock**</span></span>  
 <span data-ttu-id="3a619-168">指定載入期間是否鎖定資料表。</span><span class="sxs-lookup"><span data-stu-id="3a619-168">Specify whether the table is locked during the load.</span></span> <span data-ttu-id="3a619-169">此屬性的預設值為 `true`。</span><span class="sxs-lookup"><span data-stu-id="3a619-169">The default value of this property is `true`.</span></span>  
  
 <span data-ttu-id="3a619-170">**檢查條件約束**</span><span class="sxs-lookup"><span data-stu-id="3a619-170">**Check constraints**</span></span>  
 <span data-ttu-id="3a619-171">指定目的地在載入資料時是否檢查條件約束。</span><span class="sxs-lookup"><span data-stu-id="3a619-171">Specify whether the destination checks constraints when it loads data.</span></span> <span data-ttu-id="3a619-172">此屬性的預設值為 `true`。</span><span class="sxs-lookup"><span data-stu-id="3a619-172">The default value of this property is `true`.</span></span>  
  
 <span data-ttu-id="3a619-173">**每批次的資料列**</span><span class="sxs-lookup"><span data-stu-id="3a619-173">**Rows per batch**</span></span>  
 <span data-ttu-id="3a619-174">指定批次中的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="3a619-174">Specify the number of rows in a batch.</span></span> <span data-ttu-id="3a619-175">此屬性的預設值是 **-1**，表示未指派任何值。</span><span class="sxs-lookup"><span data-stu-id="3a619-175">The default value of this property is **-1**, which indicates that no value has been assigned.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3a619-176">清除 [OLE DB 目的地編輯器]  中的文字方塊，指出您不要指派此屬性的自訂值。</span><span class="sxs-lookup"><span data-stu-id="3a619-176">Clear the text box in the **OLE DB Destination Editor** to indicate that you do not want to assign a custom value for this property.</span></span>  
  
 <span data-ttu-id="3a619-177">**插入認可大小上限**</span><span class="sxs-lookup"><span data-stu-id="3a619-177">**Maximum insert commit size**</span></span>  
 <span data-ttu-id="3a619-178">指定快速載入作業期間，OLE DB 目的地嘗試認可的批次大小。</span><span class="sxs-lookup"><span data-stu-id="3a619-178">Specify the batch size that the OLE DB destination tries to commit during fast load operations.</span></span> <span data-ttu-id="3a619-179">預設值 **0** 表示處理所有資料列之後會在單一批次中認可所有資料。</span><span class="sxs-lookup"><span data-stu-id="3a619-179">The value of **0** indicates that all data is committed in a single batch after all rows have been processed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3a619-180">**0** 的值可能會造成封裝停止回應，前提是 OLE DB 目的地和另一個資料流程元件正在更新相同的來源資料表。</span><span class="sxs-lookup"><span data-stu-id="3a619-180">A value of **0** might cause the running package to stop responding if the OLE DB destination and another data flow component are updating the same source table.</span></span> <span data-ttu-id="3a619-181">若要避免封裝停止回應，請將 **[插入認可大小上限]** 選項設定為 **2147483647**。</span><span class="sxs-lookup"><span data-stu-id="3a619-181">To prevent the package from stopping, set the **Maximum insert commit size** option to **2147483647**.</span></span>  
  
 <span data-ttu-id="3a619-182">如果您提供此屬性的值，目的地會認可批次中的資料列，這些批次小於 (a) [插入認可大小上限]  或 (b) 目前正在處理之緩衝區中的其餘資料列。</span><span class="sxs-lookup"><span data-stu-id="3a619-182">If you provide a value for this property, the destination commits rows in batches that are the smaller of (a) the **Maximum insert commit size**, or (b) the remaining rows in the buffer that is currently being processed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3a619-183">目的地的任何條件約束失敗都會使 [插入認可大小上限]  所定義的整批資料列失敗。</span><span class="sxs-lookup"><span data-stu-id="3a619-183">Any constraint failure at the destination causes the entire batch of rows defined by **Maximum insert commit size** to fail.</span></span>  
  
### <a name="data-access-mode--table-name-or-view-name-variable"></a><span data-ttu-id="3a619-184">資料存取模式 = 資料表名稱或檢視名稱變數</span><span class="sxs-lookup"><span data-stu-id="3a619-184">Data access mode = Table name or view name variable</span></span>  
 <span data-ttu-id="3a619-185">**變數名稱**</span><span class="sxs-lookup"><span data-stu-id="3a619-185">**Variable name**</span></span>  
 <span data-ttu-id="3a619-186">請選取包含資料表或檢視名稱的變數。</span><span class="sxs-lookup"><span data-stu-id="3a619-186">Select the variable that contains the name of the table or view.</span></span>  
  
### <a name="data-access-mode--table-name-or-view-name-variable---fast-load"></a><span data-ttu-id="3a619-187">資料存取模式 = 資料表名稱或檢視名稱變數 - 快速載入)</span><span class="sxs-lookup"><span data-stu-id="3a619-187">Data Access Mode = Table name or view name variable - fast load)</span></span>  
 <span data-ttu-id="3a619-188">**變數名稱**</span><span class="sxs-lookup"><span data-stu-id="3a619-188">**Variable name**</span></span>  
 <span data-ttu-id="3a619-189">請選取包含資料表或檢視名稱的變數。</span><span class="sxs-lookup"><span data-stu-id="3a619-189">Select the variable that contains the name of the table or view.</span></span>  
  
 <span data-ttu-id="3a619-190">**新增**</span><span class="sxs-lookup"><span data-stu-id="3a619-190">**New**</span></span>  
 <span data-ttu-id="3a619-191">使用 [建立資料表]  對話方塊建立新的資料表。</span><span class="sxs-lookup"><span data-stu-id="3a619-191">Create a new table by using the **Create Table** dialog box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3a619-192">當您按一下 **[新增]** 時， [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 會根據連接的資料來源來產生預設 CREATE TABLE 陳述式。</span><span class="sxs-lookup"><span data-stu-id="3a619-192">When you click **New**, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] generates a default CREATE TABLE statement based on the connected data source.</span></span> <span data-ttu-id="3a619-193">這個預設 CREATE TABLE 陳述式將不會包含 FILESTREAM 屬性，即使來源資料表包含有宣告 FILESTREAM 屬性的資料行亦然。</span><span class="sxs-lookup"><span data-stu-id="3a619-193">This default CREATE TABLE statement will not include the FILESTREAM attribute even if the source table includes a column with the FILESTREAM attribute declared.</span></span> <span data-ttu-id="3a619-194">若要執行具有 FILESTREAM 屬性的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 元件，請先在目的地資料庫上實作 FILESTREAM 儲存體。</span><span class="sxs-lookup"><span data-stu-id="3a619-194">To run an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] component with the FILESTREAM attribute, first implement FILESTREAM storage on the destination database.</span></span> <span data-ttu-id="3a619-195">然後在 **[建立資料表]** 對話方塊中，將 FILESTREAM 屬性加入至 CREATE TABLE 陳述式。</span><span class="sxs-lookup"><span data-stu-id="3a619-195">Then, add the FILESTREAM attribute to the CREATE TABLE statement in the **Create Table** dialog box.</span></span> <span data-ttu-id="3a619-196">如需詳細資訊，請參閱[二進位大型物件 &#40;Blob&#41; 資料 &#40;SQL Server&#41;](../relational-databases/blob/binary-large-object-blob-data-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="3a619-196">For more information, see [Binary Large Object &#40;Blob&#41; Data &#40;SQL Server&#41;](../relational-databases/blob/binary-large-object-blob-data-sql-server.md).</span></span>  
  
 <span data-ttu-id="3a619-197">**保留識別**</span><span class="sxs-lookup"><span data-stu-id="3a619-197">**Keep identity**</span></span>  
 <span data-ttu-id="3a619-198">指定載入資料時是否複製識別值。</span><span class="sxs-lookup"><span data-stu-id="3a619-198">Specify whether to copy identity values when data is loaded.</span></span> <span data-ttu-id="3a619-199">這個屬性只能搭配快速載入選項使用。</span><span class="sxs-lookup"><span data-stu-id="3a619-199">This property is available only with the fast load option.</span></span> <span data-ttu-id="3a619-200">此屬性的預設值為 `false`。</span><span class="sxs-lookup"><span data-stu-id="3a619-200">The default value of this property is `false`.</span></span>  
  
 <span data-ttu-id="3a619-201">**保留 Null**</span><span class="sxs-lookup"><span data-stu-id="3a619-201">**Keep nulls**</span></span>  
 <span data-ttu-id="3a619-202">指定載入資料時是否複製 Null 值。</span><span class="sxs-lookup"><span data-stu-id="3a619-202">Specify whether to copy null values when data is loaded.</span></span> <span data-ttu-id="3a619-203">這個屬性只能搭配快速載入選項使用。</span><span class="sxs-lookup"><span data-stu-id="3a619-203">This property is available only with the fast load option.</span></span> <span data-ttu-id="3a619-204">此屬性的預設值為 `false`。</span><span class="sxs-lookup"><span data-stu-id="3a619-204">The default value of this property is `false`.</span></span>  
  
 <span data-ttu-id="3a619-205">**資料表鎖定**</span><span class="sxs-lookup"><span data-stu-id="3a619-205">**Table lock**</span></span>  
 <span data-ttu-id="3a619-206">指定載入期間是否鎖定資料表。</span><span class="sxs-lookup"><span data-stu-id="3a619-206">Specify whether the table is locked during the load.</span></span> <span data-ttu-id="3a619-207">此屬性的預設值為 `false`。</span><span class="sxs-lookup"><span data-stu-id="3a619-207">The default value of this property is `false`.</span></span>  
  
 <span data-ttu-id="3a619-208">**檢查條件約束**</span><span class="sxs-lookup"><span data-stu-id="3a619-208">**Check constraints**</span></span>  
 <span data-ttu-id="3a619-209">指定工作是否檢查條件約束。</span><span class="sxs-lookup"><span data-stu-id="3a619-209">Specify whether the task checks constraints.</span></span> <span data-ttu-id="3a619-210">此屬性的預設值為 `false`。</span><span class="sxs-lookup"><span data-stu-id="3a619-210">The default value of this property is `false`.</span></span>  
  
 <span data-ttu-id="3a619-211">**每批次的資料列**</span><span class="sxs-lookup"><span data-stu-id="3a619-211">**Rows per batch**</span></span>  
 <span data-ttu-id="3a619-212">指定批次中的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="3a619-212">Specify the number of rows in a batch.</span></span> <span data-ttu-id="3a619-213">此屬性的預設值是 **-1**，表示未指派任何值。</span><span class="sxs-lookup"><span data-stu-id="3a619-213">The default value of this property is **-1**, which indicates that no value has been assigned.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3a619-214">清除 [OLE DB 目的地編輯器]  中的文字方塊，指出您不要指派此屬性的自訂值。</span><span class="sxs-lookup"><span data-stu-id="3a619-214">Clear the text box in the **OLE DB Destination Editor** to indicate that you do not want to assign a custom value for this property.</span></span>  
  
 <span data-ttu-id="3a619-215">**插入認可大小上限**</span><span class="sxs-lookup"><span data-stu-id="3a619-215">**Maximum insert commit size**</span></span>  
 <span data-ttu-id="3a619-216">指定快速載入作業期間，OLE DB 目的地嘗試認可的批次大小。</span><span class="sxs-lookup"><span data-stu-id="3a619-216">Specify the batch size that the OLE DB destination tries to commit during fast load operations.</span></span> <span data-ttu-id="3a619-217">預設值 **2147483647** 表示處理所有資料列之後會在單一批次中認可所有資料。</span><span class="sxs-lookup"><span data-stu-id="3a619-217">The default value of **2147483647** indicates that all data is committed in a single batch after all rows have been processed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3a619-218">**0** 的值可能會造成封裝停止回應，前提是 OLE DB 目的地和另一個資料流程元件正在更新相同的來源資料表。</span><span class="sxs-lookup"><span data-stu-id="3a619-218">A value of **0** might cause the running package to stop responding if the OLE DB destination and another data flow component are updating the same source table.</span></span> <span data-ttu-id="3a619-219">若要避免封裝停止回應，請將 **[插入認可大小上限]** 選項設定為 **2147483647**。</span><span class="sxs-lookup"><span data-stu-id="3a619-219">To prevent the package from stopping, set the **Maximum insert commit size** option to **2147483647**.</span></span>  
  
### <a name="data-access-mode--sql-command"></a><span data-ttu-id="3a619-220">資料存取模式 = SQL 命令</span><span class="sxs-lookup"><span data-stu-id="3a619-220">Data access mode = SQL command</span></span>  
 <span data-ttu-id="3a619-221">**SQL 命令文字**</span><span class="sxs-lookup"><span data-stu-id="3a619-221">**SQL command text**</span></span>  
 <span data-ttu-id="3a619-222">輸入 SQL 查詢文字，按一下 [建立查詢]  建立查詢，或按一下 [瀏覽]  找到包含查詢文字的檔案。</span><span class="sxs-lookup"><span data-stu-id="3a619-222">Enter the text of a SQL query, build the query by clicking **Build Query**, or locate the file that contains the query text by clicking **Browse**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3a619-223">OLE DB 目的地不支援參數。</span><span class="sxs-lookup"><span data-stu-id="3a619-223">The OLE DB destination does not support parameters.</span></span> <span data-ttu-id="3a619-224">如果需要執行參數化 INSERT 陳述式，請考慮 OLE DB 命令轉換。</span><span class="sxs-lookup"><span data-stu-id="3a619-224">If you need to execute a parameterized INSERT statement, consider the OLE DB Command transformation.</span></span> <span data-ttu-id="3a619-225">如需相關資訊，請參閱 [OLE DB Command Transformation](data-flow/transformations/ole-db-command-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="3a619-225">For more information, see [OLE DB Command Transformation](data-flow/transformations/ole-db-command-transformation.md).</span></span>  
  
 <span data-ttu-id="3a619-226">**建立查詢**</span><span class="sxs-lookup"><span data-stu-id="3a619-226">**Build query**</span></span>  
 <span data-ttu-id="3a619-227">使用 [查詢產生器]  對話方塊，以視覺化的方式來建構 SQL 查詢。</span><span class="sxs-lookup"><span data-stu-id="3a619-227">Use the **Query Builder** dialog box to construct the SQL query visually.</span></span>  
  
 <span data-ttu-id="3a619-228">**瀏覽**</span><span class="sxs-lookup"><span data-stu-id="3a619-228">**Browse**</span></span>  
 <span data-ttu-id="3a619-229">使用 [開啟]  對話方塊來找出包含 SQL 查詢文字的檔案。</span><span class="sxs-lookup"><span data-stu-id="3a619-229">Use the **Open** dialog box to locate the file that contains the text of the SQL query.</span></span>  
  
 <span data-ttu-id="3a619-230">**剖析查詢**</span><span class="sxs-lookup"><span data-stu-id="3a619-230">**Parse query**</span></span>  
 <span data-ttu-id="3a619-231">請確認查詢文字的語法。</span><span class="sxs-lookup"><span data-stu-id="3a619-231">Verify the syntax of the query text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a619-232">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3a619-232">See Also</span></span>  
 <span data-ttu-id="3a619-233">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="3a619-233">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="3a619-234">[OLE DB 目的地編輯器 &#40;對應] 頁面&#41;](../../2014/integration-services/ole-db-destination-editor-mappings-page.md) </span><span class="sxs-lookup"><span data-stu-id="3a619-234">[OLE DB Destination Editor &#40;Mappings Page&#41;](../../2014/integration-services/ole-db-destination-editor-mappings-page.md) </span></span>  
 <span data-ttu-id="3a619-235">[OLE DB 目的地編輯器 &#40;錯誤輸出頁面&#41;](../../2014/integration-services/ole-db-destination-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="3a619-235">[OLE DB Destination Editor &#40;Error Output Page&#41;](../../2014/integration-services/ole-db-destination-editor-error-output-page.md) </span></span>  
 [<span data-ttu-id="3a619-236">使用 OLE DB 目的地來載入資料</span><span class="sxs-lookup"><span data-stu-id="3a619-236">Load Data by Using the OLE DB Destination</span></span>](data-flow/load-data-by-using-the-ole-db-destination.md)  
  
  
