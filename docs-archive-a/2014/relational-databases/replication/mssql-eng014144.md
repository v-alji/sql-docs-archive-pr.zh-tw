---
title: MSSQL_ENG014144 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014144 error
ms.assetid: fdc744d5-530e-48c4-9420-cca032fd482b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0d93f06a585bcc01c52438ff7b99bbd635532402
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584414"
---
# <a name="mssql_eng014144"></a><span data-ttu-id="9d2c1-102">MSSQL_ENG014144</span><span class="sxs-lookup"><span data-stu-id="9d2c1-102">MSSQL_ENG014144</span></span>
    
## <a name="message-details"></a><span data-ttu-id="9d2c1-103">訊息詳細資料</span><span class="sxs-lookup"><span data-stu-id="9d2c1-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9d2c1-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="9d2c1-104">Product Name</span></span>|<span data-ttu-id="9d2c1-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="9d2c1-105">SQL Server</span></span>|  
|<span data-ttu-id="9d2c1-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="9d2c1-106">Event ID</span></span>|<span data-ttu-id="9d2c1-107">14144</span><span class="sxs-lookup"><span data-stu-id="9d2c1-107">14144</span></span>|  
|<span data-ttu-id="9d2c1-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="9d2c1-108">Event Source</span></span>|<span data-ttu-id="9d2c1-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="9d2c1-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="9d2c1-110">元件</span><span class="sxs-lookup"><span data-stu-id="9d2c1-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="9d2c1-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="9d2c1-111">Symbolic Name</span></span>||  
|<span data-ttu-id="9d2c1-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="9d2c1-112">Message Text</span></span>|<span data-ttu-id="9d2c1-113">無法卸除訂閱者 '%s'。</span><span class="sxs-lookup"><span data-stu-id="9d2c1-113">Cannot drop Subscriber '%s'.</span></span> <span data-ttu-id="9d2c1-114">發行集資料庫 '%s' 中有其訂閱。</span><span class="sxs-lookup"><span data-stu-id="9d2c1-114">There are subscriptions for it in the publication database '%s'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="9d2c1-115">說明</span><span class="sxs-lookup"><span data-stu-id="9d2c1-115">Explanation</span></span>  
 <span data-ttu-id="9d2c1-116">如果存在為執行個體設定的使用中訂閱，則設定為「訂閱者」的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體將無法從「訂閱者」角色中移除。</span><span class="sxs-lookup"><span data-stu-id="9d2c1-116">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance that is configured as a Subscriber cannot be removed from the role of Subscriber while there are active subscriptions configured for the instance.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="9d2c1-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="9d2c1-117">User Action</span></span>  
 <span data-ttu-id="9d2c1-118">在嘗試變更 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的「訂閱者」狀態之前，請先卸除所有相關聯的訂閱。</span><span class="sxs-lookup"><span data-stu-id="9d2c1-118">Drop all associated subscriptions before attempting to change the Subscriber status of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance:</span></span>  
  
1.  <span data-ttu-id="9d2c1-119">在「發行者」端的發行集資料庫中執行 [sp_helpsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql) 以尋找訂閱。</span><span class="sxs-lookup"><span data-stu-id="9d2c1-119">Execute [sp_helpsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql) in the publication database at the Publisher to find subscriptions.</span></span>  
  
2.  <span data-ttu-id="9d2c1-120">在發行集資料庫中執行 [sp_dropsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql) 以卸除訂閱。</span><span class="sxs-lookup"><span data-stu-id="9d2c1-120">Execute [sp_dropsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql) in the publication database to drop subscriptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d2c1-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9d2c1-121">See Also</span></span>  
 <span data-ttu-id="9d2c1-122">[錯誤和事件參考 &#40;複寫&#41;](errors-and-events-reference-replication.md) </span><span class="sxs-lookup"><span data-stu-id="9d2c1-122">[Errors and Events Reference &#40;Replication&#41;](errors-and-events-reference-replication.md) </span></span>  
 [<span data-ttu-id="9d2c1-123">訂閱發行集</span><span class="sxs-lookup"><span data-stu-id="9d2c1-123">Subscribe to Publications</span></span>](subscribe-to-publications.md)  
  
  
