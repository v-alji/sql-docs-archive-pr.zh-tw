---
title: MSSQLSERVER_3417 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3417 (Database Engine error)
ms.assetid: 005829c8-cf57-4828-818a-bbe8ee2e00f0
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 680e5a4266c7d0d9aaacb7b3deb9525a002077e8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598900"
---
# <a name="mssqlserver_3417"></a><span data-ttu-id="21f8e-102">MSSQLSERVER_3417</span><span class="sxs-lookup"><span data-stu-id="21f8e-102">MSSQLSERVER_3417</span></span>
    
## <a name="details"></a><span data-ttu-id="21f8e-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="21f8e-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="21f8e-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="21f8e-104">Product Name</span></span>|<span data-ttu-id="21f8e-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="21f8e-105">SQL Server</span></span>|  
|<span data-ttu-id="21f8e-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="21f8e-106">Event ID</span></span>|<span data-ttu-id="21f8e-107">3417</span><span class="sxs-lookup"><span data-stu-id="21f8e-107">3417</span></span>|  
|<span data-ttu-id="21f8e-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="21f8e-108">Event Source</span></span>|<span data-ttu-id="21f8e-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="21f8e-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="21f8e-110">元件</span><span class="sxs-lookup"><span data-stu-id="21f8e-110">Component</span></span>|<span data-ttu-id="21f8e-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="21f8e-111">SQLEngine</span></span>|  
|<span data-ttu-id="21f8e-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="21f8e-112">Symbolic Name</span></span>|<span data-ttu-id="21f8e-113">REC_BADMASTER</span><span class="sxs-lookup"><span data-stu-id="21f8e-113">REC_BADMASTER</span></span>|  
|<span data-ttu-id="21f8e-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="21f8e-114">Message Text</span></span>|<span data-ttu-id="21f8e-115">無法復原 master 資料庫。</span><span class="sxs-lookup"><span data-stu-id="21f8e-115">Cannot recover the master database.</span></span> <span data-ttu-id="21f8e-116">SQL Server 無法執行。</span><span class="sxs-lookup"><span data-stu-id="21f8e-116">SQL Server is unable to run.</span></span> <span data-ttu-id="21f8e-117">Restore master from a full backup, repair it, or rebuild it.</span><span class="sxs-lookup"><span data-stu-id="21f8e-117">Restore master from a full backup, repair it, or rebuild it.</span></span> <span data-ttu-id="21f8e-118">如需有關如何重建 master 資料庫的詳細資訊，請參閱《SQL Server 線上叢書》。</span><span class="sxs-lookup"><span data-stu-id="21f8e-118">For more information about how to rebuild the master database, see SQL Server Books Online.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="21f8e-119">說明</span><span class="sxs-lookup"><span data-stu-id="21f8e-119">Explanation</span></span>  
 <span data-ttu-id="21f8e-120">SQL Server 無法啟動 **master** 資料庫。</span><span class="sxs-lookup"><span data-stu-id="21f8e-120">SQL Server cannot start the **master** database.</span></span> <span data-ttu-id="21f8e-121">如果無法讓 **master** 或 **tempdb** 上線，SQL Server 就無法執行。</span><span class="sxs-lookup"><span data-stu-id="21f8e-121">If the **master** or **tempdb** cannot be brought online, SQL Server cannot run.</span></span> <span data-ttu-id="21f8e-122">這項錯誤通常在其他錯誤之前發生。</span><span class="sxs-lookup"><span data-stu-id="21f8e-122">This error is usually preceded by other errors.</span></span> <span data-ttu-id="21f8e-123">請查閱錯誤記錄檔，找出根本的原因。</span><span class="sxs-lookup"><span data-stu-id="21f8e-123">Review error logs to find the root cause.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="21f8e-124">使用者動作</span><span class="sxs-lookup"><span data-stu-id="21f8e-124">User Action</span></span>  
 <span data-ttu-id="21f8e-125">還原資料庫備份或修復資料庫。</span><span class="sxs-lookup"><span data-stu-id="21f8e-125">Restore backup of the database or repair the database.</span></span>  
  
  
