---
title: 使用已註冊的伺服器來執行隨選評估 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: c14034ef-6e0b-4df5-8072-bfb8d90b3172
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: a3a06efaabff7e94e5b560744f0e1c739831042a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584904"
---
# <a name="perform-an-on-demand-evaluation-by-using-registered-servers"></a><span data-ttu-id="43cff-102">使用已註冊的伺服器執行指定評估</span><span class="sxs-lookup"><span data-stu-id="43cff-102">Perform an On-Demand Evaluation by Using Registered Servers</span></span>

  <span data-ttu-id="43cff-103">您可以使用已註冊的伺服器，針對 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的一個或多個執行個體執行最佳作法原則的指定評估。</span><span class="sxs-lookup"><span data-stu-id="43cff-103">You can perform an on-demand evaluation of best practices policies against one or more instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] by using Registered Servers.</span></span> <span data-ttu-id="43cff-104">您可以使用本機伺服器群組或中央管理伺服器。</span><span class="sxs-lookup"><span data-stu-id="43cff-104">You can use either local server groups or a central management server.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="43cff-105">您可以針對執行 [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] 或 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 更新版本的伺服器群組成員執行最佳作法原則的指定評估。</span><span class="sxs-lookup"><span data-stu-id="43cff-105">You can perform an on-demand evaluation of best practices policies against server group members that are running [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] or a later version of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="43cff-106">不過，如果有一些 [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] 或 [!INCLUDE[ssVersion2000](../includes/ssversion2000-md.md)] 中不支援之原則參考的屬性，您可能會收到例外狀況錯誤。</span><span class="sxs-lookup"><span data-stu-id="43cff-106">However, you may receive an exception error if there are some properties that are referred to by a policy that are not supported in [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] or [!INCLUDE[ssVersion2000](../includes/ssversion2000-md.md)].</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="43cff-107">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="43cff-107">Prerequisites</span></span>  
 <span data-ttu-id="43cff-108">若要執行這個工作，必須已經在已註冊的伺服器中設定一個或多個伺服器註冊。</span><span class="sxs-lookup"><span data-stu-id="43cff-108">To perform this task, you must have configured one or more server registrations in Registered Servers.</span></span> <span data-ttu-id="43cff-109">如需詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="43cff-109">For more information, see the following topics:</span></span>  
  
-   [<span data-ttu-id="43cff-110">建立或編輯伺服器群組 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="43cff-110">Create or Edit a Server Group &#40;SQL Server Management Studio&#41;</span></span>](../ssms/register-servers/create-or-edit-a-server-group-sql-server-management-studio.md)  
  
-   <span data-ttu-id="43cff-111">[&#40;SQL Server Management Studio&#41;註冊已連線的伺服器](../ssms/register-servers/register-a-connected-server-sql-server-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="43cff-111">[Register a Connected Server &#40;SQL Server Management Studio&#41;](../ssms/register-servers/register-a-connected-server-sql-server-management-studio.md).</span></span>  
  
-   [<span data-ttu-id="43cff-112">建立中央管理伺服器與伺服器群組 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="43cff-112">Create a Central Management Server and Server Group &#40;SQL Server Management Studio&#41;</span></span>](../ssms/register-servers/create-a-central-management-server-and-server-group.md)  
  
### <a name="to-evaluate-best-practices-policies-against-a-server-group"></a><span data-ttu-id="43cff-113">若要針對伺服器群組評估最佳做法原則</span><span class="sxs-lookup"><span data-stu-id="43cff-113">To evaluate best practices policies against a server group</span></span>  
  
1.  <span data-ttu-id="43cff-114">在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]的 **[檢視]** 功能表中，按一下 **[已註冊的伺服器]** 。</span><span class="sxs-lookup"><span data-stu-id="43cff-114">In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], on the **View** menu, click **Registered Servers**.</span></span>  
  
2.  <span data-ttu-id="43cff-115">展開 [**資料庫引擎**]，然後展開 [**本機伺服器群組**] 或 [**中央管理伺服器**]，視您的設定而定。</span><span class="sxs-lookup"><span data-stu-id="43cff-115">Expand **Database Engine**, and then expand either **Local Server Groups**, or **Central Management Servers**, depending on your configuration.</span></span>  
  
3.  <span data-ttu-id="43cff-116">執行下列任一步驟：</span><span class="sxs-lookup"><span data-stu-id="43cff-116">Do either of the following:</span></span>  
  
    -   <span data-ttu-id="43cff-117">若要針對本機伺服器群組或中央管理伺服器所管理的所有伺服器來評估原則，請以滑鼠右鍵按一下本機伺服器組名或中央管理伺服器名稱，然後按一下 [**評估原則**]。</span><span class="sxs-lookup"><span data-stu-id="43cff-117">To evaluate the policies against all servers that are managed by the local server group or the central management server, right-click the local server group name or the central management server name, and then click **Evaluate Policies**.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="43cff-118">當您透過中央管理伺服器管理原則時，不會針對中央管理伺服器本身評估原則。</span><span class="sxs-lookup"><span data-stu-id="43cff-118">When you evaluate policies through a central management server, the policies are not evaluated against the central management server itself.</span></span>  
  
    -   <span data-ttu-id="43cff-119">若要針對特定伺服器或伺服器群組評估原則，請展開 [**本機伺服器群組**] 或 [中央管理伺服器名稱]，以滑鼠右鍵按一下您想要評估原則的伺服器或伺服器群組，然後按一下 [**評估原則**]。</span><span class="sxs-lookup"><span data-stu-id="43cff-119">To evaluate the policies against a specific server or server group, expand **Local Server Groups** or the central management server name, right-click the server or server group that you want to evaluate policies against, and then click **Evaluate Policies**.</span></span>  
  
4.  <span data-ttu-id="43cff-120">在 [**評估原則**] 對話方塊中，按一下 [**來源**] 方塊旁的省略號 (**...**) ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="43cff-120">In the **Evaluate Policies** dialog box, next to the **Source** box, click the ellipsis (**...**) button.</span></span>  
  
5.  <span data-ttu-id="43cff-121">在 [**選取來源**] 對話方塊中，您可以選取 [檔案 **] 或 [** **伺服器**] 做為要評估之原則檔案的來源。</span><span class="sxs-lookup"><span data-stu-id="43cff-121">In the **Select Source** dialog box, you can select either **Files** or **Server** as the source of the policy files to evaluate.</span></span> <span data-ttu-id="43cff-122">如果您按一下 [**伺服器**]，可以針對先前匯入本機或遠端伺服器上以原則為基礎之管理的任何最佳作法原則，執行視需要評估。</span><span class="sxs-lookup"><span data-stu-id="43cff-122">If you click **Server**, you can perform an on-demand evaluation of any best practices policies that were previously imported into Policy-Based Management on a local or remote server.</span></span> <span data-ttu-id="43cff-123">在本教學課程**中，您將按一下 [** 檔案]，然後選取您想要評估的個別原則檔案。</span><span class="sxs-lookup"><span data-stu-id="43cff-123">In this tutorial, you will click **Files**, and then select the individual policy files that you want to evaluate.</span></span> <span data-ttu-id="43cff-124">若要這樣做，請執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="43cff-124">To do this, follow these steps:</span></span>  
  
    1.  <span data-ttu-id="43cff-125">按一下 **[** 檔案]。</span><span class="sxs-lookup"><span data-stu-id="43cff-125">Click **Files**.</span></span>  
  
    2.  <span data-ttu-id="43cff-126">在 [檔案]**旁，按一下**省略號 (**...**) ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="43cff-126">Next to **Files**, click the ellipsis (**...**) button.</span></span>  
  
    3.  <span data-ttu-id="43cff-127">選取一或多個要評估的 .xml 原則檔案，然後按一下 [**開啟**]。</span><span class="sxs-lookup"><span data-stu-id="43cff-127">Select one or more .xml policy files to evaluate, and then click **Open**.</span></span>  
  
         <span data-ttu-id="43cff-128">選取的檔案清單會出現**在 [檔案**] 方塊中。</span><span class="sxs-lookup"><span data-stu-id="43cff-128">The list of selected files appears in the **Files** box.</span></span>  
  
    4.  <span data-ttu-id="43cff-129">在 [**選取來源**] 對話方塊中，按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="43cff-129">In the **Select Source** dialog box, click **OK**.</span></span>  
  
    5.  <span data-ttu-id="43cff-130">如果出現 [**正在載入原則**] 對話方塊，請按一下 [**關閉**]。</span><span class="sxs-lookup"><span data-stu-id="43cff-130">If the **Loading Policies** dialog box appears, click **Close**.</span></span>  
  
     <span data-ttu-id="43cff-131">您選取的原則會列在 [**原則選取**] 頁面上。</span><span class="sxs-lookup"><span data-stu-id="43cff-131">The policies that you selected are listed on the **Policy Selection** page.</span></span> <span data-ttu-id="43cff-132">請注意，原則旁邊的警告圖示表示該原則包含指令碼。</span><span class="sxs-lookup"><span data-stu-id="43cff-132">Be aware that a warning icon next to a policy indicates that the policy contains scripts.</span></span>  
  
6.  <span data-ttu-id="43cff-133">按一下 [**評估**] 以評估原則。</span><span class="sxs-lookup"><span data-stu-id="43cff-133">Click **Evaluate** to evaluate the policies.</span></span>  
  
7.  <span data-ttu-id="43cff-134">對於某些原則失敗，以原則為基礎的管理可讓您立即強制符合目標上的原則。</span><span class="sxs-lookup"><span data-stu-id="43cff-134">For some policy failures, Policy-Based Management enables you to immediately enforce policy compliance on the target.</span></span> <span data-ttu-id="43cff-135">若是此類失敗，失敗的原則旁邊會出現一個核取方塊。</span><span class="sxs-lookup"><span data-stu-id="43cff-135">For such failures, a check box will appear next to the failed policy.</span></span> <span data-ttu-id="43cff-136">如果您選取此核取方塊，或按一下具有失敗原則的資料列，核取方塊就會出現在評估失敗的目標實例旁的 [**目標詳細資料**] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="43cff-136">If you select the check box, or click the row with the failed policy, check boxes appear in the **Target details** pane next to the target instances that failed the evaluation.</span></span> <span data-ttu-id="43cff-137">如果選取了任何核取方塊，[套用]**按鈕就**會變成可用。</span><span class="sxs-lookup"><span data-stu-id="43cff-137">If any of the check boxes are selected, the **Apply** button becomes available.</span></span> <span data-ttu-id="43cff-138">當**您按一下 [** 套用] 時，將會在您選取的目標實例上自動更新不符合規範的設定。</span><span class="sxs-lookup"><span data-stu-id="43cff-138">When you click **Apply**, the noncompliant setting will be automatically updated on the target instances that you selected.</span></span>  
  
    > [!CAUTION]  
    >  <span data-ttu-id="43cff-139">請在自動更新目標執行個體之前，確認您完全了解原則設定。</span><span class="sxs-lookup"><span data-stu-id="43cff-139">Make sure that you fully understand the policy setting before automatically updating a target instance.</span></span> <span data-ttu-id="43cff-140">我們建議您在選取一個或多個核取方塊後，按一下 [**腳本**]，然後選擇輸出位置，以便您可以在套用 [!INCLUDE[tsql](../includes/tsql-md.md)] 變更之前，先檢查基礎程式碼。</span><span class="sxs-lookup"><span data-stu-id="43cff-140">We recommend that after you select one or more check boxes, you click **Script**, and choose an output location so that you can review the underlying [!INCLUDE[tsql](../includes/tsql-md.md)] code before you apply the changes.</span></span>  
  
8.  <span data-ttu-id="43cff-141">若要查看原則的詳細結果，請按一下 [**結果**] 資料表中的原則。</span><span class="sxs-lookup"><span data-stu-id="43cff-141">To view detailed results for a policy, click the policy in the **Results** table.</span></span> <span data-ttu-id="43cff-142">[**目標詳細資料**] 資料表會顯示每個實例的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="43cff-142">The **Target details** table shows the details for each instance.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="43cff-143">下一課</span><span class="sxs-lookup"><span data-stu-id="43cff-143">Next Lesson</span></span>  
 [<span data-ttu-id="43cff-144">第 2 課：根據排程評估最佳做法原則</span><span class="sxs-lookup"><span data-stu-id="43cff-144">Lesson 2: Evaluate Best Practices Policies on a Scheduled Basis</span></span>](../../2014/tutorials/lesson-2-evaluate-best-practices-policies-on-a-scheduled-basis.md)  
  
## <a name="see-also"></a><span data-ttu-id="43cff-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="43cff-145">See Also</span></span>  
 <span data-ttu-id="43cff-146">[使用以原則為基礎的管理來監視和強制執行最佳作法](../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md) </span><span class="sxs-lookup"><span data-stu-id="43cff-146">[Monitor and Enforce Best Practices by Using Policy-Based Management](../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md) </span></span>  
 [<span data-ttu-id="43cff-147">使用中央管理伺服器管理多部伺服器</span><span class="sxs-lookup"><span data-stu-id="43cff-147">Administer Multiple Servers Using Central Management Servers</span></span>](../relational-databases/administer-multiple-servers-using-central-management-servers.md)  
  
  
