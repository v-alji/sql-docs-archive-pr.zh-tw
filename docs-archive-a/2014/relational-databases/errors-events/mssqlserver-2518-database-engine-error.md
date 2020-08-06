---
title: MSSQLSERVER_2518 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2518 (Database Engine error)
ms.assetid: 54a13abc-4c33-43f0-b55d-e2e74a1381c8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5f5517458c1014d7830c4813b95e1120bef452e4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594089"
---
# <a name="mssqlserver_2518"></a><span data-ttu-id="99fe0-102">MSSQLSERVER_2518</span><span class="sxs-lookup"><span data-stu-id="99fe0-102">MSSQLSERVER_2518</span></span>
    
## <a name="details"></a><span data-ttu-id="99fe0-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="99fe0-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="99fe0-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="99fe0-104">Product Name</span></span>|<span data-ttu-id="99fe0-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="99fe0-105">SQL Server</span></span>|  
|<span data-ttu-id="99fe0-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="99fe0-106">Event ID</span></span>|<span data-ttu-id="99fe0-107">2518</span><span class="sxs-lookup"><span data-stu-id="99fe0-107">2518</span></span>|  
|<span data-ttu-id="99fe0-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="99fe0-108">Event Source</span></span>|<span data-ttu-id="99fe0-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="99fe0-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="99fe0-110">元件</span><span class="sxs-lookup"><span data-stu-id="99fe0-110">Component</span></span>|<span data-ttu-id="99fe0-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="99fe0-111">SQLEngine</span></span>|  
|<span data-ttu-id="99fe0-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="99fe0-112">Symbolic Name</span></span>|<span data-ttu-id="99fe0-113">DBCC_NO_EXPRESSION_EVAL_CLR_DISABLED</span><span class="sxs-lookup"><span data-stu-id="99fe0-113">DBCC_NO_EXPRESSION_EVAL_CLR_DISABLED</span></span>|  
|<span data-ttu-id="99fe0-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="99fe0-114">Message Text</span></span>|<span data-ttu-id="99fe0-115">物件識別碼 O_ID (物件"O_NAME")：無法檢查此物件的計算資料行和使用者定義型別，因為通用語言執行平台 (CLR) 已停用。</span><span class="sxs-lookup"><span data-stu-id="99fe0-115">Object ID O_ID (object "O_NAME"): Computed columns and user-defined types cannot be checked for this object because the common language runtime (CLR) is disabled.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="99fe0-116">說明</span><span class="sxs-lookup"><span data-stu-id="99fe0-116">Explanation</span></span>  
 <span data-ttu-id="99fe0-117">這項參考用訊息指出查詢處理器無法提供 DBCC 與內部物件，以便評估計算資料行和 Common Language Runtime (CLR) 使用者自訂類型。</span><span class="sxs-lookup"><span data-stu-id="99fe0-117">This informational message indicates that the query processor could not provide DBCC with an internal object to allow for computed columns and common language runtime (CLR) user-defined types to be evaluated.</span></span> <span data-ttu-id="99fe0-118">發生這個問題的原因是因為其中一個資料行包含 CLR，但是 CLR 並未啟用。</span><span class="sxs-lookup"><span data-stu-id="99fe0-118">This problem occurred because one of the columns involved the CLR, but the CLR is not enabled.</span></span> <span data-ttu-id="99fe0-119">該內部物件涵蓋所有資料行。</span><span class="sxs-lookup"><span data-stu-id="99fe0-119">The internal object covers all columns.</span></span> <span data-ttu-id="99fe0-120">因此，無法評估單一資料行也會造成無法建立內部物件的結果。</span><span class="sxs-lookup"><span data-stu-id="99fe0-120">Therefore, the inability to evaluate a single column prevents creating the internal object.</span></span> <span data-ttu-id="99fe0-121">這表示 DBCC 不會在檢查索引和基底資料表的一致性時檢查計算資料行的正確性，或是使用這些計算資料行。</span><span class="sxs-lookup"><span data-stu-id="99fe0-121">This means that computed columns will not be checked for correctness or be used when DBCC checks the consistency between indexes and base tables.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="99fe0-122">使用者動作</span><span class="sxs-lookup"><span data-stu-id="99fe0-122">User Action</span></span>  
 <span data-ttu-id="99fe0-123">啟用 CLR，然後重新執行 DBCC 陳述式。</span><span class="sxs-lookup"><span data-stu-id="99fe0-123">Enable CLR and rerun the DBCC statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99fe0-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="99fe0-124">See Also</span></span>  
 [<span data-ttu-id="99fe0-125">啟用 CLR 整合</span><span class="sxs-lookup"><span data-stu-id="99fe0-125">Enabling CLR Integration</span></span>](../clr-integration/clr-integration-enabling.md)  
  
  
