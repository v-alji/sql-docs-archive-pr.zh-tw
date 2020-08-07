---
title: 將屬性加入至維度 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 80551dad-97ac-40d0-90af-b810780321ce
author: minewiskan
ms.author: owend
ms.openlocfilehash: 76a04c42cc501fdca3e5ceb6481452052966796b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584774"
---
# <a name="adding-attributes-to-dimensions"></a><span data-ttu-id="b84e8-102">將屬性加入至維度</span><span class="sxs-lookup"><span data-stu-id="b84e8-102">Adding Attributes to Dimensions</span></span>
  <span data-ttu-id="b84e8-103">既然您已經定義維度，就可以使用代表維度中每個資料元素的屬性擴展它們。</span><span class="sxs-lookup"><span data-stu-id="b84e8-103">Now that you have defined dimensions, you can populate them with attributes that represent each data element in the dimension.</span></span> <span data-ttu-id="b84e8-104">屬性通常是以資料來源檢視中的欄位為基礎。</span><span class="sxs-lookup"><span data-stu-id="b84e8-104">Attributes are commonly based on fields from a data source view.</span></span> <span data-ttu-id="b84e8-105">將屬性加入至維度時，您可以將欄位從任何資料表加入至資料來源檢視中。</span><span class="sxs-lookup"><span data-stu-id="b84e8-105">When adding attributes to a dimension, you can include fields from any table in the data source view.</span></span>  
  
 <span data-ttu-id="b84e8-106">在此工作中，您將使用維度設計師，將屬性加入至 [客戶] 和 [產品] 維度。</span><span class="sxs-lookup"><span data-stu-id="b84e8-106">In this task, you will use Dimension Designer to add attributes to the Customer and Product dimensions.</span></span> <span data-ttu-id="b84e8-107">根據 [客戶] 和 [地理位置] 資料表中的欄位，[客戶] 維度將包含屬性。</span><span class="sxs-lookup"><span data-stu-id="b84e8-107">The Customer dimension will include attributes based on fields from both the Customer and Geography tables.</span></span>  
  
## <a name="adding-attributes-to-the-customer-dimension"></a><span data-ttu-id="b84e8-108">將屬性加入至 [客戶] 維度</span><span class="sxs-lookup"><span data-stu-id="b84e8-108">Adding Attributes to the Customer Dimension</span></span>  
  
#### <a name="to-add-attributes"></a><span data-ttu-id="b84e8-109">加入屬性</span><span class="sxs-lookup"><span data-stu-id="b84e8-109">To add attributes</span></span>  
  
1.  <span data-ttu-id="b84e8-110">針對 [客戶] 維度開啟維度設計師。</span><span class="sxs-lookup"><span data-stu-id="b84e8-110">Open Dimension Designer for the Customer dimension.</span></span> <span data-ttu-id="b84e8-111">若要這樣做，請在方案總管的 [維度]\*\*\*\* 節點中，按兩下 [客戶]\*\*\*\* 維度。</span><span class="sxs-lookup"><span data-stu-id="b84e8-111">To do this, double-click the **Customer** dimension in the **Dimensions** node of Solution Explorer.</span></span>  
  
2.  <span data-ttu-id="b84e8-112">在 [屬性]\*\*\*\* 窗格中，注意由 Cube 精靈所建立的 [客戶索引鍵] 和 [地理位置索引鍵] 屬性。</span><span class="sxs-lookup"><span data-stu-id="b84e8-112">In the **Attributes** pane, notice the Customer Key and Geography Key attributes that were created by the Cube Wizard.</span></span>  
  
3.  <span data-ttu-id="b84e8-113">在 [維度結構]\*\*\*\* 索引標籤的工具列上，確定用來檢視 [資料來源檢視]\*\*\*\* 窗格中資料表的 [顯示比例] 圖示設為 100%。</span><span class="sxs-lookup"><span data-stu-id="b84e8-113">On the toolbar of the **Dimension Structure** tab, make sure the Zoom icon to view the tables in the **Data Source View** pane is set at 100 percent.</span></span>  
  
4.  <span data-ttu-id="b84e8-114">將下列資料行，從 [資料來源檢視]\*\*\*\* 窗格中的 [客戶]\*\*\*\* 資料表拖曳至 [屬性]\*\*\*\* 窗格：</span><span class="sxs-lookup"><span data-stu-id="b84e8-114">Drag the following columns from the **Customer** table in the **Data Source View** pane to the **Attributes** pane:</span></span>  
  
    -   <span data-ttu-id="b84e8-115">**BirthDate**</span><span class="sxs-lookup"><span data-stu-id="b84e8-115">**BirthDate**</span></span>  
  
    -   <span data-ttu-id="b84e8-116">**MaritalStatus**</span><span class="sxs-lookup"><span data-stu-id="b84e8-116">**MaritalStatus**</span></span>  
  
    -   <span data-ttu-id="b84e8-117">**性別**</span><span class="sxs-lookup"><span data-stu-id="b84e8-117">**Gender**</span></span>  
  
    -   <span data-ttu-id="b84e8-118">**EmailAddress**</span><span class="sxs-lookup"><span data-stu-id="b84e8-118">**EmailAddress**</span></span>  
  
    -   <span data-ttu-id="b84e8-119">**YearlyIncome**</span><span class="sxs-lookup"><span data-stu-id="b84e8-119">**YearlyIncome**</span></span>  
  
    -   <span data-ttu-id="b84e8-120">**TotalChildren**</span><span class="sxs-lookup"><span data-stu-id="b84e8-120">**TotalChildren**</span></span>  
  
    -   <span data-ttu-id="b84e8-121">**NumberChildrenAtHome**</span><span class="sxs-lookup"><span data-stu-id="b84e8-121">**NumberChildrenAtHome**</span></span>  
  
    -   <span data-ttu-id="b84e8-122">**EnglishEducation**</span><span class="sxs-lookup"><span data-stu-id="b84e8-122">**EnglishEducation**</span></span>  
  
    -   <span data-ttu-id="b84e8-123">**EnglishOccupation**</span><span class="sxs-lookup"><span data-stu-id="b84e8-123">**EnglishOccupation**</span></span>  
  
    -   <span data-ttu-id="b84e8-124">**HouseOwnerFlag**</span><span class="sxs-lookup"><span data-stu-id="b84e8-124">**HouseOwnerFlag**</span></span>  
  
    -   <span data-ttu-id="b84e8-125">**NumberCarsOwned**</span><span class="sxs-lookup"><span data-stu-id="b84e8-125">**NumberCarsOwned**</span></span>  
  
    -   <span data-ttu-id="b84e8-126">**來電**</span><span class="sxs-lookup"><span data-stu-id="b84e8-126">**Phone**</span></span>  
  
    -   <span data-ttu-id="b84e8-127">**DateFirstPurchase**</span><span class="sxs-lookup"><span data-stu-id="b84e8-127">**DateFirstPurchase**</span></span>  
  
    -   <span data-ttu-id="b84e8-128">**CommuteDistance**</span><span class="sxs-lookup"><span data-stu-id="b84e8-128">**CommuteDistance**</span></span>  
  
5.  <span data-ttu-id="b84e8-129">將下列資料行，從 [資料來源檢視]\*\*\*\* 窗格中的 [地理位置]\*\*\*\* 資料表拖曳至 [屬性]\*\*\*\* 窗格：</span><span class="sxs-lookup"><span data-stu-id="b84e8-129">Drag the following columns from the **Geography** table in the **Data Source View** pane to the **Attributes** pane:</span></span>  
  
    -   <span data-ttu-id="b84e8-130">**城市**</span><span class="sxs-lookup"><span data-stu-id="b84e8-130">**City**</span></span>  
  
    -   <span data-ttu-id="b84e8-131">**StateProvinceName**</span><span class="sxs-lookup"><span data-stu-id="b84e8-131">**StateProvinceName**</span></span>  
  
    -   <span data-ttu-id="b84e8-132">**EnglishCountryRegionName**</span><span class="sxs-lookup"><span data-stu-id="b84e8-132">**EnglishCountryRegionName**</span></span>  
  
    -   <span data-ttu-id="b84e8-133">**PostalCode**</span><span class="sxs-lookup"><span data-stu-id="b84e8-133">**PostalCode**</span></span>  
  
6.  <span data-ttu-id="b84e8-134">在 [檔案] 功能表上，按一下 [**全部儲存**]。</span><span class="sxs-lookup"><span data-stu-id="b84e8-134">On the File menu, click **Save All**.</span></span>  
  
## <a name="adding-attributes-to-the-product-dimension"></a><span data-ttu-id="b84e8-135">將屬性加入至 [產品] 維度</span><span class="sxs-lookup"><span data-stu-id="b84e8-135">Adding Attributes to the Product Dimension</span></span>  
  
#### <a name="to-add-attributes"></a><span data-ttu-id="b84e8-136">加入屬性</span><span class="sxs-lookup"><span data-stu-id="b84e8-136">To add attributes</span></span>  
  
1.  <span data-ttu-id="b84e8-137">針對 [產品] 維度開啟維度設計師。</span><span class="sxs-lookup"><span data-stu-id="b84e8-137">Open Dimension Designer for the Product dimension.</span></span> <span data-ttu-id="b84e8-138">按兩下方案總管中的 [產品]\*\*\*\* 維度。</span><span class="sxs-lookup"><span data-stu-id="b84e8-138">Double-click the **Product** dimension in Solution Explorer.</span></span>  
  
2.  <span data-ttu-id="b84e8-139">在 [屬性]\*\*\*\* 窗格中，注意由 Cube 精靈所建立的 [產品金鑰] 屬性。</span><span class="sxs-lookup"><span data-stu-id="b84e8-139">In the **Attributes** pane, notice the Product Key attribute that was created by the Cube Wizard.</span></span>  
  
3.  <span data-ttu-id="b84e8-140">在 [維度結構]\*\*\*\* 索引標籤的工具列上，確定用來檢視 [資料來源檢視]\*\*\*\* 窗格中資料表的 [顯示比例] 圖示設為 100%。</span><span class="sxs-lookup"><span data-stu-id="b84e8-140">On the toolbar of the **Dimension Structure** tab, make sure the Zoom icon to view the tables in the **Data Source View** pane is set at 100 percent.</span></span>  
  
4.  <span data-ttu-id="b84e8-141">將下列資料行，從 [資料來源檢視]\*\*\*\* 窗格中的 [產品]\*\*\*\* 資料表拖曳至 [屬性]\*\*\*\* 窗格：</span><span class="sxs-lookup"><span data-stu-id="b84e8-141">Drag the following columns from the **Product** table in the **Data Source View** pane to the **Attributes** pane:</span></span>  
  
    -   <span data-ttu-id="b84e8-142">**StandardCost**</span><span class="sxs-lookup"><span data-stu-id="b84e8-142">**StandardCost**</span></span>  
  
    -   <span data-ttu-id="b84e8-143">**色彩**</span><span class="sxs-lookup"><span data-stu-id="b84e8-143">**Color**</span></span>  
  
    -   <span data-ttu-id="b84e8-144">**SafetyStockLevel**</span><span class="sxs-lookup"><span data-stu-id="b84e8-144">**SafetyStockLevel**</span></span>  
  
    -   <span data-ttu-id="b84e8-145">**ReorderPoint**</span><span class="sxs-lookup"><span data-stu-id="b84e8-145">**ReorderPoint**</span></span>  
  
    -   <span data-ttu-id="b84e8-146">**ListPrice**</span><span class="sxs-lookup"><span data-stu-id="b84e8-146">**ListPrice**</span></span>  
  
    -   <span data-ttu-id="b84e8-147">**大小**</span><span class="sxs-lookup"><span data-stu-id="b84e8-147">**Size**</span></span>  
  
    -   <span data-ttu-id="b84e8-148">**SizeRange**</span><span class="sxs-lookup"><span data-stu-id="b84e8-148">**SizeRange**</span></span>  
  
    -   <span data-ttu-id="b84e8-149">**Weight**</span><span class="sxs-lookup"><span data-stu-id="b84e8-149">**Weight**</span></span>  
  
    -   <span data-ttu-id="b84e8-150">**DaysToManufacture**</span><span class="sxs-lookup"><span data-stu-id="b84e8-150">**DaysToManufacture**</span></span>  
  
    -   <span data-ttu-id="b84e8-151">**ProductLine**</span><span class="sxs-lookup"><span data-stu-id="b84e8-151">**ProductLine**</span></span>  
  
    -   <span data-ttu-id="b84e8-152">**DealerPrice**</span><span class="sxs-lookup"><span data-stu-id="b84e8-152">**DealerPrice**</span></span>  
  
    -   <span data-ttu-id="b84e8-153">**類別**</span><span class="sxs-lookup"><span data-stu-id="b84e8-153">**Class**</span></span>  
  
    -   <span data-ttu-id="b84e8-154">**Style**</span><span class="sxs-lookup"><span data-stu-id="b84e8-154">**Style**</span></span>  
  
    -   <span data-ttu-id="b84e8-155">**ModelName**</span><span class="sxs-lookup"><span data-stu-id="b84e8-155">**ModelName**</span></span>  
  
    -   <span data-ttu-id="b84e8-156">**開始**</span><span class="sxs-lookup"><span data-stu-id="b84e8-156">**StartDate**</span></span>  
  
    -   <span data-ttu-id="b84e8-157">**終止**</span><span class="sxs-lookup"><span data-stu-id="b84e8-157">**EndDate**</span></span>  
  
    -   <span data-ttu-id="b84e8-158">**狀態**</span><span class="sxs-lookup"><span data-stu-id="b84e8-158">**Status**</span></span>  
  
5.  <span data-ttu-id="b84e8-159">在 [檔案] 功能表上，按一下 [**全部儲存**]。</span><span class="sxs-lookup"><span data-stu-id="b84e8-159">On the File menu, click **Save All**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="b84e8-160">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="b84e8-160">Next Task in Lesson</span></span>  
 [<span data-ttu-id="b84e8-161">檢閱 Cube 和維度屬性</span><span class="sxs-lookup"><span data-stu-id="b84e8-161">Reviewing Cube and Dimension Properties</span></span>](lesson-2-4-reviewing-cube-and-dimension-properties.md)  
  
## <a name="see-also"></a><span data-ttu-id="b84e8-162">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b84e8-162">See Also</span></span>  
 [<span data-ttu-id="b84e8-163">維度屬性 (attribute) 屬性 (property) 參考</span><span class="sxs-lookup"><span data-stu-id="b84e8-163">Dimension Attribute Properties Reference</span></span>](multidimensional-models/dimension-attribute-properties-reference.md)  
  
  
