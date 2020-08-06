---
title: 使用 DQS 預設知識庫 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: b36af13b-9fcc-4168-bb92-214d600b1c93
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 3261c7af28bb5710ede203d1fe27c6540286e9f5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592847"
---
# <a name="using-the-dqs-default-knowledge-base"></a><span data-ttu-id="825b5-102">使用 DQS 預設知識庫</span><span class="sxs-lookup"><span data-stu-id="825b5-102">Using the DQS Default Knowledge Base</span></span>
  <span data-ttu-id="825b5-103">本主題說明隨著 **(DQS) 一併安裝的預設知識庫**DQS [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] 資料。</span><span class="sxs-lookup"><span data-stu-id="825b5-103">This topic describes the default knowledge base, **DQS Data**, which is installed with [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).</span></span> <span data-ttu-id="825b5-104">這是包含下列定義域之預先建立的預設知識庫：</span><span class="sxs-lookup"><span data-stu-id="825b5-104">This is a pre-built default knowledge base that contains the following domains:</span></span>  
  
-   <span data-ttu-id="825b5-105">**國家/地區**：包含傳統的完整名稱 (該國家/地區所指定的官方名稱) 和簡短名稱 (清單、地圖等所使用的一般名稱)、兩個字母的縮寫、三個字母的縮寫，以及代表每個地點的三位數代碼。</span><span class="sxs-lookup"><span data-stu-id="825b5-105">**Country/Region**: Contains the conventional long (official name as designated by the country/region ) and short names (common name used in lists, on maps, etc. ), two-letter abbreviation, three-letter abbreviation and three-digit code for each location.</span></span>  <span data-ttu-id="825b5-106">前置值設定為完整的國家名稱。</span><span class="sxs-lookup"><span data-stu-id="825b5-106">Leading value is set to the long country name.</span></span>  
  
-   <span data-ttu-id="825b5-107">**國家/地區 (前置三個字母)**：包含傳統的完整名稱 (該國家/地區所指定的官方名稱) 和簡短名稱 (清單、地圖等所使用的一般名稱)、兩個字母的縮寫、三個字母的縮寫，以及代表每個地點的三位數代碼。</span><span class="sxs-lookup"><span data-stu-id="825b5-107">**Country/Region (three-letter leading)**: Contains the conventional long (official name as designated by the country/region) and short names (common name used in lists, on maps, and so on), two-letter abbreviation, three-letter abbreviation and three-digit code for each location.</span></span>  <span data-ttu-id="825b5-108">前置值設定為三個字母的縣市縮寫。</span><span class="sxs-lookup"><span data-stu-id="825b5-108">Leading values is set to County three-letter abbreviation.</span></span>  
  
-   <span data-ttu-id="825b5-109">**國家/地區 (前置兩個字母)**：包含傳統的完整名稱 (該國家/地區所指定的官方名稱) 和簡短名稱 (清單、地圖等所使用的一般名稱)、兩個字母的縮寫、三個字母的縮寫，以及代表每個地點的三位數代碼。</span><span class="sxs-lookup"><span data-stu-id="825b5-109">**Country/Region (two-letter leading)**: Contains the conventional long (official name as designated by the country/region ) and short names (common name used in lists, on maps, etc. ), two-letter abbreviation, three-letter abbreviation and three-digit code for each location.</span></span>  <span data-ttu-id="825b5-110">前置值設定為兩個字母的國家/地區縮寫。</span><span class="sxs-lookup"><span data-stu-id="825b5-110">Leading value is set to the Country two-letter abbreviation.</span></span>  
  
-   <span data-ttu-id="825b5-111">**美國 - 郡**：包含美國各郡的清單。</span><span class="sxs-lookup"><span data-stu-id="825b5-111">**US - Counties**: Contains a list of US counties.</span></span>  
  
-   <span data-ttu-id="825b5-112">**美國 - 姓氏**：在 2000 年人口普查中出現 100 (含) 次以上的姓氏清單。</span><span class="sxs-lookup"><span data-stu-id="825b5-112">**US - Last Name**: Contains a list of last names (surnames) occurring 100 or more times in the Census 2000.</span></span>  
  
-   <span data-ttu-id="825b5-113">**美國 - 地點**：包含從 2010 年人口普查擷取之 50 州、哥倫比亞特區以及波多黎各的地點清單。</span><span class="sxs-lookup"><span data-stu-id="825b5-113">**US - Places**: Contains a list of places for the 50 states, the District of Columbia, and Puerto Rico extracted from the Census 2010.</span></span>  
  
-   <span data-ttu-id="825b5-114">**美國 - 州**：包含美國各州的傳統完整 (官方) 名稱及兩個字母的縮寫。</span><span class="sxs-lookup"><span data-stu-id="825b5-114">**US - State**: Contains the conventional long (official) name and two-letter abbreviation for each state in US.</span></span> <span data-ttu-id="825b5-115">前置值設定為傳統的州名稱。</span><span class="sxs-lookup"><span data-stu-id="825b5-115">Leading value is set to the conventional state name.</span></span>  
  
-   <span data-ttu-id="825b5-116">**美國 - 州 (2 個字母的標題)**：包含美國各州的傳統完整 (官方) 名稱及兩個字母的縮寫。</span><span class="sxs-lookup"><span data-stu-id="825b5-116">**US - State (2-letter heading)**: Contains the conventional long (official) name and two-letter abbreviation for each state in US.</span></span> <span data-ttu-id="825b5-117">前置值設定為兩個字母的州名縮寫。</span><span class="sxs-lookup"><span data-stu-id="825b5-117">Leading value is set to the two-letter abbreviation state name.</span></span>  
  
## <a name="using-the-default-knowledge-base"></a><span data-ttu-id="825b5-118">使用預設知識庫</span><span class="sxs-lookup"><span data-stu-id="825b5-118">Using the Default Knowledge Base</span></span>  
 <span data-ttu-id="825b5-119">您可以透過下列方式使用預設的 DQS 知識庫 DQS 資料：</span><span class="sxs-lookup"><span data-stu-id="825b5-119">You can use the default DQS knowledge base, DQS Data, in the following ways:</span></span>  
  
-   <span data-ttu-id="825b5-120">使用預設知識庫快速啟動並執行清理資料品質專案，而不需要先在 DQS 中建立新的知識庫。</span><span class="sxs-lookup"><span data-stu-id="825b5-120">Quickly start and run a cleansing data quality project using the default knowledge base without first having to create a new knowledge base in DQS.</span></span>  
  
-   <span data-ttu-id="825b5-121">在預設知識庫上執行定義域管理、知識探索或比對原則活動。</span><span class="sxs-lookup"><span data-stu-id="825b5-121">Run the Domain Management, Knowledge Discovery, or Matching Policy activities on the default knowledge base.</span></span> <span data-ttu-id="825b5-122">若要執行這項操作，請在 [ **Data Quality Client Home Screen** ] 中按一下 [[開啟知識庫]](../../2014/data-quality-services/data-quality-client-home-screen.md)，然後選取 **[開啟知識庫]** 畫面中的 **[DQS 資料]** 知識庫，再選取 **[選取活動]** 區域中的必要活動。</span><span class="sxs-lookup"><span data-stu-id="825b5-122">To do so, click **Open Knowledge Base** in the [Data Quality Client Home Screen](../../2014/data-quality-services/data-quality-client-home-screen.md), select the **DQS Data** knowledge base in the **Open Knowledge Base** screen, and then select the required activity in the **Select Activity** area.</span></span> <span data-ttu-id="825b5-123">按 [下一步]  繼續進行。</span><span class="sxs-lookup"><span data-stu-id="825b5-123">Click **Next** to proceed.</span></span>  
  
-   <span data-ttu-id="825b5-124">使用預設知識庫建立新的知識庫。</span><span class="sxs-lookup"><span data-stu-id="825b5-124">Create a new knowledge base using the default knowledge base.</span></span> <span data-ttu-id="825b5-125">若要從現有的知識庫建立知識庫，請參閱＜ [Create a Knowledge Base](../../2014/data-quality-services/create-a-knowledge-base.md)＞。</span><span class="sxs-lookup"><span data-stu-id="825b5-125">To create a knowledge base from an existing knowledge base, see [Create a Knowledge Base](../../2014/data-quality-services/create-a-knowledge-base.md).</span></span>  
  
-   <span data-ttu-id="825b5-126">在 [Integration Services 中的 DQS 清理元件](https://go.microsoft.com/fwlink/?LinkId=238830) 及 [Excel 的 Master Data Services 增益集](../master-data-services/microsoft-excel-add-in/data-quality-matching-in-the-mds-add-in-for-excel.md)中使用。</span><span class="sxs-lookup"><span data-stu-id="825b5-126">Use it in the [DQS Cleansing component in Integration Services](https://go.microsoft.com/fwlink/?LinkId=238830) and [Master Data Services Add-in for Excel](../master-data-services/microsoft-excel-add-in/data-quality-matching-in-the-mds-add-in-for-excel.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="825b5-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="825b5-127">See Also</span></span>  
 [<span data-ttu-id="825b5-128">DQS 知識庫與定義域</span><span class="sxs-lookup"><span data-stu-id="825b5-128">DQS Knowledge Bases and Domains</span></span>](../../2014/data-quality-services/dqs-knowledge-bases-and-domains.md)  
  
  
