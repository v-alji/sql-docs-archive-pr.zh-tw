---
title: '[執行 SQL 工作編輯器] ([結果集] 頁面) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.executesqltask.resultset.f1
helpviewer_keywords:
- Execute SQL Task Editor
ms.assetid: d27000c8-8d91-4e1c-b45e-bca9a3c12f6d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 027f3c77e84b47958e9fb6567acdb308c14eb1e7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594124"
---
# <a name="execute-sql-task-editor-result-set-page"></a><span data-ttu-id="5c899-102">執行 SQL 工作編輯器 (結果集頁面)</span><span class="sxs-lookup"><span data-stu-id="5c899-102">Execute SQL Task Editor (Result Set Page)</span></span>
  <span data-ttu-id="5c899-103">使用 [執行 SQL 工作編輯器]  對話方塊的 [結果集]  頁面，即可將 SQL 陳述式的結果對應至新的或現有的變數。</span><span class="sxs-lookup"><span data-stu-id="5c899-103">Use the **Result Set** page of the **Execute SQL Task Editor** dialog to map the result of the SQL statement to new or existing variables.</span></span> <span data-ttu-id="5c899-104">如果 [一般] 頁面上的 [結果集]  已設定為 [無]  ，就會停用此對話方塊中的選項。</span><span class="sxs-lookup"><span data-stu-id="5c899-104">The options in this dialog box are disabled if **ResultSet** on the General page is set to **None**.</span></span>  
  
 <span data-ttu-id="5c899-105">如需這項工作的詳細資訊，請參閱[執行 SQL 工作](control-flow/execute-sql-task.md)和[執行 SQL 工作中的結果集](../../2014/integration-services/result-sets-in-the-execute-sql-task.md)。</span><span class="sxs-lookup"><span data-stu-id="5c899-105">For more information about this task, see [Execute SQL Task](control-flow/execute-sql-task.md) and [Result Sets in the Execute SQL Task](../../2014/integration-services/result-sets-in-the-execute-sql-task.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="5c899-106">選項。</span><span class="sxs-lookup"><span data-stu-id="5c899-106">Options</span></span>  
 <span data-ttu-id="5c899-107">**結果名稱**</span><span class="sxs-lookup"><span data-stu-id="5c899-107">**Result Name**</span></span>  
 <span data-ttu-id="5c899-108">按一下 [加入]  加入結果集對應集之後，請為結果提供名稱。</span><span class="sxs-lookup"><span data-stu-id="5c899-108">After you have added a result set mapping set by clicking **Add**, provide a name for the result.</span></span> <span data-ttu-id="5c899-109">您必須根據結果集類型來使用特定的結果名稱。</span><span class="sxs-lookup"><span data-stu-id="5c899-109">Depending on the result set type, you must use specific result names.</span></span>  
  
 <span data-ttu-id="5c899-110">如果結果集類型是「 **單一資料列**」，則您可以使用查詢所傳回之資料行的名稱，或查詢所傳回之資料行的資料行清單中，代表資料行位置的數字。</span><span class="sxs-lookup"><span data-stu-id="5c899-110">If the result set type is **Single row**, you can use either the name of a column returned by the query or the number that represents the position of a column in the column list of a column returned by the query.</span></span>  
  
 <span data-ttu-id="5c899-111">如果結果集類型為 **完整結果集** 或 **XML**，則必須使用 0 作為結果集名稱。</span><span class="sxs-lookup"><span data-stu-id="5c899-111">If the result set type is **Full result set** or **XML**, you must use 0 as the result set name.</span></span>  
  
 <span data-ttu-id="5c899-112">**相關主題**： [執行 SQL 工作中的結果集](../../2014/integration-services/result-sets-in-the-execute-sql-task.md)</span><span class="sxs-lookup"><span data-stu-id="5c899-112">**Related Topics**: [Result Sets in the Execute SQL Task](../../2014/integration-services/result-sets-in-the-execute-sql-task.md)</span></span>  
  
 <span data-ttu-id="5c899-113">**變數名稱**</span><span class="sxs-lookup"><span data-stu-id="5c899-113">**Variable Name**</span></span>  
 <span data-ttu-id="5c899-114">選取變數來將結果集對應至變數，或按一下 \<**New variable...**>，使用 [新增變數] 對話方塊來新增新的變數。</span><span class="sxs-lookup"><span data-stu-id="5c899-114">Map the result set to a variable by selecting a variable or click \<**New variable...**> to add a new variable by using the **Add Variable** dialog box.</span></span>  
  
 <span data-ttu-id="5c899-115">**加入**</span><span class="sxs-lookup"><span data-stu-id="5c899-115">**Add**</span></span>  
 <span data-ttu-id="5c899-116">按一下即可新增結果集對應。</span><span class="sxs-lookup"><span data-stu-id="5c899-116">Click to add a result set mapping.</span></span>  
  
 <span data-ttu-id="5c899-117">**移除**</span><span class="sxs-lookup"><span data-stu-id="5c899-117">**Remove**</span></span>  
 <span data-ttu-id="5c899-118">選取清單中的結果集對應，然後按一下 [移除]  。</span><span class="sxs-lookup"><span data-stu-id="5c899-118">Select a result set mapping in the list and then click **Remove**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c899-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5c899-119">See Also</span></span>  
 <span data-ttu-id="5c899-120">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="5c899-120">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="5c899-121">[&#40;一般頁面&#41;執行 SQL 工作編輯器](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="5c899-121">[Execute SQL Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="5c899-122">[[執行 SQL 工作編輯器] &#40;[參數對應] 頁面&#41;](../../2014/integration-services/execute-sql-task-editor-parameter-mapping-page.md) </span><span class="sxs-lookup"><span data-stu-id="5c899-122">[Execute SQL Task Editor &#40;Parameter Mapping Page&#41;](../../2014/integration-services/execute-sql-task-editor-parameter-mapping-page.md) </span></span>  
 [<span data-ttu-id="5c899-123">Transact-SQL 參考 &#40;資料庫引擎41;</span><span class="sxs-lookup"><span data-stu-id="5c899-123">Transact-SQL Reference &#40;Database Engine&#41;</span></span>](/sql/t-sql/language-reference)  
  
  
