---
title: 修改檢查條件約束 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- CHECK constraints, modifying
- modifying constraints
- constraints [SQL Server], check
- constraints [SQL Server], modifying
ms.assetid: f22daef8-e350-40ef-8ff0-b5f87d1d9e56
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8377c80590612c8b68c315f7c37823eb8f5c5093
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597033"
---
# <a name="modify-check-constraints"></a><span data-ttu-id="0684b-102">修改檢查條件約束</span><span class="sxs-lookup"><span data-stu-id="0684b-102">Modify Check Constraints</span></span>
  <span data-ttu-id="0684b-103">當您想要變更條件約束運算式或是針對特定條件啟用或停用條件約束的選項時，可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 中修改檢查條件約束。</span><span class="sxs-lookup"><span data-stu-id="0684b-103">You can modify a check constraint in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)] when you want to change the constraint expression or the options that enable or disable the constraint for specific conditions.</span></span>  
  
 <span data-ttu-id="0684b-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="0684b-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="0684b-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="0684b-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="0684b-106">安全性</span><span class="sxs-lookup"><span data-stu-id="0684b-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="0684b-107">**若要使用下列項目來修改檢查條件約束：**</span><span class="sxs-lookup"><span data-stu-id="0684b-107">**To modify a check constraint using:**</span></span>  
  
     [<span data-ttu-id="0684b-108">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="0684b-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="0684b-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="0684b-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="0684b-110">開始之前</span><span class="sxs-lookup"><span data-stu-id="0684b-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="0684b-111">Security</span><span class="sxs-lookup"><span data-stu-id="0684b-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="0684b-112">權限</span><span class="sxs-lookup"><span data-stu-id="0684b-112">Permissions</span></span>  
 <span data-ttu-id="0684b-113">需要資料表的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="0684b-113">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="0684b-114">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="0684b-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-modify-a-check-constraint"></a><span data-ttu-id="0684b-115">若要修改檢查條件約束</span><span class="sxs-lookup"><span data-stu-id="0684b-115">To modify a check constraint</span></span>  
  
1.  <span data-ttu-id="0684b-116">在 [物件總管]  中，以滑鼠右鍵按一下包含檢查條件約束的資料表，並選取 [設計]  。</span><span class="sxs-lookup"><span data-stu-id="0684b-116">In the **Object Explorer**, right-click the table containing the check constraint and select **Design**.</span></span>  
  
2.  <span data-ttu-id="0684b-117">在 [資料表設計工具]  功能表上，按一下 [檢查條件約束...]  。</span><span class="sxs-lookup"><span data-stu-id="0684b-117">On the **Table Designer** menu, click **Check Constraints...**.</span></span>  
  
3.  <span data-ttu-id="0684b-118">在 **[檢查條件約束]** 對話方塊的 **[選取的檢查條件約束]** 底下，選取您想要編輯的條件約束。</span><span class="sxs-lookup"><span data-stu-id="0684b-118">In the **Check Constraints** dialog box, under **Selected Check Constraint**, select the constraint you wish to edit.</span></span>  
  
4.  <span data-ttu-id="0684b-119">完成下表中的動作：</span><span class="sxs-lookup"><span data-stu-id="0684b-119">Complete an action from the following table:</span></span>  
  
    |<span data-ttu-id="0684b-120">至</span><span class="sxs-lookup"><span data-stu-id="0684b-120">To</span></span>|<span data-ttu-id="0684b-121">請依照下列步驟：</span><span class="sxs-lookup"><span data-stu-id="0684b-121">Follow these steps</span></span>|  
    |--------|------------------------|  
    |<span data-ttu-id="0684b-122">編輯條件約束運算式</span><span class="sxs-lookup"><span data-stu-id="0684b-122">Edit the constraint expression</span></span>|<span data-ttu-id="0684b-123">在 **[運算式]** 欄位中輸入新的運算式。</span><span class="sxs-lookup"><span data-stu-id="0684b-123">Type the new expression in the **Expression** field.</span></span>|  
    |<span data-ttu-id="0684b-124">重新命名條件約束</span><span class="sxs-lookup"><span data-stu-id="0684b-124">Rename the constraint</span></span>|<span data-ttu-id="0684b-125">在 **[名稱]** 欄位中輸入新的名稱。</span><span class="sxs-lookup"><span data-stu-id="0684b-125">Type a new name in the **Name** field.</span></span>|  
    |<span data-ttu-id="0684b-126">套用條件約束至現有資料</span><span class="sxs-lookup"><span data-stu-id="0684b-126">Apply the constraint to existing data</span></span>|<span data-ttu-id="0684b-127">選取 [ **檢查建立或啟用時的現有資料** ] 選項。</span><span class="sxs-lookup"><span data-stu-id="0684b-127">Select the **Check Existing Data on Creation or Enabling** option.</span></span>|  
    |<span data-ttu-id="0684b-128">當加入新資料至資料表，或當現有資料在資料表中更新時，停用條件約束。</span><span class="sxs-lookup"><span data-stu-id="0684b-128">Disable the constraint when new data is added to the table or when existing data is updated in the table.</span></span>|<span data-ttu-id="0684b-129">清除 [ **INSERT 及 UPDATE 必須合乎條件約束** ] 選項。</span><span class="sxs-lookup"><span data-stu-id="0684b-129">Clear the **Enforce Constraint for INSERTs and UPDATEs** option.</span></span>|  
    |<span data-ttu-id="0684b-130">當複寫代理程式在資料表中插入或更新資料時，停用條件約束。</span><span class="sxs-lookup"><span data-stu-id="0684b-130">Disable the constraint when a replication agent inserts or updates data in your table.</span></span>|<span data-ttu-id="0684b-131">清除 **[強制複寫]** 選項。</span><span class="sxs-lookup"><span data-stu-id="0684b-131">Clear the **Enforce For Replication** option.</span></span>|  
  
    > [!NOTE]  
    >  <span data-ttu-id="0684b-132">某些資料庫具有不同的檢查條件約束功能。</span><span class="sxs-lookup"><span data-stu-id="0684b-132">Some databases have different functionality for check constraints.</span></span>  
  
5.  <span data-ttu-id="0684b-133">按一下 [關閉]  。</span><span class="sxs-lookup"><span data-stu-id="0684b-133">Click **Close**.</span></span>  
  
6.  <span data-ttu-id="0684b-134">在 [檔案]  功能表上，按一下 [儲存「資料表名稱」]。</span><span class="sxs-lookup"><span data-stu-id="0684b-134">On the **File** menu, click **Save**_table name_.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="0684b-135">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="0684b-135">Using Transact-SQL</span></span>  
 <span data-ttu-id="0684b-136">**若要修改檢查條件約束**</span><span class="sxs-lookup"><span data-stu-id="0684b-136">**To modify a check constraint**</span></span>  
  
 <span data-ttu-id="0684b-137">若要使用 `CHECK` 來修改 [!INCLUDE[tsql](../../includes/tsql-md.md)]條件約束，您必須先刪除現有的 `CHECK` 條件約束，然後以新的定義重新建立。</span><span class="sxs-lookup"><span data-stu-id="0684b-137">To modify a `CHECK` constraint using [!INCLUDE[tsql](../../includes/tsql-md.md)], you must first delete the existing `CHECK` constraint and then re-create it with the new definition.</span></span> <span data-ttu-id="0684b-138">如需詳細資訊，請參閱 [Delete Check Constraints](delete-check-constraints.md) (刪除檢查條件約束) 和 [Create Check Constraints](create-check-constraints.md)(建立檢查條件約束)。</span><span class="sxs-lookup"><span data-stu-id="0684b-138">For more information, see [Delete Check Constraints](delete-check-constraints.md) and [Create Check Constraints](create-check-constraints.md).</span></span>  
  
###  <a name="TsqlExample"></a>  
