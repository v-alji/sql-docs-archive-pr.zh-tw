---
title: 工作8：新增條件式分割轉換來分割清理輸出 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: d4ebe420-a4a9-4076-89d3-41abe726fc5c
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 9be7ea6f5330382ad0417df99e18bcba5b59a4e9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584876"
---
# <a name="task-8-adding-conditional-split-transform-to-split-cleansing-output"></a><span data-ttu-id="9a0d6-102">工作 8：新增條件式分割轉換來分割清理輸出</span><span class="sxs-lookup"><span data-stu-id="9a0d6-102">Task 8: Adding Conditional Split Transform to Split Cleansing Output</span></span>
  <span data-ttu-id="9a0d6-103">在這項轉換中，您會將條件式分割轉換加入至資料流程。</span><span class="sxs-lookup"><span data-stu-id="9a0d6-103">In this transform, you add a Conditional Split Transform to the data flow.</span></span> <span data-ttu-id="9a0d6-104">「條件式分割」轉換可根據資料的內容，將資料列路由傳送至不同的輸出。</span><span class="sxs-lookup"><span data-stu-id="9a0d6-104">The Conditional Split transformation can route rows to different outputs based on the content of the data.</span></span> <span data-ttu-id="9a0d6-105">在本教學課程中，您會使用 DQS 清理轉換中的 [**記錄狀態**輸出] 資料行。</span><span class="sxs-lookup"><span data-stu-id="9a0d6-105">For this tutorial, you use the **Record Status** output column from the DQS Cleansing transform.</span></span> <span data-ttu-id="9a0d6-106">在本教學課程中，您只會將正確或已更正的記錄上傳到 MDS 伺服器。</span><span class="sxs-lookup"><span data-stu-id="9a0d6-106">You will upload only correct or corrected records to MDS server in this tutorial.</span></span> <span data-ttu-id="9a0d6-107">因此，您會檢查**記錄狀態**是否**正確**或已**更正**，並在將記錄上傳至 MDS 之前，先合併記錄。</span><span class="sxs-lookup"><span data-stu-id="9a0d6-107">Therefore you check if the **Record Status** is **Correct** or **Corrected**, and combine the records before uploading the records to MDS.</span></span>  
  
1.  <span data-ttu-id="9a0d6-108">從 [ **SSIS 工具箱**] 中的 [**一般**] 區段，將 [**條件式分割轉換**] 拖放至 [**清理供應商資料**] 底下的 **[資料流程]**</span><span class="sxs-lookup"><span data-stu-id="9a0d6-108">Drag-drop **Conditional Split Transform** from **Common** section in the **SSIS Toolbox** to the **Data Flow** tab under **Cleanse Supplier Data**.</span></span>  
  
2.  <span data-ttu-id="9a0d6-109">以滑鼠右鍵按一下 [**條件式分割**]，然後按一下 [**重新命名**]。</span><span class="sxs-lookup"><span data-stu-id="9a0d6-109">Right-click **Conditional Split**, and click **Rename**.</span></span> <span data-ttu-id="9a0d6-110">輸入**挑選正確和已更正的記錄**，然後按**enter**。</span><span class="sxs-lookup"><span data-stu-id="9a0d6-110">Type **Pick Correct and Corrected Records** and press **ENTER**.</span></span>  
  
3.  <span data-ttu-id="9a0d6-111">連接**清理供應商資料**，並使用藍色連接器**挑選正確和已更正的記錄**。</span><span class="sxs-lookup"><span data-stu-id="9a0d6-111">Connect **Cleanse Supplier Data** and **Pick Correct and Corrected Records** using the blue connector.</span></span>  
  
     <span data-ttu-id="9a0d6-112">![清理供應商資料-> 挑選正確 & 更正](../../2014/tutorials/media/et-addingcsttosplitcleansingoutput-01.jpg "清理供應商資料 -> 挑選 [正確] 與 [更正]")</span><span class="sxs-lookup"><span data-stu-id="9a0d6-112">![Cleanse Supplier Data -> Pick Correct & Corrected](../../2014/tutorials/media/et-addingcsttosplitcleansingoutput-01.jpg "Cleanse Supplier Data -> Pick Correct & Corrected")</span></span>  
  
4.  <span data-ttu-id="9a0d6-113">按兩下 [**資料流程**] 索引標籤中的 [**挑選正確和已更正的記錄**]。</span><span class="sxs-lookup"><span data-stu-id="9a0d6-113">Double-click **Pick Correct and Corrected Records** in the **Data Flow** tab.</span></span>  
  
5.  <span data-ttu-id="9a0d6-114">將畫面底部的**預設輸出名稱**變更為 [**更正**]。</span><span class="sxs-lookup"><span data-stu-id="9a0d6-114">Change the **Default Output Name** at the bottom of the screen to **Correct**.</span></span>  
  
6.  <span data-ttu-id="9a0d6-115">展開**左上方窗格**中的 [資料**行**]。</span><span class="sxs-lookup"><span data-stu-id="9a0d6-115">Expand **Columns** in the **top-left pane**.</span></span>  
  
     <span data-ttu-id="9a0d6-116">![條件式分割轉換編輯器](../../2014/tutorials/media/et-addingcsttosplitcleansingoutput-02.jpg "條件式分割轉換編輯器")</span><span class="sxs-lookup"><span data-stu-id="9a0d6-116">![Conditional Split Transformation Editor](../../2014/tutorials/media/et-addingcsttosplitcleansingoutput-02.jpg "Conditional Split Transformation Editor")</span></span>  
  
7.  <span data-ttu-id="9a0d6-117">將 [**記錄狀態**] 拖放至 [**條件**] 資料行。</span><span class="sxs-lookup"><span data-stu-id="9a0d6-117">Drag-drop **Record Status** to the **Condition** column.</span></span>  
  
8.  <span data-ttu-id="9a0d6-118">在 [**條件**] 資料行的 **[記錄狀態]** 旁，輸入 **= = "已更正"** 。</span><span class="sxs-lookup"><span data-stu-id="9a0d6-118">Type **=="Corrected"** next to **[Record Status]** for the **Condition** column.</span></span>  
  
9. <span data-ttu-id="9a0d6-119">在 [**輸出名稱**] 資料行中按一下 [**案例 1** ]，並將名稱變更為 [已**更正**]。</span><span class="sxs-lookup"><span data-stu-id="9a0d6-119">Click **Case 1** in the **Output Name Column**, and change the name to **Corrected**.</span></span>  
  
10. <span data-ttu-id="9a0d6-120">按一下 **[確定]** 以關閉 [**條件式分割轉換編輯器**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="9a0d6-120">Click **OK** to close the **Conditional Split Transformation Editor** dialog box.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="9a0d6-121">後續步驟</span><span class="sxs-lookup"><span data-stu-id="9a0d6-121">Next Step</span></span>  
 [<span data-ttu-id="9a0d6-122">工作 9：新增聯集全部轉換來結合正確和更正的記錄</span><span class="sxs-lookup"><span data-stu-id="9a0d6-122">Task 9: Adding Union All Transform to Combine Correct and Corrected Records</span></span>](../../2014/tutorials/task-9-adding-union-all-transform-to-combine-correct-and-corrected-records.md)  
  
  
