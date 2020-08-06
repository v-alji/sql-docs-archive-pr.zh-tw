---
title: 步驟 1：建置部署公用程式 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 1ff4dcff-89b3-4b99-a725-5f7963e98abf
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3d32dcbf4bfcf9758dfe58803b75094d1807aa90
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596114"
---
# <a name="step-1-building-the-deployment-utility"></a><span data-ttu-id="58fe4-102">步驟 1:建置部署公用程式</span><span class="sxs-lookup"><span data-stu-id="58fe4-102">Step 1: Building the Deployment Utility</span></span>
  <span data-ttu-id="58fe4-103">在這項工作中，您將設定並建立「部署教學課程」專案的部署公用程式。</span><span class="sxs-lookup"><span data-stu-id="58fe4-103">In this task, you will configure and build a deployment utility for the Deployment Tutorial project.</span></span>  
  
 <span data-ttu-id="58fe4-104">您必須先修改「部署教學課程」專案的屬性，才能建立部署公用程式。</span><span class="sxs-lookup"><span data-stu-id="58fe4-104">Before you can build the deployment utility, you must modify the properties of the Deployment Tutorial project.</span></span> <span data-ttu-id="58fe4-105">您將使用 [Deployment Tutorial Property Pages (部署教學課程屬性頁)]  對話方塊來設定這些屬性。</span><span class="sxs-lookup"><span data-stu-id="58fe4-105">You will use the **Deployment Tutorial Property Pages** dialog box to configure these properties.</span></span> <span data-ttu-id="58fe4-106">在這個對話方塊中，您必須啟用能夠在部署期間更新組態的能力，而且指定建立期間產生部署公用程式。</span><span class="sxs-lookup"><span data-stu-id="58fe4-106">In this dialog box, you must enable the ability to update configurations during deployment and specify that the build process generates a deployment utility.</span></span> <span data-ttu-id="58fe4-107">在設定完屬性後，您將建立專案。</span><span class="sxs-lookup"><span data-stu-id="58fe4-107">After you set the properties, you will build the project.</span></span>  
  
 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] <span data-ttu-id="58fe4-108">提供一組可用來偵錯套件的視窗。</span><span class="sxs-lookup"><span data-stu-id="58fe4-108">provides a set of windows that you can use to debug packages.</span></span> <span data-ttu-id="58fe4-109">您可以檢視錯誤、警告和資訊訊息、在執行階段追蹤有關封裝的狀態，或是檢視建立過程的進度及結果。</span><span class="sxs-lookup"><span data-stu-id="58fe4-109">You can view error, warning, and information messages, track about the status of packages at run time, or view the progress and results of build processes.</span></span> <span data-ttu-id="58fe4-110">在本課程中，您將使用 [輸出] 視窗來檢視建立部署公用程式的進度及結果。</span><span class="sxs-lookup"><span data-stu-id="58fe4-110">For this lesson, you will use the Output window to view the progress and results of building the deployment utility.</span></span>  
  
### <a name="to-set-the-deployment-utility-properties"></a><span data-ttu-id="58fe4-111">設定部署公用程式屬性</span><span class="sxs-lookup"><span data-stu-id="58fe4-111">To set the deployment utility properties</span></span>  
  
1.  <span data-ttu-id="58fe4-112">如果尚未開啟 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]，請按一下 [開始]  ，依序指向 [所有程式]  和 [Microsoft SQL Server]  ，然後按一下 [Business Intelligence Development Studio]  。</span><span class="sxs-lookup"><span data-stu-id="58fe4-112">If [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] is not already open, click **Start**, point to **All Programs**, point to **Microsoft SQL Server**, and then click **Business Intelligence Development Studio**.</span></span>  
  
2.  <span data-ttu-id="58fe4-113">在 [檔案]  功能表上，依序按一下 [開啟]  、[專案/方案]  和 [部署教學課程]  資料夾，然後按一下 [開啟]  ，再按兩下 [Deployment Tutorial.sln]  。</span><span class="sxs-lookup"><span data-stu-id="58fe4-113">On the **File** menu, click **Open**, click **Project/Solution**, click the **Deployment Tutorial** folder and click **Open**, and then double-click **Deployment Tutorial.sln**.</span></span>  
  
3.  <span data-ttu-id="58fe4-114">在方案總管中，以滑鼠右鍵按一下 [Deployment Tutorial (部署教學課程)]，然後按一下 [屬性]  。</span><span class="sxs-lookup"><span data-stu-id="58fe4-114">In Solution Explorer, right-click Deployment Tutorial and click **Properties**.</span></span>  
  
4.  <span data-ttu-id="58fe4-115">在 [Deployment Tutorial Property Pages (部署教學課程屬性頁)]  對話方塊中，展開 [組態屬性]，然後按一下 [部署公用程式]。</span><span class="sxs-lookup"><span data-stu-id="58fe4-115">In the **Deployment Tutorial Property Pages** dialog box, expand Configuration Properties, and click Deployment Utility.</span></span>  
  
5.  <span data-ttu-id="58fe4-116">在 [**部署教學課程屬性頁**] 對話方塊的右窗格中，確認 `AllowConfigurationChanges` 已設定為 `true` 、將設 `CreateDeploymentUtility` 為 `true` ，並選擇性地更新的預設值 `DeploymentOutputPath` 。</span><span class="sxs-lookup"><span data-stu-id="58fe4-116">In the right pane of the **Deployment Tutorial Property Pages** dialog box, verify that `AllowConfigurationChanges` is set to `true`, set `CreateDeploymentUtility` to `true`, and optionally update the default value of `DeploymentOutputPath`.</span></span>  
  
6.  <span data-ttu-id="58fe4-117">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="58fe4-117">Click **OK**.</span></span>  
  
### <a name="to-build-the-deployment-utility"></a><span data-ttu-id="58fe4-118">建立部署公用程式</span><span class="sxs-lookup"><span data-stu-id="58fe4-118">To build the deployment utility</span></span>  
  
1.  <span data-ttu-id="58fe4-119">在方案總管中，按一下 [Deployment Tutorial (部署教學課程)]  。</span><span class="sxs-lookup"><span data-stu-id="58fe4-119">In Solution Explorer, click **Deployment Tutorial**.</span></span>  
  
2.  <span data-ttu-id="58fe4-120">在 [檢視]  功能表上，按一下 [輸出]  。</span><span class="sxs-lookup"><span data-stu-id="58fe4-120">On the **View** menu, click **Output**.</span></span> <span data-ttu-id="58fe4-121">根據預設值，[輸出] 視窗是位在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]的左下角。</span><span class="sxs-lookup"><span data-stu-id="58fe4-121">By default, the Output window is located in the bottom left corner of [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
3.  <span data-ttu-id="58fe4-122">在 [建立]  功能表上，按一下 [Build Deployment Tutorial (建立部署教學課程)]  。</span><span class="sxs-lookup"><span data-stu-id="58fe4-122">On the **Build** menu, click **Build Deployment Tutorial**.</span></span>  
  
4.  <span data-ttu-id="58fe4-123">在 [輸出] 視窗中，確認以下資訊：</span><span class="sxs-lookup"><span data-stu-id="58fe4-123">In the Output window, verify the following information:</span></span>  
  
     <span data-ttu-id="58fe4-124">已經開始建立: SQL Integration Services 專案: 累加 ...</span><span class="sxs-lookup"><span data-stu-id="58fe4-124">Build started: SQL Integration Services project: Incremental ...</span></span>  
  
     <span data-ttu-id="58fe4-125">正在建立部署公用程式...</span><span class="sxs-lookup"><span data-stu-id="58fe4-125">Creating deployment utility...</span></span>  
  
     <span data-ttu-id="58fe4-126">已建立部署公用程式。</span><span class="sxs-lookup"><span data-stu-id="58fe4-126">Deployment Utility created.</span></span>  
  
     <span data-ttu-id="58fe4-127">建立已完成 -- 0 個錯誤，0 個警告</span><span class="sxs-lookup"><span data-stu-id="58fe4-127">Build complete -- 0 errors, 0 warnings</span></span>  
  
     <span data-ttu-id="58fe4-128">========== 建置: 0 成功、0 失敗、1 最新、0 略過 ==========</span><span class="sxs-lookup"><span data-stu-id="58fe4-128">========== Build: 0 succeeded, 0 failed, 1 up-to-date, 0 skipped ==========</span></span>  
  
5.  <span data-ttu-id="58fe4-129">在 **[檔案]** 功能表上按一下 **[結束]** 。</span><span class="sxs-lookup"><span data-stu-id="58fe4-129">On the **File** menu, click **Exit**.</span></span> <span data-ttu-id="58fe4-130">如果出現對 [Deployment Tutorial (部署教學課程)] 項目儲存變更的提示，請按一下 [是]  。</span><span class="sxs-lookup"><span data-stu-id="58fe4-130">If prompted to save changes to Deployment Tutorial items, click **Yes**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="58fe4-131">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="58fe4-131">Next Task in Lesson</span></span>  
 [<span data-ttu-id="58fe4-132">步驟 2：確認部署配套</span><span class="sxs-lookup"><span data-stu-id="58fe4-132">Step 2: Verifying the Deployment Bundle</span></span>](../integration-services/lesson-2-2-verifying-the-deployment-bundle.md)  
  
<span data-ttu-id="58fe4-133">![Integration Services 圖示 (小型) ](media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="58fe4-133">![Integration Services icon (small)](media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="58fe4-134">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="58fe4-134">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="58fe4-135">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="58fe4-135">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="58fe4-136">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="58fe4-136">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58fe4-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="58fe4-137">See Also</span></span>  
 [<span data-ttu-id="58fe4-138">建立部署公用程式</span><span class="sxs-lookup"><span data-stu-id="58fe4-138">Create a Deployment Utility</span></span>](../../2014/integration-services/create-a-deployment-utility.md)  
  
  
