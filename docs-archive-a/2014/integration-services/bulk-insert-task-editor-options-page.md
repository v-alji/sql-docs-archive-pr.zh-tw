---
title: '[大量插入工作編輯器] (選項] 頁面) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.bulkinserttask.options.f1
helpviewer_keywords:
- Bulk Insert Task Editor
ms.assetid: b3702811-3eb8-4b28-9190-5ae7a1a7bb6f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1751d1e0ac01d5459a8c76e6a48626c2ad6deafd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706670"
---
# <a name="bulk-insert-task-editor-options-page"></a><span data-ttu-id="9844b-102">大量插入工作編輯器 (選項頁面)</span><span class="sxs-lookup"><span data-stu-id="9844b-102">Bulk Insert Task Editor (Options Page)</span></span>
  <span data-ttu-id="9844b-103">使用 **[大量插入工作編輯器]** 對話方塊的 **[選項]** 頁面，即可設定大量插入作業的屬性。</span><span class="sxs-lookup"><span data-stu-id="9844b-103">Use the **Options** page of the **Bulk Insert Task Editor** dialog box to set properties for the bulk insert operation.</span></span> <span data-ttu-id="9844b-104">大量插入工作會將大量資料複製到 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 資料表或檢視表。</span><span class="sxs-lookup"><span data-stu-id="9844b-104">The Bulk Insert task copies large amounts of data into a [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] table or view.</span></span>  
  
 <span data-ttu-id="9844b-105">若要了解如何使用大量插入，請參閱[大量插入工作](control-flow/bulk-insert-task.md)和 [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="9844b-105">To learn about working with bulk inserts, see [Bulk Insert Task](control-flow/bulk-insert-task.md) and [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql).</span></span>  
  
## <a name="options"></a><span data-ttu-id="9844b-106">選項。</span><span class="sxs-lookup"><span data-stu-id="9844b-106">Options</span></span>  
 <span data-ttu-id="9844b-107">**CodePage**</span><span class="sxs-lookup"><span data-stu-id="9844b-107">**CodePage**</span></span>  
 <span data-ttu-id="9844b-108">指定資料檔中之資料的字碼頁。</span><span class="sxs-lookup"><span data-stu-id="9844b-108">Specify the code page of the data in the data file.</span></span>  
  
 <span data-ttu-id="9844b-109">**DataFileType**</span><span class="sxs-lookup"><span data-stu-id="9844b-109">**DataFileType**</span></span>  
 <span data-ttu-id="9844b-110">指定載入作業所用的資料類型值。</span><span class="sxs-lookup"><span data-stu-id="9844b-110">Specify the data-type value to use in the load operation.</span></span>  
  
 <span data-ttu-id="9844b-111">**BatchSize**</span><span class="sxs-lookup"><span data-stu-id="9844b-111">**BatchSize**</span></span>  
 <span data-ttu-id="9844b-112">指定批次中的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="9844b-112">Specify the number of rows in a batch.</span></span> <span data-ttu-id="9844b-113">預設為整個資料檔。</span><span class="sxs-lookup"><span data-stu-id="9844b-113">The default is the entire data file.</span></span> <span data-ttu-id="9844b-114">如果您將 **[BatchSize]** 設定為零，則會以單一批次載入資料。</span><span class="sxs-lookup"><span data-stu-id="9844b-114">If you set **BatchSize** to zero, the data is loaded in a single batch.</span></span>  
  
 <span data-ttu-id="9844b-115">**LastRow**</span><span class="sxs-lookup"><span data-stu-id="9844b-115">**LastRow**</span></span>  
 <span data-ttu-id="9844b-116">指定要複製的最後一個資料列。</span><span class="sxs-lookup"><span data-stu-id="9844b-116">Specify the last row to copy.</span></span>  
  
 <span data-ttu-id="9844b-117">**FirstRow**</span><span class="sxs-lookup"><span data-stu-id="9844b-117">**FirstRow**</span></span>  
 <span data-ttu-id="9844b-118">指定要開始複製的第一個資料列。</span><span class="sxs-lookup"><span data-stu-id="9844b-118">Specify the first row from which to start copying.</span></span>  
  
 <span data-ttu-id="9844b-119">**選項**</span><span class="sxs-lookup"><span data-stu-id="9844b-119">**Options**</span></span>  
 |<span data-ttu-id="9844b-120">詞彙</span><span class="sxs-lookup"><span data-stu-id="9844b-120">Term</span></span>|<span data-ttu-id="9844b-121">定義</span><span class="sxs-lookup"><span data-stu-id="9844b-121">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="9844b-122">**檢查條件約束**</span><span class="sxs-lookup"><span data-stu-id="9844b-122">**Check constraints**</span></span>|<span data-ttu-id="9844b-123">選取此選項可檢查資料表與資料行條件約束。</span><span class="sxs-lookup"><span data-stu-id="9844b-123">Select to check the table and column constraints.</span></span>|  
|<span data-ttu-id="9844b-124">**保留 Null**</span><span class="sxs-lookup"><span data-stu-id="9844b-124">**Keep nulls**</span></span>|<span data-ttu-id="9844b-125">選取此選項可在大量插入作業期間保留 Null 值，而不是在空白資料行插入任何預設值。</span><span class="sxs-lookup"><span data-stu-id="9844b-125">Select to retain null values during the bulk insert operation, instead of inserting any default values for empty columns.</span></span>|  
|<span data-ttu-id="9844b-126">**啟用識別插入**</span><span class="sxs-lookup"><span data-stu-id="9844b-126">**Enable identity insert**</span></span>|<span data-ttu-id="9844b-127">選取此選項可將現有的值插入識別欄位。</span><span class="sxs-lookup"><span data-stu-id="9844b-127">Select to insert existing values into an identity column.</span></span>|  
|<span data-ttu-id="9844b-128">**資料表鎖定**</span><span class="sxs-lookup"><span data-stu-id="9844b-128">**Table lock**</span></span>|<span data-ttu-id="9844b-129">選取此選項可在大量插入期間鎖定資料表。</span><span class="sxs-lookup"><span data-stu-id="9844b-129">Select to lock the table during the bulk insert.</span></span>|  
|<span data-ttu-id="9844b-130">**引發觸發程序**</span><span class="sxs-lookup"><span data-stu-id="9844b-130">**Fire triggers**</span></span>|<span data-ttu-id="9844b-131">選取即可引發資料表上的任何插入、更新或刪除觸發程序。</span><span class="sxs-lookup"><span data-stu-id="9844b-131">Select to fire any insert, update, or delete triggers on the table.</span></span>|  
  
 <span data-ttu-id="9844b-132">**SortedData**</span><span class="sxs-lookup"><span data-stu-id="9844b-132">**SortedData**</span></span>  
 <span data-ttu-id="9844b-133">在大量插入陳述式中指定 ORDER BY 子句。</span><span class="sxs-lookup"><span data-stu-id="9844b-133">Specify the ORDER BY clause in the bulk insert statement.</span></span> <span data-ttu-id="9844b-134">您所提供的資料行名稱必須是目的資料表中的有效資料行。</span><span class="sxs-lookup"><span data-stu-id="9844b-134">The column name that you supply must be a valid column in the destination table.</span></span> <span data-ttu-id="9844b-135">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="9844b-135">The default is `false`.</span></span> <span data-ttu-id="9844b-136">這表示資料並未依 ORDER BY 子句排序。</span><span class="sxs-lookup"><span data-stu-id="9844b-136">This means that the data is not sorted by an ORDER BY clause.</span></span>  
  
 <span data-ttu-id="9844b-137">**MaxErrors**</span><span class="sxs-lookup"><span data-stu-id="9844b-137">**MaxErrors**</span></span>  
 <span data-ttu-id="9844b-138">指定取消大量插入作業之前，可以發生的錯誤數目上限。</span><span class="sxs-lookup"><span data-stu-id="9844b-138">Specify the maximum number of errors that can occur before the bulk insert operation is canceled.</span></span> <span data-ttu-id="9844b-139">值為 0 指出允許發生無限個錯誤。</span><span class="sxs-lookup"><span data-stu-id="9844b-139">A value of 0 indicates that an infinite number of errors are allowed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9844b-140">大量載入作業無法匯入的每個資料列都會計算為一個錯誤。</span><span class="sxs-lookup"><span data-stu-id="9844b-140">Each row that cannot be imported by the bulk load operation is counted as one error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9844b-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9844b-141">See Also</span></span>  
 <span data-ttu-id="9844b-142">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="9844b-142">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="9844b-143">[[大量插入工作編輯器] &#40;[一般] 頁面&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="9844b-143">[Bulk Insert Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="9844b-144">[[大量插入工作編輯器] &#40;連接] 頁面&#41;](../../2014/integration-services/bulk-insert-task-editor-connection-page.md) </span><span class="sxs-lookup"><span data-stu-id="9844b-144">[Bulk Insert Task Editor &#40;Connection Page&#41;](../../2014/integration-services/bulk-insert-task-editor-connection-page.md) </span></span>  
 <span data-ttu-id="9844b-145">[運算式頁面](expressions/expressions-page.md) </span><span class="sxs-lookup"><span data-stu-id="9844b-145">[Expressions Page](expressions/expressions-page.md) </span></span>  
 [<span data-ttu-id="9844b-146">控制流程</span><span class="sxs-lookup"><span data-stu-id="9844b-146">Control Flow</span></span>](control-flow/control-flow.md)  
  
  
