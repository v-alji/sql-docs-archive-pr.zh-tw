---
title: ADO NET 目的地編輯器 (對應頁面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.adonetdest.mappings.f1
ms.assetid: 842d075f-8b7a-457c-a1a1-a7acbe10e9b7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7e7a2397e4e2d16e6eeca93d41f5127dfde4c35e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584695"
---
# <a name="ado-net-destination-editor-mappings-page"></a><span data-ttu-id="d8476-102">ADO NET 目的地編輯器 (對應頁面)</span><span class="sxs-lookup"><span data-stu-id="d8476-102">ADO NET Destination Editor (Mappings Page)</span></span>
  <span data-ttu-id="d8476-103">使用 [ADO NET 目的地編輯器]  對話方塊的 [對應]  頁面，即可將輸入資料行對應至目的地資料行。</span><span class="sxs-lookup"><span data-stu-id="d8476-103">Use the **Mappings** page of the **ADO NET Destination Editor** dialog box to map input columns to destination columns.</span></span>  
  
 <span data-ttu-id="d8476-104">若要深入了解 ADO NET 目的地，請參閱＜ [ADO NET Destination](data-flow/ado-net-destination.md)＞。</span><span class="sxs-lookup"><span data-stu-id="d8476-104">To learn more about the ADO NET destination, see [ADO NET Destination](data-flow/ado-net-destination.md).</span></span>  
  
 <span data-ttu-id="d8476-105">**開啟對應頁面**</span><span class="sxs-lookup"><span data-stu-id="d8476-105">**To open the Mappings page**</span></span>  
  
1.  <span data-ttu-id="d8476-106">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，開啟具有 ADO NET 目的地的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 封裝。</span><span class="sxs-lookup"><span data-stu-id="d8476-106">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package that has the ADO NET destination.</span></span>  
  
2.  <span data-ttu-id="d8476-107">在 [資料流程]  索引標籤中，按兩下 ADO NET 目的地。</span><span class="sxs-lookup"><span data-stu-id="d8476-107">On the **Data Flow** tab, double-click the ADO NET destination.</span></span>  
  
3.  <span data-ttu-id="d8476-108">在 [ADO NET 目的地編輯器]  中，按一下 [對應]  。</span><span class="sxs-lookup"><span data-stu-id="d8476-108">In the **ADO NET Destination Editor**, click **Mappings**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="d8476-109">選項。</span><span class="sxs-lookup"><span data-stu-id="d8476-109">Options</span></span>  
 <span data-ttu-id="d8476-110">**可用的輸入資料行**</span><span class="sxs-lookup"><span data-stu-id="d8476-110">**Available Input Columns**</span></span>  
 <span data-ttu-id="d8476-111">檢視可用的輸入資料行清單。</span><span class="sxs-lookup"><span data-stu-id="d8476-111">View the list of available input columns.</span></span> <span data-ttu-id="d8476-112">使用拖放作業，即可將資料表中的可用輸入資料行對應到目的地資料行。</span><span class="sxs-lookup"><span data-stu-id="d8476-112">Use a drag-and-drop operation to map available input columns in the table to destination columns.</span></span>  
  
 <span data-ttu-id="d8476-113">**可用的目的地資料行**</span><span class="sxs-lookup"><span data-stu-id="d8476-113">**Available Destination Columns**</span></span>  
 <span data-ttu-id="d8476-114">檢視可用的目的地資料行清單。</span><span class="sxs-lookup"><span data-stu-id="d8476-114">View the list of available destination columns.</span></span> <span data-ttu-id="d8476-115">使用拖放作業，即可將資料表中的可用目的地資料行對應到輸入資料行。</span><span class="sxs-lookup"><span data-stu-id="d8476-115">Use a drag-and-drop operation to map available destination columns in the table to input columns.</span></span>  
  
 <span data-ttu-id="d8476-116">**輸入資料行**</span><span class="sxs-lookup"><span data-stu-id="d8476-116">**Input Column**</span></span>  
 <span data-ttu-id="d8476-117">檢視所選取的輸入資料行。</span><span class="sxs-lookup"><span data-stu-id="d8476-117">View the input columns that you selected.</span></span> <span data-ttu-id="d8476-118">您可選取 **\<ignore>** 從輸出中將資料行排除來移除對應。</span><span class="sxs-lookup"><span data-stu-id="d8476-118">You can remove mappings by selecting **\<ignore>** to exclude columns from the output.</span></span>  
  
 <span data-ttu-id="d8476-119">**目的地資料行**</span><span class="sxs-lookup"><span data-stu-id="d8476-119">**Destination Column**</span></span>  
 <span data-ttu-id="d8476-120">檢視每個可用的目的地資料行，不論是否已經對應。</span><span class="sxs-lookup"><span data-stu-id="d8476-120">View each available destination column, regardless of whether it is mapped or not.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8476-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d8476-121">See Also</span></span>  
 <span data-ttu-id="d8476-122">[ADO NET 目的地編輯器 &#40;連線管理員頁面&#41;](../../2014/integration-services/ado-net-destination-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="d8476-122">[ADO NET Destination Editor &#40;Connection Manager Page&#41;](../../2014/integration-services/ado-net-destination-editor-connection-manager-page.md) </span></span>  
 [<span data-ttu-id="d8476-123">ADO NET 目的地編輯器 &#40;錯誤輸出頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="d8476-123">ADO NET Destination Editor &#40;Error Output Page&#41;</span></span>](../../2014/integration-services/ado-net-destination-editor-error-output-page.md)  
  
  
