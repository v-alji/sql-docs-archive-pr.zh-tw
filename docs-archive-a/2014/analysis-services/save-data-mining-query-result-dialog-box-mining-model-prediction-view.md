---
title: '[儲存資料] [挖掘查詢結果] 對話方塊 ([採礦模型預測] 視圖) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dm.savedataminingqueryresult.f1
helpviewer_keywords:
- Save Data Mining Query Result dialog box
ms.assetid: 112fb527-7466-4fd4-9cf1-75596135648f
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0838c90f0797a0db9c8a66cd8c5f877aaecdad0a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592925"
---
# <a name="save-data-mining-query-result-dialog-box-mining-model-prediction-view"></a><span data-ttu-id="9d189-102">儲存資料採礦查詢結果對話方塊 (採礦模型預測檢視)</span><span class="sxs-lookup"><span data-stu-id="9d189-102">Save Data Mining Query Result Dialog Box (Mining Model Prediction View)</span></span>
  <span data-ttu-id="9d189-103">使用 **[儲存資料採礦查詢結果]** 對話方塊，即可將資料採礦查詢的結果儲存到新的資料表。</span><span class="sxs-lookup"><span data-stu-id="9d189-103">Use the **Save Data Mining Query Result** dialog box to save the results of a data mining query to a new table.</span></span>  
  
 <span data-ttu-id="9d189-104">新的資料表將建立在資料來源所定義的資料庫中。</span><span class="sxs-lookup"><span data-stu-id="9d189-104">The new table will be created in the database defined by the data source.</span></span>  
  
## <a name="options"></a><span data-ttu-id="9d189-105">選項</span><span class="sxs-lookup"><span data-stu-id="9d189-105">Options</span></span>  
 <span data-ttu-id="9d189-106">**資料來源**</span><span class="sxs-lookup"><span data-stu-id="9d189-106">**Data Source**</span></span>  
 <span data-ttu-id="9d189-107">從目前的專案中選取資料來源。</span><span class="sxs-lookup"><span data-stu-id="9d189-107">Select a data source from the current project.</span></span> <span data-ttu-id="9d189-108">如果正確的資料來源不存在，請按一下 **[新增]** 建立新的資料來源。</span><span class="sxs-lookup"><span data-stu-id="9d189-108">If the correct data source does not exist, click **New** to create a new data source.</span></span>  
  
 <span data-ttu-id="9d189-109">**新增**</span><span class="sxs-lookup"><span data-stu-id="9d189-109">**New**</span></span>  
 <span data-ttu-id="9d189-110">開啟 [資料來源精靈]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9d189-110">Opens the **Data Source Wizard**.</span></span>  
  
 <span data-ttu-id="9d189-111">**資料表名稱**</span><span class="sxs-lookup"><span data-stu-id="9d189-111">**Table Name**</span></span>  
 <span data-ttu-id="9d189-112">輸入新資料表的名稱。</span><span class="sxs-lookup"><span data-stu-id="9d189-112">Type a name for the new table.</span></span>  
  
 <span data-ttu-id="9d189-113">**如果存在則覆寫**</span><span class="sxs-lookup"><span data-stu-id="9d189-113">**Overwrite if exists**</span></span>  
 <span data-ttu-id="9d189-114">如果您要以相同名稱覆寫現有的資料表，請選取此選項。</span><span class="sxs-lookup"><span data-stu-id="9d189-114">Select this option if you want to overwrite an existing table with the same name.</span></span>  
  
 <span data-ttu-id="9d189-115">如果下列任何一種情況成立，就必須覆寫現有的資料表：</span><span class="sxs-lookup"><span data-stu-id="9d189-115">Overwriting the existing table is required if any of the following is true:</span></span>  
  
-   <span data-ttu-id="9d189-116">您已將資料行加入至預測查詢。</span><span class="sxs-lookup"><span data-stu-id="9d189-116">You added columns to the prediction query.</span></span>  
  
-   <span data-ttu-id="9d189-117">您已在預測查詢中變更任何資料行的名稱或資料類型。</span><span class="sxs-lookup"><span data-stu-id="9d189-117">You changed the names or data types of any columns in the prediction query.</span></span>  
  
-   <span data-ttu-id="9d189-118">您已在目的地資料表上執行 ALTER 陳述式。</span><span class="sxs-lookup"><span data-stu-id="9d189-118">You ran an ALTER statement on the destination table.</span></span>  
  
 <span data-ttu-id="9d189-119">如果多個資料行具有相同的名稱 (例如，許多衍生的資料行可能具有預設資料行名稱 [運算式]\*\*\*\*)，您就必須針對名稱重複的每個資料行建立別名。</span><span class="sxs-lookup"><span data-stu-id="9d189-119">If multiple columns have the same name (for example, several derived columns might have the default column name **Expression**), you must create an alias for each column with a duplicate name.</span></span> <span data-ttu-id="9d189-120">如果資料行沒有唯一的名稱，當設計師嘗試將結果儲存至 SQL Server 時，將會引發錯誤，因為資料表中的資料行必須具有唯一的名稱。</span><span class="sxs-lookup"><span data-stu-id="9d189-120">If the columns do not have unique names, an error will be raised when the designer tries to save the results to SQL Server, because columns in a table must have unique names.</span></span>  
  
 <span data-ttu-id="9d189-121">**加入至 DSV**</span><span class="sxs-lookup"><span data-stu-id="9d189-121">**Add to DSV**</span></span>  
 <span data-ttu-id="9d189-122">(選擇性) 如果您要將資料表加入至現有的資料來源，請選取專案中包含的資料來源檢視。</span><span class="sxs-lookup"><span data-stu-id="9d189-122">(Optional) Select a data source view contained in the project if you want to add the table to an existing data source.</span></span>  
  
 <span data-ttu-id="9d189-123">如果您想要在相同的資料來源中保留模型的所有相關資料表（例如定型資料、預測來源資料和查詢結果），這個選項就很有用。</span><span class="sxs-lookup"><span data-stu-id="9d189-123">This option is useful if you want to keep all related tables for a model-such as training data, prediction source data, and query results-in the same data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d189-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9d189-124">See Also</span></span>  
 <span data-ttu-id="9d189-125">[預測查詢產生器 &#40;資料採礦&#41;](prediction-query-builder-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="9d189-125">[Prediction Query Builder &#40;Data Mining&#41;](prediction-query-builder-data-mining.md) </span></span>  
 <span data-ttu-id="9d189-126">[資料採礦查詢介面](data-mining/data-mining-query-tools.md) </span><span class="sxs-lookup"><span data-stu-id="9d189-126">[Data Mining Query Interfaces](data-mining/data-mining-query-tools.md) </span></span>  
 [<span data-ttu-id="9d189-127">資料採礦延伸模組 &#40;DMX&#41; 陳述式參考</span><span class="sxs-lookup"><span data-stu-id="9d189-127">Data Mining Extensions &#40;DMX&#41; Statement Reference</span></span>](/sql/dmx/data-mining-extensions-dmx-statements)  
  
  
