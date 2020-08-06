---
title: MSSQLSERVER_3181 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3181 (Database Engine error)
ms.assetid: e6d2e716-5263-477c-ad0e-7bcbfef4c1f3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f18509d9a18ba8be1f4e40c93bff5abfcae3d69c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596021"
---
# <a name="mssqlserver_3181"></a><span data-ttu-id="04af0-102">MSSQLSERVER_3181</span><span class="sxs-lookup"><span data-stu-id="04af0-102">MSSQLSERVER_3181</span></span>
    
## <a name="details"></a><span data-ttu-id="04af0-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="04af0-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="04af0-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="04af0-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="04af0-105">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="04af0-105">Event ID</span></span>|<span data-ttu-id="04af0-106">3181</span><span class="sxs-lookup"><span data-stu-id="04af0-106">3181</span></span>|  
|<span data-ttu-id="04af0-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="04af0-107">Event Source</span></span>|<span data-ttu-id="04af0-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="04af0-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="04af0-109">元件</span><span class="sxs-lookup"><span data-stu-id="04af0-109">Component</span></span>|<span data-ttu-id="04af0-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="04af0-110">SQLEngine</span></span>|  
|<span data-ttu-id="04af0-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="04af0-111">Symbolic Name</span></span>|<span data-ttu-id="04af0-112">LDDB_STORAGE_VERIFY</span><span class="sxs-lookup"><span data-stu-id="04af0-112">LDDB_STORAGE_VERIFY</span></span>|  
|<span data-ttu-id="04af0-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="04af0-113">Message Text</span></span>|<span data-ttu-id="04af0-114">嘗試還原這個備份可能會遭遇儲存空間的問題。</span><span class="sxs-lookup"><span data-stu-id="04af0-114">Attempting to restore this backup may encounter storage space problems.</span></span> <span data-ttu-id="04af0-115">後續的訊息將會提供詳細資料。</span><span class="sxs-lookup"><span data-stu-id="04af0-115">Subsequent messages will provide details.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="04af0-116">說明</span><span class="sxs-lookup"><span data-stu-id="04af0-116">Explanation</span></span>  
 <span data-ttu-id="04af0-117">RESTORE VERIFYONLY 陳述式會檢查資料庫還原所在磁碟的可用儲存空間。</span><span class="sxs-lookup"><span data-stu-id="04af0-117">The RESTORE VERIFYONLY statement checks the available storage space on the disk to which the database is to be restored.</span></span>  
  
### <a name="possible-causes"></a><span data-ttu-id="04af0-118">可能的原因</span><span class="sxs-lookup"><span data-stu-id="04af0-118">Possible Causes</span></span>  
 <span data-ttu-id="04af0-119">可用的磁碟空間可能不足，無法還原受檢查的備份。</span><span class="sxs-lookup"><span data-stu-id="04af0-119">The available disk space may be insufficient to restore the backup being verified.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="04af0-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="04af0-120">User Action</span></span>  
 <span data-ttu-id="04af0-121">請將備份還原到磁碟空間足夠的位置，或增加磁碟的可用空間。</span><span class="sxs-lookup"><span data-stu-id="04af0-121">Restore the backup to a location with sufficient disk space, or provide more space on the disk.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04af0-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="04af0-122">See Also</span></span>  
 <span data-ttu-id="04af0-123">[將資料庫還原到新位置 &#40;SQL Server&#41;](../backup-restore/restore-a-database-to-a-new-location-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="04af0-123">[Restore a Database to a New Location &#40;SQL Server&#41;](../backup-restore/restore-a-database-to-a-new-location-sql-server.md) </span></span>  
 <span data-ttu-id="04af0-124">[將檔案還原到新的位置 &#40;SQL Server&#41;](../backup-restore/restore-files-to-a-new-location-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="04af0-124">[Restore Files to a New Location &#40;SQL Server&#41;](../backup-restore/restore-files-to-a-new-location-sql-server.md) </span></span>  
 <span data-ttu-id="04af0-125">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="04af0-125">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 [<span data-ttu-id="04af0-126">RESTORE VERIFYONLY &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="04af0-126">RESTORE VERIFYONLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql)  
  
  
