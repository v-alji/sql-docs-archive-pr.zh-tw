---
title: 重新排序資料行 (適用於 Excel 的 MDS 增益集) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: ac00462e-c0f7-4b8d-86f2-d9eda2598a15
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: f0c47a631ffe699936a8d45bcc4e47e0b6f0a985
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698374"
---
# <a name="reorder-columns-mds-add-in-for-excel"></a><span data-ttu-id="4ace2-102">重新排序資料行 (適用於 Excel 的 MDS 增益集)</span><span class="sxs-lookup"><span data-stu-id="4ace2-102">Reorder Columns (MDS Add-in for Excel)</span></span>
  <span data-ttu-id="4ace2-103">在 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]中，您可以在載入之前篩選清單，藉以重新排序資料行。</span><span class="sxs-lookup"><span data-stu-id="4ace2-103">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], you can reorder columns by filtering the list before loading.</span></span>  
  
 <span data-ttu-id="4ace2-104">當您重新排序 **[篩選]** 對話方塊中的屬性時，會使用新的順序，將資料載入至 Excel。</span><span class="sxs-lookup"><span data-stu-id="4ace2-104">When you reorder attributes in the **Filter** dialog box, the data is loaded into Excel with the new order.</span></span> <span data-ttu-id="4ace2-105">不過，下次您篩選屬性資料時，此順序將會回復到原始設計的順序。</span><span class="sxs-lookup"><span data-stu-id="4ace2-105">However, the next time that you filter the attribute data, the order will revert to the order in the original design.</span></span> <span data-ttu-id="4ace2-106">若要永久變更順序，管理員應該在主資料管理員的 **[系統管理]** 區域中變更順序。</span><span class="sxs-lookup"><span data-stu-id="4ace2-106">To change the order permanently, an administrator should change the order in the **System Administration** area of Master Data Manager.</span></span> <span data-ttu-id="4ace2-107">如需相關資訊，請參閱 [Change the Order of Attributes](../change-the-order-of-attributes.md)。</span><span class="sxs-lookup"><span data-stu-id="4ace2-107">For more information, see [Change the Order of Attributes](../change-the-order-of-attributes.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="4ace2-108">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="4ace2-108">Prerequisites</span></span>  
 <span data-ttu-id="4ace2-109">若要執行此程序：</span><span class="sxs-lookup"><span data-stu-id="4ace2-109">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="4ace2-110">您必須擁有存取 [ **Explorer** ] 功能區域的許可權。</span><span class="sxs-lookup"><span data-stu-id="4ace2-110">You must have permission to access the **Explorer** functional area.</span></span>  
  
### <a name="to-reorder-mds-managed-columns"></a><span data-ttu-id="4ace2-111">若要重新排序 MDS 管理的資料行</span><span class="sxs-lookup"><span data-stu-id="4ace2-111">To reorder MDS-managed columns</span></span>  
  
1.  <span data-ttu-id="4ace2-112">開啟 Excel，然後在 **[主要資料]** 索引標籤上，連接到 MDS 儲存機制。</span><span class="sxs-lookup"><span data-stu-id="4ace2-112">Open Excel and on the **Master Data** tab, connect to an MDS repository.</span></span> <span data-ttu-id="4ace2-113">如需詳細資訊，請參閱[連接到 MDS 儲存機制 &#40;適用於 Excel 的 MDS 增益集&#41;](connect-to-an-mds-repository-mds-add-in-for-excel.md)。</span><span class="sxs-lookup"><span data-stu-id="4ace2-113">For more information, see [Connect to an MDS Repository &#40;MDS Add-in for Excel&#41;](connect-to-an-mds-repository-mds-add-in-for-excel.md).</span></span>  
  
2.  <span data-ttu-id="4ace2-114">在 **[主資料總管]** 窗格中，選取模型和版本。</span><span class="sxs-lookup"><span data-stu-id="4ace2-114">In the **Master Data Explorer** pane, select a model and version.</span></span> <span data-ttu-id="4ace2-115">系統就會填入實體的清單。</span><span class="sxs-lookup"><span data-stu-id="4ace2-115">The list of entities is populated.</span></span>  
  
    -   <span data-ttu-id="4ace2-116">如果沒有顯示 **[主資料總管]** 窗格，請按一下 **[連接和載入]** 群組中的 **[顯示總管]**。</span><span class="sxs-lookup"><span data-stu-id="4ace2-116">If the **Master Data Explorer** pane is not visible, in the **Connect and Load** group, click **Show Explorer**.</span></span>  
  
    -   <span data-ttu-id="4ace2-117">如果 **[主資料總管]** 窗格已停用，這是因為現有的工作表已經包含 MDS 管理的資料。</span><span class="sxs-lookup"><span data-stu-id="4ace2-117">If the **Master Data Explorer** pane is disabled, it is because the existing sheet already contains MDS-managed data.</span></span> <span data-ttu-id="4ace2-118">若要啟用此窗格，請開啟新的工作表。</span><span class="sxs-lookup"><span data-stu-id="4ace2-118">To enable the pane, open a new worksheet.</span></span>  
  
3.  <span data-ttu-id="4ace2-119">在 **[主資料總管]** 窗格中，按一下實體。</span><span class="sxs-lookup"><span data-stu-id="4ace2-119">In the **Master Data Explorer** pane, click an entity.</span></span>  
  
4.  <span data-ttu-id="4ace2-120">按一下 **[連接和載入]** 群組中的 **[篩選]**。</span><span class="sxs-lookup"><span data-stu-id="4ace2-120">In the **Connect and Load** group, click **Filter**.</span></span>  
  
5.  <span data-ttu-id="4ace2-121">在 **[篩選]** 對話方塊中，於 **[資料行]** 區段的屬性清單中，按一下您想要移動的屬性。</span><span class="sxs-lookup"><span data-stu-id="4ace2-121">In the **Filter** dialog box, in the **Columns** section, in the list of attributes, click the attribute you want to move.</span></span>  
  
6.  <span data-ttu-id="4ace2-122">按一下清單右邊的 **[向上]** 或 **[向下]** 箭號，即可在工作表中向左或向右移動屬性。</span><span class="sxs-lookup"><span data-stu-id="4ace2-122">To the right of the list, click the **Up** or **Down** arrow to move the attribute left and right in the worksheet.</span></span>  
  
7.  <span data-ttu-id="4ace2-123">針對每個屬性重複步驟 7，直到由上至下順序代表您想要在工作表中呈現的由左至右順序為止。</span><span class="sxs-lookup"><span data-stu-id="4ace2-123">Repeat step 7 for each attribute until the top-to-bottom order represents the left-to-right order you want in the worksheet.</span></span>  
  
8.  <span data-ttu-id="4ace2-124">按一下 **[載入資料]**。</span><span class="sxs-lookup"><span data-stu-id="4ace2-124">Click **Load Data**.</span></span> <span data-ttu-id="4ace2-125">工作表就會填入 MDS 管理的資料，而且資料行會依照您所指定的順序顯示。</span><span class="sxs-lookup"><span data-stu-id="4ace2-125">The sheet is populated with MDS-managed data and the columns are displayed in the order you specified.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ace2-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4ace2-126">See Also</span></span>  
 [<span data-ttu-id="4ace2-127">載入適用于 Excel 的 MDS 增益集&#41;的資料 &#40;</span><span class="sxs-lookup"><span data-stu-id="4ace2-127">Loading Data &#40;MDS Add-in for Excel&#41;</span></span>](overview-exporting-data-to-excel-mds-add-in-for-excel.md)  
  
  
