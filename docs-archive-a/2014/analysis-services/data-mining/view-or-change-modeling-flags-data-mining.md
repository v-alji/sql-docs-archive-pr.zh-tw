---
title: 查看或變更 (資料採礦) 的模型旗標 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d1169735-fb18-417b-b8d6-9a161e444020
author: minewiskan
ms.author: owend
ms.openlocfilehash: bf0edd827321685a2d6a9041759328a7ac6e7cbd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702157"
---
# <a name="view-or-change-modeling-flags-data-mining"></a><span data-ttu-id="c26b9-102">檢視或變更模型旗標 (資料採礦)</span><span class="sxs-lookup"><span data-stu-id="c26b9-102">View or Change Modeling Flags (Data Mining)</span></span>
  <span data-ttu-id="c26b9-103">模型旗標是您針對採礦結構資料行或採礦模型資料行設定的屬性，可控制演算法如何在分析期間處理資料。</span><span class="sxs-lookup"><span data-stu-id="c26b9-103">Modeling flags are properties that you set on a mining structure column or mining model columns to control how the algorithm processes the data during analysis.</span></span>  
  
 <span data-ttu-id="c26b9-104">在資料採礦設計師中，您可以藉由檢視結構或模型的屬性來檢視及修改與採礦結構或採礦資料行相關聯的模型旗標。</span><span class="sxs-lookup"><span data-stu-id="c26b9-104">In Data Mining Designer, you can view and modify the modeling flags associated with a mining structure or mining column by viewing the properties of the structure or model.</span></span> <span data-ttu-id="c26b9-105">您也可以使用 DMX、AMO 或 XMLA 來設定模型旗標。</span><span class="sxs-lookup"><span data-stu-id="c26b9-105">You can also set modeling flags by using DMX, AMO, or XMLA.</span></span>  
  
 <span data-ttu-id="c26b9-106">此程序描述如何在設計工具中變更模型旗標。</span><span class="sxs-lookup"><span data-stu-id="c26b9-106">This procedure describes how to change the modeling flags in the designer.</span></span>  
  
### <a name="view-or-change-the-modeling-flag-for-a-structure-column-or-model-column"></a><span data-ttu-id="c26b9-107">檢視或變更結構資料行或模型資料行的模型旗標</span><span class="sxs-lookup"><span data-stu-id="c26b9-107">View or change the modeling flag for a structure column or model column</span></span>  
  
1.  <span data-ttu-id="c26b9-108">在 SQL Server Design Studio 中開啟 [方案總管]，然後按兩下採礦結構。</span><span class="sxs-lookup"><span data-stu-id="c26b9-108">In SQL Server Design Studio, open Solution Explorer, and then double-click the mining structure.</span></span>  
  
2.  <span data-ttu-id="c26b9-109">若要設定 NOT Null 模型旗標，請按一下 [**採礦結構**] 索引標籤。若要設定回歸輸入變數或 MODEL_EXISTENCE_ONLY 旗標，請按一下 [**採礦模型**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="c26b9-109">To set the NOT NULL modeling flag, click the **Mining Structure** tab. To set the REGRESSOR or MODEL_EXISTENCE_ONLY flags, click the **Mining Model** tab.</span></span>  
  
3.  <span data-ttu-id="c26b9-110">以滑鼠右鍵按一下要檢視或變更的資料行，然後選取 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c26b9-110">Right-click the column you want to view or change, and select **Properties**.</span></span>  
  
4.  <span data-ttu-id="c26b9-111">若要新增模型旗標，按一下 **[ModelingFlags]** 屬性，然後選取要使用之模型旗標的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="c26b9-111">To add a new modeling flag, click the text box next to the **ModelingFlags** property, and select the check box or check boxes for the modeling flags you want to use.</span></span>  
  
     <span data-ttu-id="c26b9-112">只有適合資料行資料類型的模型旗標才會顯示。</span><span class="sxs-lookup"><span data-stu-id="c26b9-112">Modeling flags are displayed only if they are appropriate for the column data type.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c26b9-113">在變更模型旗標後，必須重新處理模型。</span><span class="sxs-lookup"><span data-stu-id="c26b9-113">After you change a modeling flag, you must reprocess the model.</span></span>  
  
### <a name="get-the-modeling-flags-used-in-the-model"></a><span data-ttu-id="c26b9-114">取得模型中使用的模型旗標</span><span class="sxs-lookup"><span data-stu-id="c26b9-114">Get the modeling flags used in the model</span></span>  
  
-   <span data-ttu-id="c26b9-115">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中開啟 [DMX 查詢] 視窗，然後輸入類似以下的查詢：</span><span class="sxs-lookup"><span data-stu-id="c26b9-115">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], open a DMX Query window, and type a query like the following:</span></span>  
  
    ```  
    SELECT COLUMN_NAME, CONTENT_TYPE, MODELING_FLAG  
    FROM $system.DMSCHEMA_MINING_COLUMNS  
    WHERE MODEL_NAME = 'Forecasting'  
  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="c26b9-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c26b9-116">See Also</span></span>  
 <span data-ttu-id="c26b9-117">[採礦模型工作和操作說明](mining-model-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="c26b9-117">[Mining Model Tasks and How-tos](mining-model-tasks-and-how-tos.md) </span></span>  
 [<span data-ttu-id="c26b9-118">模型旗標 &#40;資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="c26b9-118">Modeling Flags &#40;Data Mining&#41;</span></span>](modeling-flags-data-mining.md)  
  
  
