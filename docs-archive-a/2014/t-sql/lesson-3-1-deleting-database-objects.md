---
title: 刪除資料庫物件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- deleting database objects
ms.assetid: dbb94fdf-c85b-477b-8e84-f830d259bade
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 6bd69935dbfac020c4c75bb391e7932009fd4197
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585743"
---
# <a name="deleting-database-objects"></a><span data-ttu-id="77026-102">刪除資料庫物件</span><span class="sxs-lookup"><span data-stu-id="77026-102">Deleting Database Objects</span></span>
  <span data-ttu-id="77026-103">若要移除這個教學課程中的所有執行內容，原本只要刪除資料庫就可以了，</span><span class="sxs-lookup"><span data-stu-id="77026-103">To remove all traces of this tutorial, you could just delete the database.</span></span> <span data-ttu-id="77026-104">但是，在這個主題中，您將會逐步執行各個步驟，以反轉您在這個教學課程中所做的每一個動作。</span><span class="sxs-lookup"><span data-stu-id="77026-104">However, in this topic, you will go through the steps to reverse every action you took doing the tutorial.</span></span>  
  
### <a name="removing-permissions-and-objects"></a><span data-ttu-id="77026-105">移除權限和物件</span><span class="sxs-lookup"><span data-stu-id="77026-105">Removing permissions and objects</span></span>  
  
1.  <span data-ttu-id="77026-106">刪除物件之前，請先確定您是在正確的資料庫中：</span><span class="sxs-lookup"><span data-stu-id="77026-106">Before you delete objects, make sure you are in the correct database:</span></span>  
  
    ```  
    USE TestData;  
    GO  
    ```  
  
2.  <span data-ttu-id="77026-107">使用 `REVOKE` 陳述式移除 `Mary` 對預存程序的執行權限：</span><span class="sxs-lookup"><span data-stu-id="77026-107">Use the `REVOKE` statement to remove execute permission for `Mary` on the stored procedure:</span></span>  
  
    ```  
    REVOKE EXECUTE ON pr_Names FROM Mary;  
    GO  
  
    ```  
  
3.  <span data-ttu-id="77026-108">使用 `DROP` 陳述式移除 `Mary` 存取 `TestData` 資料庫的權限：</span><span class="sxs-lookup"><span data-stu-id="77026-108">Use the `DROP` statement to remove permission for `Mary` to access the `TestData` database:</span></span>  
  
    ```  
    DROP USER Mary;  
    GO  
  
    ```  
  
4.  <span data-ttu-id="77026-109">使用 `DROP` 陳述式移除 `Mary` 存取這個 [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)]執行個體的權限：</span><span class="sxs-lookup"><span data-stu-id="77026-109">Use the `DROP` statement to remove permission for `Mary` to access this instance of [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)]:</span></span>  
  
    ```  
    DROP LOGIN [<computer_name>\Mary];  
    GO  
  
    ```  
  
5.  <span data-ttu-id="77026-110">使用 `DROP` 陳述式移除 `pr_Names`預存程序：</span><span class="sxs-lookup"><span data-stu-id="77026-110">Use the `DROP` statement to remove the store procedure `pr_Names`:</span></span>  
  
    ```  
    DROP PROC pr_Names;  
    GO  
  
    ```  
  
6.  <span data-ttu-id="77026-111">使用 `DROP` 陳述式移除 `vw_Names`檢視：</span><span class="sxs-lookup"><span data-stu-id="77026-111">Use the `DROP` statement to remove the view `vw_Names`:</span></span>  
  
    ```  
    DROP View vw_Names;  
    GO  
  
    ```  
  
7.  <span data-ttu-id="77026-112">使用 `DELETE` 陳述式移除 `Products` 資料表中的所有資料列：</span><span class="sxs-lookup"><span data-stu-id="77026-112">Use the `DELETE` statement to remove all rows from the `Products` table:</span></span>  
  
    ```  
    DELETE FROM Products;  
    GO  
  
    ```  
  
8.  <span data-ttu-id="77026-113">使用 `DROP` 陳述式移除 `Products` 資料表：</span><span class="sxs-lookup"><span data-stu-id="77026-113">Use the `DROP` statement to remove the `Products` table:</span></span>  
  
    ```  
    DROP Table Products;  
    GO  
  
    ```  
  
9. <span data-ttu-id="77026-114">當您還在 `TestData` 資料庫中時，將無法移除這個資料庫；因此，請先將內容切換到其他資料庫，然後使用 `DROP` 陳述式移除 `TestData` 資料庫：</span><span class="sxs-lookup"><span data-stu-id="77026-114">You cannot remove the `TestData` database while you are in the database; therefore, first switch context to another database, and then use the `DROP` statement to remove the `TestData` database:</span></span>  
  
    ```  
    USE MASTER;  
    GO  
    DROP DATABASE TestData;  
    GO  
  
    ```  
  
 <span data-ttu-id="77026-115">「撰寫 [!INCLUDE[tsql](../includes/tsql-md.md)] 陳述式」教學課程到此結束。</span><span class="sxs-lookup"><span data-stu-id="77026-115">This concludes the Writing [!INCLUDE[tsql](../includes/tsql-md.md)] Statements tutorial.</span></span> <span data-ttu-id="77026-116">請記住，這個教學課程只是簡短概觀，因此並不會描述陳述式的所有選項。</span><span class="sxs-lookup"><span data-stu-id="77026-116">Remember, this tutorial is a brief overview and it does not describe all the options to the statements that are used.</span></span> <span data-ttu-id="77026-117">如果要設計和建立有效率的資料庫結構，以及設定資料的安全存取，則所需的資料庫將會比這個教學課程的所示範例更加複雜。</span><span class="sxs-lookup"><span data-stu-id="77026-117">Designing and creating an efficient database structure and configuring secure access to the data requires a more complex database than that shown in this tutorial.</span></span>  
  
## <a name="return-to-sql-server-tools-portal"></a><span data-ttu-id="77026-118">返回 SQL Server 工具入口網站</span><span class="sxs-lookup"><span data-stu-id="77026-118">Return to SQL Server Tools Portal</span></span>  
 [<span data-ttu-id="77026-119">教學課程：撰寫 Transact-SQL 陳述式</span><span class="sxs-lookup"><span data-stu-id="77026-119">Tutorial: Writing Transact-SQL Statements</span></span>](tutorial-writing-transact-sql-statements.md)  
  
## <a name="see-also"></a><span data-ttu-id="77026-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="77026-120">See Also</span></span>  
 <span data-ttu-id="77026-121">[REVOKE &#40;Transact-SQL&#41;](/sql/t-sql/statements/revoke-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="77026-121">[REVOKE &#40;Transact-SQL&#41;](/sql/t-sql/statements/revoke-transact-sql) </span></span>  
 <span data-ttu-id="77026-122">[DROP USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-user-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="77026-122">[DROP USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-user-transact-sql) </span></span>  
 <span data-ttu-id="77026-123">[DROP LOGIN &#40;Transact-sql&#41;](/sql/t-sql/statements/drop-login-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="77026-123">[DROP LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-login-transact-sql) </span></span>  
 <span data-ttu-id="77026-124">[DROP PROCEDURE &#40;Transact-sql&#41;](/sql/t-sql/statements/drop-procedure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="77026-124">[DROP PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-procedure-transact-sql) </span></span>  
 <span data-ttu-id="77026-125">[DROP VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-view-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="77026-125">[DROP VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-view-transact-sql) </span></span>  
 <span data-ttu-id="77026-126">[DELETE &#40;Transact-SQL&#41;](/sql/t-sql/statements/delete-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="77026-126">[DELETE &#40;Transact-SQL&#41;](/sql/t-sql/statements/delete-transact-sql) </span></span>  
 <span data-ttu-id="77026-127">[DROP TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-table-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="77026-127">[DROP TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-table-transact-sql) </span></span>  
 [<span data-ttu-id="77026-128">DROP DATABASE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="77026-128">DROP DATABASE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-database-audit-specification-transact-sql)  
  
  
