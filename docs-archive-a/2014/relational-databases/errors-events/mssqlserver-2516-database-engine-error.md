---
title: MSSQLSERVER_2516 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2516 (Database Engine error)
ms.assetid: 79ed14b5-f53c-40c6-8334-8a083f732207
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6be0809b3560d94bb883cf3a4acfa3d2c484b8b9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687918"
---
# <a name="mssqlserver_2516"></a><span data-ttu-id="0aa6e-102">MSSQLSERVER_2516</span><span class="sxs-lookup"><span data-stu-id="0aa6e-102">MSSQLSERVER_2516</span></span>
    
## <a name="details"></a><span data-ttu-id="0aa6e-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="0aa6e-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0aa6e-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="0aa6e-104">Product Name</span></span>|<span data-ttu-id="0aa6e-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="0aa6e-105">SQL Server</span></span>|  
|<span data-ttu-id="0aa6e-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="0aa6e-106">Event ID</span></span>|<span data-ttu-id="0aa6e-107">2516</span><span class="sxs-lookup"><span data-stu-id="0aa6e-107">2516</span></span>|  
|<span data-ttu-id="0aa6e-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="0aa6e-108">Event Source</span></span>|<span data-ttu-id="0aa6e-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="0aa6e-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="0aa6e-110">元件</span><span class="sxs-lookup"><span data-stu-id="0aa6e-110">Component</span></span>|<span data-ttu-id="0aa6e-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="0aa6e-111">SQLEngine</span></span>|  
|<span data-ttu-id="0aa6e-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="0aa6e-112">Symbolic Name</span></span>|<span data-ttu-id="0aa6e-113">DBCC_REPAIR_DIFF_MAP_INVALIDATED</span><span class="sxs-lookup"><span data-stu-id="0aa6e-113">DBCC_REPAIR_DIFF_MAP_INVALIDATED</span></span>|  
|<span data-ttu-id="0aa6e-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="0aa6e-114">Message Text</span></span>|<span data-ttu-id="0aa6e-115">修復導致資料庫 NAME 的差異式點陣圖無效。</span><span class="sxs-lookup"><span data-stu-id="0aa6e-115">Repair has invalidated the differential bitmap for database NAME.</span></span> <span data-ttu-id="0aa6e-116">差異備份鏈已中斷。</span><span class="sxs-lookup"><span data-stu-id="0aa6e-116">The differential backup chain is broken.</span></span> <span data-ttu-id="0aa6e-117">您必須執行完整的資料庫備份，然後才能執行差異備份。</span><span class="sxs-lookup"><span data-stu-id="0aa6e-117">You must perform a full database backup before you can perform a differential backup.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="0aa6e-118">說明</span><span class="sxs-lookup"><span data-stu-id="0aa6e-118">Explanation</span></span>  
 <span data-ttu-id="0aa6e-119">在修復錯誤 MSSQLEngine_2515 時，會傳回這項參考用訊息。</span><span class="sxs-lookup"><span data-stu-id="0aa6e-119">This informational message is returned when error MSSQLEngine_2515 is repaired.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="0aa6e-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="0aa6e-120">User Action</span></span>  
 <span data-ttu-id="0aa6e-121">執行完整的資料庫備份。</span><span class="sxs-lookup"><span data-stu-id="0aa6e-121">Perform a full database backup.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0aa6e-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0aa6e-122">See Also</span></span>  
 [<span data-ttu-id="0aa6e-123">建立完整資料庫備份 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="0aa6e-123">Create a Full Database Backup &#40;SQL Server&#41;</span></span>](../backup-restore/create-a-full-database-backup-sql-server.md)  
  
  
