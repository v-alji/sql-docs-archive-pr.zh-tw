---
title: 教學課程：Database Engine Tuning Advisor | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- Database Engine Tuning Advisor [SQL Server], tutorials
- tutorials [Database Engine Tuning Advisor]
ms.assetid: 3b54cbbe-d8c6-424d-92f1-aa58179f4da8
author: stevestein
ms.author: sstein
ms.openlocfilehash: 68e026cb28b875b834f20c906232285ede8e217b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585736"
---
# <a name="tutorial-database-engine-tuning-advisor"></a><span data-ttu-id="262b6-102">教學課程：Database Engine Tuning Advisor</span><span class="sxs-lookup"><span data-stu-id="262b6-102">Tutorial: Database Engine Tuning Advisor</span></span>
  <span data-ttu-id="262b6-103">歡迎使用 Database Engine Tuning Advisor 教學課程。</span><span class="sxs-lookup"><span data-stu-id="262b6-103">Welcome to the Database Engine Tuning Advisor tutorial.</span></span> <span data-ttu-id="262b6-104">Database Engine Tuning Advisor 會檢查在您指定的資料庫中如何處理查詢，之後，它會建議您如何修改資料庫結構 (如索引、索引檢視和資料分割) 來改進查詢處理效能。</span><span class="sxs-lookup"><span data-stu-id="262b6-104">Database Engine Tuning Advisor examines how queries are processed in the databases you specify, and then recommends how you can improve query processing performance by modifying database structures such as indexes, indexed views, and partitioning.</span></span>  
  
 <span data-ttu-id="262b6-105">Database Engine Tuning Advisor 提供兩個使用者介面：圖形化使用者介面 (GUI) 和 **dta** 命令提示字元公用程式。</span><span class="sxs-lookup"><span data-stu-id="262b6-105">Database Engine Tuning Advisor provides two user interfaces: a graphical user interface (GUI) and the **dta** command prompt utility.</span></span> <span data-ttu-id="262b6-106">GUI 可讓您既快又容易檢視微調工作階段的結果， **dta** 公用程式則可以輕易將 Database Engine Tuning Advisor 功能納入自動微調的指令碼中。</span><span class="sxs-lookup"><span data-stu-id="262b6-106">The GUI makes it easy to quickly view the results of tuning sessions, and the **dta** utility makes it easy to incorporate Database Engine Tuning Advisor functionality into scripts for automated tuning.</span></span> <span data-ttu-id="262b6-107">此外，Database Engine Tuning Advisor 可接受 XML 輸入，對微調處理序提供更多控制權。</span><span class="sxs-lookup"><span data-stu-id="262b6-107">In addition, Database Engine Tuning Advisor can take XML input, which offers more control over the tuning process.</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="262b6-108">學習內容</span><span class="sxs-lookup"><span data-stu-id="262b6-108">What You Will Learn</span></span>  
 <span data-ttu-id="262b6-109">這個教學課程將告訴您如何導覽 Database Engine Tuning Advisor GUI，以及如何利用這個 GUI 和 **dta** 公用程式來執行某些基本工作。</span><span class="sxs-lookup"><span data-stu-id="262b6-109">This tutorial will teach you how to navigate the Database Engine Tuning Advisor GUI, and how to perform some basic tasks with both the GUI and the **dta** utility.</span></span> <span data-ttu-id="262b6-110">它包含下列課程：</span><span class="sxs-lookup"><span data-stu-id="262b6-110">It contains the following lessons:</span></span>  
  
 [<span data-ttu-id="262b6-111">第 1 課：Database Engine Tuning Advisor 中的基本導覽</span><span class="sxs-lookup"><span data-stu-id="262b6-111">Lesson 1: Basic Navigation in Database Engine Tuning Advisor</span></span>](../../relational-databases/performance/database-engine-tuning-advisor.md)  
 <span data-ttu-id="262b6-112">在這個課程中，您將熟悉新的 Database Engine Tuning Advisor GUI，以及學習如何設定顯示選項和配置。</span><span class="sxs-lookup"><span data-stu-id="262b6-112">In this lesson, you will familiarize yourself with the new Database Engine Tuning Advisor GUI and learn how to set display options and layout.</span></span>  
  
 [<span data-ttu-id="262b6-113">第 2 課：使用 Database Engine Tuning Advisor</span><span class="sxs-lookup"><span data-stu-id="262b6-113">Lesson 2: Using Database Engine Tuning Advisor</span></span>](lesson-2-using-database-engine-tuning-advisor.md)  
 <span data-ttu-id="262b6-114">在這個課程中，您將學會如何使用 Database Engine Tuning Advisor GUI 來執行基本微調工作。</span><span class="sxs-lookup"><span data-stu-id="262b6-114">In this lesson, you will learn how to perform basic tuning tasks with the Database Engine Tuning Advisor GUI.</span></span>  
  
 [<span data-ttu-id="262b6-115">第 3 課：使用 dta 命令提示字元公用程式</span><span class="sxs-lookup"><span data-stu-id="262b6-115">Lesson 3: Using the dta Command Prompt Utility</span></span>](lesson-3-using-the-dta-command-prompt-utility.md)  
 <span data-ttu-id="262b6-116">在這個課程中，您將學習如何啟動 **DTA** 命令提示字元公用程式，以及如何執行簡單的微調命令。</span><span class="sxs-lookup"><span data-stu-id="262b6-116">In this lesson, you learn how to start the **dta** command prompt utility and how to run some simple tuning commands.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="262b6-117">需求</span><span class="sxs-lookup"><span data-stu-id="262b6-117">Requirements</span></span>  
 <span data-ttu-id="262b6-118">這個教學課程是專門針對不熟悉 Database Engine Tuning Advisor GUI 或 **dta** 命令提示字元公用程式，但是熟悉資料庫概念和結構 (例如索引和索引檢視) 的資料庫管理員而提供。</span><span class="sxs-lookup"><span data-stu-id="262b6-118">This tutorial is intended for database administrators who are not familiar with the Database Engine Tuning Advisor GUI or the **dta** command prompt utility, but who are experienced with database concepts and structures, such as indexes and indexed views.</span></span>  
  
 <span data-ttu-id="262b6-119">您必須安裝具有 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 範例資料庫的 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] (或更新版本)。</span><span class="sxs-lookup"><span data-stu-id="262b6-119">You must install [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] (or a later version) with the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database.</span></span> <span data-ttu-id="262b6-120">為了加強安全性，依預設，不會安裝範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="262b6-120">To enhance security, the sample databases are not installed by default.</span></span> <span data-ttu-id="262b6-121">若要安裝範例資料庫，請參閱＜ [安裝 SQL Server 範例和範例資料庫](http://sqlserversamples.codeplex.com)＞。</span><span class="sxs-lookup"><span data-stu-id="262b6-121">To install the sample databases, see [Installing SQL Server Samples and Sample Databases](http://sqlserversamples.codeplex.com).</span></span>  
  
## <a name="after-you-finish-this-tutorial"></a><span data-ttu-id="262b6-122">完成這個教學課程之後</span><span class="sxs-lookup"><span data-stu-id="262b6-122">After You Finish This Tutorial</span></span>  
 <span data-ttu-id="262b6-123">完成這個教學課程中的課程之後，請參閱下列主題，以取得有關 Database Engine Tuning Advisor 的詳細資訊：</span><span class="sxs-lookup"><span data-stu-id="262b6-123">After you finish the lessons in this tutorial, refer to the following topics for more information about Database Engine Tuning Advisor:</span></span>  
  
-   <span data-ttu-id="262b6-124">＜[Database Engine Tuning Advisor](../../relational-databases/performance/database-engine-tuning-advisor.md) ＞提供如何利用這個工具來執行工作的描述。</span><span class="sxs-lookup"><span data-stu-id="262b6-124">[Database Engine Tuning Advisor](../../relational-databases/performance/database-engine-tuning-advisor.md) for descriptions of how to perform tasks with this tool.</span></span>  
  
-   <span data-ttu-id="262b6-125">＜[dta Utility](dta-utility.md) ＞提供有關命令提示字元公用程式的參考資料，以及可用來控制公用程式作業的選擇性 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="262b6-125">[dta Utility](dta-utility.md) for reference material on the command prompt utility and the optional XML file you can use to control the operation of the utility.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="262b6-126">下一課</span><span class="sxs-lookup"><span data-stu-id="262b6-126">Next Lesson</span></span>  
 [<span data-ttu-id="262b6-127">第 1 課：Database Engine Tuning Advisor 中的基本導覽</span><span class="sxs-lookup"><span data-stu-id="262b6-127">Lesson 1: Basic Navigation in Database Engine Tuning Advisor</span></span>](../../relational-databases/performance/database-engine-tuning-advisor.md)  
  
  
