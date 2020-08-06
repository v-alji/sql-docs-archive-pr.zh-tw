---
title: MSSQL_ENG014121 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014121 error
ms.assetid: c8595854-cce1-4566-ad64-d565555caded
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 04d4cbdd2197745d2d795814d88c4f7bc28eb90e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584419"
---
# <a name="mssql_eng014121"></a><span data-ttu-id="68979-102">MSSQL_ENG014121</span><span class="sxs-lookup"><span data-stu-id="68979-102">MSSQL_ENG014121</span></span>
    
## <a name="message-details"></a><span data-ttu-id="68979-103">訊息詳細資料</span><span class="sxs-lookup"><span data-stu-id="68979-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="68979-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="68979-104">Product Name</span></span>|<span data-ttu-id="68979-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="68979-105">SQL Server</span></span>|  
|<span data-ttu-id="68979-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="68979-106">Event ID</span></span>|<span data-ttu-id="68979-107">14121</span><span class="sxs-lookup"><span data-stu-id="68979-107">14121</span></span>|  
|<span data-ttu-id="68979-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="68979-108">Event Source</span></span>|<span data-ttu-id="68979-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="68979-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="68979-110">元件</span><span class="sxs-lookup"><span data-stu-id="68979-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="68979-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="68979-111">Symbolic Name</span></span>||  
|<span data-ttu-id="68979-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="68979-112">Message Text</span></span>|<span data-ttu-id="68979-113">無法卸除散發者 '%s'。</span><span class="sxs-lookup"><span data-stu-id="68979-113">Could not drop the Distributor '%s'.</span></span> <span data-ttu-id="68979-114">這個散發者有相關聯的散發資料庫。</span><span class="sxs-lookup"><span data-stu-id="68979-114">This Distributor has associated distribution databases.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="68979-115">說明</span><span class="sxs-lookup"><span data-stu-id="68979-115">Explanation</span></span>  
 <span data-ttu-id="68979-116">設定為「散發者」的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體不能從「散發者」的角色中移除，因為散發資料庫與此執行個體關聯。</span><span class="sxs-lookup"><span data-stu-id="68979-116">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance that is configured as a Distributor cannot be removed from the role of Distributor because there are distribution databases associated with the instance.</span></span> <span data-ttu-id="68979-117">若您嘗試卸除與一個或多個發行者相關聯的散發資料庫，就會發生這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="68979-117">This error occurs if you attempt to drop a distribution database that is associated with one or more Publishers.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="68979-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="68979-118">User Action</span></span>  
 <span data-ttu-id="68979-119">若要尋找已與此「散發者」建立關聯之任何「發行者」及散發資料庫的名稱，請從「散發者」的所有資料庫中執行 [sp_helpdistpublisher &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpdistpublisher-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="68979-119">To find the names of any Publishers and distribution databases associated with this Distributor, execute [sp_helpdistpublisher &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpdistpublisher-transact-sql) from any database on the Distributor.</span></span>  
  
 <span data-ttu-id="68979-120">針對已與此「散發者」建立關聯的所有散發資料庫，執行 [sp_dropdistributiondb &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropdistributiondb-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="68979-120">Execute [sp_dropdistributiondb &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropdistributiondb-transact-sql) for any distribution databases associated with this Distributor.</span></span> <span data-ttu-id="68979-121">在移除了所有散發資料庫關聯後，您可以停用散發。</span><span class="sxs-lookup"><span data-stu-id="68979-121">After all distribution database associations are removed, you can disable distribution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68979-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="68979-122">See Also</span></span>  
 <span data-ttu-id="68979-123">[錯誤和事件參考 &#40;複寫&#41;](errors-and-events-reference-replication.md) </span><span class="sxs-lookup"><span data-stu-id="68979-123">[Errors and Events Reference &#40;Replication&#41;](errors-and-events-reference-replication.md) </span></span>  
 [<span data-ttu-id="68979-124">設定散發</span><span class="sxs-lookup"><span data-stu-id="68979-124">Configure Distribution</span></span>](configure-distribution.md)  
  
  
