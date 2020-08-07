---
title: MSSQLSERVER_1401 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1401 (Database Engine error)
ms.assetid: 02928770-aa63-4509-8713-406c73e4cedc
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 720263939e2f1685649fc41896e8ea10907d92ac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598964"
---
# <a name="mssqlserver_1401"></a><span data-ttu-id="ab784-102">MSSQLSERVER_1401</span><span class="sxs-lookup"><span data-stu-id="ab784-102">MSSQLSERVER_1401</span></span>
    
## <a name="details"></a><span data-ttu-id="ab784-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="ab784-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ab784-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="ab784-104">Product Name</span></span>|<span data-ttu-id="ab784-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="ab784-105">SQL Server</span></span>|  
|<span data-ttu-id="ab784-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="ab784-106">Event ID</span></span>|<span data-ttu-id="ab784-107">1401</span><span class="sxs-lookup"><span data-stu-id="ab784-107">1401</span></span>|  
|<span data-ttu-id="ab784-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="ab784-108">Event Source</span></span>|<span data-ttu-id="ab784-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="ab784-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="ab784-110">元件</span><span class="sxs-lookup"><span data-stu-id="ab784-110">Component</span></span>|<span data-ttu-id="ab784-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="ab784-111">SQLEngine</span></span>|  
|<span data-ttu-id="ab784-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="ab784-112">Symbolic Name</span></span>|<span data-ttu-id="ab784-113">DBM_MASTERSTARTUP</span><span class="sxs-lookup"><span data-stu-id="ab784-113">DBM_MASTERSTARTUP</span></span>|  
|<span data-ttu-id="ab784-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="ab784-114">Message Text</span></span>|<span data-ttu-id="ab784-115">資料庫鏡像主執行緒常式啟動失敗，原因如下: %ls。</span><span class="sxs-lookup"><span data-stu-id="ab784-115">Startup of the database-mirroring master thread routine failed for the following reason: %ls.</span></span> <span data-ttu-id="ab784-116">請更正錯誤的原因，然後重新啟動 SQL Server 服務。</span><span class="sxs-lookup"><span data-stu-id="ab784-116">Correct the cause of this error, and restart the SQL Server service.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ab784-117">說明</span><span class="sxs-lookup"><span data-stu-id="ab784-117">Explanation</span></span>  
 <span data-ttu-id="ab784-118">鏡像控制執行緒啟動失敗。</span><span class="sxs-lookup"><span data-stu-id="ab784-118">Startup of the mirroring control thread failed.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ab784-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="ab784-119">User Action</span></span>  
 <span data-ttu-id="ab784-120">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤記錄中，尋找在此訊息之前發生的相關錯誤。</span><span class="sxs-lookup"><span data-stu-id="ab784-120">In the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log, look for the associated error that preceded this message.</span></span> <span data-ttu-id="ab784-121">請更正錯誤的原因，然後重新啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務 (MSSQLSERVER)。</span><span class="sxs-lookup"><span data-stu-id="ab784-121">Correct the cause of this error, and then restart the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service (MSSQLSERVER).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab784-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ab784-122">See Also</span></span>  
 [<span data-ttu-id="ab784-123">啟動、停止、暫停、繼續、重新啟動 Database Engine、SQL Server Agent 或 SQL Server Browser 服務</span><span class="sxs-lookup"><span data-stu-id="ab784-123">Start, Stop, Pause, Resume, Restart the Database Engine, SQL Server Agent, or SQL Server Browser Service</span></span>](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md)  
  
  
