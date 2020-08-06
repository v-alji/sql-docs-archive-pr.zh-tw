---
title: 定義連結維度 |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- dimensions [Analysis Services], linked
- linked dimensions [Analysis Services]
ms.assetid: d5ad5eae-5dde-46a6-91c3-c8766d016dec
author: minewiskan
ms.author: owend
ms.openlocfilehash: 088dda52042a53c252eed8d759e54af4dee1a029
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687286"
---
# <a name="define-linked-dimensions"></a><span data-ttu-id="2f56e-102">定義連結維度</span><span class="sxs-lookup"><span data-stu-id="2f56e-102">Define Linked Dimensions</span></span>
  <span data-ttu-id="2f56e-103">連結維度是根據在相同版本與相容性層級的另一個 Analysis Services 資料庫中所建立和儲存的維度。</span><span class="sxs-lookup"><span data-stu-id="2f56e-103">A linked dimension is based on a dimension created and stored in another Analysis Services database of the same version and compatibility level.</span></span> <span data-ttu-id="2f56e-104">藉由使用連結維度，您可以在一個資料庫上建立、儲存和維護維度，同時將該維度提供給多個資料庫的使用者使用。</span><span class="sxs-lookup"><span data-stu-id="2f56e-104">By using a linked dimension, you can create, store, and maintain a dimension on one database, while making it available to users of multiple databases.</span></span> <span data-ttu-id="2f56e-105">對於使用者來說，連結維度和其他任何維度看起來都一樣。</span><span class="sxs-lookup"><span data-stu-id="2f56e-105">To users, a linked dimension appears like any other dimension.</span></span>  
  
 <span data-ttu-id="2f56e-106">連結維度是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="2f56e-106">Linked dimensions are read-only.</span></span> <span data-ttu-id="2f56e-107">若您想修改維度或建立新的關聯性，則必須變更來源維度，然後刪除並重新建立連結維度和其關聯性。</span><span class="sxs-lookup"><span data-stu-id="2f56e-107">If you want to modify the dimension or create new relationships, you must change the source dimension, then delete and recreate the linked dimension and its relationships.</span></span> <span data-ttu-id="2f56e-108">您無法重新整理連結維度來收集來源物件中的變更。</span><span class="sxs-lookup"><span data-stu-id="2f56e-108">You cannot refresh a linked dimension to pick up changes from the source object.</span></span>  
  
 <span data-ttu-id="2f56e-109">所有相關的量值群組與維度，必須來自相同的來源資料庫。</span><span class="sxs-lookup"><span data-stu-id="2f56e-109">All related measure groups and dimensions must come from the same source database.</span></span> <span data-ttu-id="2f56e-110">您無法建立本機量值群組和您加入 Cube 的連結維度之間的新關聯性。</span><span class="sxs-lookup"><span data-stu-id="2f56e-110">You cannot create new relationships between local measure groups and the linked dimensions you add to your cube.</span></span> <span data-ttu-id="2f56e-111">將連結維度與量值群組加入目前的 Cube 之後，必須在它們的來源資料庫中維護兩者間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="2f56e-111">After linked dimensions and measure groups have been added to the current cube, the relationships between them must be maintained in their source database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2f56e-112">因為無法使用重新整理，所以大多數的 Analysis Services 開發人員都會複製維度而不是連結維度。</span><span class="sxs-lookup"><span data-stu-id="2f56e-112">Because refresh is not available, most Analysis Services developers copy dimensions rather than link them.</span></span> <span data-ttu-id="2f56e-113">您可以在相同方案內複製不同專案中的維度。</span><span class="sxs-lookup"><span data-stu-id="2f56e-113">You can copy dimensions across projects within the same solution.</span></span> <span data-ttu-id="2f56e-114">如需詳細資訊，請參閱 [Refresh of a linked dimension in SSAS](http://sqlblog.com/blogs/marco_russo/archive/2006/09/12/refresh-of-a-linked-dimension-in-ssas.aspx)(在 SSAS 中重新整理連結維度)。</span><span class="sxs-lookup"><span data-stu-id="2f56e-114">For more information, see [Refresh of a linked dimension in SSAS](http://sqlblog.com/blogs/marco_russo/archive/2006/09/12/refresh-of-a-linked-dimension-in-ssas.aspx).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="2f56e-115">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="2f56e-115">Prerequisites</span></span>  
 <span data-ttu-id="2f56e-116">提供維度的來源資料庫和使用該維度的目前資料庫都必須具有相同的版本和相容性層級。</span><span class="sxs-lookup"><span data-stu-id="2f56e-116">The source database that provides the dimension and the current database that uses it must be at the same version and compatibility level.</span></span> <span data-ttu-id="2f56e-117">如需詳細資訊，請參閱[將多維度資料庫的相容性層級設定 &#40;Analysis Services&#41;](compatibility-level-of-a-multidimensional-database-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="2f56e-117">For more information, see [Set the Compatibility Level of a Multidimensional Database &#40;Analysis Services&#41;](compatibility-level-of-a-multidimensional-database-analysis-services.md).</span></span>  
  
 <span data-ttu-id="2f56e-118">來源資料庫必須已部署並處於線上。</span><span class="sxs-lookup"><span data-stu-id="2f56e-118">The source database must be deployed and online.</span></span> <span data-ttu-id="2f56e-119">您必須將發行或取用連結物件的伺服器設定為允許該作業 (如下所示)。</span><span class="sxs-lookup"><span data-stu-id="2f56e-119">Servers that publish or consume linked objects must be configured to allow the operation (see below).</span></span>  
  
 <span data-ttu-id="2f56e-120">您所要使用的維度本身不能是連結維度。</span><span class="sxs-lookup"><span data-stu-id="2f56e-120">The dimension you want to use cannot itself be a linked dimension.</span></span>  
  
## <a name="configure-server-to-allow-linked-objects"></a><span data-ttu-id="2f56e-121">將伺服器設定為允許連結物件</span><span class="sxs-lookup"><span data-stu-id="2f56e-121">Configure server to allow linked objects</span></span>  
  
1.  <span data-ttu-id="2f56e-122">在 SQL Server Management Studio 中，連接到 Analysis Services 伺服器。</span><span class="sxs-lookup"><span data-stu-id="2f56e-122">In SQL Server Management Studio, connect to an Analysis Services server.</span></span> <span data-ttu-id="2f56e-123">在 [物件總管] 中，以滑鼠右鍵按一下伺服器名稱，然後選取 [Facet]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2f56e-123">In Object Explorer, right-click the server name and select **Facets**.</span></span>  
  
2.  <span data-ttu-id="2f56e-124">將 **LinkedObjectsLinksFromOtherInstancesEnabled** 設定為 **True** ，允許伺服器發出在其他執行個體上執行之資料庫的連結物件要求。</span><span class="sxs-lookup"><span data-stu-id="2f56e-124">Set **LinkedObjectsLinksFromOtherInstancesEnabled** to **True** to allow the server to issue requests for linked objects that reside in databases running on other instances.</span></span>  
  
3.  <span data-ttu-id="2f56e-125">將 **LinkedObjectsLinksToOtherInstances** 設定為 **True** ，允許伺服器要求資料連結於在其他執行個體上執行的資料庫。</span><span class="sxs-lookup"><span data-stu-id="2f56e-125">Set **LinkedObjectsLinksToOtherInstances** to **True** to allow the server to request data for linked on databases running on other instances.</span></span>  
  
## <a name="create-a-linked-dimension-in-sql-server-data-tools"></a><span data-ttu-id="2f56e-126">在 SQL Server Data Tools 中建立連結維度</span><span class="sxs-lookup"><span data-stu-id="2f56e-126">Create a linked dimension in SQL Server Data Tools</span></span>  
  
1.  <span data-ttu-id="2f56e-127">啟動精靈。</span><span class="sxs-lookup"><span data-stu-id="2f56e-127">Start the wizard.</span></span> <span data-ttu-id="2f56e-128">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 中，以滑鼠右鍵按一下 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫或專案中的 [維度]\*\*\*\* 資料夾，然後按一下 [新增連結維度]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2f56e-128">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], right-click the **Dimensions** folder in an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database or project, and then click **New Linked Dimension**.</span></span>  
  
2.  <span data-ttu-id="2f56e-129">連接至提供維度的 Analysis Services 資料庫。</span><span class="sxs-lookup"><span data-stu-id="2f56e-129">Connect to the Analysis Services database that provides the dimension.</span></span> <span data-ttu-id="2f56e-130">在連結物件精靈會的 [選取資料來源]\*\*\*\* 頁面上，選擇 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料來源或建立新的資料來源。</span><span class="sxs-lookup"><span data-stu-id="2f56e-130">On the **Select a Data Source** page of the Linked Object Wizard, choose the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] data source or create a new one.</span></span>  
  
3.  <span data-ttu-id="2f56e-131">在精靈的 [選取物件]\*\*\*\* 頁面上，選擇您要在遠端資料庫中連結的維度。</span><span class="sxs-lookup"><span data-stu-id="2f56e-131">On the **Select Objects** page of the wizard, choose the dimensions you want to link to in the remote database.</span></span>  
  
4.  <span data-ttu-id="2f56e-132">在 [正在完成精靈]\*\*\*\* 頁面上，您可以預覽連結物件。</span><span class="sxs-lookup"><span data-stu-id="2f56e-132">On the **Completing the Wizard** page, you can preview the linked objects.</span></span> <span data-ttu-id="2f56e-133">如果您連結的維度與已存在的維度具有相同名稱，則會在名稱後附加序號 (第一個重複的名稱會從 '1' 開始)。</span><span class="sxs-lookup"><span data-stu-id="2f56e-133">If you link a dimension that has the same name as one that already exists, an ordinal number (starting with '1' for the first duplicated name) is appended to the name.</span></span> <span data-ttu-id="2f56e-134">當您完成精靈時，維度會加入至 [維度]\*\*\*\* 資料夾。</span><span class="sxs-lookup"><span data-stu-id="2f56e-134">When you complete the wizard, the dimension is added to the **Dimensions** folder.</span></span>  
  
##  <a name="create-a-new-data-source-connection-to-an-analysis-services-database"></a><a name="bkmk_CreateNew"></a> <span data-ttu-id="2f56e-135">建立新的資料來源與 Analysis Services 資料庫的連接</span><span class="sxs-lookup"><span data-stu-id="2f56e-135">Create a New Data Source Connection to an Analysis Services Database</span></span>  
 <span data-ttu-id="2f56e-136">使用 [建立新的資料來源] 精靈，以將提供維度之 Analysis Services 資料庫相關資訊加入您的專案連接。</span><span class="sxs-lookup"><span data-stu-id="2f56e-136">Use the New Data Source wizard to add to your project connection information about the Analysis Services database that provides the dimension.</span></span> <span data-ttu-id="2f56e-137">您可以在 [連結物件精靈] 中的 [選取資料來源] 頁面上，按一下 [新增資料來源]\*\*\*\* 以啟動精靈。</span><span class="sxs-lookup"><span data-stu-id="2f56e-137">You can start the wizard by clicking **New Data Source** in the Select a Data Source page of the Linked Objects wizard.</span></span>  
  
1.  <span data-ttu-id="2f56e-138">在 [資料來源精靈] 中的 [選取如何定義連接] 頁面上，按一下 [新增]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2f56e-138">In the Data Source Wizard, on the Select how to define the connection page, click **New**.</span></span>  
  
2.  <span data-ttu-id="2f56e-139">在 [連線管理員] 中，確認提供者是否設定為 **Native OLE DB\Microsoft OLE DB Provider for Analysis Services 11.0**。</span><span class="sxs-lookup"><span data-stu-id="2f56e-139">In Connection Manager, verify that the provider is set to **Native OLE DB\Microsoft OLE DB Provider for Analysis Services 11.0**.</span></span>  
  
3.  <span data-ttu-id="2f56e-140">輸入伺服器的名稱 (將*servername* \\ *instancename*用於已命名的實例) <sup>1</sup>或輸入**localhost** ，以連接到在同一部電腦上執行的 Analysis Services 伺服器。</span><span class="sxs-lookup"><span data-stu-id="2f56e-140">Enter the name of the server (use *servername*\\*instancename* for a named instance)<sup>1</sup> or type **localhost** to connect to an Analysis Services server that is running on the same computer.</span></span>  
  
4.  <span data-ttu-id="2f56e-141">使用連接的 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="2f56e-141">Use Windows authentication for the connection.</span></span>  
  
5.  <span data-ttu-id="2f56e-142">在 [初始目錄]\*\*\*\* 中，按一下向下鍵選取此伺服器上的資料庫。</span><span class="sxs-lookup"><span data-stu-id="2f56e-142">In **Initial catalog**, click the down arrow to select a database on this server.</span></span>  
  
6.  <span data-ttu-id="2f56e-143">在 [資料來源精靈] 中，按一下 [下一步]\*\*\*\* 繼續。</span><span class="sxs-lookup"><span data-stu-id="2f56e-143">On the Data Source Wizard, click **Next** to continue.</span></span>  
  
7.  <span data-ttu-id="2f56e-144">在 [模擬資訊] 頁面上，按一下 [使用服務帳戶]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2f56e-144">On the Impersonation Information page, click **Use the service account**.</span></span> <span data-ttu-id="2f56e-145">按一下 [下一步]\*\*\*\* 以完成精靈。</span><span class="sxs-lookup"><span data-stu-id="2f56e-145">Click **Next**, and then finish the wizard.</span></span> <span data-ttu-id="2f56e-146">[連結物件精靈] 即會選取您所定義的連接。</span><span class="sxs-lookup"><span data-stu-id="2f56e-146">The connection you just defined will be selected in the Linked Objects Wizard.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="2f56e-147">後續步驟</span><span class="sxs-lookup"><span data-stu-id="2f56e-147">Next Steps</span></span>  
 <span data-ttu-id="2f56e-148">您不能變更連結維度的結構，所以無法使用維度設計師的 [維度結構]\*\*\*\* 索引標籤來檢視它。</span><span class="sxs-lookup"><span data-stu-id="2f56e-148">You cannot change the structure of a linked dimension, so you cannot view it with the **Dimension Structure** tab of Dimension Designer.</span></span> <span data-ttu-id="2f56e-149">處理連結維度之後，您可以使用 [**瀏覽器**] 索引標籤來查看它。您也可以變更其名稱，並建立名稱的翻譯。</span><span class="sxs-lookup"><span data-stu-id="2f56e-149">After processing the linked dimension, you can view it with the **Browser** tab. You can also change its name and create a translation for the name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f56e-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2f56e-150">See Also</span></span>  
 <span data-ttu-id="2f56e-151">[將多維度資料庫的相容性層級設定 &#40;Analysis Services&#41;](compatibility-level-of-a-multidimensional-database-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="2f56e-151">[Set the Compatibility Level of a Multidimensional Database &#40;Analysis Services&#41;](compatibility-level-of-a-multidimensional-database-analysis-services.md) </span></span>  
 <span data-ttu-id="2f56e-152">[連結量值群組](linked-measure-groups.md) </span><span class="sxs-lookup"><span data-stu-id="2f56e-152">[Linked Measure Groups](linked-measure-groups.md) </span></span>  
 [<span data-ttu-id="2f56e-153">維度關聯性</span><span class="sxs-lookup"><span data-stu-id="2f56e-153">Dimension Relationships</span></span>](../multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)  
  
  
