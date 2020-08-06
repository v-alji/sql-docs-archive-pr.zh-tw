---
title: 建立資料庫 (SQL Server 匯入和匯出精靈) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.createdatabase.f1
ms.assetid: 56a8a79f-086c-4bdc-8888-0045bb4b0cbf
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 617b3fe10a17ae2d8659b51e85cdb3fed4470506
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597938"
---
# <a name="create-database-sql-server-import-and-export-wizard"></a><span data-ttu-id="8524c-102">建立資料庫 (SQL Server 匯入和匯出精靈)</span><span class="sxs-lookup"><span data-stu-id="8524c-102">Create Database (SQL Server Import and Export Wizard)</span></span>
  <span data-ttu-id="8524c-103">使用 [**建立資料庫**] 頁面，即可為目的地檔案定義新的資料庫。</span><span class="sxs-lookup"><span data-stu-id="8524c-103">Use the **Create Database** page to define a new database for a destination file.</span></span>  
  
 <span data-ttu-id="8524c-104">這個頁面提供建立新資料庫之可用選項的子集。</span><span class="sxs-lookup"><span data-stu-id="8524c-104">This page offers a subset of the available options for creating a new database.</span></span> <span data-ttu-id="8524c-105">若要查看所有選項，請使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="8524c-105">To view all the options, use [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="8524c-106">若要深入瞭解此嚮導，請參閱[SQL Server 匯入和匯出嚮導](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="8524c-106">To learn more about this wizard, see [SQL Server Import and Export Wizard](import-and-export-data-with-the-sql-server-import-and-export-wizard.md).</span></span> <span data-ttu-id="8524c-107">若要瞭解啟動精靈的選項，以及成功執行嚮導所需的許可權，請參閱[執行 SQL Server 匯入和匯出嚮導](start-the-sql-server-import-and-export-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="8524c-107">To learn about the options for starting the wizard, and about the permissions required to run the wizard successfully, see [Run the SQL Server Import and Export Wizard](start-the-sql-server-import-and-export-wizard.md).</span></span>  
  
 <span data-ttu-id="8524c-108">「SQL Server 匯入和匯出精靈」的用途在於將資料從來源複製到目的地。</span><span class="sxs-lookup"><span data-stu-id="8524c-108">The purpose of the SQL Server Import and Export Wizard is to copy data from a source to a destination.</span></span> <span data-ttu-id="8524c-109">這個精靈也可以為您建立目的地資料庫和目的地資料表。</span><span class="sxs-lookup"><span data-stu-id="8524c-109">The wizard can also create a destination database and destination tables for you.</span></span> <span data-ttu-id="8524c-110">不過，如果您必須複製多個資料庫或資料表，或複製其他種類的資料庫物件，則應該改用「複製資料庫精靈」。</span><span class="sxs-lookup"><span data-stu-id="8524c-110">However, if you have to copy multiple databases or tables, or other kinds of database objects, you should use the Copy Database Wizard instead.</span></span> <span data-ttu-id="8524c-111">如需詳細資訊，請參閱 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="8524c-111">For more information, see [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="8524c-112">選項。</span><span class="sxs-lookup"><span data-stu-id="8524c-112">Options</span></span>  
 <span data-ttu-id="8524c-113">**名稱**</span><span class="sxs-lookup"><span data-stu-id="8524c-113">**Name**</span></span>  
 <span data-ttu-id="8524c-114">為目的地 SQL Server 資料庫提供唯一的名稱。</span><span class="sxs-lookup"><span data-stu-id="8524c-114">Provide a unique name for the destination SQL Server database.</span></span> <span data-ttu-id="8524c-115">當您命名此資料庫時，請確認有遵循 SQL Server 慣例。</span><span class="sxs-lookup"><span data-stu-id="8524c-115">Make sure that you follow SQL Server conventions when you name this database.</span></span>  
  
 <span data-ttu-id="8524c-116">**資料檔名稱**</span><span class="sxs-lookup"><span data-stu-id="8524c-116">**Data file name**</span></span>  
 <span data-ttu-id="8524c-117">檢視資料檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="8524c-117">View the name of the data file.</span></span> <span data-ttu-id="8524c-118">這是從您在先前提供的資料庫名稱衍生的。</span><span class="sxs-lookup"><span data-stu-id="8524c-118">This is derived from the database name you provided earlier.</span></span>  
  
 <span data-ttu-id="8524c-119">**記錄檔名稱**</span><span class="sxs-lookup"><span data-stu-id="8524c-119">**Log file name**</span></span>  
 <span data-ttu-id="8524c-120">檢視記錄檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="8524c-120">View the name of the log file.</span></span> <span data-ttu-id="8524c-121">這是從您在先前提供的資料庫名稱衍生的。</span><span class="sxs-lookup"><span data-stu-id="8524c-121">This is derived from the database name you provided earlier.</span></span>  
  
 <span data-ttu-id="8524c-122">**初始大小 (資料檔)**</span><span class="sxs-lookup"><span data-stu-id="8524c-122">**Initial size (data file)**</span></span>  
 <span data-ttu-id="8524c-123">指定資料檔的初始大小 (以 MB 為單位)。</span><span class="sxs-lookup"><span data-stu-id="8524c-123">Specify the number of megabytes for the initial size of the data file.</span></span>  
  
 <span data-ttu-id="8524c-124">**不允許成長 (資料檔)**</span><span class="sxs-lookup"><span data-stu-id="8524c-124">**No growth allowed (data file)**</span></span>  
 <span data-ttu-id="8524c-125">指出資料檔是否可以成長超過指定的初始大小。</span><span class="sxs-lookup"><span data-stu-id="8524c-125">Indicate whether the data file can grow beyond the specified initial size.</span></span>  
  
 <span data-ttu-id="8524c-126">**成長百分比 (資料檔)**</span><span class="sxs-lookup"><span data-stu-id="8524c-126">**Grow by percentage (data file)**</span></span>  
 <span data-ttu-id="8524c-127">指定資料檔可以成長的百分比。</span><span class="sxs-lookup"><span data-stu-id="8524c-127">Specify a percentage by which the data file can grow.</span></span>  
  
 <span data-ttu-id="8524c-128">**成長大小 (資料檔)**</span><span class="sxs-lookup"><span data-stu-id="8524c-128">**Grow by size (data file)**</span></span>  
 <span data-ttu-id="8524c-129">指定資料檔可以成長的大小 (以 MB 為單位)。</span><span class="sxs-lookup"><span data-stu-id="8524c-129">Specify a number of megabytes by which the data file can grow.</span></span>  
  
 <span data-ttu-id="8524c-130">**初始大小 (記錄檔)**</span><span class="sxs-lookup"><span data-stu-id="8524c-130">**Initial size (log file)**</span></span>  
 <span data-ttu-id="8524c-131">指定記錄檔的初始大小 (以 MB 為單位)。</span><span class="sxs-lookup"><span data-stu-id="8524c-131">Specify the number of megabytes for the initial size of the log file.</span></span>  
  
 <span data-ttu-id="8524c-132">**不允許成長 (記錄檔)**</span><span class="sxs-lookup"><span data-stu-id="8524c-132">**No growth allowed (log file)**</span></span>  
 <span data-ttu-id="8524c-133">指出記錄檔是否可以成長超過指定的初始大小。</span><span class="sxs-lookup"><span data-stu-id="8524c-133">Indicate whether the log file can grow beyond the specified initial size.</span></span>  
  
 <span data-ttu-id="8524c-134">**成長百分比 (記錄檔)**</span><span class="sxs-lookup"><span data-stu-id="8524c-134">**Grow by percentage (log file)**</span></span>  
 <span data-ttu-id="8524c-135">指定記錄檔可以成長的百分比。</span><span class="sxs-lookup"><span data-stu-id="8524c-135">Specify a percentage by which the log file can grow.</span></span>  
  
 <span data-ttu-id="8524c-136">**成長大小 (記錄檔)**</span><span class="sxs-lookup"><span data-stu-id="8524c-136">**Grow by size (log file)**</span></span>  
 <span data-ttu-id="8524c-137">指定記錄檔可以成長的大小 (以 MB 為單位)。</span><span class="sxs-lookup"><span data-stu-id="8524c-137">Specify a number of megabytes by which the log file can grow.</span></span>  
  
  
