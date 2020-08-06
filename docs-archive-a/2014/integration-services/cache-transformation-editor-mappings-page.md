---
title: '[快取轉換編輯器 (對應] 頁面) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.cachetransmap.f1
ms.assetid: ffd53f18-9646-458a-a84a-f2467d601ea5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6bb31e479ea98133da34dcbf257d59e70f4ffe8f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599153"
---
# <a name="cache-transformation-editor-mappings-page"></a><span data-ttu-id="d39df-102">快取轉換編輯器 (對應頁面)</span><span class="sxs-lookup"><span data-stu-id="d39df-102">Cache Transformation Editor (Mappings Page)</span></span>
  <span data-ttu-id="d39df-103">使用 **[快取轉換編輯器]** 的 **[對應]** 頁面，將 [快取轉換] 轉換中的輸入資料行對應至快取連接管理員中的目的地資料行。</span><span class="sxs-lookup"><span data-stu-id="d39df-103">Use the **Mappings** page of the **Cache Transformation Editor** to map the input columns in the Cache Transform transformation to destination columns in the Cache connection manager.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d39df-104">每個輸入資料行都必須對應至目的地資料行，而資料行資料類型也必須相符；</span><span class="sxs-lookup"><span data-stu-id="d39df-104">Each input column must be mapped to a destination column, and the column data types must match.</span></span> <span data-ttu-id="d39df-105">否則，「 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 設計師」會顯示錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="d39df-105">Otherwise, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] Designer displays an error message.</span></span>  
  
 <span data-ttu-id="d39df-106">若要深入了解「快取轉換」，請參閱＜ [Cache Transform](data-flow/transformations/cache-transform.md)＞。</span><span class="sxs-lookup"><span data-stu-id="d39df-106">To learn more about the Cache Transform, see [Cache Transform](data-flow/transformations/cache-transform.md).</span></span>  
  
 <span data-ttu-id="d39df-107">若要深入了解快取連接管理員，請參閱＜ [Cache Connection Manager](connection-manager/cache-connection-manager.md)＞。</span><span class="sxs-lookup"><span data-stu-id="d39df-107">To learn more about the Cache connection manager, see [Cache Connection Manager](connection-manager/cache-connection-manager.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="d39df-108">選項。</span><span class="sxs-lookup"><span data-stu-id="d39df-108">Options</span></span>  
 <span data-ttu-id="d39df-109">**可用的輸入資料行**</span><span class="sxs-lookup"><span data-stu-id="d39df-109">**Available Input Columns**</span></span>  
 <span data-ttu-id="d39df-110">檢視可用的輸入資料行清單。</span><span class="sxs-lookup"><span data-stu-id="d39df-110">View the list of available input columns.</span></span> <span data-ttu-id="d39df-111">使用拖放作業，即可將可用的輸入資料行對應到目的地資料行。</span><span class="sxs-lookup"><span data-stu-id="d39df-111">Use a drag-and-drop operation to map available input columns to destination columns.</span></span>  
  
 <span data-ttu-id="d39df-112">您也可以藉由在 **[可用的輸入資料行]** 資料表中反白顯示資料行，按下功能表鍵，然後選取 **[藉由比對名稱來對應項目]**，使用鍵盤將輸入資料行對應到目的地資料行。</span><span class="sxs-lookup"><span data-stu-id="d39df-112">You can also map input columns to destination columns using the keyboard, by highlighting a column in the **Available Input Columns** table, pressing the menu key, and then selecting **Map Items By Matching Names**.</span></span>  
  
 <span data-ttu-id="d39df-113">**可用的目的地資料行**</span><span class="sxs-lookup"><span data-stu-id="d39df-113">**Available Destination Columns**</span></span>  
 <span data-ttu-id="d39df-114">檢視可用的目的地資料行清單。</span><span class="sxs-lookup"><span data-stu-id="d39df-114">View the list of available destination columns.</span></span> <span data-ttu-id="d39df-115">使用拖放作業，即可將可用的目的地資料行對應到輸入資料行。</span><span class="sxs-lookup"><span data-stu-id="d39df-115">Use a drag-and-drop operation to map available destination columns to input columns.</span></span>  
  
 <span data-ttu-id="d39df-116">您也可以藉由在 **[可用的目的地資料行]** 資料表中反白顯示資料行，按下功能表鍵，然後選取 **[藉由比對名稱來對應項目]**，使用鍵盤將輸入資料行對應到目的地資料行。</span><span class="sxs-lookup"><span data-stu-id="d39df-116">You can also map input columns to destination columns using the keyboard, by highlighting a column in the **Available Destination Columns** table, pressing the menu key, and then selecting **Map Items By Matching Names**.</span></span>  
  
 <span data-ttu-id="d39df-117">**輸入資料行**</span><span class="sxs-lookup"><span data-stu-id="d39df-117">**Input Column**</span></span>  
 <span data-ttu-id="d39df-118">檢視在這個主題中稍早選取的輸入資料行。</span><span class="sxs-lookup"><span data-stu-id="d39df-118">View input columns selected earlier in this topic.</span></span> <span data-ttu-id="d39df-119">您可以使用 **[可用的輸入資料行]** 清單來變更對應。</span><span class="sxs-lookup"><span data-stu-id="d39df-119">You can change the mappings by using the list of **Available Input Columns**.</span></span>  
  
 <span data-ttu-id="d39df-120">**目的地資料行**</span><span class="sxs-lookup"><span data-stu-id="d39df-120">**Destination Column**</span></span>  
 <span data-ttu-id="d39df-121">檢視每個可用的目的地資料行。</span><span class="sxs-lookup"><span data-stu-id="d39df-121">View each available destination column.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d39df-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d39df-122">See Also</span></span>  
 [<span data-ttu-id="d39df-123">快取轉換編輯器 &#40;連線管理員頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="d39df-123">Cache Transformation Editor &#40;Connection Manager Page&#41;</span></span>](../../2014/integration-services/cache-transformation-editor-connection-manager-page.md)  
  
  
