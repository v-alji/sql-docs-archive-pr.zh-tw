---
title: SSAS 表格式)  (的資料表屬性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.tableprop.f1
ms.assetid: 16d3347b-7e43-4a6b-9956-fdd6ede092e6
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9613609c42de8fd3a4aab7aec3208dfe3d31be4a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706786"
---
# <a name="table-properties-ssas-tabular"></a><span data-ttu-id="38614-102">資料表屬性 (SSAS 表格式)</span><span class="sxs-lookup"><span data-stu-id="38614-102">Table Properties (SSAS Tabular)</span></span>
  <span data-ttu-id="38614-103">此主題描述表格式模型資料表屬性。</span><span class="sxs-lookup"><span data-stu-id="38614-103">This topic describes tabular model table properties.</span></span> <span data-ttu-id="38614-104">這裡所述的屬性與 [編輯資料表屬性] 對話方塊中的屬性不同，後者會定義從來源匯入的資料行。</span><span class="sxs-lookup"><span data-stu-id="38614-104">The properties described here are different from those in the Edit Table Properties dialog box, which define which columns from the source are imported.</span></span>  
  
 <span data-ttu-id="38614-105">本主題的章節：</span><span class="sxs-lookup"><span data-stu-id="38614-105">Sections in this topic:</span></span>  
  
-   [<span data-ttu-id="38614-106">資料表屬性</span><span class="sxs-lookup"><span data-stu-id="38614-106">Table Properties</span></span>](#bkmk_properties)  
  
-   [<span data-ttu-id="38614-107">若要設定資料表屬性設定</span><span class="sxs-lookup"><span data-stu-id="38614-107">To configure table property settings</span></span>](#bkmk_config_prop)  
  
##  <a name="table-properties"></a><a name="bkmk_properties"></a><span data-ttu-id="38614-108">資料表屬性</span><span class="sxs-lookup"><span data-stu-id="38614-108">Table Properties</span></span>  
 <span data-ttu-id="38614-109">**基本**</span><span class="sxs-lookup"><span data-stu-id="38614-109">**Basic**</span></span>  
  
|<span data-ttu-id="38614-110">屬性</span><span class="sxs-lookup"><span data-stu-id="38614-110">Property</span></span>|<span data-ttu-id="38614-111">預設值</span><span class="sxs-lookup"><span data-stu-id="38614-111">Default Setting</span></span>|<span data-ttu-id="38614-112">描述</span><span class="sxs-lookup"><span data-stu-id="38614-112">Description</span></span>|  
|--------------|---------------------|-----------------|  
|<span data-ttu-id="38614-113">**連接名稱**</span><span class="sxs-lookup"><span data-stu-id="38614-113">**Connection Name**</span></span>|\<connection name>|<span data-ttu-id="38614-114">資料表的資料來源連接名稱。</span><span class="sxs-lookup"><span data-stu-id="38614-114">The name of the connection to the table's data source.</span></span><br /><br /> <span data-ttu-id="38614-115">若要編輯連接，請按一下此按鈕。</span><span class="sxs-lookup"><span data-stu-id="38614-115">To edit the connection, click the button.</span></span>|  
|<span data-ttu-id="38614-116">**Hidden**</span><span class="sxs-lookup"><span data-stu-id="38614-116">**Hidden**</span></span>|<span data-ttu-id="38614-117">否</span><span class="sxs-lookup"><span data-stu-id="38614-117">False</span></span>|<span data-ttu-id="38614-118">指定是否在報表用戶端欄位清單中隱藏資料表。</span><span class="sxs-lookup"><span data-stu-id="38614-118">Specifies whether the table is hidden from reporting client field lists.</span></span>|  
|<span data-ttu-id="38614-119">**資料分割**</span><span class="sxs-lookup"><span data-stu-id="38614-119">**Partitions**</span></span>||<span data-ttu-id="38614-120">資料表的資料分割無法在 **[屬性]** 視窗中顯示。</span><span class="sxs-lookup"><span data-stu-id="38614-120">Partitions for the table cannot be displayed in the **Properties** window.</span></span> <span data-ttu-id="38614-121">若要檢視、建立或編輯資料分割，請按一下此按鈕以開啟 [資料分割管理員]。</span><span class="sxs-lookup"><span data-stu-id="38614-121">To view, create, or edit partitions, click the button to open the Partition Manager.</span></span>|  
|<span data-ttu-id="38614-122">**來源資料**</span><span class="sxs-lookup"><span data-stu-id="38614-122">**Source Data**</span></span>||<span data-ttu-id="38614-123">資料表的來源資料無法在 **[屬性]** 視窗中顯示。</span><span class="sxs-lookup"><span data-stu-id="38614-123">Source data for the table cannot be displayed in the **Properties** window.</span></span> <span data-ttu-id="38614-124">若要檢視或編輯來源資料，請按一下此按鈕以開啟 [編輯資料表屬性] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="38614-124">To view or edit the source data, click the button to open the Edit Table Properties dialog box.</span></span>|  
|<span data-ttu-id="38614-125">**資料表描述**</span><span class="sxs-lookup"><span data-stu-id="38614-125">**Table Description**</span></span>||<span data-ttu-id="38614-126">資料表的文字描述。</span><span class="sxs-lookup"><span data-stu-id="38614-126">A text description for the table.</span></span><br /><br /> <span data-ttu-id="38614-127">在 [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)]中，如果使用者將游標置於欄位清單內這個資料表的上方，將以工具提示的形式顯示說明。</span><span class="sxs-lookup"><span data-stu-id="38614-127">In [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)], if an end-user places the cursor over this table in the field list, the description appears as a tooltip.</span></span>|  
|<span data-ttu-id="38614-128">**資料表名稱**</span><span class="sxs-lookup"><span data-stu-id="38614-128">**Table Name**</span></span>|\<friendly name>|<span data-ttu-id="38614-129">指定資料表的易記名稱。</span><span class="sxs-lookup"><span data-stu-id="38614-129">Specifies the table's friendly name.</span></span> <span data-ttu-id="38614-130">資料表名稱可在使用 [資料表匯入精靈] 匯入資料表時指定，或在匯入後隨時指定。</span><span class="sxs-lookup"><span data-stu-id="38614-130">The table name can be specified when a table is imported using the Table Import Wizard or at any time after import.</span></span> <span data-ttu-id="38614-131">模型中的資料表名稱可以不同於在來源的關聯資料表。</span><span class="sxs-lookup"><span data-stu-id="38614-131">The table name in the model can be different from the associated table at the source.</span></span> <span data-ttu-id="38614-132">資料表易記名稱出現在報表用戶端應用程式欄位清單中以及 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中的模型資料庫。</span><span class="sxs-lookup"><span data-stu-id="38614-132">The table friendly name appears in the reporting client application field list as well as in the model database in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>|  
  
 <span data-ttu-id="38614-133">**報表屬性**</span><span class="sxs-lookup"><span data-stu-id="38614-133">**Reporting Properties**</span></span>  
  
 <span data-ttu-id="38614-134">如需報表屬性的詳細描述和組態資訊，請參閱 [Power View 報表屬性 &#40;SSAS 表格式&#41;](properties-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="38614-134">For detailed descriptions and configuration information for reporting properties, see [Power View Reporting Properties &#40;SSAS Tabular&#41;](properties-ssas-tabular.md).</span></span>  
  
|<span data-ttu-id="38614-135">屬性</span><span class="sxs-lookup"><span data-stu-id="38614-135">Property</span></span>|<span data-ttu-id="38614-136">預設值</span><span class="sxs-lookup"><span data-stu-id="38614-136">Default Setting</span></span>|<span data-ttu-id="38614-137">描述</span><span class="sxs-lookup"><span data-stu-id="38614-137">Description</span></span>|  
|--------------|---------------------|-----------------|  
|<span data-ttu-id="38614-138">**預設欄位集**</span><span class="sxs-lookup"><span data-stu-id="38614-138">**Default Field Set**</span></span>|||  
|<span data-ttu-id="38614-139">資料表行為</span><span class="sxs-lookup"><span data-stu-id="38614-139">Table Behavior</span></span>|||  
  
###  <a name="to-configure-table-property-settings"></a><a name="bkmk_config_prop"></a><span data-ttu-id="38614-140">若要設定資料表屬性設定</span><span class="sxs-lookup"><span data-stu-id="38614-140">To configure table property settings</span></span>  
  
1.  <span data-ttu-id="38614-141">在模型設計師的 [資料檢視] 中按一下資料表 (索引標籤)，或在 [圖表檢視] 中按一下資料表標頭。</span><span class="sxs-lookup"><span data-stu-id="38614-141">In the model designer, in Data View, click a table (tab), or, in Diagram View, click a table header.</span></span>  
  
2.  <span data-ttu-id="38614-142">在 **[屬性]** 視窗中按一下屬性，然後輸入值，或按一下按鈕來選取其他組態選項。</span><span class="sxs-lookup"><span data-stu-id="38614-142">In the **Properties** window, click on a property, and then type a value or click the button for additional configuration options.</span></span>  
  
  
