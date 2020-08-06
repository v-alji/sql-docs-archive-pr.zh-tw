---
title: 建立網域屬性 (適用於 Excel 的 MDS 增益集) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 7b3e30dc-8f41-4a5d-8009-ae5a4426a64b
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: bda0c7f63ad380aaea5d980d2e729822ec9a3d22
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584619"
---
# <a name="create-a-domain-based-attribute-mds-add-in-for-excel"></a><span data-ttu-id="40393-102">建立網域屬性 (適用於 Excel 的 MDS 增益集)</span><span class="sxs-lookup"><span data-stu-id="40393-102">Create a Domain-based Attribute (MDS Add-in for Excel)</span></span>
  <span data-ttu-id="40393-103">在 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]中，當系統管理員想要將資料行中的值限制為一組特定的值時，可以建立網域屬性。</span><span class="sxs-lookup"><span data-stu-id="40393-103">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], administrators can create a domain-based attribute when they want to constrain the values in a column to a specific set of values.</span></span>  
  
 <span data-ttu-id="40393-104">值可以已經在工作表中，也可以來自現有實體。</span><span class="sxs-lookup"><span data-stu-id="40393-104">The values can already be in the worksheet or they can come from an existing entity.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="40393-105">如果使用者在受條件約束的資料行中輸入值，而不是從清單中選取，在發行時 **$InputStatus$** 資料行中會顯示錯誤。</span><span class="sxs-lookup"><span data-stu-id="40393-105">If users type a value in the constrained column, rather than selecting from the list, errors are displayed in the **$InputStatus$** column when they publish.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="40393-106">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="40393-106">Prerequisites</span></span>  
 <span data-ttu-id="40393-107">若要執行此程序：</span><span class="sxs-lookup"><span data-stu-id="40393-107">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="40393-108">您必須擁有存取 [系統管理]\*\*\*\* 和總管\*\*\*\* 功能區域的權限。</span><span class="sxs-lookup"><span data-stu-id="40393-108">You must have permission to access the **System Administration** and **Explorer** functional areas.</span></span>  
  
-   <span data-ttu-id="40393-109">您必須是模型管理員。</span><span class="sxs-lookup"><span data-stu-id="40393-109">You must be a model administrator.</span></span> <span data-ttu-id="40393-110">如需詳細資訊，請參閱系統[管理員 &#40;Master Data Services&#41;](../administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="40393-110">For more information, see [Administrators &#40;Master Data Services&#41;](../administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="40393-111">模型和實體必須已經存在。</span><span class="sxs-lookup"><span data-stu-id="40393-111">The model and entity must already exist.</span></span>  
  
### <a name="to-perform-this-procedure"></a><span data-ttu-id="40393-112">若要執行此程序：</span><span class="sxs-lookup"><span data-stu-id="40393-112">To perform this procedure:</span></span>  
  
1.  <span data-ttu-id="40393-113">在 Excel 中，載入包含您想要限制之資料行 (屬性) 的實體。</span><span class="sxs-lookup"><span data-stu-id="40393-113">In Excel, load the entity that contains the column (attribute) you want to constrain.</span></span> <span data-ttu-id="40393-114">如需詳細資訊，請參閱將[資料從 MDS 載入 Excel](export-data-to-excel-from-master-data-services.md)中。</span><span class="sxs-lookup"><span data-stu-id="40393-114">For more information, see [Load Data from MDS into Excel](export-data-to-excel-from-master-data-services.md).</span></span>  
  
2.  <span data-ttu-id="40393-115">在您想要限制的資料行中按一下任何資料格。</span><span class="sxs-lookup"><span data-stu-id="40393-115">Click any cell in the column you want to constrain.</span></span>  
  
3.  <span data-ttu-id="40393-116">在 [建立模型]\*\*\*\* 群組中，按一下 [屬性內容]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="40393-116">In the **Build Model** group, click **Attribute Properties**.</span></span>  
  
4.  <span data-ttu-id="40393-117">在 [屬性內容]\*\*\*\* 對話方塊中，從 [屬性類型]\*\*\*\* 清單中選擇 [受條件約束的清單 (網域)]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="40393-117">In the **Attribute Properties** dialog box, in the **Attribute type** list, choose **Constrained list (domain-based)**.</span></span>  
  
5.  <span data-ttu-id="40393-118">在 [使用下列來源的值擴展屬性]\*\*\*\* 清單中：</span><span class="sxs-lookup"><span data-stu-id="40393-118">In the **Populate the attribute with values from** list:</span></span>  
  
    -   <span data-ttu-id="40393-119">若要使用工作表中的值，請選擇 [選取的資料行]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="40393-119">To use values from the worksheet, choose **the selected column**.</span></span> <span data-ttu-id="40393-120">將會以選取的資料行中的值建立新的實體和新的暫存資料表。</span><span class="sxs-lookup"><span data-stu-id="40393-120">A new entity and new staging table will be created with the values from the selected column.</span></span>  
  
    -   <span data-ttu-id="40393-121">若要使用現有實體中的值，請選擇實體的名稱。</span><span class="sxs-lookup"><span data-stu-id="40393-121">To use values from an existing entity, choose the name of the entity.</span></span>  
  
6.  <span data-ttu-id="40393-122">如果您在上一個步驟中選擇 [選取的資料行]\*\*\*\*，請在 [新實體名稱]\*\*\*\* 方塊中輸入新實體的名稱。</span><span class="sxs-lookup"><span data-stu-id="40393-122">If you chose **the selected column** in the previous step, in the **New entity name** box, type a name for the new entity.</span></span> <span data-ttu-id="40393-123">此名稱可以與資料行 (屬性) 名稱相同。</span><span class="sxs-lookup"><span data-stu-id="40393-123">This can be the same as the column (attribute) name.</span></span>  
  
7.  <span data-ttu-id="40393-124">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="40393-124">Click **OK**.</span></span> <span data-ttu-id="40393-125">資料行中的每個資料格現在都有一個可供使用者選擇的值清單。</span><span class="sxs-lookup"><span data-stu-id="40393-125">Each cell in the column now has a list of values for users to choose from.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="40393-126">後續步驟</span><span class="sxs-lookup"><span data-stu-id="40393-126">Next Steps</span></span>  
  
-   <span data-ttu-id="40393-127">若要在受條件約束的清單中加入及刪除值，請載入屬性所依據的實體。</span><span class="sxs-lookup"><span data-stu-id="40393-127">To add and delete values in the constrained list, load the entity that the attribute is based on.</span></span> <span data-ttu-id="40393-128">如需載入實體的詳細資訊，請參閱將[資料從 MDS 載入 Excel](export-data-to-excel-from-master-data-services.md)中。</span><span class="sxs-lookup"><span data-stu-id="40393-128">For more information on loading entities, see [Load Data from MDS into Excel](export-data-to-excel-from-master-data-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40393-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="40393-129">See Also</span></span>  
 <span data-ttu-id="40393-130">[以網域為基礎的屬性 &#40;Master Data Services&#41;](../domain-based-attributes-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="40393-130">[Domain-Based Attributes &#40;Master Data Services&#41;](../domain-based-attributes-master-data-services.md) </span></span>  
 <span data-ttu-id="40393-131">[&#40;適用于 Excel 的 MDS 增益集建立實體&#41;](create-an-entity-mds-add-in-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="40393-131">[Create an Entity &#40;MDS Add-in for Excel&#41;](create-an-entity-mds-add-in-for-excel.md) </span></span>  
 [<span data-ttu-id="40393-132">建立模型 &#40;適用於 Excel 的 MDS 增益集&#41;</span><span class="sxs-lookup"><span data-stu-id="40393-132">Building a Model &#40;MDS Add-in for Excel&#41;</span></span>](building-a-model-mds-add-in-for-excel.md)  
  
  
