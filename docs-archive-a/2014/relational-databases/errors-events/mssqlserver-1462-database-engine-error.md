---
title: MSSQLSERVER_1462 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1462 (Database Engine error)
ms.assetid: 680e9c1c-a9d6-4765-b601-956d0a83324c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 704b847bde2d7b4da9da91b4b24bfe2b9e2afa07
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598950"
---
# <a name="mssqlserver_1462"></a><span data-ttu-id="06228-102">MSSQLSERVER_1462</span><span class="sxs-lookup"><span data-stu-id="06228-102">MSSQLSERVER_1462</span></span>
    
## <a name="details"></a><span data-ttu-id="06228-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="06228-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="06228-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="06228-104">Product Name</span></span>|<span data-ttu-id="06228-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="06228-105">SQL Server</span></span>|  
|<span data-ttu-id="06228-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="06228-106">Event ID</span></span>|<span data-ttu-id="06228-107">1462</span><span class="sxs-lookup"><span data-stu-id="06228-107">1462</span></span>|  
|<span data-ttu-id="06228-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="06228-108">Event Source</span></span>|<span data-ttu-id="06228-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="06228-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="06228-110">元件</span><span class="sxs-lookup"><span data-stu-id="06228-110">Component</span></span>|<span data-ttu-id="06228-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="06228-111">SQLEngine</span></span>|  
|<span data-ttu-id="06228-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="06228-112">Symbolic Name</span></span>|<span data-ttu-id="06228-113">DBM_DISABLED_DUE_TO_FAILED_REDO</span><span class="sxs-lookup"><span data-stu-id="06228-113">DBM_DISABLED_DUE_TO_FAILED_REDO</span></span>|  
|<span data-ttu-id="06228-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="06228-114">Message Text</span></span>|<span data-ttu-id="06228-115">重做作業失敗，已停用資料庫鏡像。</span><span class="sxs-lookup"><span data-stu-id="06228-115">Database mirroring is disabled due to a failed redo operation.</span></span> <span data-ttu-id="06228-116">無法繼續。</span><span class="sxs-lookup"><span data-stu-id="06228-116">Unable to resume.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="06228-117">說明</span><span class="sxs-lookup"><span data-stu-id="06228-117">Explanation</span></span>  
 <span data-ttu-id="06228-118">資料庫鏡像無法在鏡像上重做記錄。</span><span class="sxs-lookup"><span data-stu-id="06228-118">Database mirroring failed to redo a log record on the mirror.</span></span>  
  
### <a name="possible-causes"></a><span data-ttu-id="06228-119">可能的原因</span><span class="sxs-lookup"><span data-stu-id="06228-119">Possible Causes</span></span>  
 <span data-ttu-id="06228-120">在主體資料庫上執行加入檔案作業成功，但接著在鏡像資料庫上執行卻失敗，最可能的原因是主體伺服器與鏡像伺服器上的檔案名稱或目錄結構不同的緣故。</span><span class="sxs-lookup"><span data-stu-id="06228-120">The most likely cause is that an add-file operation completed on the principal database but then failed on the mirror database because file names or directory structures differ on the principal server and mirror server.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="06228-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="06228-121">User Action</span></span>  
 <span data-ttu-id="06228-122">查詢 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤記錄檔，找出造成這個錯誤的原因。</span><span class="sxs-lookup"><span data-stu-id="06228-122">Look in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log for the cause of this error.</span></span> <span data-ttu-id="06228-123">嘗試解決失敗的原因，然後在資料庫上繼續執行鏡像。</span><span class="sxs-lookup"><span data-stu-id="06228-123">Try to resolve the cause and resume mirroring on the database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06228-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="06228-124">See Also</span></span>  
 [<span data-ttu-id="06228-125">疑難排解資料庫鏡像組態 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="06228-125">Troubleshoot Database Mirroring Configuration &#40;SQL Server&#41;</span></span>](../../database-engine/database-mirroring/troubleshoot-database-mirroring-configuration-sql-server.md)  
  
  
