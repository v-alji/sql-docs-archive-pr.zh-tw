---
title: 將多維度資料庫的相容性層級設定 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 978279e6-a581-4184-af9d-8701b9826a89
author: minewiskan
ms.author: owend
ms.openlocfilehash: eea3d522abc5133e759cf476f3b169fd570b196f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705657"
---
# <a name="set-the-compatibility-level-of-a-multidimensional-database-analysis-services"></a><span data-ttu-id="a6c70-102">設定多維度資料庫的相容性層級 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="a6c70-102">Set the Compatibility Level of a Multidimensional Database (Analysis Services)</span></span>
  <span data-ttu-id="a6c70-103">在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]中，資料庫相容性層級屬性會決定資料庫的功能層級。</span><span class="sxs-lookup"><span data-stu-id="a6c70-103">In [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], the database compatibility level property determines the functional level of a database.</span></span> <span data-ttu-id="a6c70-104">每個模型類型都有唯一的相容性層級。</span><span class="sxs-lookup"><span data-stu-id="a6c70-104">Compatibility levels are unique to each model type.</span></span> <span data-ttu-id="a6c70-105">例如，的相容性層級 `1100` 根據資料庫是多維度或表格式而有不同的意義。</span><span class="sxs-lookup"><span data-stu-id="a6c70-105">For example, a compatibility level of `1100` has a different meaning depending on whether the database is multidimensional or tabular.</span></span>  
  
 <span data-ttu-id="a6c70-106">本主題描述只適用於多維度資料庫的相容性層級。</span><span class="sxs-lookup"><span data-stu-id="a6c70-106">This topic describes compatibility level for multidimensional databases only.</span></span> <span data-ttu-id="a6c70-107">如需表格式方案的詳細資訊，請參閱[&#40;SSAS 表格式 SP1&#41;的相容性層級](../tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="a6c70-107">For more information about tabular solutions, see [Compatibility Level &#40;SSAS Tabular SP1&#41;](../tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a6c70-108">表格式模型具有另外的資料庫相容性層級，並不適用於多維度模型。</span><span class="sxs-lookup"><span data-stu-id="a6c70-108">Tabular models have additional database compatibility levels that are not applicable to multidimensional models.</span></span> <span data-ttu-id="a6c70-109">多維度模型不存在相容性層級 `1103`。</span><span class="sxs-lookup"><span data-stu-id="a6c70-109">Compatibility level `1103` does not exist for multidimensional models.</span></span> <span data-ttu-id="a6c70-110">如需表格式方案的詳細資訊，請參閱[SQL Server 2012 SP1 和相容性層級中的表格式模型的新功能](https://go.microsoft.com/fwlink/?LinkId=301727) `1103` 。</span><span class="sxs-lookup"><span data-stu-id="a6c70-110">See [What is new for the Tabular model in SQL Server 2012 SP1 and compatibility level](https://go.microsoft.com/fwlink/?LinkId=301727) for more information about `1103` for tabular solutions.</span></span>  
  
 <span data-ttu-id="a6c70-111">**多維度資料庫的相容性層級**</span><span class="sxs-lookup"><span data-stu-id="a6c70-111">**Compatibility Levels for multidimensional databases**</span></span>  
  
 <span data-ttu-id="a6c70-112">目前唯一會隨功能層級而改變的多維度資料庫行為就是字串儲存體架構。</span><span class="sxs-lookup"><span data-stu-id="a6c70-112">Currently, the only multidimensional database behavior that varies by functional level is string storage architecture.</span></span> <span data-ttu-id="a6c70-113">經由提高資料庫的相容性層級，您可以覆寫量值和維度的 4 GB 字串儲存體上限。</span><span class="sxs-lookup"><span data-stu-id="a6c70-113">By raising the database compatibility level, you can override the 4 gigabyte maximum limit for string storage of measures and dimensions.</span></span>  
  
 <span data-ttu-id="a6c70-114">對於多維度資料庫，`CompatibilityLevel` 屬性的有效值包括：</span><span class="sxs-lookup"><span data-stu-id="a6c70-114">For a multidimensional database, valid values for the `CompatibilityLevel` property include the following:</span></span>  
  
|<span data-ttu-id="a6c70-115">設定</span><span class="sxs-lookup"><span data-stu-id="a6c70-115">Setting</span></span>|<span data-ttu-id="a6c70-116">描述</span><span class="sxs-lookup"><span data-stu-id="a6c70-116">Description</span></span>|  
|-------------|-----------------|  
|`1050`|<span data-ttu-id="a6c70-117">在指令碼或工具中並不會看見這個值，但它對應至在 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]、 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]或 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]中所建立的資料庫。</span><span class="sxs-lookup"><span data-stu-id="a6c70-117">This value is not visible in script or tools, but it corresponds to databases created in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], or [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)].</span></span> <span data-ttu-id="a6c70-118">所有未明確設定 `CompatibilityLevel` 的資料庫都是隱含地在 `1050` 層級執行。</span><span class="sxs-lookup"><span data-stu-id="a6c70-118">Any database that does not have `CompatibilityLevel` explicitly set is implicitly running at the `1050` level.</span></span>|  
|`1100`|<span data-ttu-id="a6c70-119">這是您在 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 或 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中建立之新資料庫的預設值。</span><span class="sxs-lookup"><span data-stu-id="a6c70-119">This is the default value for new databases that you create in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] or [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="a6c70-120">您也可以針對使用舊版 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 建立的資料庫指定這個值，以啟用僅在此相容性層級支援的功能 (亦即，維度屬性的增加字串儲存體或包含字串資料的相異計數量值)。</span><span class="sxs-lookup"><span data-stu-id="a6c70-120">You can also specify it for databases created in earlier versions of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] to enable the use of features that are supported only at this compatibility level (namely, increased string storage for dimension attributes or distinct count measures that contain string data).</span></span><br /><br /> <span data-ttu-id="a6c70-121">已 `CompatibilityLevel` 設定為 `1100` 取得額外屬性的資料庫，可 `StringStoresCompatibilityLevel` 讓您選擇資料分割和維度的替代字串儲存體。</span><span class="sxs-lookup"><span data-stu-id="a6c70-121">Databases that have a `CompatibilityLevel` set to `1100` get an additional property, `StringStoresCompatibilityLevel`, that lets you choose alternative string storage for partitions and dimensions.</span></span>|  
  
> [!WARNING]  
>  <span data-ttu-id="a6c70-122">將資料庫相容性設為更高的層級將無法回復。</span><span class="sxs-lookup"><span data-stu-id="a6c70-122">Setting the database compatibility to a higher level is irreversible.</span></span> <span data-ttu-id="a6c70-123">將相容性層級增加到之後 `1100` ，您必須在較新的伺服器上繼續執行資料庫。</span><span class="sxs-lookup"><span data-stu-id="a6c70-123">After you increase the compatibility level to `1100`, you must continue to run the database on newer servers.</span></span> <span data-ttu-id="a6c70-124">您無法回復至 `1050` 。</span><span class="sxs-lookup"><span data-stu-id="a6c70-124">You cannot rollback to `1050`.</span></span> <span data-ttu-id="a6c70-125">您無法 `1100` 在或之前的伺服器版本上附加或還原資料庫 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="a6c70-125">You cannot attach or restore an `1100` database on a server version that is earlier than [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] or [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="a6c70-126">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="a6c70-126">Prerequisites</span></span>  
 <span data-ttu-id="a6c70-127">資料庫相容性層級是在 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]中引進。</span><span class="sxs-lookup"><span data-stu-id="a6c70-127">Database compatibility levels are introduced in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].</span></span> <span data-ttu-id="a6c70-128">您必須有 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 或更新版本，才能檢視或設定資料庫相容性層級。</span><span class="sxs-lookup"><span data-stu-id="a6c70-128">You must have [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] or higher to view or set the database compatibility level.</span></span>  
  
 <span data-ttu-id="a6c70-129">資料庫不可為本機 Cube。</span><span class="sxs-lookup"><span data-stu-id="a6c70-129">The database cannot be a local cube.</span></span> <span data-ttu-id="a6c70-130">本機 Cube 不支援 `CompatibilityLevel` 屬性。</span><span class="sxs-lookup"><span data-stu-id="a6c70-130">Local cubes do not support the `CompatibilityLevel` property.</span></span>  
  
 <span data-ttu-id="a6c70-131">資料庫必須已經使用舊版 (SQL Server 2008 R2 或更早版本) 建立，然後附加或還原到 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 或更新版本的伺服器。</span><span class="sxs-lookup"><span data-stu-id="a6c70-131">The database must have been created in a previous release (SQL Server 2008 R2 or earlier) and then attached or restored to a [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] or higher server.</span></span> <span data-ttu-id="a6c70-132">部署至 SQL Server 2012 的資料庫已是 `1100`，且無法降級至較低層級執行。</span><span class="sxs-lookup"><span data-stu-id="a6c70-132">Databases deployed to SQL Server 2012 are already at `1100` and cannot be downgraded to run at a lower level.</span></span>  
  
## <a name="determine-the-existing-database-compatibility-level-for-a-multidimensional-database"></a><span data-ttu-id="a6c70-133">判斷多維度資料庫的現有資料庫相容性層級</span><span class="sxs-lookup"><span data-stu-id="a6c70-133">Determine the existing database compatibility level for a multidimensional database</span></span>  
 <span data-ttu-id="a6c70-134">檢視或修改資料庫相容性層級的唯一方式是透過 XMLA。</span><span class="sxs-lookup"><span data-stu-id="a6c70-134">The only way to view or modify the database compatibility level is through XMLA.</span></span> <span data-ttu-id="a6c70-135">您可以在 SQL Server Management Studio 中檢視或修改指定資料庫的 XMLA 指令碼。</span><span class="sxs-lookup"><span data-stu-id="a6c70-135">You can view or modify the XMLA script that specifies your database in SQL Server Management Studio.</span></span>  
  
 <span data-ttu-id="a6c70-136">如果您在資料庫的 XMLA 定義中搜尋屬性 `CompatibilityLevel` 而此屬性並不存在，很有可能該資料庫是位於 `1050` 層級。</span><span class="sxs-lookup"><span data-stu-id="a6c70-136">If you search the XMLA definition of a database for the property `CompatibilityLevel` and it does not exist, you most likely have a database at the `1050` level.</span></span>  
  
 <span data-ttu-id="a6c70-137">下一節中會提供檢視及修改 XMLA 指令碼的指示。</span><span class="sxs-lookup"><span data-stu-id="a6c70-137">Instructions for viewing and modifying the XMLA script are provided in the next section.</span></span>  
  
## <a name="set-the-database-compatibility-level-in-sql-server-management-studio"></a><span data-ttu-id="a6c70-138">在 SQL Server Management Studio 中設定資料庫相容性層級</span><span class="sxs-lookup"><span data-stu-id="a6c70-138">Set the database compatibility level in SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="a6c70-139">在提高相容性層級之前，請先備份資料庫，以防您之後想要還原變更。</span><span class="sxs-lookup"><span data-stu-id="a6c70-139">Before raising the compatibility level, backup the database in case you want to reverse your changes later.</span></span>  
  
2.  <span data-ttu-id="a6c70-140">使用 SQL Server Management Studio 連接至裝載資料庫的 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 伺服器。</span><span class="sxs-lookup"><span data-stu-id="a6c70-140">Using SQL Server Management Studio, connect to the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] server that hosts the database.</span></span>  
  
3.  <span data-ttu-id="a6c70-141">以滑鼠右鍵按一下資料庫名稱，依序指向 [編寫資料庫的指令碼為]\*\*\*\* 和 [ALTER 至]\*\*\*\*，然後選取 [新增查詢編輯器視窗]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a6c70-141">Right-click the database name, point to **Script Database as**, point to **ALTER to**, and then select **New Query Editor Window**.</span></span> <span data-ttu-id="a6c70-142">資料庫的 XMLA 表示法將會在新視窗中開啟。</span><span class="sxs-lookup"><span data-stu-id="a6c70-142">An XMLA representation of the database will open in a new window.</span></span>  
  
4.  <span data-ttu-id="a6c70-143">複製下面 XML 元素：</span><span class="sxs-lookup"><span data-stu-id="a6c70-143">Copy the following XML element:</span></span>  
  
    ```  
    <ddl200:CompatibilityLevel>1100</ddl200:CompatibilityLevel>  
    ```  
  
5.  <span data-ttu-id="a6c70-144">將它貼到 `</Annotations>` 結束元素的後面和 `<Language>` 元素的前面。</span><span class="sxs-lookup"><span data-stu-id="a6c70-144">Paste it after the `</Annotations>` closing element and before the `<Language>` element.</span></span> <span data-ttu-id="a6c70-145">XML 看起來應該類似於下面範例：</span><span class="sxs-lookup"><span data-stu-id="a6c70-145">The XML should look similar to the following example:</span></span>  
  
    ```  
    </Annotations>  
    <ddl200:CompatibilityLevel>1100</ddl200:CompatibilityLevel>  
    <Language>1033</Language>  
    ```  
  
6.  <span data-ttu-id="a6c70-146">儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="a6c70-146">Save the file.</span></span>  
  
7.  <span data-ttu-id="a6c70-147">若要執行指令檔，按一下 [查詢] 功能表上的 [執行]\*\*\*\*，或按 F5 鍵。</span><span class="sxs-lookup"><span data-stu-id="a6c70-147">To run the script, click **Execute** on the Query menu or press F5.</span></span>  
  
## <a name="supported-operations-that-require-the-same-compatibility-level"></a><span data-ttu-id="a6c70-148">支援且需要相同相容性層級的作業</span><span class="sxs-lookup"><span data-stu-id="a6c70-148">Supported Operations that Require the Same Compatibility Level</span></span>  
 <span data-ttu-id="a6c70-149">以下作業要求來源資料庫共用相同的相容性層級。</span><span class="sxs-lookup"><span data-stu-id="a6c70-149">The following operations require that the source databases share the same compatibility level.</span></span>  
  
1.  <span data-ttu-id="a6c70-150">只有在兩個資料庫共用相同的相容性層級時，才支援從不同資料庫合併磁碟分割。</span><span class="sxs-lookup"><span data-stu-id="a6c70-150">Merging partitions from different databases is supported only if both databases share the same compatibility level.</span></span>  
  
2.  <span data-ttu-id="a6c70-151">從其他資料庫使用連結的維度需要相同的相容性層級。</span><span class="sxs-lookup"><span data-stu-id="a6c70-151">Using linked dimensions from another database requires the same compatibility level.</span></span> <span data-ttu-id="a6c70-152">例如，如果您想要從資料庫中的資料庫使用連結的維度 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] ，您必須將 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 資料庫移植至伺服器， [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 並將相容性層級設定為 `1100` 。</span><span class="sxs-lookup"><span data-stu-id="a6c70-152">For example, if you want to use a linked dimension from a [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] database in a [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] database, you must port the [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] database to a [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] server and set the compatibility level to `1100`.</span></span>  
  
3.  <span data-ttu-id="a6c70-153">只有共用相同版本與資料庫相容性層級的伺服器，才支援同步處理伺服器。</span><span class="sxs-lookup"><span data-stu-id="a6c70-153">Synchronizing servers is only supported for servers that share the same version and database compatibility level.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="a6c70-154">後續步驟</span><span class="sxs-lookup"><span data-stu-id="a6c70-154">Next Steps</span></span>  
 <span data-ttu-id="a6c70-155">在您提高資料庫相容性層級之後，就可以在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] 中設定 `StringStoresCompatibilityLevel` 屬性。</span><span class="sxs-lookup"><span data-stu-id="a6c70-155">After you increase the database compatibility level, you can set the `StringStoresCompatibilityLevel` property in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].</span></span> <span data-ttu-id="a6c70-156">這樣做會增加量值和維度的字串儲存體。</span><span class="sxs-lookup"><span data-stu-id="a6c70-156">This increases string storage for measures and dimensions.</span></span> <span data-ttu-id="a6c70-157">如需這項功能的詳細資訊，請參閱 [設定維度及資料分割的字串存放區](configure-string-storage-for-dimensions-and-partitions.md)。</span><span class="sxs-lookup"><span data-stu-id="a6c70-157">For more information about this feature, see [Configure String Storage for Dimensions and Partitions](configure-string-storage-for-dimensions-and-partitions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6c70-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a6c70-158">See Also</span></span>  
 [<span data-ttu-id="a6c70-159">備份、還原和同步處理資料庫 &#40;XMLA&#41;</span><span class="sxs-lookup"><span data-stu-id="a6c70-159">Backing Up, Restoring, and Synchronizing Databases &#40;XMLA&#41;</span></span>](../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md)  
  
  
