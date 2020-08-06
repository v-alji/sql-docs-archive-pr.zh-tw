---
title: MSSQL_ENG014120 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014120 error
ms.assetid: 6b169a3b-30da-4981-b998-b52d61811572
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e7f3484d9344a203ca8c44fee6b79605163ea069
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584418"
---
# <a name="mssql_eng014120"></a><span data-ttu-id="34e00-102">MSSQL_ENG014120</span><span class="sxs-lookup"><span data-stu-id="34e00-102">MSSQL_ENG014120</span></span>
    
## <a name="message-details"></a><span data-ttu-id="34e00-103">訊息詳細資料</span><span class="sxs-lookup"><span data-stu-id="34e00-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="34e00-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="34e00-104">Product Name</span></span>|<span data-ttu-id="34e00-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="34e00-105">SQL Server</span></span>|  
|<span data-ttu-id="34e00-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="34e00-106">Event ID</span></span>|<span data-ttu-id="34e00-107">14120</span><span class="sxs-lookup"><span data-stu-id="34e00-107">14120</span></span>|  
|<span data-ttu-id="34e00-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="34e00-108">Event Source</span></span>|<span data-ttu-id="34e00-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="34e00-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="34e00-110">元件</span><span class="sxs-lookup"><span data-stu-id="34e00-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="34e00-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="34e00-111">Symbolic Name</span></span>||  
|<span data-ttu-id="34e00-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="34e00-112">Message Text</span></span>|<span data-ttu-id="34e00-113">無法卸除散發資料庫 '%s'。</span><span class="sxs-lookup"><span data-stu-id="34e00-113">Could not drop the distribution database '%s'.</span></span> <span data-ttu-id="34e00-114">這個散發資料庫與一發行者相關聯。</span><span class="sxs-lookup"><span data-stu-id="34e00-114">This distributor database is associated with a Publisher.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="34e00-115">說明</span><span class="sxs-lookup"><span data-stu-id="34e00-115">Explanation</span></span>  
 <span data-ttu-id="34e00-116">散發資料庫為異動複寫中所有類型的複寫與交易，儲存中繼資料和歷程資料。</span><span class="sxs-lookup"><span data-stu-id="34e00-116">The distribution database stores metadata and history data for all types of replication and transactions for transactional replication.</span></span> <span data-ttu-id="34e00-117">若您嘗試卸除與一個或多個發行者相關聯的散發資料庫，就會發生這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="34e00-117">This error occurs if you attempt to drop a distribution database that is associated with one or more Publishers.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="34e00-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="34e00-118">User Action</span></span>  
 <span data-ttu-id="34e00-119">若要卸除散發資料庫，您必須先卸除「散發者」與「發行者」之間的關聯。</span><span class="sxs-lookup"><span data-stu-id="34e00-119">To drop a distribution database you must first drop the association between the Distributor and the Publisher.</span></span> <span data-ttu-id="34e00-120">如需詳細資訊，請參閱 [sp_dropdistpublisher &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="34e00-120">For more information, see [sp_dropdistpublisher &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34e00-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="34e00-121">See Also</span></span>  
 <span data-ttu-id="34e00-122">[錯誤和事件參考 &#40;複寫&#41;](errors-and-events-reference-replication.md) </span><span class="sxs-lookup"><span data-stu-id="34e00-122">[Errors and Events Reference &#40;Replication&#41;](errors-and-events-reference-replication.md) </span></span>  
 [<span data-ttu-id="34e00-123">設定散發</span><span class="sxs-lookup"><span data-stu-id="34e00-123">Configure Distribution</span></span>](configure-distribution.md)  
  
  
