---
title: 90或更新版本相容性模式中的 views 不允許使用 FOR BROWSE |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- views [SQL Server], FOR BROWSE clause
- FOR BROWSE clause
ms.assetid: 8f49b1c1-d877-4c46-b988-f8cdd8ac0925
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 251e0ae2ff6f19dfcff3b0f8056f6697c1bfc40d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598177"
---
# <a name="for-browse-is-not-allowed-in-views-in-90-or-later-compatibility-modes"></a><span data-ttu-id="9be58-102">在 90 或 90 之後的相容性模式中，檢視內不允許有 FOR BROWSE</span><span class="sxs-lookup"><span data-stu-id="9be58-102">FOR BROWSE is not allowed in views in 90 or later compatibility modes</span></span>
  <span data-ttu-id="9be58-103">Upgrade Advisor 偵測到在檢視中使用 FOR BROWSE 子句。</span><span class="sxs-lookup"><span data-stu-id="9be58-103">Upgrade Advisor detected the use of the FOR BROWSE clause in a view.</span></span> <span data-ttu-id="9be58-104">當資料庫相容性模式設定為 80 時，檢視中允許有 FOR BROWSE 子句 (並且會忽略)。</span><span class="sxs-lookup"><span data-stu-id="9be58-104">The FOR BROWSE clause is allowed (and ignored) in views when the database compatibility mode is set to 80.</span></span> <span data-ttu-id="9be58-105">當資料庫相容性模式設定為 90 或之後時，檢視中就不允許有 FOR BROWSE 子句。</span><span class="sxs-lookup"><span data-stu-id="9be58-105">The FOR BROWSE clause is not allowed in views when the database compatibility mode is set to 90 or later.</span></span>  
  
## <a name="component"></a><span data-ttu-id="9be58-106">元件</span><span class="sxs-lookup"><span data-stu-id="9be58-106">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a><span data-ttu-id="9be58-107">更正動作</span><span class="sxs-lookup"><span data-stu-id="9be58-107">Corrective Action</span></span>  
 <span data-ttu-id="9be58-108">當您升級時，使用者資料庫會維持其相容性模式。</span><span class="sxs-lookup"><span data-stu-id="9be58-108">When you upgrade, user databases maintain their compatibility mode.</span></span> <span data-ttu-id="9be58-109">將資料庫相容性模式變更為 90 或之後以前，請從檢視定義中移除 FOR BROWSE 子句。</span><span class="sxs-lookup"><span data-stu-id="9be58-109">Before you change the database compatibility mode to 90 or later, remove the FOR BROWSE clause from view definitions.</span></span> <span data-ttu-id="9be58-110">如需詳細資訊，請參閱《[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 線上叢書》中的＜sp_dbcmptlevel＞。</span><span class="sxs-lookup"><span data-stu-id="9be58-110">For more information, see "sp_dbcmptlevel" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9be58-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9be58-111">See Also</span></span>  
 <span data-ttu-id="9be58-112">[資料庫引擎升級問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="9be58-112">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="9be58-113">SQL Server 2014 Upgrade Advisor &#91;新的&#93;</span><span class="sxs-lookup"><span data-stu-id="9be58-113">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
