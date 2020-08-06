---
title: 刪除檢視 |Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- dropping views
- deleting views
- views [SQL Server], deleting
- removing views
ms.assetid: 6823c7f8-06ca-4bda-8482-7092f03d52a0
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3e05724f7d6384d0407e915207ad60a1cdfb01b6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585211"
---
# <a name="delete-views"></a><span data-ttu-id="3778e-102">刪除檢視</span><span class="sxs-lookup"><span data-stu-id="3778e-102">Delete Views</span></span>
  <span data-ttu-id="3778e-103">您可以在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中刪除 (卸除) 檢視，方法是使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或 [!INCLUDE[tsql](../../includes/tsql-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3778e-103">You can delete (drop) views in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)]</span></span>  
  

  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="3778e-104">開始之前</span><span class="sxs-lookup"><span data-stu-id="3778e-104">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="3778e-105">限制事項</span><span class="sxs-lookup"><span data-stu-id="3778e-105">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="3778e-106">當您卸除檢視時，也會從系統目錄中刪除檢視的定義和檢視的其他相關資訊。</span><span class="sxs-lookup"><span data-stu-id="3778e-106">When you drop a view, the definition of the view and other information about the view is deleted from the system catalog.</span></span> <span data-ttu-id="3778e-107">檢視的所有權限也都會刪除。</span><span class="sxs-lookup"><span data-stu-id="3778e-107">All permissions for the view are also deleted.</span></span>  
  
-   <span data-ttu-id="3778e-108">在利用 `DROP TABLE` 來卸除的資料表中，您必須利用 `DROP VIEW`來明確卸除任何檢視。</span><span class="sxs-lookup"><span data-stu-id="3778e-108">Any view on a table that is dropped by using `DROP TABLE` must be dropped explicitly by using `DROP VIEW`.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="3778e-109">Security</span><span class="sxs-lookup"><span data-stu-id="3778e-109">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="3778e-110">權限</span><span class="sxs-lookup"><span data-stu-id="3778e-110">Permissions</span></span>  
 <span data-ttu-id="3778e-111">需要 SCHEMA 的 ALTER 權限或 OBJECT 的 CONTROL 權限。</span><span class="sxs-lookup"><span data-stu-id="3778e-111">Requires ALTER permission on SCHEMA or CONTROL permission on OBJECT.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="3778e-112">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="3778e-112">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-a-view-from-a-database"></a><span data-ttu-id="3778e-113">若要從資料庫刪除檢視</span><span class="sxs-lookup"><span data-stu-id="3778e-113">To delete a view from a database</span></span>  
  
1.  <span data-ttu-id="3778e-114">在 **[物件總管]** 中，展開資料庫，此資料庫包含您要刪除的檢視，然後展開 **[檢視]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="3778e-114">In **Object Explorer**, expand the database that contains the view you want to delete, and then expand the **Views** folder.</span></span>  
  
2.  <span data-ttu-id="3778e-115">以滑鼠右鍵按一下您要刪除的檢視，然後按一下 [刪除]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3778e-115">Right-click the view you want to delete and click **Delete**.</span></span>  
  
3.  <span data-ttu-id="3778e-116">在 **[刪除物件]** 對話方塊中，按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="3778e-116">In the **Delete Object** dialog box, click **OK**.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="3778e-117">在 [刪除物件]\*\*\*\* 對話方塊中按一下 [顯示相依性]\*\*\*\*，開啟 [<檢視名稱>__ 相依性]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="3778e-117">Click **Show Dependencies** in the **Delete Object** dialog box to open the _view_name_**Dependencies** dialog box.</span></span> <span data-ttu-id="3778e-118">這就會顯示相依於檢視的所有物件以及檢視所相依的所有物件。</span><span class="sxs-lookup"><span data-stu-id="3778e-118">This will show all of the objects that depend on the view and all of the objects on which the view depends.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="3778e-119">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="3778e-119">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-a-view-from-a-database"></a><span data-ttu-id="3778e-120">若要從資料庫刪除檢視</span><span class="sxs-lookup"><span data-stu-id="3778e-120">To delete a view from a database</span></span>  
  
1.  <span data-ttu-id="3778e-121">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="3778e-121">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="3778e-122">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="3778e-122">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="3778e-123">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="3778e-123">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="3778e-124">此範例只在指定的檢視已存在時才會予以刪除。</span><span class="sxs-lookup"><span data-stu-id="3778e-124">The example deletes the specified view only if the view already exists.</span></span>  
  
    ```  
    USE AdventureWorks2012 ;  
    GO  
    IF OBJECT_ID ('HumanResources.EmployeeHireDate', 'V') IS NOT NULL  
    DROP VIEW HumanResources.EmployeeHireDate;  
    GO  
    ```  
  
 <span data-ttu-id="3778e-125">如需詳細資訊，請參閱 [DROP VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-view-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="3778e-125">For more information, see [DROP VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-view-transact-sql).</span></span>  
  
  
