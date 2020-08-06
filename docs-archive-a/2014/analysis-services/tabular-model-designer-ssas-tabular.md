---
title: 表格式模型設計師 (SSAS 表格式) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- SQL12.ASVS.BIDTOOLSET.TOPLEVSEMMODUIENTRY.F1
ms.assetid: 45735c57-2a95-4e45-8994-7242df6c9c5f
author: minewiskan
ms.author: owend
ms.openlocfilehash: ac63826d3e8a93f341c181faeef44714afd92353
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594246"
---
# <a name="tabular-model-designer-ssas-tabular"></a><span data-ttu-id="ba62a-102">表格式模型設計師 (SSAS 表格式)</span><span class="sxs-lookup"><span data-stu-id="ba62a-102">Tabular Model Designer (SSAS Tabular)</span></span>
  <span data-ttu-id="ba62a-103">表格式模型設計師是 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 與 Microsoft [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 2010 或更新版本整合的一部分，具有特別用來開發專業表格式模型方案的額外專案類型範本。</span><span class="sxs-lookup"><span data-stu-id="ba62a-103">The tabular model designer is part of [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], integrated with Microsoft [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 2010 or later, with additional project type templates specifically for developing professional tabular model solutions.</span></span>  
  
 <span data-ttu-id="ba62a-104">本主題的章節：</span><span class="sxs-lookup"><span data-stu-id="ba62a-104">Sections in this topic:</span></span>  
  
-   [<span data-ttu-id="ba62a-105">優點</span><span class="sxs-lookup"><span data-stu-id="ba62a-105">Benefits</span></span>](#bkmk_benefits)  
  
-   [<span data-ttu-id="ba62a-106">專案範本</span><span class="sxs-lookup"><span data-stu-id="ba62a-106">Project Templates</span></span>](#bkmk_proj_temp)  
  
-   [<span data-ttu-id="ba62a-107">視窗和功能表</span><span class="sxs-lookup"><span data-stu-id="ba62a-107">Windows and Menus</span></span>](#bkmk_wind_men)  
  
-   [<span data-ttu-id="ba62a-108">Visual Studio 整合</span><span class="sxs-lookup"><span data-stu-id="ba62a-108">Visual Studio Integration</span></span>](#bkmk_vsint)  
  
##  <a name="benefits"></a><a name="bkmk_benefits"></a> <span data-ttu-id="ba62a-109">優點</span><span class="sxs-lookup"><span data-stu-id="ba62a-109">Benefits</span></span>  
 <span data-ttu-id="ba62a-110">當您安裝 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]時，用來建立表格式模型的專案範本會加入至可用的專案類型中。</span><span class="sxs-lookup"><span data-stu-id="ba62a-110">When you install [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], new project templates for creating tabular models are added to the available project types.</span></span> <span data-ttu-id="ba62a-111">在使用其中一個範本建立新的表格式模型專案之後，您可以使用表格式模型設計師工具和精靈開始撰寫模型。</span><span class="sxs-lookup"><span data-stu-id="ba62a-111">After creating a new tabular model project by using one of the templates, you can begin model authoring by using the tabular model designer tools and wizards.</span></span>  
  
 <span data-ttu-id="ba62a-112">除了用於撰寫專業多維度和表格式模型方案的新範本和工具之外， [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 環境也提供偵錯和專案週期功能，確保您能為組織建立最強大的 BI 方案。</span><span class="sxs-lookup"><span data-stu-id="ba62a-112">In addition to new templates and tools for authoring professional multidimensional and tabular model solutions, the [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] environment provides debugging and project lifecycle capabilities that ensure you create the most powerful BI solutions for your organization.</span></span> <span data-ttu-id="ba62a-113">如需 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]的詳細資訊，請參閱 [Visual Studio 使用者入門](https://go.microsoft.com/fwlink/?LinkId=206389)。</span><span class="sxs-lookup"><span data-stu-id="ba62a-113">For more information about [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], see [Getting Started with Visual Studio](https://go.microsoft.com/fwlink/?LinkId=206389).</span></span>  
  
##  <a name="project-templates"></a><a name="bkmk_proj_temp"></a><span data-ttu-id="ba62a-114">專案範本</span><span class="sxs-lookup"><span data-stu-id="ba62a-114">Project Templates</span></span>  
 <span data-ttu-id="ba62a-115">當您安裝 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]時，下列表格式模型專案範本會加入至商業智慧專案類型中：</span><span class="sxs-lookup"><span data-stu-id="ba62a-115">When you install [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], the following tabular model project templates are added to the Business Intelligence project types:</span></span>  
  
 <span data-ttu-id="ba62a-116">**Analysis Services 表格式專案**</span><span class="sxs-lookup"><span data-stu-id="ba62a-116">**Analysis Services Tabular Project**</span></span>  
 <span data-ttu-id="ba62a-117">這個範本可用來建立新的空白表格式模型專案。</span><span class="sxs-lookup"><span data-stu-id="ba62a-117">This template can be used to create a new, blank tabular model project.</span></span>  
  
 <span data-ttu-id="ba62a-118">**從伺服器匯入 (表格式)**</span><span class="sxs-lookup"><span data-stu-id="ba62a-118">**Import from Server (Tabular)**</span></span>  
 <span data-ttu-id="ba62a-119">這個範本可用來從 Analysis Services 中的現有表格式模型擷取中繼資料，以建立新的表格式模型專案。</span><span class="sxs-lookup"><span data-stu-id="ba62a-119">This template can be used to create a new tabular model project by extracting the metadata from an existing tabular model in Analysis Services.</span></span>  
  
 <span data-ttu-id="ba62a-120">**從 PowerPivot 匯入**</span><span class="sxs-lookup"><span data-stu-id="ba62a-120">**Import from PowerPivot**</span></span>  
 <span data-ttu-id="ba62a-121">這個範本可用來從 [!INCLUDE[ssGeminiClient](../includes/ssgeminiclient-md.md)] 檔案擷取中繼資料和其他資料，以建立新的表格式模型專案。</span><span class="sxs-lookup"><span data-stu-id="ba62a-121">This template is used for creating a new tabular model project by extracting the metadata and data from a [!INCLUDE[ssGeminiClient](../includes/ssgeminiclient-md.md)] file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ba62a-122">表格式模型專案要求表格式模式的 Analysis Services 伺服器執行個體必須在本機或在網路上執行。</span><span class="sxs-lookup"><span data-stu-id="ba62a-122">Tabular model projects require an Analysis Services server instance in tabular mode be running locally or on the network.</span></span>  
  
##  <a name="windows-and-menus"></a><a name="bkmk_wind_men"></a> <span data-ttu-id="ba62a-123">視窗和功能表</span><span class="sxs-lookup"><span data-stu-id="ba62a-123">Windows and Menus</span></span>  
 <span data-ttu-id="ba62a-124">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 表格式模型撰寫環境包含下列項目：</span><span class="sxs-lookup"><span data-stu-id="ba62a-124">The [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] tabular model authoring environment includes the following:</span></span>  
  
### <a name="designer-window"></a><span data-ttu-id="ba62a-125">設計師視窗</span><span class="sxs-lookup"><span data-stu-id="ba62a-125">Designer Window</span></span>  
 <span data-ttu-id="ba62a-126">設計師視窗可透過提供模型的視覺表示法，用來撰寫表格式模型。</span><span class="sxs-lookup"><span data-stu-id="ba62a-126">The designer window is used to author tabular models by providing a visual representation of the model.</span></span> <span data-ttu-id="ba62a-127">當您開啟 Model.bim 檔案時，會在設計師視窗中開啟模型。</span><span class="sxs-lookup"><span data-stu-id="ba62a-127">When you open the Model.bim file, the model opens in the designer window.</span></span> <span data-ttu-id="ba62a-128">您可以在設計師視窗中使用兩種不同的檢視模式撰寫模型：</span><span class="sxs-lookup"><span data-stu-id="ba62a-128">You can author a model in the designer window by using two different view modes:</span></span>  
  
 <span data-ttu-id="ba62a-129">**資料檢視**</span><span class="sxs-lookup"><span data-stu-id="ba62a-129">**Data View**</span></span>  
 <span data-ttu-id="ba62a-130">資料檢視以表格式的方格格式顯示資料表。</span><span class="sxs-lookup"><span data-stu-id="ba62a-130">The data view displays tables in a tabular, grid format.</span></span> <span data-ttu-id="ba62a-131">您也可以使用量值方格定義量值，僅針對 [資料檢視] 中的每個資料表顯示。</span><span class="sxs-lookup"><span data-stu-id="ba62a-131">You can also define measures by using the measure grid, which can be shown for each table in Data View only.</span></span>  
  
 <span data-ttu-id="ba62a-132">**圖表視圖**</span><span class="sxs-lookup"><span data-stu-id="ba62a-132">**Diagram View**</span></span>  
 <span data-ttu-id="ba62a-133">此圖表檢視以圖形格式顯示資料表，以及資料表之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="ba62a-133">The diagram view displays tables, with relationships between them, in a graphical format.</span></span> <span data-ttu-id="ba62a-134">您可以篩選資料行、量值、階層及 KPI，也可以選擇使用定義的檢視方塊來檢視模型。</span><span class="sxs-lookup"><span data-stu-id="ba62a-134">Columns, measures, hierarchies, and KPIs can be filtered, and you can choose to view the model by using a defined perspective.</span></span>  
  
 <span data-ttu-id="ba62a-135">您可以在上述任一檢視中，執行大部分的模型撰寫工作。</span><span class="sxs-lookup"><span data-stu-id="ba62a-135">Most model authoring tasks can be performed in either view.</span></span>  
  
### <a name="solution-explorer"></a><span data-ttu-id="ba62a-136">方案總管</span><span class="sxs-lookup"><span data-stu-id="ba62a-136">Solution Explorer</span></span>  
 <span data-ttu-id="ba62a-137">[方案總管] 視窗以表格式模型專案及其相關項目的邏輯容器來呈現使用中方案。</span><span class="sxs-lookup"><span data-stu-id="ba62a-137">The Solution Explorer window presents the active solution as a logical container for a tabular model project and its associated items.</span></span> <span data-ttu-id="ba62a-138">模型專案 (.smproj) 只包含 References 物件 (空白) 和 Model.bim 檔案。</span><span class="sxs-lookup"><span data-stu-id="ba62a-138">The model project (.smproj) contains only a References object (empty) and the Model.bim file.</span></span> <span data-ttu-id="ba62a-139">您可以開啟專案項目進行修改，以及直接從這個檢視執行其他管理工作。</span><span class="sxs-lookup"><span data-stu-id="ba62a-139">You can open project items for modification and perform other management tasks directly from this view.</span></span>  
  
 <span data-ttu-id="ba62a-140">表格式模型方案通常只包含一個專案；但是，方案也可以包含其他專案，例如 Integration Services 或 Reporting Services 專案。</span><span class="sxs-lookup"><span data-stu-id="ba62a-140">Tabular model solutions typically contain only one project; however, a solution can contain other projects too, for example, Integration Services or Reporting services project.</span></span> <span data-ttu-id="ba62a-141">您可以加入任意數目的檔案，但是這些檔案的類型不得與表格式模型專案檔案的類型相同，且其 [建置動作] 屬性設為 [無] 或 [複製到輸出] 屬性設為 [不要複製]。</span><span class="sxs-lookup"><span data-stu-id="ba62a-141">You can add any number of files provided they are not of the same type as tabular model project files and their Build Action property is set to None, or Copy to Output property is set to Do Not Copy.</span></span>  
  
 <span data-ttu-id="ba62a-142">若要檢視方案總管，請按一下 [檢視]\*\*\*\* 功能表，然後按一下方案總管\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba62a-142">To view Solution Explorer, click the **View** menu, and then click **Solution Explorer**.</span></span>  
  
### <a name="properties-window"></a><span data-ttu-id="ba62a-143">屬性視窗</span><span class="sxs-lookup"><span data-stu-id="ba62a-143">Properties Window</span></span>  
 <span data-ttu-id="ba62a-144">[屬性] 視窗列出選取物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="ba62a-144">The Properties window lists the properties of the selected object.</span></span> <span data-ttu-id="ba62a-145">下列物件具有可在 [屬性] 視窗中檢視及編輯的屬性：</span><span class="sxs-lookup"><span data-stu-id="ba62a-145">The following objects have properties that can be viewed and edited in the Properties window:</span></span>  
  
-   <span data-ttu-id="ba62a-146">Model.bim</span><span class="sxs-lookup"><span data-stu-id="ba62a-146">Model.bim</span></span>  
  
-   <span data-ttu-id="ba62a-147">資料表</span><span class="sxs-lookup"><span data-stu-id="ba62a-147">Table</span></span>  
  
-   <span data-ttu-id="ba62a-148">資料行</span><span class="sxs-lookup"><span data-stu-id="ba62a-148">Column</span></span>  
  
-   <span data-ttu-id="ba62a-149">Measure</span><span class="sxs-lookup"><span data-stu-id="ba62a-149">Measure</span></span>  
  
 <span data-ttu-id="ba62a-150">[專案屬性] 僅會顯示 [屬性] 視窗中的專案名稱和專案資料夾。</span><span class="sxs-lookup"><span data-stu-id="ba62a-150">Project Properties display only the project name and project folder in the Properties window.</span></span> <span data-ttu-id="ba62a-151">專案也具有您可以使用強制回應屬性對話方塊設定的其他部署選項和部署伺服器設定。</span><span class="sxs-lookup"><span data-stu-id="ba62a-151">Projects also have additional deployment Options and deployment server settings that you can set using a modal properties dialog box.</span></span> <span data-ttu-id="ba62a-152">若要檢視這些屬性，請以滑鼠右鍵按一下方案總管\*\*\*\* 中的專案，然後按一下 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba62a-152">To view these properties, in **Solution Explorer**, right click the project, and then click **Properties**.</span></span>  
  
 <span data-ttu-id="ba62a-153">[屬性] 視窗中的欄位包含內嵌控制項，當您按一下欄位時，即會開啟這些控制項。</span><span class="sxs-lookup"><span data-stu-id="ba62a-153">Fields in the Properties window have embedded controls that open when you click them.</span></span> <span data-ttu-id="ba62a-154">編輯控制項的類型會隨著特定屬性而不同。</span><span class="sxs-lookup"><span data-stu-id="ba62a-154">The type of edit control depends on the particular property.</span></span> <span data-ttu-id="ba62a-155">這些控制項包含編輯方塊、下拉式清單和自訂對話方塊的連結。</span><span class="sxs-lookup"><span data-stu-id="ba62a-155">Controls include edit boxes, dropdown lists, and links to custom dialog boxes.</span></span> <span data-ttu-id="ba62a-156">呈暗灰色的屬性是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="ba62a-156">Properties that are shown as dimmed are read-only.</span></span>  
  
 <span data-ttu-id="ba62a-157">若要檢視 [屬性]\*\*\*\* 視窗，請按一下 [檢視]\*\*\*\* 功能表，然後按一下 [屬性視窗]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba62a-157">To view the **Properties** window, click the **View** menu, and then click **Properties Window**.</span></span>  
  
### <a name="error-list"></a><span data-ttu-id="ba62a-158">錯誤清單</span><span class="sxs-lookup"><span data-stu-id="ba62a-158">Error List</span></span>  
 <span data-ttu-id="ba62a-159">[錯誤清單] 視窗包含模型狀態的訊息：</span><span class="sxs-lookup"><span data-stu-id="ba62a-159">The Error List window contains messages about the model state:</span></span>  
  
-   <span data-ttu-id="ba62a-160">安全性最佳作法的通知。</span><span class="sxs-lookup"><span data-stu-id="ba62a-160">Notifications about security best practices.</span></span>  
  
-   <span data-ttu-id="ba62a-161">資料處理的需求。</span><span class="sxs-lookup"><span data-stu-id="ba62a-161">Requirements for data processing.</span></span>  
  
-   <span data-ttu-id="ba62a-162">角色之導出資料行、量值及資料列篩選的語意錯誤資訊。</span><span class="sxs-lookup"><span data-stu-id="ba62a-162">Semantic error information for calculated columns, measures, and row filters for roles.</span></span> <span data-ttu-id="ba62a-163">您可以按兩下導出資料行的錯誤訊息，瀏覽至錯誤的來源。</span><span class="sxs-lookup"><span data-stu-id="ba62a-163">For calculated columns, you can double-click the error message to navigate to the source of the error.</span></span>  
  
-   <span data-ttu-id="ba62a-164">DirectQuery 驗證錯誤。</span><span class="sxs-lookup"><span data-stu-id="ba62a-164">DirectQuery validation errors.</span></span>  
  
 <span data-ttu-id="ba62a-165">依預設，除非傳回錯誤，否則不會顯示 [錯誤清單]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba62a-165">By default, the **Error List** does not appear unless an error is returned.</span></span> <span data-ttu-id="ba62a-166">但是，您可以隨時檢視 [錯誤清單]\*\*\*\* 視窗。</span><span class="sxs-lookup"><span data-stu-id="ba62a-166">You can, however, view the **Error List** window at any time.</span></span> <span data-ttu-id="ba62a-167">若要檢視 [錯誤清單]\*\*\*\* 視窗，請按一下 [檢視]\*\*\*\* 功能表，然後按一下 [錯誤清單]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba62a-167">To view the **Error List** window, click the **View** menu, and then click **Error List**.</span></span>  
  
### <a name="output"></a><span data-ttu-id="ba62a-168">輸出</span><span class="sxs-lookup"><span data-stu-id="ba62a-168">Output</span></span>  
 <span data-ttu-id="ba62a-169">建置和部署資訊會顯示在 [輸出]\*\*\*\* 視窗中 (以及模型進度對話方塊)。</span><span class="sxs-lookup"><span data-stu-id="ba62a-169">Build and deployment information is displayed in the **Output** Window (in addition to the modal progress dialog).</span></span> <span data-ttu-id="ba62a-170">若要檢視 [輸出]\*\*\*\* 視窗，請按一下 [檢視]\*\*\*\* 功能表，然後按一下 [輸出]。</span><span class="sxs-lookup"><span data-stu-id="ba62a-170">To view the **Output** window, click the **View** menu, and then click Output.</span></span>  
  
### <a name="menu-items"></a><span data-ttu-id="ba62a-171">功能表項目</span><span class="sxs-lookup"><span data-stu-id="ba62a-171">Menu Items</span></span>  
 <span data-ttu-id="ba62a-172">當您安裝 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]時，特別用來撰寫表格式模型的額外功能表項目會加入至 Visual Studio 功能表列。</span><span class="sxs-lookup"><span data-stu-id="ba62a-172">When you install [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], additional menu items specifically for authoring tabular models are added to the Visual Studio menu bar.</span></span> <span data-ttu-id="ba62a-173">[模型]\*\*\*\* 功能表可用來啟動資料匯入精靈、檢視現有連接、處理工作空間資料，以及在 [!INCLUDE[msCoName](../includes/msconame-md.md)] Excel 中瀏覽模型工作空間。</span><span class="sxs-lookup"><span data-stu-id="ba62a-173">The **Model** menu can be used to launch the Data Import Wizard, view existing connections, process workspace data, and browse the model workspace in [!INCLUDE[msCoName](../includes/msconame-md.md)] Excel.</span></span> <span data-ttu-id="ba62a-174">[資料表]\*\*\*\* 功能表用來建立及管理資料表之間的關聯性、建立及管理量值、指定資料表設定、指定計算選項，以及指定其他資料表屬性。</span><span class="sxs-lookup"><span data-stu-id="ba62a-174">The **Table** menu is used to create and manage relationships between tables, create and manage measures, specify data table settings, specify calculation options, and specify other table properties.</span></span> <span data-ttu-id="ba62a-175">您可以使用 [資料行]\*\*\*\* 功能表在資料表中加入及刪除資料行、隱藏及取消隱藏資料行，以及指定其他資料行屬性，例如資料類型和篩選。</span><span class="sxs-lookup"><span data-stu-id="ba62a-175">With the **Column** menu, you can add and delete columns in a table, hide and unhide columns, and specify other column properties such as data types and filters.</span></span> <span data-ttu-id="ba62a-176">您可以在 [建立]\*\*\*\* 功能表上建立及部署表格式模型方案。</span><span class="sxs-lookup"><span data-stu-id="ba62a-176">You can build and deploy tabular model solutions on the **Build** menu.</span></span> <span data-ttu-id="ba62a-177">複製/貼上功能包含在 [編輯]\*\*\*\* 功能表中。</span><span class="sxs-lookup"><span data-stu-id="ba62a-177">Copy/Paste functions are included on the **Edit** menu.</span></span>  
  
 <span data-ttu-id="ba62a-178">除了這些功能表項目之外，也會將其他設定加入至 [工具] 功能表項目的 Analysis Services 選項。</span><span class="sxs-lookup"><span data-stu-id="ba62a-178">In addition to these menu items, additional settings are added to the Analysis Services options on the Tools menu items.</span></span>  
  
### <a name="toolbar"></a><span data-ttu-id="ba62a-179">工具列</span><span class="sxs-lookup"><span data-stu-id="ba62a-179">Toolbar</span></span>  
 <span data-ttu-id="ba62a-180">Analysis Services 工具列可輕鬆快速地存取最常用的模型撰寫命令。</span><span class="sxs-lookup"><span data-stu-id="ba62a-180">The Analysis Services toolbar provides quick and easy access to the most frequently used model authoring commands.</span></span>  
  
##  <a name="visual-studio-integration"></a><a name="bkmk_vsint"></a> <span data-ttu-id="ba62a-181">Visual Studio 整合</span><span class="sxs-lookup"><span data-stu-id="ba62a-181">Visual Studio Integration</span></span>  
 <span data-ttu-id="ba62a-182">**原始檔控制**</span><span class="sxs-lookup"><span data-stu-id="ba62a-182">**Source Control**</span></span>  
 <span data-ttu-id="ba62a-183">Analysis Services 專案會與選取的原始檔控制外掛程式整合。</span><span class="sxs-lookup"><span data-stu-id="ba62a-183">Analysis Services projects integrate with the selected source control plug-in.</span></span> <span data-ttu-id="ba62a-184">如果您已設定 Visual Studio 使用原始檔控制，則可以從 [方案總管] 使用簽入/簽出。</span><span class="sxs-lookup"><span data-stu-id="ba62a-184">If you have configured Visual Studio to use source control, you can use check in/check out from Solution Explorer.</span></span> <span data-ttu-id="ba62a-185">若要設定使用 Team Foundation Server，請參閱 [Configure Visual Studio with Team Foundation Version Control](https://msdn.microsoft.com/library/ms253064.aspx)(使用 Team Foundation 版本控制設定 Visual Studio)。</span><span class="sxs-lookup"><span data-stu-id="ba62a-185">To configure to use Team Foundation Server, see [Configure Visual Studio with Team Foundation Version Control](https://msdn.microsoft.com/library/ms253064.aspx).</span></span> <span data-ttu-id="ba62a-186">此外，也支援許多協力廠商原始檔控制外掛程式。</span><span class="sxs-lookup"><span data-stu-id="ba62a-186">Many third-party source control plug-ins are supported as well.</span></span>  
  
 <span data-ttu-id="ba62a-187">**字體**</span><span class="sxs-lookup"><span data-stu-id="ba62a-187">**Fonts**</span></span>  
 <span data-ttu-id="ba62a-188">表格式模型使用 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 環境字型來控制顯示的字型。</span><span class="sxs-lookup"><span data-stu-id="ba62a-188">Tabular models use the [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] environment font to control the fonts in the display.</span></span> <span data-ttu-id="ba62a-189">如果預設 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 字型不含您的語言所需的全部 Unicode 字元，您可能必須變更此字型。</span><span class="sxs-lookup"><span data-stu-id="ba62a-189">It can be necessary to change this font if the default [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] font does not have all of the Unicode characters you need for your language.</span></span> <span data-ttu-id="ba62a-190">若要變更字型，請依序按一下 [工具]\*\*\*\* 功能表、[選項]\*\*\*\* 及 [字型和色彩]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ba62a-190">To change fonts, click the **Tools** menu, then click **Options**, and then click **Fonts and Colors**.</span></span>  
  
 <span data-ttu-id="ba62a-191">**鍵盤快速鍵**</span><span class="sxs-lookup"><span data-stu-id="ba62a-191">**Keyboard Shortcuts**</span></span>  
 <span data-ttu-id="ba62a-192">您可以透過 [工具] -> [選項] -> [鍵盤] 對話方塊，設定/重新對應 Analysis Services 鍵盤快速鍵。</span><span class="sxs-lookup"><span data-stu-id="ba62a-192">The Analysis Services keyboard shortcuts can be configured/remapped through the Tools->Options->Keyboard dialog.</span></span> <span data-ttu-id="ba62a-193">表格式模型設計師內容支援如建立、儲存、偵錯、新增專案等一些通用的 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 快速鍵。</span><span class="sxs-lookup"><span data-stu-id="ba62a-193">Some global [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] shortcuts, such as build, save, debug, new project, etc. are supported in the tabular model designer context.</span></span> <span data-ttu-id="ba62a-194">其他表格式模型設計師的特定快速鍵則會在 Analysis Services 內容中。</span><span class="sxs-lookup"><span data-stu-id="ba62a-194">Other tabular model designer specific shortcuts are in the Analysis Services context.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba62a-195">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ba62a-195">See Also</span></span>  
 <span data-ttu-id="ba62a-196">[&#40;SSAS 表格式&#41;的表格式模型專案](tabular-models/tabular-model-projects-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="ba62a-196">[Tabular Model Projects &#40;SSAS Tabular&#41;](tabular-models/tabular-model-projects-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="ba62a-197">屬性 &#40;SSAS 表格式&#41;</span><span class="sxs-lookup"><span data-stu-id="ba62a-197">Properties &#40;SSAS Tabular&#41;</span></span>](tabular-models/properties-ssas-tabular.md)  
  
  
