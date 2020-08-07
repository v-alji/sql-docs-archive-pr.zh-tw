---
title: MSSQLSERVER_9002 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 9002 (Database Engine error)
ms.assetid: 2e50841f-2b99-45f4-aec5-aa4add70cbeb
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b40fe70db8849d09f9296a06cbeed65a9c71e5a5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597851"
---
# <a name="mssqlserver_9002"></a><span data-ttu-id="99cc4-102">MSSQLSERVER_9002</span><span class="sxs-lookup"><span data-stu-id="99cc4-102">MSSQLSERVER_9002</span></span>
    
## <a name="details"></a><span data-ttu-id="99cc4-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="99cc4-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="99cc4-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="99cc4-104">Product Name</span></span>|<span data-ttu-id="99cc4-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="99cc4-105">SQL Server</span></span>|  
|<span data-ttu-id="99cc4-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="99cc4-106">Event ID</span></span>|<span data-ttu-id="99cc4-107">9002</span><span class="sxs-lookup"><span data-stu-id="99cc4-107">9002</span></span>|  
|<span data-ttu-id="99cc4-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="99cc4-108">Event Source</span></span>|<span data-ttu-id="99cc4-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="99cc4-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="99cc4-110">元件</span><span class="sxs-lookup"><span data-stu-id="99cc4-110">Component</span></span>|<span data-ttu-id="99cc4-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="99cc4-111">SQLEngine</span></span>|  
|<span data-ttu-id="99cc4-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="99cc4-112">Symbolic Name</span></span>|<span data-ttu-id="99cc4-113">LOG_IS_FULL</span><span class="sxs-lookup"><span data-stu-id="99cc4-113">LOG_IS_FULL</span></span>|  
|<span data-ttu-id="99cc4-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="99cc4-114">Message Text</span></span>|<span data-ttu-id="99cc4-115">資料庫 '%.\*ls' 的交易記錄已滿。</span><span class="sxs-lookup"><span data-stu-id="99cc4-115">The transaction log for database '%.\*ls' is full.</span></span> <span data-ttu-id="99cc4-116">如果要了解為何無法重複使用記錄中的空間，請參閱 sys.databases 中的 log_reuse_wait_desc 資料行。</span><span class="sxs-lookup"><span data-stu-id="99cc4-116">To find out why space in the log cannot be reused, see the log_reuse_wait_desc column in sys.databases.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="99cc4-117">說明</span><span class="sxs-lookup"><span data-stu-id="99cc4-117">Explanation</span></span>  
 <span data-ttu-id="99cc4-118">資料庫記錄檔空間不足。</span><span class="sxs-lookup"><span data-stu-id="99cc4-118">The database log is out of space.</span></span> <span data-ttu-id="99cc4-119">**sys.databases** 中的 **log_reuse_wait_desc** 資料行描述為何無法重複使用記錄檔中的空間。</span><span class="sxs-lookup"><span data-stu-id="99cc4-119">The **log_reuse_wait_desc** column in **sys.databases** describes why space in the log cannot be reused.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="99cc4-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="99cc4-120">User Action</span></span>  
 <span data-ttu-id="99cc4-121">使用 **sys.databases** 確定記錄已滿的原因，然後更正該狀況。</span><span class="sxs-lookup"><span data-stu-id="99cc4-121">Use **sys.databases** to determine why the log is full and then correct the condition.</span></span> <span data-ttu-id="99cc4-122">如需詳細資訊，請參閱《SQL Server 線上叢書》中的＜寫滿交易記錄疑難排解 (錯誤 9002)＞。</span><span class="sxs-lookup"><span data-stu-id="99cc4-122">For more information, see "Troubleshooting a Full Transaction Log (Error 9002)" in SQL Server Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99cc4-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="99cc4-123">See Also</span></span>  
 <span data-ttu-id="99cc4-124">[針對完整交易記錄 &#40;SQL Server 錯誤 9002&#41; 進行疑難排解](../logs/troubleshoot-a-full-transaction-log-sql-server-error-9002.md) </span><span class="sxs-lookup"><span data-stu-id="99cc4-124">[Troubleshoot a Full Transaction Log &#40;SQL Server Error 9002&#41;](../logs/troubleshoot-a-full-transaction-log-sql-server-error-9002.md) </span></span>  
 [<span data-ttu-id="99cc4-125">sys.databases &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="99cc4-125">sys.databases &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)  
  
  
