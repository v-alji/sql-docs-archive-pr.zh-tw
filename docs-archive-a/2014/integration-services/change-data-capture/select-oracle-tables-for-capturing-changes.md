---
title: 選取 Oracle 資料表來擷取變更 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- selOraTabDia
ms.assetid: 2e295dc8-999d-4c4d-96cc-1519674b47a4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e9064789dce83ff7d3917ed026c861743142e048
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704342"
---
# <a name="select-oracle-tables-for-capturing-changes"></a><span data-ttu-id="1b932-102">選取 Oracle 資料表來擷取變更</span><span class="sxs-lookup"><span data-stu-id="1b932-102">Select Oracle Tables for Capturing Changes</span></span>
  <span data-ttu-id="1b932-103">使用此對話方塊來選取 CDC 執行個體中所包含的資料表。</span><span class="sxs-lookup"><span data-stu-id="1b932-103">Use this dialog box to select the tables that are included in the CDC instance.</span></span> <span data-ttu-id="1b932-104">選取的資料表會加入至新增執行個體精靈中 **[選取資料表和資料行]** 頁面的清單中。</span><span class="sxs-lookup"><span data-stu-id="1b932-104">The tables selected are added to the list in the **Select Tables and Columns** page of the New Instance wizard.</span></span> <span data-ttu-id="1b932-105">您可以在此對話方塊中執行下列動作。</span><span class="sxs-lookup"><span data-stu-id="1b932-105">You can do the following in this dialog box.</span></span>  
  
 <span data-ttu-id="1b932-106">根據預設，此對話方塊的資料表清單中不包含任何資料表。</span><span class="sxs-lookup"><span data-stu-id="1b932-106">By default, no tables are included in the list of tables in this dialog box.</span></span> <span data-ttu-id="1b932-107">您可以選取核取方塊資料行頂端的核取方塊，以選取所有資料表或是搜尋特定資料表。</span><span class="sxs-lookup"><span data-stu-id="1b932-107">You can select the check box at the top of the check box column to select all of the tables or search for specific tables.</span></span>  
  
 <span data-ttu-id="1b932-108">**若要搜尋特定資料表**</span><span class="sxs-lookup"><span data-stu-id="1b932-108">**To search for specific tables**</span></span>  
 <span data-ttu-id="1b932-109">依照以下方式輸入搜尋準則，然後按一下 [搜尋]  ：</span><span class="sxs-lookup"><span data-stu-id="1b932-109">Enter search criteria as follows, and then click **Search**:</span></span>  
  
-   <span data-ttu-id="1b932-110">**結構描述**：從清單中選取資料庫結構描述。</span><span class="sxs-lookup"><span data-stu-id="1b932-110">**Schema**: Select a database schema from the list.</span></span> <span data-ttu-id="1b932-111">清單中只會包含具有該結構描述的資料表。</span><span class="sxs-lookup"><span data-stu-id="1b932-111">Only tables that have that schema will be included in the list.</span></span>  
  
-   <span data-ttu-id="1b932-112">**資料表名稱模式**：輸入任何字元字串。</span><span class="sxs-lookup"><span data-stu-id="1b932-112">**Table Name Pattern**: Enter any string of characters.</span></span> <span data-ttu-id="1b932-113">只會顯示包含所輸入之字元字串的資料表。</span><span class="sxs-lookup"><span data-stu-id="1b932-113">Only tables that include the character string entered are displayed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1b932-114">您可以在一個或兩個欄位中輸入準則。</span><span class="sxs-lookup"><span data-stu-id="1b932-114">You can enter criteria in one or both of these fields.</span></span>  
  
-   <span data-ttu-id="1b932-115">**顯示前 1000 個相符的資料表**：預設會選取這個核取方塊。</span><span class="sxs-lookup"><span data-stu-id="1b932-115">**Display first 1000 matching tables**: By default this check box is selected.</span></span> <span data-ttu-id="1b932-116">它會將顯示畫面限制為前 1000 個相符的資料表。</span><span class="sxs-lookup"><span data-stu-id="1b932-116">It limits the display to the first 1000 matching tables.</span></span> <span data-ttu-id="1b932-117">如果您清除此核取方塊，符合準則的所有資料表都會顯示。</span><span class="sxs-lookup"><span data-stu-id="1b932-117">If you clear the check box, all tables that match the criteria are displayed.</span></span> <span data-ttu-id="1b932-118">如果有大量的資料表，則顯示清單可能需要很長的時間。</span><span class="sxs-lookup"><span data-stu-id="1b932-118">If there are a large number of tables, it may take a long time to display the list.</span></span>  
  
 <span data-ttu-id="1b932-119">**若要選取包含在 CDC 執行個體中的資料表**</span><span class="sxs-lookup"><span data-stu-id="1b932-119">**To select tables to include in the CDC instance**</span></span>  
 <span data-ttu-id="1b932-120">按一下您想要包含之任何資料表旁邊的核取方塊，然後按一下 [加入]  。</span><span class="sxs-lookup"><span data-stu-id="1b932-120">Click the check box next to any of the tables you want to include, and then click **Add**.</span></span> <span data-ttu-id="1b932-121">資料表隨即加入至新增執行個體精靈中 **[選取資料表和資料行]** 頁面的清單中。</span><span class="sxs-lookup"><span data-stu-id="1b932-121">The tables are added to the list in the New Instance Wizard **Select Tables and Columns** page.</span></span>  
  
 <span data-ttu-id="1b932-122">按一下 **[關閉]** ，關閉此對話方塊，而不加入任何其他資料表。</span><span class="sxs-lookup"><span data-stu-id="1b932-122">Click **Close** to close the dialog box without adding any additional tables.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1b932-123">如果您選取的資料表包含不支援的資料類型，您會看到錯誤訊息而且不會包含該資料表。</span><span class="sxs-lookup"><span data-stu-id="1b932-123">If you select a table that includes a non-supported data type, you will see an error message and the table will not be included.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b932-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1b932-124">See Also</span></span>  
 <span data-ttu-id="1b932-125">[如何建立 SQL Server 變更資料庫執行個體](how-to-create-the-sql-server-change-database-instance.md) </span><span class="sxs-lookup"><span data-stu-id="1b932-125">[How to Create the SQL Server Change Database Instance](how-to-create-the-sql-server-change-database-instance.md) </span></span>  
 [<span data-ttu-id="1b932-126">選取 Oracle 資料表和資料行</span><span class="sxs-lookup"><span data-stu-id="1b932-126">Select Oracle Tables and Columns</span></span>](select-oracle-tables-and-columns.md)  
  
  
