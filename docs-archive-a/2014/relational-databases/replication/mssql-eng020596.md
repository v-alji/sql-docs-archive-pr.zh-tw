---
title: MSSQL_ENG020596 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG020596 error
ms.assetid: fa33627c-2e99-4be3-9424-52ab83446e07
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8b1c61f3683442e0d474ff36a65c89446dbd7bd1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606784"
---
# <a name="mssql_eng020596"></a><span data-ttu-id="1ae15-102">MSSQL_ENG020596</span><span class="sxs-lookup"><span data-stu-id="1ae15-102">MSSQL_ENG020596</span></span>
    
## <a name="message-details"></a><span data-ttu-id="1ae15-103">訊息詳細資料</span><span class="sxs-lookup"><span data-stu-id="1ae15-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1ae15-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="1ae15-104">Product Name</span></span>|<span data-ttu-id="1ae15-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="1ae15-105">SQL Server</span></span>|  
|<span data-ttu-id="1ae15-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="1ae15-106">Event ID</span></span>|<span data-ttu-id="1ae15-107">20596</span><span class="sxs-lookup"><span data-stu-id="1ae15-107">20596</span></span>|  
|<span data-ttu-id="1ae15-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="1ae15-108">Event Source</span></span>|<span data-ttu-id="1ae15-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="1ae15-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="1ae15-110">元件</span><span class="sxs-lookup"><span data-stu-id="1ae15-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="1ae15-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="1ae15-111">Symbolic Name</span></span>||  
|<span data-ttu-id="1ae15-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="1ae15-112">Message Text</span></span>|<span data-ttu-id="1ae15-113">只有 '%s' 或 db_owner 的成員可以卸除匿名的代理程式。</span><span class="sxs-lookup"><span data-stu-id="1ae15-113">Only '%s' or members of db_owner can drop the anonymous agent.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="1ae15-114">說明</span><span class="sxs-lookup"><span data-stu-id="1ae15-114">Explanation</span></span>  
 <span data-ttu-id="1ae15-115">您沒有足夠的權限卸除匿名訂閱的代理程式。</span><span class="sxs-lookup"><span data-stu-id="1ae15-115">You do not have sufficient permissions to drop the agent for the anonymous subscription.</span></span> <span data-ttu-id="1ae15-116">呼叫 [sp_dropanonymousagent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropanonymousagent-transact-sql) 時使用的登入必須是「散發者」端 **sysadmin** 固定伺服器角色的成員、散發資料庫中的 **db_owner** 固定資料庫角色的成員，或者該使用者必須是第一次執行代理程式時初始化的使用者。</span><span class="sxs-lookup"><span data-stu-id="1ae15-116">The login used when calling [sp_dropanonymousagent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropanonymousagent-transact-sql) must be a member of the **sysadmin** fixed server role at the Distributor or **db_owner** fixed database role in the distribution database, or the user must be the one that initiated the first run of the agent.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="1ae15-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="1ae15-117">User Action</span></span>  
 <span data-ttu-id="1ae15-118">使用適當的認證登入，並執行 **sp_dropanonymousagent**。</span><span class="sxs-lookup"><span data-stu-id="1ae15-118">Login with the appropriate credentials, and execute **sp_dropanonymousagent**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ae15-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1ae15-119">See Also</span></span>  
 [<span data-ttu-id="1ae15-120">錯誤和事件參考 &#40;複寫&#41;</span><span class="sxs-lookup"><span data-stu-id="1ae15-120">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
