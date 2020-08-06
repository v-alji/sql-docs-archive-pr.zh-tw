---
title: 選取不符合某值的資料列 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- search conditions [SQL Server], rows not matching value
- row not matching value [SQL Server]
- NOT operator [Visual Database Tools]
- search criteria [SQL Server], rows not matching value
ms.assetid: 19898578-7b2f-401c-bb8f-9f2a017efdf7
author: stevestein
ms.author: sstein
ms.openlocfilehash: 412ec93cbfedc87e92da9e86c7e4c7455919722a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703686"
---
# <a name="select-rows-that-do-not-match-a-value-visual-database-tools"></a><span data-ttu-id="91425-102">選取不符合某值的資料列 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="91425-102">Select Rows That Do Not Match a Value (Visual Database Tools)</span></span>
  <span data-ttu-id="91425-103">若要尋找不符合某值的資料列，請使用 NOT 運算子。</span><span class="sxs-lookup"><span data-stu-id="91425-103">To find rows that do not match a value, use the NOT operator.</span></span>  
  
### <a name="to-find-rows-that-do-not-match-a-value"></a><span data-ttu-id="91425-104">若要尋找不符合值的資料列</span><span class="sxs-lookup"><span data-stu-id="91425-104">To find rows that do not match a value</span></span>  
  
1.  <span data-ttu-id="91425-105">如果尚未這麼做，請將想要在搜尋條件中使用的資料行或運算式新增至 [準則窗格](visual-database-tools.md)中。</span><span class="sxs-lookup"><span data-stu-id="91425-105">If you have not done so already, add the columns or expressions that you want to use within your search condition to the [Criteria pane](visual-database-tools.md).</span></span>  
  
2.  <span data-ttu-id="91425-106">尋找包含想要搜尋之資料行或運算式的資料列，然後在 [篩選條件]  方格資料行中輸入 NOT 運算子，後面再加上搜尋值。</span><span class="sxs-lookup"><span data-stu-id="91425-106">Locate the row containing the data column or expression to search, and then in the **Filter** grid column, enter the NOT operator followed by a search value.</span></span>  
  
 <span data-ttu-id="91425-107">例如，若要尋找 `products` 資料表中產品代碼資料行不是以 "A," 為開頭的所有資料列，則可以輸入如下所示的搜尋條件：</span><span class="sxs-lookup"><span data-stu-id="91425-107">For example, to find all the rows in a `products` table where the values in the product code column begin with a character other than "A," you can enter a search condition such as the following:</span></span>  
  
```  
NOT LIKE 'A%'  
```  
  
## <a name="see-also"></a><span data-ttu-id="91425-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="91425-108">See Also</span></span>  
 <span data-ttu-id="91425-109">[&#40;Visual Database Tools 輸入搜尋值的規則&#41;](rules-for-entering-search-values-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="91425-109">[Rules for Entering Search Values &#40;Visual Database Tools&#41;](rules-for-entering-search-values-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="91425-110">指定搜尋準則 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="91425-110">Specify Search Criteria &#40;Visual Database Tools&#41;</span></span>](specify-search-criteria-visual-database-tools.md)  
  
  
