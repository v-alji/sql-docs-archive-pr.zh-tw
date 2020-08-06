---
title: 將排程的原則部署至多個實例 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: f551b8e8-3668-4ed4-852f-bae826254f4f
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 30faf94c2033be43ac035517e58d5a18c0c68ab8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687386"
---
# <a name="deploy-scheduled-policies-to-multiple-instances"></a><span data-ttu-id="a3c35-102">將已排程的原則部署至多個執行個體</span><span class="sxs-lookup"><span data-stu-id="a3c35-102">Deploy Scheduled Policies to Multiple Instances</span></span>
  <span data-ttu-id="a3c35-103">您可以使用已註冊的伺服器，將已排程的原則從中央位置部署到 Managed 伺服器。</span><span class="sxs-lookup"><span data-stu-id="a3c35-103">By using Registered Servers, you can deploy scheduled policies to managed servers from a central location.</span></span> <span data-ttu-id="a3c35-104">您可以從本機伺服器群組，或從中央管理伺服器部署已排程的原則。</span><span class="sxs-lookup"><span data-stu-id="a3c35-104">You can deploy scheduled policies from either a local server group, or from a Central Management Server.</span></span>  
  
 <span data-ttu-id="a3c35-105">在這個工作中，您將進行下列作業：</span><span class="sxs-lookup"><span data-stu-id="a3c35-105">In this task, you will do the following:</span></span>  
  
1.  <span data-ttu-id="a3c35-106">將您在先前工作中排程的原則匯出至資料夾。</span><span class="sxs-lookup"><span data-stu-id="a3c35-106">Export the policies that you scheduled in the previous task to a folder.</span></span>  
  
2.  <span data-ttu-id="a3c35-107">將已排程的原則部署到透過已註冊的伺服器所管理的目標執行個體。</span><span class="sxs-lookup"><span data-stu-id="a3c35-107">Deploy the scheduled policies to target instances that are managed through Registered Servers.</span></span>  
  
 <span data-ttu-id="a3c35-108">您必須在已完成本課程先前工作的電腦上執行這些工作。</span><span class="sxs-lookup"><span data-stu-id="a3c35-108">You will perform these tasks on the computer where you completed the previous tasks in this lesson.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="a3c35-109">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="a3c35-109">Prerequisites</span></span>  
 <span data-ttu-id="a3c35-110">此工作的必要條件如下：</span><span class="sxs-lookup"><span data-stu-id="a3c35-110">This task has the following prerequisites:</span></span>  
  
-   <span data-ttu-id="a3c35-111">您必須先完成本課程先前的工作。</span><span class="sxs-lookup"><span data-stu-id="a3c35-111">You must have completed the previous tasks in this lesson.</span></span>  
  
-   <span data-ttu-id="a3c35-112">其上要部署已排程原則的執行個體必須是執行 [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="a3c35-112">The instances where you want to deploy the scheduled policies must be running [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] or a later version.</span></span> <span data-ttu-id="a3c35-113">若要進行自動化作業，原則必須儲存在本機位置，[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 之前的 [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] 版本不支援此功能。</span><span class="sxs-lookup"><span data-stu-id="a3c35-113">Automation requires the policies to be stored locally, which is not supported on versions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] earlier than [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)].</span></span>  
  
-   <span data-ttu-id="a3c35-114">您要部署已排程原則的伺服器，必須在 [**本機伺服器群組**] 或 [**中央管理伺服器**] 節點的 [已註冊的伺服器] 中註冊。</span><span class="sxs-lookup"><span data-stu-id="a3c35-114">The servers where you want to deploy the scheduled policies must be registered in Registered Servers in either the **Local Server Groups** or the **Central Management Servers** node.</span></span> <span data-ttu-id="a3c35-115">如需詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="a3c35-115">For more information, see the following topics:</span></span>  
  
    -   [<span data-ttu-id="a3c35-116">建立或編輯伺服器群組 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="a3c35-116">Create or Edit a Server Group &#40;SQL Server Management Studio&#41;</span></span>](../ssms/register-servers/create-or-edit-a-server-group-sql-server-management-studio.md)  
  
    -   <span data-ttu-id="a3c35-117">[&#40;SQL Server Management Studio&#41;註冊已連線的伺服器](../ssms/register-servers/register-a-connected-server-sql-server-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="a3c35-117">[Register a Connected Server &#40;SQL Server Management Studio&#41;](../ssms/register-servers/register-a-connected-server-sql-server-management-studio.md).</span></span>  
  
    -   [<span data-ttu-id="a3c35-118">建立中央管理伺服器與伺服器群組 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="a3c35-118">Create a Central Management Server and Server Group &#40;SQL Server Management Studio&#41;</span></span>](../ssms/register-servers/create-a-central-management-server-and-server-group.md)  
  
### <a name="to-export-the-scheduled-policies-as-xml-files"></a><span data-ttu-id="a3c35-119">若要將已排程的原則匯出為 .xml 檔案</span><span class="sxs-lookup"><span data-stu-id="a3c35-119">To export the scheduled policies as .xml files</span></span>  
  
1.  <span data-ttu-id="a3c35-120">在您在上一個工作中設定排程原則的伺服器上，依序展開 [**管理**]、[**原則管理**] 和 [**原則**]。</span><span class="sxs-lookup"><span data-stu-id="a3c35-120">On the server where you configured scheduled policies in the previous task, expand **Management**, expand **Policy Management**, and then click **Policies**.</span></span>  
  
2.  <span data-ttu-id="a3c35-121">在 [檢視]\*\*\*\* 功能表上，按一下 [物件總管詳細資料]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a3c35-121">On the **View** menu, click **Object Explorer Details**.</span></span>  
  
3.  <span data-ttu-id="a3c35-122">在 [**物件總管詳細資料**] 窗格中，選取您想要透過 [已註冊的伺服器] 部署到其他伺服器的所有已排程最佳做法原則。</span><span class="sxs-lookup"><span data-stu-id="a3c35-122">In the **Object Explorer Details** pane, select all the scheduled best practices policies that you want to deploy to other servers through Registered Servers.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a3c35-123">您可以按一下 [**類別**] 標題，依類別目錄來排序原則。</span><span class="sxs-lookup"><span data-stu-id="a3c35-123">You can click the **Category** heading to sort the policies by category.</span></span>  
  
4.  <span data-ttu-id="a3c35-124">以滑鼠右鍵按一下選取專案，然後按一下 [**匯出原則**]。</span><span class="sxs-lookup"><span data-stu-id="a3c35-124">Right-click the selection, and then click **Export Policy**.</span></span>  
  
5.  <span data-ttu-id="a3c35-125">如果您選取了多個要匯出的原則，請在 [**流覽資料夾**] 對話方塊中，選取目的地資料夾，或建立新的資料夾。</span><span class="sxs-lookup"><span data-stu-id="a3c35-125">If you selected multiple policies to export, in the **Browse For Folder** dialog box, select a destination folder, or create a new folder.</span></span> <span data-ttu-id="a3c35-126">在此課程中，請建立路徑為**c：\ Scheduled_BP_Policies**的新資料夾，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="a3c35-126">For this lesson, create a new folder with the path **C:\Scheduled_BP_Policies**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="a3c35-127">如果您只選取一個要匯出的原則，請在 [**匯出原則**] 對話方塊中，建立路徑為**c：\ Scheduled_BP_Policies**的新資料夾，按一下 [**開啟**]，然後按一下 [**儲存**]。</span><span class="sxs-lookup"><span data-stu-id="a3c35-127">If you only selected one policy to export, in the **Export Policy** dialog box, create a new folder with the path **C:\Scheduled_BP_Policies**, click **Open**, and then click **Save**.</span></span>  
  
     <span data-ttu-id="a3c35-128">.xml 原則檔案是建立在資料夾位置。</span><span class="sxs-lookup"><span data-stu-id="a3c35-128">The .xml policy files are created in the folder location.</span></span>  
  
### <a name="to-deploy-the-scheduled-policies-to-servers-that-are-managed-through-registered-servers"></a><span data-ttu-id="a3c35-129">若要將已排程的原則部署到透過已註冊的伺服器所管理的伺服器</span><span class="sxs-lookup"><span data-stu-id="a3c35-129">To deploy the scheduled policies to servers that are managed through Registered Servers</span></span>  
  
1.  <span data-ttu-id="a3c35-130">在 [檢視]\*\*\*\* 功能表上，按一下 [已註冊的伺服器]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a3c35-130">On the **View** menu, click **Registered Servers**.</span></span>  
  
2.  <span data-ttu-id="a3c35-131">依序展開 [**資料庫引擎**]、[**本機伺服器群組**] 或 [**中央管理伺服器**]，以滑鼠右鍵按一下您要部署原則的節點，然後按一下 [匯**入原則**]。</span><span class="sxs-lookup"><span data-stu-id="a3c35-131">Expand **Database Engine**, expand either **Local Server Groups** or **Central Management Servers**, right-click the node that you want to deploy the policies to, and then click **Import Policies**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a3c35-132">如果您以滑鼠右鍵按一下 [**本機伺服器群組**] 或 [中央管理伺服器本身]，原則就會部署到所有受管理的伺服器。</span><span class="sxs-lookup"><span data-stu-id="a3c35-132">If you right-click **Local Server Groups** or the Central Management Server itself, the policies will be deployed to all managed servers.</span></span> <span data-ttu-id="a3c35-133">如果以滑鼠右鍵按一下特定的伺服器群組，原則就只會部署到該群組中的伺服器。</span><span class="sxs-lookup"><span data-stu-id="a3c35-133">If you right-click a specific server group, the policies will only be deployed to servers in that group.</span></span> <span data-ttu-id="a3c35-134">如果以滑鼠右鍵按一下特定的已註冊伺服器，原則就只會部署到該伺服器。</span><span class="sxs-lookup"><span data-stu-id="a3c35-134">If you right-click a specific registered server, the policies will only be deployed to that server.</span></span>  
  
3.  <span data-ttu-id="a3c35-135">在 [**要匯入**的檔案] 旁，按一下省略號按鈕 (**...** ]) 。</span><span class="sxs-lookup"><span data-stu-id="a3c35-135">Next to **Files to import**, click the ellipsis button (**...**).</span></span>  
  
4.  <span data-ttu-id="a3c35-136">在 [**選取原則**] 對話方塊中，流覽至您儲存已排程原則的資料夾位置。</span><span class="sxs-lookup"><span data-stu-id="a3c35-136">In the **Select Policy** dialog box, browse to the folder location where you saved the scheduled policies.</span></span> <span data-ttu-id="a3c35-137">在此範例中，流覽至位置**c：\ Scheduled_BP_Policies**。</span><span class="sxs-lookup"><span data-stu-id="a3c35-137">For this example, browse to the location **C:\Scheduled_BP_Policies**.</span></span>  
  
5.  <span data-ttu-id="a3c35-138">選取您要匯入目標實例的原則，然後按一下 [**開啟**]。</span><span class="sxs-lookup"><span data-stu-id="a3c35-138">Select the policies that you want to import to the target instances, and then click **Open**.</span></span>  
  
6.  <span data-ttu-id="a3c35-139">在 [匯**入**] 對話方塊的 [**原則狀態**] 清單中，選取所需的原則狀態。</span><span class="sxs-lookup"><span data-stu-id="a3c35-139">In the **Import** dialog box, in the **Policy state** list, select the desired policy state.</span></span> <span data-ttu-id="a3c35-140">您可以選擇在匯入原則保留原則狀態 (啟用) 或加以停用。</span><span class="sxs-lookup"><span data-stu-id="a3c35-140">You can choose to preserve the policy state, enable, or disable the policies on import.</span></span> <span data-ttu-id="a3c35-141">請注意，原則必須啟用才能按排程執行。</span><span class="sxs-lookup"><span data-stu-id="a3c35-141">Be aware that the policies must be enabled to run on a schedule.</span></span>  
  
7.  <span data-ttu-id="a3c35-142">按一下 **[確定]** ，將原則匯入至所有目標實例。</span><span class="sxs-lookup"><span data-stu-id="a3c35-142">Click **OK** to import the policies to all the target instances.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a3c35-143">如果發生任何錯誤，[匯**入**] 對話方塊就不會消失。</span><span class="sxs-lookup"><span data-stu-id="a3c35-143">If there are any errors, the **Import** dialog box does not disappear.</span></span> <span data-ttu-id="a3c35-144">按一下 [**記錄**] 頁面來檢查訊息。</span><span class="sxs-lookup"><span data-stu-id="a3c35-144">Click the **Log** page to review the messages.</span></span> <span data-ttu-id="a3c35-145">按一下 [**取消**] 關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="a3c35-145">Click **Cancel** to close the dialog box.</span></span>  
  
8.  <span data-ttu-id="a3c35-146">若要從目標實例中查看原則，請連接到實例，開啟物件總管，展開 [**管理**]，然後展開 [**原則**]。</span><span class="sxs-lookup"><span data-stu-id="a3c35-146">To view the policies from a target instance, connect to the instance, open Object Explorer, expand **Management**, and then expand **Policies**.</span></span> <span data-ttu-id="a3c35-147">您應該會在 [**原則**] 節點中看到匯入的原則。</span><span class="sxs-lookup"><span data-stu-id="a3c35-147">You should see the imported policies in the **Policies** node.</span></span> <span data-ttu-id="a3c35-148">您可以在每個原則上按兩下來檢視排程或變更設定。</span><span class="sxs-lookup"><span data-stu-id="a3c35-148">If you double-click each policy, you can view the schedule, or change the settings.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a3c35-149">若要在已排程的原則執行後檢視評估結果，請開啟目標執行個體上的「原則記錄」記錄檔。</span><span class="sxs-lookup"><span data-stu-id="a3c35-149">To view the evaluation results after a scheduled policy runs, open the Policy History log on the target instance.</span></span> <span data-ttu-id="a3c35-150">若要開啟記錄檔，請以滑鼠右鍵按一下 [**原則管理**]，然後按一下 [**查看歷程記錄**]。</span><span class="sxs-lookup"><span data-stu-id="a3c35-150">To open the log, right-click **Policy Management**, and then click **View History**.</span></span>  
  
## <a name="summary"></a><span data-ttu-id="a3c35-151">總結</span><span class="sxs-lookup"><span data-stu-id="a3c35-151">Summary</span></span>  
 <span data-ttu-id="a3c35-152">本教學課程已為您示範如何針對 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的一個或多個執行個體，視需要或按排程來執行最佳做法原則的評估。</span><span class="sxs-lookup"><span data-stu-id="a3c35-152">This tutorial has shown you how to perform both on-demand and scheduled evaluations of the best practices policies against one or more instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="next"></a><span data-ttu-id="a3c35-153">下一個</span><span class="sxs-lookup"><span data-stu-id="a3c35-153">Next</span></span>  
 <span data-ttu-id="a3c35-154">本教學課程已完成。</span><span class="sxs-lookup"><span data-stu-id="a3c35-154">This tutorial is finished.</span></span> <span data-ttu-id="a3c35-155">若要回到開頭，請參閱[教學課程：使用以原則為基礎的管理來評估最佳作法](../../2014/tutorials/tutorial-evaluating-best-practices-by-using-policy-based-management.md)。</span><span class="sxs-lookup"><span data-stu-id="a3c35-155">To return to the start, see [Tutorial: Evaluating Best Practices by Using Policy-Based Management](../../2014/tutorials/tutorial-evaluating-best-practices-by-using-policy-based-management.md).</span></span>  
  
 <span data-ttu-id="a3c35-156">若要查看教學課程的清單 [!INCLUDE[ssDE](../includes/ssde-md.md)] ，請按一下 [[資料庫引擎教學](../relational-databases/database-engine-tutorials.md)課程]。</span><span class="sxs-lookup"><span data-stu-id="a3c35-156">To see a list of [!INCLUDE[ssDE](../includes/ssde-md.md)] tutorials, click [Database Engine Tutorials](../relational-databases/database-engine-tutorials.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3c35-157">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a3c35-157">See Also</span></span>  
 [<span data-ttu-id="a3c35-158">使用原則式管理來管理伺服器</span><span class="sxs-lookup"><span data-stu-id="a3c35-158">Administer Servers by Using Policy-Based Management</span></span>](../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)  
  
  
