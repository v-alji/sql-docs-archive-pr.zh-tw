---
title: " (設計工具的選項-資料表和資料庫設計工具頁面) |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Designers.Table_Designer
ms.assetid: b43f4b97-17b9-4004-a824-f77b9e145741
author: stevestein
ms.author: sstein
ms.openlocfilehash: d8a1218b4ea1ae9c6f9cf734bb33a2a4bebcb167
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598104"
---
# <a name="options-designers-table-and-database-designers-page"></a><span data-ttu-id="773d8-102"> (設計工具的選項-資料表和資料庫設計工具頁面) </span><span class="sxs-lookup"><span data-stu-id="773d8-102">Options (Designers-Table and Database Designers Page)</span></span>
  <span data-ttu-id="773d8-103">使用此頁面來決定設計師的預設行為。</span><span class="sxs-lookup"><span data-stu-id="773d8-103">Use this page to determine the default behavior of the designer.</span></span> <span data-ttu-id="773d8-104">若要存取設定，請在 [工具]  功能表上按一下 [選項]  、展開 [設計工具]  資料夾，然後按一下 [資料表設計工具]  。</span><span class="sxs-lookup"><span data-stu-id="773d8-104">To access the settings, on the **Tools** menu, click **Options**, expand the **Designers** folder, and click **Table Designer**.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="773d8-105">UI 元素清單</span><span class="sxs-lookup"><span data-stu-id="773d8-105">UI element list</span></span>  
 <span data-ttu-id="773d8-106">**覆寫資料表設計師更新的連接字串逾時值**</span><span class="sxs-lookup"><span data-stu-id="773d8-106">**Override connection string time-out value for table designer updates**</span></span>  
 <span data-ttu-id="773d8-107">允許針對資料表設計師之動作設定新的逾時值。</span><span class="sxs-lookup"><span data-stu-id="773d8-107">Permits a new time-out value to be set for the actions of the table designer.</span></span> <span data-ttu-id="773d8-108">當資料表設計師影響大型資料表而需要額外的時間來完成資料表修改時，這就非常有用。</span><span class="sxs-lookup"><span data-stu-id="773d8-108">This can be useful when the table designer affects a large table and requires extra time to complete the table modification.</span></span>  
  
 <span data-ttu-id="773d8-109">**交易逾時設定值**</span><span class="sxs-lookup"><span data-stu-id="773d8-109">**Transaction time-out after**</span></span>  
 <span data-ttu-id="773d8-110">設定資料表設計師的逾時值。</span><span class="sxs-lookup"><span data-stu-id="773d8-110">Sets a time-out value for the table designer.</span></span>  
  
 <span data-ttu-id="773d8-111">**自動產生變更指令碼**</span><span class="sxs-lookup"><span data-stu-id="773d8-111">**Auto generate change scripts**</span></span>  
 <span data-ttu-id="773d8-112">自動建立指令碼以實作資料表設計師中所定義的變更。</span><span class="sxs-lookup"><span data-stu-id="773d8-112">Automatically creates a script to implement the changes defined in the table designer.</span></span>  
  
 <span data-ttu-id="773d8-113">**針對 Null 主索引鍵產生警告**</span><span class="sxs-lookup"><span data-stu-id="773d8-113">**Warn on null primary keys**</span></span>  
 <span data-ttu-id="773d8-114">當選取作為主索引鍵的欄位可以包含 Null 值時，提供警告對話方塊。</span><span class="sxs-lookup"><span data-stu-id="773d8-114">Provides a warning dialog box when a field that is selected for a primary key can contain null values.</span></span>  
  
 <span data-ttu-id="773d8-115">**警告差異偵測**</span><span class="sxs-lookup"><span data-stu-id="773d8-115">**Warn about difference detection**</span></span>  
 <span data-ttu-id="773d8-116">如果核取這個方塊，則當儲存變更時，有一個訊息方塊會列出您所進行之變更與另一位使用者所進行之變更的任何衝突。</span><span class="sxs-lookup"><span data-stu-id="773d8-116">If you check this box, when you save the changes, a message box will list any conflicts between your changes and changes that were made by another user.</span></span>  
  
 <span data-ttu-id="773d8-117">**警告受影響資料表**</span><span class="sxs-lookup"><span data-stu-id="773d8-117">**Warn about tables affected**</span></span>  
 <span data-ttu-id="773d8-118">提供一個警告對話方塊，其中會列出受此動作影響的資料表並提示確認。</span><span class="sxs-lookup"><span data-stu-id="773d8-118">Provides a warning dialog box that lists the tables to be affected by the action and prompts for confirmation.</span></span>  
  
 <span data-ttu-id="773d8-119">**防止儲存需要資料表重建的變更**</span><span class="sxs-lookup"><span data-stu-id="773d8-119">**Prevent saving changes that require table re-creation**</span></span>  
 <span data-ttu-id="773d8-120">便免使用者進行需要資料表重建的變更。</span><span class="sxs-lookup"><span data-stu-id="773d8-120">Prevents a user from making changes that require re-creating the table.</span></span> <span data-ttu-id="773d8-121">下列動作可能需要重新建立資料表：</span><span class="sxs-lookup"><span data-stu-id="773d8-121">The following actions might require a table to be re-created:</span></span>  
  
-   <span data-ttu-id="773d8-122">將新的資料行加入資料表的中間</span><span class="sxs-lookup"><span data-stu-id="773d8-122">Adding a new column to the middle of the table</span></span>  
  
-   <span data-ttu-id="773d8-123">卸除資料行</span><span class="sxs-lookup"><span data-stu-id="773d8-123">Dropping a column</span></span>  
  
-   <span data-ttu-id="773d8-124">變更資料行的 Null 屬性</span><span class="sxs-lookup"><span data-stu-id="773d8-124">Changing column nullability</span></span>  
  
-   <span data-ttu-id="773d8-125">變更資料行的順序</span><span class="sxs-lookup"><span data-stu-id="773d8-125">Changing the order of the columns</span></span>  
  
-   <span data-ttu-id="773d8-126">變更資料行的資料類型</span><span class="sxs-lookup"><span data-stu-id="773d8-126">Changing the data type of a column</span></span>  
  
 <span data-ttu-id="773d8-127">**預設資料表檢視**</span><span class="sxs-lookup"><span data-stu-id="773d8-127">**Default table view**</span></span>  
 <span data-ttu-id="773d8-128">選取在設計師中查看資料表的方式：</span><span class="sxs-lookup"><span data-stu-id="773d8-128">Select the way you want to see tables in the designers:</span></span>  
  
-   <span data-ttu-id="773d8-129">**Standard**</span><span class="sxs-lookup"><span data-stu-id="773d8-129">**Standard**</span></span>  
  
     <span data-ttu-id="773d8-130">顯示資料表標頭、所有資料行名稱、資料類型以及允許 Null 設定。</span><span class="sxs-lookup"><span data-stu-id="773d8-130">Shows the table header, all column names, data types, and the Allow Nulls setting.</span></span>  
  
-   <span data-ttu-id="773d8-131">**資料行名稱**</span><span class="sxs-lookup"><span data-stu-id="773d8-131">**Column Names**</span></span>  
  
     <span data-ttu-id="773d8-132">顯示資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="773d8-132">Shows the column names.</span></span>  
  
-   <span data-ttu-id="773d8-133">**索引鍵**</span><span class="sxs-lookup"><span data-stu-id="773d8-133">**Key**</span></span>  
  
     <span data-ttu-id="773d8-134">顯示資料表標頭與主索引鍵資料行。</span><span class="sxs-lookup"><span data-stu-id="773d8-134">Shows the table header and the primary key columns.</span></span>  
  
-   <span data-ttu-id="773d8-135">**僅顯示名稱**</span><span class="sxs-lookup"><span data-stu-id="773d8-135">**Name Only**</span></span>  
  
     <span data-ttu-id="773d8-136">只顯示具有其名稱的資料表標頭。</span><span class="sxs-lookup"><span data-stu-id="773d8-136">Shows only the table header with it's name.</span></span>  
  
-   <span data-ttu-id="773d8-137">**Custom**</span><span class="sxs-lookup"><span data-stu-id="773d8-137">**Custom**</span></span>  
  
     <span data-ttu-id="773d8-138">允許您選擇要檢視的資料行。</span><span class="sxs-lookup"><span data-stu-id="773d8-138">Allows you to choose which columns to view.</span></span>  
  
 <span data-ttu-id="773d8-139">**在新圖表上啟動加入資料表對話方塊**</span><span class="sxs-lookup"><span data-stu-id="773d8-139">**Launch add table dialog on new diagram**</span></span>  
 <span data-ttu-id="773d8-140">在開啟設計師時自動開啟 [新增資料表]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="773d8-140">Automatically opens the **Add Table** dialog box when the designers open.</span></span>  
  
  
