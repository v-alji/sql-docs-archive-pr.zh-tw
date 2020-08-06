---
title: 建立查詢參數與報表參數的關聯 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- queries [Reporting Services], parameters
- parameters [Reporting Services], queries
ms.assetid: 6d297e1a-ff71-472a-addc-349e863092b5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f65aa36e8910378d68963c8c9990518b661025ab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688617"
---
# <a name="associate-a-query-parameter-with-a-report-parameter-report-builder-and-ssrs"></a><span data-ttu-id="221ec-102">將查詢參數與報表參數產生關聯 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="221ec-102">Associate a Query Parameter with a Report Parameter (Report Builder and SSRS)</span></span>
  <span data-ttu-id="221ec-103">當您定義包含查詢變數的資料集查詢時，就會剖析查詢命令。</span><span class="sxs-lookup"><span data-stu-id="221ec-103">When you define a dataset query that contains a query variable, the query command is parsed.</span></span> <span data-ttu-id="221ec-104">系統會針對每個查詢變數建立對應的資料集參數和報表參數。</span><span class="sxs-lookup"><span data-stu-id="221ec-104">For each query variable, a corresponding dataset parameter and report parameter are created.</span></span> <span data-ttu-id="221ec-105">資料集參數會指向報表參數。</span><span class="sxs-lookup"><span data-stu-id="221ec-105">The dataset parameter points to the report parameter.</span></span> <span data-ttu-id="221ec-106">如此可讓使用者輸入一個值來直接傳遞給查詢。</span><span class="sxs-lookup"><span data-stu-id="221ec-106">This enables a user to enter a value that passes directly to the query.</span></span> <span data-ttu-id="221ec-107">每次您編輯查詢命令時，系統都會進行相同的程序。</span><span class="sxs-lookup"><span data-stu-id="221ec-107">Each time you edit the query command, the same process takes place.</span></span>  
  
 <span data-ttu-id="221ec-108">如果您重新命名繫結至查詢參數的報表參數，您需要使用本主題的查詢，手動將查詢參數連結到重新命名過的報表參數。</span><span class="sxs-lookup"><span data-stu-id="221ec-108">If you rename a report parameter that is bound to a query parameter, you need to manually link the query parameters to the renamed report parameter by using the procedure in this topic.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-associate-a-query-parameter-with-a-report-parameter"></a><span data-ttu-id="221ec-109">將查詢參數與報表參數相關聯</span><span class="sxs-lookup"><span data-stu-id="221ec-109">To associate a query parameter with a report parameter</span></span>  
  
1.  <span data-ttu-id="221ec-110">在 [報表資料] 窗格中，以滑鼠右鍵按一下資料集，然後按一下 [資料集屬性]\*\*\*\*，再按一下 [參數]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="221ec-110">In the Report Data pane, right-click the dataset, click **Dataset Properties**, and then click **Parameters**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="221ec-111">如果看不到 [報表資料] 窗格，請按一下 [檢視]\*\*\*\* 功能表上的 [報表資料]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="221ec-111">If the Report Data pane is not visible, click **Report Data** on the **View** menu.</span></span>  
  
2.  <span data-ttu-id="221ec-112">在 [參數名稱]\*\*\*\* 資料行中，尋找查詢參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="221ec-112">In the column **Parameter Name**, find the name of the query parameter.</span></span> <span data-ttu-id="221ec-113">參數名稱會依據查詢自動填入。</span><span class="sxs-lookup"><span data-stu-id="221ec-113">Parameter names are automatically populated based on the query.</span></span> <span data-ttu-id="221ec-114">每當您變更查詢時，系統都會檢查查詢，看看是否有新的查詢參數。</span><span class="sxs-lookup"><span data-stu-id="221ec-114">Every time you change the query, the query is checked for new query parameters.</span></span> <span data-ttu-id="221ec-115">當查詢變更時，您手動建立的查詢參數並不會變更。</span><span class="sxs-lookup"><span data-stu-id="221ec-115">Query parameters that you create manually are not changed when the query changes.</span></span>  
  
    -   <span data-ttu-id="221ec-116">在 [參數名稱]\*\*\*\* 中，尋找存在於查詢中的查詢參數名稱。</span><span class="sxs-lookup"><span data-stu-id="221ec-116">In **Parameter Name**, find the query parameter name as it exists in the query.</span></span> <span data-ttu-id="221ec-117">您也可以手動加入新的查詢參數，並輸入名稱。</span><span class="sxs-lookup"><span data-stu-id="221ec-117">You can also manually add a new query parameter and enter a name.</span></span>  
  
    -   <span data-ttu-id="221ec-118">在 [參數值]\*\*\*\* 中，鍵入或選取會評估為要傳遞到查詢參數之值的運算式。</span><span class="sxs-lookup"><span data-stu-id="221ec-118">In **Parameter Value**, type or select an expression that evaluates to the value to pass to the query parameter.</span></span> <span data-ttu-id="221ec-119">這通常是報表參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="221ec-119">This is typically the name of the report parameter.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="221ec-120">並非只有報表參數才能做為查詢參數的值。</span><span class="sxs-lookup"><span data-stu-id="221ec-120">You are not limited to report parameters as values for a query parameter.</span></span> <span data-ttu-id="221ec-121">您可以使用任何會評估為值的運算式，以做為參數值。</span><span class="sxs-lookup"><span data-stu-id="221ec-121">You can use any expression that evaluates to a value for the parameter value.</span></span>  
  
3.  <span data-ttu-id="221ec-122">重複步驟 2 可以加入其他查詢參數。</span><span class="sxs-lookup"><span data-stu-id="221ec-122">Repeat step 2 for additional query parameters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="221ec-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="221ec-123">See Also</span></span>  
 <span data-ttu-id="221ec-124">[報表內嵌資料集和共用資料集 &#40;報表產生器和 SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="221ec-124">[Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="221ec-125">報表參數概念 &#40;報表產生器和 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="221ec-125">Report Parameters Concept &#40;Report Builder and SSRS&#41;</span></span>](../report-design/report-parameters-concepts-report-builder-and-ssrs.md)  
  
  
