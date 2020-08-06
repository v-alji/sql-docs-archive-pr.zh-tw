---
title: 在80相容性模式中，會忽略索引視圖定義中的資料表提示，而且在90模式或更新版本中不允許使用 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- query hints [SQL Server]
- indexed views [SQL Server], query hints
ms.assetid: 405dfcff-a3a6-4e6d-a53a-ed77bbacdd13
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: cf3cb2b06dc477d93c8fd42312b4835ded42afb4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704674"
---
# <a name="table-hints-in-indexed-view-definitions-are-ignored-in-80-compatibility-mode-and-are-not-allowed-in-90-mode-or-later"></a><span data-ttu-id="cbcc5-102">在 80 相容性模式中，將忽略索引檢視定義中的資料表提示，而在 90 或之後的模式中則不允許</span><span class="sxs-lookup"><span data-stu-id="cbcc5-102">Table hints in indexed view definitions are ignored in 80 compatibility mode and are not allowed in 90 mode or later</span></span>
  <span data-ttu-id="cbcc5-103">在 90 或之後的相容性模式中，不允許在索引檢視的定義中使用資料表提示。</span><span class="sxs-lookup"><span data-stu-id="cbcc5-103">Table hints in the definitions of indexed views are not permitted in the compatibility mode of 90 or later.</span></span> <span data-ttu-id="cbcc5-104">如需詳細資訊，請參閱《[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 線上叢書》中的下列主題：＜設計索引檢視＞、＜建立索引檢視＞和＜查詢提示 ([!INCLUDE[tsql](../../includes/tsql-md.md)])＞。</span><span class="sxs-lookup"><span data-stu-id="cbcc5-104">For more information, see the following topics in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online: "Designing Indexed Views," "Creating Indexed Views," and "Query Hint ([!INCLUDE[tsql](../../includes/tsql-md.md)])."</span></span>  
  
## <a name="component"></a><span data-ttu-id="cbcc5-105">元件</span><span class="sxs-lookup"><span data-stu-id="cbcc5-105">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a><span data-ttu-id="cbcc5-106">更正動作</span><span class="sxs-lookup"><span data-stu-id="cbcc5-106">Corrective Action</span></span>  
 <span data-ttu-id="cbcc5-107">您必須將資料表提示從索引檢視的定義中移除。</span><span class="sxs-lookup"><span data-stu-id="cbcc5-107">Table hints must be removed from the definitions of indexed views.</span></span> <span data-ttu-id="cbcc5-108">不論使用的相容性模式為何，我們都建議您測試應用程式。</span><span class="sxs-lookup"><span data-stu-id="cbcc5-108">Regardless of which compatibility mode is used, we recommend that you test the application.</span></span> <span data-ttu-id="cbcc5-109">透過測試應用程式，您可以確保在建立、更新和存取索引檢視時 (包括索引檢視與查詢相符時)，應用程式會如預期方式執行。</span><span class="sxs-lookup"><span data-stu-id="cbcc5-109">By testing the application, you can make sure it performs as expected when indexed views are created, updated, and accessed, including when indexed views are matched to queries.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbcc5-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cbcc5-110">See Also</span></span>  
 <span data-ttu-id="cbcc5-111">[資料庫引擎升級問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="cbcc5-111">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="cbcc5-112">SQL Server 2014 Upgrade Advisor &#91;新的&#93;</span><span class="sxs-lookup"><span data-stu-id="cbcc5-112">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
