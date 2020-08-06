---
title: 排程原則 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: 59417a54-55f1-4468-ba41-368aa852c2d4
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 1bce1b9d650606e9485899c34c72ca6b27a72dae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704441"
---
# <a name="schedule-the-policies"></a><span data-ttu-id="10f32-102">排程原則</span><span class="sxs-lookup"><span data-stu-id="10f32-102">Schedule the Policies</span></span>
  <span data-ttu-id="10f32-103">在這項工作中，您將會排程匯入至先前工作中的最佳作法原則。</span><span class="sxs-lookup"><span data-stu-id="10f32-103">In this task, you will schedule the best practices policies that you imported in the previous task.</span></span>  
  
### <a name="to-schedule-the-best-practices-policies"></a><span data-ttu-id="10f32-104">若要排程最佳做法原則</span><span class="sxs-lookup"><span data-stu-id="10f32-104">To schedule the best practices policies</span></span>  
  
1.  <span data-ttu-id="10f32-105">在物件總管中，依序展開 [**管理**]、[**原則管理**] 和 [**原則**]，以滑鼠右鍵按一下最佳作法原則，然後按一下 [**屬性**]。</span><span class="sxs-lookup"><span data-stu-id="10f32-105">In Object Explorer, expand **Management**, expand **Policy Management**, expand **Policies**, right-click a best practices policy, and then click **Properties**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="10f32-106">或者，若要輕鬆查看與最佳作法相關聯的原則，以及排序最佳做法分類，請展開 [**管理**]，展開 [**原則管理**]，然後按一下 [**原則**]。</span><span class="sxs-lookup"><span data-stu-id="10f32-106">As an alternative, to easily see which policies are associated with best practices and to sort the best practices categories, expand **Management**, expand **Policy Management**, and then click **Policies**.</span></span> <span data-ttu-id="10f32-107">在 [檢視]\*\*\*\* 功能表上，按一下 [物件總管詳細資料]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="10f32-107">On the **View** menu, click **Object Explorer Details**.</span></span> <span data-ttu-id="10f32-108">在 [**物件總管詳細資料**] 窗格中，按一下 [**類別**] 標題，依類別目錄來排序原則。</span><span class="sxs-lookup"><span data-stu-id="10f32-108">In the **Object Explorer Details** pane, click the **Category** heading to sort the policies by category.</span></span> <span data-ttu-id="10f32-109">最佳做法原則的前置詞為**Microsoft 的最佳作法**。</span><span class="sxs-lookup"><span data-stu-id="10f32-109">The best practices policies have the prefix **Microsoft Best Practices**.</span></span> <span data-ttu-id="10f32-110">以滑鼠右鍵按一下您要設定的原則，然後按一下 [**屬性**]。</span><span class="sxs-lookup"><span data-stu-id="10f32-110">Right-click the policy that you want to configure, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="10f32-111">在 [**開啟原則**] 對話方塊的 [**一般**] 頁面上，按一下 [**評估模式**] 清單中的 [**排程**]。</span><span class="sxs-lookup"><span data-stu-id="10f32-111">On the **General** page of the **Open Policy** dialog box, in the **Evaluation Mode** list, click **On schedule**.</span></span>  
  
3.  <span data-ttu-id="10f32-112">在 [**排程**] 方塊旁，按一下 [**挑選**] 指定現有的排程，或按一下 [**新增**] 建立新的排程。</span><span class="sxs-lookup"><span data-stu-id="10f32-112">Next to the **Schedule** box, click **Pick** to specify an existing schedule, or click **New** to create a new schedule.</span></span>  
  
4.  <span data-ttu-id="10f32-113">設定排程之後，您可以選取接近頁面頂端的 [**已啟用**] 核取方塊，以啟用排定的原則。</span><span class="sxs-lookup"><span data-stu-id="10f32-113">After you have configured a schedule, you can select the **Enabled** check box near the top of the page to enable the scheduled policy.</span></span>  
  
5.  <span data-ttu-id="10f32-114">針對您要排程的每個原則重複步驟 1 到步驟 4。</span><span class="sxs-lookup"><span data-stu-id="10f32-114">Repeats steps 1 through 4 for each policy that you want to schedule.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="10f32-115">若要在已排程的原則執行後檢視評估結果，請開啟目標執行個體上的「原則記錄」記錄檔。</span><span class="sxs-lookup"><span data-stu-id="10f32-115">To view the evaluation results after a scheduled policy runs, open the Policy History log on the target instance.</span></span> <span data-ttu-id="10f32-116">若要開啟記錄檔，請以滑鼠右鍵按一下 [**原則管理**]，然後按一下 [**查看歷程記錄**]。</span><span class="sxs-lookup"><span data-stu-id="10f32-116">To open the log, right-click **Policy Management**, and then click **View History**.</span></span>  
  
## <a name="summary"></a><span data-ttu-id="10f32-117">總結</span><span class="sxs-lookup"><span data-stu-id="10f32-117">Summary</span></span>  
 <span data-ttu-id="10f32-118">您設定排程的原則針對單一 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 執行個體執行。</span><span class="sxs-lookup"><span data-stu-id="10f32-118">You configured scheduled policies to run on a single instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="10f32-119">如果您要將排程的原則部署至多個執行個體，請繼續本教學課程中的下一個工作。</span><span class="sxs-lookup"><span data-stu-id="10f32-119">If you want to deploy scheduled policies to multiple instances, continue to the next task in this tutorial.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="10f32-120">後續步驟</span><span class="sxs-lookup"><span data-stu-id="10f32-120">Next Steps</span></span>  
 [<span data-ttu-id="10f32-121">將已排程的原則部署至多個執行個體</span><span class="sxs-lookup"><span data-stu-id="10f32-121">Deploy Scheduled Policies to Multiple Instances</span></span>](../../2014/tutorials/deploy-scheduled-policies-to-multiple-instances.md)  
  
  
