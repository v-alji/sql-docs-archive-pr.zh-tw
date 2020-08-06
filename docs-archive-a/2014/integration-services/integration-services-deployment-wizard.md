---
title: Integration Services 部署嚮導 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.deploymentwizard.f1
ms.assetid: f3d93e13-2d85-47ff-a913-cda4046491c4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9afdc529baa4546f126eb67456927e770cb345dd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705289"
---
# <a name="integration-services-deployment-wizard"></a><span data-ttu-id="c685b-102">Integration Services 部署精靈</span><span class="sxs-lookup"><span data-stu-id="c685b-102">Integration Services Deployment Wizard</span></span>
  <span data-ttu-id="c685b-103">「[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 部署精靈」會使用專案部署模型，將專案部署至 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 執行個體上的 SSISDB 目錄。</span><span class="sxs-lookup"><span data-stu-id="c685b-103">The [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] Deployment Wizard deploys projects to the SSISDB catalog on a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance using the project deployment model.</span></span>  
  
 <span data-ttu-id="c685b-104">若要 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 從中開啟的專案啟動部署嚮導 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ，請從 [**專案**] 功能表中選取 [**部署**]。</span><span class="sxs-lookup"><span data-stu-id="c685b-104">To start the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] Deployment Wizard from an open project in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], select **Deploy** from the **Project** menu.</span></span> <span data-ttu-id="c685b-105">若要在中啟動精靈 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ，請在物件總管中展開 [ **Integration Services 目錄**  >  **SSISDB** ] 節點，以滑鼠右鍵按一下 [**專案**] 資料夾，然後按一下 [**部署專案**]。</span><span class="sxs-lookup"><span data-stu-id="c685b-105">To start the wizard in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], expand the **Integration Services Catalogs** > **SSISDB** node in Object Explorer, right-click the **Projects** folder, and then click **Deploy Project**.</span></span>  
  
 <span data-ttu-id="c685b-106">此精靈會繼續進行下列四個步驟。</span><span class="sxs-lookup"><span data-stu-id="c685b-106">The wizard proceeds through the following four steps.</span></span> <span data-ttu-id="c685b-107">按 **[下一步]** 移至下一個步驟，或按一下 [**上**一步] 返回上一個步驟。</span><span class="sxs-lookup"><span data-stu-id="c685b-107">Click **Next** to move to the next step, or **Previous** to return to the previous step.</span></span>  
  
1.  <span data-ttu-id="c685b-108">**選取來源**-選取 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 您要部署的專案。</span><span class="sxs-lookup"><span data-stu-id="c685b-108">**Select Source** - Select the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that you want to deploy.</span></span>  
  
2.  <span data-ttu-id="c685b-109">**選取目的地**-選取專案目的地。</span><span class="sxs-lookup"><span data-stu-id="c685b-109">**Select Destination** - Select the project destination.</span></span>  
  
3.  <span data-ttu-id="c685b-110">**審查**-顯示您的選擇。</span><span class="sxs-lookup"><span data-stu-id="c685b-110">**Review** - Displays your selections.</span></span>  
  
4.  <span data-ttu-id="c685b-111">**部署/結果**-部署專案並顯示結果。</span><span class="sxs-lookup"><span data-stu-id="c685b-111">**Deploy/Results** - Deploys the project and displays the results.</span></span>  
  
## <a name="select-source"></a><span data-ttu-id="c685b-112">選取來源</span><span class="sxs-lookup"><span data-stu-id="c685b-112">Select Source</span></span>  
 <span data-ttu-id="c685b-113">若要部署您建立的專案部署檔案，請選取 [**專案部署**檔案]，並輸入 .ispac 檔案的路徑，或按一下 **[流覽]** ，在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 專案資料夾中尋找檔案。</span><span class="sxs-lookup"><span data-stu-id="c685b-113">To deploy a project deployment file that you created, select **Project deployment file** and enter the path to the .ispac file or click **Browse** to find it in the [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] project folder.</span></span> <span data-ttu-id="c685b-114">若要部署位於 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 目錄中的專案，請選取 **[Integration Services 目錄]**，然後輸入伺服器名稱以及該專案在目錄中的路徑。</span><span class="sxs-lookup"><span data-stu-id="c685b-114">To deploy a project that resides in the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] catalog, select **Integration Services catalog**, and then enter the server name and the path to the project in the catalog.</span></span>  
  
 <span data-ttu-id="c685b-115">如果您在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 中啟動精靈，則該精靈預設會選取已開啟的專案做為來源，並略過此步驟。</span><span class="sxs-lookup"><span data-stu-id="c685b-115">If you start the wizard in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], then by default the wizard selects the open project as the source and skips this step.</span></span> <span data-ttu-id="c685b-116">若要返回此步驟並選取不同的來源，請按一下 [**上一**步]，或按一下左窗格中的 [**選取來源**]。</span><span class="sxs-lookup"><span data-stu-id="c685b-116">To return to this step and select a different source, click **Previous** or click **Select Source** in the left pane.</span></span>  
  
## <a name="select-destination"></a><span data-ttu-id="c685b-117">選取目的地</span><span class="sxs-lookup"><span data-stu-id="c685b-117">Select Destination</span></span>  
 <span data-ttu-id="c685b-118">若要選取專案在 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 目錄中的目的地資料夾，請輸入 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 執行個體，或按一下 **[瀏覽]** ，從伺服器清單中選取。</span><span class="sxs-lookup"><span data-stu-id="c685b-118">To select the destination folder for the project in the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] catalog, enter the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance or click **Browse** to select from a list of servers.</span></span> <span data-ttu-id="c685b-119">在 SSISDB 中輸入專案路徑，或按一下 **[瀏覽]** 來選取路徑。</span><span class="sxs-lookup"><span data-stu-id="c685b-119">Enter the project path in SSISDB or click **Browse** to select it.</span></span>  
  
 <span data-ttu-id="c685b-120">如果您在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 中啟動精靈，則該精靈預設會選取已連接的伺服器執行個體，並輸入所選專案的路徑。</span><span class="sxs-lookup"><span data-stu-id="c685b-120">If you start the wizard in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], then by default the wizard selects the connected server instance and enters the path to the selected project.</span></span> <span data-ttu-id="c685b-121">您可以變更這些值，以便將專案部署至不同的位置。</span><span class="sxs-lookup"><span data-stu-id="c685b-121">You can change these values to deploy the project to a different location.</span></span>  
  
## <a name="review"></a><span data-ttu-id="c685b-122">檢閱</span><span class="sxs-lookup"><span data-stu-id="c685b-122">Review</span></span>  
 <span data-ttu-id="c685b-123">此精靈可讓您在部署專案之前，先檢閱您所選取的設定。</span><span class="sxs-lookup"><span data-stu-id="c685b-123">The wizard allows you to review the settings you have selected before deploying the project.</span></span> <span data-ttu-id="c685b-124">您可以按一下 **[上一步]**，或按一下左窗格中的任何步驟來變更您的選取項目。</span><span class="sxs-lookup"><span data-stu-id="c685b-124">You can change your selections by clicking **Previous**, or by clicking any of the steps in the left pane.</span></span>  
  
## <a name="deployresults"></a><span data-ttu-id="c685b-125">部署/結果</span><span class="sxs-lookup"><span data-stu-id="c685b-125">Deploy/Results</span></span>  
 <span data-ttu-id="c685b-126">當您從 [**審核**] 頁面按一下 [**部署**] 時，會部署專案，而 [**結果**] 頁面會顯示每個動作的成功或失敗。</span><span class="sxs-lookup"><span data-stu-id="c685b-126">When you click **Deploy** from the **Review** page, the project is deployed and the **Results** page displays the success or failure of each action.</span></span> <span data-ttu-id="c685b-127">如果動作失敗，按一下 **[結果]** 資料行中的 **[失敗]** 以顯示錯誤的說明。</span><span class="sxs-lookup"><span data-stu-id="c685b-127">If the action fails, click the **Failed** in the **Result** column to display an explanation of the error.</span></span> <span data-ttu-id="c685b-128">按一下 [**儲存報表**]，將結果儲存至 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="c685b-128">Click **Save Report...** to save the results to an XML file.</span></span>  
  
 <span data-ttu-id="c685b-129">按一下 [關閉] 結束精靈。</span><span class="sxs-lookup"><span data-stu-id="c685b-129">Click **Close** to exit the wizard.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c685b-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c685b-130">See Also</span></span>  
 <span data-ttu-id="c685b-131">[將專案部署至 Integration Services 伺服器](../../2014/integration-services/deploy-projects-to-integration-services-server.md) </span><span class="sxs-lookup"><span data-stu-id="c685b-131">[Deploy Projects to Integration Services Server](../../2014/integration-services/deploy-projects-to-integration-services-server.md) </span></span>  
 [<span data-ttu-id="c685b-132">部署專案和封裝</span><span class="sxs-lookup"><span data-stu-id="c685b-132">Deployment of Projects and Packages</span></span>](packages/deploy-integration-services-ssis-projects-and-packages.md)  
  
  
