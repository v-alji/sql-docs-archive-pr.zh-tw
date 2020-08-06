---
title: 排除重複的資料列 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- search criteria [SQL Server], excluding rows
- row duplicates [SQL Server]
- duplicate rows
- row excluded in search [SQL Server]
- result sets [SQL Server], duplicate values
- excluding rows
ms.assetid: ab35a363-421d-4665-946b-ae3f6397af50
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3b396f2738f6895684d828884d4822ea9165e0a9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606001"
---
# <a name="exclude-duplicate-rows-visual-database-tools"></a><span data-ttu-id="e09b9-102">排除重複的資料列 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="e09b9-102">Exclude Duplicate Rows (Visual Database Tools)</span></span>
  <span data-ttu-id="e09b9-103">如果您只想在結果集中查看唯一的值，您可以指定您要從結果集排除重複的項目。</span><span class="sxs-lookup"><span data-stu-id="e09b9-103">If you want to see only unique values in a result set, you can specify that you want to exclude duplicates from the result set.</span></span>  
  
### <a name="to-exclude-duplicate-rows-from-the-result-set"></a><span data-ttu-id="e09b9-104">若要從結果集排除重複資料列</span><span class="sxs-lookup"><span data-stu-id="e09b9-104">To exclude duplicate rows from the result set</span></span>  
  
1.  <span data-ttu-id="e09b9-105">在 [圖表] 窗格的背景上按一下滑鼠右鍵，然後從快速鍵功能表中選擇 [屬性]  。</span><span class="sxs-lookup"><span data-stu-id="e09b9-105">Right-click the background of the Diagram pane, then choose **Properties** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="e09b9-106">在 [屬性] 視窗中，按一下 [重複資料僅顯示一筆]  ，並且將值設定為 [是]  。</span><span class="sxs-lookup"><span data-stu-id="e09b9-106">In the Property window, click **Distinct values** and set the value to **Yes**.</span></span>  
  
     <span data-ttu-id="e09b9-107">[查詢和檢視設計師] 會將關鍵字 DISTINCT 插入至 SQL 陳述式中顯示資料行清單的前面。</span><span class="sxs-lookup"><span data-stu-id="e09b9-107">The Query and View Designer inserts the keyword DISTINCT in front of the list of display columns in the SQL statement.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e09b9-108">如果使用 DISTINCT 關鍵字，您可能無法在 [結果] 窗格中修改結果集。</span><span class="sxs-lookup"><span data-stu-id="e09b9-108">If you use the DISTINCT keyword you may not be able to modify the result set in the results pane.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e09b9-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e09b9-109">See Also</span></span>  
 <span data-ttu-id="e09b9-110">[&#40;Visual Database Tools 指定搜尋準則&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="e09b9-110">[Specify Search Criteria &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 [<span data-ttu-id="e09b9-111">排序及分組查詢結果 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="e09b9-111">Sort and Group Query Results &#40;Visual Database Tools&#41;</span></span>](sort-and-group-query-results-visual-database-tools.md)  
  
  
