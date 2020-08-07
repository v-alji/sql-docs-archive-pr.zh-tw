---
title: 了解資料庫圖表擁有權 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.diagnostic.CannotOpenWithInvalidOwner
helpviewer_keywords:
- diagrams [SQL Server], ownership
- database diagrams [SQL Server], ownership
- owners [SQL Server], database diagrams
ms.assetid: 4a27a48e-c4ef-4017-82b8-0cac4d0bbcac
author: stevestein
ms.author: sstein
ms.openlocfilehash: 21d0f6f006328d8843bbbe12ee066a8564fb722a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703673"
---
# <a name="understand-database-diagram-ownership-visual-database-tools"></a><span data-ttu-id="d0eb5-102">了解資料庫圖表擁有權 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="d0eb5-102">Understand Database Diagram Ownership (Visual Database Tools)</span></span>
  <span data-ttu-id="d0eb5-103">若要使用資料庫圖表設計工具，必須先由 db_owner 角色 ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫的角色) 的成員進行設定，才能控制圖表的存取權。</span><span class="sxs-lookup"><span data-stu-id="d0eb5-103">To use Database Diagram Designer it must first be set up by a member of the db_owner role (a role of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases) to control access to diagrams.</span></span> <span data-ttu-id="d0eb5-104">每個圖表必定有一個，也只能有一個擁有者，也就是建立該圖表的使用者。</span><span class="sxs-lookup"><span data-stu-id="d0eb5-104">Each diagram has one and only one owner, the user who created it.</span></span> <span data-ttu-id="d0eb5-105">如需設定圖表化的詳細資訊，請參閱[設定資料庫關係圖設計工具 &#40;Visual Database Tools&#41;](visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="d0eb5-105">For more information on setting up diagramming see [Set Up Database Diagram Designer &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span>  
  
 <span data-ttu-id="d0eb5-106">圖表擁有權有下列幾點注意事項：</span><span class="sxs-lookup"><span data-stu-id="d0eb5-106">Some points to keep in mind about diagram ownership:</span></span>  
  
-   <span data-ttu-id="d0eb5-107">雖然任何有資料庫存取權的使用者都能建立圖表，但圖表建立後，則只有圖表的建立者及 db_owner 角色的任何成員可以檢視該圖表。</span><span class="sxs-lookup"><span data-stu-id="d0eb5-107">Although any user with access to a database can create a diagram, once the diagram has been created, the only users who can see it are the diagram's creator and any member of the db_owner role.</span></span>  
  
-   <span data-ttu-id="d0eb5-108">圖表的擁有權只能轉移給 db_owner 角色的成員。</span><span class="sxs-lookup"><span data-stu-id="d0eb5-108">Ownership of diagrams can only be transferred to members of the db_owner role.</span></span> <span data-ttu-id="d0eb5-109">只有在圖表的先前擁有者已從資料庫中移除時，才能轉移擁有權。</span><span class="sxs-lookup"><span data-stu-id="d0eb5-109">This is only possible if the previous owner of the diagram has been removed from the database.</span></span>  
  
-   <span data-ttu-id="d0eb5-110">如果圖表擁有人已從資料庫中移除，圖表將保留在資料庫中，直到 db_owner 角色的成員開啟為止。</span><span class="sxs-lookup"><span data-stu-id="d0eb5-110">If the owner of a diagram has been removed from the database, the diagram will remain in the database until a member of the db_owner role attempts to open it.</span></span> <span data-ttu-id="d0eb5-111">此時，db_owner 成員可選擇接管圖表的擁有權。</span><span class="sxs-lookup"><span data-stu-id="d0eb5-111">At that point the db_owner member can choose to take over ownership of the diagram.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0eb5-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d0eb5-112">See Also</span></span>  
 <span data-ttu-id="d0eb5-113">[使用資料庫關係圖 &#40;Visual Database Tools&#41;](work-with-database-diagrams-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="d0eb5-113">[Work with Database Diagrams &#40;Visual Database Tools&#41;](work-with-database-diagrams-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="d0eb5-114">設定資料庫圖表設計工具 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="d0eb5-114">Set Up Database Diagram Designer &#40;Visual Database Tools&#41;</span></span>](visual-database-tools.md)  
  
  
