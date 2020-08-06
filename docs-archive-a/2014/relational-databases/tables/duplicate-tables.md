---
title: 複製資料表 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- copying tables
- tables [SQL Server], duplicating
- duplicating tables
- table copying [SQL Server]
ms.assetid: c6b07423-d1e5-4e5e-8681-5088921f5df3
author: stevestein
ms.author: sstein
ms.openlocfilehash: 793a38416f86a5b43a3e3bb2420127d7acf2af1f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593918"
---
# <a name="duplicate-tables"></a><span data-ttu-id="5c1de-102">複製資料表</span><span class="sxs-lookup"><span data-stu-id="5c1de-102">Duplicate Tables</span></span>
  <span data-ttu-id="5c1de-103">您可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 來建立新的資料表，然後從現有的資料表複製資料行資訊，藉以在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 中複製現有的資料表。</span><span class="sxs-lookup"><span data-stu-id="5c1de-103">You can duplicate an existing table in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)] by creating a new table and then copying column information from an existing table.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="5c1de-104">這個作業只會複製資料表的結構，不會複製任何資料表資料列。</span><span class="sxs-lookup"><span data-stu-id="5c1de-104">This operation duplicates only the structure of a table; it does not duplicate any table rows.</span></span>  
  
 <span data-ttu-id="5c1de-105">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="5c1de-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="5c1de-106">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="5c1de-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="5c1de-107">安全性</span><span class="sxs-lookup"><span data-stu-id="5c1de-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="5c1de-108">**若要使用下列項目來複製資料表：**</span><span class="sxs-lookup"><span data-stu-id="5c1de-108">**To duplicate a table, using:**</span></span>  
  
     [<span data-ttu-id="5c1de-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="5c1de-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="5c1de-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="5c1de-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="5c1de-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="5c1de-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="5c1de-112">Security</span><span class="sxs-lookup"><span data-stu-id="5c1de-112">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="5c1de-113">權限</span><span class="sxs-lookup"><span data-stu-id="5c1de-113">Permissions</span></span>  
 <span data-ttu-id="5c1de-114">需要目的地資料庫中的 CREATE TABLE 權限。</span><span class="sxs-lookup"><span data-stu-id="5c1de-114">Requires CREATE TABLE permission in the destination database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="5c1de-115">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="5c1de-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-duplicate-a-table"></a><span data-ttu-id="5c1de-116">若要複製資料表</span><span class="sxs-lookup"><span data-stu-id="5c1de-116">To duplicate a table</span></span>  
  
1.  <span data-ttu-id="5c1de-117">請確定已連接至要建立資料表的資料庫，以及已在 [物件總管] 中選取資料庫。</span><span class="sxs-lookup"><span data-stu-id="5c1de-117">Make sure you are connected to the database in which you want to create the table and that the database is selected in Object Explorer.</span></span>  
  
2.  <span data-ttu-id="5c1de-118">在 [物件總管] 中，以滑鼠右鍵按一下 [資料表]  ，再按一下 [新增資料表]  。</span><span class="sxs-lookup"><span data-stu-id="5c1de-118">In Object Explorer, right-click **Tables** and click **New Table**.</span></span>  
  
3.  <span data-ttu-id="5c1de-119">在 [物件總管] 中，以滑鼠右鍵按一下您要複製的資料表，然後按一下 [設計]  。</span><span class="sxs-lookup"><span data-stu-id="5c1de-119">In Object Explorer right-click the table you want to copy and click **Design**.</span></span>  
  
4.  <span data-ttu-id="5c1de-120">選取現有資料表中的資料行，再從 **[編輯]** 功能表中按一下 **[複製]** 。</span><span class="sxs-lookup"><span data-stu-id="5c1de-120">Select the columns in the existing table and, from the **Edit** menu, click **Copy**.</span></span>  
  
5.  <span data-ttu-id="5c1de-121">切換回新的資料表，並選取第一列。</span><span class="sxs-lookup"><span data-stu-id="5c1de-121">Switch back to the new table and select the first row.</span></span>  
  
6.  <span data-ttu-id="5c1de-122">從 **[編輯]** 功能表中，按一下 **[貼上]** 。</span><span class="sxs-lookup"><span data-stu-id="5c1de-122">From the **Edit** menu, click **Paste**.</span></span>  
  
7.  <span data-ttu-id="5c1de-123">從 [檔案]  功能表中，按一下 [儲存]  _table name_。</span><span class="sxs-lookup"><span data-stu-id="5c1de-123">From the **File** menu, click **Save**_table name_.</span></span>  
  
8.  <span data-ttu-id="5c1de-124">在 **[選擇名稱]** 對話方塊中，輸入新資料表的名稱，並按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="5c1de-124">In the **Choose Name** dialog box, type a name for the new table and click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="5c1de-125">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="5c1de-125">Using Transact-SQL</span></span>  
  
#### <a name="to-duplicate-a-table-in-query-editor"></a><span data-ttu-id="5c1de-126">若要在查詢編輯器中複製資料表</span><span class="sxs-lookup"><span data-stu-id="5c1de-126">To duplicate a table in Query Editor</span></span>  
  
1.  <span data-ttu-id="5c1de-127">請確定已連接至要建立資料表的資料庫，以及已在 [物件總管] 中選取資料庫。</span><span class="sxs-lookup"><span data-stu-id="5c1de-127">Make sure you are connected to the database in which you want to create the table and that the database is selected in Object Explorer.</span></span>  
  
2.  <span data-ttu-id="5c1de-128">以滑鼠右鍵按一下您想要複製的資料表，並依序指向 [編寫資料表的指令碼為]  和 [CREATE 至]  ，然後選取 [新增查詢編輯器視窗]  。</span><span class="sxs-lookup"><span data-stu-id="5c1de-128">Right-click the table you wish to duplicate, point to **Script Table as**, then point to **CREATE to**, and then select **New Query Editor Window**.</span></span>  
  
3.  <span data-ttu-id="5c1de-129">變更資料表的名稱。</span><span class="sxs-lookup"><span data-stu-id="5c1de-129">Change the name of the table.</span></span>  
  
4.  <span data-ttu-id="5c1de-130">移除新資料表不需要的任何資料行。</span><span class="sxs-lookup"><span data-stu-id="5c1de-130">Remove any columns that are not needed in the new table.</span></span>  
  
5.  <span data-ttu-id="5c1de-131">按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="5c1de-131">Click **Execute**.</span></span>  
  
  
