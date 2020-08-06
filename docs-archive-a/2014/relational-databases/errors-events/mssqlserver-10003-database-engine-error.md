---
title: MSSQLSERVER_10003 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10003 (Database Engine error)
ms.assetid: 9e2cb199-f077-4d88-8117-1b7550afc696
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8ea44fc9591602bfc8279924e10a1803d0d5a87a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585490"
---
# <a name="mssqlserver_10003"></a><span data-ttu-id="d907e-102">MSSQLSERVER_10003</span><span class="sxs-lookup"><span data-stu-id="d907e-102">MSSQLSERVER_10003</span></span>
    
## <a name="details"></a><span data-ttu-id="d907e-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="d907e-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d907e-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="d907e-104">Product Name</span></span>|<span data-ttu-id="d907e-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="d907e-105">SQL Server</span></span>|  
|<span data-ttu-id="d907e-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="d907e-106">Event ID</span></span>|<span data-ttu-id="d907e-107">10003</span><span class="sxs-lookup"><span data-stu-id="d907e-107">10003</span></span>|  
|<span data-ttu-id="d907e-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="d907e-108">Event Source</span></span>|<span data-ttu-id="d907e-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="d907e-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="d907e-110">元件</span><span class="sxs-lookup"><span data-stu-id="d907e-110">Component</span></span>|<span data-ttu-id="d907e-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="d907e-111">SQLEngine</span></span>|  
|<span data-ttu-id="d907e-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="d907e-112">Symbolic Name</span></span>|<span data-ttu-id="d907e-113">HR_E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="d907e-113">HR_E_OUTOFMEMORY</span></span>|  
|<span data-ttu-id="d907e-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="d907e-114">Message Text</span></span>|<span data-ttu-id="d907e-115">提供者已用完記憶體。</span><span class="sxs-lookup"><span data-stu-id="d907e-115">The provider ran out of memory.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d907e-116">說明</span><span class="sxs-lookup"><span data-stu-id="d907e-116">Explanation</span></span>  
 <span data-ttu-id="d907e-117">系統記憶體不足導致 OLE DB 提供者用完記憶體。</span><span class="sxs-lookup"><span data-stu-id="d907e-117">Low system memory has caused the OLE DB provider to run out of memory.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d907e-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="d907e-118">User Action</span></span>  
 <span data-ttu-id="d907e-119">重新啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="d907e-119">Restart the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="d907e-120">如果這樣做沒有用，請重新啟動電腦。</span><span class="sxs-lookup"><span data-stu-id="d907e-120">If that does not help, restart the computer.</span></span> <span data-ttu-id="d907e-121">如果持續發生此問題，請使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 來收集 OLE DB 追蹤事件，並提供這項資料給 OLE DB 提供者的產品支援部門。</span><span class="sxs-lookup"><span data-stu-id="d907e-121">If the problem persists, collect OLE DB trace events using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] and provide this data to product support for the OLE DB provider.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d907e-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d907e-122">See Also</span></span>  
 <span data-ttu-id="d907e-123">[SQL Server Profiler 範本和權限](../../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="d907e-123">[SQL Server Profiler Templates and Permissions](../../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md) </span></span>  
 [<span data-ttu-id="d907e-124">SQL Server Native Client &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="d907e-124">SQL Server Native Client &#40;OLE DB&#41;</span></span>](../native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
