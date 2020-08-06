---
title: 手動編輯預測查詢 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- modifying prediction queries
- Mining Model Prediction [Analysis Services], modifying prediction queries
- manual prediction query modification [Analysis Services]
ms.assetid: 9f6a9298-49d5-4675-ad49-977a47dff5a6
author: minewiskan
ms.author: owend
ms.openlocfilehash: e887e935dafcd2428859fd959cb7bc64650c660d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607156"
---
# <a name="manually-edit-a-prediction-query"></a><span data-ttu-id="59433-102">手動編輯預測查詢</span><span class="sxs-lookup"><span data-stu-id="59433-102">Manually Edit a Prediction Query</span></span>
  <span data-ttu-id="59433-103">在使用預測查詢產生器設計查詢之後，您可以切換到資料採礦設計師的 [採礦模型預測]\*\*\*\* 索引標籤上的 [查詢文字] 檢視來修改查詢。</span><span class="sxs-lookup"><span data-stu-id="59433-103">After you have designed a query by using the Prediction Query Builder, you can modify the query by switching to Query Text view on the **Mining Model Prediction** tab of Data Mining Designer.</span></span> <span data-ttu-id="59433-104">文字編輯器會出現在畫面底端，以顯示查詢產生器建立的查詢。</span><span class="sxs-lookup"><span data-stu-id="59433-104">A text editor appears at the bottom of the screen to display the query that the query builder created.</span></span>  
  
 <span data-ttu-id="59433-105">切換到 [查詢文字] 檢視對於在查詢中添加內容很實用。</span><span class="sxs-lookup"><span data-stu-id="59433-105">Switching to Query Text view is useful for making additions to the query.</span></span> <span data-ttu-id="59433-106">例如，您可以加入 WHERE 子句或 ORDER BY 子句。</span><span class="sxs-lookup"><span data-stu-id="59433-106">For example, you can add a WHERE clause or ORDER BY clause.</span></span>  
  
 <span data-ttu-id="59433-107">使用預測查詢產生器中的方格來插入物件和資料行的名稱，並為個別預測函數設定語法，然後切換到手動編輯模式來變更參數值。</span><span class="sxs-lookup"><span data-stu-id="59433-107">Use the grid in the Prediction Query Builder to insert the names of objects and columns and set up the syntax for individual prediction functions, and then switch to manual editing mode to change parameter values.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="59433-108">如果您從 [查詢文字]\*\*\*\* 檢視切回到 [設計]\*\*\*\* 檢視，則會失去您在 [查詢文字]\*\*\*\* 檢視中所做的任何變更。</span><span class="sxs-lookup"><span data-stu-id="59433-108">If you switch back to **Design** view from **Query Text** view, any changes that you made in **Query Text** view will be lost.</span></span>  
  
### <a name="modify-a-query"></a><span data-ttu-id="59433-109">修改查詢</span><span class="sxs-lookup"><span data-stu-id="59433-109">Modify a query</span></span>  
  
1.  <span data-ttu-id="59433-110">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 中，於資料採礦設計師的 [採礦模型預測]\*\*\*\* 索引標籤上，按一下 [SQL]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="59433-110">On the **Mining Model Prediction** tab in Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], click **SQL**.</span></span>  
  
     <span data-ttu-id="59433-111">畫面底端的方格會由包含查詢的文字編輯器所取代。</span><span class="sxs-lookup"><span data-stu-id="59433-111">The grid at the bottom of the screen is replaced by a text editor that contains the query.</span></span> <span data-ttu-id="59433-112">您可以在此編輯器中輸入對查詢的變更。</span><span class="sxs-lookup"><span data-stu-id="59433-112">You can type changes to the query in this editor.</span></span>  
  
2.  <span data-ttu-id="59433-113">若要執行查詢，請在 [採礦模型]\*\*\*\* 功能表上選取 [結果]\*\*\*\*，或按一下按鈕切換到查詢結果。</span><span class="sxs-lookup"><span data-stu-id="59433-113">To run the query, on the **Mining Model** menu, select **Result**, or click the button to switch to query results.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="59433-114">如果您建立的查詢無效，則 [結果] 視窗不會顯示錯誤，也不會顯示任何結果。</span><span class="sxs-lookup"><span data-stu-id="59433-114">If the query that you have created is invalid, the Results window does not display an error and does not display any results.</span></span> <span data-ttu-id="59433-115">按一下 [設計]\*\*\*\* 按鈕或從 [採礦模型]\*\*\*\* 功能表選取 [設計]\*\*\*\* 或 [查詢]\*\*\*\* 以修正問題，並再次執行查詢。</span><span class="sxs-lookup"><span data-stu-id="59433-115">Click the **Design** button, or select **Design** or **Query** from the **Mining Model** menu to correct the problem and run the query again.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59433-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="59433-116">See Also</span></span>  
 <span data-ttu-id="59433-117">[資料採礦查詢](data-mining-queries.md) </span><span class="sxs-lookup"><span data-stu-id="59433-117">[Data Mining Queries](data-mining-queries.md) </span></span>  
 <span data-ttu-id="59433-118">[預測查詢產生器 &#40;資料採礦&#41;](../prediction-query-builder-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="59433-118">[Prediction Query Builder &#40;Data Mining&#41;](../prediction-query-builder-data-mining.md) </span></span>  
 [<span data-ttu-id="59433-119">第 6 課：建立及處理預測 &#40;基本資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="59433-119">Lesson 6: Creating and Working with Predictions &#40;Basic Data Mining Tutorial&#41;</span></span>](../../tutorials/lesson-6-creating-and-working-with-predictions-basic-data-mining-tutorial.md)  
  
  
