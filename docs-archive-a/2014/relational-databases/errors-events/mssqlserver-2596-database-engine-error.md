---
title: MSSQLSERVER_2596 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2596 (Database Engine error)
ms.assetid: 49ab892f-8ba3-4ba1-b562-ddf205019802
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 27b2ceed40274df4ba57c4d61a83fbc60b6a7f80
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596045"
---
# <a name="mssqlserver_2596"></a><span data-ttu-id="9d435-102">MSSQLSERVER_2596</span><span class="sxs-lookup"><span data-stu-id="9d435-102">MSSQLSERVER_2596</span></span>
    
## <a name="details"></a><span data-ttu-id="9d435-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="9d435-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9d435-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="9d435-104">Product Name</span></span>|<span data-ttu-id="9d435-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="9d435-105">SQL Server</span></span>|  
|<span data-ttu-id="9d435-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="9d435-106">Event ID</span></span>|<span data-ttu-id="9d435-107">2596</span><span class="sxs-lookup"><span data-stu-id="9d435-107">2596</span></span>|  
|<span data-ttu-id="9d435-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="9d435-108">Event Source</span></span>|<span data-ttu-id="9d435-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="9d435-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="9d435-110">元件</span><span class="sxs-lookup"><span data-stu-id="9d435-110">Component</span></span>|<span data-ttu-id="9d435-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="9d435-111">SQLEngine</span></span>|  
|<span data-ttu-id="9d435-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="9d435-112">Symbolic Name</span></span>|<span data-ttu-id="9d435-113">DBCC_DATABASE_IN_READ_ONLY_MODE</span><span class="sxs-lookup"><span data-stu-id="9d435-113">DBCC_DATABASE_IN_READ_ONLY_MODE</span></span>|  
|<span data-ttu-id="9d435-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="9d435-114">Message Text</span></span>|<span data-ttu-id="9d435-115">未處理修復陳述式。</span><span class="sxs-lookup"><span data-stu-id="9d435-115">The repair statement was not processed.</span></span> <span data-ttu-id="9d435-116">資料庫不可以是唯讀模式。</span><span class="sxs-lookup"><span data-stu-id="9d435-116">The database cannot be in read-only mode.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="9d435-117">說明</span><span class="sxs-lookup"><span data-stu-id="9d435-117">Explanation</span></span>  
 <span data-ttu-id="9d435-118">此訊息指出資料庫為唯讀模式。</span><span class="sxs-lookup"><span data-stu-id="9d435-118">This message indicates that the database is in read-only mode.</span></span> <span data-ttu-id="9d435-119">當資料庫處於唯讀模式時，便無法進行修復。</span><span class="sxs-lookup"><span data-stu-id="9d435-119">Repairs are not possible when a database is in read-only mode.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="9d435-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="9d435-120">User Action</span></span>  
 <span data-ttu-id="9d435-121">使用 ALTER DATABASE 將資料庫設定成讀取/寫入，然後重新執行 DBCC 命令。</span><span class="sxs-lookup"><span data-stu-id="9d435-121">Set the database to read-write by using ALTER DATABASE, and then re-run the DBCC command.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d435-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9d435-122">See Also</span></span>  
 [<span data-ttu-id="9d435-123">ALTER DATABASE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="9d435-123">ALTER DATABASE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql)  
  
  
