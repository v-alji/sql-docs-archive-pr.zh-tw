---
title: 修改唯一的條件約束 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- modifying constraints
- UNIQUE constraints [SQL Server], modifying
- constraints [SQL Server], modifying
- constraints [SQL Server], unique
ms.assetid: fddbdc9e-958b-4614-8e88-6ca205d64a4e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 74b044202f7e8e9bc762f025833cf2d0ff84c4c8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607331"
---
# <a name="modify-unique-constraints"></a><span data-ttu-id="fb0ee-102">修改唯一的條件約束</span><span class="sxs-lookup"><span data-stu-id="fb0ee-102">Modify Unique Constraints</span></span>
  <span data-ttu-id="fb0ee-103">您可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中修改唯一條件約束。</span><span class="sxs-lookup"><span data-stu-id="fb0ee-103">You can modify a unique constraint in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="fb0ee-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="fb0ee-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="fb0ee-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="fb0ee-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="fb0ee-106">安全性</span><span class="sxs-lookup"><span data-stu-id="fb0ee-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="fb0ee-107">**若要使用下列項目來修改唯一條件約束：**</span><span class="sxs-lookup"><span data-stu-id="fb0ee-107">**To modify a unique constraint using:**</span></span>  
  
     [<span data-ttu-id="fb0ee-108">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="fb0ee-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="fb0ee-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="fb0ee-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="fb0ee-110">開始之前</span><span class="sxs-lookup"><span data-stu-id="fb0ee-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="fb0ee-111">Security</span><span class="sxs-lookup"><span data-stu-id="fb0ee-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="fb0ee-112">權限</span><span class="sxs-lookup"><span data-stu-id="fb0ee-112">Permissions</span></span>  
 <span data-ttu-id="fb0ee-113">需要資料表的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="fb0ee-113">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="fb0ee-114">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="fb0ee-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-modify-a-unique-constraint"></a><span data-ttu-id="fb0ee-115">若要修改唯一條件約束</span><span class="sxs-lookup"><span data-stu-id="fb0ee-115">To modify a unique constraint</span></span>  
  
1.  <span data-ttu-id="fb0ee-116">在 [物件總管]  中，以滑鼠右鍵按一下包含唯一條件約束的資料表，然後選取 [設計]  。</span><span class="sxs-lookup"><span data-stu-id="fb0ee-116">In the **Object Explorer**, right-click the table containing the unique constraint and select **Design**.</span></span>  
  
2.  <span data-ttu-id="fb0ee-117">在 [資料表設計工具]  功能表中，按一下 [索引/索引鍵]  。</span><span class="sxs-lookup"><span data-stu-id="fb0ee-117">On the **Table Designer** menu, click **Indexes/Keys...**.</span></span>  
  
3.  <span data-ttu-id="fb0ee-118">在 [索引/索引鍵]  對話方塊的 [選取的主/唯一索引鍵或索引]  底下，選取您想要編輯的條件約束。</span><span class="sxs-lookup"><span data-stu-id="fb0ee-118">In the **Indexes/Keys** dialog box, under **Selected Primary/Unique Key or Index**, select the constraint you wish to edit.</span></span>  
  
4.  <span data-ttu-id="fb0ee-119">完成下表中的動作：</span><span class="sxs-lookup"><span data-stu-id="fb0ee-119">Complete an action from the following table:</span></span>  
  
    |<span data-ttu-id="fb0ee-120">至</span><span class="sxs-lookup"><span data-stu-id="fb0ee-120">To</span></span>|<span data-ttu-id="fb0ee-121">請依照下列步驟：</span><span class="sxs-lookup"><span data-stu-id="fb0ee-121">Follow these steps</span></span>|  
    |--------|------------------------|  
    |<span data-ttu-id="fb0ee-122">變更與條件約束有關的資料行</span><span class="sxs-lookup"><span data-stu-id="fb0ee-122">Change the columns that the constraint is associated with</span></span>|<span data-ttu-id="fb0ee-123">1) 在 [(一般)]  底下的方格中，按一下 [資料行]  ，然後按一下屬性右邊的省略符號 **(...)** 。</span><span class="sxs-lookup"><span data-stu-id="fb0ee-123">1) In the grid under **(General)**, click **Columns** and then click the ellipses **(...)** to the right of the property.</span></span><br /><br /> <span data-ttu-id="fb0ee-124">2) 在 [索引資料行]  對話方塊中，指定索引的新資料行或排序次序，同時指定這兩者。</span><span class="sxs-lookup"><span data-stu-id="fb0ee-124">2) In the **Index Columns** dialog box, specify the new column or sort order or both for the index.</span></span>|  
    |<span data-ttu-id="fb0ee-125">重新命名條件約束</span><span class="sxs-lookup"><span data-stu-id="fb0ee-125">Rename the constraint</span></span>|<span data-ttu-id="fb0ee-126">在 **[識別]** 底下的方格中，於 **[名稱]** 方塊中輸入新的名稱。</span><span class="sxs-lookup"><span data-stu-id="fb0ee-126">In the grid under **Identity**, type a new name in the **Name** box.</span></span> <span data-ttu-id="fb0ee-127">確定新名稱不會與 [選取的主索引鍵/唯一索引鍵或索引]  清單中的名稱重複。</span><span class="sxs-lookup"><span data-stu-id="fb0ee-127">Make sure that your new name does not duplicate a name in the **Selected Primary/Unique Key or Index** list.</span></span>|  
    |<span data-ttu-id="fb0ee-128">設定叢集選項</span><span class="sxs-lookup"><span data-stu-id="fb0ee-128">Set the clustered option</span></span>|<span data-ttu-id="fb0ee-129">在 [資料表設計工具]  下的方格中，選取 [建立為叢集]  ，然後從下拉式清單中，選擇 [是] 建立叢集索引，或選擇 [否] 建立非叢集索引。</span><span class="sxs-lookup"><span data-stu-id="fb0ee-129">In the grid under **Table Designer**, select **Create As Clustered** and from the dropdown choose Yes to create a clustered index and No to create a nonclustered one.</span></span> <span data-ttu-id="fb0ee-130">每個資料表只能存在一個叢集索引。</span><span class="sxs-lookup"><span data-stu-id="fb0ee-130">Only one clustered index can exist per table.</span></span> <span data-ttu-id="fb0ee-131">如果叢集索引已經存在這個資料表中，您就必須清除原始索引的這項設定。</span><span class="sxs-lookup"><span data-stu-id="fb0ee-131">If a clustered index already exists in this table, you must clear this setting on the original index.</span></span>|  
    |<span data-ttu-id="fb0ee-132">定義填滿因數</span><span class="sxs-lookup"><span data-stu-id="fb0ee-132">Define a fill factor</span></span>|<span data-ttu-id="fb0ee-133">在 **[資料表設計工具]** 底下的方格中，展開 **[填滿規格]** 類別目錄，然後在 **[填滿因數]** 方塊中輸入 0 到 100 之間的整數。</span><span class="sxs-lookup"><span data-stu-id="fb0ee-133">In the grid under **Table Designer**, expand the **Fill Specification** category and type an integer from 0 to 100 in the **Fill Factor** box.</span></span>|  
  
5.  <span data-ttu-id="fb0ee-134">在 [檔案]  功能表上，按一下 [儲存「資料表名稱」]。</span><span class="sxs-lookup"><span data-stu-id="fb0ee-134">On the **File** menu, click **Save**_table name_.</span></span>  
  
##  <a name="to-modify-a-unique-constraint"></a><a name="TsqlProcedure"></a> <span data-ttu-id="fb0ee-135">**修改唯一條件約束**</span><span class="sxs-lookup"><span data-stu-id="fb0ee-135">**To modify a unique constraint**</span></span>  
  
 <span data-ttu-id="fb0ee-136">若要使用 Transact-SQL 來修改 UNIQUE 條件約束，您必須先刪除現有的 UNIQUE 條件約束，然後使用新的定義來重新建立。</span><span class="sxs-lookup"><span data-stu-id="fb0ee-136">To modify a UNIQUE constraint using Transact-SQL, you must first delete the existing UNIQUE constraint and then re-create it with the new definition.</span></span> <span data-ttu-id="fb0ee-137">如需相關資訊，請參閱 [Delete Unique Constraints](delete-unique-constraints.md) 及 [Create Unique Constraints](create-unique-constraints.md)。</span><span class="sxs-lookup"><span data-stu-id="fb0ee-137">For more information, see [Delete Unique Constraints](delete-unique-constraints.md) and [Create Unique Constraints](create-unique-constraints.md).</span></span>  
  
###  <a name="TsqlExample"></a>  
