---
title: 驗證查詢 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdtsql.chm:100644
helpviewer_keywords:
- verifying queries
- queries [SQL Server], verifying
- checking queries
ms.assetid: 1382c0c0-46dc-45f9-ab38-9bba1d347eea
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7bf24de9bdc0e8b7b7ceb33bb881812b180ce112
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596964"
---
# <a name="verify-queries-visual-database-tools"></a><span data-ttu-id="db8ac-102">驗證查詢 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="db8ac-102">Verify Queries (Visual Database Tools)</span></span>
  <span data-ttu-id="db8ac-103">為避免發生問題，您可以檢查所建立的查詢，確定語法是否正確。</span><span class="sxs-lookup"><span data-stu-id="db8ac-103">To avoid problems, you can check the query you have built to ensure its syntax is correct.</span></span> <span data-ttu-id="db8ac-104">當您在 [SQL 窗格](visual-database-tools.md)輸入陳述式時，這個選項特別有用。</span><span class="sxs-lookup"><span data-stu-id="db8ac-104">This option is especially useful when you enter statements in the [SQL pane](visual-database-tools.md).</span></span>  
  
 <span data-ttu-id="db8ac-105">關於驗證查詢的注意事項：</span><span class="sxs-lookup"><span data-stu-id="db8ac-105">Some notes to keep in mind about verifying queries:</span></span>  
  
-   <span data-ttu-id="db8ac-106">即使在 [圖表]  窗格和 [準則]  窗格中無法表示陳述式，其語法也可以是正確的，因此能夠成功地驗證。</span><span class="sxs-lookup"><span data-stu-id="db8ac-106">A statement can be valid, and therefore be verified successfully, even if it cannot be represented in the **Diagram Pane** and **Criteria Pane**.</span></span>  
  
-   <span data-ttu-id="db8ac-107">[SQL 驗證] 能夠偵測某些，但不是所有的 SQL 錯誤。</span><span class="sxs-lookup"><span data-stu-id="db8ac-107">SQL Verification can detect some, but not all SQL errors.</span></span> <span data-ttu-id="db8ac-108">如果查詢中包含在 SQL 驗證期間未偵測到的錯誤，當您執行查詢時，資料庫會偵測到錯誤。</span><span class="sxs-lookup"><span data-stu-id="db8ac-108">If a query contains an error not detected during SQL verification, the database will detect the error when you run the query.</span></span>  
  
-   <span data-ttu-id="db8ac-109">包含無法驗證參數的查詢。</span><span class="sxs-lookup"><span data-stu-id="db8ac-109">Queries that contain parameters cannot be verified.</span></span>  
  
### <a name="to-verify-an-sql-statement"></a><span data-ttu-id="db8ac-110">若要驗證 SQL 陳述式</span><span class="sxs-lookup"><span data-stu-id="db8ac-110">To verify an SQL statement</span></span>  
  
-   <span data-ttu-id="db8ac-111">在 [SQL]  窗格按一下滑鼠右鍵，然後從快速鍵功能表選取 [驗證 SQL 語法]  。</span><span class="sxs-lookup"><span data-stu-id="db8ac-111">Right-click in the **SQL Pane**, and select **Verify SQL Syntax** from the shortcut menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db8ac-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="db8ac-112">See Also</span></span>  
 <span data-ttu-id="db8ac-113">[&#40;Visual Database Tools 執行查詢&#41;](run-queries-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="db8ac-113">[Run Queries &#40;Visual Database Tools&#41;](run-queries-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="db8ac-114">使用查詢執行基本作業 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="db8ac-114">Perform Basic Operations with Queries &#40;Visual Database Tools&#41;</span></span>](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  
