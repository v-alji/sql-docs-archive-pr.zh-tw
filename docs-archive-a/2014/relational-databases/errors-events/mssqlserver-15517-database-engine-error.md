---
title: MSSQLSERVER_15517 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 15517 (Database Engine error)
ms.assetid: f94287f5-129f-4c52-9d34-62b996088001
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b8e66e211faf03e1457953d0292e711cde1798ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598948"
---
# <a name="mssqlserver_15517"></a><span data-ttu-id="345d8-102">MSSQLSERVER_15517</span><span class="sxs-lookup"><span data-stu-id="345d8-102">MSSQLSERVER_15517</span></span>
    
## <a name="details"></a><span data-ttu-id="345d8-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="345d8-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="345d8-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="345d8-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="345d8-105">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="345d8-105">Event ID</span></span>|<span data-ttu-id="345d8-106">15517</span><span class="sxs-lookup"><span data-stu-id="345d8-106">15517</span></span>|  
|<span data-ttu-id="345d8-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="345d8-107">Event Source</span></span>|<span data-ttu-id="345d8-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="345d8-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="345d8-109">元件</span><span class="sxs-lookup"><span data-stu-id="345d8-109">Component</span></span>|<span data-ttu-id="345d8-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="345d8-110">SQLEngine</span></span>|  
|<span data-ttu-id="345d8-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="345d8-111">Symbolic Name</span></span>|<span data-ttu-id="345d8-112">SEC_CANNOTEXECUTEASUSER</span><span class="sxs-lookup"><span data-stu-id="345d8-112">SEC_CANNOTEXECUTEASUSER</span></span>|  
|<span data-ttu-id="345d8-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="345d8-113">Message Text</span></span>|<span data-ttu-id="345d8-114">無法以資料庫主體執行，因為主體 "*principal*" 不存在、無法模擬這種主體，或者您沒有權限。</span><span class="sxs-lookup"><span data-stu-id="345d8-114">Cannot execute as the database principal because the principal "*principal*" does not exist, this type of principal cannot be impersonated, or you do not have permission.</span></span>|  
  
## <a name="user-action"></a><span data-ttu-id="345d8-115">使用者動作</span><span class="sxs-lookup"><span data-stu-id="345d8-115">User Action</span></span>  
 <span data-ttu-id="345d8-116">使用現有主體的名稱，或取得該主體的 IMPERSONATE 權限。</span><span class="sxs-lookup"><span data-stu-id="345d8-116">Use the name of an existing principal or get the IMPERSONATE permission on that principal.</span></span>  
  
 <span data-ttu-id="345d8-117">15517 也可能在原始資料庫擁有者以外的人執行附加和還原資料庫之後發生。</span><span class="sxs-lookup"><span data-stu-id="345d8-117">15517 can also occur after performing an attach and restore of a database by someone other than the original database owner.</span></span> <span data-ttu-id="345d8-118">若要解決此錯誤，請執行下列命令將 db_owner 變更為伺服器上的登入：</span><span class="sxs-lookup"><span data-stu-id="345d8-118">To resolve this error, change the db_owner to a login on your server, by running the following command:</span></span>  
  
```  
ALTER AUTHORIZATION ON DATABASE:: DBName TO [NewLogin]  
```  
  
## <a name="see-also"></a><span data-ttu-id="345d8-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="345d8-119">See Also</span></span>  
 [<span data-ttu-id="345d8-120">記憶體內部 OLTP &#40;記憶體內部最佳化&#41;</span><span class="sxs-lookup"><span data-stu-id="345d8-120">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
