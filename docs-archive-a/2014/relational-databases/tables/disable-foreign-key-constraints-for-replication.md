---
title: 停用複寫的外部索引鍵條件約束 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- constraints [SQL Server], foreign keys
- foreign keys [SQL Server], disabling constraints
- disabling constraints
ms.assetid: 4211f2fd-d16a-4081-995c-43f1f0827f0b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4ee7f2fb7b0a27870a09a9d99b723b7faf739aeb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594967"
---
# <a name="disable-foreign-key-constraints-for-replication"></a><span data-ttu-id="19dea-102">停用複寫的外部索引鍵條件約束</span><span class="sxs-lookup"><span data-stu-id="19dea-102">Disable Foreign Key Constraints for Replication</span></span>
  <span data-ttu-id="19dea-103">您可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中停用複寫的外部索引鍵條件約束。</span><span class="sxs-lookup"><span data-stu-id="19dea-103">You can disable foreign key constraints for replication in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="19dea-104">這有助於從舊版 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]發行資料。</span><span class="sxs-lookup"><span data-stu-id="19dea-104">This can be useful if you are publishing data from a previous version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="19dea-105">如果使用複寫發行資料表，則會自動停用複寫代理程式所執行作業的外部索引鍵條件約束。</span><span class="sxs-lookup"><span data-stu-id="19dea-105">If a table is published using replication, foreign key constraints are automatically disabled for operations performed by replication agents.</span></span> <span data-ttu-id="19dea-106">當複寫代理程式在訂閱者端執行插入、更新或刪除時，不會檢查條件約束；如果使用者執行插入、更新或刪除，則會檢查條件約束。</span><span class="sxs-lookup"><span data-stu-id="19dea-106">When a replication agent performs an insert, update, or delete at a Subscriber, the constraint is not checked; if a user performs an insert, update, or delete, the constraint is checked.</span></span> <span data-ttu-id="19dea-107">停用複製代理程式的條件約束，是因為原本插入、更新或刪除資料時，就已在發行者端檢查過條件約束。</span><span class="sxs-lookup"><span data-stu-id="19dea-107">The constraint is disabled for the replication agent because the constraint was already checked at the Publisher when the data was originally inserted, updated, or deleted.</span></span>  
  
 <span data-ttu-id="19dea-108">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="19dea-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="19dea-109">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="19dea-109">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="19dea-110">安全性</span><span class="sxs-lookup"><span data-stu-id="19dea-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="19dea-111">**使用下列方法，停用複寫的外部索引鍵條件約束：**</span><span class="sxs-lookup"><span data-stu-id="19dea-111">**To disable a foreign key constraint for replication, using:**</span></span>  
  
     [<span data-ttu-id="19dea-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="19dea-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="19dea-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="19dea-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="19dea-114">開始之前</span><span class="sxs-lookup"><span data-stu-id="19dea-114">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="19dea-115">Security</span><span class="sxs-lookup"><span data-stu-id="19dea-115">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="19dea-116">權限</span><span class="sxs-lookup"><span data-stu-id="19dea-116">Permissions</span></span>  
 <span data-ttu-id="19dea-117">需要資料表的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="19dea-117">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="19dea-118">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="19dea-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-disable-a-foreign-key-constraint-for-replication"></a><span data-ttu-id="19dea-119">停用複寫的外部索引鍵條件約束</span><span class="sxs-lookup"><span data-stu-id="19dea-119">To disable a foreign key constraint for replication</span></span>  
  
1.  <span data-ttu-id="19dea-120">在 **[物件總管]** 中，展開您要修改其外部索引鍵條件約束的資料表，然後展開 **[索引鍵]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="19dea-120">In **Object Explorer**, expand the table with the foreign key constraint you want to modify, and then expand the **Keys** folder.</span></span>  
  
2.  <span data-ttu-id="19dea-121">以滑鼠右鍵按一下外部索引鍵條件約束，然後按一下 [修改]  。</span><span class="sxs-lookup"><span data-stu-id="19dea-121">Right-click the foreign key constraint and then click **Modify**.</span></span>  
  
3.  <span data-ttu-id="19dea-122">在 **[外部索引鍵關聯性]** 對話方塊中，針對 **[強制複寫]** 選取 **[否]** 值。</span><span class="sxs-lookup"><span data-stu-id="19dea-122">In the **Foreign Key Relationships** dialog box, select a value of **No** for **Enforce For Replication**.</span></span>  
  
4.  <span data-ttu-id="19dea-123">按一下 [關閉]  。</span><span class="sxs-lookup"><span data-stu-id="19dea-123">Click **Close**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="19dea-124">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="19dea-124">Using Transact-SQL</span></span>  
  
#### <a name="to-disable-a-foreign-key-constraint-for-replication"></a><span data-ttu-id="19dea-125">停用複寫的外部索引鍵條件約束</span><span class="sxs-lookup"><span data-stu-id="19dea-125">To disable a foreign key constraint for replication</span></span>  
  
1.  <span data-ttu-id="19dea-126">若要在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中執行此工作，請卸除外部索引鍵條件約束。</span><span class="sxs-lookup"><span data-stu-id="19dea-126">To perform this task in [!INCLUDE[tsql](../../includes/tsql-md.md)], drop the foreign key constraint.</span></span> <span data-ttu-id="19dea-127">然後加入新的外部索引鍵條件約束，並指定 NOT FOR REPLICATION 選項。</span><span class="sxs-lookup"><span data-stu-id="19dea-127">Then add a new foreign key constraint and specify the NOT FOR REPLICATION option.</span></span>  
  
 <span data-ttu-id="19dea-128">如需詳細資訊，請參閱 [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="19dea-128">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql).</span></span>  
  
###  <a name="TsqlExample"></a>  
