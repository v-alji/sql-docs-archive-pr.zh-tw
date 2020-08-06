---
title: 查詢參數對話方塊 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdtsql.chm:69645
- vdt.dlgbox.definequeryparameters
ms.assetid: 31cdaee2-d7cd-4d64-a45f-924b27e8b1f0
author: stevestein
ms.author: sstein
ms.openlocfilehash: 76052876ad2899fc959aa7fc49f4299e08bac713
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688405"
---
# <a name="query-parameters-dialog-box-visual-database-tools"></a><span data-ttu-id="5758c-102">查詢參數對話方塊 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="5758c-102">Query Parameters Dialog Box (Visual Database Tools)</span></span>
  <span data-ttu-id="5758c-103">這對話方塊可以讓您輸入查詢中定義的參數值。</span><span class="sxs-lookup"><span data-stu-id="5758c-103">This dialog allows you to enter values for the parameters defined in the query.</span></span> <span data-ttu-id="5758c-104">執行查詢時，如果查詢中包含在執行階段期間需要使用者輸入的參數，此對話方塊就會出現。</span><span class="sxs-lookup"><span data-stu-id="5758c-104">This dialog box appears when you execute a query that contains parameters that require end-user input at run time.</span></span>  
  
## <a name="options"></a><span data-ttu-id="5758c-105">選項。</span><span class="sxs-lookup"><span data-stu-id="5758c-105">Options</span></span>  
 <span data-ttu-id="5758c-106">**名稱**</span><span class="sxs-lookup"><span data-stu-id="5758c-106">**Name**</span></span>  
 <span data-ttu-id="5758c-107">列出針對正在執行之查詢所定義的參數。</span><span class="sxs-lookup"><span data-stu-id="5758c-107">Lists the parameters defined for the query being executed.</span></span> <span data-ttu-id="5758c-108">如果查詢包含具名參數，名稱會出現在清單中。</span><span class="sxs-lookup"><span data-stu-id="5758c-108">If the query contains named parameters, the names appear in the list.</span></span> <span data-ttu-id="5758c-109">如果查詢包含未命名的參數，則查詢中會針對每個參數列出系統定義的參數名稱。</span><span class="sxs-lookup"><span data-stu-id="5758c-109">If the query contains unnamed parameters, system-defined parameter names are listed for each parameter in the query.</span></span>  
  
 <span data-ttu-id="5758c-110">**ReplTest1**</span><span class="sxs-lookup"><span data-stu-id="5758c-110">**Value**</span></span>  
 <span data-ttu-id="5758c-111">請輸入 [Name]  下方列出的每個參數值。</span><span class="sxs-lookup"><span data-stu-id="5758c-111">Enter the value for each parameter listed under **Name**.</span></span> <span data-ttu-id="5758c-112">最近使用的值將顯示為預設參數值。</span><span class="sxs-lookup"><span data-stu-id="5758c-112">The value used most recently appears as the default parameter value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5758c-113">範例</span><span class="sxs-lookup"><span data-stu-id="5758c-113">Example</span></span>  
 <span data-ttu-id="5758c-114">在 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 資料庫中執行下列 [SQL 窗格] 中的查詢時，會開啟 [查詢參數] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="5758c-114">The following query in the SQL Pane, opens the Query Parameters dialog box when executed in the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span>  
  
```  
SELECT   FirstName, LastName  
FROM    Person.Person AS Lastname  
WHERE   (LastName = @Param1);  
```  
  
## <a name="see-also"></a><span data-ttu-id="5758c-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5758c-115">See Also</span></span>  
 [<span data-ttu-id="5758c-116">使用參數查詢 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="5758c-116">Query with Parameters &#40;Visual Database Tools&#41;</span></span>](visual-database-tools.md)  
  
  
