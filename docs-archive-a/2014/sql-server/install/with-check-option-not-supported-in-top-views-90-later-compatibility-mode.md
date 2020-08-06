---
title: 在90或更新版本的相容性模式中包含 TOP 的視圖中不支援 WITH CHECK OPTION |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- TOP clause
- WITH CHECK OPTION clause
ms.assetid: 1b9581d0-bad9-43e0-b8fc-f32d8a8a04ca
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: ee7775c875e33f104341a1da39f5fe6c9326f284
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595386"
---
# <a name="with-check-option-is-not-supported-in-views-that-contain-top-in-90-or-later-compatibility-modes"></a><span data-ttu-id="a04c6-102">在 90 或之後的相容性模式中，在包含 TOP 的檢視中不支援 WITH CHECK OPTION</span><span class="sxs-lookup"><span data-stu-id="a04c6-102">WITH CHECK OPTION is not supported in views that contain TOP in 90 or later compatibility modes</span></span>
  <span data-ttu-id="a04c6-103">Upgrade Advisor 偵測到有檢視在該檢視的 SELECT 陳述式中或它所參考的檢視中使用 WITH CHECK OPTION 和 TOP 子句。</span><span class="sxs-lookup"><span data-stu-id="a04c6-103">Upgrade Advisor detected a view that uses the WITH CHECK OPTION and a TOP clause in the SELECT statement of the view or in a referenced view.</span></span> <span data-ttu-id="a04c6-104">當資料庫相容性模式設定為 80 及之前的相容性模式時，以此方式定義的檢視會錯誤地允許資料透過檢視修改，而產生不正確的結果。</span><span class="sxs-lookup"><span data-stu-id="a04c6-104">Views defined this way incorrectly allow data to be modified through the view and may produce inaccurate results when the database compatibility mode is set to 80 and earlier.</span></span> <span data-ttu-id="a04c6-105">當檢視或它所參考的檢視使用 TOP 子句，而且資料庫相容性模式設定為 90 或之後的相容性模式時，資料無法透過使用 WITH CHECK OPTION 的檢視進行插入或更新。</span><span class="sxs-lookup"><span data-stu-id="a04c6-105">Data cannot be inserted or updated through a view that uses WITH CHECK OPTION when the view or a referenced view uses the TOP clause and the database compatibility mode is set to 90 or later.</span></span>  
  
## <a name="component"></a><span data-ttu-id="a04c6-106">元件</span><span class="sxs-lookup"><span data-stu-id="a04c6-106">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a><span data-ttu-id="a04c6-107">更正動作</span><span class="sxs-lookup"><span data-stu-id="a04c6-107">Corrective Action</span></span>  
 <span data-ttu-id="a04c6-108">當您升級時，使用者資料庫會維持其相容性模式。</span><span class="sxs-lookup"><span data-stu-id="a04c6-108">When you upgrade, user databases maintain their compatibility mode.</span></span> <span data-ttu-id="a04c6-109">在您將資料庫相容性模式變更為 100 或之後以前，如果需要透過檢視進行資料修改，請修改使用 WITH CHECK OPTION 和 TOP 的檢視。</span><span class="sxs-lookup"><span data-stu-id="a04c6-109">Before you change the database compatibility mode to 100 or later, modify views that use both WITH CHECK OPTION and TOP if data modification through the view is required.</span></span> <span data-ttu-id="a04c6-110">如需詳細資訊，請參閱[sp_dbcmptlevel &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-dbcmptlevel-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="a04c6-110">For more information, see [sp_dbcmptlevel &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dbcmptlevel-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a04c6-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a04c6-111">See Also</span></span>  
 <span data-ttu-id="a04c6-112">[資料庫引擎升級問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="a04c6-112">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="a04c6-113">SQL Server 2014 Upgrade Advisor &#91;新的&#93;</span><span class="sxs-lookup"><span data-stu-id="a04c6-113">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
