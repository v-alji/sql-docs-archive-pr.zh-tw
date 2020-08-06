---
title: 查閱轉換編輯器 (一般頁面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.lookuptransformation.general.f1
ms.assetid: 4bd15e48-0feb-4f95-be91-5df58105dbfb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: aa178118f7e090b6a3c15c7ab9347f322461f07b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688025"
---
# <a name="lookup-transformation-editor-general-page"></a><span data-ttu-id="65f70-102">查閱轉換編輯器 (一般頁面)</span><span class="sxs-lookup"><span data-stu-id="65f70-102">Lookup Transformation Editor (General Page)</span></span>
  <span data-ttu-id="65f70-103">使用 [查閱轉換編輯器] 對話方塊的 **[一般]** 頁面來選取快取模式、選取連接類型，及指定如何處理無相符項目的資料列。</span><span class="sxs-lookup"><span data-stu-id="65f70-103">Use the **General** page of the Lookup Transformation Editor dialog box to select the cache mode, select the connection type, and specify how to handle rows with no matching entries.</span></span>  
  
 <span data-ttu-id="65f70-104">若要深入了解查閱轉換，請參閱＜ [Lookup Transformation](data-flow/transformations/lookup-transformation.md)＞。</span><span class="sxs-lookup"><span data-stu-id="65f70-104">To learn more about the Lookup transformation, see [Lookup Transformation](data-flow/transformations/lookup-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="65f70-105">選項</span><span class="sxs-lookup"><span data-stu-id="65f70-105">Options</span></span>  
 <span data-ttu-id="65f70-106">**完整快取**</span><span class="sxs-lookup"><span data-stu-id="65f70-106">**Full cache**</span></span>  
 <span data-ttu-id="65f70-107">在查閱轉換執行之前產生參考資料集並將其載入快取。</span><span class="sxs-lookup"><span data-stu-id="65f70-107">Generate and load the reference dataset into cache before the Lookup transformation is executed.</span></span>  
  
 <span data-ttu-id="65f70-108">**部分快取**</span><span class="sxs-lookup"><span data-stu-id="65f70-108">**Partial cache**</span></span>  
 <span data-ttu-id="65f70-109">在查閱轉換執行期間產生參考資料集。</span><span class="sxs-lookup"><span data-stu-id="65f70-109">Generate the reference dataset during the execution of the Lookup transformation.</span></span> <span data-ttu-id="65f70-110">將參考資料集中具有相符項目的資料列，以及在資料集中沒有相符項目的資料列載入到快取。</span><span class="sxs-lookup"><span data-stu-id="65f70-110">Load the rows with matching entries in the reference dataset and the rows with no matching entries in the dataset into cache.</span></span>  
  
 <span data-ttu-id="65f70-111">**無快取**</span><span class="sxs-lookup"><span data-stu-id="65f70-111">**No cache**</span></span>  
 <span data-ttu-id="65f70-112">在查閱轉換執行期間產生參考資料集。</span><span class="sxs-lookup"><span data-stu-id="65f70-112">Generate the reference dataset during the execution of the Lookup transformation.</span></span> <span data-ttu-id="65f70-113">沒有資料會載入到快取。</span><span class="sxs-lookup"><span data-stu-id="65f70-113">No data is loaded into cache.</span></span>  
  
 <span data-ttu-id="65f70-114">**快取連線管理員**</span><span class="sxs-lookup"><span data-stu-id="65f70-114">**Cache connection manager**</span></span>  
 <span data-ttu-id="65f70-115">將查閱轉換設定為使用快取連接管理員。</span><span class="sxs-lookup"><span data-stu-id="65f70-115">Configure the Lookup transformation to use a Cache connection manager.</span></span> <span data-ttu-id="65f70-116">只有在選取 [完整快取] 選項時，才能使用這個選項。</span><span class="sxs-lookup"><span data-stu-id="65f70-116">This option is available only if the Full cache option is selected.</span></span>  
  
 <span data-ttu-id="65f70-117">**[無快取]**</span><span class="sxs-lookup"><span data-stu-id="65f70-117">**OLE DB connection manager**</span></span>  
 <span data-ttu-id="65f70-118">將查閱轉換設定為使用 OLE DB 連接管理員。</span><span class="sxs-lookup"><span data-stu-id="65f70-118">Configure the Lookup transformation to use an OLE DB connection manager.</span></span>  
  
 <span data-ttu-id="65f70-119">**指定如何處理無相符項目的資料列**</span><span class="sxs-lookup"><span data-stu-id="65f70-119">**Specify how to handle rows with no matching entries**</span></span>  
 <span data-ttu-id="65f70-120">選取選項以處理沒有至少符合參考資料集中一個項目的資料列。</span><span class="sxs-lookup"><span data-stu-id="65f70-120">Select an option for handling rows that do not match at least one entry in the reference dataset.</span></span>  
  
 <span data-ttu-id="65f70-121">當您選取 **[將資料列重新導向無相符結果輸出]** 時，資料列會重新導向無相符結果輸出，且不當做錯誤處理。</span><span class="sxs-lookup"><span data-stu-id="65f70-121">When you select **Redirect rows to no match output**, the rows are redirected to a no match output and are not handled as errors.</span></span> <span data-ttu-id="65f70-122">無法使用 **[查閱轉換編輯器]** 對話方塊的 **[錯誤輸出]** 頁面上的 **[錯誤]** 選項。</span><span class="sxs-lookup"><span data-stu-id="65f70-122">The **Error** option on the **Error Output** page of the **Lookup Transformation Editor** dialog box is not available.</span></span>  
  
 <span data-ttu-id="65f70-123">從 **[指定如何處理無相符項目的資料列]** 清單方塊中選取任何其他選項時，會將資料列當做錯誤處理。</span><span class="sxs-lookup"><span data-stu-id="65f70-123">When you select any other option in the **Specify how to handle rows with no matching entries** list box, the rows are handled as errors.</span></span> <span data-ttu-id="65f70-124">可以使用 **[錯誤輸出]** 頁面上的 **[錯誤]** 選項。</span><span class="sxs-lookup"><span data-stu-id="65f70-124">The **Error** option on the **Error Output** page is available.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="65f70-125">外部資源</span><span class="sxs-lookup"><span data-stu-id="65f70-125">External Resources</span></span>  
 <span data-ttu-id="65f70-126">blogs.msdn.com 上的部落格文章： [查閱快取模式](https://go.microsoft.com/fwlink/?LinkId=219518)</span><span class="sxs-lookup"><span data-stu-id="65f70-126">Blog entry, [Lookup cache modes](https://go.microsoft.com/fwlink/?LinkId=219518) on blogs.msdn.com</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65f70-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="65f70-127">See Also</span></span>  
 <span data-ttu-id="65f70-128">[快取連線管理員](connection-manager/cache-connection-manager.md) </span><span class="sxs-lookup"><span data-stu-id="65f70-128">[Cache Connection Manager](connection-manager/cache-connection-manager.md) </span></span>  
 <span data-ttu-id="65f70-129">[查閱轉換編輯器 &#40;連接頁面&#41;](../../2014/integration-services/lookup-transformation-editor-connection-page.md) </span><span class="sxs-lookup"><span data-stu-id="65f70-129">[Lookup Transformation Editor &#40;Connection Page&#41;](../../2014/integration-services/lookup-transformation-editor-connection-page.md) </span></span>  
 <span data-ttu-id="65f70-130">[查閱轉換編輯器 &#40;資料行頁面&#41;](../../2014/integration-services/lookup-transformation-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="65f70-130">[Lookup Transformation Editor &#40;Columns Page&#41;](../../2014/integration-services/lookup-transformation-editor-columns-page.md) </span></span>  
 <span data-ttu-id="65f70-131">[查閱轉換編輯器 &#40;Advanced Page&#41;](../../2014/integration-services/lookup-transformation-editor-advanced-page.md) </span><span class="sxs-lookup"><span data-stu-id="65f70-131">[Lookup Transformation Editor &#40;Advanced Page&#41;](../../2014/integration-services/lookup-transformation-editor-advanced-page.md) </span></span>  
 [<span data-ttu-id="65f70-132">查閱轉換編輯器 &#40;錯誤輸出頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="65f70-132">Lookup Transformation Editor &#40;Error Output Page&#41;</span></span>](../../2014/integration-services/lookup-transformation-editor-error-output-page.md)  
  
  
