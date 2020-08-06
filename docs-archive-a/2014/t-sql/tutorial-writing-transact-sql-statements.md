---
title: 教學課程：撰寫國際性通用的 Transact-SQL 陳述式 | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: t-sql
ms.topic: conceptual
helpviewer_keywords:
- Transact-SQL statements, tutorials
- Transact-SQL tutorials
- tutorials [Transact-SQL]
ms.assetid: 2addc9be-67d0-423d-a457-192fe9d7d058
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: ac190d6099bca1a38ca2f286e6ce048fe5322e2a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708862"
---
# <a name="tutorial-writing-transact-sql-statements"></a><span data-ttu-id="cde48-102">教學課程：撰寫國際性通用的 Transact-SQL 陳述式</span><span class="sxs-lookup"><span data-stu-id="cde48-102">Tutorial: Writing Transact-SQL Statements</span></span>
  <span data-ttu-id="cde48-103">歡迎使用「撰寫 [!INCLUDE[tsql](../includes/tsql-md.md)] 陳述式」教學課程。</span><span class="sxs-lookup"><span data-stu-id="cde48-103">Welcome to the Writing [!INCLUDE[tsql](../includes/tsql-md.md)] Statements tutorial.</span></span> <span data-ttu-id="cde48-104">本教學課程的主要對象是撰寫 SQL 陳述式的新手，</span><span class="sxs-lookup"><span data-stu-id="cde48-104">This tutorial is intended for users who are new to writing SQL statements.</span></span> <span data-ttu-id="cde48-105">會透過檢閱一些建立資料表及插入資料的基本陳述式，協助新手上路。</span><span class="sxs-lookup"><span data-stu-id="cde48-105">It will help new users get started by reviewing some basic statements for creating tables and inserting data.</span></span> <span data-ttu-id="cde48-106">本教學課程採用 [!INCLUDE[tsql](../includes/tsql-md.md)]，是 SQL 標準的 [!INCLUDE[msCoName](../includes/msconame-md.md)] 實作。</span><span class="sxs-lookup"><span data-stu-id="cde48-106">This tutorial uses [!INCLUDE[tsql](../includes/tsql-md.md)], the [!INCLUDE[msCoName](../includes/msconame-md.md)] implementation of the SQL standard.</span></span> <span data-ttu-id="cde48-107">本教學課程的目的是用來概述 [!INCLUDE[tsql](../includes/tsql-md.md)] 語言，而非用來取代 [!INCLUDE[tsql](../includes/tsql-md.md)] 類別。</span><span class="sxs-lookup"><span data-stu-id="cde48-107">This tutorial is intended as a brief introduction to the [!INCLUDE[tsql](../includes/tsql-md.md)] language and not as a replacement for a [!INCLUDE[tsql](../includes/tsql-md.md)] class.</span></span> <span data-ttu-id="cde48-108">在本教學課程中的陳述式是有意經過簡化的，並無意呈現一般實際資料庫中所遇到的複雜問題。</span><span class="sxs-lookup"><span data-stu-id="cde48-108">The statements in this tutorial are intentionally simple, and are not meant to represent the complexity found in a typical production database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cde48-109">資料庫的新手通常會發現使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 處理 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 反而比撰寫 [!INCLUDE[tsql](../includes/tsql-md.md)] 陳述式更容易。</span><span class="sxs-lookup"><span data-stu-id="cde48-109">Novice users of databases will usually find it easier to work with [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] by using [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], instead of writing [!INCLUDE[tsql](../includes/tsql-md.md)] statements.</span></span>  
  
## <a name="finding-more-information"></a><span data-ttu-id="cde48-110">尋找詳細資訊</span><span class="sxs-lookup"><span data-stu-id="cde48-110">Finding More Information</span></span>  
 <span data-ttu-id="cde48-111">若要尋找任何特定陳述式的詳細資訊，請在《SQL Server 線上叢書》中依名稱搜尋陳述式，或是使用 [內容] 瀏覽 [Transact-SQL 參考 &#40;Database Engine&#41;](/sql/t-sql/language-reference) 底下依字母順序排列的 1,800 個語言元素。</span><span class="sxs-lookup"><span data-stu-id="cde48-111">To find more information about any specific statement, either search for the statement by name in SQL Server Books Online, or use the Contents to browse the 1,800 language elements listed alphabetically under [Transact-SQL Reference &#40;Database Engine&#41;](/sql/t-sql/language-reference).</span></span> <span data-ttu-id="cde48-112">此外，搜尋與您有興趣的主題內容相關的關鍵字，也是另一種找出資訊的不錯方式。</span><span class="sxs-lookup"><span data-stu-id="cde48-112">Another good strategy for finding information is to search for key words that are related to the subject matter you are interested in.</span></span> <span data-ttu-id="cde48-113">例如，您想要知道如何傳回一部分的日期 (如月份)，您可以搜尋 **dates [SQL Server]** 的索引，然後選取 **dateparts**，</span><span class="sxs-lookup"><span data-stu-id="cde48-113">For example, if you want to know how to return a part of a date (such as the month), search the index for **dates [SQL Server]**, and then select **dateparts**.</span></span> <span data-ttu-id="cde48-114">即會帶您前往 [DATEPART &#40;Transact-SQL&#41;](/sql/t-sql/functions/datepart-transact-sql) 主題。</span><span class="sxs-lookup"><span data-stu-id="cde48-114">This takes you to the topic [DATEPART &#40;Transact-SQL&#41;](/sql/t-sql/functions/datepart-transact-sql).</span></span> <span data-ttu-id="cde48-115">例如若要找出如何使用字串，您可以搜尋 **字串函數**，</span><span class="sxs-lookup"><span data-stu-id="cde48-115">As another example, to find out how to work with strings, search for **string functions**.</span></span> <span data-ttu-id="cde48-116">即會帶您前往[字串函數 &#40;Transact-SQL&#41;](/sql/t-sql/functions/string-functions-transact-sql) 主題。</span><span class="sxs-lookup"><span data-stu-id="cde48-116">This takes you to the topic [String Functions &#40;Transact-SQL&#41;](/sql/t-sql/functions/string-functions-transact-sql).</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="cde48-117">學習內容</span><span class="sxs-lookup"><span data-stu-id="cde48-117">What You Will Learn</span></span>  
 <span data-ttu-id="cde48-118">本教學課程會示範如何建立資料庫、在資料庫中建立資料表、插入資料至資料表、更新資料、讀取資料、刪除資料，然後刪除資料表。</span><span class="sxs-lookup"><span data-stu-id="cde48-118">This tutorial shows you how to create a database, create a table in the database, insert data into the table, update the data, read the data, delete the data, and then delete the table.</span></span> <span data-ttu-id="cde48-119">您將建立檢視和預存程序，並將使用者設定到資料庫及資料。</span><span class="sxs-lookup"><span data-stu-id="cde48-119">You will create views and stored procedures and configure a user to the database and the data.</span></span>  
  
 <span data-ttu-id="cde48-120">本教學課程分成三個課程：</span><span class="sxs-lookup"><span data-stu-id="cde48-120">This tutorial is divided into three lessons:</span></span>  
  
 [<span data-ttu-id="cde48-121">課程 1：建立資料庫物件</span><span class="sxs-lookup"><span data-stu-id="cde48-121">Lesson 1: Creating Database Objects</span></span>](lesson-1-creating-database-objects.md)  
 <span data-ttu-id="cde48-122">在這一課，您會建立資料庫、在資料庫中建立資料表、插入資料至資料表、更新資料以及讀取資料。</span><span class="sxs-lookup"><span data-stu-id="cde48-122">In this lesson, you create a database, create a table in the database, insert data into the table, update the data, and read the data.</span></span>  
  
 [<span data-ttu-id="cde48-123">課程 2：設定資料庫物件的權限</span><span class="sxs-lookup"><span data-stu-id="cde48-123">Lesson 2: Configuring Permissions on Database Objects</span></span>](lesson-2-configuring-permissions-on-database-objects.md)  
 <span data-ttu-id="cde48-124">在這一課，您會建立登入及使用者，</span><span class="sxs-lookup"><span data-stu-id="cde48-124">In this lesson, you create a login and user.</span></span> <span data-ttu-id="cde48-125">也會建立檢視和預存程序，然後將使用者權授與預存程序。</span><span class="sxs-lookup"><span data-stu-id="cde48-125">You will also create a view and a stored procedure, and then grant the user permission to the stored procedure.</span></span>  
  
 [<span data-ttu-id="cde48-126">課程 3：刪除資料庫物件</span><span class="sxs-lookup"><span data-stu-id="cde48-126">Lesson 3: Deleting Database Objects</span></span>](lesson-3-1-deleting-database-objects.md)  
 <span data-ttu-id="cde48-127">在這一課，您會移除資料的存取、從資料表中刪除資料、刪除資料表，最後刪除資料庫。</span><span class="sxs-lookup"><span data-stu-id="cde48-127">In this lesson, you remove access to data, delete data from a table, delete the table, and then delete the database.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cde48-128">需求</span><span class="sxs-lookup"><span data-stu-id="cde48-128">Requirements</span></span>  
 <span data-ttu-id="cde48-129">為了完成本教學課程，您並不需要精通 SQL 語言，但必須了解基本資料庫概念 (如資料表)。</span><span class="sxs-lookup"><span data-stu-id="cde48-129">To complete this tutorial, you do not have to know the SQL language, but you should understand basic database concepts such as tables.</span></span> <span data-ttu-id="cde48-130">在進行本教學課程期間，您將建立資料庫以及建立 Windows 使用者。</span><span class="sxs-lookup"><span data-stu-id="cde48-130">During this tutorial, you will create a database and create a Windows user.</span></span> <span data-ttu-id="cde48-131">這些工作需要高層權限，因此您必須以系統管理員的身份登入電腦。</span><span class="sxs-lookup"><span data-stu-id="cde48-131">These tasks require a high level of permissions; therefore, you should log in to the computer as an administrator.</span></span>  
  
 <span data-ttu-id="cde48-132">另外，系統必須有安裝下列程式：</span><span class="sxs-lookup"><span data-stu-id="cde48-132">Your system must have the following installed:</span></span>  
  
-   <span data-ttu-id="cde48-133">任何版本的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="cde48-133">Any edition of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="cde48-134">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 或 Management Studio Express。</span><span class="sxs-lookup"><span data-stu-id="cde48-134">Either [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] or Management Studio Express.</span></span>  
  
-   <span data-ttu-id="cde48-135">Internet Explorer 6 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="cde48-135">Internet Explorer 6 or later.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cde48-136">當您查看教學課程時，建議您在檔檢視器工具列上加入 [**下一個]** 和 [**上一個**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="cde48-136">When you review the tutorials, we recommend that you add the **Next** and **Previous** buttons to the document viewer toolbar.</span></span>  
  
  
