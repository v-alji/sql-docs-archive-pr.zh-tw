---
title: 使用資料轉換將資料轉換成不同的資料類型 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- converting data types [Integration Services]
- Data Conversion transformation
- data types [Integration Services], converting
ms.assetid: 4aabbe4f-7666-4672-865a-9627bd25fbfd
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 878741717c36c18e9a069c62e86be0148272239f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597242"
---
# <a name="convert-data-to-a-different-data-type-by-using-the-data-conversion-transformation"></a><span data-ttu-id="c791c-102">使用資料轉換將資料轉換至不同的資料類型</span><span class="sxs-lookup"><span data-stu-id="c791c-102">Convert Data to a Different Data Type by Using the Data Conversion Transformation</span></span>
  <span data-ttu-id="c791c-103">若要加入及設定「資料轉換」，封裝必須已包含至少一個「資料流程」工作及一個來源。</span><span class="sxs-lookup"><span data-stu-id="c791c-103">To add and configure a Data Conversion transformation, the package must already include at least one Data Flow task and one source.</span></span>  
  
### <a name="to-convert-data-to-a-different-data-type"></a><span data-ttu-id="c791c-104">轉換資料至不同的資料類型</span><span class="sxs-lookup"><span data-stu-id="c791c-104">To convert data to a different data type</span></span>  
  
1.  <span data-ttu-id="c791c-105">在 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]中，開啟包含所需封裝的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="c791c-105">In [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="c791c-106">在 [方案總管] 中，按兩下封裝將其開啟。</span><span class="sxs-lookup"><span data-stu-id="c791c-106">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="c791c-107">按一下 **[資料流程]** 索引標籤，然後將 [資料轉換] 從 **[工具箱]** 拖曳到設計介面。</span><span class="sxs-lookup"><span data-stu-id="c791c-107">Click the **Data Flow** tab, and then, from the **Toolbox**, drag the Data Conversion transformation to the design surface.</span></span>  
  
4.  <span data-ttu-id="c791c-108">將連接子從來源或前一轉換拖曳至 [資料轉換]，以便將 [資料轉換] 連接到資料流程。</span><span class="sxs-lookup"><span data-stu-id="c791c-108">Connect the Data Conversion transformation to the data flow by dragging a connector from the source or the previous transformation to the Data Conversion transformation.</span></span>  
  
5.  <span data-ttu-id="c791c-109">按兩下 [資料轉換]。</span><span class="sxs-lookup"><span data-stu-id="c791c-109">Double-click the Data Conversion transformation.</span></span>  
  
6.  <span data-ttu-id="c791c-110">在 [資料轉換編輯器]  對話方塊中，於 [可用的輸入資料行]  資料表中，選取您要轉換其資料類型之資料行旁邊的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="c791c-110">In the **Data ConversionTransformation Editor** dialog box, in the **Available Input Columns** table, select the check box next to the columns whose data type you want to convert.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c791c-111">您可以對輸入資料行套用多個資料轉換。</span><span class="sxs-lookup"><span data-stu-id="c791c-111">You can apply multiple data conversions to an input column.</span></span>  
  
7.  <span data-ttu-id="c791c-112">(選擇性) 修改 **[輸出別名]** 資料行中的預設值。</span><span class="sxs-lookup"><span data-stu-id="c791c-112">Optionally, modify the default values in the **Output Alias** column.</span></span>  
  
8.  <span data-ttu-id="c791c-113">在 **[資料類型]** 清單中，選取資料行的新資料類型。</span><span class="sxs-lookup"><span data-stu-id="c791c-113">In the **Data Type** list, select the new data type for the column.</span></span> <span data-ttu-id="c791c-114">預設資料類型是輸入資料行的資料類型。</span><span class="sxs-lookup"><span data-stu-id="c791c-114">The default data type is the data type of the input column.</span></span>  
  
9. <span data-ttu-id="c791c-115">(選擇性) 視所選取資料類型而定，更新 **[長度]** 、 **[有效位數]** 、 **[小數位數]** 及 **[字碼頁]** 資料行中的值。</span><span class="sxs-lookup"><span data-stu-id="c791c-115">Optionally, depending on the selected data type, update the values in the **Length**, the **Precision**, the **Scale**, and the **Code Page** columns.</span></span>  
  
10. <span data-ttu-id="c791c-116">若要設定錯誤輸出，請按一下 **[設定錯誤輸出]** 。</span><span class="sxs-lookup"><span data-stu-id="c791c-116">To configure the error output, click **Configure Error Output**.</span></span> <span data-ttu-id="c791c-117">如需詳細資訊，請參閱 [在資料流程元件中設定錯誤輸出](../../configure-an-error-output-in-a-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="c791c-117">For more information, see [Configure an Error Output in a Data Flow Component](../../configure-an-error-output-in-a-data-flow-component.md).</span></span>  
  
11. <span data-ttu-id="c791c-118">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="c791c-118">Click **OK**.</span></span>  
  
12. <span data-ttu-id="c791c-119">若要儲存已更新的封裝，請在 **[檔案]** 功能表上，按一下 **[儲存選取項目]** 。</span><span class="sxs-lookup"><span data-stu-id="c791c-119">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c791c-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c791c-120">See Also</span></span>  
 <span data-ttu-id="c791c-121">[Data Conversion Transformation](data-conversion-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="c791c-121">[Data Conversion Transformation](data-conversion-transformation.md) </span></span>  
 <span data-ttu-id="c791c-122">[Integration Services 轉換](integration-services-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="c791c-122">[Integration Services Transformations](integration-services-transformations.md) </span></span>  
 <span data-ttu-id="c791c-123">[Integration Services 路徑](../integration-services-paths.md) </span><span class="sxs-lookup"><span data-stu-id="c791c-123">[Integration Services Paths](../integration-services-paths.md) </span></span>  
 <span data-ttu-id="c791c-124">[Integration Services 資料類型](../integration-services-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="c791c-124">[Integration Services Data Types](../integration-services-data-types.md) </span></span>  
 [<span data-ttu-id="c791c-125">資料流程工作</span><span class="sxs-lookup"><span data-stu-id="c791c-125">Data Flow Task</span></span>](../../control-flow/data-flow-task.md)  
  
  
