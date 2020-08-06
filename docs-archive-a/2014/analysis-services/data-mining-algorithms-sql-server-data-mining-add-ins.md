---
title: 資料採礦演算法 (SQL Server 資料採礦增益集) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- segmentation
- data mining algorithms
- clustering [data mining]
- linear regression
- association [data mining]
- neural networks
- logistic regression
- regression
- sequence analysis
- decision tree [data mining]
- Naive Bayes
- time series [data mining]
ms.assetid: 3a1a62e4-9fb5-4cdb-a6c6-1b8b30d417ef
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3a73ce5a538756a740afd2db72d585fa54f03cae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599281"
---
# <a name="data-mining-algorithms-sql-server-data-mining-add-ins"></a><span data-ttu-id="1b545-102">資料採礦演算法 (SQL Server 資料採礦增益集)</span><span class="sxs-lookup"><span data-stu-id="1b545-102">Data Mining Algorithms (SQL Server Data Mining Add-ins)</span></span>
  <span data-ttu-id="1b545-103">適用於 Office 的資料採礦增益集支援使用下列資料採礦演算法建立分析模型。</span><span class="sxs-lookup"><span data-stu-id="1b545-103">The Data Mining Add-ins for Office supports creation of analytical models using the following data mining algorithms.</span></span> <span data-ttu-id="1b545-104">所有的演算法都是根據已知的機器學習方法而由 Microsoft Research 實作過。</span><span class="sxs-lookup"><span data-stu-id="1b545-104">All algorithms are based on well-known machine learning methods and have been implemented by Microsoft Research.</span></span>  
  
## <a name="algorithms"></a><span data-ttu-id="1b545-105">演算法</span><span class="sxs-lookup"><span data-stu-id="1b545-105">Algorithms</span></span>  
  
|<span data-ttu-id="1b545-106">機器學習方法</span><span class="sxs-lookup"><span data-stu-id="1b545-106">Machine learning method</span></span>|<span data-ttu-id="1b545-107">運作方式</span><span class="sxs-lookup"><span data-stu-id="1b545-107">How it works</span></span>|  
|-----------------------------|------------------|  
|<span data-ttu-id="1b545-108">Microsoft 關聯規則演算法</span><span class="sxs-lookup"><span data-stu-id="1b545-108">Microsoft Association Rules  algorithm</span></span>|<span data-ttu-id="1b545-109">探索會一起購買的產品或一同發生的事件，並且使用模型產生建議。</span><span class="sxs-lookup"><span data-stu-id="1b545-109">Discover which products are purchased together or which events occur together, and use the model to create recommendations.</span></span><br /><br /> [https://msdn.microsoft.com/library/ms174916.aspx](https://msdn.microsoft.com/library/ms174916.aspx)|  
|<span data-ttu-id="1b545-110">Microsoft 叢集演算法</span><span class="sxs-lookup"><span data-stu-id="1b545-110">Microsoft Clustering algorithm</span></span>|<span data-ttu-id="1b545-111">定義市場區隔、自動將相關的客戶分組，或尋找資料的關聯性以用於進一步採礦。</span><span class="sxs-lookup"><span data-stu-id="1b545-111">Define market segments, automatically group related customers together, or find relationships in data to use in further mining.</span></span><br /><br /> [https://msdn.microsoft.com/library/ms174879.aspx](https://msdn.microsoft.com/library/ms174879.aspx)|  
|<span data-ttu-id="1b545-112">Microsoft 決策樹演算法</span><span class="sxs-lookup"><span data-stu-id="1b545-112">Microsoft Decision Trees algorithm</span></span>|<span data-ttu-id="1b545-113">識別資料的各種元素之間原本未知的關聯性，以利做出更明智的決策或尋找導致特定結果的因素。</span><span class="sxs-lookup"><span data-stu-id="1b545-113">Identify previously unknown relationships between various elements of your data to better inform your decisions, or find the factors that lead to specific outcomes.</span></span><br /><br /> [https://msdn.microsoft.com/library/ms174923.aspx](https://msdn.microsoft.com/library/ms174923.aspx)|  
|<span data-ttu-id="1b545-114">Microsoft 線性迴歸演算法</span><span class="sxs-lookup"><span data-stu-id="1b545-114">Microsoft Linear Regression algorithm</span></span>|<span data-ttu-id="1b545-115">尋找數學公式，其內容描述促成數值結果的因素。</span><span class="sxs-lookup"><span data-stu-id="1b545-115">Find a mathematical formula that describes factors that contribute to a numeric outcome.</span></span><br /><br /> [https://msdn.microsoft.com/library/ms174824.aspx](https://msdn.microsoft.com/library/ms174824.aspx)|  
|<span data-ttu-id="1b545-116">Microsoft 羅吉斯迴歸演算法</span><span class="sxs-lookup"><span data-stu-id="1b545-116">Microsoft Logistic Regression algorithm</span></span>|<span data-ttu-id="1b545-117">識別促成二進位結果的因素，並且學習如何運用這些因素來影響結果。</span><span class="sxs-lookup"><span data-stu-id="1b545-117">Identify the factors that contribute to binary outcomes, and learn how to use those to affect results.</span></span><br /><br /> [https://msdn.microsoft.com/library/ms174828.aspx](https://msdn.microsoft.com/library/ms174828.aspx)|  
|<span data-ttu-id="1b545-118">Microsoft 貝氏機率分類演算法</span><span class="sxs-lookup"><span data-stu-id="1b545-118">Microsoft Naïve Bayes algorithm</span></span>|<span data-ttu-id="1b545-119">探索資料的關聯性，並且尋找與特定結果最密切相關的關聯性。</span><span class="sxs-lookup"><span data-stu-id="1b545-119">Explore relationships in your data and find those mostly closely correlated with an outcome.</span></span><br /><br /> [https://msdn.microsoft.com/library/ms174806.aspx](https://msdn.microsoft.com/library/ms174806.aspx)|  
|<span data-ttu-id="1b545-120">Microsoft 類神經網路演算法</span><span class="sxs-lookup"><span data-stu-id="1b545-120">Microsoft Neural Networks algorithm</span></span>|<span data-ttu-id="1b545-121">尋找多項輸入甚至多項輸出之間隱藏的關聯性。</span><span class="sxs-lookup"><span data-stu-id="1b545-121">Find hidden relationships among multiple inputs and even multiple outputs.</span></span> <span data-ttu-id="1b545-122">用於進行探索或預測。</span><span class="sxs-lookup"><span data-stu-id="1b545-122">Use for exploration or for prediction.</span></span><br /><br /> [https://msdn.microsoft.com/library/ms174941.aspx](https://msdn.microsoft.com/library/ms174941.aspx)|  
|<span data-ttu-id="1b545-123">Microsoft 時間序列演算法</span><span class="sxs-lookup"><span data-stu-id="1b545-123">Microsoft Time Series algorithm</span></span>|<span data-ttu-id="1b545-124">使用歷程記錄資料預測未來值。</span><span class="sxs-lookup"><span data-stu-id="1b545-124">Use historical data to forecast future values.</span></span><br /><br /> [https://msdn.microsoft.com/library/ms174923.aspx](https://msdn.microsoft.com/library/ms174923.aspx)|  
  
## <a name="advanced-options"></a><span data-ttu-id="1b545-125">進階選項</span><span class="sxs-lookup"><span data-stu-id="1b545-125">Advanced Options</span></span>  
 <span data-ttu-id="1b545-126">當您使用適用於 Excel 的資料採礦用戶端時，您可以選擇建立自己的資料採礦結構和模型或是微調演算法的參數。</span><span class="sxs-lookup"><span data-stu-id="1b545-126">When you use the Data Mining Client for Excel, you have the option to create your own data mining structures and models, or to fine-tune the parameters of the algorithms.</span></span>  
  
 [<span data-ttu-id="1b545-127">SQL Server 資料採礦增益集 &#40;的演算法參數&#41;</span><span class="sxs-lookup"><span data-stu-id="1b545-127">Algorithm Parameters &#40;SQL Server Data Mining Add-ins&#41;</span></span>](algorithm-parameters-sql-server-data-mining-add-ins.md)  
  
 <span data-ttu-id="1b545-128">使用這些進階選項自訂模型的方式有兩種：</span><span class="sxs-lookup"><span data-stu-id="1b545-128">There are two ways to customize your models using these advanced options:</span></span>  
  
-   <span data-ttu-id="1b545-129">使用 **[資料採礦查詢]** 精靈建立模型。</span><span class="sxs-lookup"><span data-stu-id="1b545-129">Use the **Data Mining Query** wizard to create your model.</span></span>  
  
-   <span data-ttu-id="1b545-130">在 **[資料採礦用戶端]** 中啟動精靈之後，按一下 **[參數]**。</span><span class="sxs-lookup"><span data-stu-id="1b545-130">In the **Data Mining Client**, after you start the wizard, click **Parameters**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b545-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1b545-131">See Also</span></span>  
 <span data-ttu-id="1b545-132">[查詢 &#40;SQL Server 資料採礦增益集&#41;](query-sql-server-data-mining-add-ins.md) </span><span class="sxs-lookup"><span data-stu-id="1b545-132">[Query &#40;SQL Server Data Mining Add-ins&#41;](query-sql-server-data-mining-add-ins.md) </span></span>  
 [<span data-ttu-id="1b545-133">適用于 Excel&#41;的先進模型化 &#40;資料採礦增益集</span><span class="sxs-lookup"><span data-stu-id="1b545-133">Advanced Modeling &#40;Data Mining Add-ins for Excel&#41;</span></span>](advanced-modeling-data-mining-add-ins-for-excel.md)  
  
  
