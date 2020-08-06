---
title: ) 的 [查詢] 窗格 ([採礦模型預測] 視圖 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.prediction.query.f1
ms.assetid: fdeec72e-d0bd-4453-9eaa-46436e4d6edc
author: minewiskan
ms.author: owend
ms.openlocfilehash: e17a27190891ea9e00be21d5013d0767d61ac148
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594248"
---
# <a name="query-pane-mining-model-prediction-view"></a><span data-ttu-id="29ac8-102">查詢窗格 (採礦模型預測檢視)</span><span class="sxs-lookup"><span data-stu-id="29ac8-102">Query Pane (Mining Model Prediction View)</span></span>
  <span data-ttu-id="29ac8-103">[查詢]\*\*\*\* 窗格會顯示預測查詢產生器所建立的資料採礦運算式 (DMX) 陳述式。</span><span class="sxs-lookup"><span data-stu-id="29ac8-103">The **Query** pane displays the Data Mining Expressions (DMX) statements created by Prediction Query Builder.</span></span> <span data-ttu-id="29ac8-104">您可以修改陳述式，然後按一下 [切換到查詢結果檢視]\*\*\*\* 按鈕，以傳回結果。</span><span class="sxs-lookup"><span data-stu-id="29ac8-104">You can modify the statements and then click the **Switch to query result view** button to return the results.</span></span> <span data-ttu-id="29ac8-105">如果切換到 [設計]\*\*\*\* 檢視，您對陳述式所做的任何變更將會遺失。</span><span class="sxs-lookup"><span data-stu-id="29ac8-105">If you switch back to the **Design** view, any changes you made to the statement will be lost.</span></span>  
  
 <span data-ttu-id="29ac8-106">**如需詳細資訊，請參閱** [資料採礦延伸模組 &#40;DMX&#41; 資料操作陳述式](/sql/dmx/dmx-statements-data-manipulation)[在 SQL Server Management Studio 中建立 DMX 查詢](data-mining/create-a-dmx-query-in-sql-server-management-studio.md)</span><span class="sxs-lookup"><span data-stu-id="29ac8-106">**For More Information:** [Data Mining Extensions &#40;DMX&#41; Data Manipulation Statements](/sql/dmx/dmx-statements-data-manipulation), [Create a DMX Query in SQL Server Management Studio](data-mining/create-a-dmx-query-in-sql-server-management-studio.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="29ac8-107">選項</span><span class="sxs-lookup"><span data-stu-id="29ac8-107">Options</span></span>  
 <span data-ttu-id="29ac8-108">**切換到查詢結果檢視**</span><span class="sxs-lookup"><span data-stu-id="29ac8-108">**Switch to query result view**</span></span>  
 <span data-ttu-id="29ac8-109">按一下，即可在 [設計]\*\*\*\*、[查詢]\*\*\*\* 及 [結果]\*\*\*\* 窗格之間切換。</span><span class="sxs-lookup"><span data-stu-id="29ac8-109">Click to switch between the **Design**, **Query**, and **Result** panes.</span></span> <span data-ttu-id="29ac8-110">切換到 **[結果]** 窗格會執行查詢。</span><span class="sxs-lookup"><span data-stu-id="29ac8-110">Switching to the **Result** pane runs the query.</span></span>  
  
 <span data-ttu-id="29ac8-111">**儲存查詢結果**</span><span class="sxs-lookup"><span data-stu-id="29ac8-111">**Save the query result**</span></span>  
 <span data-ttu-id="29ac8-112">開啟 [儲存資料採礦查詢結果]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="29ac8-112">Opens the **Save Data Mining Query Result** dialog box.</span></span>  
  
 <span data-ttu-id="29ac8-113">**單一查詢**</span><span class="sxs-lookup"><span data-stu-id="29ac8-113">**Singleton query**</span></span>  
 <span data-ttu-id="29ac8-114">讓您能夠建立單一查詢，且您可以直接在此查詢中提供輸入資料，而不必提供輸入值之資料表的參考。</span><span class="sxs-lookup"><span data-stu-id="29ac8-114">Lets you create a singleton query, in which you provide the input data directly in your query instead of providing a reference to a table of input values.</span></span> <span data-ttu-id="29ac8-115">[選取輸入資料表]\*\*\*\* 資料表已由 [單一查詢輸入]\*\*\*\* 資料表取代。</span><span class="sxs-lookup"><span data-stu-id="29ac8-115">The **Select Input Table(s)** table is replaced by a **Singleton Query Input** table.</span></span> <span data-ttu-id="29ac8-116">如果您切換到單一查詢，目前的預測查詢將會遺失。</span><span class="sxs-lookup"><span data-stu-id="29ac8-116">The current prediction query will be lost if you switch to a singleton query.</span></span>  
  
 <span data-ttu-id="29ac8-117">**重新整理查詢結果**</span><span class="sxs-lookup"><span data-stu-id="29ac8-117">**Refresh query results**</span></span>  
 <span data-ttu-id="29ac8-118">重新處理預測查詢。</span><span class="sxs-lookup"><span data-stu-id="29ac8-118">Reprocesses the prediction query.</span></span> <span data-ttu-id="29ac8-119">這只會在 **[結果]** 窗格中啟用。</span><span class="sxs-lookup"><span data-stu-id="29ac8-119">This is enabled only in the **Result** pane.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29ac8-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="29ac8-120">See Also</span></span>  
 <span data-ttu-id="29ac8-121">[資料採礦查詢介面](data-mining/data-mining-query-tools.md) </span><span class="sxs-lookup"><span data-stu-id="29ac8-121">[Data Mining Query Interfaces](data-mining/data-mining-query-tools.md) </span></span>  
 <span data-ttu-id="29ac8-122">[資料採礦延伸模組 &#40;DMX&#41; 語句參考](/sql/dmx/data-mining-extensions-dmx-statements) </span><span class="sxs-lookup"><span data-stu-id="29ac8-122">[Data Mining Extensions &#40;DMX&#41; Statement Reference](/sql/dmx/data-mining-extensions-dmx-statements) </span></span>  
 [<span data-ttu-id="29ac8-123">預測查詢產生器 &#40;資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="29ac8-123">Prediction Query Builder &#40;Data Mining&#41;</span></span>](prediction-query-builder-data-mining.md)  
  
  
