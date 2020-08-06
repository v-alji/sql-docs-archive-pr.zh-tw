---
title: 將 Excel 中的資料發佈到 MDS (適用于 Excel 的 MDS 增益集) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 89fce454-a816-4b33-a26a-d1b9741d269b
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 597a954760816d8938628974998fe8f6daad1af5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599036"
---
# <a name="publish-data-from-excel-to-mds-mds-add-in-for-excel"></a><span data-ttu-id="a1680-102">將資料從 Excel 發行至 MDS (適用於 Excel 的 MDS 增益集)</span><span class="sxs-lookup"><span data-stu-id="a1680-102">Publish Data from Excel to MDS (MDS Add-in for Excel)</span></span>
  <span data-ttu-id="a1680-103">在 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]中，若您已結束使用 Excel 且想要儲存變更，以讓其他使用者能夠存取，請將資料發行至 MDS 儲存機制。</span><span class="sxs-lookup"><span data-stu-id="a1680-103">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], publish data to the MDS repository when you are finished working in Excel and want to save your changes so other users have access to them.</span></span>  
  
> [!NOTE]
>  -   <span data-ttu-id="a1680-104">當您發行變更時，系統會刪除 MDS 管理之資料格的註解。</span><span class="sxs-lookup"><span data-stu-id="a1680-104">When you publish changes, comments on MDS-managed cells are deleted.</span></span>  
> -   <span data-ttu-id="a1680-105">MDS 管理的資料格中不支援公式。</span><span class="sxs-lookup"><span data-stu-id="a1680-105">A formula is not supported in an MDS-managed cell.</span></span> <span data-ttu-id="a1680-106">MDS 管理之資料格中的公式會處理為文字值。</span><span class="sxs-lookup"><span data-stu-id="a1680-106">A formula in an MDS-managed cell is handled as a text value.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="a1680-107">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="a1680-107">Prerequisites</span></span>  
 <span data-ttu-id="a1680-108">若要執行此程序：</span><span class="sxs-lookup"><span data-stu-id="a1680-108">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="a1680-109">您必須擁有存取 [ **Explorer** ] 功能區域的許可權。</span><span class="sxs-lookup"><span data-stu-id="a1680-109">You must have permission to access the **Explorer** functional area.</span></span>  
  
-   <span data-ttu-id="a1680-110">使用中工作表必須包含 MDS 管理的資料，而且您必須已經對 MDS 管理的資料進行變更或加入作業。</span><span class="sxs-lookup"><span data-stu-id="a1680-110">The active worksheet must contain MDS-managed data and you must have made changes or additions to the MDS-managed data.</span></span>  
  
-   <span data-ttu-id="a1680-111">如果您要加入成員，而且系統會自動產生實體的代碼，您就不需要指定 **Code** 值。</span><span class="sxs-lookup"><span data-stu-id="a1680-111">If you are adding members, you do not have to specify a **Code** value if codes for the entity are being automatically generated.</span></span> <span data-ttu-id="a1680-112">如需詳細資訊，請參閱[自動建立程式碼 &#40;Master Data Services&#41;](../automatic-code-creation-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="a1680-112">For more information, see [Automatic Code Creation &#40;Master Data Services&#41;](../automatic-code-creation-master-data-services.md).</span></span>  
  
### <a name="to-publish-data-to-the-mds-repository"></a><span data-ttu-id="a1680-113">若要將資料發行至 MDS 儲存機制</span><span class="sxs-lookup"><span data-stu-id="a1680-113">To publish data to the MDS repository</span></span>  
  
1.  <span data-ttu-id="a1680-114">按一下 [發行和驗證]\*\*\*\* 群組中的 [發行]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a1680-114">In the **Publish and Validate** group, click **Publish**.</span></span>  
  
2.  <span data-ttu-id="a1680-115">選擇性。</span><span class="sxs-lookup"><span data-stu-id="a1680-115">Optional.</span></span> <span data-ttu-id="a1680-116">如果顯示 [發行並註解]\*\*\*\* 對話方塊，請選擇要針對所有更新共用相同的註解，還是個別註解每個變更。</span><span class="sxs-lookup"><span data-stu-id="a1680-116">If the **Publish and Annotate** dialog box is displayed, choose to share the same annotation (comment) for all updates, or to annotate each change individually.</span></span>  
  
3.  <span data-ttu-id="a1680-117">選擇性。</span><span class="sxs-lookup"><span data-stu-id="a1680-117">Optional.</span></span> <span data-ttu-id="a1680-118">選取 [不要再顯示這個對話方塊]\*\*\*\* 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="a1680-118">Select the **Do not show this dialog box again** check box.</span></span> <span data-ttu-id="a1680-119">未來，您隨時都可以透過選擇 [設定]\*\*\*\* 並選取 [發行時顯示發行和註解對話方塊]\*\*\*\* 核取方塊，顯示此對話方塊。</span><span class="sxs-lookup"><span data-stu-id="a1680-119">You can always show the dialog box in the future by choosing **Settings** and selecting the **Show Publish and Annotate dialog box when publishing** check box.</span></span>  
  
4.  <span data-ttu-id="a1680-120">按一下 [發佈]。</span><span class="sxs-lookup"><span data-stu-id="a1680-120">Click **Publish**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a1680-121">如果您要將新的成員 (資料列) 加入至工作表，但是無法順利將它們發行至 MDS 儲存機制，表示您可能沒有工作表中所有屬性的 [更新]\*\*\*\* 權限。</span><span class="sxs-lookup"><span data-stu-id="a1680-121">If you are adding new members (rows) to your worksheet and you cannot successfully publish them to the MDS repository, you may not have **Update** permission to all of the attributes in the worksheet.</span></span> <span data-ttu-id="a1680-122">在 [檢閱]\*\*\*\* 索引標籤上，按一下 [變更]\*\*\*\* 群組中的 [取消保護工作表]\*\*\*\*，再次嘗試發行。</span><span class="sxs-lookup"><span data-stu-id="a1680-122">On the **Review** tab, in the **Changes** group, click **Unprotect Sheet** and try to publish again.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="a1680-123">後續步驟</span><span class="sxs-lookup"><span data-stu-id="a1680-123">Next Steps</span></span>  
 [<span data-ttu-id="a1680-124">套用商務規則 &#40;適用於 Excel 的 MDS 增益集&#41;</span><span class="sxs-lookup"><span data-stu-id="a1680-124">Apply Business Rules &#40;MDS Add-in for Excel&#41;</span></span>](apply-business-rules-mds-add-in-for-excel.md)  
  
## <a name="see-also"></a><span data-ttu-id="a1680-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a1680-125">See Also</span></span>  
 <span data-ttu-id="a1680-126">[發行資料 &#40;適用于 Excel 的 MDS 增益集&#41;](overview-importing-data-from-excel-mds-add-in-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="a1680-126">[Publishing Data &#40;MDS Add-in for Excel&#41;](overview-importing-data-from-excel-mds-add-in-for-excel.md) </span></span>  
 [<span data-ttu-id="a1680-127">驗證資料 &#40;適用於 Excel 的 MDS 增益集&#41;</span><span class="sxs-lookup"><span data-stu-id="a1680-127">Validating Data &#40;MDS Add-in for Excel&#41;</span></span>](validating-data-mds-add-in-for-excel.md)  
  
  
