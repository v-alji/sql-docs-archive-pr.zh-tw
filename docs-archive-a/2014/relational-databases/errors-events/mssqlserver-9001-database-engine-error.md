---
title: MSSQLSERVER_9001 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 9001 (Database Engine error)
ms.assetid: a54de936-90c6-4845-aa96-29d32f154601
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0e61894d0d071fbdb36dcfb77895c46c61d0bbd1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704109"
---
# <a name="mssqlserver_9001"></a><span data-ttu-id="80793-102">MSSQLSERVER_9001</span><span class="sxs-lookup"><span data-stu-id="80793-102">MSSQLSERVER_9001</span></span>
    
## <a name="details"></a><span data-ttu-id="80793-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="80793-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="80793-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="80793-104">Product Name</span></span>|<span data-ttu-id="80793-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="80793-105">SQL Server</span></span>|  
|<span data-ttu-id="80793-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="80793-106">Event ID</span></span>|<span data-ttu-id="80793-107">9001</span><span class="sxs-lookup"><span data-stu-id="80793-107">9001</span></span>|  
|<span data-ttu-id="80793-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="80793-108">Event Source</span></span>|<span data-ttu-id="80793-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="80793-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="80793-110">元件</span><span class="sxs-lookup"><span data-stu-id="80793-110">Component</span></span>|<span data-ttu-id="80793-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="80793-111">SQLEngine</span></span>|  
|<span data-ttu-id="80793-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="80793-112">Symbolic Name</span></span>|<span data-ttu-id="80793-113">LOG_NOT_AVAIL</span><span class="sxs-lookup"><span data-stu-id="80793-113">LOG_NOT_AVAIL</span></span>|  
|<span data-ttu-id="80793-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="80793-114">Message Text</span></span>|<span data-ttu-id="80793-115">無法使用資料庫 '%.\*ls' 的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="80793-115">The log for database '%.\*ls' is not available.</span></span> <span data-ttu-id="80793-116">相關錯誤訊息請查閱事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="80793-116">Check the event log for related error messages.</span></span> <span data-ttu-id="80793-117">解決任何錯誤，並重新啟動資料庫。</span><span class="sxs-lookup"><span data-stu-id="80793-117">Resolve any errors and restart the database.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="80793-118">說明</span><span class="sxs-lookup"><span data-stu-id="80793-118">Explanation</span></span>  
 <span data-ttu-id="80793-119">資料庫記錄檔已離線。</span><span class="sxs-lookup"><span data-stu-id="80793-119">The database log was taken offline.</span></span> <span data-ttu-id="80793-120">通常這種情況表示需要重新啟動資料庫的重大錯誤。</span><span class="sxs-lookup"><span data-stu-id="80793-120">Usually this signifies a catastrophic failure that requires the database to restart.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="80793-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="80793-121">User Action</span></span>  
 <span data-ttu-id="80793-122">診斷其他錯誤並重新啟動 SQL Server 的執行個體 (如果它尚未自行重新啟動的話)。</span><span class="sxs-lookup"><span data-stu-id="80793-122">Diagnose other errors and restart the instance of SQL Server if it has not already restarted itself.</span></span>  
  
  
