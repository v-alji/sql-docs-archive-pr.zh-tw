---
title: 變更資料表中的資料行順序 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- columns [SQL Server], change order in a table
- column order, change
ms.assetid: cd99ef56-9085-431a-a0fc-58e7add5399f
author: stevestein
ms.author: sstein
ms.openlocfilehash: d162f9dc793ceb9ea423d94922f7358f1729712e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595883"
---
# <a name="change-column-order-in-a-table"></a><span data-ttu-id="501fe-102">變更資料表中的資料行順序</span><span class="sxs-lookup"><span data-stu-id="501fe-102">Change Column Order in a Table</span></span>
  <span data-ttu-id="501fe-103">您可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ，在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]的資料表設計工具中變更資料行的順序。</span><span class="sxs-lookup"><span data-stu-id="501fe-103">You can change the order of columns in Table Designer in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="501fe-104">變更資料表的資料行順序可能影響相依於特定資料行順序的程式碼和應用程式。</span><span class="sxs-lookup"><span data-stu-id="501fe-104">Changing the column order of a table may affect code and applications that depend on the specific order of columns.</span></span> <span data-ttu-id="501fe-105">這些包含查詢、檢視、預存程序、使用者自訂函數，以及用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="501fe-105">These include queries, views, stored procedures, user-defined functions, and client applications.</span></span> <span data-ttu-id="501fe-106">在對資料行順序進行任何變更之前，請審慎考慮。</span><span class="sxs-lookup"><span data-stu-id="501fe-106">Carefully consider any changes you want to make to column order before making it.</span></span> <span data-ttu-id="501fe-107">最佳作法是在應用程式和查詢層級指定傳回資料行的順序。</span><span class="sxs-lookup"><span data-stu-id="501fe-107">Best practice is to specify the order in which the columns are returned at the application and query level.</span></span> <span data-ttu-id="501fe-108">您不應該仰賴使用 SELECT \*，根據資料表中定義資料行的順序，按照預期的順序傳回所有資料行。</span><span class="sxs-lookup"><span data-stu-id="501fe-108">You should not rely on the use of SELECT \* to return all columns in an expected order based on the order in which they are defined in the table.</span></span> <span data-ttu-id="501fe-109">請務必按照您想要顯示資料行的順序，在查詢和應用程式中依名稱指定資料行。</span><span class="sxs-lookup"><span data-stu-id="501fe-109">Always specify the columns by name in your queries and applications in the order in which you would like them to appear.</span></span>  
  
 <span data-ttu-id="501fe-110">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="501fe-110">**In This Topic**</span></span>  
  
-   <span data-ttu-id="501fe-111">**若要使用下列項目來變更資料行順序：**</span><span class="sxs-lookup"><span data-stu-id="501fe-111">**To change the column order, using:**</span></span>  
  
     [<span data-ttu-id="501fe-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="501fe-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="501fe-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="501fe-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="501fe-114">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="501fe-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-change-the-column-order"></a><span data-ttu-id="501fe-115">若要變更資料行順序</span><span class="sxs-lookup"><span data-stu-id="501fe-115">To change the column order</span></span>  
  
1.  <span data-ttu-id="501fe-116">在 [物件總管]  中，以滑鼠右鍵按一下包含要重新排序之資料行的資料表，然後按一下 [設計]  。</span><span class="sxs-lookup"><span data-stu-id="501fe-116">In **Object Explorer**, right-click the table with columns you want to reorder and click **Design**.</span></span>  
  
2.  <span data-ttu-id="501fe-117">選取要重排順序之資料行名稱左邊的方塊。</span><span class="sxs-lookup"><span data-stu-id="501fe-117">Select the box to the left of the column name that you want to reorder.</span></span>  
  
3.  <span data-ttu-id="501fe-118">將資料行拖曳到資料表中的其他位置。</span><span class="sxs-lookup"><span data-stu-id="501fe-118">Drag the column to another location within the table.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="501fe-119">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="501fe-119">Using Transact-SQL</span></span>  
 <span data-ttu-id="501fe-120">**若要變更資料行順序**</span><span class="sxs-lookup"><span data-stu-id="501fe-120">**To change the column order**</span></span>  
  
 <span data-ttu-id="501fe-121">您無法使用 Transact-SQL 陳述式來執行這項工作。</span><span class="sxs-lookup"><span data-stu-id="501fe-121">This task cannot be performed using Transact-SQL statements.</span></span>  
  
###  <a name="TsqlExample"></a>  
