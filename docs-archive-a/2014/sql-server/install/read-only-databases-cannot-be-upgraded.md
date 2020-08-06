---
title: 無法升級唯讀資料庫 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- database cannot be upgraded
ms.assetid: 27964211-ea30-4390-b791-dcf225fb9ae7
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: ba48ed2bd80961a4949dc13f04fed0637ecc27ec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598704"
---
# <a name="read-only-databases-cannot-be-upgraded"></a><span data-ttu-id="c6bb2-102">無法升級唯讀資料庫</span><span class="sxs-lookup"><span data-stu-id="c6bb2-102">Read-only databases cannot be upgraded</span></span>
  <span data-ttu-id="c6bb2-103">Upgrade Advisor 已確定此 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體上的某些資料庫無法升級。</span><span class="sxs-lookup"><span data-stu-id="c6bb2-103">Upgrade Advisor has determined that some databases on this instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cannot be upgraded.</span></span>  
  
## <a name="component"></a><span data-ttu-id="c6bb2-104">元件</span><span class="sxs-lookup"><span data-stu-id="c6bb2-104">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="c6bb2-105">描述</span><span class="sxs-lookup"><span data-stu-id="c6bb2-105">Description</span></span>  
 <span data-ttu-id="c6bb2-106">已偵測到唯讀資料庫。</span><span class="sxs-lookup"><span data-stu-id="c6bb2-106">A read-only database has been detected.</span></span> <span data-ttu-id="c6bb2-107">若要升級資料庫，安裝程式必須可以寫入資料庫。</span><span class="sxs-lookup"><span data-stu-id="c6bb2-107">To upgrade the database, Setup must be able to write to the database.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="c6bb2-108">更正動作</span><span class="sxs-lookup"><span data-stu-id="c6bb2-108">Corrective Action</span></span>  
 <span data-ttu-id="c6bb2-109">如果沒有人正在使用資料庫，請使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise Manager、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 或 ALTER database 語句，將資料庫變更為讀寫。</span><span class="sxs-lookup"><span data-stu-id="c6bb2-109">When no one is using the database, use the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise Manager, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], or the ALTER DATABASE statement to change the database to read-write.</span></span> <span data-ttu-id="c6bb2-110">下列陳述式會將資料庫變更為可讀寫。</span><span class="sxs-lookup"><span data-stu-id="c6bb2-110">The following statement changes the database to read-write.</span></span>  
  
```  
USE master;  
GO  
ALTER DATABASE <database name>  
SET READ_WRITE;  
GO  
```  
  
 <span data-ttu-id="c6bb2-111">如需有關 ALTER DATABASE 陳述式的詳細資訊，請參閱《[!INCLUDE[tsql](../../includes/tsql-md.md)] 線上叢書》中的＜ALTER DATABASE ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)])＞主題。</span><span class="sxs-lookup"><span data-stu-id="c6bb2-111">For more information about the ALTER DATABASE statement, see the "ALTER DATABASE ([!INCLUDE[tsql](../../includes/tsql-md.md)])" topic in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6bb2-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c6bb2-112">See Also</span></span>  
 <span data-ttu-id="c6bb2-113">[資料庫引擎升級問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="c6bb2-113">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="c6bb2-114">SQL Server 2014 Upgrade Advisor &#91;新的&#93;</span><span class="sxs-lookup"><span data-stu-id="c6bb2-114">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
