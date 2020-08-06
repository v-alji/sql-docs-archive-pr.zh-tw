---
title: MSSQLSERVER_17130 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 17130 (Database Engine error)
ms.assetid: 7ce6afca-221d-402f-89df-da7e74a339a8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b63be325273e4df33d837ec1548ed46701323977
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699703"
---
# <a name="mssqlserver_17130"></a><span data-ttu-id="fa459-102">MSSQLSERVER_17130</span><span class="sxs-lookup"><span data-stu-id="fa459-102">MSSQLSERVER_17130</span></span>
    
## <a name="details"></a><span data-ttu-id="fa459-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="fa459-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="fa459-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="fa459-104">Product Name</span></span>|<span data-ttu-id="fa459-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="fa459-105">SQL Server</span></span>|  
|<span data-ttu-id="fa459-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="fa459-106">Event ID</span></span>|<span data-ttu-id="fa459-107">17130</span><span class="sxs-lookup"><span data-stu-id="fa459-107">17130</span></span>|  
|<span data-ttu-id="fa459-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="fa459-108">Event Source</span></span>|<span data-ttu-id="fa459-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="fa459-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="fa459-110">元件</span><span class="sxs-lookup"><span data-stu-id="fa459-110">Component</span></span>|<span data-ttu-id="fa459-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="fa459-111">SQLEngine</span></span>|  
|<span data-ttu-id="fa459-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="fa459-112">Symbolic Name</span></span>|<span data-ttu-id="fa459-113">INIT_NOLOCKSPACE</span><span class="sxs-lookup"><span data-stu-id="fa459-113">INIT_NOLOCKSPACE</span></span>|  
|<span data-ttu-id="fa459-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="fa459-114">Message Text</span></span>|<span data-ttu-id="fa459-115">記憶體不足以供已設定的鎖定數目使用。</span><span class="sxs-lookup"><span data-stu-id="fa459-115">Not enough memory for the configured number of locks.</span></span> <span data-ttu-id="fa459-116">請嘗試使用較小的鎖定雜湊表來啟動，但是可能會影響到效能。</span><span class="sxs-lookup"><span data-stu-id="fa459-116">Attempting to start with a smaller lock hash table, which may impact performance.</span></span> <span data-ttu-id="fa459-117">請聯繫資料庫管理員為 Database Engine 的執行個體設定更多記憶體。</span><span class="sxs-lookup"><span data-stu-id="fa459-117">Contact the database administrator to configure more memory for this instance of the Database Engine.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="fa459-118">說明</span><span class="sxs-lookup"><span data-stu-id="fa459-118">Explanation</span></span>  
 <span data-ttu-id="fa459-119">記憶體不足以供所需的鎖定管理員雜湊表大小使用。</span><span class="sxs-lookup"><span data-stu-id="fa459-119">Not enough memory for the desired lock manager hash table size.</span></span>  <span data-ttu-id="fa459-120">系統將嘗試配置更小的雜湊表。</span><span class="sxs-lookup"><span data-stu-id="fa459-120">An attempt will be made to allocate a smaller hash table.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="fa459-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="fa459-121">User Action</span></span>  
 <span data-ttu-id="fa459-122">請檢查伺服器記憶體組態參數 (min/max server memory) 和記憶體不足的壓力。</span><span class="sxs-lookup"><span data-stu-id="fa459-122">Check server memory configuration parameters (min/max server memory), check for memory pressures.</span></span> <span data-ttu-id="fa459-123">提供 SQL Server 更多記憶體。</span><span class="sxs-lookup"><span data-stu-id="fa459-123">Provide SQL Server more memory.</span></span>  
  
  
