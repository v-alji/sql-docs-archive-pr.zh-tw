---
title: 刪除預存程序 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: stored-procedures
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- removing stored procedures
- stored procedures [SQL Server], deleting
- deleting stored procedures
ms.assetid: 232dbf4d-392a-406f-af3a-579518cd8e46
author: stevestein
ms.author: sstein
ms.openlocfilehash: 418e68d4bb7c6ba6632767a554aea72e85726840
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599400"
---
# <a name="delete-a-stored-procedure"></a><span data-ttu-id="623e5-102">刪除預存程序</span><span class="sxs-lookup"><span data-stu-id="623e5-102">Delete a Stored Procedure</span></span>
    
##  <a name="this-topic-describes-how-to-delete-a-stored-procedure-in-sscurrent-by-using-ssmanstudiofull-or-tsql"></a><a name="Top"></a> <span data-ttu-id="623e5-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 來刪除 [!INCLUDE[tsql](../../includes/tsql-md.md)]中的預存程序。</span><span class="sxs-lookup"><span data-stu-id="623e5-103">This topic describes how to delete a stored procedure in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
-   <span data-ttu-id="623e5-104">**開始之前：** [限制事項](#Restrictions)、[安全性](#Security)</span><span class="sxs-lookup"><span data-stu-id="623e5-104">**Before you begin:**  [Limitations and Restrictions](#Restrictions), [Security](#Security)</span></span>  
  
-   <span data-ttu-id="623e5-105">**若要刪除程序，請使用：** [SQL Server Management Studio](#SSMSProcedure)、[Transact-SQL](#TsqlProcedure)</span><span class="sxs-lookup"><span data-stu-id="623e5-105">**To delete a procedure, using:**  [SQL Server Management Studio](#SSMSProcedure), [Transact-SQL](#TsqlProcedure)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="623e5-106">開始之前</span><span class="sxs-lookup"><span data-stu-id="623e5-106">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="623e5-107">限制事項</span><span class="sxs-lookup"><span data-stu-id="623e5-107">Limitations and Restrictions</span></span>  
 <span data-ttu-id="623e5-108">刪除程序後，若未更新物件和指令碼來反映程序移除，則可能導致相依物件和指令碼執行失敗。</span><span class="sxs-lookup"><span data-stu-id="623e5-108">Deleting a procedure can cause dependent objects and scripts to fail when the objects and scripts are not updated to reflect the removal of the procedure.</span></span> <span data-ttu-id="623e5-109">不過，如果所建立的相同名稱及相同參數的新程序是用以取代刪除的程序，其他參考該程序的物件仍然會成功地處理。</span><span class="sxs-lookup"><span data-stu-id="623e5-109">However, if a new procedure of the same name and the same parameters is created to replace the one that was deleted, other objects that reference it will still process successfully.</span></span> <span data-ttu-id="623e5-110">如需詳細資訊，請參閱 [檢視預存程序的相依性](view-the-dependencies-of-a-stored-procedure.md)。</span><span class="sxs-lookup"><span data-stu-id="623e5-110">For more information, see [View the Dependencies of a Stored Procedure](view-the-dependencies-of-a-stored-procedure.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="623e5-111">Security</span><span class="sxs-lookup"><span data-stu-id="623e5-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="623e5-112">權限</span><span class="sxs-lookup"><span data-stu-id="623e5-112">Permissions</span></span>  
 <span data-ttu-id="623e5-113">需要程序所屬結構描述的 ALTER 權限，或程序的 CONTROL 權限。</span><span class="sxs-lookup"><span data-stu-id="623e5-113">Requires ALTER permission on the schema to which the procedure belongs, or CONTROL permission on the procedure.</span></span>  
  
##  <a name="how-to-delete-a-stored-procedure"></a><a name="Procedures"></a> <span data-ttu-id="623e5-114">如何刪除預存程序</span><span class="sxs-lookup"><span data-stu-id="623e5-114">How to Delete a Stored Procedure</span></span>  
 <span data-ttu-id="623e5-115">您可以使用下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="623e5-115">You can use one of the following:</span></span>  
  
-   [<span data-ttu-id="623e5-116">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="623e5-116">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
-   [<span data-ttu-id="623e5-117">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="623e5-117">Transact-SQL</span></span>](#TsqlProcedure)  
  
###  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="623e5-118">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="623e5-118">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="623e5-119">**若要在物件總管中刪除程序**</span><span class="sxs-lookup"><span data-stu-id="623e5-119">**To delete a procedure in Object Explorer**</span></span>  
  
1.  <span data-ttu-id="623e5-120">在物件總管中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的執行個體，然後展開該執行個體。</span><span class="sxs-lookup"><span data-stu-id="623e5-120">In Object Explorer, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="623e5-121">依序展開 **[資料庫]** 、程序所屬的資料庫，以及 **[可程式性]** 。</span><span class="sxs-lookup"><span data-stu-id="623e5-121">Expand **Databases**, expand the database in which the procedure belongs, and then expand **Programmability**.</span></span>  
  
3.  <span data-ttu-id="623e5-122">展開 [預存程序]，以滑鼠右鍵按一下要移除的程序，然後按一下 [刪除]。</span><span class="sxs-lookup"><span data-stu-id="623e5-122">Expand **Stored Procedures**, right-click the procedure to remove, and then click **Delete**.</span></span>  
  
4.  <span data-ttu-id="623e5-123">若要檢視相依於程序的物件，請按一下 **[顯示相依性]** 。</span><span class="sxs-lookup"><span data-stu-id="623e5-123">To view objects that depend on the procedure, click **Show Dependencies**.</span></span>  
  
5.  <span data-ttu-id="623e5-124">確認已選取正確的程序，再按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="623e5-124">Confirm the correct procedure is selected, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="623e5-125">從任何相依物件和指令碼中移除程序的參考。</span><span class="sxs-lookup"><span data-stu-id="623e5-125">Remove references to the procedure from any dependent objects and scripts.</span></span>  
  
###  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="623e5-126">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="623e5-126">Using Transact-SQL</span></span>  
 <span data-ttu-id="623e5-127">**若要在查詢編輯器中刪除程序**</span><span class="sxs-lookup"><span data-stu-id="623e5-127">**To delete a procedure in Query Editor**</span></span>  
  
1.  <span data-ttu-id="623e5-128">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的執行個體，然後展開該執行個體。</span><span class="sxs-lookup"><span data-stu-id="623e5-128">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="623e5-129">依序展開 **[資料庫]** 、程序所屬的資料庫，或從工具列的可用資料庫清單中選取資料庫。</span><span class="sxs-lookup"><span data-stu-id="623e5-129">Expand **Databases**, expand the database in which the procedure belongs, or, from the tool bar, select the database from the list of available databases.</span></span>  
  
3.  <span data-ttu-id="623e5-130">按一下 [檔案] 功能表上的 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="623e5-130">On the File menu, click **New Query**.</span></span>  
  
4.  <span data-ttu-id="623e5-131">取得要從目前資料庫移除之預存程序的名稱。</span><span class="sxs-lookup"><span data-stu-id="623e5-131">Obtain the name of stored procedure to remove in the current database.</span></span> <span data-ttu-id="623e5-132">在 [物件總管] 中，依序展開 **[可程式性]** 與 **[預存程序]** 。</span><span class="sxs-lookup"><span data-stu-id="623e5-132">From Object Explorer, expand **Programmability** and then expand **Stored Procedures**.</span></span> <span data-ttu-id="623e5-133">或在查詢編輯器中，執行下列陳述式。</span><span class="sxs-lookup"><span data-stu-id="623e5-133">Alternatively, in the query editor, run the following statement.</span></span>  
  
    ```sql  
    SELECT name AS procedure_name   
        ,SCHEMA_NAME(schema_id) AS schema_name  
        ,type_desc  
        ,create_date  
        ,modify_date  
    FROM sys.procedures;  
    ```  
  
5.  <span data-ttu-id="623e5-134">將下列範例複製並貼到查詢編輯器中，然後插入要從目前資料庫中刪除的預存程序名稱。</span><span class="sxs-lookup"><span data-stu-id="623e5-134">Copy and paste the following example into the query editor and insert a stored procedure name to delete from the current database.</span></span>  
  
    ```sql  
    DROP PROCEDURE <stored procedure name>;  
    GO  
    ```  
  
6.  <span data-ttu-id="623e5-135">從任何相依物件和指令碼中移除程序的參考。</span><span class="sxs-lookup"><span data-stu-id="623e5-135">Remove references to the procedure from any dependent objects and scripts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="623e5-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="623e5-136">See Also</span></span>  
 <span data-ttu-id="623e5-137">[建立預存程序](create-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="623e5-137">[Create a Stored Procedure](create-a-stored-procedure.md) </span></span>  
 <span data-ttu-id="623e5-138">[修改預存程序](modify-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="623e5-138">[Modify a Stored Procedure](modify-a-stored-procedure.md) </span></span>  
 <span data-ttu-id="623e5-139">[重新命名預存程序](rename-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="623e5-139">[Rename a Stored Procedure](rename-a-stored-procedure.md) </span></span>  
 <span data-ttu-id="623e5-140">[檢視預存程序的定義](view-the-definition-of-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="623e5-140">[View the Definition of a Stored Procedure](view-the-definition-of-a-stored-procedure.md) </span></span>  
 <span data-ttu-id="623e5-141">[檢視預存程序的相依性](view-the-dependencies-of-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="623e5-141">[View the Dependencies of a Stored Procedure](view-the-dependencies-of-a-stored-procedure.md) </span></span>  
 [<span data-ttu-id="623e5-142">DROP PROCEDURE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="623e5-142">DROP PROCEDURE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-procedure-transact-sql)  
  
  
