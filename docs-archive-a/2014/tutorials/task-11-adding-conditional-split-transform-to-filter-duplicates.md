---
title: 工作11：新增條件式分割轉換來篩選重複專案 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 3094bd57-5cf4-4860-bf51-fadd1b309f94
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: e8370563c4275df0d0513d5434a8b16efba728d0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710046"
---
# <a name="task-11-adding-conditional-split-transform-to-filter-duplicates"></a><span data-ttu-id="f2511-102">工作 11：新增條件式分割轉換來篩選重複項</span><span class="sxs-lookup"><span data-stu-id="f2511-102">Task 11: Adding Conditional Split Transform to Filter Duplicates</span></span>
  <span data-ttu-id="f2511-103">在這項工作中，您會將條件式分割轉換加入至資料流程。</span><span class="sxs-lookup"><span data-stu-id="f2511-103">In this task, you add the Conditional Split Transform to the data flow.</span></span> <span data-ttu-id="f2511-104">此轉換可幫助您篩選傳入記錄集中的重複項。</span><span class="sxs-lookup"><span data-stu-id="f2511-104">This transform helps you filter duplicates from the incoming record set.</span></span> <span data-ttu-id="f2511-105">模糊群組轉換會將它找到的相符記錄群組在一起，並挑選其中一筆記錄當做樞紐記錄。</span><span class="sxs-lookup"><span data-stu-id="f2511-105">The Fuzzy Group transform groups the records that it finds to be matches and picks one of the records as a pivot record.</span></span> <span data-ttu-id="f2511-106">群組中的所有記錄都有相同的 _key_out 值。</span><span class="sxs-lookup"><span data-stu-id="f2511-106">All the records in a group have the same _key_out value.</span></span> <span data-ttu-id="f2511-107">群組中的樞紐記錄的 _key_in 值與 _key_out 值相同。</span><span class="sxs-lookup"><span data-stu-id="f2511-107">The pivot record in the group has _key_in same as the _key_out value.</span></span> <span data-ttu-id="f2511-108">群組中其他記錄的 _key_in 和 _key_out 值不同。</span><span class="sxs-lookup"><span data-stu-id="f2511-108">The other records in the group have different values for _key_in and _key_out.</span></span> <span data-ttu-id="f2511-109">因此，當您使用 _key_in==_key_out 條件篩選時，您只會得到群組中的樞紐資料列。</span><span class="sxs-lookup"><span data-stu-id="f2511-109">Therefore, when you filter using the condition _key_in==_key_out, you only get the pivot row in the group.</span></span>  
  
1.  <span data-ttu-id="f2511-110">從 [ **SSIS 工具箱**] 中的 [**通用**] 區段將 [**條件式分割**轉換] 拖放至 [**資料流程**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="f2511-110">Drag-drop **Conditional Split** Transform from **Common** section in the **SSIS Toolbox** to the **Data Flow** tab.</span></span>  
  
2.  <span data-ttu-id="f2511-111">以滑鼠右鍵**按一下 [資料流程**] 索引標籤中的 [**條件式分割轉換**]，然後按一下 [**重新命名**]</span><span class="sxs-lookup"><span data-stu-id="f2511-111">Right-click **Conditional Split Transform** in the **Data Flow** tab, and click **Rename**.</span></span> <span data-ttu-id="f2511-112">輸入**篩選重複專案**，然後按**enter**。</span><span class="sxs-lookup"><span data-stu-id="f2511-112">Type **Filter Duplicates** and press **ENTER**.</span></span>  
  
3.  <span data-ttu-id="f2511-113">連接**具有相符識別碼的群組供應商**來**篩選重複專案**。</span><span class="sxs-lookup"><span data-stu-id="f2511-113">Connect **Group Suppliers with Matching IDs** to **Filter Duplicates**.</span></span>  
  
4.  <span data-ttu-id="f2511-114">按兩下 [**篩選重複專案**]，啟動 [**條件式分割轉換編輯器**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="f2511-114">Double-click **Filter Duplicates** to launch the **Conditional Split Transform Editor** dialog box.</span></span>  
  
5.  <span data-ttu-id="f2511-115">展開左上方窗格中的 [資料**行**]。</span><span class="sxs-lookup"><span data-stu-id="f2511-115">Expand **Columns** in the top-left pane.</span></span>  
  
6.  <span data-ttu-id="f2511-116">將 **_key_in**拖放至 [**條件**] 資料行。</span><span class="sxs-lookup"><span data-stu-id="f2511-116">Drag-drop **_key_in** to the **Condition** column.</span></span>  
  
7.  <span data-ttu-id="f2511-117">在 [ **_key_in** ] 和 [拖放 **_key_out**] 旁，輸入 = = (等於) 。</span><span class="sxs-lookup"><span data-stu-id="f2511-117">Type == (equals to) next to **_key_in** and drag-drop **_key_out**.</span></span>  
  
8.  <span data-ttu-id="f2511-118">在 [**輸出名稱**] 資料行中按一下 [**案例 1** ]，輸入**唯一記錄**，然後按**enter**。</span><span class="sxs-lookup"><span data-stu-id="f2511-118">Click **Case 1** in the **Output Name** column, type **Unique Records**, and press **ENTER**.</span></span>  
  
     <span data-ttu-id="f2511-119">![條件式分割轉換編輯器](../../2014/tutorials/media/et-addingconditionalsplittransformtofilterduplicates.jpg "條件式分割轉換編輯器")</span><span class="sxs-lookup"><span data-stu-id="f2511-119">![Conditional Split Transformation Editor](../../2014/tutorials/media/et-addingconditionalsplittransformtofilterduplicates.jpg "Conditional Split Transformation Editor")</span></span>  
  
9. <span data-ttu-id="f2511-120">按一下 **[確定]** 以關閉 [**條件式分割轉換編輯器**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="f2511-120">Click **OK** to close the **Conditional Split Transformation Editor** dialog box.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="f2511-121">後續步驟</span><span class="sxs-lookup"><span data-stu-id="f2511-121">Next Step</span></span>  
 [<span data-ttu-id="f2511-122">工作 12：新增衍生的資料行轉換來新增 MDS 需要的資料行</span><span class="sxs-lookup"><span data-stu-id="f2511-122">Task 12: Adding Derived Column Transform to Add Columns Required by MDS</span></span>](../../2014/tutorials/task-12-adding-derived-column-transform-to-add-columns-required-by-mds.md)  
  
  
