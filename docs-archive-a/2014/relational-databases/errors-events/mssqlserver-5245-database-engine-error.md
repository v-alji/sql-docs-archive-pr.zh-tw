---
title: MSSQLSERVER_5245 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 5245 (Database Engine error)
ms.assetid: 6005c9ec-ccdd-4def-9eb4-37cdb599ddb3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f98c831642580587552bf60c604d84c38fffca8c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598885"
---
# <a name="mssqlserver_5245"></a><span data-ttu-id="8d623-102">MSSQLSERVER_5245</span><span class="sxs-lookup"><span data-stu-id="8d623-102">MSSQLSERVER_5245</span></span>
    
## <a name="details"></a><span data-ttu-id="8d623-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="8d623-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8d623-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="8d623-104">Product Name</span></span>|<span data-ttu-id="8d623-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="8d623-105">SQL Server</span></span>|  
|<span data-ttu-id="8d623-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="8d623-106">Event ID</span></span>|<span data-ttu-id="8d623-107">5245</span><span class="sxs-lookup"><span data-stu-id="8d623-107">5245</span></span>|  
|<span data-ttu-id="8d623-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="8d623-108">Event Source</span></span>|<span data-ttu-id="8d623-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="8d623-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="8d623-110">元件</span><span class="sxs-lookup"><span data-stu-id="8d623-110">Component</span></span>|<span data-ttu-id="8d623-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="8d623-111">SQLEngine</span></span>|  
|<span data-ttu-id="8d623-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="8d623-112">Symbolic Name</span></span>|<span data-ttu-id="8d623-113">DBCC4_TABLE_LOCK_TIMEOUT_EXCEEDED</span><span class="sxs-lookup"><span data-stu-id="8d623-113">DBCC4_TABLE_LOCK_TIMEOUT_EXCEEDED</span></span>|  
|<span data-ttu-id="8d623-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="8d623-114">Message Text</span></span>|<span data-ttu-id="8d623-115">物件識別碼 O_ID (物件 'NAME')：DBCC 無法在此物件上取得鎖定，因為已超過鎖定要求逾時期間。</span><span class="sxs-lookup"><span data-stu-id="8d623-115">Object ID O_ID (object 'NAME'): DBCC could not obtain a lock on this object because the lock request time-out period was exceeded.</span></span> <span data-ttu-id="8d623-116">已經略過這個物件，不會處理。</span><span class="sxs-lookup"><span data-stu-id="8d623-116">This object has been skipped and will not be processed.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="8d623-117">說明</span><span class="sxs-lookup"><span data-stu-id="8d623-117">Explanation</span></span>  
 <span data-ttu-id="8d623-118">DBCC 等候指定物件的資料表鎖定時發生鎖定逾時。</span><span class="sxs-lookup"><span data-stu-id="8d623-118">A lock time-out occurred while DBCC was waiting on a table lock for the specified object.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="8d623-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="8d623-119">User Action</span></span>  
 <span data-ttu-id="8d623-120">重新執行 DBCC 命令。</span><span class="sxs-lookup"><span data-stu-id="8d623-120">Rerun the DBCC command.</span></span>  
  
  
