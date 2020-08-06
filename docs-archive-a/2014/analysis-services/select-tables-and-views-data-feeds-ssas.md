---
title: 選取資料表和 Views (資料摘要)  (SSAS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.seltablesviewsdf.f1
ms.assetid: 6c4fafe0-e02e-47d1-b8bc-e70e872690af
author: minewiskan
ms.author: owend
ms.openlocfilehash: 46c317ecf2a87adcde264e8d6d7e822eb833b8b2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594722"
---
# <a name="select-tables-and-views-data-feeds-ssas"></a><span data-ttu-id="73e4d-102">選取資料表和檢視表 (資料摘要) (SSAS)</span><span class="sxs-lookup"><span data-stu-id="73e4d-102">Select Tables and Views (Data Feeds) (SSAS)</span></span>
  <span data-ttu-id="73e4d-103">[資料表匯入精靈]\*\*\*\* 的這個頁面可讓您選取您要匯入資料的來源資料表和檢視表。</span><span class="sxs-lookup"><span data-stu-id="73e4d-103">This page of the **Table Import Wizard** enables you to select the tables and views that you want to import data from.</span></span> <span data-ttu-id="73e4d-104">若要從 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]存取精靈，請按一下 **[模型]** 功能表上的 **[從資料來源匯入]**。</span><span class="sxs-lookup"><span data-stu-id="73e4d-104">To access the wizard from the [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], on the **Model** menu, click **Import from Data Source**.</span></span>  
  
 <span data-ttu-id="73e4d-105">此頁面之資料表和檢視表的外觀不保證匯入將會成功。</span><span class="sxs-lookup"><span data-stu-id="73e4d-105">The appearance of tables and views on this page does not guarantee that import will succeed.</span></span> <span data-ttu-id="73e4d-106">如果在 [模擬資訊] 頁面中指定的使用者未具備從所選資料庫讀取的權限，則匯入將會失敗。</span><span class="sxs-lookup"><span data-stu-id="73e4d-106">If the user specified in the Impersonation Information page does not have sufficient privileges to read from the selected database, import will fail.</span></span>  
  
 <span data-ttu-id="73e4d-107">針對使用 Windows 驗證的資料來源，目前使用者的認證會用來提取 [選取資料表和檢視表] 對話方塊中的資料表和檢視表。</span><span class="sxs-lookup"><span data-stu-id="73e4d-107">For data sources using Windows authentication, the credentials of the current user are used to fetch the tables and views in the Select Tables and Views dialog.</span></span> <span data-ttu-id="73e4d-108">至於其他資料來源，連接字串中提供的認證則用來提取資料。</span><span class="sxs-lookup"><span data-stu-id="73e4d-108">For other data sources, the credentials supplied in the connection string are used to fetch the data.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="73e4d-109">UI 元素清單</span><span class="sxs-lookup"><span data-stu-id="73e4d-109">UI element list</span></span>  
 <span data-ttu-id="73e4d-110">**資料摘要 URL**</span><span class="sxs-lookup"><span data-stu-id="73e4d-110">**Data feed URL**</span></span>  
 <span data-ttu-id="73e4d-111">顯示您選取之資料摘要的 URL。</span><span class="sxs-lookup"><span data-stu-id="73e4d-111">Displays the URL for the data feed that you selected.</span></span>  
  
 <span data-ttu-id="73e4d-112">**資料表和視圖**</span><span class="sxs-lookup"><span data-stu-id="73e4d-112">**Tables and views**</span></span>  
 <span data-ttu-id="73e4d-113">列出資料摘要中的資料表和檢視表。</span><span class="sxs-lookup"><span data-stu-id="73e4d-113">Lists the tables and views in the data feed.</span></span> <span data-ttu-id="73e4d-114">選取您要匯入之每個資料表和檢視表旁邊的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="73e4d-114">Select the checkbox beside each table and view that you want to import.</span></span>  
  
 <span data-ttu-id="73e4d-115">**來源資料表**</span><span class="sxs-lookup"><span data-stu-id="73e4d-115">**Source Table**</span></span>  
 <span data-ttu-id="73e4d-116">根據資料來源的類型指定來源資料表的名稱。</span><span class="sxs-lookup"><span data-stu-id="73e4d-116">Specifies the name of the source table based on the type of data source.</span></span>  
  
 <span data-ttu-id="73e4d-117">**易記名稱**</span><span class="sxs-lookup"><span data-stu-id="73e4d-117">**Friendly Name**</span></span>  
 <span data-ttu-id="73e4d-118">指定來源資料表的易記名稱。</span><span class="sxs-lookup"><span data-stu-id="73e4d-118">Specifies the friendly name of the source table.</span></span> <span data-ttu-id="73e4d-119">根據預設，此資料行會顯示出現在 [來源資料表]\*\*\*\* 資料行內的來源資料表名稱。</span><span class="sxs-lookup"><span data-stu-id="73e4d-119">By default, the column displays the name of the source table that appears in the **Source Table** column.</span></span>  
  
 <span data-ttu-id="73e4d-120">**篩選詳細資料**</span><span class="sxs-lookup"><span data-stu-id="73e4d-120">**Filter Details**</span></span>  
 <span data-ttu-id="73e4d-121">當篩選已經套用到正在匯入的資料時，在 [篩選詳細資料]\*\*\*\* 對話方塊中顯示資料匯入篩選。</span><span class="sxs-lookup"><span data-stu-id="73e4d-121">Displays the data import filter in the **Filter Details** dialog box, when a filter has been applied to the data that is being imported.</span></span> <span data-ttu-id="73e4d-122">如需詳細資訊，請參閱[篩選詳細資料 &#40;SSAS&#41;](filter-details-ssas.md)。</span><span class="sxs-lookup"><span data-stu-id="73e4d-122">For more information, see [Filter Details &#40;SSAS&#41;](filter-details-ssas.md).</span></span>  
  
 <span data-ttu-id="73e4d-123">**預覽和篩選**</span><span class="sxs-lookup"><span data-stu-id="73e4d-123">**Preview and Filter**</span></span>  
 <span data-ttu-id="73e4d-124">顯示 [預覽選取的資料表]\*\*\*\* 對話方塊，此對話方塊是用來將篩選套用到匯入的資料。</span><span class="sxs-lookup"><span data-stu-id="73e4d-124">Displays the **Preview Selected Table** dialog box that is used to apply a filter to the data that is being imported.</span></span> <span data-ttu-id="73e4d-125">如需詳細資訊，請參閱[預覽選取的資料表 &#40;SSAS&#41;](preview-selected-table-ssas.md)。</span><span class="sxs-lookup"><span data-stu-id="73e4d-125">For more information, see [Preview Selected Table &#40;SSAS&#41;](preview-selected-table-ssas.md).</span></span>  
  
 <span data-ttu-id="73e4d-126">**選取相關資料表**</span><span class="sxs-lookup"><span data-stu-id="73e4d-126">**Select Related Tables**</span></span>  
 <span data-ttu-id="73e4d-127">選取與您選取之資料表和檢視表相關的資料表。</span><span class="sxs-lookup"><span data-stu-id="73e4d-127">Select tables that are related to the tables and views that you have selected.</span></span>  
  
  
