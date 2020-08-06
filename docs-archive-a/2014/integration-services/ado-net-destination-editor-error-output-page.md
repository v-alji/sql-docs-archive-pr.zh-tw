---
title: ADO NET 目的地編輯器 (錯誤輸出頁面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.adonetdest.erroroutput.f1
ms.assetid: 1a56c3cf-fb6a-416d-a62c-bb19fe441ae5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b9cfd69d3adec2aa617f5e9d3add35a1a6923804
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596237"
---
# <a name="ado-net-destination-editor-error-output-page"></a><span data-ttu-id="5ed35-102">ADO NET 目的地編輯器 (錯誤輸出頁面)</span><span class="sxs-lookup"><span data-stu-id="5ed35-102">ADO NET Destination Editor (Error Output Page)</span></span>
  <span data-ttu-id="5ed35-103">使用 **[ADO NET 目的地編輯器]** 對話方塊的 **[錯誤輸出]** 頁面，即可指定錯誤處理選項。</span><span class="sxs-lookup"><span data-stu-id="5ed35-103">Use the **Error Output** page of the **ADO NET Destination Editor** dialog box to specify error handling options.</span></span>  
  
 <span data-ttu-id="5ed35-104">若要深入了解 ADO NET 目的地，請參閱＜ [ADO NET Destination](data-flow/ado-net-destination.md)＞。</span><span class="sxs-lookup"><span data-stu-id="5ed35-104">To learn more about the ADO NET destination, see [ADO NET Destination](data-flow/ado-net-destination.md).</span></span>  
  
 <span data-ttu-id="5ed35-105">**開啟錯誤輸出頁面**</span><span class="sxs-lookup"><span data-stu-id="5ed35-105">**To open the Error Output page**</span></span>  
  
1.  <span data-ttu-id="5ed35-106">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，開啟具有 ADO NET 目的地的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 封裝。</span><span class="sxs-lookup"><span data-stu-id="5ed35-106">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package that has the ADO NET destination.</span></span>  
  
2.  <span data-ttu-id="5ed35-107">在 [資料流程]  索引標籤中，按兩下 ADO NET 目的地。</span><span class="sxs-lookup"><span data-stu-id="5ed35-107">On the **Data Flow** tab, double-click the ADO NET destination.</span></span>  
  
3.  <span data-ttu-id="5ed35-108">在 **[ADO NET 目的地編輯器]** 中，按一下 **[錯誤輸出]** 。</span><span class="sxs-lookup"><span data-stu-id="5ed35-108">In the **ADO NET Destination Editor**, click **Error Output**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="5ed35-109">選項。</span><span class="sxs-lookup"><span data-stu-id="5ed35-109">Options</span></span>  
 <span data-ttu-id="5ed35-110">**輸入或輸出**</span><span class="sxs-lookup"><span data-stu-id="5ed35-110">**Input or Output**</span></span>  
 <span data-ttu-id="5ed35-111">檢視輸入的名稱。</span><span class="sxs-lookup"><span data-stu-id="5ed35-111">View the name of the input.</span></span>  
  
 <span data-ttu-id="5ed35-112">**資料行**</span><span class="sxs-lookup"><span data-stu-id="5ed35-112">**Column**</span></span>  
 <span data-ttu-id="5ed35-113">未使用。</span><span class="sxs-lookup"><span data-stu-id="5ed35-113">Not used.</span></span>  
  
 <span data-ttu-id="5ed35-114">**錯誤**</span><span class="sxs-lookup"><span data-stu-id="5ed35-114">**Error**</span></span>  
 <span data-ttu-id="5ed35-115">指定錯誤發生時要採取的動作：忽略失敗、重新導向資料列，或使元件失效。</span><span class="sxs-lookup"><span data-stu-id="5ed35-115">Specify what should happen when an error occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="5ed35-116">**相關主題：** [資料中的錯誤處理](data-flow/error-handling-in-data.md)</span><span class="sxs-lookup"><span data-stu-id="5ed35-116">**Related Topics:** [Error Handling in Data](data-flow/error-handling-in-data.md)</span></span>  
  
 <span data-ttu-id="5ed35-117">**截斷**</span><span class="sxs-lookup"><span data-stu-id="5ed35-117">**Truncation**</span></span>  
 <span data-ttu-id="5ed35-118">未使用。</span><span class="sxs-lookup"><span data-stu-id="5ed35-118">Not used.</span></span>  
  
 <span data-ttu-id="5ed35-119">**說明**</span><span class="sxs-lookup"><span data-stu-id="5ed35-119">**Description**</span></span>  
 <span data-ttu-id="5ed35-120">檢視作業的描述。</span><span class="sxs-lookup"><span data-stu-id="5ed35-120">View the description of the operation.</span></span>  
  
 <span data-ttu-id="5ed35-121">**將這個值設定到選取的資料格**</span><span class="sxs-lookup"><span data-stu-id="5ed35-121">**Set this value to selected cells**</span></span>  
 <span data-ttu-id="5ed35-122">指定發生錯誤或截斷時要對所有選取之資料格採取的動作：忽略失敗、重新導向資料列，或使元件失效。</span><span class="sxs-lookup"><span data-stu-id="5ed35-122">Specify what should happen to all the selected cells when an error or truncation occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="5ed35-123">**套用**</span><span class="sxs-lookup"><span data-stu-id="5ed35-123">**Apply**</span></span>  
 <span data-ttu-id="5ed35-124">將錯誤處理選項套用至選取的資料格。</span><span class="sxs-lookup"><span data-stu-id="5ed35-124">Apply the error handling option to the selected cells.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ed35-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5ed35-125">See Also</span></span>  
 <span data-ttu-id="5ed35-126">[ADO NET 目的地編輯器 &#40;連線管理員頁面&#41;](../../2014/integration-services/ado-net-destination-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="5ed35-126">[ADO NET Destination Editor &#40;Connection Manager Page&#41;](../../2014/integration-services/ado-net-destination-editor-connection-manager-page.md) </span></span>  
 [<span data-ttu-id="5ed35-127">ADO NET 目的地編輯器 &#40;對應頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="5ed35-127">ADO NET Destination Editor &#40;Mappings Page&#41;</span></span>](../../2014/integration-services/ado-net-destination-editor-mappings-page.md)  
  
  
