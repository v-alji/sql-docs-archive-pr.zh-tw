---
title: 刪除外部索引鍵關聯性 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- foreign keys [SQL Server], deleting
- removing foreign keys
- deleting foreign keys
ms.assetid: 9c9e9ae4-9e03-4137-acb6-b18928a0c4ca
author: stevestein
ms.author: sstein
ms.openlocfilehash: 86ae466b9fce53073bfc0645c753246023ff3269
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595876"
---
# <a name="delete-foreign-key-relationships"></a><span data-ttu-id="87134-102">刪除外部索引鍵關聯性</span><span class="sxs-lookup"><span data-stu-id="87134-102">Delete Foreign Key Relationships</span></span>
  <span data-ttu-id="87134-103">您可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中刪除外部索引鍵條件約束。</span><span class="sxs-lookup"><span data-stu-id="87134-103">You can delete a foreign key constraint in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="87134-104">刪除外部索引鍵條件約束後，就不需要強制執行參考完整性。</span><span class="sxs-lookup"><span data-stu-id="87134-104">Deleting a foreign key constraint removes the requirement to enforce referential integrity.</span></span>  
  
 <span data-ttu-id="87134-105">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="87134-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="87134-106">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="87134-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="87134-107">安全性</span><span class="sxs-lookup"><span data-stu-id="87134-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="87134-108">**使用下列方法刪除外部索引鍵條件約束：**</span><span class="sxs-lookup"><span data-stu-id="87134-108">**To delete a foreign key constraint, using:**</span></span>  
  
     [<span data-ttu-id="87134-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="87134-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="87134-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="87134-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="87134-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="87134-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="87134-112">Security</span><span class="sxs-lookup"><span data-stu-id="87134-112">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="87134-113">權限</span><span class="sxs-lookup"><span data-stu-id="87134-113">Permissions</span></span>  
 <span data-ttu-id="87134-114">需要資料表的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="87134-114">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="87134-115">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="87134-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-a-foreign-key-constraint"></a><span data-ttu-id="87134-116">若要刪除外部索引鍵條件約束</span><span class="sxs-lookup"><span data-stu-id="87134-116">To delete a foreign key constraint</span></span>  
  
1.  <span data-ttu-id="87134-117">在 **[物件總管]** 中，展開含有條件約束的資料表，然後展開 **[索引鍵]** 。</span><span class="sxs-lookup"><span data-stu-id="87134-117">In **Object Explorer**, expand the table with the constraint and then expand **Keys**.</span></span>  
  
2.  <span data-ttu-id="87134-118">以滑鼠右鍵按一下條件約束，然後按一下 [刪除]  。</span><span class="sxs-lookup"><span data-stu-id="87134-118">Right-click the constraint and then click **Delete**.</span></span>  
  
3.  <span data-ttu-id="87134-119">在 **[刪除物件]** 對話方塊中，按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="87134-119">In the **Delete Object** dialog box, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="87134-120">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="87134-120">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-a-foreign-key-constraint"></a><span data-ttu-id="87134-121">若要刪除外部索引鍵條件約束</span><span class="sxs-lookup"><span data-stu-id="87134-121">To delete a foreign key constraint</span></span>  
  
1.  <span data-ttu-id="87134-122">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="87134-122">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="87134-123">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="87134-123">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="87134-124">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="87134-124">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    ALTER TABLE dbo.DocExe   
    DROP CONSTRAINT FK_Column_B;   
    GO  
    ```  
  
 <span data-ttu-id="87134-125">如需詳細資訊，請參閱 [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="87134-125">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql).</span></span>  
  
  
