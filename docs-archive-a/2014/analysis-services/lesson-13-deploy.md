---
title: 第14課：部署 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 24863a8a-9017-415a-a97b-fbac76ed0675
author: minewiskan
ms.author: owend
ms.openlocfilehash: c1a55960a0c33a386d978f3c15e489ed7bd861ce
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584780"
---
# <a name="lesson-14-deploy"></a><span data-ttu-id="740f9-102">第 14 課：部署</span><span class="sxs-lookup"><span data-stu-id="740f9-102">Lesson 14: Deploy</span></span>
  <span data-ttu-id="740f9-103">在這一課，您將設定部署屬性：指定以 [表格式] 模式執行之 Analysis Services 的部署伺服器執行個體，以及您所部署模型的名稱。</span><span class="sxs-lookup"><span data-stu-id="740f9-103">In this lesson, you will configure deployment properties; specifying a deployment server instance of Analysis Services running in Tabular mode, and a name for the model you deploy.</span></span> <span data-ttu-id="740f9-104">接著將模型部署至該執行個體。</span><span class="sxs-lookup"><span data-stu-id="740f9-104">You will then deploy the model to that instance.</span></span> <span data-ttu-id="740f9-105">部署完成後，使用者就可以使用報表用戶端應用程式連接到此模型。</span><span class="sxs-lookup"><span data-stu-id="740f9-105">After it is deployed, users can connect to the model by using a reporting client application.</span></span> <span data-ttu-id="740f9-106">如需詳細資訊，請參閱[表格式模型方案部署 &#40;SSAS 表格式&#41;](tabular-models/tabular-model-solution-deployment-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="740f9-106">To learn more, see [Tabular Model Solution Deployment &#40;SSAS Tabular&#41;](tabular-models/tabular-model-solution-deployment-ssas-tabular.md).</span></span>  
  
 <span data-ttu-id="740f9-107">完成本課程的估計時間： **5 分鐘**</span><span class="sxs-lookup"><span data-stu-id="740f9-107">Estimated time to complete this lesson: **5 minutes**</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="740f9-108">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="740f9-108">Prerequisites</span></span>  
 <span data-ttu-id="740f9-109">本主題是表格式模型教學課程的一部分，請依序完成。</span><span class="sxs-lookup"><span data-stu-id="740f9-109">This topic is part of a tabular modeling tutorial, which should be completed in order.</span></span> <span data-ttu-id="740f9-110">在執行本課程的工作之前，您應已完成上一課： [第 13 課：在 Excel 中進行分析](lesson-12-analyze-in-excel.md)。</span><span class="sxs-lookup"><span data-stu-id="740f9-110">Before performing the tasks in this lesson, you should have completed the previous lesson: [Lesson 13: Analyze in Excel](lesson-12-analyze-in-excel.md).</span></span>  
  
## <a name="deploy-the-model"></a><span data-ttu-id="740f9-111">部署模型</span><span class="sxs-lookup"><span data-stu-id="740f9-111">Deploy the Model</span></span>  
  
#### <a name="to-configure-deployment-properties"></a><span data-ttu-id="740f9-112">設定部署屬性</span><span class="sxs-lookup"><span data-stu-id="740f9-112">To configure deployment properties</span></span>  
  
1.  <span data-ttu-id="740f9-113">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 的**方案總管**中，以滑鼠右鍵按一下 **Adventure Works Internet Sales Tabular Model** 專案，然後在操作功能表中按一下 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="740f9-113">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], in **Solution Explorer**, right-click on the **Adventure Works Internet Sales Tabular Model** project, and then in the context menu, click **Properties**.</span></span>  
  
2.  <span data-ttu-id="740f9-114">在 [AW Internet Sales Tabular Model 屬性頁]\*\*\*\* 對話方塊中的 [部署伺服器]\*\*\*\* 底下，於 [伺服器]\*\*\*\* 屬性中輸入以表格式模式執行的 Analysis Services 執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="740f9-114">In the **AW Internet Sales Tabular Model Property Pages** dialog box, under **Deployment Server**, in the **Server** property, type the name of an Analysis Services instance running in Tabular mode.</span></span> <span data-ttu-id="740f9-115">您會將模型部署到這個執行個體中。</span><span class="sxs-lookup"><span data-stu-id="740f9-115">This will be the instance your model will be deployed to.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="740f9-116">您必須具有遠端 Analysis Services 執行個體的系統管理員權限，才能部署到該執行個體。</span><span class="sxs-lookup"><span data-stu-id="740f9-116">You must have Administrator permissions on a remote Analysis Services instance in-order to deploy to it.</span></span>  
  
3.  <span data-ttu-id="740f9-117">確認 [**查詢模式]** 屬性設定為 [**記憶體**內部]。</span><span class="sxs-lookup"><span data-stu-id="740f9-117">Verify the **Query Mode** property is set to **In-Memory**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="740f9-118">DirectQuery 模式不支援使用本教學課程建立的模型。</span><span class="sxs-lookup"><span data-stu-id="740f9-118">The model created by using this tutorial is not supported in DirectQuery mode.</span></span>  
  
4.  <span data-ttu-id="740f9-119">在 [**資料庫**] 屬性中，輸入 `Adventure Works Internet Sales Model` 。</span><span class="sxs-lookup"><span data-stu-id="740f9-119">In the **Database** property, type `Adventure Works Internet Sales Model`.</span></span>  
  
5.  <span data-ttu-id="740f9-120">在 [ **Cube**名稱] 屬性中，輸入 `Adventure Works Internet Sales Model` 。</span><span class="sxs-lookup"><span data-stu-id="740f9-120">In the **Cube** Name property, type `Adventure Works Internet Sales Model`.</span></span>  
  
6.  <span data-ttu-id="740f9-121">驗證您的選取項目，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="740f9-121">Verify your selections and then click **OK**.</span></span>  
  
#### <a name="to-deploy-the-adventure-works-internet-sales-tabular-model"></a><span data-ttu-id="740f9-122">若要部署 Adventure Works Internet Sales 表格式模型</span><span class="sxs-lookup"><span data-stu-id="740f9-122">To deploy the Adventure Works Internet Sales tabular model</span></span>  
  
1.  <span data-ttu-id="740f9-123">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 中，按一下 [建立]\*\*\*\* 功能表，然後按一下 [Deploy AW Internet Sales Tabular Model (部署 AW Internet Sales Tabular Model)]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="740f9-123">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click the **Build** menu, and then click **Deploy AW Internet Sales Tabular Model**.</span></span>  
  
     <span data-ttu-id="740f9-124">[部署] 對話方塊隨即出現，並且顯示中繼資料以及模型中每個資料表的部署狀態。</span><span class="sxs-lookup"><span data-stu-id="740f9-124">The Deploy dialog box appears and displays the deployment status of the metadata as well as each table included in the model.</span></span>  
  
## <a name="conclusion"></a><span data-ttu-id="740f9-125">結論</span><span class="sxs-lookup"><span data-stu-id="740f9-125">Conclusion</span></span>  
 <span data-ttu-id="740f9-126">恭喜！</span><span class="sxs-lookup"><span data-stu-id="740f9-126">Congratulations!</span></span> <span data-ttu-id="740f9-127">您已完成撰寫和部署第一個 Analysis Services 表格式模型。</span><span class="sxs-lookup"><span data-stu-id="740f9-127">You are finished authoring and deploying your first Analysis Services tabular model.</span></span> <span data-ttu-id="740f9-128">本教學課程已幫助您完成建立表格式模型最常執行的工作。</span><span class="sxs-lookup"><span data-stu-id="740f9-128">This tutorial has helped guide you through completing the most common tasks in creating a tabular model.</span></span> <span data-ttu-id="740f9-129">現在您已部署了 Adventure Works Internet Sales Model，就可以使用 SQL Server Management Studio 管理此模型，並且建立處理序指令碼及備份計畫。</span><span class="sxs-lookup"><span data-stu-id="740f9-129">Now that your Adventure Works Internet Sales Model is deployed, you can use SQL Server Management Studio to manage the model; create process scripts and a backup plan.</span></span> <span data-ttu-id="740f9-130">使用者可以使用報表用戶端應用程式 (例如 Microsoft Excel 或 [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)]) 連接到此模型。</span><span class="sxs-lookup"><span data-stu-id="740f9-130">Users can connect to the model using a reporting client application such as Microsoft Excel or [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)].</span></span>  
  
## <a name="additional-resources"></a><span data-ttu-id="740f9-131">其他資源</span><span class="sxs-lookup"><span data-stu-id="740f9-131">Additional Resources</span></span>  
 <span data-ttu-id="740f9-132">若要深入了解支援 [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] 報表的表格式模型屬性，請參閱 [Power View 報表屬性 &#40;SSAS 表格式&#41;](tabular-models/properties-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="740f9-132">To learn more about tabular model properties that support [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] reports, see [Power View Reporting Properties &#40;SSAS Tabular&#41;](tabular-models/properties-ssas-tabular.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="740f9-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="740f9-133">See Also</span></span>  
 <span data-ttu-id="740f9-134">[&#40;SSAS 表格式&#41;的 DirectQuery 模式](tabular-models/directquery-mode-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="740f9-134">[DirectQuery Mode &#40;SSAS Tabular&#41;](tabular-models/directquery-mode-ssas-tabular.md) </span></span>  
 <span data-ttu-id="740f9-135">[&#40;SSAS 表格式&#41;設定預設的資料模型和部署屬性](tabular-models/configure-default-data-modeling-and-deployment-properties-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="740f9-135">[Configure Default Data Modeling and Deployment Properties &#40;SSAS Tabular&#41;](tabular-models/configure-default-data-modeling-and-deployment-properties-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="740f9-136">表格式模型資料庫 &#40;SSAS 表格式&#41;</span><span class="sxs-lookup"><span data-stu-id="740f9-136">Tabular Model Databases &#40;SSAS Tabular&#41;</span></span>](tabular-models/tabular-model-databases-ssas-tabular.md)  
  
  
