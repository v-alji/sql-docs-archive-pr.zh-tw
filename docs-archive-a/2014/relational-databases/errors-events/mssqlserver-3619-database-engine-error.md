---
title: MSSQLSERVER_3619 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3619 (Database Engine error)
ms.assetid: 7d94f8d9-65ca-4fde-9c17-7b83e94a3779
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2328ee6366d47130a02c444bce65b7b655af7965
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598892"
---
# <a name="mssqlserver_3619"></a><span data-ttu-id="f0f48-102">MSSQLSERVER_3619</span><span class="sxs-lookup"><span data-stu-id="f0f48-102">MSSQLSERVER_3619</span></span>
    
## <a name="details"></a><span data-ttu-id="f0f48-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="f0f48-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f0f48-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="f0f48-104">Product Name</span></span>|<span data-ttu-id="f0f48-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="f0f48-105">SQL Server</span></span>|  
|<span data-ttu-id="f0f48-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="f0f48-106">Event ID</span></span>|<span data-ttu-id="f0f48-107">3619</span><span class="sxs-lookup"><span data-stu-id="f0f48-107">3619</span></span>|  
|<span data-ttu-id="f0f48-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="f0f48-108">Event Source</span></span>|<span data-ttu-id="f0f48-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="f0f48-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="f0f48-110">元件</span><span class="sxs-lookup"><span data-stu-id="f0f48-110">Component</span></span>|<span data-ttu-id="f0f48-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="f0f48-111">SQLEngine</span></span>|  
|<span data-ttu-id="f0f48-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="f0f48-112">Symbolic Name</span></span>|<span data-ttu-id="f0f48-113">SYS_NOLOG</span><span class="sxs-lookup"><span data-stu-id="f0f48-113">SYS_NOLOG</span></span>|  
|<span data-ttu-id="f0f48-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="f0f48-114">Message Text</span></span>|<span data-ttu-id="f0f48-115">無法在資料庫識別碼 %d 中寫入檢查點記錄，因為記錄空間不足。</span><span class="sxs-lookup"><span data-stu-id="f0f48-115">Could not write a checkpoint record in database ID %d because the log is out of space.</span></span> <span data-ttu-id="f0f48-116">請連絡資料庫管理員截斷記錄，或者配置更多的空間給資料庫記錄檔。</span><span class="sxs-lookup"><span data-stu-id="f0f48-116">Contact the database administrator to truncate the log or allocate more space to the database log files.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f0f48-117">說明</span><span class="sxs-lookup"><span data-stu-id="f0f48-117">Explanation</span></span>  
 <span data-ttu-id="f0f48-118">交易記錄磁碟空間不足。</span><span class="sxs-lookup"><span data-stu-id="f0f48-118">The transaction log is out of disk space.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f0f48-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="f0f48-119">User Action</span></span>  
 <span data-ttu-id="f0f48-120">截斷記錄以釋出部分空間，或配置更多空間給記錄檔。</span><span class="sxs-lookup"><span data-stu-id="f0f48-120">Truncate the log to release some space, or allocate more space to the log.</span></span> <span data-ttu-id="f0f48-121">如需詳細資訊，請參閱《SQL Server 線上叢書》中的＜寫滿交易記錄疑難排解 (錯誤 9002)＞。</span><span class="sxs-lookup"><span data-stu-id="f0f48-121">For more information see, "Troubleshooting a Full Transaction Log (Error 9002)" in SQL Server Books Online.</span></span>  
  
  
