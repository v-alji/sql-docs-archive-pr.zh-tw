---
title: 建立實體 (適用於 Excel 的 MDS 增益集) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: d354abb3-88fe-4b40-a374-f6256b84ffae
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 87ad67f7347da87c67afc11590df6775af4cf3d0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584617"
---
# <a name="create-an-entity-mds-add-in-for-excel"></a><span data-ttu-id="8f760-102">建立實體 (適用於 Excel 的 MDS 增益集)</span><span class="sxs-lookup"><span data-stu-id="8f760-102">Create an Entity (MDS Add-in for Excel)</span></span>
  <span data-ttu-id="8f760-103">在 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]中，系統管理員可以建立新的實體來儲存資料。</span><span class="sxs-lookup"><span data-stu-id="8f760-103">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], administrators can create new entities to store data.</span></span> <span data-ttu-id="8f760-104">當您建立實體時，應該至少載入要儲存的資料樣本。</span><span class="sxs-lookup"><span data-stu-id="8f760-104">When you create an entity you should load at least a sampling of the data you want to store.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="8f760-105">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="8f760-105">Prerequisites</span></span>  
 <span data-ttu-id="8f760-106">若要執行此程序：</span><span class="sxs-lookup"><span data-stu-id="8f760-106">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="8f760-107">您必須擁有存取 [系統管理]\*\*\*\* 和總管\*\*\*\* 功能區域的權限。</span><span class="sxs-lookup"><span data-stu-id="8f760-107">You must have permission to access the **System Administration** and **Explorer** functional areas.</span></span>  
  
-   <span data-ttu-id="8f760-108">您必須是模型管理員。</span><span class="sxs-lookup"><span data-stu-id="8f760-108">You must be a model administrator.</span></span> <span data-ttu-id="8f760-109">如需詳細資訊，請參閱系統[管理員 &#40;Master Data Services&#41;](../administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="8f760-109">For more information, see [Administrators &#40;Master Data Services&#41;](../administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="8f760-110">您必須有要在其中建立實體的現有模型。</span><span class="sxs-lookup"><span data-stu-id="8f760-110">You must have an existing model to create the entity in.</span></span> <span data-ttu-id="8f760-111">如需詳細資訊，請參閱[建立模型 &#40;Master Data Services&#41;](../create-a-model-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="8f760-111">For more information, see [Create a Model &#40;Master Data Services&#41;](../create-a-model-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="8f760-112">確定您的資料符合下列需求：</span><span class="sxs-lookup"><span data-stu-id="8f760-112">Ensure that your data meets the following requirements:</span></span>  
  
    -   <span data-ttu-id="8f760-113">資料應該具有標頭資料列。</span><span class="sxs-lookup"><span data-stu-id="8f760-113">The data should have a header row.</span></span>  
  
    -   <span data-ttu-id="8f760-114">具有 **Name** 和 **Code** 資料行是有幫助的。</span><span class="sxs-lookup"><span data-stu-id="8f760-114">It is helpful to have **Name** and **Code** columns.</span></span> <span data-ttu-id="8f760-115">**Code** 是每個資料列的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="8f760-115">**Code** is a unique identifier for each row.</span></span>  
  
    -   <span data-ttu-id="8f760-116">除了標頭以外，應該至少還有一個資料列。</span><span class="sxs-lookup"><span data-stu-id="8f760-116">You should have at least one row of data other than the header.</span></span> <span data-ttu-id="8f760-117">並不是所有資料行都需要值，但資料應該有代表性，可代表實體中的未來資料。</span><span class="sxs-lookup"><span data-stu-id="8f760-117">All columns do not need values, but the data should be representative of the data that will be in the entity.</span></span>  
  
    -   <span data-ttu-id="8f760-118">如果您有包含唯一識別碼 (在 MDS 中稱為 **Code**) 的資料行，請確定值是唯一的。</span><span class="sxs-lookup"><span data-stu-id="8f760-118">If you have a column that contains a unique identifier (known in MDS as **Code**), ensure that the values are unique.</span></span> <span data-ttu-id="8f760-119">如果沒有資料行包含識別碼，可在建立實體時讓它們自動產生。</span><span class="sxs-lookup"><span data-stu-id="8f760-119">If no column contains identifiers, you can have them generated automatically when you create the entity.</span></span>  
  
    -   <span data-ttu-id="8f760-120">確定沒有資料格包含公式。</span><span class="sxs-lookup"><span data-stu-id="8f760-120">Ensure that no cells contain formulas.</span></span>  
  
    -   <span data-ttu-id="8f760-121">確定沒有資料格包含時間值。</span><span class="sxs-lookup"><span data-stu-id="8f760-121">Ensure that no cells contain time values.</span></span> <span data-ttu-id="8f760-122">日期值可儲存在 MDS 中，但時間值不能。</span><span class="sxs-lookup"><span data-stu-id="8f760-122">Date values can be saved in MDS but time values cannot.</span></span>  
  
### <a name="to-create-an-entity-and-load-data"></a><span data-ttu-id="8f760-123">若要建立實體及載入資料</span><span class="sxs-lookup"><span data-stu-id="8f760-123">To create an entity and load data</span></span>  
  
1.  <span data-ttu-id="8f760-124">開啟或建立 Excel 工作表，其中包含您要載入的資料。</span><span class="sxs-lookup"><span data-stu-id="8f760-124">Open or create an Excel worksheet that contains data you want to load.</span></span>  
  
2.  <span data-ttu-id="8f760-125">選取要載入到新實體的資料格。</span><span class="sxs-lookup"><span data-stu-id="8f760-125">Select the cells you want to load into the new entity.</span></span>  
  
3.  <span data-ttu-id="8f760-126">在 [主要資料]\*\*\*\* 索引標籤的 [建立模型]\*\*\*\* 群組中，按一下 [建立實體]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8f760-126">On the **Master Data** tab, in the **Build Model** group, click **Create Entity**.</span></span>  
  
4.  <span data-ttu-id="8f760-127">如果系統提示您連接到 MDS 儲存機制，請連接。</span><span class="sxs-lookup"><span data-stu-id="8f760-127">If you are prompted to connect to an MDS repository, connect.</span></span>  
  
5.  <span data-ttu-id="8f760-128">在 [建立實體]\*\*\*\* 對話方塊中，保持預設的範圍，或加以變更以套用至要載入的資料。</span><span class="sxs-lookup"><span data-stu-id="8f760-128">In the **Create Entity** dialog box, leave the default range or change it to apply to the data you want to load.</span></span>  
  
6.  <span data-ttu-id="8f760-129">請不要清除 [我的資料有標題]\*\*\*\* 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="8f760-129">Do not clear the **My data has headers** check box.</span></span>  
  
7.  <span data-ttu-id="8f760-130">從 **[模型]** 清單中選取模型。</span><span class="sxs-lookup"><span data-stu-id="8f760-130">From the **Model** list, select a model.</span></span>  
  
8.  <span data-ttu-id="8f760-131">從 **[版本]** 清單中選取版本。</span><span class="sxs-lookup"><span data-stu-id="8f760-131">From the **Version** list, select a version.</span></span>  
  
9. <span data-ttu-id="8f760-132">在 [新實體名稱]\*\*\*\* 方塊中，輸入實體的名稱。</span><span class="sxs-lookup"><span data-stu-id="8f760-132">In the **New entity name** box, type a name for the entity.</span></span>  
  
10. <span data-ttu-id="8f760-133">從 **Code** 清單中，選取包含唯一識別碼的資料行或讓系統自動產生代碼。</span><span class="sxs-lookup"><span data-stu-id="8f760-133">From the **Code** list, select the column that contains unique identifiers or have codes generated automatically.</span></span>  
  
11. <span data-ttu-id="8f760-134">選擇性。</span><span class="sxs-lookup"><span data-stu-id="8f760-134">Optional.</span></span> <span data-ttu-id="8f760-135">從 [名稱]\*\*\*\* 清單中，選取包含每個成員名稱的資料行。</span><span class="sxs-lookup"><span data-stu-id="8f760-135">From the **Name** list, select a column that contains names for each member.</span></span>  
  
12. <span data-ttu-id="8f760-136">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="8f760-136">Click **OK**.</span></span> <span data-ttu-id="8f760-137">成功建立實體時，畫面上會顯示新標頭資料列，反白顯示資料格，而且更新工作表名稱以符合實體名稱。</span><span class="sxs-lookup"><span data-stu-id="8f760-137">When the entity has been created successfully, a new header row is displayed, the cells are highlighted, and the sheet name is updated to match the entity name.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="8f760-138">後續步驟</span><span class="sxs-lookup"><span data-stu-id="8f760-138">Next Steps</span></span>  
  
-   <span data-ttu-id="8f760-139">若要檢視發生的錯誤，請按一下 [發行和驗證]\*\*\*\* 群組中的 [顯示狀態]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8f760-139">To view errors that occurred, in the **Publish and Validate** group, click **Show Status**.</span></span> <span data-ttu-id="8f760-140">ValidationStatus 和 InputStatus 資料行隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="8f760-140">ValidationStatus and InputStatus columns are displayed.</span></span> <span data-ttu-id="8f760-141">如需詳細資訊，請參閱[驗證資料 &#40;MDS 適用於 Excel 的增益集&#41;](validating-data-mds-add-in-for-excel.md)。</span><span class="sxs-lookup"><span data-stu-id="8f760-141">For more information, see [Validating Data &#40;MDS Add-in for Excel&#41;](validating-data-mds-add-in-for-excel.md).</span></span>  
  
-   <span data-ttu-id="8f760-142">確認屬性已建立為預期的資料類型。</span><span class="sxs-lookup"><span data-stu-id="8f760-142">Confirm that the attributes were created as the data type you expected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f760-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8f760-143">See Also</span></span>  
 [<span data-ttu-id="8f760-144">建立網域屬性 &#40;適用於 Excel 的 MDS 增益集&#41;</span><span class="sxs-lookup"><span data-stu-id="8f760-144">Create a Domain-based Attribute &#40;MDS Add-in for Excel&#41;</span></span>](create-a-domain-based-attribute-mds-add-in-for-excel.md)  
  
  
