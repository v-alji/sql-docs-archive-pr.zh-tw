---
title: 設定資料庫圖表設計工具 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.diagnostic.InstallSqlDiagramSupport
helpviewer_keywords:
- Database Diagram Designer
- database diagrams [SQL Server], Database Diagram Designer
- diagrams [SQL Server], Database Diagram Designer
ms.assetid: 927321ee-b459-4f5b-9719-4a7a95639143
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6d59fa2ed197a410de6b68e388e76d2bf21c334d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703678"
---
# <a name="set-up-database-diagram-designer-visual-database-tools"></a><span data-ttu-id="d8911-102">設定資料庫圖表設計工具 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="d8911-102">Set Up Database Diagram Designer (Visual Database Tools)</span></span>
  <span data-ttu-id="d8911-103">若要使用資料庫圖表設計工具，必須先由 **db_owner** 角色的成員進行設定，才能控制圖表的存取權。</span><span class="sxs-lookup"><span data-stu-id="d8911-103">To use Database Diagram Designer, it must first be set up by a member of the **db_owner** role to control access to diagrams.</span></span>  
  
### <a name="to-set-up-database-diagramming"></a><span data-ttu-id="d8911-104">設定資料庫圖表化</span><span class="sxs-lookup"><span data-stu-id="d8911-104">To set up database diagramming</span></span>  
  
1.  <span data-ttu-id="d8911-105">從 [物件總管] 中，展開資料庫節點。</span><span class="sxs-lookup"><span data-stu-id="d8911-105">From Object Explorer, expand a database node.</span></span>  
  
2.  <span data-ttu-id="d8911-106">在資料庫連接中展開 [資料庫圖表] 節點。</span><span class="sxs-lookup"><span data-stu-id="d8911-106">Expand the Database Diagrams node under the database connection.</span></span>  
  
3.  <span data-ttu-id="d8911-107">如果您要設定資料庫圖表化，可在提示出現時選取 [是]  。</span><span class="sxs-lookup"><span data-stu-id="d8911-107">Select **Yes** when prompted if you want to set up database diagramming.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d8911-108">這會在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫中建立資料庫圖表資料表、系統預存程序和系統函數。</span><span class="sxs-lookup"><span data-stu-id="d8911-108">This will create the database diagram table, system stored procedures, and a system function on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span>  
  
4.  <span data-ttu-id="d8911-109">Visual Studio 會在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體上建立下列物件：</span><span class="sxs-lookup"><span data-stu-id="d8911-109">Visual Studio will create the following objects on the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
    1.  <span data-ttu-id="d8911-110">sysdiagrams 資料表</span><span class="sxs-lookup"><span data-stu-id="d8911-110">sysdiagrams table</span></span>  
  
    2.  <span data-ttu-id="d8911-111">sp_alterdiagram 預存程序</span><span class="sxs-lookup"><span data-stu-id="d8911-111">sp_alterdiagram stored procedure</span></span>  
  
    3.  <span data-ttu-id="d8911-112">sp_creatediagram 預存程序</span><span class="sxs-lookup"><span data-stu-id="d8911-112">sp_creatediagram stored procedure</span></span>  
  
    4.  <span data-ttu-id="d8911-113">sp_dropdiagram 預存程序</span><span class="sxs-lookup"><span data-stu-id="d8911-113">sp_dropdiagram stored procedure</span></span>  
  
    5.  <span data-ttu-id="d8911-114">sp_renamediagram 預存程序</span><span class="sxs-lookup"><span data-stu-id="d8911-114">sp_renamediagram stored procedure</span></span>  
  
    6.  <span data-ttu-id="d8911-115">fn_diagramobjects 函數</span><span class="sxs-lookup"><span data-stu-id="d8911-115">fn_diagramobjects function</span></span>  
  
    7.  <span data-ttu-id="d8911-116">sp_helpdiagrams 預存程序</span><span class="sxs-lookup"><span data-stu-id="d8911-116">sp_helpdiagrams stored procedure</span></span>  
  
    8.  <span data-ttu-id="d8911-117">sp_helpdiagramsdefinition 預存程序</span><span class="sxs-lookup"><span data-stu-id="d8911-117">sp_helpdiagramsdefinition stored procedure</span></span>  
  
    9. <span data-ttu-id="d8911-118">sp_upgraddiagrams 預存程序</span><span class="sxs-lookup"><span data-stu-id="d8911-118">sp_upgraddiagrams stored procedure</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8911-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d8911-119">See Also</span></span>  
 <span data-ttu-id="d8911-120">[瞭解資料庫關係圖擁有權 &#40;Visual Database Tools&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="d8911-120">[Understand Database Diagram Ownership &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 <span data-ttu-id="d8911-121">[升級舊版的資料庫關係圖 &#40;Visual Database Tools&#41;](upgrade-database-diagrams-from-previous-editions-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="d8911-121">[Upgrade Database Diagrams from Previous Editions &#40;Visual Database Tools&#41;](upgrade-database-diagrams-from-previous-editions-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="d8911-122">ALTER AUTHORIZATION &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d8911-122">ALTER AUTHORIZATION &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-authorization-transact-sql)  
  
  
