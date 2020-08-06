---
title: XML 索引對話方塊 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.xmlindexes
ms.assetid: eef38310-4498-4ccc-bb77-5bbd1c7cc477
author: stevestein
ms.author: sstein
ms.openlocfilehash: f1fb23a801a9129611c032fa1d659caf624088aa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597489"
---
# <a name="xml-indexes-dialog-box-visual-database-tools"></a><span data-ttu-id="001a9-102">XML 索引對話方塊 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="001a9-102">XML Indexes Dialog Box (Visual Database Tools)</span></span>
  <span data-ttu-id="001a9-103">使用 [XML 索引]  對話方塊可建立 XML 資料類型資料行的索引，但是此類資料行無法以 [索引/索引鍵]  對話方塊進行索引。</span><span class="sxs-lookup"><span data-stu-id="001a9-103">Use the **XML Indexes** dialog box to create indexes for columns of the data type XML, which cannot be indexed using the **Index/Keys** dialog box.</span></span> <span data-ttu-id="001a9-104">各個 XML 資料行可以具有一個以上的 XML 索引，但是首先建立 (主要) 的索引將成為其他索引 (次要) 的基準。</span><span class="sxs-lookup"><span data-stu-id="001a9-104">Each XML column can have more than one XML Index, but the first one created (primary) will be the basis of the others (secondary).</span></span> <span data-ttu-id="001a9-105">如果刪除主要的 XML 索引，次要索引也將一併刪除。</span><span class="sxs-lookup"><span data-stu-id="001a9-105">If you delete the primary XML index, the secondary indexes will also be deleted.</span></span>  
  
## <a name="options"></a><span data-ttu-id="001a9-106">選項。</span><span class="sxs-lookup"><span data-stu-id="001a9-106">Options</span></span>  
 <span data-ttu-id="001a9-107">**選取的 XML 索引**</span><span class="sxs-lookup"><span data-stu-id="001a9-107">**Selected XML Index**</span></span>  
 <span data-ttu-id="001a9-108">列出現有的 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="001a9-108">Lists existing XML indexes.</span></span> <span data-ttu-id="001a9-109">選取此選項，即可在右邊方格中顯示其屬性。</span><span class="sxs-lookup"><span data-stu-id="001a9-109">Select to show its properties in the grid to the right.</span></span> <span data-ttu-id="001a9-110">如果清單是空的，表示此資料表沒有任何定義的項目。</span><span class="sxs-lookup"><span data-stu-id="001a9-110">If the list is empty, none have been defined for the table.</span></span>  
  
 <span data-ttu-id="001a9-111">**加入**</span><span class="sxs-lookup"><span data-stu-id="001a9-111">**Add**</span></span>  
 <span data-ttu-id="001a9-112">建立新的 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="001a9-112">Create a new XML index.</span></span>  
  
 <span data-ttu-id="001a9-113">**刪除**</span><span class="sxs-lookup"><span data-stu-id="001a9-113">**Delete**</span></span>  
 <span data-ttu-id="001a9-114">刪除 [選取的 XML 索引]  清單中選取的 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="001a9-114">Delete XML index selected in the **Selected XML Index** list.</span></span> <span data-ttu-id="001a9-115">如果刪除主要 XML 索引，您會接獲通知表示這個動作將同時刪除所有的次要索引；您可以選擇繼續或取消動作。</span><span class="sxs-lookup"><span data-stu-id="001a9-115">If you delete the primary XML index, you will be notified that this will delete all secondary ones as well, and you can either continue or cancel the action.</span></span>  
  
 <span data-ttu-id="001a9-116">**一般類別目錄**</span><span class="sxs-lookup"><span data-stu-id="001a9-116">**General Category**</span></span>  
 <span data-ttu-id="001a9-117">展開時會顯示 [資料行]  、[為主要]  和 [類型]  屬性欄位。</span><span class="sxs-lookup"><span data-stu-id="001a9-117">When expanded, shows the property fields for **Columns**, **Is Primary**, and **Type**.</span></span>  
  
 <span data-ttu-id="001a9-118">**資料行**</span><span class="sxs-lookup"><span data-stu-id="001a9-118">**Columns**</span></span>  
 <span data-ttu-id="001a9-119">顯示此索引依遞增順序排列。</span><span class="sxs-lookup"><span data-stu-id="001a9-119">Shows that this index is sorted in ascending order.</span></span>  
  
 <span data-ttu-id="001a9-120">**為主要**</span><span class="sxs-lookup"><span data-stu-id="001a9-120">**Is Primary**</span></span>  
 <span data-ttu-id="001a9-121">表示此索引是否為主要索引。</span><span class="sxs-lookup"><span data-stu-id="001a9-121">Indicates whether this is the primary index.</span></span> <span data-ttu-id="001a9-122">資料行上建立的第一個 XML 索引，將為其他索引的基礎。</span><span class="sxs-lookup"><span data-stu-id="001a9-122">The first XML index created on the column will be the basis of the others.</span></span>  
  
 <span data-ttu-id="001a9-123">**主要參考名稱**</span><span class="sxs-lookup"><span data-stu-id="001a9-123">**Primary reference name**</span></span>  
 <span data-ttu-id="001a9-124">顯示主要索引的名稱 (如果此索引為次要索引)。</span><span class="sxs-lookup"><span data-stu-id="001a9-124">Shows the name of the primary index if this is a secondary index.</span></span> <span data-ttu-id="001a9-125">只有在索引是次要索引時，才能使用這個選項。</span><span class="sxs-lookup"><span data-stu-id="001a9-125">Only available if this is a secondary index.</span></span>  
  
 <span data-ttu-id="001a9-126">**次要類型**</span><span class="sxs-lookup"><span data-stu-id="001a9-126">**Secondary type**</span></span>  
 <span data-ttu-id="001a9-127">顯示次要索引的類型。</span><span class="sxs-lookup"><span data-stu-id="001a9-127">Shows the type of secondary index.</span></span> <span data-ttu-id="001a9-128">只有在索引是次要索引時，才能使用這個選項。</span><span class="sxs-lookup"><span data-stu-id="001a9-128">Only available if this is a secondary index.</span></span>  
  
 <span data-ttu-id="001a9-129">**型別**</span><span class="sxs-lookup"><span data-stu-id="001a9-129">**Type**</span></span>  
 <span data-ttu-id="001a9-130">顯示此索引為 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="001a9-130">Shows that this is an XML index.</span></span>  
  
 <span data-ttu-id="001a9-131">**識別類別目錄**</span><span class="sxs-lookup"><span data-stu-id="001a9-131">**Identity Category**</span></span>  
 <span data-ttu-id="001a9-132">展開時會顯示 [名稱]  和 [描述]  屬性欄位。</span><span class="sxs-lookup"><span data-stu-id="001a9-132">When expanded, shows the **Name** and **Description** property fields.</span></span>  
  
 <span data-ttu-id="001a9-133">**名稱**</span><span class="sxs-lookup"><span data-stu-id="001a9-133">**Name**</span></span>  
 <span data-ttu-id="001a9-134">顯示 XML 索引的名稱。</span><span class="sxs-lookup"><span data-stu-id="001a9-134">Shows the name of the XML index.</span></span> <span data-ttu-id="001a9-135">在建立新索引時，會根據 [資料表設計師] 作用中視窗的資料表，給予預設的名稱。</span><span class="sxs-lookup"><span data-stu-id="001a9-135">When a new one is created, it is given a default name based on the table in the active window in Table Designer.</span></span> <span data-ttu-id="001a9-136">您可以隨時變更名稱。</span><span class="sxs-lookup"><span data-stu-id="001a9-136">You can change the name at any time.</span></span>  
  
 <span data-ttu-id="001a9-137">**說明**</span><span class="sxs-lookup"><span data-stu-id="001a9-137">**Description**</span></span>  
 <span data-ttu-id="001a9-138">描述索引。</span><span class="sxs-lookup"><span data-stu-id="001a9-138">Describe the index.</span></span> <span data-ttu-id="001a9-139">若要寫入更詳細的描述，請按一下 [描述]  ，然後按一下屬性欄位右邊出現的省略符號按鈕 ( **...** )。</span><span class="sxs-lookup"><span data-stu-id="001a9-139">To write a more detailed description, click **Description** and then click the ellipsis button (**...**) that appears to the right of the property field.</span></span> <span data-ttu-id="001a9-140">如此便可提供較大的區域以寫入文字。</span><span class="sxs-lookup"><span data-stu-id="001a9-140">This provides a larger area in which to write text.</span></span>  
  
 <span data-ttu-id="001a9-141">**資料表設計工具類別目錄**</span><span class="sxs-lookup"><span data-stu-id="001a9-141">**Table Designer Category**</span></span>  
 <span data-ttu-id="001a9-142">展開時會顯示此 XML 索引的屬性相關資訊。</span><span class="sxs-lookup"><span data-stu-id="001a9-142">When expanded, shows information about the properties of this XML index.</span></span>  
  
 <span data-ttu-id="001a9-143">**填滿規格**</span><span class="sxs-lookup"><span data-stu-id="001a9-143">**Fill Specification**</span></span>  
 <span data-ttu-id="001a9-144">展開時會顯示 [填滿因數]  \(Fill Factor) 和 [索引頁預留空間]  的資訊。</span><span class="sxs-lookup"><span data-stu-id="001a9-144">When expanded, shows information for **Fill Factor** and **Pad Index**.</span></span>  
  
 <span data-ttu-id="001a9-145">**填滿因數**</span><span class="sxs-lookup"><span data-stu-id="001a9-145">**Fill Factor**</span></span>  
 <span data-ttu-id="001a9-146">指定系統可以填滿的索引頁百分比。</span><span class="sxs-lookup"><span data-stu-id="001a9-146">Specify what percentage of the index page the system can fill.</span></span> <span data-ttu-id="001a9-147">當一頁填滿時，如果加入新資料，系統必須分割此頁，因此會降低效能。</span><span class="sxs-lookup"><span data-stu-id="001a9-147">Once a page is full, the system must split the page if new data is added, which impairs performance.</span></span>  
  
-   <span data-ttu-id="001a9-148">值 100 表示頁面已填滿，如此便需要最少的儲存空間，但也是最沒效率。</span><span class="sxs-lookup"><span data-stu-id="001a9-148">A value of 100 means the pages will be full; this requires the least amount of storage space but is the least efficient.</span></span> <span data-ttu-id="001a9-149">只有在資料未進行任何變更時 (例如，在唯讀的資料表上)，才應該使用此設定。</span><span class="sxs-lookup"><span data-stu-id="001a9-149">This setting should be used only when there will be no changes to the data, for example, on a read-only table.</span></span>  
  
-   <span data-ttu-id="001a9-150">較小的值會在資料頁中會留下較多空白空間，因此索引增加時就不需要分割資料頁。</span><span class="sxs-lookup"><span data-stu-id="001a9-150">A lower value leaves more empty space on the data pages, which reduces the need to split data pages as indexes grow.</span></span> <span data-ttu-id="001a9-151">不過會需要更多的儲存空間。</span><span class="sxs-lookup"><span data-stu-id="001a9-151">However, it requires more storage space.</span></span> <span data-ttu-id="001a9-152">此設定較適用於資料表內資料被變更的情況。</span><span class="sxs-lookup"><span data-stu-id="001a9-152">This setting is more appropriate when there will be changes to the data in the table.</span></span>  
  
 <span data-ttu-id="001a9-153">**索引頁預留空間**</span><span class="sxs-lookup"><span data-stu-id="001a9-153">**Pad Index**</span></span>  
 <span data-ttu-id="001a9-154">提供此索引中的頁面與 [填滿因數]  中所指定相同的空白空間 (填補) 百分比。</span><span class="sxs-lookup"><span data-stu-id="001a9-154">Provide pages in this index the same percentage of empty space (padding) that is specified in **Fill Factor**.</span></span>  
  
 <span data-ttu-id="001a9-155">**是停用的**</span><span class="sxs-lookup"><span data-stu-id="001a9-155">**Is Disabled**</span></span>  
 <span data-ttu-id="001a9-156">指定此索引是否停用。</span><span class="sxs-lookup"><span data-stu-id="001a9-156">Specify whether this index is disabled.</span></span> <span data-ttu-id="001a9-157">停用的索引不支援搜尋功能，而且新項目加入資料表時也不會更新停用的索引。</span><span class="sxs-lookup"><span data-stu-id="001a9-157">Disabled indexes do not support searches, nor do they get updated when new items are added to the table.</span></span> <span data-ttu-id="001a9-158">您可以停用索引，提升大量插入與更新的效能。</span><span class="sxs-lookup"><span data-stu-id="001a9-158">You can improve performance for bulk inserts and updates by disabling an index.</span></span>  
  
 <span data-ttu-id="001a9-159">**允許頁面鎖定**</span><span class="sxs-lookup"><span data-stu-id="001a9-159">**Page Locks Allowed**</span></span>  
 <span data-ttu-id="001a9-160">指定是否在此索引中允許頁面層級的鎖定。</span><span class="sxs-lookup"><span data-stu-id="001a9-160">Specify whether page-level locking is allowed on this index.</span></span> <span data-ttu-id="001a9-161">允許或不允許頁面層級的鎖定會影響資料庫效能。</span><span class="sxs-lookup"><span data-stu-id="001a9-161">Allowing or disallowing page-level locking affects database performance.</span></span>  
  
 <span data-ttu-id="001a9-162">**重新計算統計資料**</span><span class="sxs-lookup"><span data-stu-id="001a9-162">**Re-compute Statistics**</span></span>  
 <span data-ttu-id="001a9-163">建立索引時計算新的統計資料。</span><span class="sxs-lookup"><span data-stu-id="001a9-163">Compute new statistics when the index is created.</span></span> <span data-ttu-id="001a9-164">重新計算統計資料會減緩索引的建置，但是通常會提升查詢效能。</span><span class="sxs-lookup"><span data-stu-id="001a9-164">Re-computing statistics slows the building of indexes but usually improves query performance.</span></span>  
  
 <span data-ttu-id="001a9-165">**允許資料列鎖定**</span><span class="sxs-lookup"><span data-stu-id="001a9-165">**Row Locks Allowed**</span></span>  
 <span data-ttu-id="001a9-166">指定是否在此索引中允許資料列層級的鎖定。</span><span class="sxs-lookup"><span data-stu-id="001a9-166">Specify whether row-level locking is allowed on this index.</span></span> <span data-ttu-id="001a9-167">允許或不允許資料列層級的鎖定會影響資料庫效能。</span><span class="sxs-lookup"><span data-stu-id="001a9-167">Allowing or disallowing row-level locking affects database performance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="001a9-168">另請參閱</span><span class="sxs-lookup"><span data-stu-id="001a9-168">See Also</span></span>  
 [<span data-ttu-id="001a9-169">建立 XML 索引</span><span class="sxs-lookup"><span data-stu-id="001a9-169">Create XML Indexes</span></span>](../../relational-databases/xml/create-xml-indexes.md)  
  
  
