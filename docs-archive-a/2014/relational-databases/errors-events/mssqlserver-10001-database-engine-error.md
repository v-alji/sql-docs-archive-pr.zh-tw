---
title: MSSQLSERVER_10001 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10001 (Database Engine error)
ms.assetid: f8fd2d8d-a4af-4b6a-ba51-9123b7e4c9bf
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0542f6d52a4fd194c4b0ae5d1aad501f5e3b8c2d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704117"
---
# <a name="mssqlserver_10001"></a><span data-ttu-id="6acb2-102">MSSQLSERVER_10001</span><span class="sxs-lookup"><span data-stu-id="6acb2-102">MSSQLSERVER_10001</span></span>
    
## <a name="details"></a><span data-ttu-id="6acb2-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="6acb2-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6acb2-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="6acb2-104">Product Name</span></span>|<span data-ttu-id="6acb2-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="6acb2-105">SQL Server</span></span>|  
|<span data-ttu-id="6acb2-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="6acb2-106">Event ID</span></span>|<span data-ttu-id="6acb2-107">10001</span><span class="sxs-lookup"><span data-stu-id="6acb2-107">10001</span></span>|  
|<span data-ttu-id="6acb2-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="6acb2-108">Event Source</span></span>|<span data-ttu-id="6acb2-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="6acb2-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="6acb2-110">元件</span><span class="sxs-lookup"><span data-stu-id="6acb2-110">Component</span></span>|<span data-ttu-id="6acb2-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="6acb2-111">SQLEngine</span></span>|  
|<span data-ttu-id="6acb2-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="6acb2-112">Symbolic Name</span></span>|<span data-ttu-id="6acb2-113">HR_E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="6acb2-113">HR_E_UNEXPECTED</span></span>|  
|<span data-ttu-id="6acb2-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="6acb2-114">Message Text</span></span>|<span data-ttu-id="6acb2-115">提供者報告了未預期的重大錯誤。</span><span class="sxs-lookup"><span data-stu-id="6acb2-115">The provider reported an unexpected catastrophic failure.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="6acb2-116">說明</span><span class="sxs-lookup"><span data-stu-id="6acb2-116">Explanation</span></span>  
 <span data-ttu-id="6acb2-117">呼叫 OLE DB 提供者時，分散式查詢處理遇到了一般錯誤。</span><span class="sxs-lookup"><span data-stu-id="6acb2-117">Distributed query processing encountered a generic error while calling into the OLE DB provider.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="6acb2-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="6acb2-118">User Action</span></span>  
 <span data-ttu-id="6acb2-119">請使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 來收集 OLE DB 追蹤事件，並提供這項資料給 OLE DB 提供者的產品支援部門。</span><span class="sxs-lookup"><span data-stu-id="6acb2-119">Collect OLE DB trace events using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] and  provide this data to product support for the OLE DB provider.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6acb2-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6acb2-120">See Also</span></span>  
 <span data-ttu-id="6acb2-121">[SQL Server Profiler 範本和權限](../../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="6acb2-121">[SQL Server Profiler Templates and Permissions](../../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md) </span></span>  
 [<span data-ttu-id="6acb2-122">SQL Server Native Client &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="6acb2-122">SQL Server Native Client &#40;OLE DB&#41;</span></span>](../native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
