---
title: 變更資料採礦查詢的超時值 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- time-out
ms.assetid: f1add4bc-e882-440a-a98b-333cfa274c3e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9dcdcdcbb6e2aef48dd8725f10f38180c73f5f6c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597463"
---
# <a name="change-the-time-out-value-for-data-mining-queries"></a><span data-ttu-id="fd092-102">針對資料採礦查詢變更逾時值</span><span class="sxs-lookup"><span data-stu-id="fd092-102">Change the Time-out Value for Data Mining Queries</span></span>
  <span data-ttu-id="fd092-103">在建立增益圖或執行預測查詢時，有時可能要花很長的時間才能產生預測所需的所有資料。</span><span class="sxs-lookup"><span data-stu-id="fd092-103">When you build a lift chart or execute a prediction query, sometimes it can take a long time to generate all the data required for the prediction.</span></span> <span data-ttu-id="fd092-104">若要避免查詢逾時，可以變更控制 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 伺服器等候完成查詢多久時間的值。</span><span class="sxs-lookup"><span data-stu-id="fd092-104">To prevent the query from timing out, you can change the value that controls how long the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] server waits to complete a query.</span></span>  
  
 <span data-ttu-id="fd092-105">預設值為 15；不過，如果模型很複雜，或者資料來源很龐大，則這樣的時間長度可能不夠。</span><span class="sxs-lookup"><span data-stu-id="fd092-105">The default value is 15; however, if your models are complex or the data source is large, this might not be enough.</span></span> <span data-ttu-id="fd092-106">如有必要，可以大幅增加此值，以提供足夠的時間進行處理。</span><span class="sxs-lookup"><span data-stu-id="fd092-106">If necessary, you can increase the value significantly, to enable enough time for processing.</span></span> <span data-ttu-id="fd092-107">例如，如果將 **[查詢逾時]** 設定為 600，則查詢可能會持續執行長達 10 分鐘。</span><span class="sxs-lookup"><span data-stu-id="fd092-107">For example, if you set **Query Timeout** to 600, the query could continue to run for up to 10 minutes.</span></span>  
  
 <span data-ttu-id="fd092-108">如需預測查詢的詳細資訊，請參閱 [資料採礦查詢工作和使用說明](data-mining-query-tasks-and-how-tos.md)。</span><span class="sxs-lookup"><span data-stu-id="fd092-108">For more information about prediction queries, see [Data Mining Query Tasks and How-tos](data-mining-query-tasks-and-how-tos.md).</span></span>  
  
### <a name="configure-the-time-out-value-for-data-mining-queries"></a><span data-ttu-id="fd092-109">設定資料採礦查詢的逾時值</span><span class="sxs-lookup"><span data-stu-id="fd092-109">Configure the time-out value for data mining queries</span></span>  
  
1.  <span data-ttu-id="fd092-110">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，從 **[工具]** 功能表選取 **[選項]**。</span><span class="sxs-lookup"><span data-stu-id="fd092-110">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], from the **Tools** menu, selection **Options**.</span></span>  
  
2.  <span data-ttu-id="fd092-111">在 **[選項]** 窗格中，展開 **[商業智慧設計師]**。</span><span class="sxs-lookup"><span data-stu-id="fd092-111">In the **Options** pane, expand **Business Intelligence Designers**.</span></span>  
  
3.  <span data-ttu-id="fd092-112">按一下 **[查詢逾時]** 文字方塊，並輸入秒數的值。</span><span class="sxs-lookup"><span data-stu-id="fd092-112">Click the **Query Timeout** text box, and type a value for the number of seconds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd092-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fd092-113">See Also</span></span>  
 <span data-ttu-id="fd092-114">[資料採礦查詢工作和操作說明](data-mining-query-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="fd092-114">[Data Mining Query Tasks and How-tos](data-mining-query-tasks-and-how-tos.md) </span></span>  
 [<span data-ttu-id="fd092-115">資料採礦查詢</span><span class="sxs-lookup"><span data-stu-id="fd092-115">Data Mining Queries</span></span>](data-mining-queries.md)  
  
  
