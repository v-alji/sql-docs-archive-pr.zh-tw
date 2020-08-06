---
title: 將資料表新增至 CDC 執行個體 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- addTabs
ms.assetid: ad260e19-c021-4035-9311-c02fc96ceaea
author: chugugrace
ms.author: chugu
ms.openlocfilehash: edcd84db9e3c464334d407987cb3567f78edd44e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687128"
---
# <a name="add-tables-to-a-cdc-instance"></a><span data-ttu-id="b206c-102">將資料表加入至 CDC 執行個體</span><span class="sxs-lookup"><span data-stu-id="b206c-102">Add Tables to a CDC Instance</span></span>
  <span data-ttu-id="b206c-103">使用 [資料表選取範圍] 對話方塊，將 Oracle 來源中的其他資料表加入至 CDC 執行個體。</span><span class="sxs-lookup"><span data-stu-id="b206c-103">Use the Table Selection dialog box to add additional tables from the Oracle source to the CDC instance.</span></span> <span data-ttu-id="b206c-104">選取的資料表會加入至屬性編輯器中 **[資料表]** 索引標籤的清單。</span><span class="sxs-lookup"><span data-stu-id="b206c-104">The tables selected are added to the list in the **Tables** tab of the Properties editor.</span></span>  
  
 <span data-ttu-id="b206c-105">根據預設，此對話方塊的資料表清單中不包含任何資料表。</span><span class="sxs-lookup"><span data-stu-id="b206c-105">By default, no tables are included in the list of tables in this dialog box.</span></span> <span data-ttu-id="b206c-106">您可以選取 [(全選)]  核取方塊或搜尋特定的資料表。</span><span class="sxs-lookup"><span data-stu-id="b206c-106">You can select the **(Select All)** check box or search for specific tables.</span></span>  
  
 <span data-ttu-id="b206c-107">**若要搜尋特定資料表**</span><span class="sxs-lookup"><span data-stu-id="b206c-107">**To search for specific tables**</span></span>  
 <span data-ttu-id="b206c-108">依照以下方式輸入搜尋準則，然後按一下 [搜尋]  ：</span><span class="sxs-lookup"><span data-stu-id="b206c-108">Enter search criteria as follows, and then click **Search**:</span></span>  
  
-   <span data-ttu-id="b206c-109">**結構描述**：從清單中選取資料庫結構描述。</span><span class="sxs-lookup"><span data-stu-id="b206c-109">**Schema**: Select a database schema from the list.</span></span> <span data-ttu-id="b206c-110">清單中只會包含具有該結構描述的資料表。</span><span class="sxs-lookup"><span data-stu-id="b206c-110">Only tables that have that schema will be included in the list.</span></span>  
  
-   <span data-ttu-id="b206c-111">**資料表名稱模式**：輸入任何字元字串。</span><span class="sxs-lookup"><span data-stu-id="b206c-111">**Table Name Pattern**: Enter any string of characters.</span></span> <span data-ttu-id="b206c-112">只會顯示包含所輸入之字元字串的資料表。</span><span class="sxs-lookup"><span data-stu-id="b206c-112">Only tables that include the character string entered are displayed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b206c-113">您可以在一個或兩個欄位中輸入準則。</span><span class="sxs-lookup"><span data-stu-id="b206c-113">You can enter criteria in one or both of these fields.</span></span>  
  
-   <span data-ttu-id="b206c-114">**顯示前 1000 個相符的資料表**：預設會選取這個核取方塊。</span><span class="sxs-lookup"><span data-stu-id="b206c-114">**Display first 1000 matching tables**: By default this check box is selected.</span></span> <span data-ttu-id="b206c-115">它會將顯示畫面限制為前 1000 個相符的資料表。</span><span class="sxs-lookup"><span data-stu-id="b206c-115">It limits the display to the first 1000 matching tables.</span></span> <span data-ttu-id="b206c-116">如果您清除此核取方塊，符合準則的所有資料表都會顯示。</span><span class="sxs-lookup"><span data-stu-id="b206c-116">If you clear the check box, all tables that match the criteria are displayed.</span></span> <span data-ttu-id="b206c-117">如果有大量的資料表，則顯示清單可能需要很長的時間。</span><span class="sxs-lookup"><span data-stu-id="b206c-117">If there are a large number of tables, it may take a long time to display the list.</span></span>  
  
 <span data-ttu-id="b206c-118">**若要選取包含在 CDC 執行個體中的資料表**</span><span class="sxs-lookup"><span data-stu-id="b206c-118">**To select tables to include in the CDC instance**</span></span>  
 <span data-ttu-id="b206c-119">按一下您想要包含之任何資料表旁邊的核取方塊，然後按一下 [加入]  。</span><span class="sxs-lookup"><span data-stu-id="b206c-119">Click the check box next to any of the tables you want to include, and then click **Add**.</span></span> <span data-ttu-id="b206c-120">資料表隨即加入至新增執行個體精靈中 **[選取資料表和資料行]** 頁面的清單中。</span><span class="sxs-lookup"><span data-stu-id="b206c-120">The tables are added to the list in the New Instance Wizard **Select Tables and Columns** page.</span></span>  
  
 <span data-ttu-id="b206c-121">按一下 **[關閉]** ，關閉此對話方塊，而不加入任何資料表。</span><span class="sxs-lookup"><span data-stu-id="b206c-121">Click **Close** to close the dialog box without adding any tables.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b206c-122">如果您選取的資料表包含不支援的資料類型，您會看到錯誤訊息而且不會包含該資料表。</span><span class="sxs-lookup"><span data-stu-id="b206c-122">If you select a table that includes a non-supported data type, you will see an error message and the table will not be included.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b206c-123">您可以在檢視器中檢視資料表清單。</span><span class="sxs-lookup"><span data-stu-id="b206c-123">You can view the list of tables in the viewer.</span></span> <span data-ttu-id="b206c-124">當使用檢視器時，此資訊是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="b206c-124">When using the viewer the information is read only.</span></span> <span data-ttu-id="b206c-125">檢視器也包括資料表中擷取的資料行清單。</span><span class="sxs-lookup"><span data-stu-id="b206c-125">The viewer also includes a list of the captured columns in the table.</span></span> <span data-ttu-id="b206c-126">如需有關如何存取此檢視器的詳細資訊，請參閱＜ [How to Manage a CDC Instance](manage-a-cdc-instance.md)＞。</span><span class="sxs-lookup"><span data-stu-id="b206c-126">For information on how to access the viewer, see [How to Manage a CDC Instance](manage-a-cdc-instance.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b206c-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b206c-127">See Also</span></span>  
 <span data-ttu-id="b206c-128">[如何編輯 CDC 執行個體屬性](how-to-edit-the-cdc-instance-properties.md) </span><span class="sxs-lookup"><span data-stu-id="b206c-128">[How to Edit the CDC Instance Properties](how-to-edit-the-cdc-instance-properties.md) </span></span>  
 <span data-ttu-id="b206c-129">[How to Manage a CDC Instance](manage-a-cdc-instance.md) </span><span class="sxs-lookup"><span data-stu-id="b206c-129">[How to Manage a CDC Instance](manage-a-cdc-instance.md) </span></span>  
 [<span data-ttu-id="b206c-130">選取 Oracle 資料表以擷取變更</span><span class="sxs-lookup"><span data-stu-id="b206c-130">Select Oracle Tables for Capturing Changes</span></span>](select-oracle-tables-for-capturing-changes.md)  
  
  
