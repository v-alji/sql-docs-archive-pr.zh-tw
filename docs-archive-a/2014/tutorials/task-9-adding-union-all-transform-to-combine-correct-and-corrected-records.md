---
title: 工作9：加入聯集全部轉換來結合正確和更正的記錄 |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 24ba466d-a7d3-49e7-9111-b348399c9e58
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 83afb5ea9367660048fe36d00ab59d808da17b81
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710042"
---
# <a name="task-9-adding-union-all-transform-to-combine-correct-and-corrected-records"></a><span data-ttu-id="78b18-102">工作 9：新增聯集全部轉換來結合正確和更正的記錄</span><span class="sxs-lookup"><span data-stu-id="78b18-102">Task 9: Adding Union All Transform to Combine Correct and Corrected Records</span></span>
  <span data-ttu-id="78b18-103">在這項工作，您會將聯集全部轉換加入至資料流程。</span><span class="sxs-lookup"><span data-stu-id="78b18-103">In this task, you add the Union All Transform to the data flow.</span></span> <span data-ttu-id="78b18-104">「聯集全部」轉換會將多項輸入結合至單一輸出。</span><span class="sxs-lookup"><span data-stu-id="78b18-104">The Union All transformation combines multiple inputs into one output.</span></span> <span data-ttu-id="78b18-105">在您的案例中，它會將正確和已更正的記錄結合到一個資料流中。</span><span class="sxs-lookup"><span data-stu-id="78b18-105">In your scenario, it combine both Correct and Corrected records into one stream.</span></span>  
  
1.  <span data-ttu-id="78b18-106">從 [ **SSIS 工具箱**] 的 [**通用**] 區段將 [**全部**轉換] 拖放至 [**資料流程**] 索引標籤，並放在 [**挑選正確和已更正的記錄**] 下。</span><span class="sxs-lookup"><span data-stu-id="78b18-106">Drag-drop **Union All** Transform from **Common** section of the **SSIS Toolbox** to the **Data Flow** tab and place it under **Pick Correct and Corrected Records**.</span></span>  
  
2.  <span data-ttu-id="78b18-107">以滑鼠右鍵按一下 [**資料流程**] 索引標籤中的 [**全部聯集**]，然後按一下 [**重新命名**]。</span><span class="sxs-lookup"><span data-stu-id="78b18-107">Right-click **Union All** Transform in the **Data Flow** tab, and click **Rename**.</span></span> <span data-ttu-id="78b18-108">輸入**結合正確和已更正的記錄**，然後按**enter**鍵。</span><span class="sxs-lookup"><span data-stu-id="78b18-108">Type **Combine Correct and Corrected Records**, and press **ENTER**.</span></span>  
  
     <span data-ttu-id="78b18-109">![結合正確與更正的記錄](../../2014/tutorials/media/et-addinguattocombinecacrecords-01.jpg "結合正確與更正的記錄")</span><span class="sxs-lookup"><span data-stu-id="78b18-109">![Combine Correct and Corrected Reocrds](../../2014/tutorials/media/et-addinguattocombinecacrecords-01.jpg "Combine Correct and Corrected Reocrds")</span></span>  
  
3.  <span data-ttu-id="78b18-110">連接**挑選正確和已更正的記錄**，以使用藍色連接器結合 [**資料流程**] 索引標籤中**正確和已更正的記錄**。</span><span class="sxs-lookup"><span data-stu-id="78b18-110">Connect **Pick Correct and Corrected Records** to **Combine Correct and Corrected Records** in the **Data Flow** tab by using the blue connector.</span></span> <span data-ttu-id="78b18-111">您應該會看到 [**輸入輸出選擇**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="78b18-111">You should see the **Input Output Selection** dialog box.</span></span>  
  
4.  <span data-ttu-id="78b18-112">在 [**輸入輸出**] 對話方塊中，針對 [**輸出**] 選取 [**正確**]，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="78b18-112">In the **Input Output** dialog box, select **Correct** for **Output** and click **OK**.</span></span>  
  
     <span data-ttu-id="78b18-113">![[輸入輸出選擇] 對話方塊](../../2014/tutorials/media/et-addinguattocombinecacrecords-02.jpg "[輸入輸出選擇] 對話方塊")</span><span class="sxs-lookup"><span data-stu-id="78b18-113">![Input Output Selection Dialog Box](../../2014/tutorials/media/et-addinguattocombinecacrecords-02.jpg "Input Output Selection Dialog Box")</span></span>  
  
5.  <span data-ttu-id="78b18-114">將標題為 [**正確**] 的連接器移至左邊，並將其拖放至左邊的連接器結尾。</span><span class="sxs-lookup"><span data-stu-id="78b18-114">Move the connector titled **Correct** to the left by dragging and dropping the dot at the end of the connector to left.</span></span>  
  
     <span data-ttu-id="78b18-115">![將 [正確] 連接至 [結合正確與更正]](../../2014/tutorials/media/et-addinguattocombinecacrecords-03.jpg "將 [正確] 連接至 [結合正確與更正]")</span><span class="sxs-lookup"><span data-stu-id="78b18-115">![Connect Correct to Combine Correct and Corrected](../../2014/tutorials/media/et-addinguattocombinecacrecords-03.jpg "Connect Correct to Combine Correct and Corrected")</span></span>  
  
6.  <span data-ttu-id="78b18-116">如果您選取 [**挑選正確和已更正的記錄**] 轉換，您應該會看到另一個藍色的連接器。</span><span class="sxs-lookup"><span data-stu-id="78b18-116">If you select **Pick Correct and Corrected Records** transform, you should see another blue connector.</span></span> <span data-ttu-id="78b18-117">拖曳藍色接頭以**結合正確和已更正的記錄**。</span><span class="sxs-lookup"><span data-stu-id="78b18-117">Drag that blue connector to **Combine Correct and Corrected Records**.</span></span>  
  
     <span data-ttu-id="78b18-118">![將 [更正] 連接至 [結合正確與更正]](../../2014/tutorials/media/et-addinguattocombinecacrecords-04.jpg "將 [更正] 連接至 [結合正確與更正]")</span><span class="sxs-lookup"><span data-stu-id="78b18-118">![Connect Corrected to Combine Correct and Corrected](../../2014/tutorials/media/et-addinguattocombinecacrecords-04.jpg "Connect Corrected to Combine Correct and Corrected")</span></span>  
  
7.  <span data-ttu-id="78b18-119">此**連接器**的標題應為 [已**更正**]。</span><span class="sxs-lookup"><span data-stu-id="78b18-119">This **connector** should be titled **Corrected**.</span></span> <span data-ttu-id="78b18-120">因為您只有兩個條件**正確**和已**更正**，而且有一個條件已在使用中，所以這次不會顯示 [**輸入輸出選擇**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="78b18-120">Since you have only two conditions **Correct** and **Corrected**, and one condition was already used, the **Input Output Selection** dialog box is not displayed this time.</span></span> <span data-ttu-id="78b18-121">如果連接器重疊，請將連接器往左或往右拖曳，將其中一個往左移，將另一個往右移。</span><span class="sxs-lookup"><span data-stu-id="78b18-121">If the connectors overlap, move one to left and the other one to right by dragging the connector to left or right.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="78b18-122">後續步驟</span><span class="sxs-lookup"><span data-stu-id="78b18-122">Next Step</span></span>  
 [<span data-ttu-id="78b18-123">工作 10：新增模糊群組轉換來識別重複項</span><span class="sxs-lookup"><span data-stu-id="78b18-123">Task 10: Adding Fuzzy Group Transform to Identify Duplicates</span></span>](../../2014/tutorials/task-10-adding-fuzzy-group-transform-to-identify-duplicates.md)  
  
  
