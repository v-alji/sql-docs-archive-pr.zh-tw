---
title: 工作7：將 DQS 清理轉換加入至資料流程 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 0b749c71-dfb6-493a-804f-600290d46eef
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 887bc361a51b61e9137404e054bd52e2b630ca5d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592379"
---
# <a name="task-7-adding-dqs-cleansing-transform-to-the-data-flow"></a><span data-ttu-id="ba992-102">工作 7：將 DQS 清理轉換新增至資料流程</span><span class="sxs-lookup"><span data-stu-id="ba992-102">Task 7: Adding DQS Cleansing Transform to the Data Flow</span></span>
  <span data-ttu-id="ba992-103">在這項工作中，您將使用 DQS 將 DQS 清理轉換加入至資料流程來清理輸入供應商資料。</span><span class="sxs-lookup"><span data-stu-id="ba992-103">In this task, you add DQS Cleansing Transform to the data flow to cleanse the input supplier data by using DQS.</span></span> <span data-ttu-id="ba992-104">如需有關轉換的詳細資訊，請參閱**[DQS 清理轉換](https://msdn.microsoft.com/library/ee677619.aspx)**。</span><span class="sxs-lookup"><span data-stu-id="ba992-104">See **[DQS Cleansing Transform](https://msdn.microsoft.com/library/ee677619.aspx)** for more details about the transform.</span></span>  
  
1.  <span data-ttu-id="ba992-105">以滑鼠右鍵**按一下 [資料流程**] 索引標籤中的 [ **DQS 清理**]，然後按一下 [**重新命名**]</span><span class="sxs-lookup"><span data-stu-id="ba992-105">Right-click **DQS Cleansing** in the **Data Flow** tab, and click **Rename**.</span></span> <span data-ttu-id="ba992-106">輸入**清理供應商資料**，然後按**enter**。</span><span class="sxs-lookup"><span data-stu-id="ba992-106">Type **Cleanse Supplier Data**, and press **ENTER**.</span></span>  
  
2.  <span data-ttu-id="ba992-107">選取 [**從 Excel 檔案讀取供應商資料**];拖曳藍色連接器以**清理供應商資料**。</span><span class="sxs-lookup"><span data-stu-id="ba992-107">Select **Read Supplier Data from Excel File**; drag the blue connector to **Cleanse Supplier Data**.</span></span> <span data-ttu-id="ba992-108">現在已連接這些元件。</span><span class="sxs-lookup"><span data-stu-id="ba992-108">The components are now connected.</span></span>  
  
     <span data-ttu-id="ba992-109">![讀取供應商資料-> 清理供應商資料](../../2014/tutorials/media/et-addingdqscleansingtransformtothedataflow-01.jpg "讀取供應商資料-> 清理供應商資料")</span><span class="sxs-lookup"><span data-stu-id="ba992-109">![Read Supplier Data -> Cleanse Supplier Data](../../2014/tutorials/media/et-addingdqscleansingtransformtothedataflow-01.jpg "Read Supplier Data -> Cleanse Supplier Data")</span></span>  
  
3.  <span data-ttu-id="ba992-110">按兩下 [**清理供應商資料**]。</span><span class="sxs-lookup"><span data-stu-id="ba992-110">Double-click **Cleanse Supplier Data**.</span></span>  
  
4.  <span data-ttu-id="ba992-111">在 [ **DQS 清理轉換編輯器**] 中，按一下 [**資料品質連接管理員] 下拉式清單**旁邊的 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="ba992-111">In the **DQS Cleansing Transformation Editor**, click **New** next to the **Data Quality Connection Manager drop-down list**.</span></span>  
  
5.  <span data-ttu-id="ba992-112">在 [ **DQS 清理連接管理員**] 對話方塊中，輸入\*\* (local) **或**period\*\* (. ) 以連接到本機伺服器。</span><span class="sxs-lookup"><span data-stu-id="ba992-112">In the **DQS Cleansing Connection Manager** dialog box, type **(local)** or **period** (.) to connect to the local server.</span></span> <span data-ttu-id="ba992-113">本課程假設您已經在本機伺服器上安裝 DQS。</span><span class="sxs-lookup"><span data-stu-id="ba992-113">This lesson assumes that you have DQS installed on a local server.</span></span>  
  
6.  <span data-ttu-id="ba992-114">按一下 [**測試連接**] 來測試 DQS 伺服器的連接。</span><span class="sxs-lookup"><span data-stu-id="ba992-114">Click **Test Connection** to test the connection to DQS server.</span></span>  
  
7.  <span data-ttu-id="ba992-115">按一下 **[確定]** ，關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="ba992-115">Click **OK** to close the dialog box.</span></span>  
  
8.  <span data-ttu-id="ba992-116">針對 [**資料品質知識庫**] 選取 [**供應商**]。</span><span class="sxs-lookup"><span data-stu-id="ba992-116">Select **Suppliers** for the **Data Quality Knowledge Base**.</span></span>  
  
     <span data-ttu-id="ba992-117">![DQS 清理轉換編輯器 - 供應商知識庫](../../2014/tutorials/media/et-addingdqscleansingtransformtothedataflow-02.jpg "DQS 清理轉換編輯器 - 供應商知識庫")</span><span class="sxs-lookup"><span data-stu-id="ba992-117">![DQS Cleansing Transformation Editor - Suppliers KB](../../2014/tutorials/media/et-addingdqscleansingtransformtothedataflow-02.jpg "DQS Cleansing Transformation Editor - Suppliers KB")</span></span>  
  
9. <span data-ttu-id="ba992-118">切換至頂端的 [**對應**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="ba992-118">Switch to the **Mapping** tab at the top.</span></span>  
  
10. <span data-ttu-id="ba992-119">從**可用的輸入**資料行中，選取 [**供應商名稱**]、[ **ContactEmailAddress**]、[**位址線** **]、[\*\*\*\*城市**]、[**國家/地區**] 和 [**郵遞區號**]，方法是選取</span><span class="sxs-lookup"><span data-stu-id="ba992-119">From **Available Input Columns**, select **Supplier Name**, **ContactEmailAddress**, **Address Line**, **City**, **State**, **Country**, and **Zip Code** by selecting the check boxes.</span></span>  
  
     <span data-ttu-id="ba992-120">![DQS 清理轉換編輯器 - 對應](../../2014/tutorials/media/et-addingdqscleansingtransformtothedataflow-03.jpg "DQS 清理轉換編輯器 - 對應")</span><span class="sxs-lookup"><span data-stu-id="ba992-120">![DQS Cleansing Transformation Editor - Mappings](../../2014/tutorials/media/et-addingdqscleansingtransformtothedataflow-03.jpg "DQS Cleansing Transformation Editor - Mappings")</span></span>  
  
11. <span data-ttu-id="ba992-121">在底部窗格中，使用 [**定義域**] 資料行中的下拉式清單來對應這些資料行：</span><span class="sxs-lookup"><span data-stu-id="ba992-121">In the bottom pane, map these columns by using drop-down lists in the **Domain** column:</span></span>  
  
    |<span data-ttu-id="ba992-122">資料行</span><span class="sxs-lookup"><span data-stu-id="ba992-122">Column</span></span>|<span data-ttu-id="ba992-123">網域</span><span class="sxs-lookup"><span data-stu-id="ba992-123">Domain</span></span>|  
    |------------|------------|  
    |<span data-ttu-id="ba992-124">Supplier Name</span><span class="sxs-lookup"><span data-stu-id="ba992-124">Supplier Name</span></span>|<span data-ttu-id="ba992-125">Supplier Name</span><span class="sxs-lookup"><span data-stu-id="ba992-125">Supplier Name</span></span>|  
    |<span data-ttu-id="ba992-126">ContactEmailAddress</span><span class="sxs-lookup"><span data-stu-id="ba992-126">ContactEmailAddress</span></span>|<span data-ttu-id="ba992-127">連絡人電子郵件</span><span class="sxs-lookup"><span data-stu-id="ba992-127">Contact Email</span></span>|  
    |<span data-ttu-id="ba992-128">[地址行]</span><span class="sxs-lookup"><span data-stu-id="ba992-128">Address Line</span></span>|<span data-ttu-id="ba992-129">[地址行]</span><span class="sxs-lookup"><span data-stu-id="ba992-129">Address Line</span></span>|  
    |<span data-ttu-id="ba992-130">城市</span><span class="sxs-lookup"><span data-stu-id="ba992-130">City</span></span>|<span data-ttu-id="ba992-131">城市</span><span class="sxs-lookup"><span data-stu-id="ba992-131">City</span></span>|  
    |<span data-ttu-id="ba992-132">州</span><span class="sxs-lookup"><span data-stu-id="ba992-132">State</span></span>|<span data-ttu-id="ba992-133">州</span><span class="sxs-lookup"><span data-stu-id="ba992-133">State</span></span>|  
    |<span data-ttu-id="ba992-134">國家/地區</span><span class="sxs-lookup"><span data-stu-id="ba992-134">Country</span></span>|<span data-ttu-id="ba992-135">國家/地區</span><span class="sxs-lookup"><span data-stu-id="ba992-135">Country</span></span>|  
    |<span data-ttu-id="ba992-136">Zip Code</span><span class="sxs-lookup"><span data-stu-id="ba992-136">Zip Code</span></span>|<span data-ttu-id="ba992-137">Zip</span><span class="sxs-lookup"><span data-stu-id="ba992-137">Zip</span></span>|  
  
12. <span data-ttu-id="ba992-138">按一下 **[確定]** 以關閉 [ **DQS 清理轉換編輯器**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="ba992-138">Click **OK** to close the **DQS Cleansing Transformation Editor** dialog box.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="ba992-139">後續步驟</span><span class="sxs-lookup"><span data-stu-id="ba992-139">Next Step</span></span>  
 [<span data-ttu-id="ba992-140">工作 8：新增條件式分割轉換來分割清理輸出</span><span class="sxs-lookup"><span data-stu-id="ba992-140">Task 8: Adding Conditional Split Transform to Split Cleansing Output</span></span>](../../2014/tutorials/task-8-adding-conditional-split-transform-to-split-cleansing-output.md)  
  
  
