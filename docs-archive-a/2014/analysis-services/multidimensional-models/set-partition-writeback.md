---
title: 設定分割區回寫 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- write-enabled partitions [Analysis Services]
- partitions [Analysis Services], writeback
- partitions [Analysis Services], write-enabled
- writeback [Analysis Services], partitions
ms.assetid: 38bb09cc-2652-4971-8373-0cf468cdc7a6
author: minewiskan
ms.author: owend
ms.openlocfilehash: eaea005bf919545e5d63be481eb3478b286c16d5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596354"
---
# <a name="set-partition-writeback"></a><span data-ttu-id="836ec-102">設定分割區回寫</span><span class="sxs-lookup"><span data-stu-id="836ec-102">Set Partition Writeback</span></span>
  <span data-ttu-id="836ec-103">如果您啟用量值群組的寫入功能，使用者可以在瀏覽 Cube 資料時進行變更，系統會將變更儲存到另一個資料表 (稱為回寫資料表)，而不是在 Cube 資料或來源資料中儲存變更。</span><span class="sxs-lookup"><span data-stu-id="836ec-103">If you write-enable a measure group, end users can change cube data while they browse it, where changes are saved in a separate table called a writeback table, not in the cube data or source data.</span></span> <span data-ttu-id="836ec-104">瀏覽可寫入分割區的使用者，會看到所有變更在分割區的回寫資料表中產生的結果。</span><span class="sxs-lookup"><span data-stu-id="836ec-104">End users who browse a write-enabled partition see the net effect of all changes in the writeback table for the partition.</span></span>  
  
 <span data-ttu-id="836ec-105">您可以瀏覽或刪除回寫資料。</span><span class="sxs-lookup"><span data-stu-id="836ec-105">You can browse or delete writeback data.</span></span> <span data-ttu-id="836ec-106">您也可以將回寫資料轉換為分割區。</span><span class="sxs-lookup"><span data-stu-id="836ec-106">You can also convert writeback data to a partition.</span></span> <span data-ttu-id="836ec-107">在可寫入分割區上，您可以使用 Cube 角色來授與讀取/寫入存取權給使用者和使用者群組，並限制對分割區中的特定資料格或資料格群組的存取。</span><span class="sxs-lookup"><span data-stu-id="836ec-107">On a write-enabled partition, you can use cube roles to grant read/write access to users and groups of users, and to limit access to specific cells or groups of cells in the partition.</span></span>  
  
 <span data-ttu-id="836ec-108">如需有關回寫的簡短影片簡介，請參閱＜ [Analysis Services 的 Excel 2010 回寫](https://go.microsoft.com/fwlink/p/?LinkId=394951)＞。</span><span class="sxs-lookup"><span data-stu-id="836ec-108">For a short video introduction to writeback, see [Excel 2010 Writeback to Analysis Services](https://go.microsoft.com/fwlink/p/?LinkId=394951).</span></span> <span data-ttu-id="836ec-109">如需此功能的更詳細說明，請參閱部落格文章系列： [Building a Writeback Application with Analysis Services](https://go.microsoft.com/fwlink/?LinkId=394977)(使用 Analysis Services 建立回寫應用程式) (部落格文章)。</span><span class="sxs-lookup"><span data-stu-id="836ec-109">A more detailed exploration of this feature is available through this blog post series, [Building a Writeback Application with Analysis Services (blog)](https://go.microsoft.com/fwlink/?LinkId=394977).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="836ec-110">只有 SQL Server 關聯式資料庫和資料超市才支援回寫，且回寫僅適用於 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 多維度模型。</span><span class="sxs-lookup"><span data-stu-id="836ec-110">Writeback is supported for SQL Server relational databases and data marts only, and only for [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] multidimensional models.</span></span>  
  
## <a name="how-to-write-enable-a-partition"></a><span data-ttu-id="836ec-111">如何啟用分割區的寫入功能</span><span class="sxs-lookup"><span data-stu-id="836ec-111">How to write-enable a partition</span></span>  
 <span data-ttu-id="836ec-112">您可以在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]的 Cube 設計師中啟用分割區本身的寫入功能，來啟用分割區之量值群組的寫入功能。</span><span class="sxs-lookup"><span data-stu-id="836ec-112">You can write-enable a partition's measure groups by write-enabling the partition itself in Cube Designer in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] or [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
-   <span data-ttu-id="836ec-113">在 Cube 設計師的 [資料分割] 索引標籤中，以滑鼠右鍵按一下資料分割並選擇 [回寫設定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="836ec-113">In Cube Designer, in the Partitions tab, right-click a partition and choose **Writeback Settings**.</span></span>  
  
-   <span data-ttu-id="836ec-114">在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 中，展開資料庫 | Cube | 量值群組，然後以滑鼠右鍵按一下 [回寫]\*\*\*\* 並選擇 [啟用回寫]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="836ec-114">In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], expand the database | cube | measure group, and then right-click **Writeback** and choose **Enable Writeback**.</span></span>  
  
 <span data-ttu-id="836ec-115">只有使用 SUM 彙總的量值才支援回寫。</span><span class="sxs-lookup"><span data-stu-id="836ec-115">Writeback is only supported for measures that use the SUM aggregation.</span></span> <span data-ttu-id="836ec-116">在 AdventureWorks 範例資料庫，您可以使用「銷售目標」量值群組測試回寫行為。</span><span class="sxs-lookup"><span data-stu-id="836ec-116">In the AdventureWorks sample database, you can use the Sales Targets measure group to test writeback behaviors.</span></span>  
  
 <span data-ttu-id="836ec-117">啟用分割區的寫入功能時，您需要指定儲存回寫資料表的資料表名稱和資料來源。</span><span class="sxs-lookup"><span data-stu-id="836ec-117">When you write-enable a partition, you specify a table name and a data source for storing the write-back table.</span></span> <span data-ttu-id="836ec-118">此資料表會記錄量值群組後續的任何變更。</span><span class="sxs-lookup"><span data-stu-id="836ec-118">Any subsequent changes to the measure group are recorded in this table.</span></span>  
  
## <a name="browse-writeback-data-in-a-partition"></a><span data-ttu-id="836ec-119">瀏覽分割區中的回寫資料</span><span class="sxs-lookup"><span data-stu-id="836ec-119">Browse writeback data in a partition</span></span>  
 <span data-ttu-id="836ec-120">您可以在 [瀏覽資料]\*\*\*\* 對話方塊中瀏覽 Cube 的回寫資料表內容，在 Cube 設計師的 [資料分割]\*\*\*\* 索引標籤上，以滑鼠右鍵按一下可寫入的資料分割，即可存取此對話方塊。</span><span class="sxs-lookup"><span data-stu-id="836ec-120">You can browse the contents of a cube's writeback table in the **Browse Data** dialog box, which you can access by right-clicking a write-enabled partition on the **Partitions** tab in Cube Designer.</span></span>  
  
## <a name="delete-writeback-data-or-disable-writeback"></a><span data-ttu-id="836ec-121">刪除回寫資料或停用回寫</span><span class="sxs-lookup"><span data-stu-id="836ec-121">Delete writeback data or disable writeback</span></span>  
 <span data-ttu-id="836ec-122">刪除回寫資料會清除回寫快取；在刪除該資料之後，隨即會重新開始執行其他回寫工作。</span><span class="sxs-lookup"><span data-stu-id="836ec-122">Deleting writeback data clears the writeback cache; as soon as that data is deleted, additional writeback work is performed on a clean slate.</span></span> <span data-ttu-id="836ec-123">停用 Cube 分割區的回寫會直接關閉該資料分割的回寫功能。</span><span class="sxs-lookup"><span data-stu-id="836ec-123">Disabling writeback for a cube partition simply turns off writeback for that partition.</span></span>  
  
## <a name="convert-writeback-data-to-a-partition"></a><span data-ttu-id="836ec-124">將回寫資料轉換為分割區</span><span class="sxs-lookup"><span data-stu-id="836ec-124">Convert writeback data to a partition</span></span>  
 <span data-ttu-id="836ec-125">您可以將分割區之回寫資料表中的資料轉換為分割區。</span><span class="sxs-lookup"><span data-stu-id="836ec-125">You can convert the data in a partition's writeback table to a partition.</span></span> <span data-ttu-id="836ec-126">此程序會讓回寫資料表變成新分割區的事實資料表。</span><span class="sxs-lookup"><span data-stu-id="836ec-126">This procedure causes the writeback table to become the new partition's fact table.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="836ec-127">不正確地使用分割區會造成不正確的 Cube 資料。</span><span class="sxs-lookup"><span data-stu-id="836ec-127">Incorrect use of partitions can result in inaccurate cube data.</span></span> <span data-ttu-id="836ec-128">如需詳細資訊，請參閱 [建立及管理本機分割區 &#40;Analysis Services&#41;](create-and-manage-a-local-partition-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="836ec-128">For more information, see [Create and Manage a Local Partition &#40;Analysis Services&#41;](create-and-manage-a-local-partition-analysis-services.md).</span></span>  
  
 <span data-ttu-id="836ec-129">將回寫資料表轉換為分割區也會造成禁止寫入分割區。</span><span class="sxs-lookup"><span data-stu-id="836ec-129">Converting the writeback data table to a partition also write-disables the partition.</span></span> <span data-ttu-id="836ec-130">分割區之資料格的所有未限制讀取/寫入原則和讀取/寫入權限會停用，且使用者將無法變更已顯示的 Cube 資料。</span><span class="sxs-lookup"><span data-stu-id="836ec-130">All unrestricted read/write policies and read/write permissions for the partition's cells are disabled, and end users will not be able to change displayed cube data.</span></span> <span data-ttu-id="836ec-131">(已停用未限制讀取/寫入原則或已停用讀取/寫入權限的使用者仍然可以瀏覽 Cube)。讀取和意外讀取權限不受影響。</span><span class="sxs-lookup"><span data-stu-id="836ec-131">(End users with disabled unrestricted read/write policies or disabled read/write permissions will still be able to browse the cube.) Read and read-contingent permissions are not affected.</span></span>  
  
 <span data-ttu-id="836ec-132">若要將回寫資料轉換為資料分割，請使用 [轉換為資料分割]\*\*\*\* 對話方塊，在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中，以滑鼠右鍵按一下可寫入資料分割的回寫資料表，即可存取此對話方塊。</span><span class="sxs-lookup"><span data-stu-id="836ec-132">To convert writeback data to a partition, use the **Convert to Partition** dialog box, which is accessed by right-clicking the writeback table for a write-enabled partition in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="836ec-133">您可以指定分割區的名稱，以及是否要在建立分割區的同時或稍後設計分割區的彙總。</span><span class="sxs-lookup"><span data-stu-id="836ec-133">You specify a name for the partition and whether to design the aggregation for the partition later or at the same time that you create it.</span></span> <span data-ttu-id="836ec-134">若要在您選擇分割區的同時建立彙總，您必須選擇從現有的分割區複製彙總設計。</span><span class="sxs-lookup"><span data-stu-id="836ec-134">To create the aggregation at the same time you choose the partition, you must choose to copy the aggregation design from an existing partition.</span></span> <span data-ttu-id="836ec-135">這通常 (但並非一定) 是目前的回寫分割區。</span><span class="sxs-lookup"><span data-stu-id="836ec-135">This is normally, but not necessarily, the current writeback partition.</span></span> <span data-ttu-id="836ec-136">您也可以選擇在建立分割區的同時處理分割區。</span><span class="sxs-lookup"><span data-stu-id="836ec-136">You can also choose to process the partition at the same time that you create it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="836ec-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="836ec-137">See Also</span></span>  
 <span data-ttu-id="836ec-138">[可寫入的磁碟分割](../multidimensional-models-olap-logical-cube-objects/partitions-write-enabled-partitions.md) </span><span class="sxs-lookup"><span data-stu-id="836ec-138">[Write-Enabled Partitions](../multidimensional-models-olap-logical-cube-objects/partitions-write-enabled-partitions.md) </span></span>  
 <span data-ttu-id="836ec-139">[在 Excel 2010 的資料格層級啟用 OLAP Cube 的回寫功能](https://go.microsoft.com/fwlink/p/?LinkId=394952) </span><span class="sxs-lookup"><span data-stu-id="836ec-139">[Enabling Write-back to an OLAP Cube at Cell Level in Excel 2010](https://go.microsoft.com/fwlink/p/?LinkId=394952) </span></span>  
 [<span data-ttu-id="836ec-140">啟用 Analysis Services 回寫並透過回寫保護資料輸入</span><span class="sxs-lookup"><span data-stu-id="836ec-140">Enabling and Securing Data Entry with Analysis Services Writeback</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=394953)  
  
  
