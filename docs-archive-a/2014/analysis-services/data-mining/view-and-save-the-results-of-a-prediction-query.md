---
title: 查看並儲存預測查詢的結果 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- prediction queries [Analysis Services]
- viewing prediction query results
- displaying prediction query results
- Mining Model Prediction [Analysis Services], viewing results
ms.assetid: abba4d24-3619-44c1-8279-88f27ad627d3
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6da4b515c4280969f665dba2cf5bee5281df0a00
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594822"
---
# <a name="view-and-save-the-results-of-a-prediction-query"></a><span data-ttu-id="2f23b-102">檢視及儲存預測查詢的結果</span><span class="sxs-lookup"><span data-stu-id="2f23b-102">View and Save the Results of a Prediction Query</span></span>
  <span data-ttu-id="2f23b-103">在中 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 使用預測查詢產生器定義查詢之後，您可以藉由切換至 [查詢結果] 視圖來執行查詢並查看結果。</span><span class="sxs-lookup"><span data-stu-id="2f23b-103">After you have defined a query in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] by using Prediction Query Builder, you can run the query and view the results by switching to the query result view.</span></span>  
  
 <span data-ttu-id="2f23b-104">您可以將預測查詢的結果儲存至專案中所定義之任何資料來源中的資料表 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="2f23b-104">You can save the results of a prediction query to a table in any data source that is defined in a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project.</span></span> <span data-ttu-id="2f23b-105">您可以建立新的資料表，或將查詢結果儲存至現有的資料表。</span><span class="sxs-lookup"><span data-stu-id="2f23b-105">You can either create a new table or save the query results to an existing table.</span></span> <span data-ttu-id="2f23b-106">如果您將結果儲存至現有的資料表，則可選擇覆寫目前儲存在資料表中的資料，否則查詢結果會附加至資料表中的現有資料。</span><span class="sxs-lookup"><span data-stu-id="2f23b-106">If you save the results to an existing table, you can choose to overwrite the data that is currently stored in the table; otherwise, the query results are appended to the existing data in the table.</span></span>  
  
### <a name="run-a-query-and-view-the-results"></a><span data-ttu-id="2f23b-107">執行查詢並檢視結果</span><span class="sxs-lookup"><span data-stu-id="2f23b-107">Run a query and view the results</span></span>  
  
1.  <span data-ttu-id="2f23b-108">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 中，於資料採礦設計師之 [採礦模型預測]\*\*\*\* 索引標籤的工具列上，按一下 [結果]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2f23b-108">On the toolbar of the **Mining Model Prediction** tab of Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], click **Result** .</span></span>  
  
     <span data-ttu-id="2f23b-109">查詢結果檢視會開啟並執行查詢。</span><span class="sxs-lookup"><span data-stu-id="2f23b-109">The query results view opens and runs the query.</span></span> <span data-ttu-id="2f23b-110">結果會顯示在檢視器的方格中。</span><span class="sxs-lookup"><span data-stu-id="2f23b-110">The results are displayed in a grid in the viewer.</span></span>  
  
### <a name="save-the-results-of-a-prediction-query-to-a-table"></a><span data-ttu-id="2f23b-111">將預測查詢的結果儲存至資料表</span><span class="sxs-lookup"><span data-stu-id="2f23b-111">Save the results of a prediction query to a table</span></span>  
  
1.  <span data-ttu-id="2f23b-112">在資料採礦設計師之 [採礦模型預測]\*\*\*\* 索引標籤的工具列上，按一下 [儲存查詢結果]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2f23b-112">On the toolbar of the **Mining Model Prediction** tab in Data Mining Designer, click **Save query result**.</span></span>  
  
     <span data-ttu-id="2f23b-113">[儲存資料採礦查詢結果]\*\*\*\* 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="2f23b-113">The **Save Data Mining Query Result** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="2f23b-114">從 [資料來源]\*\*\*\* 清單中選取資料來源，或按一下 [新增]\*\*\*\* 來建立新的資料來源。</span><span class="sxs-lookup"><span data-stu-id="2f23b-114">Select a data source from the **Data Source** list, or click **New** to create a new data source.</span></span>  
  
3.  <span data-ttu-id="2f23b-115">在 [資料表名稱]\*\*\*\* 方塊中，輸入資料表的名稱。</span><span class="sxs-lookup"><span data-stu-id="2f23b-115">In the **Table Name** box, enter the name of the table.</span></span> <span data-ttu-id="2f23b-116">如果資料表已存在，請選取 [如果存在則覆寫]\*\*\*\*，即可將資料表的內容取代成查詢結果。</span><span class="sxs-lookup"><span data-stu-id="2f23b-116">If the table already exists, select **Overwrite if exists** to replace the contents of the table with the query results.</span></span> <span data-ttu-id="2f23b-117">如果您不想要覆寫資料表的內容，請勿選取此核取方塊。</span><span class="sxs-lookup"><span data-stu-id="2f23b-117">If you do not want to overwrite the contents of the table, do not select this check box.</span></span> <span data-ttu-id="2f23b-118">新查詢結果將附加至資料表中的現有資料。</span><span class="sxs-lookup"><span data-stu-id="2f23b-118">The new query results will be appended to the existing data in the table.</span></span>  
  
4.  <span data-ttu-id="2f23b-119">如果您想要將資料表加入資料來源檢視，請從 [加入至 DSV]\*\*\*\* 中選取資料來源檢視。</span><span class="sxs-lookup"><span data-stu-id="2f23b-119">Select a data source view from **Add to DSV** if you want to add the table to a data source view.</span></span>  
  
5.  <span data-ttu-id="2f23b-120">按一下 [檔案] 。</span><span class="sxs-lookup"><span data-stu-id="2f23b-120">Click **Save**.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="2f23b-121">如果目的地不支援階層式資料列集，您可以將 FALTTENED 關鍵字加入至結果中，以便儲存為二維資料表。</span><span class="sxs-lookup"><span data-stu-id="2f23b-121">If the destination does not support hierarchical rowsets, you can add the FALTTENED keyword to the results to save as a flat table.</span></span>  
  
  
