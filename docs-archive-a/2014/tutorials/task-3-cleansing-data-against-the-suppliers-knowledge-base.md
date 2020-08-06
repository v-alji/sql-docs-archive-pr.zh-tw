---
title: 工作3：針對供應商知識庫清理資料 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 647c924a-9b91-4294-8d96-e81416e4e90e
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 13201a8b904a5fc5232b9fa860710e4e39cce67a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704417"
---
# <a name="task-3-cleansing-data-against-the-suppliers-knowledge-base"></a><span data-ttu-id="e7424-102">工作 3：針對供應商知識庫清理資料</span><span class="sxs-lookup"><span data-stu-id="e7424-102">Task 3: Cleansing Data against the Suppliers Knowledge Base</span></span>
  <span data-ttu-id="e7424-103">在這項工作中，您會執行電腦輔助的清理程序。</span><span class="sxs-lookup"><span data-stu-id="e7424-103">In this task, you run the computer-assisted cleansing process.</span></span> <span data-ttu-id="e7424-104">DQS 會根據為了針對選取的知識庫分析及清理資料所指定的臨界值，使用進階演算法與信賴等級。</span><span class="sxs-lookup"><span data-stu-id="e7424-104">DQS uses advanced algorithms and confidence levels based on the threshold values specified to analyze the data against the selected knowledge base, and then cleanse it.</span></span> <span data-ttu-id="e7424-105">如需詳細資訊，請參閱[使用 DQS (內部) 知識清理資料](https://msdn.microsoft.com/library/hh213061.aspx)。</span><span class="sxs-lookup"><span data-stu-id="e7424-105">See [Cleansing Data Using DQS (Internal) Knowledge](https://msdn.microsoft.com/library/hh213061.aspx) for more details.</span></span>

1.  <span data-ttu-id="e7424-106">按一下 [**啟動**] 以啟動電腦輔助的清理程式。</span><span class="sxs-lookup"><span data-stu-id="e7424-106">Click **Start** to start the computer-assisted cleansing process.</span></span>

     <span data-ttu-id="e7424-107">![清理程序的 [清理] 頁面](../../2014/tutorials/media/et-cleansingdataagainstthesupplierkb-01.jpg "清理程序的 [清理] 頁面")</span><span class="sxs-lookup"><span data-stu-id="e7424-107">![Cleanse Page of the Cleansing Process](../../2014/tutorials/media/et-cleansingdataagainstthesupplierkb-01.jpg "Cleanse Page of the Cleansing Process")</span></span>

2.  <span data-ttu-id="e7424-108">清理程式完成時，**請在 [分析工具] 索引**標籤中檢查**統計資料**。來源統計資料會提供已處理的記錄數目、找到正確的記錄數目、DQS 更正的記錄數目、有 DQS 建議變更的記錄數目，以及不正確記錄數目。</span><span class="sxs-lookup"><span data-stu-id="e7424-108">When the cleansing process is completed, review **statistics** in the **Profiler** tab. The Source Statistics provide the number of records processed, number of records that are found to be correct, number of records that DQS corrects, number of records that have changes suggested by DQS, and the number of records that are invalid.</span></span> <span data-ttu-id="e7424-109">在右邊的清單方塊中，您可以看到清理程序中每一個相關定義域的更正值、建議值及完整性 (資料存在的程度) 和精確度 (資料可用於預定用途的程度) 等值。</span><span class="sxs-lookup"><span data-stu-id="e7424-109">In the list box to the right, you can see the corrected values, suggested values, and the completeness (the extent to which the data is present) and accuracy (the extent to which the data can be used for intended purposes) of values for each domain involved in the cleansing process.</span></span>

     <span data-ttu-id="e7424-110">![清理結果](../../2014/tutorials/media/et-cleansingdataagainstthesupplierkb-02.jpg "清理結果")</span><span class="sxs-lookup"><span data-stu-id="e7424-110">![Cleansing Results](../../2014/tutorials/media/et-cleansingdataagainstthesupplierkb-02.jpg "Cleansing Results")</span></span>

3.  <span data-ttu-id="e7424-111">按 **[下一步]** 以切換至 [**管理及查看結果**] 頁面。</span><span class="sxs-lookup"><span data-stu-id="e7424-111">Click **Next** to switch to **Manage and View Results** page.</span></span>

## <a name="next-step"></a><span data-ttu-id="e7424-112">後續步驟</span><span class="sxs-lookup"><span data-stu-id="e7424-112">Next Step</span></span>
 [<span data-ttu-id="e7424-113">工作 4：管理和檢視結果</span><span class="sxs-lookup"><span data-stu-id="e7424-113">Task 4: Manaing and Viewing Results</span></span>](../../2014/tutorials/task-4-manaing-and-viewing-results.md)


