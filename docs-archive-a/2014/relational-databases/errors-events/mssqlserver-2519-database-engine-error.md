---
title: MSSQLSERVER_2519 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2519 (Database Engine error)
ms.assetid: 8dc6ad98-5db8-4c88-8dea-6d455e63b839
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c8577b07586553f4b03714cd31451ac755faf824
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585475"
---
# <a name="mssqlserver_2519"></a><span data-ttu-id="b800d-102">MSSQLSERVER_2519</span><span class="sxs-lookup"><span data-stu-id="b800d-102">MSSQLSERVER_2519</span></span>
    
## <a name="details"></a><span data-ttu-id="b800d-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="b800d-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b800d-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="b800d-104">Product Name</span></span>|<span data-ttu-id="b800d-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="b800d-105">SQL Server</span></span>|  
|<span data-ttu-id="b800d-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="b800d-106">Event ID</span></span>|<span data-ttu-id="b800d-107">2519</span><span class="sxs-lookup"><span data-stu-id="b800d-107">2519</span></span>|  
|<span data-ttu-id="b800d-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="b800d-108">Event Source</span></span>|<span data-ttu-id="b800d-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="b800d-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="b800d-110">元件</span><span class="sxs-lookup"><span data-stu-id="b800d-110">Component</span></span>|<span data-ttu-id="b800d-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="b800d-111">SQLEngine</span></span>|  
|<span data-ttu-id="b800d-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="b800d-112">Symbolic Name</span></span>|<span data-ttu-id="b800d-113">DBCC_NO_EXPRESSION_EVALUATOR</span><span class="sxs-lookup"><span data-stu-id="b800d-113">DBCC_NO_EXPRESSION_EVALUATOR</span></span>|  
|<span data-ttu-id="b800d-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="b800d-114">Message Text</span></span>|<span data-ttu-id="b800d-115">無法檢查物件識別碼 O_ID (物件 "O_NAME") 的計算資料行和使用者自訂類型，因為內部運算式評估工具無法初始化。</span><span class="sxs-lookup"><span data-stu-id="b800d-115">Computed columns and user-defined types cannot be checked for object ID O_ID (object "O_NAME") because the internal expression evaluator could not be initialized.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="b800d-116">說明</span><span class="sxs-lookup"><span data-stu-id="b800d-116">Explanation</span></span>  
 <span data-ttu-id="b800d-117">這項參考用訊息指出查詢處理器無法提供 DBCC 與內部物件，以便評估計算資料行和 Common Language Runtime (CLR) 使用者自訂類型。</span><span class="sxs-lookup"><span data-stu-id="b800d-117">This informational message indicates that the query processor could not provide DBCC with an internal object to allow for the evaluation of computed columns and common language runtime (CLR) user-defined types.</span></span> <span data-ttu-id="b800d-118">這表示 DBCC 不會在檢查索引和基底資料表的一致性時檢查計算資料行和 CLR 使用者自訂類型的正確性，或是使用這些使用者自訂類型。</span><span class="sxs-lookup"><span data-stu-id="b800d-118">This means that computed columns and CLR user-defined types will not be checked for correctness or be used when DBCC checks the consistency between indexes and base tables.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="b800d-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="b800d-119">User Action</span></span>  
 <span data-ttu-id="b800d-120">None</span><span class="sxs-lookup"><span data-stu-id="b800d-120">None</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b800d-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b800d-121">See Also</span></span>  
 [<span data-ttu-id="b800d-122">MSSQLSERVER_2518</span><span class="sxs-lookup"><span data-stu-id="b800d-122">MSSQLSERVER_2518</span></span>](mssqlserver-2518-database-engine-error.md)  
  
  
