---
title: 第 1 課：建立範例訂閱者資料庫 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 47a882b7-efe5-4ee6-bef4-06118eb56903
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6ee49f0858b28c0c4b00fd391b0db7b4d2c54b16
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710270"
---
# <a name="lesson-1-creating-a-sample-subscriber-database"></a><span data-ttu-id="99b84-102">第 1 課：建立範例訂閱者資料庫</span><span class="sxs-lookup"><span data-stu-id="99b84-102">Lesson 1: Creating a Sample Subscriber Database</span></span>
  <span data-ttu-id="99b84-103">在定義資料驅動訂閱之前，您必須先有提供訂閱資料的資料來源。</span><span class="sxs-lookup"><span data-stu-id="99b84-103">Before you can define a data-driven subscription, you must have a data source that provides subscription data.</span></span> <span data-ttu-id="99b84-104">在這個步驟中，您將建立一個小型資料庫來儲存這個教學課程所用的訂閱資料。</span><span class="sxs-lookup"><span data-stu-id="99b84-104">In this step, you will create a small database to store the subscription data used in this tutorial.</span></span> <span data-ttu-id="99b84-105">稍後，當處理訂閱時，報表伺服器會擷取這份資料，並利用它來自訂報表輸出、傳遞選項以及報表呈現格式。</span><span class="sxs-lookup"><span data-stu-id="99b84-105">Later, when the subscription is processed, the report server retrieves this data and uses it to customize report output, delivery options, and report presentation format.</span></span>  
  
 <span data-ttu-id="99b84-106">這一課會假設您要使用 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 來建立 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="99b84-106">This lesson assumes you are using [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] to create a [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] database.</span></span>  
  
### <a name="to-create-a-sample-subscriber-database"></a><span data-ttu-id="99b84-107">若要建立範例訂閱者資料庫</span><span class="sxs-lookup"><span data-stu-id="99b84-107">To create a sample Subscriber database</span></span>  
  
1.  <span data-ttu-id="99b84-108">啟動 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]，然後開啟 [!INCLUDE[ssDE](../includes/ssde-md.md)] 的連接。</span><span class="sxs-lookup"><span data-stu-id="99b84-108">Start [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], and open a connection to a [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="99b84-109">以滑鼠右鍵按一下 [資料庫]，然後選取 [新增資料庫...]  。</span><span class="sxs-lookup"><span data-stu-id="99b84-109">Right-click on Databases, select **New Database...**.</span></span>  
  
3.  <span data-ttu-id="99b84-110">在 [新增資料庫] 對話方塊的 [資料庫名稱] 中，輸入*訂閱者*。</span><span class="sxs-lookup"><span data-stu-id="99b84-110">In the New Database dialog box, in Database Name, type *Subscribers*.</span></span> [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
4.  <span data-ttu-id="99b84-111">按一下工具列上的 [新增查詢]  按鈕。</span><span class="sxs-lookup"><span data-stu-id="99b84-111">Click the **New Query** button on the toolbar.</span></span>  
  
5.  <span data-ttu-id="99b84-112">將下列 [!INCLUDE[tsql](../includes/tsql-md.md)] 陳述式複製到空的查詢中：</span><span class="sxs-lookup"><span data-stu-id="99b84-112">Copy the following [!INCLUDE[tsql](../includes/tsql-md.md)] statements into the empty query:</span></span>  
  
    ```  
    Use Subscribers  
    CREATE TABLE [dbo].[OrderInfo] (  
        [SubscriptionID] [int] NOT NULL PRIMARY KEY ,  
        [Order] [nvarchar] (20) NOT NULL,  
        [FileType] [bit],  
        [Format] [nvarchar] (20) NOT NULL ,  
    ) ON [PRIMARY]  
    GO  
  
    INSERT INTO [dbo].[OrderInfo] (SubscriptionID, [Order], FileType, Format)   
    VALUES ('1', 'so43659', '1', 'IMAGE')  
    INSERT INTO [dbo].[OrderInfo] (SubscriptionID, [Order], FileType, Format)   
    VALUES ('2', 'so43664', '1', 'MHTML')  
    INSERT INTO [dbo].[OrderInfo] (SubscriptionID, [Order], FileType, Format)   
    VALUES ('3', 'so43668', '1', 'PDF')  
    INSERT INTO [dbo].[OrderInfo] (SubscriptionID, [Order], FileType, Format)   
    VALUES ('4', 'so71949', '1', 'Excel')  
    GO  
    ```  
  
6.  <span data-ttu-id="99b84-113">按一下工具列上的 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="99b84-113">Click **! Execute** on the toolbar.</span></span>  
  
7.  <span data-ttu-id="99b84-114">利用 SELECT 陳述式來確認您已有三個資料列。</span><span class="sxs-lookup"><span data-stu-id="99b84-114">Use a SELECT statement to verify that you have three rows of data.</span></span> <span data-ttu-id="99b84-115">例如： `select * from OrderInfo`</span><span class="sxs-lookup"><span data-stu-id="99b84-115">For example: `select * from OrderInfo`</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="99b84-116">後續步驟</span><span class="sxs-lookup"><span data-stu-id="99b84-116">Next Steps</span></span>  
 <span data-ttu-id="99b84-117">您已順利建立驅動報表散發作業的訂閱資料，且每位訂閱者的報表輸出都各不相同。</span><span class="sxs-lookup"><span data-stu-id="99b84-117">You have successfully created the subscription data that will drive report distribution and vary the report output for each subscriber.</span></span> <span data-ttu-id="99b84-118">之後，您要修改將散發給各訂閱者之報表的資料來源屬性。</span><span class="sxs-lookup"><span data-stu-id="99b84-118">Next, you will modify the data source properties of the report you will distribute to subscribers.</span></span> <span data-ttu-id="99b84-119">修改資料來源屬性是為了準備資料驅動訂閱所傳遞的報表。</span><span class="sxs-lookup"><span data-stu-id="99b84-119">Modifying the data source properties is done to prepare the report for data-driven subscription delivery.</span></span> <span data-ttu-id="99b84-120">您也會將報表設計修改為包含訂閱將搭配訂閱者資料使用的參數。</span><span class="sxs-lookup"><span data-stu-id="99b84-120">You will also modify the report design to include a parameter that the subscription will use with the subscriber data.</span></span> <span data-ttu-id="99b84-121">[第2課：修改報告資料來源屬性](lesson-2-modifying-the-report-data-source-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="99b84-121">[Lesson 2: Modifying the Report Data Source Properties](lesson-2-modifying-the-report-data-source-properties.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99b84-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="99b84-122">See Also</span></span>  
 <span data-ttu-id="99b84-123">[建立資料驅動訂閱 &#40;SSRS 教學課程&#41;](create-a-data-driven-subscription-ssrs-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="99b84-123">[Create a Data-Driven Subscription &#40;SSRS Tutorial&#41;](create-a-data-driven-subscription-ssrs-tutorial.md) </span></span>  
 <span data-ttu-id="99b84-124">[建立資料庫](../relational-databases/databases/create-a-database.md) </span><span class="sxs-lookup"><span data-stu-id="99b84-124">[Create a Database](../relational-databases/databases/create-a-database.md) </span></span>  
 [<span data-ttu-id="99b84-125">建立基本資料表報表 &#40;SSRS 教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="99b84-125">Create a Basic Table Report &#40;SSRS Tutorial&#41;</span></span>](create-a-basic-table-report-ssrs-tutorial.md)  
  
  
