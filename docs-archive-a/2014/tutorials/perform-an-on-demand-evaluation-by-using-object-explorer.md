---
title: 使用物件總管執行隨選評估 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: ee6d3b79-18bc-49d3-8a1d-0c0905b990f0
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: e32876978ac462af361986d84e11ef3dc0f278e2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584903"
---
# <a name="perform-an-on-demand-evaluation-by-using-object-explorer"></a><span data-ttu-id="efd8b-102">使用物件總管執行視需要評估</span><span class="sxs-lookup"><span data-stu-id="efd8b-102">Perform an On-Demand Evaluation by Using Object Explorer</span></span>
  <span data-ttu-id="efd8b-103">在這項工作中，您將使用 [物件總管]，針對 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] 的單一執行個體，為 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 執行最佳作法原則的視需要評估。</span><span class="sxs-lookup"><span data-stu-id="efd8b-103">In this task, you will use Object Explorer to perform an on-demand evaluation of best practices policies for the [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] on a single instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="efd8b-104">您也可以透過已註冊的伺服器評估單一執行個體的原則。</span><span class="sxs-lookup"><span data-stu-id="efd8b-104">You can also evaluate policies on a single instance through Registered Servers.</span></span> <span data-ttu-id="efd8b-105">如需詳細資訊，請參閱[使用已註冊的伺服器執行隨選評估](../../2014/tutorials/perform-an-on-demand-evaluation-by-using-registered-servers.md)。</span><span class="sxs-lookup"><span data-stu-id="efd8b-105">For more information, see [Perform an On-Demand Evaluation by Using Registered Servers](../../2014/tutorials/perform-an-on-demand-evaluation-by-using-registered-servers.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="efd8b-106">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="efd8b-106">Prerequisites</span></span>  
 <span data-ttu-id="efd8b-107">這一課是以 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 的 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 版本為基礎。</span><span class="sxs-lookup"><span data-stu-id="efd8b-107">This lesson is based on the version of [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] from [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="efd8b-108">若要針對執行中的實例執行最佳作法原則的視需要評估 [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] ，您必須使用使用[已註冊的伺服器執行隨選評估](../../2014/tutorials/perform-an-on-demand-evaluation-by-using-registered-servers.md)主題中的程式。</span><span class="sxs-lookup"><span data-stu-id="efd8b-108">To perform an on-demand evaluation of best practices policies against instances that are running [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)], you must use the procedure in the topic [Perform an On-Demand Evaluation by Using Registered Servers](../../2014/tutorials/perform-an-on-demand-evaluation-by-using-registered-servers.md).</span></span>  
  
### <a name="to-perform-an-on-demand-evaluation-by-using-object-explorer"></a><span data-ttu-id="efd8b-109">若要使用物件總管執行視需要評估</span><span class="sxs-lookup"><span data-stu-id="efd8b-109">To perform an on-demand evaluation by using Object Explorer</span></span>  
  
1.  <span data-ttu-id="efd8b-110">啟動 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]，然後連接至 [!INCLUDE[ssDE](../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="efd8b-110">Start [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], and then connect to the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="efd8b-111">在物件總管中，展開 [**管理**]，展開 [**原則管理**]，以滑鼠右鍵按一下 [**原則**]，然後按一下 [**評估**]。</span><span class="sxs-lookup"><span data-stu-id="efd8b-111">In Object Explorer, expand **Management**, expand **Policy Management**, right-click **Policies**, and then click **Evaluate**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="efd8b-112">根據預設，本機執行個體會當做原則來源使用。</span><span class="sxs-lookup"><span data-stu-id="efd8b-112">By default, the local instance is used as the source of the policies.</span></span> <span data-ttu-id="efd8b-113">如果您先前已匯入最佳做法原則，則會列出這些原則以及您已經建立的其他所有原則。</span><span class="sxs-lookup"><span data-stu-id="efd8b-113">If you have previously imported best practices policies, they will be listed, together with any other policies that you have created.</span></span> <span data-ttu-id="efd8b-114">您可以選取任何匯入的最佳做法原則，然後按一下 [**評估**]。</span><span class="sxs-lookup"><span data-stu-id="efd8b-114">You can select any of the imported best practices policies, and then click **Evaluate**.</span></span> <span data-ttu-id="efd8b-115">如果您尚未匯入最佳做法原則，請繼續此程序。</span><span class="sxs-lookup"><span data-stu-id="efd8b-115">If you have not imported the best practices policies, continue with this procedure.</span></span>  
  
3.  <span data-ttu-id="efd8b-116">在 [**評估原則**] 對話方塊中，按一下 [**來源**] 方塊旁的省略號 (**...**) ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="efd8b-116">In the **Evaluate Policies** dialog box, next to the **Source** box, click the ellipsis (**...**) button.</span></span>  
  
4.  <span data-ttu-id="efd8b-117">在 [**選取來源**] 對話方塊中，您可以選取 [檔案 **] 或 [** **伺服器**] 做為要評估之原則檔案的來源。</span><span class="sxs-lookup"><span data-stu-id="efd8b-117">In the **Select Source** dialog box, you can select either **Files** or **Server** as the source of the policy files to evaluate.</span></span> <span data-ttu-id="efd8b-118">如果您按一下 [**伺服器**]，可以針對先前匯入本機或遠端伺服器上以原則為基礎之管理的任何最佳作法原則，執行視需要評估。</span><span class="sxs-lookup"><span data-stu-id="efd8b-118">If you click **Server**, you can perform an on-demand evaluation of any best practices policies that were previously imported into Policy-Based Management on a local or remote server.</span></span> <span data-ttu-id="efd8b-119">在本教學課程**中，您將按一下 [** 檔案]，然後選取您想要評估的個別原則檔案。</span><span class="sxs-lookup"><span data-stu-id="efd8b-119">In this tutorial, you will click **Files**, and then select the individual policy files that you want to evaluate.</span></span> <span data-ttu-id="efd8b-120">若要這樣做，請執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="efd8b-120">To do this, follow these steps:</span></span>  
  
    1.  <span data-ttu-id="efd8b-121">按一下 **[** 檔案]。</span><span class="sxs-lookup"><span data-stu-id="efd8b-121">Click **Files**.</span></span>  
  
    2.  <span data-ttu-id="efd8b-122">在 [檔案]**旁，按一下**省略號 (**...**) ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="efd8b-122">Next to **Files**, click the ellipsis (**...**) button.</span></span>  
  
    3.  <span data-ttu-id="efd8b-123">在 [**選取原則**] 對話方塊中，流覽至包含最佳作法原則的下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="efd8b-123">In the **Select Policy** dialog box, browse to the following folder, which contains the best practices policies:</span></span>  
  
         <span data-ttu-id="efd8b-124">**C:\Program Files (x86)\Microsoft SQL Server\110\Tools\Policies\DatabaseEngine\1033**</span><span class="sxs-lookup"><span data-stu-id="efd8b-124">**C:\Program Files (x86)\Microsoft SQL Server\110\Tools\Policies\DatabaseEngine\1033**</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="efd8b-125">檔案路徑可能會隨著您安裝 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 程式檔案的位置、執行 32 位元或 64 位元作業系統，以及語言識別碼而有所不同。</span><span class="sxs-lookup"><span data-stu-id="efd8b-125">The file path may vary, depending on where you installed the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] program files, whether you are running a 32-bit or 64-bit operating system, and the language identifier.</span></span>  
  
    4.  <span data-ttu-id="efd8b-126">選取一或多個要評估的 .xml 原則檔案，然後按一下 [**開啟**]。</span><span class="sxs-lookup"><span data-stu-id="efd8b-126">Select one or more .xml policy files to evaluate, and then click **Open**.</span></span>  
  
         <span data-ttu-id="efd8b-127">選取的檔案清單會出現**在 [檔案**] 方塊中。</span><span class="sxs-lookup"><span data-stu-id="efd8b-127">The list of selected files appears in the **Files** box.</span></span>  
  
    5.  <span data-ttu-id="efd8b-128">在 [**選取來源**] 對話方塊中，按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="efd8b-128">In the **Select Source** dialog box, click **OK**.</span></span>  
  
    6.  <span data-ttu-id="efd8b-129">如果出現 [**正在載入原則**] 對話方塊，請按一下 [**關閉**]。</span><span class="sxs-lookup"><span data-stu-id="efd8b-129">If the **Loading Policies** dialog box appears, click **Close**.</span></span>  
  
     <span data-ttu-id="efd8b-130">您選取的原則會列在 [**原則選取**] 頁面上。</span><span class="sxs-lookup"><span data-stu-id="efd8b-130">The policies that you selected are listed on the **Policy Selection** page.</span></span> <span data-ttu-id="efd8b-131">請注意，原則旁邊的警告圖示表示該原則包含指令碼。</span><span class="sxs-lookup"><span data-stu-id="efd8b-131">Be aware that a warning icon next to a policy indicates that the policy contains scripts.</span></span>  
  
5.  <span data-ttu-id="efd8b-132">按一下 [**評估**] 以評估原則。</span><span class="sxs-lookup"><span data-stu-id="efd8b-132">Click **Evaluate** to evaluate the policies.</span></span>  
  
     <span data-ttu-id="efd8b-133">在 [**結果**] 資料表中，會列出每個原則的結果。</span><span class="sxs-lookup"><span data-stu-id="efd8b-133">In the **Results** table, the results for each policy are listed.</span></span> <span data-ttu-id="efd8b-134">紅色的 "x" 圖示表示原則符合失敗。</span><span class="sxs-lookup"><span data-stu-id="efd8b-134">A red "x" icon indicates that policy compliance failed.</span></span>  
  
6.  <span data-ttu-id="efd8b-135">對於某些原則失敗，以原則為基礎的管理可讓您立即強制符合目標上的原則。</span><span class="sxs-lookup"><span data-stu-id="efd8b-135">For some policy failures, Policy-Based Management enables you to immediately enforce policy compliance on the target.</span></span> <span data-ttu-id="efd8b-136">若是此類失敗，失敗的原則旁邊會出現一個核取方塊。</span><span class="sxs-lookup"><span data-stu-id="efd8b-136">For such failures, a check box will appear next to the failed policy.</span></span> <span data-ttu-id="efd8b-137">如果您**選取此核取方塊，[套用**] 按鈕就會變成可用。</span><span class="sxs-lookup"><span data-stu-id="efd8b-137">If you select the check box, the **Apply** button becomes available.</span></span> <span data-ttu-id="efd8b-138">當**您按一下 [** 套用] 時，將會自動更新目標實例上不符合規範的設定。</span><span class="sxs-lookup"><span data-stu-id="efd8b-138">When you click **Apply**, the noncompliant setting will be automatically updated on the target instance.</span></span>  
  
    > [!CAUTION]  
    >  <span data-ttu-id="efd8b-139">請在自動更新目標執行個體之前，確認您完全了解原則設定。</span><span class="sxs-lookup"><span data-stu-id="efd8b-139">Make sure that you fully understand the policy setting before automatically updating a target instance.</span></span> <span data-ttu-id="efd8b-140">我們建議您在選取一個或多個核取方塊後，按一下 [**腳本**]，然後選擇輸出位置，以便您可以在套用 [!INCLUDE[tsql](../includes/tsql-md.md)] 變更之前，先檢查基礎程式碼。</span><span class="sxs-lookup"><span data-stu-id="efd8b-140">We recommend that after you select one or more check boxes, you click **Script**, and choose an output location so that you can review the underlying [!INCLUDE[tsql](../includes/tsql-md.md)] code before you apply the changes.</span></span>  
  
7.  <span data-ttu-id="efd8b-141">若要查看原則的詳細結果，請按一下 [**結果**] 資料表中的原則。</span><span class="sxs-lookup"><span data-stu-id="efd8b-141">To view detailed results for a policy, click the policy in the **Results** table.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="efd8b-142">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="efd8b-142">Next Task in Lesson</span></span>  
 [<span data-ttu-id="efd8b-143">使用已註冊的伺服器執行指定評估</span><span class="sxs-lookup"><span data-stu-id="efd8b-143">Perform an On-Demand Evaluation by Using Registered Servers</span></span>](../../2014/tutorials/perform-an-on-demand-evaluation-by-using-registered-servers.md)  
  
  
