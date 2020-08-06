---
title: 工作1：定義比對原則 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 6f89a720-fce5-4f60-bef3-a159bbc9f25c
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: bb2556874174939c46d91c6d89e797393d590914
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585709"
---
# <a name="task-1-defining-a-matching-policy"></a><span data-ttu-id="ed24f-102">工作 1：定義比對原則</span><span class="sxs-lookup"><span data-stu-id="ed24f-102">Task 1: Defining a Matching Policy</span></span>
  <span data-ttu-id="ed24f-103">在這項工作中，您會建立包含一個規則的比對原則。</span><span class="sxs-lookup"><span data-stu-id="ed24f-103">In this task, you create a matching policy with one rule in it.</span></span> <span data-ttu-id="ed24f-104">此規則會有一個必要條件：**供應商識別碼**，這表示供應商識別碼必須符合，才能使用規則中的其他網域。</span><span class="sxs-lookup"><span data-stu-id="ed24f-104">The rule will have one prerequisite: **Supplier ID**, which means that the Supplier IDs must match before using the other domains in the rule.</span></span> <span data-ttu-id="ed24f-105">此規則會使用其他兩個網域： [**具有相似性**的**供應商名稱**] 值設為 [ **70%** ] **，並將**[**相似性**] 值設為**30%**。</span><span class="sxs-lookup"><span data-stu-id="ed24f-105">The rule uses two other domains: **Supplier Name** with **Similarity** value set to **70%** and **Contact Email** with **Similarity** value set to **30%**.</span></span>  
  
1.  <span data-ttu-id="ed24f-106">在**DQS 用戶端**的主頁面中，按一下 [**供應商**知識庫] 旁的**向右箭**號，然後選取 [比對**原則**]。</span><span class="sxs-lookup"><span data-stu-id="ed24f-106">In the main page of **DQS Client**, click **right-arrow** next to **Suppliers** knowledge base, and select **Matching Policy**.</span></span>  
  
     <span data-ttu-id="ed24f-107">![主頁面上的 [比對原則] 功能表](../../2014/tutorials/media/et-definingamatchingpolicy-01.jpg "主頁面上的 [比對原則] 功能表")</span><span class="sxs-lookup"><span data-stu-id="ed24f-107">![Matching Policy Menu on Main Page](../../2014/tutorials/media/et-definingamatchingpolicy-01.jpg "Matching Policy Menu on Main Page")</span></span>  
  
2.  <span data-ttu-id="ed24f-108">在 [**對應**] 頁面上，針對 [**資料來源**] 選取 [ **Excel**檔案]。</span><span class="sxs-lookup"><span data-stu-id="ed24f-108">On the **Map** page, select **Excel File** for **Data Source**.</span></span>  
  
3.  <span data-ttu-id="ed24f-109">按一下 **[流覽]**，確認 [篩選] 設定為 [ **Excel 活頁簿**]，然後選取您在執行清理活動之後所匯出的**清理供應商 List.xls**檔案。</span><span class="sxs-lookup"><span data-stu-id="ed24f-109">Click **Browse**, ensure that filter is set to **Excel Workbook**, and select **Cleansed Supplier List.xls** file that you exported after you perform the cleansing activity.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ed24f-110">在此活動結束時，您將無法匯出結果，因為此活動主要著重於定義比對原則。</span><span class="sxs-lookup"><span data-stu-id="ed24f-110">At the end of this activity, you cannot export results because this activity is primarily focused on defining a matching policy.</span></span> <span data-ttu-id="ed24f-111">您將會針對比對活動建立資料品質專案，並在下一課使用這個比對原則來執行專案，以便從供應商清單中移除重複項。</span><span class="sxs-lookup"><span data-stu-id="ed24f-111">You will create a Data Quality Project for the Matching activity and run it to remove duplicates from the supplier list by using this matching policy in the next lesson.</span></span>  
  
4.  <span data-ttu-id="ed24f-112">將**供應商的資料行對應至\*\*\*\*供應商識別碼**網域、**供應商名稱**資料行至**供應商名稱**網域、 **ContactEmailAddress**資料行到**連絡人電子郵件**網域。</span><span class="sxs-lookup"><span data-stu-id="ed24f-112">Map **SupplierID** column to **Supplier ID** domain, **Supplier Name** column to **Supplier Name** domain, **ContactEmailAddress** column to **Contact Email** domain.</span></span> <span data-ttu-id="ed24f-113">您只需要將來源資料行對應至定義比對原則所要使用的定義域。</span><span class="sxs-lookup"><span data-stu-id="ed24f-113">You only need to map source columns to domains that you want to use in defining the matching policy.</span></span> <span data-ttu-id="ed24f-114">在此情況下，您會提供 Supplier ID、Supplier Name 和 Contact Email 等定義域給比對原則活動使用。</span><span class="sxs-lookup"><span data-stu-id="ed24f-114">In this case, you are making the Supplier ID, Supplier Name, and Contact Email domains available for the matching policy activity.</span></span>  
  
     <span data-ttu-id="ed24f-115">![比對原則定義程序的 [對應] 頁面](../../2014/tutorials/media/et-definingamatchingpolicy-02.jpg "比對原則定義程序的 [對應] 頁面")</span><span class="sxs-lookup"><span data-stu-id="ed24f-115">![Map Page of Matching Policy Definition Process](../../2014/tutorials/media/et-definingamatchingpolicy-02.jpg "Map Page of Matching Policy Definition Process")</span></span>  
  
5.  <span data-ttu-id="ed24f-116">按 **[下一步]** 移至 [比對**原則**] 頁面，您將在其中定義比對原則，其中包含一個規則。</span><span class="sxs-lookup"><span data-stu-id="ed24f-116">Click **Next** to move to the **Matching Policy** page where you will be defining a matching policy with one rule in it.</span></span>  
  
6.  <span data-ttu-id="ed24f-117">按一下工具列上的 [建立比對**規則**] 按鈕，以在原則中建立規則。</span><span class="sxs-lookup"><span data-stu-id="ed24f-117">Click **Create a matching rule** button on the toolbar to create a rule in the policy.</span></span>  
  
     <span data-ttu-id="ed24f-118">![[建立比對規則] 工具列按鈕](../../2014/tutorials/media/et-definingamatchingpolicy-03.jpg "[建立比對規則] 工具列按鈕")</span><span class="sxs-lookup"><span data-stu-id="ed24f-118">![Create a Matching Rule Toolbar Button](../../2014/tutorials/media/et-definingamatchingpolicy-03.jpg "Create a Matching Rule Toolbar Button")</span></span>  
  
7.  <span data-ttu-id="ed24f-119">在右側的 [**規則詳細資料**] 窗格中，針對 [**規則名稱**] 輸入 [**移除重複的供應商**]。</span><span class="sxs-lookup"><span data-stu-id="ed24f-119">In the **Rule Details** pane on the right, enter **Remove Duplicate Suppliers** for the **Rule name**.</span></span>  
  
8.  <span data-ttu-id="ed24f-120">在右窗格的工具列中，按一下 [**加入新的定義域元素**]。</span><span class="sxs-lookup"><span data-stu-id="ed24f-120">Click **Add a new domain element** in the toolbar in the right pane.</span></span>  
  
     <span data-ttu-id="ed24f-121">![規則詳細資料 - [加入新的定義域項目] 按鈕](../../2014/tutorials/media/et-definingamatchingpolicy-04.jpg "規則詳細資料 - [加入新的定義域項目] 按鈕")</span><span class="sxs-lookup"><span data-stu-id="ed24f-121">![Rule Details - Add a New Domain Element Button](../../2014/tutorials/media/et-definingamatchingpolicy-04.jpg "Rule Details - Add a New Domain Element Button")</span></span>  
  
9. <span data-ttu-id="ed24f-122">選取**網域**的 [**供應商識別碼**]，然後選取 [必要條件 **] 核取方塊**。</span><span class="sxs-lookup"><span data-stu-id="ed24f-122">Select **Supplier ID** for the **domain** and select the **Prerequisite** check box.</span></span> <span data-ttu-id="ed24f-123">請注意，**相似性**會自動設定為 [**精確**]。</span><span class="sxs-lookup"><span data-stu-id="ed24f-123">Notice that **Similarity** is automatically set to **Exact**.</span></span> <span data-ttu-id="ed24f-124">藉由將**供應商識別碼**設定為**必要條件，您**可以指定兩筆記錄中此欄位的值必須傳回100% 相符，否則這些記錄不會被視為相符，而且會忽略規則中的其他子句。</span><span class="sxs-lookup"><span data-stu-id="ed24f-124">By setting **Supplier ID** as the **Prerequisite**, you specify that the values for this field in the two records must return a 100% match, else the records are not considered a match and the other clauses in the rule are disregarded.</span></span>  
  
     <span data-ttu-id="ed24f-125">![移除重複供應商規則定義](../../2014/tutorials/media/et-definingamatchingpolicy-05.jpg "移除重複供應商規則定義")</span><span class="sxs-lookup"><span data-stu-id="ed24f-125">![Remove Duplicate Suppliers Rule Definition](../../2014/tutorials/media/et-definingamatchingpolicy-05.jpg "Remove Duplicate Suppliers Rule Definition")</span></span>  
  
10. <span data-ttu-id="ed24f-126">再次按一下工具列上的 [**加入新的定義域元素**]。</span><span class="sxs-lookup"><span data-stu-id="ed24f-126">Click **Add a new domain element** from the toolbar again.</span></span>  
  
11. <span data-ttu-id="ed24f-127">選取 [**供應商名稱**] [網域]，選取 [**類似** **]，並針對 [\*\*\*\*權數**] 輸入**70** 。</span><span class="sxs-lookup"><span data-stu-id="ed24f-127">Select **Supplier Name** domain, select **Similar** for **Similarity**, and Type **70** for the **Weight**.</span></span>  <span data-ttu-id="ed24f-128">您在此指定供應商名稱不需要完全相同但可以類似，以便讓記錄視為相符。</span><span class="sxs-lookup"><span data-stu-id="ed24f-128">Here, you are specifying that supplier names do not need to be identical but can be similar for the records to be considered as a match.</span></span> <span data-ttu-id="ed24f-129">權數表示此欄位的分數占整體符合分數的比重。</span><span class="sxs-lookup"><span data-stu-id="ed24f-129">The weight indicates the contribution of this field's score to the overall matching score.</span></span>  
  
12. <span data-ttu-id="ed24f-130">重複先前的兩個步驟，為**權數**新增具有**30**的**連絡人電子郵件**網域。</span><span class="sxs-lookup"><span data-stu-id="ed24f-130">Repeat previous two steps to add **Contact Email** domain with **30** for the **Weight**.</span></span>  
  
13. <span data-ttu-id="ed24f-131">請注意，[**最小符合分數**] 設定為 [ **80%**]，這是您在**DQS 管理**的 [設定 **] 頁面的**[**一般**] 索引標籤中看到的值。</span><span class="sxs-lookup"><span data-stu-id="ed24f-131">Notice that the **min matching score** is set to **80%**, which is the value you see in the **General** tab of the **Configuration** page of **DQS Administration**.</span></span> <span data-ttu-id="ed24f-132">您在這裡只能增加這個分數，使其高於此臨界值。</span><span class="sxs-lookup"><span data-stu-id="ed24f-132">You can only increase this score above this threshold value here.</span></span>  
  
14. <span data-ttu-id="ed24f-133">請注意，已選取 [重**迭**的叢集] 選項。</span><span class="sxs-lookup"><span data-stu-id="ed24f-133">Notice that **Overlapping Clusters** option is selected.</span></span> <span data-ttu-id="ed24f-134">有了這個選項，記錄就會出現在多個叢集中。</span><span class="sxs-lookup"><span data-stu-id="ed24f-134">With this option, a record can show up in multiple clusters.</span></span> <span data-ttu-id="ed24f-135">如果您將設定變更為 [非重疊的叢集]，具有共同記錄的叢集就會結合到單一叢集中。</span><span class="sxs-lookup"><span data-stu-id="ed24f-135">If you change the setting to Non-Overlapping Clusters, the clusters that have common records are combined into one single cluster.</span></span>  
  
15. <span data-ttu-id="ed24f-136">此頁面上的 [**開始**] 按鈕可讓您分別測試原則中的每個規則，而下一個頁面中的 [開始] 按鈕可讓您測試整個原則 (原則) 中的所有規則。</span><span class="sxs-lookup"><span data-stu-id="ed24f-136">The **Start** button on this page allows you to test each rule in the policy separately, whereas, the Start button in the next page allows you to test entire policy (all the rules in the policy).</span></span>  
  
16. <span data-ttu-id="ed24f-137">按 **[下一步]** 切換至 [比對**結果**] 頁面。</span><span class="sxs-lookup"><span data-stu-id="ed24f-137">Click **Next** to switch to the **Matching Results** page.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="ed24f-138">後續步驟</span><span class="sxs-lookup"><span data-stu-id="ed24f-138">Next Step</span></span>  
 [<span data-ttu-id="ed24f-139">工作 2：測試和發行比對原則</span><span class="sxs-lookup"><span data-stu-id="ed24f-139">Task 2: Testing and Publishing the Matching Policy</span></span>](../../2014/tutorials/task-2-testing-and-publishing-the-matching-policy.md)  
  
  
