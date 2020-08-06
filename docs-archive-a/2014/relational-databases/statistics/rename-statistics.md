---
title: 重新命名統計資料 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- renaming statistics
- statistics [SQL Server], renaming
ms.assetid: a3bed7b7-3dc5-4b33-b1c6-67c27f573764
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 1528dcec50a662524531065d597b004fe7f59e5f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599414"
---
# <a name="rename-statistics"></a><span data-ttu-id="80220-102">重新命名統計資料</span><span class="sxs-lookup"><span data-stu-id="80220-102">Rename Statistics</span></span>
  <span data-ttu-id="80220-103">您可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80220-103">You can rename a statistics object in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[tsql](../../includes/tsql-md.md)]</span></span>  
  
 <span data-ttu-id="80220-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="80220-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="80220-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="80220-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="80220-106">限制事項</span><span class="sxs-lookup"><span data-stu-id="80220-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="80220-107">安全性</span><span class="sxs-lookup"><span data-stu-id="80220-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="80220-108">**若要使用下列項目重新命名統計資料物件：**</span><span class="sxs-lookup"><span data-stu-id="80220-108">**To rename a statistics object, using:**</span></span>  
  
     [<span data-ttu-id="80220-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="80220-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="80220-110">開始之前</span><span class="sxs-lookup"><span data-stu-id="80220-110">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="80220-111">限制事項</span><span class="sxs-lookup"><span data-stu-id="80220-111">Limitations and Restrictions</span></span>  
 <span data-ttu-id="80220-112">根據預設，建立索引時會在該索引的索引鍵資料行上建立統計資訊。</span><span class="sxs-lookup"><span data-stu-id="80220-112">By default, creating an index creates a statistic on the key columns of that index.</span></span> <span data-ttu-id="80220-113">因此，重新命名索引會自動重新命名統計資料物件，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="80220-113">Therefore, renaming the index automatically renames the statistics object, and vice versa.</span></span>  
  
 <span data-ttu-id="80220-114">變更物件名稱的任何部分，可能破壞指令碼和預存程序。</span><span class="sxs-lookup"><span data-stu-id="80220-114">Changing any part of an object name can break scripts and stored procedures.</span></span> <span data-ttu-id="80220-115">建議您卸除統計資料物件，並使用新名稱重新建立統計資料物件，而不要重新命名。</span><span class="sxs-lookup"><span data-stu-id="80220-115">Instead of renaming, we recommend that you drop the statistics object and re-create it with the new name.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="80220-116">Security</span><span class="sxs-lookup"><span data-stu-id="80220-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="80220-117">權限</span><span class="sxs-lookup"><span data-stu-id="80220-117">Permissions</span></span>  
 <span data-ttu-id="80220-118">需要資料表或檢視表的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="80220-118">Requires ALTER permission on the table or view.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="80220-119">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="80220-119">Using Transact-SQL</span></span>  
  
#### <a name="to-rename-a-statistics-object"></a><span data-ttu-id="80220-120">若要重新命名統計資料物件</span><span class="sxs-lookup"><span data-stu-id="80220-120">To rename a statistics object</span></span>  
  
1.  <span data-ttu-id="80220-121">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="80220-121">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="80220-122">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="80220-122">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="80220-123">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="80220-123">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    EXEC sp_rename N'AK_Employee_LoginID', N'AK_Emp_Login', N'STATISTICS';   
    GO  
    ```  
  
 <span data-ttu-id="80220-124">如需詳細資訊，請參閱 [sp_rename &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-rename-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="80220-124">For more information, see [sp_rename &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-rename-transact-sql).</span></span>  
  
  
