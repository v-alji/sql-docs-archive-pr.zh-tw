---
title: 依據變更類型來導向 CDC 資料流 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 3afa531e-f425-40a4-a1bf-1c3e1727287e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4a9b4e0c6a196669e4cedafcecf0477b228f3001
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593493"
---
# <a name="direct-the-cdc-stream-according-to-the-type-of-change"></a><span data-ttu-id="098bc-102">依據變更類型來導向 CDC 資料流</span><span class="sxs-lookup"><span data-stu-id="098bc-102">Direct the CDC Stream According to the Type of Change</span></span>
  <span data-ttu-id="098bc-103">若要加入及設定 CDC 分隔器轉換，封裝至少必須包含一個資料流程工作及一個 CDC 來源。</span><span class="sxs-lookup"><span data-stu-id="098bc-103">To add and configure a CDC splitter Transformation, the package must contain at least one Data Flow task and a CDC source.</span></span>  
  
 <span data-ttu-id="098bc-104">加入至封裝的 CDC 來源必須已選取 NetCDC 處理模式。</span><span class="sxs-lookup"><span data-stu-id="098bc-104">The CDC source added to the package must have a NetCDC processing mode selected.</span></span> <span data-ttu-id="098bc-105">如需選取處理模式的詳細資訊，請參閱 [CDC 來源編輯器 &#40;連線管理員頁面&#41;](../cdc-source-editor-connection-manager-page.md)。</span><span class="sxs-lookup"><span data-stu-id="098bc-105">For more information on selecting processing modes, see [CDC Source Editor &#40;Connection Manager Page&#41;](../cdc-source-editor-connection-manager-page.md).</span></span>  
  
### <a name="to-direct-the-cdc-stream-according-to-the-type-of-change"></a><span data-ttu-id="098bc-106">若要依據變更類型來導向 CDC 資料流</span><span class="sxs-lookup"><span data-stu-id="098bc-106">To direct the CDC stream according to the type of change</span></span>  
  
1.  <span data-ttu-id="098bc-107">在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]中，開啟包含所需封裝的 [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="098bc-107">In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], open the [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="098bc-108">在 [方案總管] 中，按兩下封裝加以開啟。</span><span class="sxs-lookup"><span data-stu-id="098bc-108">In the Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="098bc-109">按一下 **[資料流程]** 索引標籤，然後將 CDC 分隔器從 **[工具箱]** 拖曳到設計介面。</span><span class="sxs-lookup"><span data-stu-id="098bc-109">Click the **Data Flow** tab, and then from the **Toolbox**, drag the CDC splitter to the design surface.</span></span>  
  
4.  <span data-ttu-id="098bc-110">將封裝中包含的 CDC 來源連接到 CDC 分隔器。</span><span class="sxs-lookup"><span data-stu-id="098bc-110">Connect the CDC source that is included in the package to the CDC Splitter.</span></span>  
  
5.  <span data-ttu-id="098bc-111">將 CDC 分隔器連接到一個或多個目的地。</span><span class="sxs-lookup"><span data-stu-id="098bc-111">Connect the CDC splitter to one or more destinations.</span></span> <span data-ttu-id="098bc-112">您最多可以連接到三個不同的輸出。</span><span class="sxs-lookup"><span data-stu-id="098bc-112">You can connect up to three different outputs.</span></span>  
  
6.  <span data-ttu-id="098bc-113">選取下列其中一個輸出：</span><span class="sxs-lookup"><span data-stu-id="098bc-113">Select one of the following outputs:</span></span>  
  
    -   <span data-ttu-id="098bc-114">刪除輸出：導向 DELETE 變更資料列的輸出。</span><span class="sxs-lookup"><span data-stu-id="098bc-114">Delete output: The output where DELETE change rows are directed.</span></span>  
  
    -   <span data-ttu-id="098bc-115">插入輸出：導向 INSERT 變更資料列的輸出。</span><span class="sxs-lookup"><span data-stu-id="098bc-115">Insert output: The output where INSERT change rows are directed.</span></span>  
  
    -   <span data-ttu-id="098bc-116">更新輸出：導向 UPDATE 前/後變更資料列和合併變更資料列的輸出。</span><span class="sxs-lookup"><span data-stu-id="098bc-116">Update output: The output where before/after UPDATE change rows and Merge change rows are directed.</span></span>  
  
7.  <span data-ttu-id="098bc-117">(選擇性) 您可以使用 **[進階編輯器]** 對話方塊來設定進階屬性。</span><span class="sxs-lookup"><span data-stu-id="098bc-117">Optionally, you can configure the advanced properties using the **Advanced Editor** dialog box.</span></span>  
  
     <span data-ttu-id="098bc-118">**[進階編輯器]** 對話方塊包含可以程式設計方式設定的屬性。</span><span class="sxs-lookup"><span data-stu-id="098bc-118">The **Advanced Editor** dialog box contains the properties that can be set programmatically.</span></span>  
  
     <span data-ttu-id="098bc-119">若要開啟 **[進階編輯器]** 對話方塊：</span><span class="sxs-lookup"><span data-stu-id="098bc-119">To open the **Advanced Editor** dialog box:</span></span>  
  
    -   <span data-ttu-id="098bc-120">在 **專案的** [資料流程] [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] 畫面中，以滑鼠右鍵按一下 CDC 分隔器，然後選取 **[顯示進階編輯器]** 。</span><span class="sxs-lookup"><span data-stu-id="098bc-120">In the **Data Flow** screen of your [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] project, right click the CDC splitter and select **Show Advanced Editor**.</span></span>  
  
     <span data-ttu-id="098bc-121">如需有關使用 CDC 分隔器的詳細資訊，請參閱＜Microsoft SQL Server Integration Services 的 CDC 元件＞。</span><span class="sxs-lookup"><span data-stu-id="098bc-121">For more information about using the CDC splitter see CDC Components for Microsoft SQL Server Integration Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="098bc-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="098bc-122">See Also</span></span>  
 [<span data-ttu-id="098bc-123">CDC 分隔器</span><span class="sxs-lookup"><span data-stu-id="098bc-123">CDC Splitter</span></span>](cdc-splitter.md)  
  
  
