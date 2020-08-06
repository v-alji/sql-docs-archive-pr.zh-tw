---
title: 移除保留關鍵字後面的冒號 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- reserved keywords
ms.assetid: 4f23f7e4-7b4d-4e19-86c9-7527bb8b107d
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: fc6882439338509a3c716129d9504f209ab1e555
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710173"
---
# <a name="remove-colon-following-reserved-keyword"></a><span data-ttu-id="4c1e1-102">移除保留關鍵字後面的冒號</span><span class="sxs-lookup"><span data-stu-id="4c1e1-102">Remove colon following reserved keyword</span></span>
  <span data-ttu-id="4c1e1-103">Upgrade Advisor 偵測到指令碼中的保留關鍵字後面有冒號 (:)。</span><span class="sxs-lookup"><span data-stu-id="4c1e1-103">The Upgrade Advisor detected a script that contains a colon (:) following a reserved keyword.</span></span> <span data-ttu-id="4c1e1-104">在舊版 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中，會忽略此語法且成功地執行該陳述式。</span><span class="sxs-lookup"><span data-stu-id="4c1e1-104">In earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], this syntax is ignored and the statements execute successfully.</span></span> <span data-ttu-id="4c1e1-105">現在，當資料庫相容性模式設定為 100 或之後時，此語法會導致陳述式失敗。</span><span class="sxs-lookup"><span data-stu-id="4c1e1-105">Now, this syntax causes the statement to fail when the database compatibility mode is set to 100 or later.</span></span>  
  
 <span data-ttu-id="4c1e1-106">使用者資料庫會維持其相容性模式。</span><span class="sxs-lookup"><span data-stu-id="4c1e1-106">User databases maintain their compatibility mode.</span></span>  
  
## <a name="component"></a><span data-ttu-id="4c1e1-107">元件</span><span class="sxs-lookup"><span data-stu-id="4c1e1-107">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a><span data-ttu-id="4c1e1-108">更正動作</span><span class="sxs-lookup"><span data-stu-id="4c1e1-108">Corrective Action</span></span>  
 <span data-ttu-id="4c1e1-109">在您將資料庫相容性模式變更為 100 或之後以前，請移除保留關鍵字後面的冒號，藉以修改指令碼。</span><span class="sxs-lookup"><span data-stu-id="4c1e1-109">Before you change the database compatibility mode to 100 or later, modify your scripts by removing colons that follow reserved keywords.</span></span> <span data-ttu-id="4c1e1-110">如需詳細資訊，請參閱《[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 線上叢書》中的＜sp_dbcmptlevel＞。</span><span class="sxs-lookup"><span data-stu-id="4c1e1-110">For more information, see "sp_dbcmptlevel" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c1e1-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4c1e1-111">See Also</span></span>  
 <span data-ttu-id="4c1e1-112">[資料庫引擎升級問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="4c1e1-112">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="4c1e1-113">SQL Server 2014 Upgrade Advisor &#91;新的&#93;</span><span class="sxs-lookup"><span data-stu-id="4c1e1-113">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
