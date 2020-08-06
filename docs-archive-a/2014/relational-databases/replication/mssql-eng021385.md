---
title: MSSQL_ENG021385 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG021385 error
ms.assetid: a2c0444f-d97b-4760-8905-3574791c2e26
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b73d3216f07cb44d750a37149634258648f1bd48
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87697933"
---
# <a name="mssql_eng021385"></a><span data-ttu-id="45587-102">MSSQL_ENG021385</span><span class="sxs-lookup"><span data-stu-id="45587-102">MSSQL_ENG021385</span></span>
    
## <a name="message-details"></a><span data-ttu-id="45587-103">訊息詳細資料</span><span class="sxs-lookup"><span data-stu-id="45587-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="45587-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="45587-104">Product Name</span></span>|<span data-ttu-id="45587-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="45587-105">SQL Server</span></span>|  
|<span data-ttu-id="45587-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="45587-106">Event ID</span></span>|<span data-ttu-id="45587-107">21385</span><span class="sxs-lookup"><span data-stu-id="45587-107">21385</span></span>|  
|<span data-ttu-id="45587-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="45587-108">Event Source</span></span>|<span data-ttu-id="45587-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="45587-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="45587-110">元件</span><span class="sxs-lookup"><span data-stu-id="45587-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="45587-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="45587-111">Symbolic Name</span></span>||  
|<span data-ttu-id="45587-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="45587-112">Message Text</span></span>|<span data-ttu-id="45587-113">快照集無法處理發行集 '%s'。</span><span class="sxs-lookup"><span data-stu-id="45587-113">Snapshot failed to process publication '%s'.</span></span> <span data-ttu-id="45587-114">可能是由於有使用中的結構描述變更活動，或是正在加入新的發行項。</span><span class="sxs-lookup"><span data-stu-id="45587-114">Possibly due to active schema change activity or new articles being added.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="45587-115">說明</span><span class="sxs-lookup"><span data-stu-id="45587-115">Explanation</span></span>  
 <span data-ttu-id="45587-116">如果尚有對發行集資料庫的變更在進行 (包括新增或卸除發行項，以及在已發行物件上執行結構描述變更)，而此時便開始執行「快照集代理程式」，即會引發此錯誤。</span><span class="sxs-lookup"><span data-stu-id="45587-116">This error is raised if the Snapshot Agent starts running when there are ongoing changes to the publication database, including adding or dropping articles and performing schema changes on published objects.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="45587-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="45587-117">User Action</span></span>  
 <span data-ttu-id="45587-118">在對發行集資料庫的變更完成後，重新啟動「快照集代理程式」。</span><span class="sxs-lookup"><span data-stu-id="45587-118">Restart the Snapshot Agent after changes to the publication database are complete.</span></span> <span data-ttu-id="45587-119">如需詳細資訊，請參閱[啟動及停止複寫代理程式 &#40;SQL Server Management Studio&#41;](agents/start-and-stop-a-replication-agent-sql-server-management-studio.md) 與[複寫代理程式可執行檔概念](concepts/replication-agent-executables-concepts.md)。</span><span class="sxs-lookup"><span data-stu-id="45587-119">For more information, see [Start and Stop a Replication Agent &#40;SQL Server Management Studio&#41;](agents/start-and-stop-a-replication-agent-sql-server-management-studio.md) and [Replication Agent Executables Concepts](concepts/replication-agent-executables-concepts.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45587-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="45587-120">See Also</span></span>  
 [<span data-ttu-id="45587-121">錯誤和事件參考 &#40;複寫&#41;</span><span class="sxs-lookup"><span data-stu-id="45587-121">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
