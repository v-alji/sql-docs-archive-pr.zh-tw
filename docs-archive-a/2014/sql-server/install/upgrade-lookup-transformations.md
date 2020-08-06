---
title: 升級查閱轉換 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Lookup transformation and upgrading
- upgrading caching for Lookup transformation
- upgrading Lookup transformation
ms.assetid: d9b2c281-91ee-4e20-bdf0-0cd77d4a4241
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 74430ab1bed232b8d510a8c28a8a690d88d1f6ba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585760"
---
# <a name="upgrade-lookup-transformations"></a><span data-ttu-id="c996c-102">升級查閱轉換</span><span class="sxs-lookup"><span data-stu-id="c996c-102">Upgrade Lookup Transformations</span></span>
  <span data-ttu-id="c996c-103">當您從 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 升級為 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 時，請考慮修改封裝，以利用查閱轉換中的新功能。</span><span class="sxs-lookup"><span data-stu-id="c996c-103">When you upgrade from [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] consider modifying packages to take advantage of the new features in the Lookup Transformation.</span></span> <span data-ttu-id="c996c-104">此轉換支援 [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] 中所提供的快取類型與資料輸出選項。</span><span class="sxs-lookup"><span data-stu-id="c996c-104">The transformation supports the caching types and data output options available in [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)].</span></span> <span data-ttu-id="c996c-105">如需其他快取和資料輸出的詳細資訊，請參閱[查閱轉換](../../integration-services/data-flow/transformations/lookup-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="c996c-105">For more information about additional the caching and data outputs, see [Lookup Transformation](../../integration-services/data-flow/transformations/lookup-transformation.md).</span></span>  
  
 <span data-ttu-id="c996c-106">在 [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] 中，可用的快取類型包括完整快取、部分快取和無快取。</span><span class="sxs-lookup"><span data-stu-id="c996c-106">In [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)], the available caching types are full caching, partial caching, and no caching.</span></span> <span data-ttu-id="c996c-107">在 [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] 中，您可以將查閱轉換設定為使用其中一種快取類型。</span><span class="sxs-lookup"><span data-stu-id="c996c-107">In [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)], you can configure a Lookup transformation to use one of these caching types.</span></span> <span data-ttu-id="c996c-108">如需如何執行部分快取或沒有快取的詳細資訊，請參閱[在無快取或部分快取模式中執行查閱](../../integration-services/data-flow/transformations/implement-a-lookup-in-no-cache-or-partial-cache-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="c996c-108">For more information about how to implement partial caching or no caching, see [Implement a Lookup in No Cache or Partial Cache Mode](../../integration-services/data-flow/transformations/implement-a-lookup-in-no-cache-or-partial-cache-mode.md).</span></span> <span data-ttu-id="c996c-109">如需如何執行完整快取的相關資訊，請參閱使用快取[連線管理員以完整快取模式來執行查閱轉換](../../integration-services/connection-manager/lookup-transformation-full-cache-mode-cache-connection-manager.md)和[使用 OLE DB 連線管理員，以完整快取模式來執行查閱轉換](../../integration-services/connection-manager/lookup-transformation-full-cache-mode-ole-db-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="c996c-109">For information about how to implement full caching, see [Implement a Lookup Transformation in Full Cache Mode Using the Cache Connection Manager](../../integration-services/connection-manager/lookup-transformation-full-cache-mode-cache-connection-manager.md) and [Implement a Lookup Transformation in Full Cache Mode Using the OLE DB Connection Manager](../../integration-services/connection-manager/lookup-transformation-full-cache-mode-ole-db-connection-manager.md).</span></span>  
  
 <span data-ttu-id="c996c-110">在 [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] 中，查閱轉換具有輸入、輸出和錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="c996c-110">In [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)], the Lookup transformation had an input, an output, and an error output.</span></span> <span data-ttu-id="c996c-111">輸出會處理在參考資料集中具有相符項目的輸入資料列。</span><span class="sxs-lookup"><span data-stu-id="c996c-111">Rows in the input that had matching entries in the reference dataset were handled by the output.</span></span> <span data-ttu-id="c996c-112">沒有相符項目的輸入資料列會被視為錯誤，而且可能會重新導向至錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="c996c-112">Rows in the input that did not have matching entries were treated as errors and could be redirected to the error output.</span></span> <span data-ttu-id="c996c-113">在 [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] 中，查閱轉換有兩個輸出：相符結果輸出和無相符結果輸出。</span><span class="sxs-lookup"><span data-stu-id="c996c-113">In [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)], the Lookup transformation has two outputs: a match output and a no match output.</span></span>  
  
 <span data-ttu-id="c996c-114">根據預設，當您執行在 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 中建立的查閱轉換時，[!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] 會將沒有相符項目的資料列視為錯誤，而且讓您將這些資料列重新導向至錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="c996c-114">By default, when you run a Lookup transformation that was created in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] treats the rows without matching entries as errors and enables you to redirect the rows to an error output.</span></span> <span data-ttu-id="c996c-115">您可以選擇設定查閱轉換，以便將這些資料列視為非錯誤，然後將這些資料列重新導向至無相符結果輸出。</span><span class="sxs-lookup"><span data-stu-id="c996c-115">You have the option of configuring the Lookup transformation to treat the rows as non-errors and redirect the rows to the no match output.</span></span>  
  
 <span data-ttu-id="c996c-116">如需詳細資訊，請參閱[查閱轉換編輯器 &#40;一般頁面&#41;](../../integration-services/general-page-of-integration-services-designers-options.md)。</span><span class="sxs-lookup"><span data-stu-id="c996c-116">For more information, see [Lookup Transformation Editor &#40;General Page&#41;](../../integration-services/general-page-of-integration-services-designers-options.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c996c-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c996c-117">See Also</span></span>  
 [<span data-ttu-id="c996c-118">查閱轉換</span><span class="sxs-lookup"><span data-stu-id="c996c-118">Lookup Transformation</span></span>](../../integration-services/data-flow/transformations/lookup-transformation.md)  
  
  
