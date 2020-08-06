---
title: 使用聯集全部轉換來合併資料 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- merging datasets [Integration Services]
- merging inputs [Integration Services]
- combining datasets
- Union All transformation
- datasets [Integration Services], merging
ms.assetid: 78304403-a81c-4101-b87e-ec80ddfdac98
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e782a5770ab9936e4c5cc84da706a5472ecd4d36
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599094"
---
# <a name="merge-data-by-using-the-union-all-transformation"></a><span data-ttu-id="3262f-102">使用聯集全部轉換來合併資料</span><span class="sxs-lookup"><span data-stu-id="3262f-102">Merge Data by Using the Union All Transformation</span></span>
  <span data-ttu-id="3262f-103">若要加入及設定「聯集全部」轉換，封裝必須已包括至少一個「資料流程」工作與兩個資料來源。</span><span class="sxs-lookup"><span data-stu-id="3262f-103">To add and configure a Union All transformation, the package must already include at least one Data Flow task and two data sources.</span></span>  
  
 <span data-ttu-id="3262f-104">「聯集全部」轉換可合併多個輸入。</span><span class="sxs-lookup"><span data-stu-id="3262f-104">The Union All transformation combines multiple inputs.</span></span> <span data-ttu-id="3262f-105">連接到轉換的第一個輸入為參考輸入，隨後連接的輸入為次要輸入。</span><span class="sxs-lookup"><span data-stu-id="3262f-105">The first input that is connected to the transformation is the reference input, and the inputs connected subsequently are the secondary inputs.</span></span> <span data-ttu-id="3262f-106">輸出包括參考輸入中的資料行。</span><span class="sxs-lookup"><span data-stu-id="3262f-106">The output includes the columns in the reference input.</span></span>  
  
### <a name="to-combine-inputs-in-a-data-flow"></a><span data-ttu-id="3262f-107">將輸入合併於資料流程</span><span class="sxs-lookup"><span data-stu-id="3262f-107">To combine inputs in a data flow</span></span>  
  
1.  <span data-ttu-id="3262f-108">在 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] 中，按兩下方案總管中的封裝，以在 [[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師] 中開啟封裝，然後按一下 [資料流程]  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="3262f-108">In [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], double-click the package in Solution Explorer to open the package in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, and then click the **Data Flow** tab.</span></span>  
  
2.  <span data-ttu-id="3262f-109">將「聯集全部」轉換從 [工具箱]  拖曳至 [資料流程]  索引標籤的設計介面。</span><span class="sxs-lookup"><span data-stu-id="3262f-109">From the **Toolbox**, drag the Union All transformation to the design surface of the **Data Flow** tab.</span></span>  
  
3.  <span data-ttu-id="3262f-110">將連接子從資料來源或前一個轉換拖曳至「聯集全部」轉換，以便將「聯集全部」轉換連接到資料流程。</span><span class="sxs-lookup"><span data-stu-id="3262f-110">Connect the Union All transformation to the data flow by dragging a connector from the data source or a previous transformation to the Union All transformation.</span></span>  
  
4.  <span data-ttu-id="3262f-111">按兩下 [聯集全部] 轉換。</span><span class="sxs-lookup"><span data-stu-id="3262f-111">Double-click the Union All transformation.</span></span>  
  
5.  <span data-ttu-id="3262f-112">在 [聯集全部轉換編輯器]  中，藉由按一下資料列並選取輸入清單中的資料行，將輸入的資料行對應至 [輸出資料行名稱]  清單中的資料行。</span><span class="sxs-lookup"><span data-stu-id="3262f-112">In the **Union All Transformation Editor**, map a column from an input to a column in the **Output Column Name** list by clicking a row and then selecting a column in the input list.</span></span> <span data-ttu-id="3262f-113">選取輸入清單中的 **\<ignore>** ，以略過資料行的對應。</span><span class="sxs-lookup"><span data-stu-id="3262f-113">Select **\<ignore>** in the input list to skip mapping the column.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="3262f-114">兩個資料行之間的對應，會要求資料行的中繼資料相符。</span><span class="sxs-lookup"><span data-stu-id="3262f-114">The mapping between two columns requires that the metadata of the columns match.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="3262f-115">未對應至參考資料行之次要輸入中的資料行，在輸出中會設為 Null 值。</span><span class="sxs-lookup"><span data-stu-id="3262f-115">Columns in a secondary input that are not mapped to reference columns are set to null values in the output.</span></span>  
  
6.  <span data-ttu-id="3262f-116">(選擇性) 在 [輸出資料行名稱]  資料行中修改資料行的名稱。</span><span class="sxs-lookup"><span data-stu-id="3262f-116">Optionally, modify the names of columns in the **Output Column Name** column.</span></span>  
  
7.  <span data-ttu-id="3262f-117">針對每個輸入中的每個資料行重複步驟 5 與 6。</span><span class="sxs-lookup"><span data-stu-id="3262f-117">Repeat steps 5 and 6 for each column in each input.</span></span>  
  
8.  <span data-ttu-id="3262f-118">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="3262f-118">Click **OK**.</span></span>  
  
9. <span data-ttu-id="3262f-119">若要儲存已更新的封裝，請在 **[檔案]** 功能表上，按一下 **[儲存選取項目]** 。</span><span class="sxs-lookup"><span data-stu-id="3262f-119">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3262f-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3262f-120">See Also</span></span>  
 <span data-ttu-id="3262f-121">[聯集全部轉換](union-all-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="3262f-121">[Union All Transformation](union-all-transformation.md) </span></span>  
 <span data-ttu-id="3262f-122">[Integration Services 轉換](integration-services-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="3262f-122">[Integration Services Transformations](integration-services-transformations.md) </span></span>  
 <span data-ttu-id="3262f-123">[Integration Services 路徑](../integration-services-paths.md) </span><span class="sxs-lookup"><span data-stu-id="3262f-123">[Integration Services Paths](../integration-services-paths.md) </span></span>  
 [<span data-ttu-id="3262f-124">資料流程工作</span><span class="sxs-lookup"><span data-stu-id="3262f-124">Data Flow Task</span></span>](../../control-flow/data-flow-task.md)  
  
  
