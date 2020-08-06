---
title: 將資料來源從內嵌轉換成共用 (報表產生器和 SSRS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- data sources [Reporting Services], embedded
- data sources [Reporting Services], shared
ms.assetid: 0e099c7e-8c03-43eb-9ea3-76e52d9ebbe3
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5827bab564b58e7a2b7922f01a33f550a6f523f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592461"
---
# <a name="convert-a-data-source-from-embedded-to-shared-report-builder-and-ssrs"></a><span data-ttu-id="07e6d-102">將資料來源從內嵌轉換成共用 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="07e6d-102">Convert a Data Source from Embedded to Shared (Report Builder and SSRS)</span></span>
  <span data-ttu-id="07e6d-103">[報表資料] 窗格中的每個資料來源都是報表內嵌且專用的項目，或共用的項目。</span><span class="sxs-lookup"><span data-stu-id="07e6d-103">Each data source in the Report Data pane is embedded and specific to the report or is shared.</span></span> <span data-ttu-id="07e6d-104">在報表產生器中，共用資料來源會指向報表伺服器或 SharePoint 網站上的已發行共用資料來源。</span><span class="sxs-lookup"><span data-stu-id="07e6d-104">In Report Builder, a shared data source points to a published shared data source on a report server or SharePoint site.</span></span> <span data-ttu-id="07e6d-105">在報表設計師中，共用資料來源會指向 [方案總管] 中 **[共用資料來源]** 資料夾的共用資料來源。</span><span class="sxs-lookup"><span data-stu-id="07e6d-105">In Report Designer, a shared data source points to a shared data source in the **Shared Data Sources** folder in Solution Explorer.</span></span>  
  
 <span data-ttu-id="07e6d-106">如需內嵌資料來源與共用資料來源之間差異的詳細資訊，請參閱[內嵌和共用資料連線或資料來源 &#40;報表產生器及 SSRS&#41;](../embedded-and-shared-data-connections-or-data-sources-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="07e6d-106">For more information about the differences between embedded and shared data sources, see [Embedded and Shared Data Connections or Data Sources &#40;Report Builder and SSRS&#41;](../embedded-and-shared-data-connections-or-data-sources-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="07e6d-107">如需如何建立共用資料來源的詳細資訊，請參閱[建立內嵌或共用資料來源 &#40;SSRS&#41;](../create-an-embedded-or-shared-data-source-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="07e6d-107">For more information on how to create a shared data source, see [Create an Embedded or Shared Data Source &#40;SSRS&#41;](../create-an-embedded-or-shared-data-source-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="report-designer"></a><span data-ttu-id="07e6d-108">報表設計師</span><span class="sxs-lookup"><span data-stu-id="07e6d-108">Report Designer</span></span>  
  
#### <a name="to-convert-a-data-source-from-embedded-to-shared"></a><span data-ttu-id="07e6d-109">若要將資料來源從內嵌轉換成共用</span><span class="sxs-lookup"><span data-stu-id="07e6d-109">To convert a data source from embedded to shared</span></span>  
  
-   <span data-ttu-id="07e6d-110">在 [報表資料] 窗格中，以滑鼠右鍵按一下資料來源，然後按一下 [轉換成共用資料來源]  。</span><span class="sxs-lookup"><span data-stu-id="07e6d-110">In the Report Data pane, right-click the data source, and then click **Convert to Shared Data Source**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="07e6d-111">如果看不到 [報表資料] 窗格，請按一下 **[檢視]** 功能表上的 **[報表資料]** 。</span><span class="sxs-lookup"><span data-stu-id="07e6d-111">If the Report Data pane is not visible, on the **View** menu, click **Report Data**.</span></span> <span data-ttu-id="07e6d-112">如果此窗格以浮動視窗的形式開啟，您可以將它停駐。</span><span class="sxs-lookup"><span data-stu-id="07e6d-112">If the pane opens as a floating window, you can dock it.</span></span> <span data-ttu-id="07e6d-113">如需詳細資訊，請參閱[停駐報表設計師中的報表資料窗格 &#40;SSRS&#41;](../tools/dock-the-report-data-pane-in-report-designer-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="07e6d-113">For more information, see [Dock the Report Data Pane in Report Designer &#40;SSRS&#41;](../tools/dock-the-report-data-pane-in-report-designer-ssrs.md).</span></span>  
  
     <span data-ttu-id="07e6d-114">在 [報表資料] 窗格中，資料來源圖示會變成共用資料來源圖示。</span><span class="sxs-lookup"><span data-stu-id="07e6d-114">In the Report Data pane, the data source icon changes to the shared data source icon.</span></span> <span data-ttu-id="07e6d-115">在 [方案總管] 中，同名的共用資料來源會出現在 **[共用資料來源]** 資料夾底下。</span><span class="sxs-lookup"><span data-stu-id="07e6d-115">In Solution Explorer, a shared data source with the same name appears under the **Shared Data Source** folder.</span></span>  
  
### <a name="to-convert-a-data-source-from-shared-to-embedded"></a><span data-ttu-id="07e6d-116">若要將資料來源從共用轉換成內嵌</span><span class="sxs-lookup"><span data-stu-id="07e6d-116">To convert a data source from shared to embedded</span></span>  
  
-   <span data-ttu-id="07e6d-117">在 [報表資料] 窗格中，以滑鼠右鍵按一下資料來源，開啟 [資料來源屬性]  對話方塊，然後按一下 [內嵌連接]  。</span><span class="sxs-lookup"><span data-stu-id="07e6d-117">In the Report Data pane, right-click the data source, open the **Data Source Properties** dialog box, and then click **Embedded Connection**.</span></span> <span data-ttu-id="07e6d-118">輸入必要資訊。</span><span class="sxs-lookup"><span data-stu-id="07e6d-118">Enter the required information.</span></span>  
  
     <span data-ttu-id="07e6d-119">在 [報表資料] 窗格中，資料來源圖示會變成共用資料來源圖示。</span><span class="sxs-lookup"><span data-stu-id="07e6d-119">In the Report Data pane, the data source icon changes to the shared data source icon.</span></span>  
  
## <a name="report-builder"></a><span data-ttu-id="07e6d-120">報表產生器</span><span class="sxs-lookup"><span data-stu-id="07e6d-120">Report Builder</span></span>  
  
#### <a name="to-convert-a-data-source-from-embedded-to-shared"></a><span data-ttu-id="07e6d-121">若要將資料來源從內嵌轉換成共用</span><span class="sxs-lookup"><span data-stu-id="07e6d-121">To convert a data source from embedded to shared</span></span>  
  
-   <span data-ttu-id="07e6d-122">在 [報表資料] 窗格中，以滑鼠右鍵按一下資料來源開啟 [資料來源屬性]  對話方塊，然後按一下 [內嵌連接]  。</span><span class="sxs-lookup"><span data-stu-id="07e6d-122">In the Report Data pane, right-click the data source to open the **Data Source Properties** dialog box, and then click **Embedded Connection**.</span></span> <span data-ttu-id="07e6d-123">輸入必要資訊。</span><span class="sxs-lookup"><span data-stu-id="07e6d-123">Enter the required information.</span></span>  
  
     <span data-ttu-id="07e6d-124">在 [報表資料] 窗格中，資料來源圖示會變成共用資料來源圖示。</span><span class="sxs-lookup"><span data-stu-id="07e6d-124">In the Report Data pane, the data source icon changes to the shared data source icon.</span></span>  
  
#### <a name="to-convert-a-data-source-from-shared-to-embedded"></a><span data-ttu-id="07e6d-125">若要將資料來源從共用轉換成內嵌</span><span class="sxs-lookup"><span data-stu-id="07e6d-125">To convert a data source from shared to embedded</span></span>  
  
-   <span data-ttu-id="07e6d-126">在 [報表資料] 窗格中，以滑鼠右鍵按一下資料來源，開啟 [資料來源屬性]  對話方塊，然後按一下 [內嵌連接]  。</span><span class="sxs-lookup"><span data-stu-id="07e6d-126">In the Report Data pane, right-click the data source, open the **Data Source Properties** dialog box, and then click **Embedded Connection**.</span></span> <span data-ttu-id="07e6d-127">輸入必要資訊。</span><span class="sxs-lookup"><span data-stu-id="07e6d-127">Enter the required information.</span></span>  
  
     <span data-ttu-id="07e6d-128">在 [報表資料] 窗格中，資料來源圖示會變成共用資料來源圖示。</span><span class="sxs-lookup"><span data-stu-id="07e6d-128">In the Report Data pane, the data source icon changes to the shared data source icon.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07e6d-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="07e6d-129">See Also</span></span>  
 <span data-ttu-id="07e6d-130">[管理報表資料來源](manage-report-data-sources.md) </span><span class="sxs-lookup"><span data-stu-id="07e6d-130">[Manage Report Data Sources](manage-report-data-sources.md) </span></span>  
 [<span data-ttu-id="07e6d-131">Data Connections, Data Sources, and Connection Strings in Reporting Services</span><span class="sxs-lookup"><span data-stu-id="07e6d-131">Data Connections, Data Sources, and Connection Strings in Reporting Services</span></span>](../data-connections-data-sources-and-connection-strings-in-reporting-services.md)  
  
  
