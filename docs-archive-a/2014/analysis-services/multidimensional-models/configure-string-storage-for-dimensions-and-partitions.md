---
title: 設定維度和資料分割的字串儲存 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 987f6cfc-da82-4b2e-96ef-a8af88339e5f
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2817af382599d4495dddbd8951a72a47629cf824
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705646"
---
# <a name="configure-string-storage-for-dimensions-and-partitions"></a><span data-ttu-id="1f59c-102">設定維度及分割區的字串存放區</span><span class="sxs-lookup"><span data-stu-id="1f59c-102">Configure String Storage for Dimensions and Partitions</span></span>
  <span data-ttu-id="1f59c-103">您可以重新設定字串存放區，在超出字串存放區之 4 GB 檔案大小限制的維度屬性或分割區中容納非常大的字串。</span><span class="sxs-lookup"><span data-stu-id="1f59c-103">You can reconfigure string storage to accommodate very large strings in dimension attributes or partitions that exceed the 4 GB file size limit for string stores.</span></span> <span data-ttu-id="1f59c-104">如果您的維度或資料分割包含此大小的字串存放區，您可以在維度或資料分割層級，變更本機及連結 (本機或遠端) 物件的 **StringStoresCompatibilityLevel** 屬性來解決檔案大小限制。</span><span class="sxs-lookup"><span data-stu-id="1f59c-104">If your dimensions or partitions include string stores of this size, you can work around the file size constraint by changing the **StringStoresCompatibilityLevel** property at the dimension or partition level, for local as well as linked (local or remote) objects.</span></span>  
  
 <span data-ttu-id="1f59c-105">請注意您可以只在需要額外容量的物件上加大字串存放區。</span><span class="sxs-lookup"><span data-stu-id="1f59c-105">Note that you can increase string storage on just those objects that require additional capacity.</span></span> <span data-ttu-id="1f59c-106">在大部分的維度模型中，字串資料會與維度相關聯。</span><span class="sxs-lookup"><span data-stu-id="1f59c-106">In most multidimensional models, string data is associated with dimensions.</span></span> <span data-ttu-id="1f59c-107">但包分割區中最上層的字串若包含相異計數量值，也可以受益於此設定。</span><span class="sxs-lookup"><span data-stu-id="1f59c-107">However, partitions that contain distinct count measures on top of strings can also benefit from this setting.</span></span> <span data-ttu-id="1f59c-108">因為此設定係針對字串，所以數值資料不受影響。</span><span class="sxs-lookup"><span data-stu-id="1f59c-108">Because the setting is for strings, numeric data is unaffected.</span></span>  
  
 <span data-ttu-id="1f59c-109">這個屬性的有效值包括：</span><span class="sxs-lookup"><span data-stu-id="1f59c-109">Valid values for this property include the following:</span></span>  
  
|<span data-ttu-id="1f59c-110">值</span><span class="sxs-lookup"><span data-stu-id="1f59c-110">Value</span></span>|<span data-ttu-id="1f59c-111">描述</span><span class="sxs-lookup"><span data-stu-id="1f59c-111">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1f59c-112">**1050**</span><span class="sxs-lookup"><span data-stu-id="1f59c-112">**1050**</span></span>|<span data-ttu-id="1f59c-113">指定每個存放區 4 GB 檔案大小上限的預設字串存放區架構。</span><span class="sxs-lookup"><span data-stu-id="1f59c-113">Specifies the default string storage architecture, subject to a 4 GB maximum file size per store.</span></span>|  
|<span data-ttu-id="1f59c-114">**1100**</span><span class="sxs-lookup"><span data-stu-id="1f59c-114">**1100**</span></span>|<span data-ttu-id="1f59c-115">指定較大的字串存放區，每個存放區最多支援 40 億個唯一字串。</span><span class="sxs-lookup"><span data-stu-id="1f59c-115">Specifies larger string storage, supports up to 4 billion unique strings per store.</span></span>|  
  
> [!IMPORTANT]  
>  <span data-ttu-id="1f59c-116">變更物件的字串存放區設定需要您重新處理物件本身以及任何相依物件。</span><span class="sxs-lookup"><span data-stu-id="1f59c-116">Changing the string storage settings of an object requires that you reprocess the object itself and any dependent object.</span></span> <span data-ttu-id="1f59c-117">完成此程序需要進行處理。</span><span class="sxs-lookup"><span data-stu-id="1f59c-117">Processing is required to complete the procedure.</span></span>  
  
 <span data-ttu-id="1f59c-118">本主題包含下列幾節：</span><span class="sxs-lookup"><span data-stu-id="1f59c-118">This topic contains the following sections:</span></span>  
  
-   [<span data-ttu-id="1f59c-119">關於字串存放</span><span class="sxs-lookup"><span data-stu-id="1f59c-119">About String Stores</span></span>](#bkmk_background)  
  
-   [<span data-ttu-id="1f59c-120">先決條件</span><span class="sxs-lookup"><span data-stu-id="1f59c-120">Prerequisites</span></span>](#bkmk_prereq)  
  
-   [<span data-ttu-id="1f59c-121">步驟 1：在 SQL Server Data Tools 中設定 StringStoreCompatiblityLevel 屬性</span><span class="sxs-lookup"><span data-stu-id="1f59c-121">Step 1: Set the StringStoreCompatiblityLevel Property in SQL Server Data Tools</span></span>](#bkmk_step1)  
  
-   [<span data-ttu-id="1f59c-122">步驟 2：處理物件</span><span class="sxs-lookup"><span data-stu-id="1f59c-122">Step 2: Process the Objects</span></span>](#bkmk_step2)  
  
##  <a name="about-string-stores"></a><a name="bkmk_background"></a><span data-ttu-id="1f59c-123">關於字串存放區</span><span class="sxs-lookup"><span data-stu-id="1f59c-123">About String Stores</span></span>  
 <span data-ttu-id="1f59c-124">字串存放區組態為選擇性，亦即，即使您建立新的資料庫，也會使用預設字串存放區架構 (檔案大小上限為 4 GB)。</span><span class="sxs-lookup"><span data-stu-id="1f59c-124">String storage configuration is optional, which means that even new databases that you create use the default string store architecture that is subject to the 4 GB maximum file size.</span></span> <span data-ttu-id="1f59c-125">使用較大的字串存放區架構對效能的影響雖然小但也顯著。</span><span class="sxs-lookup"><span data-stu-id="1f59c-125">Using the larger string storage architecture has a small but noticeable impact on performance.</span></span> <span data-ttu-id="1f59c-126">只有在您的字串存放區檔案接近或達到最大 4 GB 限制時，才使用它。</span><span class="sxs-lookup"><span data-stu-id="1f59c-126">You should use it only if your string storage files are close to or at the maximum 4 GB limit.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1f59c-127">這個設定不適用於資料採礦模型。</span><span class="sxs-lookup"><span data-stu-id="1f59c-127">This setting does not apply to data mining models.</span></span> <span data-ttu-id="1f59c-128">目前，包含資料採礦結構的模型仍然可能會有 GB 檔案大小限制。</span><span class="sxs-lookup"><span data-stu-id="1f59c-128">Currently, it is still possible to encounter the GB file size limitation on models containing data mining structures.</span></span>  
  
 <span data-ttu-id="1f59c-129">在 Analysis Services 多維度資料庫中，字串與數值資料分開存放，以便根據資料的特性進行最佳化。</span><span class="sxs-lookup"><span data-stu-id="1f59c-129">In an Analysis Services multidimensional database, strings are stored separately from numeric data to allow for optimizations based on characteristics of the data.</span></span> <span data-ttu-id="1f59c-130">字串資料通常會在表示名稱或描述的維度屬性中找到。</span><span class="sxs-lookup"><span data-stu-id="1f59c-130">String data is typically found in dimension attributes that represent names or descriptions.</span></span> <span data-ttu-id="1f59c-131">字串資料也可以為在相異計數量值中。</span><span class="sxs-lookup"><span data-stu-id="1f59c-131">It is also possible to have string data in distinct count measures.</span></span> <span data-ttu-id="1f59c-132">字串資料也可以用於索引鍵。</span><span class="sxs-lookup"><span data-stu-id="1f59c-132">String data can also be used in keys.</span></span>  
  
 <span data-ttu-id="1f59c-133">您可以依字串存放的副檔名識別字串存放 (例如 asstore、.bstore、.ksstore 或 .string 檔)。</span><span class="sxs-lookup"><span data-stu-id="1f59c-133">You can identify a string store by its file extension (for example, asstore, .bstore, .ksstore, or .string files).</span></span> <span data-ttu-id="1f59c-134">根據預設，這些檔案中的每一個都遵從最大 4 GB 的限制。</span><span class="sxs-lookup"><span data-stu-id="1f59c-134">By default, each of these files is subject to a maximum 4 GB limit.</span></span> <span data-ttu-id="1f59c-135">在 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]中，您可以指定允許字串存放區依需要成長的替代儲存機制，來覆寫檔案大小上限。</span><span class="sxs-lookup"><span data-stu-id="1f59c-135">In [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], you can override the maximum file size by specifying an alternative storage mechanism that allows a string store to grow as needed.</span></span>  
  
 <span data-ttu-id="1f59c-136">與限制實體檔案大小的預設字串存放區架構相比，較大的字串存放區是以字串數目上限為基礎。</span><span class="sxs-lookup"><span data-stu-id="1f59c-136">In contrast with the default string storage architecture which limits the size of the physical file, larger string storage is based on a maximum number of strings.</span></span> <span data-ttu-id="1f59c-137">較大的字串存放區的最大限制為 40 億個唯一字串，或 40 億筆記錄，以先發生者為準。</span><span class="sxs-lookup"><span data-stu-id="1f59c-137">The maximum limit for larger string storage is 4 billion unique strings or 4 billion records, whichever occurs first.</span></span> <span data-ttu-id="1f59c-138">較大的字串存放區會針對偶數大小建立記錄，其中每筆記錄等於 64K 的頁面。</span><span class="sxs-lookup"><span data-stu-id="1f59c-138">Larger string storage creates records of an even size, where each record is equal to a 64K page.</span></span> <span data-ttu-id="1f59c-139">如果您有非常長，而且無法納入單一記錄的字串，則有效限制將少於 40 億個字串。</span><span class="sxs-lookup"><span data-stu-id="1f59c-139">If you have very long strings that do not fit in a single record, your effective limit will be less than 4 billion strings.</span></span>  
  
##  <a name="prerequisites"></a><a name="bkmk_prereq"></a> <span data-ttu-id="1f59c-140">必要條件</span><span class="sxs-lookup"><span data-stu-id="1f59c-140">Prerequisites</span></span>  
 <span data-ttu-id="1f59c-141">您也必須有 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 或更新版的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="1f59c-141">You must have a [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] or later version of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="1f59c-142">維度和分割區必須使用 MOLAP 儲存。</span><span class="sxs-lookup"><span data-stu-id="1f59c-142">Dimensions and partitions must use MOLAP storage.</span></span>  
  
 <span data-ttu-id="1f59c-143">資料庫相容性層級必須設定為 1100。</span><span class="sxs-lookup"><span data-stu-id="1f59c-143">The database compatibility level must be set to 1100.</span></span> <span data-ttu-id="1f59c-144">如果您使用 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] 和 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 或更新版的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]建立或部署資料庫，則資料庫相容性層級已經設定為 1100。</span><span class="sxs-lookup"><span data-stu-id="1f59c-144">If you created or deployed a database using [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] and the [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] or later version of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], the database compatibility level is already set to 1100.</span></span> <span data-ttu-id="1f59c-145">如果您將使用舊版 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 建立的資料庫移到 ssSQL11 或更新版本，必須更新相容性層級。</span><span class="sxs-lookup"><span data-stu-id="1f59c-145">If you moved a database created in an earlier version of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] to ssSQL11 or later, you must update the compatibility level.</span></span> <span data-ttu-id="1f59c-146">如果是移動但未重新部署的資料庫，您可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 設定相容性層級。</span><span class="sxs-lookup"><span data-stu-id="1f59c-146">For databases that you are moving, but not redeploying, you can use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to set the compatibility level.</span></span> <span data-ttu-id="1f59c-147">如需詳細資訊，請參閱[將多維度資料庫的相容性層級設定 &#40;Analysis Services&#41;](compatibility-level-of-a-multidimensional-database-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="1f59c-147">For more information, see [Set the Compatibility Level of a Multidimensional Database &#40;Analysis Services&#41;](compatibility-level-of-a-multidimensional-database-analysis-services.md).</span></span>  
  
##  <a name="step-1-set-the-stringstorecompatiblitylevel-property-in-sql-server-data-tools"></a><a name="bkmk_step1"></a><span data-ttu-id="1f59c-148">步驟1：在 SQL Server Data Tools 中設定 StringStoreCompatiblityLevel 屬性</span><span class="sxs-lookup"><span data-stu-id="1f59c-148">Step 1: Set the StringStoreCompatiblityLevel Property in SQL Server Data Tools</span></span>  
  
1.  <span data-ttu-id="1f59c-149">使用 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]開啟包含您要修改之維度或資料分割的專案。</span><span class="sxs-lookup"><span data-stu-id="1f59c-149">Using [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the project that contains the dimensions or partitions you want to modify.</span></span>  
  
2.  <span data-ttu-id="1f59c-150">若要變更維度的字串存放區，請開啟 [方案總管]。</span><span class="sxs-lookup"><span data-stu-id="1f59c-150">To change the string storage for dimensions, open Solution Explorer.</span></span> <span data-ttu-id="1f59c-151">按兩下要修改其字串存放區的維度。</span><span class="sxs-lookup"><span data-stu-id="1f59c-151">Double-click the dimension for which you are modifying string storage.</span></span>  
  
3.  <span data-ttu-id="1f59c-152">在 [維度設計師] 的 [屬性] 窗格中，確認已選取維度的父節點 (例如，如果維度是 Customers，選取 Customers 而不是其中一個子屬性)。</span><span class="sxs-lookup"><span data-stu-id="1f59c-152">In Dimension Designer, in the Attributes pane, make sure that the parent node of the dimension is selected (for example, if the dimension is Customers, select Customers and not one of the child attributes).</span></span>  
  
4.  <span data-ttu-id="1f59c-153">在 [屬性] 窗格的 [進階] 區段中，將 **StringStoresCompatibilityLevel** 設定為 **1100**。</span><span class="sxs-lookup"><span data-stu-id="1f59c-153">In the Properties pane, in the Advanced section, set **StringStoresCompatibilityLevel** to **1100**.</span></span> <span data-ttu-id="1f59c-154">針對需要較大儲存體的其他維度重複此作業，否則請將其餘維度保持在值 **1050** 。</span><span class="sxs-lookup"><span data-stu-id="1f59c-154">Repeat for other dimensions that require larger storage, otherwise leave the remaining dimensions at the **1050** value.</span></span>  
  
5.  <span data-ttu-id="1f59c-155">針對分割區，從 [方案總管] 開啟 Cube。</span><span class="sxs-lookup"><span data-stu-id="1f59c-155">For partitions, open a cube from Solution Explorer.</span></span>  
  
6.  <span data-ttu-id="1f59c-156">按一下 [分割區] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="1f59c-156">Click the Partitions tab.</span></span>  
  
7.  <span data-ttu-id="1f59c-157">展開資料分割，選取需要額外儲存容量的資料分割，然後修改 **StringStoresCompatibilityLevel** 屬性。</span><span class="sxs-lookup"><span data-stu-id="1f59c-157">Expand the partition, select the partition that requires extra storage capacity, and then modify the **StringStoresCompatibilityLevel** property.</span></span>  
  
8.  <span data-ttu-id="1f59c-158">儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="1f59c-158">Save the file.</span></span>  
  
##  <a name="step-2-process-the-objects"></a><a name="bkmk_step2"></a><span data-ttu-id="1f59c-159">步驟2：處理物件</span><span class="sxs-lookup"><span data-stu-id="1f59c-159">Step 2: Process the Objects</span></span>  
 <span data-ttu-id="1f59c-160">處理物件之後，將會使用新的儲存體架構。</span><span class="sxs-lookup"><span data-stu-id="1f59c-160">The new storage architecture will be used after you process the objects.</span></span> <span data-ttu-id="1f59c-161">處理物件也會證明您已經成功解決儲存限制問題，因為先前回報字串存放溢位情況的錯誤應該不會再發生。</span><span class="sxs-lookup"><span data-stu-id="1f59c-161">Processing objects also proves you have successfully resolved storage constraint problem because the error that previously reported a string store overflow condition should no longer occur.</span></span>  
  
-   <span data-ttu-id="1f59c-162">在方案總管中，以滑鼠右鍵按一下您剛修改的維度，然後選取 [處理]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1f59c-162">In Solution Explorer, right-click the dimension or you just modified and select **Process**.</span></span>  
  
 <span data-ttu-id="1f59c-163">您必須針對即將使用新字串存放架構的每個物件，使用 [完整處理] 選項。</span><span class="sxs-lookup"><span data-stu-id="1f59c-163">You must use the Process Full option on each object that is using the new string store architecture.</span></span> <span data-ttu-id="1f59c-164">在處理之前，請務必針對維度執行影響分析，以確認相依物件是否也需要處理。</span><span class="sxs-lookup"><span data-stu-id="1f59c-164">Before processing, be sure to run an impact analysis on the dimension to check whether dependent objects also require reprocessing.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f59c-165">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1f59c-165">See Also</span></span>  
 <span data-ttu-id="1f59c-166">[處理 &#40;Analysis Services&#41;的工具和方法](tools-and-approaches-for-processing-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="1f59c-166">[Tools and Approaches for Processing &#40;Analysis Services&#41;](tools-and-approaches-for-processing-analysis-services.md) </span></span>  
 <span data-ttu-id="1f59c-167">[處理選項和設定 &#40;Analysis Services&#41;](processing-options-and-settings-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="1f59c-167">[Processing Options and Settings &#40;Analysis Services&#41;](processing-options-and-settings-analysis-services.md) </span></span>  
 <span data-ttu-id="1f59c-168">[分割區儲存模式和處理](../multidimensional-models-olap-logical-cube-objects/partitions-partition-storage-modes-and-processing.md) </span><span class="sxs-lookup"><span data-stu-id="1f59c-168">[Partition Storage Modes and Processing](../multidimensional-models-olap-logical-cube-objects/partitions-partition-storage-modes-and-processing.md) </span></span>  
 [<span data-ttu-id="1f59c-169">維度儲存</span><span class="sxs-lookup"><span data-stu-id="1f59c-169">Dimension Storage</span></span>](../multidimensional-models-olap-logical-dimension-objects/dimensions-storage.md)  
  
  
