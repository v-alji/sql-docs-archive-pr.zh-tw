---
title: 第5課：使用 SSIS 自動化清理和比對 |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: f068d4db-2d56-41b1-bed2-0cffa3ca411d
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 90f967b2446e11a27f5a87803bb71d6e1ec53557
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702194"
---
# <a name="lesson-5-automating-the-cleansing-and-matching-using-ssis"></a><span data-ttu-id="72b4c-102">第 5 課：使用 SSIS 將清理和比對自動化</span><span class="sxs-lookup"><span data-stu-id="72b4c-102">Lesson 5: Automating the Cleansing and Matching using SSIS</span></span>
  <span data-ttu-id="72b4c-103">在第1課中，您已建立供應商知識庫，並用它來清理第2課中的資料，並使用**DQS 用戶端**工具來比對第3課的資料。</span><span class="sxs-lookup"><span data-stu-id="72b4c-103">In Lesson 1, you built the Suppliers knowledge base and used it to cleanse data in Lesson 2 and match data in Lesson 3 using the tool **DQS Client**.</span></span> <span data-ttu-id="72b4c-104">在真實世界的案例中，您可能必須從 DQS 不支援的來源提取資料，或者您想要自動化清理和比對程式，而不需要使用**DQS 用戶端**工具。</span><span class="sxs-lookup"><span data-stu-id="72b4c-104">In a real world scenario, you may have to pull data from a source that DQS does not support or you want to automate the cleansing and matching process without having to use the **DQS Client** tool.</span></span> <span data-ttu-id="72b4c-105">SQL Server Integration Services (SSIS) 具有元件，可讓您用來整合各種不同來源的資料，以及使用**[Dqs 清理轉換](https://msdn.microsoft.com/library/ee677619.aspx)** 元件來叫用 dqs 所公開的清理功能。</span><span class="sxs-lookup"><span data-stu-id="72b4c-105">SQL Server Integration Services (SSIS) has components that you can use to integrate data from various heterogeneous sources and a **[DQS Cleansing Transform](https://msdn.microsoft.com/library/ee677619.aspx)** component to invoke the cleansing functionality exposed by DQS.</span></span> <span data-ttu-id="72b4c-106">目前，DQS 不會公開要使用之 SSIS 的比對功能，但您可以使用**[模糊群組轉換](../integration-services/data-flow/transformations/fuzzy-grouping-transformation.md)** 來識別資料中的重複項。</span><span class="sxs-lookup"><span data-stu-id="72b4c-106">Currently, DQS does not expose matching functionality for SSIS to use, but you can use the **[Fuzzy Grouping Transform](../integration-services/data-flow/transformations/fuzzy-grouping-transformation.md)** to identify duplicates in the data.</span></span>  
  
 <span data-ttu-id="72b4c-107">您可以使用以**實體為基礎的暫存功能**，將資料上傳至 MDS。</span><span class="sxs-lookup"><span data-stu-id="72b4c-107">You can upload data to MDS by using the **Entity-based Staging feature**.</span></span> <span data-ttu-id="72b4c-108">當您在 MDS 中建立實體時，將會自動建立對應的暫存資料表和預存程序。</span><span class="sxs-lookup"><span data-stu-id="72b4c-108">When you create an entity in MDS, corresponding staging tables and stored procedures are automatically created.</span></span> <span data-ttu-id="72b4c-109">例如，當您建立供應商實體時，會自動建立**supplier_Leaf stg.<** 資料表和**udp_Supplier_Leaf stg.<** 預存程式。</span><span class="sxs-lookup"><span data-stu-id="72b4c-109">For example, when you created the Supplier entity, the **stg.supplier_Leaf** table and the **stg.udp_Supplier_Leaf** stored procedure were automatically created.</span></span> <span data-ttu-id="72b4c-110">您會使用暫存資料表和程序來建立、更新及刪除實體成員。</span><span class="sxs-lookup"><span data-stu-id="72b4c-110">You use the staging tables and procedures to create, update, and delete entity members.</span></span> <span data-ttu-id="72b4c-111">在這一課，您會建立 Supplier 實體的新實體成員。</span><span class="sxs-lookup"><span data-stu-id="72b4c-111">In this lesson, you create new entity members for the Supplier Entity.</span></span> <span data-ttu-id="72b4c-112">為了將資料載入 MDS 伺服器，SSIS 封裝會先將資料載入暫存資料表 stg.supplier_Leaf，然後觸發相關的預存程序 stg.udp_Supplier_Leaf。</span><span class="sxs-lookup"><span data-stu-id="72b4c-112">To load data into the MDS server, the SSIS package first loads the data into the staging table stg.supplier_Leaf and then triggers the associated stored procedure stg.udp_Supplier_Leaf.</span></span> <span data-ttu-id="72b4c-113">如需詳細資訊，請參閱匯[入資料](../master-data-services/overview-importing-data-from-tables-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="72b4c-113">See [Importing Data](../master-data-services/overview-importing-data-from-tables-master-data-services.md) for more details.</span></span>  
  
 <span data-ttu-id="72b4c-114">在這一課，您會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="72b4c-114">In this lesson, you perform the following tasks:</span></span>  
  
1.  <span data-ttu-id="72b4c-115">在 MDS 中移除供應商資料 (如果您已經完成之前的四個課程)。</span><span class="sxs-lookup"><span data-stu-id="72b4c-115">Remove supplier data in MDS (if you have gone through previous four lessons).</span></span> <span data-ttu-id="72b4c-116">您在這一課建立的 SSIS 封裝會將資料自動上傳至 MDS。</span><span class="sxs-lookup"><span data-stu-id="72b4c-116">The SSIS package you create in this lesson uploads the data to MDS automatically.</span></span> <span data-ttu-id="72b4c-117">您在稍早已使用 DQS 用戶端，手動將已清理和比對的供應商資料上傳至 MDS 伺服器。</span><span class="sxs-lookup"><span data-stu-id="72b4c-117">Earlier, you uploaded the cleansed and matched supplier data to MDS server manually using the DQS Client.</span></span>  
  
2.  <span data-ttu-id="72b4c-118">請在 Supplier 實體中建立訂閱檢視，向其他應用程式公開此實體中的資料。</span><span class="sxs-lookup"><span data-stu-id="72b4c-118">Create a subscription view on the Supplier entity to expose data in the entity to other applications.</span></span> <span data-ttu-id="72b4c-119">此動作會建立一個 SQL 檢視表，您將使用 SQL Server Management Studio 加以驗證。</span><span class="sxs-lookup"><span data-stu-id="72b4c-119">This action creates a SQL view that you will verify using SQL Server Management Studio.</span></span> <span data-ttu-id="72b4c-120">您不會在這一版的教學課程中使用這個檢視表。</span><span class="sxs-lookup"><span data-stu-id="72b4c-120">You will not be consuming this view in this version of the tutorial.</span></span>  
  
3.  <span data-ttu-id="72b4c-121">使用**SQL Server Data Tools**建立及執行 SSIS 專案。</span><span class="sxs-lookup"><span data-stu-id="72b4c-121">Create and run an SSIS project by using **SQL Server Data Tools**.</span></span> <span data-ttu-id="72b4c-122">專案會使用**資料清理**轉換，將清理要求提交至 DQS 伺服器。</span><span class="sxs-lookup"><span data-stu-id="72b4c-122">The project uses **Data Cleansing** transform to submit a cleansing request to the DQS server.</span></span> <span data-ttu-id="72b4c-123">DQS 尚未公開相符的功能，因此您將使用**模糊群組**轉換來識別重複專案。</span><span class="sxs-lookup"><span data-stu-id="72b4c-123">DQS does not expose the matching functionality yet, so you will use **Fuzzy Grouping** transform to identify duplicates.</span></span>  
  
4.  <span data-ttu-id="72b4c-124">確認已使用主資料管理員在 MDS 中建立資料。</span><span class="sxs-lookup"><span data-stu-id="72b4c-124">Verify that the data is created in MDS by using Master Data Manger.</span></span>  
  
5.  <span data-ttu-id="72b4c-125">檢閱 SSIS 封裝所建立之 DQS 清理專案的結果，並選擇性地執行互動式清理，進一步建立知識庫。</span><span class="sxs-lookup"><span data-stu-id="72b4c-125">Review the results from DQS cleansing project created by the SSIS package and optionally perform interactive cleansing to build the knowledge base further.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="72b4c-126">後續步驟</span><span class="sxs-lookup"><span data-stu-id="72b4c-126">Next Step</span></span>  
 [<span data-ttu-id="72b4c-127">工作 1 &#40;必要條件&#41;：在 MDS 中移除供應商資料</span><span class="sxs-lookup"><span data-stu-id="72b4c-127">Task 1 &#40;Prerequisite&#41;: Removing Supplier Data in MDS</span></span>](../../2014/tutorials/task-1-prerequisite-removing-supplier-data-in-mds.md)  
  
  
