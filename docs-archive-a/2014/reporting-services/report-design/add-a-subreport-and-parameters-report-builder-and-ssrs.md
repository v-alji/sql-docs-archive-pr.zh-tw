---
title: 新增子報表和參數 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10093"
- sql12.rtp.rptdesigner.subreportproperties.general.f1
ms.assetid: 94f960f8-a629-4f1e-8277-c3b8f0680d98
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3aeede343763ea5fc8fbdfde179208f98fa1a2ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585036"
---
# <a name="add-a-subreport-and-parameters-report-builder-and-ssrs"></a><span data-ttu-id="32d00-102">加入子報表和參數 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="32d00-102">Add a Subreport and Parameters (Report Builder and SSRS)</span></span>
  <span data-ttu-id="32d00-103">當您想要建立主報表，而該主報表為多個相關報表的容器時，請在報表中加入子報表。</span><span class="sxs-lookup"><span data-stu-id="32d00-103">Add subreports to a report when you want to create a main report that is a container for multiple related reports.</span></span> <span data-ttu-id="32d00-104">子報表是另一個報表的參考。</span><span class="sxs-lookup"><span data-stu-id="32d00-104">A subreport is a reference to another report.</span></span> <span data-ttu-id="32d00-105">若要透過資料值讓報表產生關聯 (例如，讓多個報表都顯示同一位客戶的資料)，您必須設計參數化報表 (例如，顯示特定客戶之詳細資料的報表) 當做子報表。</span><span class="sxs-lookup"><span data-stu-id="32d00-105">To relate the reports through data values (for example, to have multiple reports show data for the same customer), you must design a parameterized report (for example, a report that shows the details for a specific customer) as the subreport.</span></span> <span data-ttu-id="32d00-106">當您將子報表加入到主報表時，可以指定要傳遞給子報表的參數。</span><span class="sxs-lookup"><span data-stu-id="32d00-106">When you add a subreport to the main report, you can specify parameters to pass to the subreport.</span></span>  
  
 <span data-ttu-id="32d00-107">您也可以將子報表加入到資料表或矩陣中的動態資料列或資料行。</span><span class="sxs-lookup"><span data-stu-id="32d00-107">You can also add subreports to dynamic rows or columns in a table or matrix.</span></span> <span data-ttu-id="32d00-108">當處理主報表時，將會針對每一個資料列處理子報表。</span><span class="sxs-lookup"><span data-stu-id="32d00-108">When the main report is processed, the subreport is processed for each row.</span></span> <span data-ttu-id="32d00-109">在此情況下，請考慮是否可以使用資料區或巢狀資料區來達到所要的效果。</span><span class="sxs-lookup"><span data-stu-id="32d00-109">In this case, consider whether you can achieve the desired effect by using data regions or nested data regions.</span></span>  
  
 <span data-ttu-id="32d00-110">若要將子報表加入至報表，您必須先建立做為子報表的報表。</span><span class="sxs-lookup"><span data-stu-id="32d00-110">To add a subreport to a report, you must first create the report that will act as the subreport.</span></span> <span data-ttu-id="32d00-111">如需建立子報表的詳細資訊，請參閱 [子報表 &#40;報表產生器及 SSRS&#41;](subreports-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="32d00-111">For more information on creating the subreport, see [Subreports &#40;Report Builder and SSRS&#41;](subreports-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-subreport"></a><span data-ttu-id="32d00-112">若要加入子報表</span><span class="sxs-lookup"><span data-stu-id="32d00-112">To add a subreport</span></span>  
  
1.  <span data-ttu-id="32d00-113">在 **[插入]** 索引標籤上，按一下 **[子報表]** 。</span><span class="sxs-lookup"><span data-stu-id="32d00-113">On the **Insert** tab, click **Subreport**.</span></span>  
  
2.  <span data-ttu-id="32d00-114">在設計介面上，按一下報表上的某個位置，然後將方塊拖曳至所需的子報表大小。</span><span class="sxs-lookup"><span data-stu-id="32d00-114">On the design surface, click a location on the report and then drag a box to the desired size of the subreport.</span></span> <span data-ttu-id="32d00-115">另外，您也可以按一下設計介面來建立預設大小的子報表。</span><span class="sxs-lookup"><span data-stu-id="32d00-115">Alternatively, click the design surface to create a subreport of default size.</span></span>  
  
3.  <span data-ttu-id="32d00-116">以滑鼠右鍵按一下子報表，然後按一下 [子報表屬性]  。</span><span class="sxs-lookup"><span data-stu-id="32d00-116">Right-click the subreport, and then click **Subreport Properties**.</span></span>  
  
4.  <span data-ttu-id="32d00-117">在 **[子報表屬性]** 對話方塊中，於 **[名稱]** 文字方塊內輸入名稱或是接受預設值。</span><span class="sxs-lookup"><span data-stu-id="32d00-117">In the **Subreport Properties** dialog box, type a name in the **Name** text box or accept the default.</span></span> <span data-ttu-id="32d00-118">名稱在報表內必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="32d00-118">The name must be unique within the report.</span></span> <span data-ttu-id="32d00-119">根據預設，系統會指派一般名稱，例如 Subreport1 或 Subreport2。</span><span class="sxs-lookup"><span data-stu-id="32d00-119">By default, a general name such as Subreport1 or Subreport2 is assigned.</span></span>  
  
5.  <span data-ttu-id="32d00-120">在 **[將此報表當成子報表]** 方塊中，按一下 **[瀏覽]** ，或輸入報表的名稱。</span><span class="sxs-lookup"><span data-stu-id="32d00-120">In the **Use this report as a subreport** box, click **Browse**, or type the name of the report.</span></span> <span data-ttu-id="32d00-121">建議您按一下 **[瀏覽]** ，因為系統將自動指定子報表的路徑。</span><span class="sxs-lookup"><span data-stu-id="32d00-121">Clicking **Browse** is preferred because the path to the subreport will be specified automatically.</span></span> <span data-ttu-id="32d00-122">您可以透過幾種方式指定報表。</span><span class="sxs-lookup"><span data-stu-id="32d00-122">You can specify the report in the several ways.</span></span> <span data-ttu-id="32d00-123">如需詳細資訊，請參閱[指定外部項目的路徑 &#40;報表產生器及 SSRS&#41;](specifying-paths-to-external-items-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="32d00-123">For more information, see [Specifying Paths to External Items &#40;Report Builder and SSRS&#41;](specifying-paths-to-external-items-report-builder-and-ssrs.md).</span></span>  
  
6.  <span data-ttu-id="32d00-124">(選用) 如果子報表橫跨多頁，針對 [省略分頁符號上的框線] 按一下 [是]，就不會在子報表中轉譯框線。</span><span class="sxs-lookup"><span data-stu-id="32d00-124">(Optional) Click **Yes** for **Omit border on page break** to prevent a border from being rendered in the middle of the subreport if the subreport spans more than one page.</span></span>  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-specify-parameters-to-pass-to-a-subreport"></a><span data-ttu-id="32d00-125">指定要傳遞給子報表的參數</span><span class="sxs-lookup"><span data-stu-id="32d00-125">To specify parameters to pass to a subreport</span></span>  
  
1.  <span data-ttu-id="32d00-126">在 [設計] 檢視中，以滑鼠右鍵按一下子報表，然後按一下 [子報表屬性]  。</span><span class="sxs-lookup"><span data-stu-id="32d00-126">In Design view, right-click the subreport and then click **Subreport Properties**.</span></span>  
  
2.  <span data-ttu-id="32d00-127">在 **[子報表屬性]** 對話方塊中，按一下 **[參數]** 。</span><span class="sxs-lookup"><span data-stu-id="32d00-127">In the **Subreport Properties** dialog box, click **Parameters**.</span></span>  
  
3.  <span data-ttu-id="32d00-128">按一下 [新增]  。</span><span class="sxs-lookup"><span data-stu-id="32d00-128">Click **Add**.</span></span> <span data-ttu-id="32d00-129">新的資料列就會加入至參數方格。</span><span class="sxs-lookup"><span data-stu-id="32d00-129">A new row is added to the parameter grid.</span></span>  
  
4.  <span data-ttu-id="32d00-130">在 **[名稱]** 文字方塊中，輸入子報表中的參數名稱或從清單方塊加以選擇。</span><span class="sxs-lookup"><span data-stu-id="32d00-130">In the **Name** text box, type the name of a parameter in the subreport or choose it from the list box.</span></span> <span data-ttu-id="32d00-131">此名稱必須與子報表中的報表參數 (而非查詢參數) 相符。</span><span class="sxs-lookup"><span data-stu-id="32d00-131">This name must match a report parameter, not a query parameter, in the subreport.</span></span>  
  
5.  <span data-ttu-id="32d00-132">在 **[值]** 清單方塊中，輸入或選取要傳遞給子報表的值。</span><span class="sxs-lookup"><span data-stu-id="32d00-132">In the **Value** list box, type or select a value to pass to the subreport.</span></span> <span data-ttu-id="32d00-133">這個值可以是靜態文字，也可以是參考主報表中的欄位或其他物件的運算式。</span><span class="sxs-lookup"><span data-stu-id="32d00-133">This value can be static text or an expression that references a field or other object in the main report.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="32d00-134">在報表產生器中，如果 [參數]  清單遺漏某參數，而子報表中定義了預設值，則系統會正確處理子報表。</span><span class="sxs-lookup"><span data-stu-id="32d00-134">In Report Builder, if a parameter is missing from the **Parameters** list and the subreport has a default value defined, the subreport will be processed correctly.</span></span>  
    >   
    >  <span data-ttu-id="32d00-135">在報表設計師中，子報表所需要的所有參數都必須包括在 **[參數]** 清單中。</span><span class="sxs-lookup"><span data-stu-id="32d00-135">In Report Designer, all parameters that are required by the subreport must be included in the **Parameters** list.</span></span> <span data-ttu-id="32d00-136">如果遺漏必要的參數，子報表便無法正確顯示在主報表內。</span><span class="sxs-lookup"><span data-stu-id="32d00-136">If a required parameter is missing, the subreport is not displayed correctly in the main report.</span></span>  
  
6.  <span data-ttu-id="32d00-137">重複步驟 3-5 來指定每個子報表參數的名稱和值。</span><span class="sxs-lookup"><span data-stu-id="32d00-137">Repeat steps 3-5 to specify a name and value for each subreport parameter.</span></span>  
  
7.  <span data-ttu-id="32d00-138">若要刪除子報表參數，請在參數方格中按一下參數，然後按一下 **[刪除]** 。</span><span class="sxs-lookup"><span data-stu-id="32d00-138">To delete a subreport parameter, click the parameter in the parameter grid, and then click **Delete**.</span></span>  
  
8.  <span data-ttu-id="32d00-139">若要變更子報表參數的順序，請按一下參數，然後按一下向上按鈕或向下按鈕。</span><span class="sxs-lookup"><span data-stu-id="32d00-139">To change the order of a subreport parameter, click the parameter, and then click the up button or the down button.</span></span>  
  
     <span data-ttu-id="32d00-140">變更子報表參數的順序並不會影響子報表的處理。</span><span class="sxs-lookup"><span data-stu-id="32d00-140">Changing the order of a subreport parameter does not affect the processing of the subreport.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32d00-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="32d00-141">See Also</span></span>  
 <span data-ttu-id="32d00-142">[子報表 &#40;報表產生器及 SSRS&#41;](subreports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="32d00-142">[Subreports &#40;Report Builder and SSRS&#41;](subreports-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="32d00-143">轉譯行為 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="32d00-143">Rendering Behaviors &#40;Report Builder  and SSRS&#41;</span></span>](rendering-behaviors-report-builder-and-ssrs.md)  
  
  
