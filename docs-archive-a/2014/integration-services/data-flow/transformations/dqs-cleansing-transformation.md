---
title: DQS 清理轉換 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- data correction
- correct data
ms.assetid: d2ec1b1a-c745-4741-b57c-6fdb524a154c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5e980497905b8fa96a73516916af17f934221992
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585511"
---
# <a name="dqs-cleansing-transformation"></a><span data-ttu-id="bc437-102">DQS 清理轉換</span><span class="sxs-lookup"><span data-stu-id="bc437-102">DQS Cleansing Transformation</span></span>
  <span data-ttu-id="bc437-103">DQS 清理轉換會使用 Data Quality Services (DQS) 來更正連接之資料來源的資料，方法是套用針對所連接資料來源或相似資料來源而建立的核准規則。</span><span class="sxs-lookup"><span data-stu-id="bc437-103">The DQS Cleansing transformation uses Data Quality Services (DQS) to correct data from a connected data source, by applying approved rules that were created for the connected data source or a similar data source.</span></span> <span data-ttu-id="bc437-104">如需有關資料更正規則的詳細資訊，請參閱＜ [DQS Knowledge Bases and Domains](../../../data-quality-services/dqs-knowledge-bases-and-domains.md)＞。</span><span class="sxs-lookup"><span data-stu-id="bc437-104">For more information about data correction rules, see [DQS Knowledge Bases and Domains](../../../data-quality-services/dqs-knowledge-bases-and-domains.md).</span></span> <span data-ttu-id="bc437-105">如需有關 DQS 的詳細資訊，請參閱＜ [Data Quality Services Concepts](../../../data-quality-services/data-quality-services-concepts.md)＞。</span><span class="sxs-lookup"><span data-stu-id="bc437-105">For more information DQS, see [Data Quality Services Concepts](../../../data-quality-services/data-quality-services-concepts.md).</span></span>  
  
 <span data-ttu-id="bc437-106">為了判斷資料是否必須更正，DQS 清理轉換會在符合下列條件的情況下，處理來自輸入資料行的資料：</span><span class="sxs-lookup"><span data-stu-id="bc437-106">To determine whether the data has to be corrected, the DQS Cleansing transformation processes data from an input column when the following conditions are true:</span></span>  
  
-   <span data-ttu-id="bc437-107">已選擇要進行資料更正的資料行。</span><span class="sxs-lookup"><span data-stu-id="bc437-107">The column is selected for data correction.</span></span>  
  
-   <span data-ttu-id="bc437-108">可支援對該資料行的資料類型進行資料更正。</span><span class="sxs-lookup"><span data-stu-id="bc437-108">The column data type is supported for data correction.</span></span>  
  
-   <span data-ttu-id="bc437-109">資料行對應至具有相容資料類型的定義域。</span><span class="sxs-lookup"><span data-stu-id="bc437-109">The column is mapped a domain that has a compatible data type.</span></span>  
  
 <span data-ttu-id="bc437-110">轉換還包括您設定來處理資料列層級錯誤的錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="bc437-110">The transformation also includes an error output that you configure to handle row-level errors.</span></span> <span data-ttu-id="bc437-111">若要設定錯誤輸出，請使用 **[DQS 清理轉換編輯器]** 。</span><span class="sxs-lookup"><span data-stu-id="bc437-111">To configure the error output, use the **DQS Cleansing Transformation Editor**.</span></span>  
  
 <span data-ttu-id="bc437-112">您可以在資料流程中包括 [Fuzzy Grouping Transformation](fuzzy-grouping-transformation.md) ，用於識別資料中可能重複的資料列。</span><span class="sxs-lookup"><span data-stu-id="bc437-112">You can include the [Fuzzy Grouping Transformation](fuzzy-grouping-transformation.md) in the data flow to identify rows of data that are likely to be duplicates.</span></span>  
  
## <a name="data-quality-projects-and-values"></a><span data-ttu-id="bc437-113">資料品質專案及值</span><span class="sxs-lookup"><span data-stu-id="bc437-113">Data Quality Projects and Values</span></span>  
 <span data-ttu-id="bc437-114">當您使用 DQS 清理轉換處理資料時，會在資料品質伺服器上建立清理專案。</span><span class="sxs-lookup"><span data-stu-id="bc437-114">When you process data with the DQS Cleansing transformation, a cleansing project is created on the Data Quality Server.</span></span> <span data-ttu-id="bc437-115">您可以使用 Data Quality Client 管理專案。</span><span class="sxs-lookup"><span data-stu-id="bc437-115">You use the Data Quality Client to manage the project.</span></span> <span data-ttu-id="bc437-116">此外，您也可以使用 Data Quality Client 將專案值匯入 DQS 知識庫定義域。</span><span class="sxs-lookup"><span data-stu-id="bc437-116">In addition, you can use the Data Quality Client to import the project values into a DQS knowledge base domain.</span></span> <span data-ttu-id="bc437-117">您可以只將值匯入設定為使用 DQS 清理轉換的定義域 (或連結的定義域)。</span><span class="sxs-lookup"><span data-stu-id="bc437-117">You can import the values only to a domain (or linked domain) that the DQS Cleansing transformation was configured to use.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="bc437-118">相關工作</span><span class="sxs-lookup"><span data-stu-id="bc437-118">Related Tasks</span></span>  
  
-   [<span data-ttu-id="bc437-119">在 Data Quality Client 中開啟 Integration Services 專案</span><span class="sxs-lookup"><span data-stu-id="bc437-119">Open Integration Services Projects in Data Quality Client</span></span>](../../../data-quality-services/open-integration-services-projects-in-data-quality-client.md)  
  
-   [<span data-ttu-id="bc437-120">將清理專案值匯入網域</span><span class="sxs-lookup"><span data-stu-id="bc437-120">Import Cleansing Project Values into a Domain</span></span>](../../../data-quality-services/import-cleansing-project-values-into-a-domain.md)  
  
-   [<span data-ttu-id="bc437-121">將資料品質規則套用至資料來源</span><span class="sxs-lookup"><span data-stu-id="bc437-121">Apply Data Quality Rules to Data Source</span></span>](apply-data-quality-rules-to-data-source.md)  
  
## <a name="related-content"></a><span data-ttu-id="bc437-122">相關內容</span><span class="sxs-lookup"><span data-stu-id="bc437-122">Related Content</span></span>  
  
-   [<span data-ttu-id="bc437-123">管理 &#40;開啟、解除鎖定、重新命名和刪除資料品質專案&#41;</span><span class="sxs-lookup"><span data-stu-id="bc437-123">Manage &#40;Open, Unlock, Rename, and Delete&#41; a Data Quality Project</span></span>](../../../data-quality-services/manage-open-unlock-rename-and-delete-a-data-quality-project.md)  
  
-   <span data-ttu-id="bc437-124">social.technet.microsoft.com 上的文章： [使用複合定義域清理複雜的資料](https://social.technet.microsoft.com/wiki/contents/articles/13324.using-dqs-cleansing-complex-data-using-composite-domains.aspx)。</span><span class="sxs-lookup"><span data-stu-id="bc437-124">Article, [Cleansing complex data using composite domains](https://social.technet.microsoft.com/wiki/contents/articles/13324.using-dqs-cleansing-complex-data-using-composite-domains.aspx), on social.technet.microsoft.com.</span></span>  
  
  
