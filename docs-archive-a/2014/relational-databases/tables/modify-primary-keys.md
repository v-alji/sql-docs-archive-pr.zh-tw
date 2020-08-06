---
title: 修改主索引鍵 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- modifying primary keys
- primary keys [SQL Server], modifying
ms.assetid: 8e2a15ba-1cd1-4408-b860-16c3ee37d635
author: stevestein
ms.author: sstein
ms.openlocfilehash: f24deeac45491f9097d90ee0407464f928a0713b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584339"
---
# <a name="modify-primary-keys"></a><span data-ttu-id="06404-102">修改主索引鍵</span><span class="sxs-lookup"><span data-stu-id="06404-102">Modify Primary Keys</span></span>
  <span data-ttu-id="06404-103">您可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中修改主索引鍵。</span><span class="sxs-lookup"><span data-stu-id="06404-103">You can modify a primary key in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="06404-104">您可以透過變更資料行順序、索引名稱、叢集選項或填滿因數，修改資料表的主索引鍵。</span><span class="sxs-lookup"><span data-stu-id="06404-104">You can modify the primary key of a table by changing the column order, index name, clustered option, or fill factor.</span></span>  
  
 <span data-ttu-id="06404-105">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="06404-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="06404-106">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="06404-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="06404-107">安全性</span><span class="sxs-lookup"><span data-stu-id="06404-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="06404-108">**若要使用下列項目來修改主索引鍵：**</span><span class="sxs-lookup"><span data-stu-id="06404-108">**To modify a primary key, using:**</span></span>  
  
     [<span data-ttu-id="06404-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="06404-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="06404-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="06404-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="06404-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="06404-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="06404-112">Security</span><span class="sxs-lookup"><span data-stu-id="06404-112">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="06404-113">權限</span><span class="sxs-lookup"><span data-stu-id="06404-113">Permissions</span></span>  
 <span data-ttu-id="06404-114">需要資料表的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="06404-114">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="06404-115">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="06404-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-modify-a-primary-key"></a><span data-ttu-id="06404-116">若要修改主索引鍵</span><span class="sxs-lookup"><span data-stu-id="06404-116">To modify a primary key</span></span>  
  
1.  <span data-ttu-id="06404-117">針對您想要修改其主索引鍵的資料表開啟 [資料表設計工具]，在 [資料表設計工具] 中按一下滑鼠右鍵，然後從捷徑功能表選擇 [索引/索引鍵]  。</span><span class="sxs-lookup"><span data-stu-id="06404-117">Open the Table Designer for the table whose primary key you want to modify, right-click in the Table Designer, and choose **Indexes/Keys** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="06404-118">在 [索引/索引鍵]  對話方塊中，從 [選取的主索引鍵/唯一索引鍵或索引]  清單中選取主索引鍵索引。</span><span class="sxs-lookup"><span data-stu-id="06404-118">In the **Indexes/Keys** dialog box, select the primary key index from the **Selected Primary/Unique Key or Index** list.</span></span>  
  
3.  <span data-ttu-id="06404-119">完成下表中的動作：</span><span class="sxs-lookup"><span data-stu-id="06404-119">Complete an action from the following table:</span></span>  
  
    |<span data-ttu-id="06404-120">至</span><span class="sxs-lookup"><span data-stu-id="06404-120">To</span></span>|<span data-ttu-id="06404-121">請依照下列步驟：</span><span class="sxs-lookup"><span data-stu-id="06404-121">Follow these steps</span></span>|  
    |--------|------------------------|  
    |<span data-ttu-id="06404-122">重新命名主索引鍵</span><span class="sxs-lookup"><span data-stu-id="06404-122">Rename the primary key</span></span>|<span data-ttu-id="06404-123">在 [ **名稱** ] 方塊中輸入新的名稱。</span><span class="sxs-lookup"><span data-stu-id="06404-123">Type a new name in the **Name** box.</span></span> <span data-ttu-id="06404-124">確定新名稱不會與 [選取的主索引鍵/唯一索引鍵或索引]  清單中的名稱重複。</span><span class="sxs-lookup"><span data-stu-id="06404-124">Make sure that your new name does not duplicate a name in the **Selected Primary/Unique Key or Index** list.</span></span>|  
    |<span data-ttu-id="06404-125">設定叢集選項</span><span class="sxs-lookup"><span data-stu-id="06404-125">Set the clustered option</span></span>|<span data-ttu-id="06404-126">若要建立主索引鍵的叢集索引，請選取 [建立成 CLUSTERED]  ，然後從下拉式清單方塊中選取選項。</span><span class="sxs-lookup"><span data-stu-id="06404-126">To create a clustered index for the primary key, select **Create as CLUSTERED**, and select the option from the drop-down list box.</span></span> <span data-ttu-id="06404-127">每個資料表只能存在一個叢集索引。</span><span class="sxs-lookup"><span data-stu-id="06404-127">Only one clustered index can exist per table.</span></span> <span data-ttu-id="06404-128">如果您的索引無法使用此選項，則必須先清除現有叢集索引的這個設定。</span><span class="sxs-lookup"><span data-stu-id="06404-128">If this option is not available for your index, you must first clear this setting on the existing clustered index.</span></span><br /><br /> <span data-ttu-id="06404-129">如果沒有選取此選項，就會建立唯一非叢集索引。</span><span class="sxs-lookup"><span data-stu-id="06404-129">If this option is not selected, a unique nonclustered index is created.</span></span>|  
    |<span data-ttu-id="06404-130">定義填滿因數</span><span class="sxs-lookup"><span data-stu-id="06404-130">Define a fill factor</span></span>|<span data-ttu-id="06404-131">展開 **[填滿規格]** 類別目錄，然後在 **[填滿因數]** 方塊中輸入 0 到 100 的整數。</span><span class="sxs-lookup"><span data-stu-id="06404-131">Expand the **Fill Specification** category and type an integer from 0 to 100 in the **Fill factor** box.</span></span> <span data-ttu-id="06404-132">如需填滿因數的詳細資訊以及使用方法，請參閱 [指定索引的填滿因素](../indexes/specify-fill-factor-for-an-index.md)。</span><span class="sxs-lookup"><span data-stu-id="06404-132">For more information about fill factors and their uses, see [Specify Fill Factor for an Index](../indexes/specify-fill-factor-for-an-index.md).</span></span>|  
    |<span data-ttu-id="06404-133">變更資料行順序</span><span class="sxs-lookup"><span data-stu-id="06404-133">Change the column order</span></span>|<span data-ttu-id="06404-134">選取 [資料行]  ，然後按一下屬性右邊的省略符號 **(…)** 。</span><span class="sxs-lookup"><span data-stu-id="06404-134">Select **Columns**, and then click the ellipses **(...)** to the right of the property.</span></span> <span data-ttu-id="06404-135">在  **[索引資料行]** 對話方塊中，從主索引鍵移除資料行。</span><span class="sxs-lookup"><span data-stu-id="06404-135">In the  **Index Columns** dialog box, remove the columns from the primary key.</span></span> <span data-ttu-id="06404-136">然後將資料行以所要的順序加回去。</span><span class="sxs-lookup"><span data-stu-id="06404-136">Then add the columns back in the order you want.</span></span> <span data-ttu-id="06404-137">若要從索引鍵移除資料行，只要從 **[資料行]** 名稱清單中移除資料行名稱即可。</span><span class="sxs-lookup"><span data-stu-id="06404-137">To remove a column from the key, simply remove the column name from the **Column** name list.</span></span>|  
  
4.  <span data-ttu-id="06404-138">在 [檔案]  功能表上，按一下 [儲存「資料表名稱」]。</span><span class="sxs-lookup"><span data-stu-id="06404-138">On the **File** menu, click **Save**_table name_.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="06404-139">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="06404-139">Using Transact-SQL</span></span>  
 <span data-ttu-id="06404-140">**若要修改主索引鍵**</span><span class="sxs-lookup"><span data-stu-id="06404-140">**To modify a primary key**</span></span>  
  
 <span data-ttu-id="06404-141">若要使用 Transact-SQL 來修改 PRIMARY KEY 條件約束，您必須先刪除現有的 PRIMARY KEY 條件約束，然後以新的定義來重新建立。</span><span class="sxs-lookup"><span data-stu-id="06404-141">To modify a PRIMARY KEY constraint using Transact-SQL, you must first delete the existing PRIMARY KEY constraint and then re-create it with the new definition.</span></span> <span data-ttu-id="06404-142">如需相關資訊，請參閱 [Delete Primary Keys](delete-primary-keys.md) 及 [Create Primary Keys](create-primary-keys.md)。</span><span class="sxs-lookup"><span data-stu-id="06404-142">For more information, see [Delete Primary Keys](delete-primary-keys.md) and [Create Primary Keys](create-primary-keys.md).</span></span>  
  
###  <a name="TsqlExample"></a>  
