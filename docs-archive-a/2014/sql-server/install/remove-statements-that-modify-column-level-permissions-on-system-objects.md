---
title: 移除在系統物件上修改資料行層級許可權的語句 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- column-level permissions [SQL Server]
- removed statement permissions [SQL Server]
ms.assetid: 7f4fbbef-2696-4911-903b-63f6d9e4484a
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: e55af3dca0c55c2babd09bc6cfc48ed0ddf3ad7a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598152"
---
# <a name="remove-statements-that-modify-column-level-permissions-on-system-objects"></a><span data-ttu-id="af1a0-102">移除在系統物件上修改資料行層級權限的陳述式</span><span class="sxs-lookup"><span data-stu-id="af1a0-102">Remove statements that modify column-level permissions on system objects</span></span>
  <span data-ttu-id="af1a0-103">Upgrade Advisor 偵測到系統物件上有非標準的資料行層級權限。</span><span class="sxs-lookup"><span data-stu-id="af1a0-103">The Upgrade Advisor detected nonstandard column-level permissions on system objects.</span></span> <span data-ttu-id="af1a0-104">升級時，將無法保持這些權限的變更。</span><span class="sxs-lookup"><span data-stu-id="af1a0-104">These permission changes will not be maintained when you upgrade.</span></span> <span data-ttu-id="af1a0-105">此外，將不再支援系統物件上的資料行層級權限。</span><span class="sxs-lookup"><span data-stu-id="af1a0-105">Additionally, column-level permissions on system objects are no longer supported.</span></span> <span data-ttu-id="af1a0-106">請從設定系統物件之資料行層級權限的應用程式中移除陳述式。</span><span class="sxs-lookup"><span data-stu-id="af1a0-106">Remove statements from your applications that set column-level permissions on system objects.</span></span>  
  
## <a name="component"></a><span data-ttu-id="af1a0-107">元件</span><span class="sxs-lookup"><span data-stu-id="af1a0-107">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a><span data-ttu-id="af1a0-108">更正動作</span><span class="sxs-lookup"><span data-stu-id="af1a0-108">Corrective Action</span></span>  
 <span data-ttu-id="af1a0-109">請從授與、拒絕或撤銷系統物件之資料行層級權限的應用程式中移除陳述式。</span><span class="sxs-lookup"><span data-stu-id="af1a0-109">Remove statements from your application that grant, deny, or revoke column-level permissions on system objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af1a0-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="af1a0-110">See Also</span></span>  
 <span data-ttu-id="af1a0-111">[資料庫引擎升級問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="af1a0-111">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="af1a0-112">SQL Server 2014 Upgrade Advisor &#91;新的&#93;</span><span class="sxs-lookup"><span data-stu-id="af1a0-112">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
