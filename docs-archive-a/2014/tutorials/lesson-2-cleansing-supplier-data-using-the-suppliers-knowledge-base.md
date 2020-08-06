---
title: 第2課：使用供應商知識庫清理供應商資料 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 215c14de-fc3f-46de-a022-bf69b9ea2a96
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: ebc0231cd0f28fcad23656cf22abd8d68eca7dc4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584908"
---
# <a name="lesson-2-cleansing-supplier-data-using-the-suppliers-knowledge-base"></a><span data-ttu-id="1abfb-102">第 2 課：使用供應商知識庫清理供應商資料</span><span class="sxs-lookup"><span data-stu-id="1abfb-102">Lesson 2: Cleansing Supplier Data using the Suppliers Knowledge Base</span></span>
  <span data-ttu-id="1abfb-103">在這一課，您會使用您在第一課建立的**供應商**知識庫來清理 Excel 檔案中的供應商資料。</span><span class="sxs-lookup"><span data-stu-id="1abfb-103">In this lesson, you cleanse the supplier data in an Excel file by using the **Suppliers** knowledge base you have created in the first lesson.</span></span> <span data-ttu-id="1abfb-104">DQS 中的資料清理包含**電腦輔助**的程式，可分析資料符合知識庫中知識的方式，以及可讓您從電腦輔助的程式中檢查和修改結果的**互動式進程**。</span><span class="sxs-lookup"><span data-stu-id="1abfb-104">Data cleansing in DQS includes a **computer-assisted process** that analyzes how data conforms to the knowledge in a knowledge base, and an **interactive process** that enables you to review and modify results from the computer-assisted process.</span></span> <span data-ttu-id="1abfb-105">資料清理功能會識別資料來源中不正確的資料，然後針對不正確的資料進行更正或建議更正。</span><span class="sxs-lookup"><span data-stu-id="1abfb-105">The data cleansing feature identifies incorrect data in your data source and then corrects or suggests corrections for the incorrect data.</span></span> <span data-ttu-id="1abfb-106">它也會使用定義域值、同義字的前置值、定義域規則、以詞彙為主的關聯及參考資料來標準化及豐富客戶資料。</span><span class="sxs-lookup"><span data-stu-id="1abfb-106">It also standardizes and enriches customer data by using domain values, leading values for synonyms, domain rules, term-based relations, and reference data.</span></span> <span data-ttu-id="1abfb-107">您可以用互動方式核准或拒絕電腦輔助程序所提議的變更。</span><span class="sxs-lookup"><span data-stu-id="1abfb-107">You can interactively approve or reject changes proposed by the computer-assisted process.</span></span> <span data-ttu-id="1abfb-108">如需詳細資訊，請參閱[資料清理](https://msdn.microsoft.com/library/gg524800.aspx)。</span><span class="sxs-lookup"><span data-stu-id="1abfb-108">See [Data Cleansing](https://msdn.microsoft.com/library/gg524800.aspx) for more details.</span></span>  
  
 <span data-ttu-id="1abfb-109">電腦輔助程序會使用以下的臨界值，您可以在 DQS 用戶端主頁面上使用 [組態] 選項設定此值。</span><span class="sxs-lookup"><span data-stu-id="1abfb-109">The computer-assisted process uses the following threshold values that you can configure using the Configuration option on the DQS Client main page.</span></span>  
  
-   <span data-ttu-id="1abfb-110">**建議的最低分數：** DQS 用來建議取代值的最低分數或信賴等級。</span><span class="sxs-lookup"><span data-stu-id="1abfb-110">**Min score for suggestions:** The minimum score or confidence level that is used by DQS for suggesting replacement for a value.</span></span>  
  
-   <span data-ttu-id="1abfb-111">**自動校正的最低分數：** DQS 用來自動校正值的最低分數或信賴等級。</span><span class="sxs-lookup"><span data-stu-id="1abfb-111">**Min score for auto corrections:** The minimum score or confidence level that is used by DQS for automatically correcting a value.</span></span>  
  
 <span data-ttu-id="1abfb-112">如需如何設定這些設定的詳細資訊，請參閱[設定清理和](https://msdn.microsoft.com/library/hh510415.aspx)比對的臨界值。</span><span class="sxs-lookup"><span data-stu-id="1abfb-112">See [Configure Threshold Values for Cleansing and Matching](https://msdn.microsoft.com/library/hh510415.aspx) for details on how to configure these settings.</span></span>  
  
 <span data-ttu-id="1abfb-113">在這一課，您會使用供應商知識庫來執行下列工作，以清理輸入資料。</span><span class="sxs-lookup"><span data-stu-id="1abfb-113">In this lesson, you perform the following tasks to cleanse the input data by using the Suppliers knowledge base.</span></span>  
  
1.  <span data-ttu-id="1abfb-114">建立清理用的資料品質專案、選取供應商知識庫做為用來分析及清理 Excel 檔案中來源資料的知識庫，並選取清理活動。</span><span class="sxs-lookup"><span data-stu-id="1abfb-114">Create a Data Quality Project for Cleansing, select the Suppliers knowledge base as the knowledge base to use to analyze and cleanse the source data in an Excel file, and select the Cleansing activity.</span></span>  
  
2.  <span data-ttu-id="1abfb-115">將您想要清理的 Excel 資料行對應到知識庫中適當的 DQS 定義域/複合定義域。</span><span class="sxs-lookup"><span data-stu-id="1abfb-115">Map the Excel columns that you want to cleanse to appropriate DQS domains/composite domains in the knowledge base.</span></span>  
  
3.  <span data-ttu-id="1abfb-116">執行電腦輔助的清理活動。</span><span class="sxs-lookup"><span data-stu-id="1abfb-116">Run the computer-assisted cleansing activity.</span></span> <span data-ttu-id="1abfb-117">電腦輔助程序會在 Data Quality Client 中顯示資料品質資訊，讓您可用來以互動方式清理資料。</span><span class="sxs-lookup"><span data-stu-id="1abfb-117">The computer-assisted process displays data quality information in the Data Quality Client that you can use to cleanse the data interactively.</span></span>  
  
4.  <span data-ttu-id="1abfb-118">檢視及管理清理活動的結果。</span><span class="sxs-lookup"><span data-stu-id="1abfb-118">View and manage the results of the cleansing activity.</span></span> <span data-ttu-id="1abfb-119">您可以檢閱電腦輔助程序所發現正確的值、不正確但是已更正的值、不正確且有建議值的值或是無效的值。</span><span class="sxs-lookup"><span data-stu-id="1abfb-119">You can review the values that the computer-assisted process finds to be correct, incorrect but corrected, incorrect with a suggested change, or invalid.</span></span> <span data-ttu-id="1abfb-120">您可以用互動方式核准或拒絕變更，使用 [更正為] 欄位更正或覆寫電腦輔助程序的建議。</span><span class="sxs-lookup"><span data-stu-id="1abfb-120">You can interactively approve or reject changes, correcting or overriding the suggestion from the computer-assisted process by using the Correct To field.</span></span>  
  
5.  <span data-ttu-id="1abfb-121">將清理程序的結果匯出到 Excel 檔案。</span><span class="sxs-lookup"><span data-stu-id="1abfb-121">Export the results from the cleansing process to an Excel file.</span></span>  
  
6.  <span data-ttu-id="1abfb-122">將清理專案中的值匯入定義域，以新的規則、值、更正等功能來增強知識庫中的知識。</span><span class="sxs-lookup"><span data-stu-id="1abfb-122">Import the values from the cleansing project into domains to augment the knowledge in the knowledge base with new rules, values, corrections etc...</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="1abfb-123">後續步驟</span><span class="sxs-lookup"><span data-stu-id="1abfb-123">Next Step</span></span>  
 [<span data-ttu-id="1abfb-124">工作 1：建立資料品質專案</span><span class="sxs-lookup"><span data-stu-id="1abfb-124">Task 1: Creating a Data Quality Project</span></span>](../../2014/tutorials/task-1-creating-a-data-quality-project.md)  
  
  
