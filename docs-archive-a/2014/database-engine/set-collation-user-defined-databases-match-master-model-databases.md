---
title: 設定使用者定義資料庫的定序，使其符合 master 和 model 資料庫的定序 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: c686446f-dae1-4b05-a3df-837b3422988d
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: b48696fb56c40062d62f04845715170887f84fda
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687138"
---
# <a name="set-the-collation-of-user-defined-databases-to-match-those-of-the-master-and-model-databases"></a><span data-ttu-id="9e75e-102">將使用者定義資料庫的定序設定為 master 和 model 資料庫的定序</span><span class="sxs-lookup"><span data-stu-id="9e75e-102">Set the Collation of User-defined Databases to Match Those of the master and model Databases</span></span>
  <span data-ttu-id="9e75e-103">此規則會使用與 master 或 model 定序相同的資料庫定序來定義使用者定義資料庫。</span><span class="sxs-lookup"><span data-stu-id="9e75e-103">This rule checks whether user-defined databases are defined by using a database collation that is the same as the collation for master or model.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="9e75e-104">最佳做法建議</span><span class="sxs-lookup"><span data-stu-id="9e75e-104">Best Practices Recommendations</span></span>  
 <span data-ttu-id="9e75e-105">我們建議您最好讓使用者定義資料庫的定序符合 master 或 model 的定序。</span><span class="sxs-lookup"><span data-stu-id="9e75e-105">We recommend that the collations of user-defined databases match the collation of master or model.</span></span> <span data-ttu-id="9e75e-106">否則，可能會發生妨礙程式碼執行的定序衝突。</span><span class="sxs-lookup"><span data-stu-id="9e75e-106">Otherwise, collation conflicts can occur that might prevent code from executing.</span></span> <span data-ttu-id="9e75e-107">例如，當預存程序將一個資料表聯結到暫存資料表時，[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 可能會在使用者定義資料庫的定序與 model 資料庫的定序不同時，結束批次並傳回定序衝突錯誤。</span><span class="sxs-lookup"><span data-stu-id="9e75e-107">For example, when a stored procedure joins one table to a temporary table, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] might end the batch and return a collation conflict error if the collations of the user-defined database and the model database are different.</span></span> <span data-ttu-id="9e75e-108">發生這個錯誤是因為暫存資料表是在 tempdb 內建立，而 tempdb 的定序是以 model 的定序為根據。</span><span class="sxs-lookup"><span data-stu-id="9e75e-108">This occurs because temporary tables are created in tempdb, which bases its collation on that of model.</span></span>  
  
 <span data-ttu-id="9e75e-109">如果您遇到定序衝突錯誤，請考慮以下其中一個解決方案：</span><span class="sxs-lookup"><span data-stu-id="9e75e-109">If you experience collation conflict errors, consider one of the following solutions:</span></span>  
  
-   <span data-ttu-id="9e75e-110">從使用者資料庫將資料匯出到定序與 master 和 model 資料庫相同的新資料表內。</span><span class="sxs-lookup"><span data-stu-id="9e75e-110">Export the data from the user database and import it into new tables that have the same collation as the master and model databases.</span></span>  
  
-   <span data-ttu-id="9e75e-111">重建系統資料庫，以便使用符合使用者資料庫定序的定序。</span><span class="sxs-lookup"><span data-stu-id="9e75e-111">Rebuild the system databases to use a collation that matches the user database collation.</span></span> <span data-ttu-id="9e75e-112">如需有關如何重建系統資料庫的詳細資訊，請參閱[重建系統資料庫](../relational-databases/databases/system-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="9e75e-112">For more information about how to rebuild the system databases, see [Rebuild System Databases](../relational-databases/databases/system-databases.md).</span></span>  
  
-   <span data-ttu-id="9e75e-113">修改可將使用者資料表聯結到 tempdb 內資料表的任何預存程序，以便使用使用者資料庫的定序在 tempdb 中建立資料表。</span><span class="sxs-lookup"><span data-stu-id="9e75e-113">Modify any stored procedures that join user tables to tables in tempdb to create the tables in tempdb by using the collation of the user database.</span></span> <span data-ttu-id="9e75e-114">若要這樣做，請將 `COLLATE database_default` 子句加入到暫存資料表的資料行定義中，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="9e75e-114">To do this, add the `COLLATE database_default` clause to the column definitions of the temporary table, as shown in the following example:</span></span>  
  
    ```  
    CREATE TABLE #temp1 ( c1 int, c2 varchar(30) COLLATE database_default )  
    ```  
  
## <a name="for-more-information"></a><span data-ttu-id="9e75e-115">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="9e75e-115">For More Information</span></span>  
 [<span data-ttu-id="9e75e-116">設定或變更資料庫定序</span><span class="sxs-lookup"><span data-stu-id="9e75e-116">Set or Change the Database Collation</span></span>](../relational-databases/collations/set-or-change-the-database-collation.md)  
  
 [<span data-ttu-id="9e75e-117">設定或變更資料行定序</span><span class="sxs-lookup"><span data-stu-id="9e75e-117">Set or Change the Column Collation</span></span>](../relational-databases/collations/set-or-change-the-column-collation.md)  
  
 [<span data-ttu-id="9e75e-118">ALTER DATABASE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="9e75e-118">ALTER DATABASE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql)  
  
 [<span data-ttu-id="9e75e-119">COLLATE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="9e75e-119">COLLATE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/collations)  
  
 [<span data-ttu-id="9e75e-120">sys.databases &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="9e75e-120">sys.databases &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)  
  
 [<span data-ttu-id="9e75e-121">Microsoft 知識庫文章325335</span><span class="sxs-lookup"><span data-stu-id="9e75e-121">Microsoft Knowledge Base article 325335</span></span>](https://go.microsoft.com/fwlink/?linkid=117751)  
  
 [<span data-ttu-id="9e75e-122">如何：從命令提示字元安裝 SQL Server 2008</span><span class="sxs-lookup"><span data-stu-id="9e75e-122">How to: Install SQL Server 2008 from the Command Prompt</span></span>](https://go.microsoft.com/fwlink/?LinkId=81585)  
  
## <a name="see-also"></a><span data-ttu-id="9e75e-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9e75e-123">See Also</span></span>  
 [<span data-ttu-id="9e75e-124">使用原則式管理來監視和強制最佳做法</span><span class="sxs-lookup"><span data-stu-id="9e75e-124">Monitor and Enforce Best Practices by Using Policy-Based Management</span></span>](../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
