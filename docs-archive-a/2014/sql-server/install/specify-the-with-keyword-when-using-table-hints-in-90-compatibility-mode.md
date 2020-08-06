---
title: 在90相容性模式中使用資料表提示時，請指定 WITH 關鍵字 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- WITH keyword
- table hints [SQL Server]
ms.assetid: 7636cc85-5155-44db-baf6-df807761adb8
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 0ecd13475395cef4257d97eb7480f32420932e22
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595449"
---
# <a name="specify-the-with-keyword-when-using-table-hints-in-90-compatibility-mode"></a><span data-ttu-id="b7e6a-102">在 90 相容性模式中，使用資料表提示時，請指定 WITH 關鍵字</span><span class="sxs-lookup"><span data-stu-id="b7e6a-102">Specify the WITH keyword when using table hints in 90 compatibility mode</span></span>
  <span data-ttu-id="b7e6a-103">唯有利用 WITH 關鍵字指定提示時，查詢的 FROM 子句中才支援資料表提示，但有些例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b7e6a-103">With some exceptions, table hints are supported in the FROM clause of a query only when the hints are specified by using the WITH keyword.</span></span> <span data-ttu-id="b7e6a-104">如需詳細資訊，請參閱《[!INCLUDE[tsql](../../includes/tsql-md.md)] 線上叢書》中的＜FROM ([!INCLUDE[tsql](../../includes/tsql-md.md)])＞和＜資料表提示 ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)])＞主題。</span><span class="sxs-lookup"><span data-stu-id="b7e6a-104">For more information, see the topics "FROM ([!INCLUDE[tsql](../../includes/tsql-md.md)])" and "Table Hint ([!INCLUDE[tsql](../../includes/tsql-md.md)])" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="component"></a><span data-ttu-id="b7e6a-105">元件</span><span class="sxs-lookup"><span data-stu-id="b7e6a-105">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a><span data-ttu-id="b7e6a-106">更正動作</span><span class="sxs-lookup"><span data-stu-id="b7e6a-106">Corrective Action</span></span>  
 <span data-ttu-id="b7e6a-107">透過在資料表提示前加入 WITH 關鍵字，修改 FROM 子句中包含資料表提示的查詢。</span><span class="sxs-lookup"><span data-stu-id="b7e6a-107">Modify queries that include table hints in the FROM clause by including the WITH keyword before the table hints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7e6a-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b7e6a-108">See Also</span></span>  
 <span data-ttu-id="b7e6a-109">[資料庫引擎升級問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="b7e6a-109">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="b7e6a-110">SQL Server 2014 Upgrade Advisor &#91;新的&#93;</span><span class="sxs-lookup"><span data-stu-id="b7e6a-110">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
