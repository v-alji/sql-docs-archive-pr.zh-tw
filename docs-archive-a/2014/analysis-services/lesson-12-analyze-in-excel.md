---
title: 第13課：在 Excel 中進行分析 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: ce717071-193b-4c99-9654-c7a613e16327
author: minewiskan
ms.author: owend
ms.openlocfilehash: 129956ddc8e755d1f2b298a7ea36307d50f52344
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584781"
---
# <a name="lesson-13-analyze-in-excel"></a><span data-ttu-id="452d7-102">第 13 課：在 Excel 中進行分析</span><span class="sxs-lookup"><span data-stu-id="452d7-102">Lesson 13: Analyze in Excel</span></span>
  <span data-ttu-id="452d7-103">在這一課，您將使用 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 中的 [在 Excel 中進行分析] 功能來開啟 Microsoft Excel、自動建立模型工作空間的資料來源連接，以及自動將樞紐分析表加入至工作表。</span><span class="sxs-lookup"><span data-stu-id="452d7-103">In this lesson, you will use the Analyze in Excel feature in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] to open Microsoft Excel, automatically create a data source connection to the model workspace, and automatically add a PivotTable to the worksheet.</span></span> <span data-ttu-id="452d7-104">「在 Excel 中進行分析」功能是為了在部署模型之前，以快速又輕鬆的方式來測試模型設計的功效。</span><span class="sxs-lookup"><span data-stu-id="452d7-104">The Analyze in Excel feature is meant to provide a quick and easy way to test the efficacy of your model design prior to deploying your model.</span></span> <span data-ttu-id="452d7-105">在本課中，您將不會執行任何資料分析。</span><span class="sxs-lookup"><span data-stu-id="452d7-105">You will not perform any data analysis in this lesson.</span></span> <span data-ttu-id="452d7-106">這堂課的目的是讓您 (模型作者) 熟悉可用來測試模型設計的工具。</span><span class="sxs-lookup"><span data-stu-id="452d7-106">The purpose of this lesson is to familiarize you, the model author, with the tools you can use to test your model design.</span></span> <span data-ttu-id="452d7-107">不像使用 [在 Excel 中進行分析] 功能，使用者將使用用戶端報表應用程式 (例如 Excel 或 [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] ) 連接與瀏覽已部署的模型資料。</span><span class="sxs-lookup"><span data-stu-id="452d7-107">Unlike using the Analyze in Excel feature, which is meant for model authors, end-users will use client reporting applications such as Excel or [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] to connect to and browse deployed model data.</span></span>  
  
 <span data-ttu-id="452d7-108">為了完成這一課，您必須在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]所在電腦上安裝 Excel。</span><span class="sxs-lookup"><span data-stu-id="452d7-108">In order to complete this lesson, Excel must be installed on the same computer as [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].</span></span> <span data-ttu-id="452d7-109">如需詳細資訊，請參閱[在 Excel 中進行分析 &#40;SSAS 表格式&#41;](tabular-models/analyze-in-excel-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="452d7-109">To learn more, see [Analyze in Excel &#40;SSAS Tabular&#41;](tabular-models/analyze-in-excel-ssas-tabular.md).</span></span>  
  
 <span data-ttu-id="452d7-110">這堂課的預估完成時間：**20 分鐘**</span><span class="sxs-lookup"><span data-stu-id="452d7-110">Estimated time to complete this lesson: **20 minutes**</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="452d7-111">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="452d7-111">Prerequisites</span></span>  
 <span data-ttu-id="452d7-112">本主題是表格式模型教學課程的一部分，請依序完成。</span><span class="sxs-lookup"><span data-stu-id="452d7-112">This topic is part of a tabular modeling tutorial, which should be completed in order.</span></span> <span data-ttu-id="452d7-113">在執行本課中的工作之前，您應已完成上一課： [第 11 課：建立資料分割](lesson-10-create-partitions.md)。</span><span class="sxs-lookup"><span data-stu-id="452d7-113">Before performing the tasks in this lesson, you should have completed the previous lesson: [Lesson 11: Create Partitions](lesson-10-create-partitions.md).</span></span>  
  
## <a name="browse-using-the-default-and-internet-sales-perspectives"></a><span data-ttu-id="452d7-114">使用 [預設] 和 [網際網路銷售] 檢視方塊來瀏覽</span><span class="sxs-lookup"><span data-stu-id="452d7-114">Browse using the Default and Internet Sales perspectives</span></span>  
 <span data-ttu-id="452d7-115">在這些首要工作中，您將使用預設檢視方塊 (包含所有模型物件) 以及您在第 8 課：「建立檢視方塊」中建立的網際網路銷售檢視方塊來瀏覽模型。</span><span class="sxs-lookup"><span data-stu-id="452d7-115">In these first tasks, you will browse your model by using both the default perspective, which includes all model objects, and also by using the Internet Sales perspective you created in Lesson 8: Create Perspectives.</span></span> <span data-ttu-id="452d7-116">網際網路銷售檢視方塊不包括 Customer 資料表物件。</span><span class="sxs-lookup"><span data-stu-id="452d7-116">The Internet Sales perspective excludes the Customer table object.</span></span>  
  
#### <a name="to-browse-by-using-the-default-perspective"></a><span data-ttu-id="452d7-117">若要使用預設檢視方塊瀏覽</span><span class="sxs-lookup"><span data-stu-id="452d7-117">To browse by using the Default perspective</span></span>  
  
1.  <span data-ttu-id="452d7-118">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]中，按一下 **[模型]** 功能表，然後按一下 **[在 Excel 中進行分析]**。</span><span class="sxs-lookup"><span data-stu-id="452d7-118">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click the **Model** menu, and then click **Analyze in Excel**.</span></span>  
  
2.  <span data-ttu-id="452d7-119">於 [在 Excel 中的進行分析]\*\*\*\* 對話方塊中，按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="452d7-119">In the **Analyze in Excel** dialog box, click **OK**.</span></span>  
  
     <span data-ttu-id="452d7-120">Excel 會開啟新的活頁簿。</span><span class="sxs-lookup"><span data-stu-id="452d7-120">Excel will open with a new workbook.</span></span> <span data-ttu-id="452d7-121">系統會使用目前的使用者帳戶建立資料來源連接，並將預設檢視方塊用於定義可檢視的欄位。</span><span class="sxs-lookup"><span data-stu-id="452d7-121">A data source connection is created using the current user account and the Default perspective is used to define viewable fields.</span></span> <span data-ttu-id="452d7-122">樞紐分析表會自動加入到工作表中。</span><span class="sxs-lookup"><span data-stu-id="452d7-122">A Pivot table is automatically added to the worksheet.</span></span>  
  
3.  <span data-ttu-id="452d7-123">在 Excel 的**樞紐分析表欄位清單**中，請注意 [**日期**] 和 [**網際網路銷售**] 量值會出現，以及 [ **Customer**]、[**日期**]、[ **Geography** **]、[product]**、[product **Category**]、[**產品子類別**目錄] 和 [**網際網路銷售**] 資料表，其各自的</span><span class="sxs-lookup"><span data-stu-id="452d7-123">In Excel, in the **PivotTable Field List**, notice the **Date** and **Internet Sales** measures appear, as well as the **Customer**, **Date**, **Geography**, **Product**, **Product Category**, **Product Subcategory**, and **Internet Sales** tables with all of their respective columns appear.</span></span>  
  
4.  <span data-ttu-id="452d7-124">關閉 Excel 而不儲存活頁簿。</span><span class="sxs-lookup"><span data-stu-id="452d7-124">Close Excel without saving the workbook.</span></span>  
  
#### <a name="to-browse-by-using-the-internet-sales-perspective"></a><span data-ttu-id="452d7-125">使用 [網際網路銷售] 檢視方塊來瀏覽</span><span class="sxs-lookup"><span data-stu-id="452d7-125">To browse by using the Internet Sales perspective</span></span>  
  
1.  <span data-ttu-id="452d7-126">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]中，按一下 **[模型]** 功能表，然後按一下 **[在 Excel 中進行分析]**。</span><span class="sxs-lookup"><span data-stu-id="452d7-126">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click the **Model** menu, and then click **Analyze in Excel**.</span></span>  
  
2.  <span data-ttu-id="452d7-127">於 [在 Excel 中進行分析]\*\*\*\* 對話方塊中，保持選取 [目前的 Windows 使用者]\*\*\*\*，接著在 [檢視方塊]\*\*\*\* 下拉式清單方塊中，選取 [網際網路銷售]\*\*\*\*，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="452d7-127">In the **Analyze in Excel** dialog box, leave **Current Windows User** selected, then in the **Perspective** drop-down listbox, select **Internet Sales**, and then click **OK**.</span></span> <span data-ttu-id="452d7-128">Excel 便會開啟。</span><span class="sxs-lookup"><span data-stu-id="452d7-128">Excel opens.</span></span>  
  
3.  <span data-ttu-id="452d7-129">在 Excel 的 [樞紐分析表欄位清單]\*\*\*\* 中，注意 Customer 資料表已從欄位清單中排除。</span><span class="sxs-lookup"><span data-stu-id="452d7-129">In Excel, in the **PivotTable Field List**, notice the Customer table is excluded from the field list.</span></span>  
  
## <a name="browse-using-roles"></a><span data-ttu-id="452d7-130">使用角色瀏覽</span><span class="sxs-lookup"><span data-stu-id="452d7-130">Browse Using Roles</span></span>  
 <span data-ttu-id="452d7-131">角色是任何表格式模型不可或缺的一部分。</span><span class="sxs-lookup"><span data-stu-id="452d7-131">Roles are an integral part of any tabular model.</span></span> <span data-ttu-id="452d7-132">如果沒有至少一個角色 (使用者會以成員形式加入角色中)，使用者將無法使用模型存取並分析資料。</span><span class="sxs-lookup"><span data-stu-id="452d7-132">Without at least one role, to which users are added as members, users will not be able to access and analyze data using your model.</span></span> <span data-ttu-id="452d7-133">[在 Excel 中進行分析] 功能提供您一個用來測試已定義之角色的方式。</span><span class="sxs-lookup"><span data-stu-id="452d7-133">The Analyze in Excel feature provides a way for you to test the roles you have defined.</span></span>  
  
#### <a name="to-browse-by-using-the-internet-sales-manager-user-role"></a><span data-ttu-id="452d7-134">若要使用 Internet Sales Manager 使用者角色瀏覽</span><span class="sxs-lookup"><span data-stu-id="452d7-134">To browse by using the Internet Sales Manager user role</span></span>  
  
1.  <span data-ttu-id="452d7-135">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]中，按一下 **[模型]** 功能表，然後按一下 **[在 Excel 中進行分析]**。</span><span class="sxs-lookup"><span data-stu-id="452d7-135">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click the **Model** menu, and then click **Analyze in Excel**.</span></span>  
  
2.  <span data-ttu-id="452d7-136">於 [在 Excel 中進行分析]\*\*\*\* 對話方塊的 [指定要用來連接到模型的使用者名稱或角色]\*\*\*\* 中，選取 [角色]\*\*\*\*，並在下拉式清單方塊中，選取 [Internet Sales Manager (網際網路銷售經理)]\*\*\*\*，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="452d7-136">In the **Analyze in Excel** dialog box, in **Specify the user name or role to use to connect to the model**, select **Role**, and then in the drop-down listbox, select **Internet Sales Manager**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="452d7-137">Excel 會開啟新的活頁簿。</span><span class="sxs-lookup"><span data-stu-id="452d7-137">Excel will open with a new workbook.</span></span> <span data-ttu-id="452d7-138">樞紐分析表會自動建立。</span><span class="sxs-lookup"><span data-stu-id="452d7-138">A Pivot table is automatically created.</span></span> <span data-ttu-id="452d7-139">[樞紐分析表欄位清單] 包含新模型中所有可用的資料欄位。</span><span class="sxs-lookup"><span data-stu-id="452d7-139">The Pivot Table Field List includes all of the data fields available in your new model.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="452d7-140">後續步驟</span><span class="sxs-lookup"><span data-stu-id="452d7-140">Next Steps</span></span>  
 <span data-ttu-id="452d7-141">若要繼續進行本教學課程，請前往下一課： [第 14 課：部署](lesson-13-deploy.md)。</span><span class="sxs-lookup"><span data-stu-id="452d7-141">To continue this tutorial, go to the next lesson: [Lesson 14: Deploy](lesson-13-deploy.md).</span></span>  
  
  
