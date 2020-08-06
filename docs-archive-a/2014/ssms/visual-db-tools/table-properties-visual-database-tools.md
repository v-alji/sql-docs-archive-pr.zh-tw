---
title: 資料表屬性 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.tabledesigner
- vdt.designers.properties.Table
ms.assetid: cc392987-1aab-45f5-b5af-a26be53409bf
author: stevestein
ms.author: sstein
ms.openlocfilehash: df4a0332ebc622b069c468e51c461b7cba20aa36
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704609"
---
# <a name="table-properties-visual-database-tools"></a><span data-ttu-id="846a1-102">資料表屬性 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="846a1-102">Table Properties (Visual Database Tools)</span></span>
  <span data-ttu-id="846a1-103">當您在 [資料表設計師] 中按一下滑鼠右鍵並選取 [屬性] 時，這些屬性便會出現在 [屬性] 視窗中。</span><span class="sxs-lookup"><span data-stu-id="846a1-103">These properties appear in the Properties window when you right click in Table Designer and select Properties.</span></span> <span data-ttu-id="846a1-104">已選取資料表時，您可以在 [屬性] 視窗中編輯這些屬性 (除非另有附註)。</span><span class="sxs-lookup"><span data-stu-id="846a1-104">Unless otherwise noted, you can edit these properties in the Properties window when the table is selected.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="846a1-105">如果資料表是要發佈以進行複寫，則必須使用 Transact-SQL 陳述式 [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) 或 SQL Server 管理物件 (SMO) 變更結構描述。</span><span class="sxs-lookup"><span data-stu-id="846a1-105">If the table is published for replication, you must make schema changes using the Transact-SQL statement [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) or SQL Server Management Objects (SMO).</span></span> <span data-ttu-id="846a1-106">使用 [資料表設計工具] 或 [資料庫圖表設計工具] 變更結構描述時，會嘗試卸除並重新建立資料表。</span><span class="sxs-lookup"><span data-stu-id="846a1-106">When schema changes are made using the Table Designer or the Database Diagram Designer, it attempts to drop and recreate the table.</span></span> <span data-ttu-id="846a1-107">您無法卸除已發行的物件，因此結構描述變更將會失敗。</span><span class="sxs-lookup"><span data-stu-id="846a1-107">You cannot drop published objects, therefore the schema change will fail.</span></span>  
  
## <a name="show-table-properties-in-table-designer"></a><span data-ttu-id="846a1-108">在資料表設計師中顯示資料表屬性</span><span class="sxs-lookup"><span data-stu-id="846a1-108">Show Table Properties in Table Designer</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="846a1-109">此主題中的屬性，是依類別目錄的順序排列，而非依字母排列。</span><span class="sxs-lookup"><span data-stu-id="846a1-109">The properties in this topic are ordered by category rather than alphabet.</span></span>  
  
 <span data-ttu-id="846a1-110">**識別類別目錄**</span><span class="sxs-lookup"><span data-stu-id="846a1-110">**Identity Category**</span></span>  
 <span data-ttu-id="846a1-111">展開以顯示 **名稱**、 **說明**及 **結構描述**的屬性。</span><span class="sxs-lookup"><span data-stu-id="846a1-111">Expands to show properties for **Name**, **Description**, and **Schema**.</span></span>  
  
 <span data-ttu-id="846a1-112">**名稱**</span><span class="sxs-lookup"><span data-stu-id="846a1-112">**Name**</span></span>  
 <span data-ttu-id="846a1-113">顯示資料表的名稱。</span><span class="sxs-lookup"><span data-stu-id="846a1-113">Displays the name of the table.</span></span> <span data-ttu-id="846a1-114">若要編輯名稱，請在文字方塊中輸入。</span><span class="sxs-lookup"><span data-stu-id="846a1-114">To edit the name, type in the text box.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="846a1-115">如果現有的查詢、檢視、使用者自訂函數、預存程序或程式參考此資料表，則名稱修改將使這些物件失效。</span><span class="sxs-lookup"><span data-stu-id="846a1-115">If existing queries, views, user-defined functions, stored procedures, or programs refer to the table, the name modification will make these objects invalid.</span></span>  
  
 <span data-ttu-id="846a1-116">**Database Name**</span><span class="sxs-lookup"><span data-stu-id="846a1-116">**Database Name**</span></span>  
 <span data-ttu-id="846a1-117">顯示選取資料表的資料來源名稱。</span><span class="sxs-lookup"><span data-stu-id="846a1-117">Shows the name of the data source of the selected table.</span></span>  
  
 <span data-ttu-id="846a1-118">**說明**</span><span class="sxs-lookup"><span data-stu-id="846a1-118">**Description**</span></span>  
 <span data-ttu-id="846a1-119">顯示選取資料表的描述。</span><span class="sxs-lookup"><span data-stu-id="846a1-119">Shows a description of the selected table.</span></span> <span data-ttu-id="846a1-120">若要查看或編輯整個描述，請按一下 [描述]，然後按一下屬性右側的省略符號 **(...)** 。</span><span class="sxs-lookup"><span data-stu-id="846a1-120">To see the entire description, or to edit it, click the description and then click the ellipses **(...)** to the right of the property.</span></span>  
  
 <span data-ttu-id="846a1-121">**結構描述**</span><span class="sxs-lookup"><span data-stu-id="846a1-121">**Schema**</span></span>  
 <span data-ttu-id="846a1-122">顯示此資料表所屬結構描述的名稱</span><span class="sxs-lookup"><span data-stu-id="846a1-122">Shows the name of the schema to which this table belongs.</span></span> <span data-ttu-id="846a1-123">(只適用於 Microsoft SQL Server)。</span><span class="sxs-lookup"><span data-stu-id="846a1-123">(Applies only to Microsoft SQL Server.)</span></span>  
  
 <span data-ttu-id="846a1-124">**伺服器名稱**</span><span class="sxs-lookup"><span data-stu-id="846a1-124">**Server Name**</span></span>  
 <span data-ttu-id="846a1-125">顯示資料來源的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="846a1-125">Shows the name of the server for the data source.</span></span>  
  
 <span data-ttu-id="846a1-126">**資料表設計工具類別目錄**</span><span class="sxs-lookup"><span data-stu-id="846a1-126">**Table Designer Category**</span></span>  
 <span data-ttu-id="846a1-127">展開以顯示 **Identity Column**、 **Is Indexable**及 **Is Replicated**的屬性。</span><span class="sxs-lookup"><span data-stu-id="846a1-127">Expands to show properties for **Identity Column**, **Is Indexable**, and **Is Replicated**.</span></span>  
  
 <span data-ttu-id="846a1-128">**Identity Column**</span><span class="sxs-lookup"><span data-stu-id="846a1-128">**Identity Column**</span></span>  
 <span data-ttu-id="846a1-129">顯示做為資料表識別欄位的資料行。</span><span class="sxs-lookup"><span data-stu-id="846a1-129">Shows the column used as the table's identity column.</span></span> <span data-ttu-id="846a1-130">若要變更識別欄位，請從下拉式清單中選擇。</span><span class="sxs-lookup"><span data-stu-id="846a1-130">To change the identity column, choose from the drop-down list.</span></span> <span data-ttu-id="846a1-131">清單中只會顯示數字資料類型的資料行。</span><span class="sxs-lookup"><span data-stu-id="846a1-131">Only columns of a numeric data type will show in the list.</span></span>  
  
 <span data-ttu-id="846a1-132">**為可編索引**</span><span class="sxs-lookup"><span data-stu-id="846a1-132">**Is Indexable**</span></span>  
 <span data-ttu-id="846a1-133">顯示是否可對資料表進行索引。</span><span class="sxs-lookup"><span data-stu-id="846a1-133">Shows whether the table can be indexed.</span></span> <span data-ttu-id="846a1-134">如果資料表不可索引，可能是因為您不是資料表擁有人，或是因為資料表包含具有 text、ntext 或 image 等資料類型的資料行。</span><span class="sxs-lookup"><span data-stu-id="846a1-134">If the table is not indexable it may be because you are not the table owner or because the table contains columns with data types of text, ntext, or image.</span></span>  
  
 <span data-ttu-id="846a1-135">**為已複寫**</span><span class="sxs-lookup"><span data-stu-id="846a1-135">**Is Replicated**</span></span>  
 <span data-ttu-id="846a1-136">顯示是否已在其他位置複寫資料表。</span><span class="sxs-lookup"><span data-stu-id="846a1-136">Shows whether the table is replicated in another location.</span></span>  
  
 <span data-ttu-id="846a1-137">**規則資料空間規格分類**</span><span class="sxs-lookup"><span data-stu-id="846a1-137">**Regular Data Space Specification Category**</span></span>  
 <span data-ttu-id="846a1-138">展開以顯示 **(資料空間類型)** 、 **檔案群組或資料分割配置名稱**及 **資料分割資料行清單**的屬性。</span><span class="sxs-lookup"><span data-stu-id="846a1-138">Expands to show properties for **(Data Space Type)**, **Filegroup or Partition Scheme Name**, and **Partition Column List**.</span></span>  
  
 <span data-ttu-id="846a1-139">**(資料空間類型)**</span><span class="sxs-lookup"><span data-stu-id="846a1-139">**(Data Space Type)**</span></span>  
 <span data-ttu-id="846a1-140">顯示此資料表是否使用檔案群組或資料分割配置加以儲存。</span><span class="sxs-lookup"><span data-stu-id="846a1-140">Shows whether this table is stored using a filegroup or partition scheme.</span></span>  
  
 <span data-ttu-id="846a1-141">**檔案群組或資料分割配置名稱**</span><span class="sxs-lookup"><span data-stu-id="846a1-141">**Filegroup or Partition Scheme Name**</span></span>  
 <span data-ttu-id="846a1-142">顯示檔案群組或資料分割配置的名稱。</span><span class="sxs-lookup"><span data-stu-id="846a1-142">Shows the name of the filegroup or partition scheme.</span></span>  
  
 <span data-ttu-id="846a1-143">**資料分割資料行清單**</span><span class="sxs-lookup"><span data-stu-id="846a1-143">**Partition Column List**</span></span>  
 <span data-ttu-id="846a1-144">提供 **資料分割資料行清單** 的存取權。</span><span class="sxs-lookup"><span data-stu-id="846a1-144">Provides access to the **Partition Column List** dialog box.</span></span>  
  
 <span data-ttu-id="846a1-145">**資料列 GUID 資料行**</span><span class="sxs-lookup"><span data-stu-id="846a1-145">**Row GUID Column**</span></span>  
 <span data-ttu-id="846a1-146">顯示 Microsoft SQL Server 用來做為資料表之 ROWGUID 資料行的資料行。</span><span class="sxs-lookup"><span data-stu-id="846a1-146">Shows the column used by Microsoft SQL Server as the table's ROWGUID column.</span></span> <span data-ttu-id="846a1-147">若要變更 ROWGUID 資料列，請從下拉式清單中選擇</span><span class="sxs-lookup"><span data-stu-id="846a1-147">To change the ROWGUID column, choose from the drop-down list.</span></span> <span data-ttu-id="846a1-148">(只適用於 SQL Server 7.0 (含) 以後版本)。</span><span class="sxs-lookup"><span data-stu-id="846a1-148">(Applies only to SQL Server 7.0 or higher.)</span></span>  
  
 <span data-ttu-id="846a1-149">**Text/Image 檔案群組**</span><span class="sxs-lookup"><span data-stu-id="846a1-149">**Text/Image Filegroup**</span></span>  
 <span data-ttu-id="846a1-150">提供下拉式清單，供您選擇具有 text 或 image 資料類型之資料行的檔案群組。</span><span class="sxs-lookup"><span data-stu-id="846a1-150">Provides a drop-down list from which you can choose the filegroup for columns that have text or image data types.</span></span> <span data-ttu-id="846a1-151">如果資料表是以資料分割配置加以儲存，請將此欄位留白。</span><span class="sxs-lookup"><span data-stu-id="846a1-151">If the table is stored using a partition scheme, leave this field blank.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="846a1-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="846a1-152">See Also</span></span>  
 [<span data-ttu-id="846a1-153">設計資料表 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="846a1-153">Design Tables &#40;Visual Database Tools&#41;</span></span>](visual-database-tools.md)  
  
  
