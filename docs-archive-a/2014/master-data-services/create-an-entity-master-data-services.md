---
title: 建立實體 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- entities [Master Data Services], creating
- creating entities [Master Data Services]
ms.assetid: d9a6a51e-7b53-4785-a118-3baeb7ca2d48
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 7cefdedd07ee248f12b3b17337878934a2b1aa84
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606391"
---
# <a name="create-an-entity-master-data-services"></a><span data-ttu-id="61dc5-102">建立實體 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="61dc5-102">Create an Entity (Master Data Services)</span></span>
  <span data-ttu-id="61dc5-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，建立實體以包含成員及其屬性。</span><span class="sxs-lookup"><span data-stu-id="61dc5-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], create an entity to contain members and their attributes.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="61dc5-104">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="61dc5-104">Prerequisites</span></span>  
 <span data-ttu-id="61dc5-105">若要執行此程序：</span><span class="sxs-lookup"><span data-stu-id="61dc5-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="61dc5-106">您必須擁有存取 **[系統管理]** 功能區域的權限。</span><span class="sxs-lookup"><span data-stu-id="61dc5-106">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="61dc5-107">您必須是模型管理員。</span><span class="sxs-lookup"><span data-stu-id="61dc5-107">You must be a model administrator.</span></span> <span data-ttu-id="61dc5-108">如需詳細資訊，請參閱系統[管理員 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="61dc5-108">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="61dc5-109">模型必須存在。</span><span class="sxs-lookup"><span data-stu-id="61dc5-109">A model must exist.</span></span> <span data-ttu-id="61dc5-110">如需詳細資訊，請參閱[建立模型 &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-model-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="61dc5-110">For more information, see [Create a Model &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-model-master-data-services.md).</span></span>  
  
### <a name="to-create-an-entity"></a><span data-ttu-id="61dc5-111">若要建立實體</span><span class="sxs-lookup"><span data-stu-id="61dc5-111">To create an entity</span></span>  
  
1.  <span data-ttu-id="61dc5-112">在 [ [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]] 中，按一下 **[系統管理]**。</span><span class="sxs-lookup"><span data-stu-id="61dc5-112">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="61dc5-113">在 **[模型檢視]** 頁面上，從功能表列指向 **[管理]** ，然後按一下 **[實體]**。</span><span class="sxs-lookup"><span data-stu-id="61dc5-113">On the **Model View** page, from the menu bar, point to **Manage** and click **Entities**.</span></span>  
  
3.  <span data-ttu-id="61dc5-114">在 **[實體維護]** 頁面上，選取 **[模型]** 清單中的模型。</span><span class="sxs-lookup"><span data-stu-id="61dc5-114">On the **Entity Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="61dc5-115">按一下 [**新增實體**]。</span><span class="sxs-lookup"><span data-stu-id="61dc5-115">Click **Add entity**.</span></span>  
  
5.  <span data-ttu-id="61dc5-116">在 [**機構名稱**] 方塊中，輸入實體的名稱。</span><span class="sxs-lookup"><span data-stu-id="61dc5-116">In the **Entity name** box, type the name of the entity.</span></span>  
  
6.  <span data-ttu-id="61dc5-117">在 [**臨時表的名稱]** 方塊中，輸入臨時表的名稱。</span><span class="sxs-lookup"><span data-stu-id="61dc5-117">In the **Name for staging tables** box, type a name for the staging table.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="61dc5-118">使用模型名稱當做暫存資料表名稱的一部分，例如 *Modelname_Entityname*。</span><span class="sxs-lookup"><span data-stu-id="61dc5-118">Use the model name as part of the staging table name, for example *Modelname_Entityname*.</span></span> <span data-ttu-id="61dc5-119">這樣會更容易在資料庫中找到資料表。</span><span class="sxs-lookup"><span data-stu-id="61dc5-119">This makes the tables easier to find in the database.</span></span> <span data-ttu-id="61dc5-120">如需有關臨時表的詳細資訊，請參閱[資料匯入 &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="61dc5-120">For more information about the staging tables, see [Data Import &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md).</span></span>  
  
7.  <span data-ttu-id="61dc5-121">選擇性。</span><span class="sxs-lookup"><span data-stu-id="61dc5-121">Optional.</span></span> <span data-ttu-id="61dc5-122">選取 **[自動建立字碼值]** 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="61dc5-122">Select the **Create Code values automatically** check box.</span></span> <span data-ttu-id="61dc5-123">如需詳細資訊，請參閱[自動建立程式碼 &#40;Master Data Services&#41;](../../2014/master-data-services/automatic-code-creation-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="61dc5-123">For more information, see [Automatic Code Creation &#40;Master Data Services&#41;](../../2014/master-data-services/automatic-code-creation-master-data-services.md).</span></span>  
  
8.  <span data-ttu-id="61dc5-124">從 [**啟用明確階層和集合**] 清單中，選取下列其中一個選項：</span><span class="sxs-lookup"><span data-stu-id="61dc5-124">From the **Enable explicit hierarchies and collections** list, select one of the following options:</span></span>  
  
    -   <span data-ttu-id="61dc5-125">**否**。</span><span class="sxs-lookup"><span data-stu-id="61dc5-125">**No**.</span></span> <span data-ttu-id="61dc5-126">如果不需要啟用明確階層和集合的實體，請選取這個選項。</span><span class="sxs-lookup"><span data-stu-id="61dc5-126">Select this option if you do not need to enable the entity for explicit hierarchies and collections.</span></span> <span data-ttu-id="61dc5-127">您稍後可以視需要加以變更。</span><span class="sxs-lookup"><span data-stu-id="61dc5-127">You can change this later if needed.</span></span>  
  
    -   <span data-ttu-id="61dc5-128">**是**。</span><span class="sxs-lookup"><span data-stu-id="61dc5-128">**Yes**.</span></span> <span data-ttu-id="61dc5-129">如果想要啟用明確階層和集合的實體，請選取這個選項。</span><span class="sxs-lookup"><span data-stu-id="61dc5-129">Select this option when you want to enable the entity for explicit hierarchies and collections.</span></span> <span data-ttu-id="61dc5-130">在 [**明確階層名稱**] 方塊中，輸入名稱。</span><span class="sxs-lookup"><span data-stu-id="61dc5-130">In the **Explicit hierarchy name** box, type a name.</span></span> <span data-ttu-id="61dc5-131">（選擇性）選取 [強制階層]， \*\* (包含所有分葉成員\*\*，讓明確階層成為強制階層。</span><span class="sxs-lookup"><span data-stu-id="61dc5-131">Optionally, select **Mandatory hierarchy (all leaf members are included** to make the explicit hierarchy a mandatory hierarchy.</span></span>  
  
9. <span data-ttu-id="61dc5-132">按一下 [**儲存實體**]。</span><span class="sxs-lookup"><span data-stu-id="61dc5-132">Click **Save entity**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="61dc5-133">後續步驟</span><span class="sxs-lookup"><span data-stu-id="61dc5-133">Next Steps</span></span>  
  
-   [<span data-ttu-id="61dc5-134">建立文字屬性 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="61dc5-134">Create a Text Attribute &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-text-attribute-master-data-services.md)  
  
-   [<span data-ttu-id="61dc5-135">建立網域屬性 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="61dc5-135">Create a Domain-Based Attribute &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md)  
  
-   [<span data-ttu-id="61dc5-136">建立檔案屬性 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="61dc5-136">Create a File Attribute &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-file-attribute-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="61dc5-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="61dc5-137">See Also</span></span>  
 <span data-ttu-id="61dc5-138">[實體 &#40;Master Data Services&#41;](../../2014/master-data-services/entities-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="61dc5-138">[Entities &#40;Master Data Services&#41;](../../2014/master-data-services/entities-master-data-services.md) </span></span>  
 <span data-ttu-id="61dc5-139">[明確階層 &#40;Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="61dc5-139">[Explicit Hierarchies &#40;Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md) </span></span>  
 <span data-ttu-id="61dc5-140">[變更機構名稱 &#40;Master Data Services&#41;](edit-an-entity-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="61dc5-140">[Change an Entity Name &#40;Master Data Services&#41;](edit-an-entity-master-data-services.md) </span></span>  
 [<span data-ttu-id="61dc5-141">刪除實體 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="61dc5-141">Delete an Entity &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/delete-an-entity-master-data-services.md)  
  
  
