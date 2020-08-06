---
title: 從 PowerPivot (SSAS 表格式) 匯入 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.importfromppt.f1
ms.assetid: ac1a6a79-bda3-4122-a717-8b1e2f77da02
author: minewiskan
ms.author: owend
ms.openlocfilehash: 581259d79e5d84bd558ca3f13519fbf4dc0ba52f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687218"
---
# <a name="import-from-powerpivot-ssas-tabular"></a><span data-ttu-id="933d1-102">從 PowerPivot 匯入 (SSAS 表格式)</span><span class="sxs-lookup"><span data-stu-id="933d1-102">Import from PowerPivot (SSAS Tabular)</span></span>
  <span data-ttu-id="933d1-103">本主題描述如何使用 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 的 [從 PowerPivot 匯入] 專案範本，從 PowerPivot 活頁簿匯入中繼資料和資料，以建立新的表格式模型專案。</span><span class="sxs-lookup"><span data-stu-id="933d1-103">This topic describes how to create a new tabular model project by importing the metadata and data from a PowerPivot workbook by using the Import from PowerPivot project template in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
## <a name="create-a-new-tabular-model-from-a-powerpivot-for-excel-file"></a><span data-ttu-id="933d1-104">從 PowerPivot for Excel 檔案建立新的表格式模型</span><span class="sxs-lookup"><span data-stu-id="933d1-104">Create a new Tabular Model from a PowerPivot for Excel file</span></span>  
 <span data-ttu-id="933d1-105">從 PowerPivot 活頁簿匯入來建立新的表格式模型專案時，系統會使用定義活頁簿結構的中繼資料來建立及定義 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] 中表格式模型專案的結構。</span><span class="sxs-lookup"><span data-stu-id="933d1-105">When creating a new tabular model project by importing from a PowerPivot workbook, the metadata that defines the structure of the workbook is used to create and define the structure of the tabular model project in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].</span></span> <span data-ttu-id="933d1-106">資料表、資料行、量值和關聯性等物件會保留，並以其在 PowerPivot 活頁簿的顯示方式出現在表格式模型專案中。</span><span class="sxs-lookup"><span data-stu-id="933d1-106">Objects such as tables, columns, measures, and relationships are retained and will appear in the tabular model project as they are in the PowerPivot workbook.</span></span> <span data-ttu-id="933d1-107">.xlsx 活頁簿檔案將不會做任何變更。</span><span class="sxs-lookup"><span data-stu-id="933d1-107">No changes are made to the .xlsx workbook file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="933d1-108">表格式模型不支援連結資料表。</span><span class="sxs-lookup"><span data-stu-id="933d1-108">Tabular models do not support linked tables.</span></span> <span data-ttu-id="933d1-109">從包含連結資料表的 PowerPivot 活頁簿匯入時，會將連結資料表資料視為複製/貼上的資料，並儲存在 Model.bim 檔案中。</span><span class="sxs-lookup"><span data-stu-id="933d1-109">When importing from a PowerPivot workbook that contains a linked table, linked table data is treated as copy\pasted data and stored in the Model.bim file.</span></span> <span data-ttu-id="933d1-110">檢視複製/貼上的資料表之屬性時，會停用 [來源資料]\*\*\*\* 屬性，並停用 [資料表]\*\*\*\* 功能表上的 [資料表屬性]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="933d1-110">When viewing properties for a copy\pasted table, the **Source Data** property is disabled and the **Table Properties** dialog on the **Table** menu is disabled.</span></span>  
>   
>  <span data-ttu-id="933d1-111">可以加入至模型中內嵌資料的上限為 10,000 個資列列。</span><span class="sxs-lookup"><span data-stu-id="933d1-111">There is a limit of 10,000 rows that can be added to the data embedded in the model.</span></span> <span data-ttu-id="933d1-112">如果您從 PowerPivot 匯入模型並看到錯誤：「資料已截斷。</span><span class="sxs-lookup"><span data-stu-id="933d1-112">If you import a model from PowerPivot and see the error, "Data was truncated.</span></span> <span data-ttu-id="933d1-113">貼上的資料表不能包含超過10000個數據列」，您應該將內嵌資料移到另一個資料來源（例如 SQL Server 中的資料表）來修改 PowerPivot 模型，然後重新匯入。</span><span class="sxs-lookup"><span data-stu-id="933d1-113">Pasted tables cannot contain more than 10000 rows" you should revise the PowerPivot model by moving the embedded data into another data source, such as a table in SQL Server, and then re-import.</span></span>  
  
 <span data-ttu-id="933d1-114">根據工作空間資料庫位於與 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 相同之電腦 (本機) 的 Analysis Services 執行個體還是遠端 Analysis Services 執行個體上而有特殊考量。</span><span class="sxs-lookup"><span data-stu-id="933d1-114">There are special considerations depending on whether or not the workspace database is on an Analysis Services instance on the same computer (local) as [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] or is on a remote Analysis Services instance..</span></span>  
  
 <span data-ttu-id="933d1-115">如果工作空間資料庫位於本機 Analysis Services 執行個體上，您可以從 PowerPivot 活頁簿匯入中繼資料和資料。</span><span class="sxs-lookup"><span data-stu-id="933d1-115">If the workspace database is on a local instance of Analysis Services, you can import both the metadata and data from the PowerPivot workbook.</span></span> <span data-ttu-id="933d1-116">中繼資料會從活頁簿複製，並用來建立表格式模型專案。</span><span class="sxs-lookup"><span data-stu-id="933d1-116">The metadata is copied from the workbook and used to create the tabular model project.</span></span> <span data-ttu-id="933d1-117">資料接著會從活頁簿複製並儲存在專案的工作空間資料庫中 (除了複製/貼上的資料，儲存在 model.bim 檔案) 中。</span><span class="sxs-lookup"><span data-stu-id="933d1-117">The data is then copied from the workbook and stored in the project's workspace database (except for copy/pasted data, which is stored in the Model.bim file).</span></span>  
  
 <span data-ttu-id="933d1-118">如果工作空間資料庫位於遠端 Analysis Services 執行個體上，您不能從 PowerPivot for Excel 活頁簿匯入資料。</span><span class="sxs-lookup"><span data-stu-id="933d1-118">If the workspace database is on a remote Analysis Services instance, you cannot import data from a PowerPivot for Excel workbook.</span></span> <span data-ttu-id="933d1-119">您依然可以匯入活頁簿中繼資料；不過，這會導致指令碼在遠端 Analysis Services 執行個體上執行。</span><span class="sxs-lookup"><span data-stu-id="933d1-119">You can still import the workbook metadata; however, this will cause a script to be run on the remote Analysis Services instance.</span></span> <span data-ttu-id="933d1-120">您應只從受信任的 PowerPivot 活頁簿匯入中繼資料。</span><span class="sxs-lookup"><span data-stu-id="933d1-120">You should only import metadata from a trusted PowerPivot workbook.</span></span> <span data-ttu-id="933d1-121">必須從資料來源連接中定義的來源匯入資料。</span><span class="sxs-lookup"><span data-stu-id="933d1-121">Data must be imported from sources defined in the data source connections.</span></span> <span data-ttu-id="933d1-122">PowerPivot 活頁簿中複製/貼上和連結資料表的資料必須複製及貼到表格式模型專案中。</span><span class="sxs-lookup"><span data-stu-id="933d1-122">Copy/pasted and linked table data in the PowerPivot workbook must be copied and pasted into the tabular model project.</span></span>  
  
#### <a name="to-create-a-new-tabular-model-project-from-a-powerpivot-for-excel-file"></a><span data-ttu-id="933d1-123">若要從 PowerPivot for Excel 檔案建立新的表格式模型專案</span><span class="sxs-lookup"><span data-stu-id="933d1-123">To create a new tabular model project from a PowerPivot for Excel file</span></span>  
  
1.  <span data-ttu-id="933d1-124">在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]的 **[檔案]** 功能表上，按一下 **[新增]**，然後再按一下 **[專案]**。</span><span class="sxs-lookup"><span data-stu-id="933d1-124">In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], on the **File** menu, click **New**, and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="933d1-125">在 [**新增專案**] 對話方塊的 [**已安裝的範本**] 底下，按一下 [**商業智慧**]，然後按一下 [**從 PowerPivot 匯入**]。</span><span class="sxs-lookup"><span data-stu-id="933d1-125">In the **New Project** dialog box, under **Installed Templates**, click **Business Intelligence**, and then click **Import from PowerPivot**.</span></span>  
  
3.  <span data-ttu-id="933d1-126">在 [**名稱**] 中，輸入專案的名稱，然後指定位置和方案名稱，再按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="933d1-126">In  **Name**, type a name for the project, then specify a location and solution name, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="933d1-127">在 [開啟]\*\*\*\* 對話方塊中，選取包含您要匯入之模型中繼資料和資料的 [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)] 檔案，然後按一下 [開啟]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="933d1-127">In the **Open** dialog box, select the [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)] file that contains the model metadata and data you want to import, and then click **Open**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="933d1-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="933d1-128">See Also</span></span>  
 <span data-ttu-id="933d1-129">[&#40;SSAS 表格式&#41;的工作空間資料庫](workspace-database-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="933d1-129">[Workspace Database &#40;SSAS Tabular&#41;](workspace-database-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="933d1-130">複製及貼上資料 &#40;SSAS 表格式&#41;</span><span class="sxs-lookup"><span data-stu-id="933d1-130">Copy and Paste Data &#40;SSAS Tabular&#41;</span></span>](../copy-and-paste-data-ssas-tabular.md)  
  
  
