---
title: MSSQLSERVER_8443 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 8443 (Database Engine error)
ms.assetid: a3541b9c-b1a8-4280-add1-275f08696b62
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ae02cc0d9e5661f4069884c22bf6eea0697bd2d7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704110"
---
# <a name="mssqlserver_8443"></a><span data-ttu-id="9e33e-102">MSSQLSERVER_8443</span><span class="sxs-lookup"><span data-stu-id="9e33e-102">MSSQLSERVER_8443</span></span>
    
## <a name="details"></a><span data-ttu-id="9e33e-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="9e33e-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9e33e-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="9e33e-104">Product Name</span></span>|<span data-ttu-id="9e33e-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="9e33e-105">SQL Server</span></span>|  
|<span data-ttu-id="9e33e-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="9e33e-106">Event ID</span></span>|<span data-ttu-id="9e33e-107">8443</span><span class="sxs-lookup"><span data-stu-id="9e33e-107">8443</span></span>|  
|<span data-ttu-id="9e33e-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="9e33e-108">Event Source</span></span>|<span data-ttu-id="9e33e-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="9e33e-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="9e33e-110">元件</span><span class="sxs-lookup"><span data-stu-id="9e33e-110">Component</span></span>|<span data-ttu-id="9e33e-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="9e33e-111">SQLEngine</span></span>|  
|<span data-ttu-id="9e33e-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="9e33e-112">Symbolic Name</span></span>|<span data-ttu-id="9e33e-113">SB_DIALOG_WO_CONV_GROUP</span><span class="sxs-lookup"><span data-stu-id="9e33e-113">SB_DIALOG_WO_CONV_GROUP</span></span>|  
|<span data-ttu-id="9e33e-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="9e33e-114">Message Text</span></span>|<span data-ttu-id="9e33e-115">具有識別碼 '%.\*ls' 和起始端 %d 的交談參考了遺漏的交談群組 '%.\*ls'。</span><span class="sxs-lookup"><span data-stu-id="9e33e-115">The conversation with ID '%.\*ls' and initiator %d references a missing conversation group '%.\*ls'.</span></span> <span data-ttu-id="9e33e-116">請執行 DBCC CHECKDB 來分析和修復資料庫。</span><span class="sxs-lookup"><span data-stu-id="9e33e-116">Run DBCC CHECKDB to analyze and repair the database.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="9e33e-117">說明</span><span class="sxs-lookup"><span data-stu-id="9e33e-117">Explanation</span></span>  
 <span data-ttu-id="9e33e-118">中繼資料層針對交談群組傳回 NULL。</span><span class="sxs-lookup"><span data-stu-id="9e33e-118">The metadata layer returned NULL for the conversation group.</span></span> <span data-ttu-id="9e33e-119">資料庫在某些方面發生損毀。</span><span class="sxs-lookup"><span data-stu-id="9e33e-119">The database has been corrupted in some way.</span></span> <span data-ttu-id="9e33e-120">其中一個可能的損毀來源是磁碟錯誤。</span><span class="sxs-lookup"><span data-stu-id="9e33e-120">One possible source of corruption is a disk error.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="9e33e-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="9e33e-121">User Action</span></span>  
 <span data-ttu-id="9e33e-122">以修復模式執行 DBCC CHECKDB，使資料庫回復到一致的狀態。</span><span class="sxs-lookup"><span data-stu-id="9e33e-122">Run DBCC CHECKDB in repair mode to bring the database back into a consistent state.</span></span> <span data-ttu-id="9e33e-123">此命令可能會在必要時刪除訊息，以還原一致性。</span><span class="sxs-lookup"><span data-stu-id="9e33e-123">It may delete messages if necessary to restore consistency.</span></span> <span data-ttu-id="9e33e-124">請查閲系統錯誤記錄檔，確定這項錯誤是否由於其他系統錯誤所造成。</span><span class="sxs-lookup"><span data-stu-id="9e33e-124">Investigate system error logs to see if this error was caused by another failure in the system.</span></span>  
  
  
