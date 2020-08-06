---
title: '[大量插入工作編輯器] (連接頁面) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.bulkinserttask.connection.f1
helpviewer_keywords:
- Bulk Insert Task Editor
ms.assetid: 51252c20-8865-4ede-a3fd-bd73a968f47d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b2cd722fd8520ff011c0d57040a55d624178e15e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706681"
---
# <a name="bulk-insert-task-editor-connection-page"></a><span data-ttu-id="a5194-102">大量插入工作編輯器 (連接頁面)</span><span class="sxs-lookup"><span data-stu-id="a5194-102">Bulk Insert Task Editor (Connection Page)</span></span>
  <span data-ttu-id="a5194-103">使用 [大量插入工作編輯器]  對話方塊的 [連接]  頁面，即可指定大量插入作業的來源和目的地，以及要使用的格式。</span><span class="sxs-lookup"><span data-stu-id="a5194-103">Use the **Connection** page of the **Bulk Insert Task Editor** dialog box to specify the source and destination of the bulk insert operation and the format to use.</span></span>  
  
 <span data-ttu-id="a5194-104">若要了解如何使用大量插入，請參閱[大量插入工作](control-flow/bulk-insert-task.md)和[匯入或匯出資料的格式檔案 &#40;SQL Server&#41;](../relational-databases/import-export/format-files-for-importing-or-exporting-data-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="a5194-104">To learn about working with bulk inserts, see [Bulk Insert Task](control-flow/bulk-insert-task.md) and [Format Files for Importing or Exporting Data &#40;SQL Server&#41;](../relational-databases/import-export/format-files-for-importing-or-exporting-data-sql-server.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="a5194-105">選項。</span><span class="sxs-lookup"><span data-stu-id="a5194-105">Options</span></span>  
 <span data-ttu-id="a5194-106">**[連接]**</span><span class="sxs-lookup"><span data-stu-id="a5194-106">**Connection**</span></span>  
 <span data-ttu-id="a5194-107">在清單中選取 OLE DB 連線管理員，或按一下 [\<**New connection...**>] 以建立新的連線。</span><span class="sxs-lookup"><span data-stu-id="a5194-107">Select an OLE DB connection manager in the list, or click \<**New connection...**> to create a new connection.</span></span>  
  
 <span data-ttu-id="a5194-108">**相關主題** [OLE DB 連線管理員](connection-manager/ole-db-connection-manager.md)、 [設定 OLE DB 連接管理員](../../2014/integration-services/configure-ole-db-connection-manager.md)</span><span class="sxs-lookup"><span data-stu-id="a5194-108">**Related Topics:** [OLE DB Connection Manager](connection-manager/ole-db-connection-manager.md), [Configure OLE DB Connection Manager](../../2014/integration-services/configure-ole-db-connection-manager.md)</span></span>  
  
 <span data-ttu-id="a5194-109">**DestinationTable**</span><span class="sxs-lookup"><span data-stu-id="a5194-109">**DestinationTable**</span></span>  
 <span data-ttu-id="a5194-110">輸入目的地資料表或檢視的名稱，或在清單中選取資料表或檢視。</span><span class="sxs-lookup"><span data-stu-id="a5194-110">Type the name of the destination table or view or select a table or view in the list.</span></span>  
  
 <span data-ttu-id="a5194-111">**格式**</span><span class="sxs-lookup"><span data-stu-id="a5194-111">**Format**</span></span>  
 <span data-ttu-id="a5194-112">選取大量插入的格式來源。</span><span class="sxs-lookup"><span data-stu-id="a5194-112">Select the source of the format for the bulk insert.</span></span> <span data-ttu-id="a5194-113">這個屬性具有下表中所列的選項。</span><span class="sxs-lookup"><span data-stu-id="a5194-113">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="a5194-114">值</span><span class="sxs-lookup"><span data-stu-id="a5194-114">Value</span></span>|<span data-ttu-id="a5194-115">描述</span><span class="sxs-lookup"><span data-stu-id="a5194-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a5194-116">**使用檔案**</span><span class="sxs-lookup"><span data-stu-id="a5194-116">**Use File**</span></span>|<span data-ttu-id="a5194-117">選取包含格式規格的檔案。</span><span class="sxs-lookup"><span data-stu-id="a5194-117">Select a file containing the format specification.</span></span> <span data-ttu-id="a5194-118">選取此選項會顯示動態選項 [FormatFile]  。</span><span class="sxs-lookup"><span data-stu-id="a5194-118">Selecting this option displays the dynamic option, **FormatFile**.</span></span>|  
|<span data-ttu-id="a5194-119">**指定**</span><span class="sxs-lookup"><span data-stu-id="a5194-119">**Specify**</span></span>|<span data-ttu-id="a5194-120">指定格式。</span><span class="sxs-lookup"><span data-stu-id="a5194-120">Specify the format.</span></span> <span data-ttu-id="a5194-121">選取此選項會顯示動態選項 [ `RowDelimiter` 和] `ColumnDelimiter` 。</span><span class="sxs-lookup"><span data-stu-id="a5194-121">Selecting this option displays the dynamic options, `RowDelimiter` and `ColumnDelimiter`.</span></span>|  
  
 <span data-ttu-id="a5194-122">**檔案**</span><span class="sxs-lookup"><span data-stu-id="a5194-122">**File**</span></span>  
 <span data-ttu-id="a5194-123">在清單中選取檔案連線管理員或一般檔案連線管理員，或按一下 [\<**New connection...**>] 以建立新的連線。</span><span class="sxs-lookup"><span data-stu-id="a5194-123">Select a File or Flat File connection manager in the list, or click \<**New connection...**> to create a new connection.</span></span>  
  
 <span data-ttu-id="a5194-124">檔案位置相對於在此工作之連接管理員中指定的 SQL Server Database Engine。</span><span class="sxs-lookup"><span data-stu-id="a5194-124">The file location is relative to the SQL Server Database Engine specified in the connection manager for this task.</span></span> <span data-ttu-id="a5194-125">SQL Server Database Engine 必須可以在伺服器上的本機硬碟，或透過 SQL Server 的共用或對應磁碟機，存取文字檔。</span><span class="sxs-lookup"><span data-stu-id="a5194-125">The text file must be accessible by the SQL Server Database Engine either on a local hard drive on the server, or via a share or mapped drive to the SQL Server.</span></span> <span data-ttu-id="a5194-126">SSIS 執行階段無法存取檔案。</span><span class="sxs-lookup"><span data-stu-id="a5194-126">The file is not accessed by the SSIS Runtime.</span></span>  
  
 <span data-ttu-id="a5194-127">如果您使用一般檔案連接管理員存取來源檔案，則大量插入工作不會使用一般檔案連接管理員中指定的格式。</span><span class="sxs-lookup"><span data-stu-id="a5194-127">If you access the source file by using a Flat File connection manager, the Bulk Insert task does not use the format specified in the Flat File connection manager.</span></span> <span data-ttu-id="a5194-128">而「大量插入」工作會使用格式檔案中指定的格式，或工作之 RowDelimiter 和 ColumnDelimiter 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="a5194-128">Instead, the Bulk Insert task uses either the format specified in a format file or the values of the RowDelimiter and ColumnDelimiter properties of the task.</span></span>  
  
 <span data-ttu-id="a5194-129">**相關主題︰** [檔案連線管理員](connection-manager/file-connection-manager.md)、[檔案連線管理員編輯器](../../2014/integration-services/file-connection-manager-editor.md)、[一般檔案連線管理員](connection-manager/flat-file-connection-manager.md)、[一般檔案連線管理員編輯器 &#40;一般頁面&#41;](general-page-of-integration-services-designers-options.md)、[一般檔案連線管理員編輯器 &#40;資料行頁面&#41;](../../2014/integration-services/flat-file-connection-manager-editor-columns-page.md)、[一般檔案連線管理員編輯器 &#40;進階頁面&#41;](../../2014/integration-services/flat-file-connection-manager-editor-advanced-page.md)</span><span class="sxs-lookup"><span data-stu-id="a5194-129">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md), [Flat File Connection Manager](connection-manager/flat-file-connection-manager.md), [Flat File Connection Manager Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md), [Flat File Connection Manager Editor &#40;Columns Page&#41;](../../2014/integration-services/flat-file-connection-manager-editor-columns-page.md), [Flat File Connection Manager Editor &#40;Advanced Page&#41;](../../2014/integration-services/flat-file-connection-manager-editor-advanced-page.md)</span></span>  
  
 <span data-ttu-id="a5194-130">**重新整理資料表**</span><span class="sxs-lookup"><span data-stu-id="a5194-130">**Refresh Tables**</span></span>  
 <span data-ttu-id="a5194-131">重新整理資料表和檢視的清單。</span><span class="sxs-lookup"><span data-stu-id="a5194-131">Refresh the list of tables and views.</span></span>  
  
## <a name="format-dynamic-options"></a><span data-ttu-id="a5194-132">格式動態選項</span><span class="sxs-lookup"><span data-stu-id="a5194-132">Format Dynamic Options</span></span>  
  
### <a name="format--use-file"></a><span data-ttu-id="a5194-133">格式 = 使用檔案</span><span class="sxs-lookup"><span data-stu-id="a5194-133">Format = Use File</span></span>  
 <span data-ttu-id="a5194-134">**FormatFile**</span><span class="sxs-lookup"><span data-stu-id="a5194-134">**FormatFile**</span></span>  
 <span data-ttu-id="a5194-135">輸入格式檔案的路徑，或按一下省略符號按鈕 **(...)** 以尋找格式檔案。</span><span class="sxs-lookup"><span data-stu-id="a5194-135">Type the path of the format file or click the ellipsis button **(...)** to locate the format file.</span></span>  
  
### <a name="format--specify"></a><span data-ttu-id="a5194-136">格式 = 指定</span><span class="sxs-lookup"><span data-stu-id="a5194-136">Format = Specify</span></span>  
 `RowDelimiter`  
 <span data-ttu-id="a5194-137">指定來源檔案中的資料列分隔符號。</span><span class="sxs-lookup"><span data-stu-id="a5194-137">Specify the row delimiter in the source file.</span></span> <span data-ttu-id="a5194-138">預設值是 [{CR}{LF}]  。</span><span class="sxs-lookup"><span data-stu-id="a5194-138">The default value is **{CR}{LF}**.</span></span>  
  
 `ColumnDelimiter`  
 <span data-ttu-id="a5194-139">指定來源檔案中的資料行分隔符號。</span><span class="sxs-lookup"><span data-stu-id="a5194-139">Specify the column delimiter in the source file.</span></span> <span data-ttu-id="a5194-140">預設值是 [定位字元]  。</span><span class="sxs-lookup"><span data-stu-id="a5194-140">The default is **Tab**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5194-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a5194-141">See Also</span></span>  
 <span data-ttu-id="a5194-142">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="a5194-142">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="a5194-143">[[大量插入工作編輯器] &#40;[一般] 頁面&#41;](../../2014/integration-services/bulk-insert-task-editor-general-page.md) </span><span class="sxs-lookup"><span data-stu-id="a5194-143">[Bulk Insert Task Editor &#40;General Page&#41;](../../2014/integration-services/bulk-insert-task-editor-general-page.md) </span></span>  
 <span data-ttu-id="a5194-144">[[大量插入工作編輯器] &#40;選項] 頁面&#41;](../../2014/integration-services/bulk-insert-task-editor-options-page.md) </span><span class="sxs-lookup"><span data-stu-id="a5194-144">[Bulk Insert Task Editor &#40;Options Page&#41;](../../2014/integration-services/bulk-insert-task-editor-options-page.md) </span></span>  
 <span data-ttu-id="a5194-145">[運算式頁面](expressions/expressions-page.md) </span><span class="sxs-lookup"><span data-stu-id="a5194-145">[Expressions Page](expressions/expressions-page.md) </span></span>  
 <span data-ttu-id="a5194-146">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a5194-146">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span></span>  
 [<span data-ttu-id="a5194-147">控制流程</span><span class="sxs-lookup"><span data-stu-id="a5194-147">Control Flow</span></span>](control-flow/control-flow.md)  
  
  
