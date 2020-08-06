---
title: MSSQLSERVER_2527 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2527 (Database Engine error)
ms.assetid: 1cef90ef-9c39-44e6-bc7f-316c8f53c10c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 900707634a016ecfd29f9f676e68b4d2f557ccea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594087"
---
# <a name="mssqlserver_2527"></a><span data-ttu-id="0c7c6-102">MSSQLSERVER_2527</span><span class="sxs-lookup"><span data-stu-id="0c7c6-102">MSSQLSERVER_2527</span></span>
    
## <a name="details"></a><span data-ttu-id="0c7c6-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="0c7c6-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0c7c6-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="0c7c6-104">Product Name</span></span>|<span data-ttu-id="0c7c6-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="0c7c6-105">SQL Server</span></span>|  
|<span data-ttu-id="0c7c6-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="0c7c6-106">Event ID</span></span>|<span data-ttu-id="0c7c6-107">2527</span><span class="sxs-lookup"><span data-stu-id="0c7c6-107">2527</span></span>|  
|<span data-ttu-id="0c7c6-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="0c7c6-108">Event Source</span></span>|<span data-ttu-id="0c7c6-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="0c7c6-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="0c7c6-110">元件</span><span class="sxs-lookup"><span data-stu-id="0c7c6-110">Component</span></span>|<span data-ttu-id="0c7c6-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="0c7c6-111">SQLEngine</span></span>|  
|<span data-ttu-id="0c7c6-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="0c7c6-112">Symbolic Name</span></span>|<span data-ttu-id="0c7c6-113">DBCC_INDEX_FILEGROUP_IS_OFFLINE</span><span class="sxs-lookup"><span data-stu-id="0c7c6-113">DBCC_INDEX_FILEGROUP_IS_OFFLINE</span></span>|  
|<span data-ttu-id="0c7c6-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="0c7c6-114">Message Text</span></span>|<span data-ttu-id="0c7c6-115">無法處理資料表 O_NAME 的索引 I_NAME，因為檔案群組 F_NAME 已離線。</span><span class="sxs-lookup"><span data-stu-id="0c7c6-115">Unable to process index I_NAME of table O_NAME because filegroup F_NAME is offline.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="0c7c6-116">說明</span><span class="sxs-lookup"><span data-stu-id="0c7c6-116">Explanation</span></span>  
 <span data-ttu-id="0c7c6-117">這項參考用訊息指出由於儲存索引資料的其中一個檔案群組已離線，因此無法檢查索引。</span><span class="sxs-lookup"><span data-stu-id="0c7c6-117">This informational message indicates that the index cannot be checked because one of the filegroups that stores data for the index is offline.</span></span> <span data-ttu-id="0c7c6-118">檔案群組中的檔案狀態將決定整個檔案群組的可用性。</span><span class="sxs-lookup"><span data-stu-id="0c7c6-118">The state of the files in a filegroup determines the availability of the whole filegroup.</span></span> <span data-ttu-id="0c7c6-119">若要使某個檔案群組為可用的，則在檔案群組中的所有檔案必須都在線上。</span><span class="sxs-lookup"><span data-stu-id="0c7c6-119">For a filegroup to be available, all files within the filegroup must be online.</span></span> <span data-ttu-id="0c7c6-120">如果沒有其他問題，將會檢查相同物件的所有其他索引。</span><span class="sxs-lookup"><span data-stu-id="0c7c6-120">If there are no other problems, all other indexes of the same object will be checked.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="0c7c6-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="0c7c6-121">User Action</span></span>  
 <span data-ttu-id="0c7c6-122">若要針對指定的檔案群組檢查檔案的狀態，請查詢 **sys.database_files** 或 **sys.master_files** 目錄檢視。</span><span class="sxs-lookup"><span data-stu-id="0c7c6-122">To view the state of the files for the specified filegroup, query either the **sys.database_files** or **sys.master_files** catalog view.</span></span>  
  
 <span data-ttu-id="0c7c6-123">從備份還原離線檔案。</span><span class="sxs-lookup"><span data-stu-id="0c7c6-123">Restore the offline file from a backup.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c7c6-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0c7c6-124">See Also</span></span>  
 <span data-ttu-id="0c7c6-125">[sys.database_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0c7c6-125">[sys.database_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql) </span></span>  
 <span data-ttu-id="0c7c6-126">[master_files &#40;Transact-sql&#41;](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0c7c6-126">[sys.master_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql) </span></span>  
 [<span data-ttu-id="0c7c6-127">RESTORE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="0c7c6-127">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
