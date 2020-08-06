---
title: 工作2：將 Excel 資料行對應到 DQS 定義域 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: f347cc92-950f-4021-b7af-393640dfe821
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 293b035ff52845959e2c8b70c63df643ae6e3e55
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599289"
---
# <a name="task-2-mapping-excel-columns-to-dqs-domains"></a><span data-ttu-id="72f34-102">工作 2：將 Excel 資料行對應到 DQS 定義域</span><span class="sxs-lookup"><span data-stu-id="72f34-102">Task 2: Mapping Excel Columns to DQS Domains</span></span>
    
1.  <span data-ttu-id="72f34-103">在 [對應] \*\*\*\* 頁面上，針對 [資料來源] \*\*\*\* 選取 [Excel 檔案] \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="72f34-103">In the **Map** page, select **Excel File** for **Data Source**.</span></span>  
  
2.  <span data-ttu-id="72f34-104">按一下 **[流覽]**，選取 [ **Suppliers.xlsx**]，然後按一下 [**開啟**]。</span><span class="sxs-lookup"><span data-stu-id="72f34-104">Click **Browse**, select **Suppliers.xlsx**, and click **Open**.</span></span>  
  
3.  <span data-ttu-id="72f34-105">針對**工作表**選取 [ **IncomingSuppliers $** ]。</span><span class="sxs-lookup"><span data-stu-id="72f34-105">Select **IncomingSuppliers$** for the **Worksheet**.</span></span>  
  
4.  <span data-ttu-id="72f34-106">對應資料行，如下表和螢幕擷取畫面所示。</span><span class="sxs-lookup"><span data-stu-id="72f34-106">Map columns as shown in the following table and screenshot.</span></span> <span data-ttu-id="72f34-107">建立**狀態**網域的對應時，請按一下工具列上位於清單正上方的 [**加入資料行對應**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="72f34-107">When creating mappings for the **State** domain, click **Add a column mapping** button on the toolbar located just above the list.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="72f34-108">您不會使用**供應商識別碼**資料行/網域進行清理。</span><span class="sxs-lookup"><span data-stu-id="72f34-108">You are not using **Supplier ID** column/domain for cleansing.</span></span> <span data-ttu-id="72f34-109">您稍後會在比對活動中使用**供應商識別碼**網域。</span><span class="sxs-lookup"><span data-stu-id="72f34-109">You will use the **Supplier ID** domain later in the matching activity.</span></span>  
  
    |<span data-ttu-id="72f34-110">Excel 資料行</span><span class="sxs-lookup"><span data-stu-id="72f34-110">Excel column</span></span>|<span data-ttu-id="72f34-111">DQS 定義域</span><span class="sxs-lookup"><span data-stu-id="72f34-111">DQS Domain</span></span>|  
    |------------------|----------------|  
    |<span data-ttu-id="72f34-112">Supplier Name</span><span class="sxs-lookup"><span data-stu-id="72f34-112">Supplier Name</span></span>|<span data-ttu-id="72f34-113">Supplier Name</span><span class="sxs-lookup"><span data-stu-id="72f34-113">Supplier Name</span></span>|  
    |<span data-ttu-id="72f34-114">ContactEmailAddress</span><span class="sxs-lookup"><span data-stu-id="72f34-114">ContactEmailAddress</span></span>|<span data-ttu-id="72f34-115">連絡人電子郵件</span><span class="sxs-lookup"><span data-stu-id="72f34-115">Contact Email</span></span>|  
    |<span data-ttu-id="72f34-116">[地址行]</span><span class="sxs-lookup"><span data-stu-id="72f34-116">Address Line</span></span>|<span data-ttu-id="72f34-117">[地址行]</span><span class="sxs-lookup"><span data-stu-id="72f34-117">Address Line</span></span>|  
    |<span data-ttu-id="72f34-118">城市</span><span class="sxs-lookup"><span data-stu-id="72f34-118">City</span></span>|<span data-ttu-id="72f34-119">城市</span><span class="sxs-lookup"><span data-stu-id="72f34-119">City</span></span>|  
    |<span data-ttu-id="72f34-120">州</span><span class="sxs-lookup"><span data-stu-id="72f34-120">State</span></span>|<span data-ttu-id="72f34-121">州</span><span class="sxs-lookup"><span data-stu-id="72f34-121">State</span></span>|  
    |<span data-ttu-id="72f34-122">國家 (按一下 [ **+ (新增**資料行對應]) 工具列來加入資料列) </span><span class="sxs-lookup"><span data-stu-id="72f34-122">Country (Click **+(Add a column mapping)** toolbar to add a row)</span></span>|<span data-ttu-id="72f34-123">國家/地區</span><span class="sxs-lookup"><span data-stu-id="72f34-123">Country</span></span>|  
    |<span data-ttu-id="72f34-124">Zip Code</span><span class="sxs-lookup"><span data-stu-id="72f34-124">Zip Code</span></span>|<span data-ttu-id="72f34-125">Zip</span><span class="sxs-lookup"><span data-stu-id="72f34-125">Zip</span></span>|  
  
     <span data-ttu-id="72f34-126">![將 Excel 資料行對應到定義域](../../2014/tutorials/media/et-mappingexcelcolumnstodqsdomains-01.jpg "將 Excel 資料行對應到定義域")</span><span class="sxs-lookup"><span data-stu-id="72f34-126">![Mappings of Excel Columns to Domains](../../2014/tutorials/media/et-mappingexcelcolumnstodqsdomains-01.jpg "Mappings of Excel Columns to Domains")</span></span>  
  
5.  <span data-ttu-id="72f34-127">當您已對應「**位址驗證**」複合定義域中的所有個別網域時，複合定義域會自動參與清理程式。</span><span class="sxs-lookup"><span data-stu-id="72f34-127">As you have mapped all the individual domains within the **Address Validation** composite domain, the composite domain automatically participates in the cleansing process.</span></span> <span data-ttu-id="72f34-128">按一下 [**視圖/選取複合定義域**] 按鈕，以查看是否已自動選取 [**位址驗證**] 複合定義域，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="72f34-128">Click **View/Select Composite Domains** button to see that the **Address Validation** composite domain is automatically selected, and then click **OK**.</span></span>  
  
     <span data-ttu-id="72f34-129">![[檢視/選取複合定義域] 對話方塊](../../2014/tutorials/media/et-mappingexcelcolumnstodqsdomains-02.jpg "[檢視/選取複合定義域] 對話方塊")</span><span class="sxs-lookup"><span data-stu-id="72f34-129">![View/Select Composite Domains Dialog Box](../../2014/tutorials/media/et-mappingexcelcolumnstodqsdomains-02.jpg "View/Select Composite Domains Dialog Box")</span></span>  
  
6.  <span data-ttu-id="72f34-130">按 **[下一步]** 切換至 [**清理**] 頁面。</span><span class="sxs-lookup"><span data-stu-id="72f34-130">Click **Next** to switch to the **Cleanse** page.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="72f34-131">後續步驟</span><span class="sxs-lookup"><span data-stu-id="72f34-131">Next Step</span></span>  
 [<span data-ttu-id="72f34-132">工作 3：針對供應商知識庫清理資料</span><span class="sxs-lookup"><span data-stu-id="72f34-132">Task 3: Cleansing Data against the Suppliers Knowledge Base</span></span>](../../2014/tutorials/task-3-cleansing-data-against-the-suppliers-knowledge-base.md)  
  
  
