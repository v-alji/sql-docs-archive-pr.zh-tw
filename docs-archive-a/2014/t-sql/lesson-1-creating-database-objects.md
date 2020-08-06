---
title: 課程 1：建立資料庫物件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: t-sql
ms.topic: conceptual
ms.assetid: 9fb8656b-0e4e-4ada-b404-4db4d3eea995
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 172fdbcaedc10f9c359befd48ed09ec825aea9bc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704597"
---
# <a name="lesson-1-creating-database-objects"></a><span data-ttu-id="c5636-102">第 1 課：建立資料庫物件</span><span class="sxs-lookup"><span data-stu-id="c5636-102">Lesson 1: Creating Database Objects</span></span>
  <span data-ttu-id="c5636-103">這一課會示範如何建立資料庫、在資料庫中建立資料表，然後在資料表中存取和變更資料。</span><span class="sxs-lookup"><span data-stu-id="c5636-103">This lesson shows you how to create a database, create a table in the database, and then access and change the data in the table.</span></span> <span data-ttu-id="c5636-104">因為這一課是使用 [!INCLUDE[tsql](../includes/tsql-md.md)]的簡介，所以並不會使用或描述這些陳述式所能使用的許多選項。</span><span class="sxs-lookup"><span data-stu-id="c5636-104">Because this lesson is an introduction to using [!INCLUDE[tsql](../includes/tsql-md.md)], it does not use or describe the many options that are available for these statements.</span></span>  
  
 [!INCLUDE[tsql](../includes/tsql-md.md)] <span data-ttu-id="c5636-105">撰寫陳述式並且提交給 [!INCLUDE[ssDE](../includes/ssde-md.md)] 可以採用下列方式：</span><span class="sxs-lookup"><span data-stu-id="c5636-105">statements can be written and submitted to the [!INCLUDE[ssDE](../includes/ssde-md.md)] in the following ways:</span></span>  
  
-   <span data-ttu-id="c5636-106">使用 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="c5636-106">By using [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="c5636-107">這個教學課程會假設您使用 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]，但是您也可以使用 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] Express，這個版本可以從 [Microsoft 下載中心](https://www.microsoft.com/download/details.aspx?id=14630)免費下載。</span><span class="sxs-lookup"><span data-stu-id="c5636-107">This tutorial assumes that you are using [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], but you can also use [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] Express, which is available as a free download from the [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=14630).</span></span>  
  
-   <span data-ttu-id="c5636-108">使用 [sqlcmd 公用程式](../tools/sqlcmd-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="c5636-108">By using the [sqlcmd utility](../tools/sqlcmd-utility.md).</span></span>  
  
-   <span data-ttu-id="c5636-109">從您建立的應用程式連接。</span><span class="sxs-lookup"><span data-stu-id="c5636-109">By connecting from an application that you create.</span></span>  
  
 <span data-ttu-id="c5636-110">不論您提交程式碼陳述式的方式為何，這個程式碼在 [!INCLUDE[ssDE](../includes/ssde-md.md)] 上都會以相同的方式和相同的權限來執行。</span><span class="sxs-lookup"><span data-stu-id="c5636-110">The code executes on the [!INCLUDE[ssDE](../includes/ssde-md.md)] in the same way and with the same permissions, regardless of how you submit the code statements.</span></span>  
  
 <span data-ttu-id="c5636-111">若要在 [!INCLUDE[tsql](../includes/tsql-md.md)] 中執行 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]陳述式，請開啟 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 並且連接到 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="c5636-111">To run [!INCLUDE[tsql](../includes/tsql-md.md)] statements in [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], open [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] and connect to an instance of the [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)].</span></span>  
  
 <span data-ttu-id="c5636-112">這個課程包含下列主題：</span><span class="sxs-lookup"><span data-stu-id="c5636-112">This lesson contains the following topics:</span></span>  
  
-   [<span data-ttu-id="c5636-113">建立資料庫 &#40;教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="c5636-113">Creating a Database &#40;Tutorial&#41;</span></span>](lesson-1-1-creating-a-database.md)  
  
-   [<span data-ttu-id="c5636-114">建立資料表 &#40;教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="c5636-114">Creating a Table &#40;Tutorial&#41;</span></span>](lesson-1-2-creating-a-table.md)  
  
-   [<span data-ttu-id="c5636-115">在資料表中插入及更新資料 &#40;教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="c5636-115">Inserting and Updating Data in a Table &#40;Tutorial&#41;</span></span>](lesson-1-3-inserting-and-updating-data-in-a-table.md)  
  
-   [<span data-ttu-id="c5636-116">讀取資料表的資料 &#40;教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="c5636-116">Reading the Data in a Table &#40;Tutorial&#41;</span></span>](lesson-1-4-reading-the-data-in-a-table.md)  
  
-   [<span data-ttu-id="c5636-117">摘要：建立資料庫物件</span><span class="sxs-lookup"><span data-stu-id="c5636-117">Summary: Creating Database Objects</span></span>](lesson-1-5-summary-creating-database-objects.md)  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="c5636-118">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="c5636-118">Next Task in Lesson</span></span>  
 [<span data-ttu-id="c5636-119">建立資料庫 &#40;教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="c5636-119">Creating a Database &#40;Tutorial&#41;</span></span>](lesson-1-1-creating-a-database.md)  
  
  
