---
title: 鎖定管理員屬性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- lock manager properties [Analysis Services]
- LockWaitGranularityMS property
- DefaultLockTimeoutMS property
- DeadlockDetectionGranularityMS property
ms.assetid: 15fe9ead-825b-4ac3-9191-7a07caa2861b
author: minewiskan
ms.author: owend
ms.openlocfilehash: d10927f1c549f00625b8affb801ec7b0831827c7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710850"
---
# <a name="lock-manager-properties"></a><span data-ttu-id="031cb-102">鎖定管理員屬性</span><span class="sxs-lookup"><span data-stu-id="031cb-102">Lock Manager Properties</span></span>
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="031cb-103">支援下表列出的鎖定管理員伺服器屬性。</span><span class="sxs-lookup"><span data-stu-id="031cb-103">supports the lock manager server properties listed in the following table.</span></span> <span data-ttu-id="031cb-104">如需有關其他伺服器屬性及如何設定伺服器屬性的詳細資訊，請參閱＜ [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md)＞。</span><span class="sxs-lookup"><span data-stu-id="031cb-104">For more information about additional server properties and how to set them, see [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md).</span></span>  
  
 <span data-ttu-id="031cb-105">**適用於：** 多維度與表格式伺服器模式</span><span class="sxs-lookup"><span data-stu-id="031cb-105">**Applies to:** Multidimensional and Tabular server mode</span></span>  
  
## <a name="properties"></a><span data-ttu-id="031cb-106">屬性</span><span class="sxs-lookup"><span data-stu-id="031cb-106">Properties</span></span>  
 `DefaultLockTimeoutMS`  
 <span data-ttu-id="031cb-107">此為帶正負號的 32 位元整數屬性，定義內部鎖定要求的預設鎖定逾時 (以毫秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="031cb-107">A signed 32-bit integer property that defines default lock timeout in milliseconds for internal lock requests.</span></span>  
  
 <span data-ttu-id="031cb-108">此屬性的預設值為 -1，指出內部鎖定要求沒有逾時。</span><span class="sxs-lookup"><span data-stu-id="031cb-108">The default value for this property is -1, which indicates there is no timeout for internal lock requests.</span></span>  
  
 `LockWaitGranularityMS`  
 <span data-ttu-id="031cb-109">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="031cb-109">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `DeadlockDetectionGranularityMS`  
 <span data-ttu-id="031cb-110">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="031cb-110">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="031cb-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="031cb-111">See Also</span></span>  
 <span data-ttu-id="031cb-112">[在 Analysis Services 中設定伺服器屬性](server-properties-in-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="031cb-112">[Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md) </span></span>  
 [<span data-ttu-id="031cb-113">判斷 Analysis Services 執行個體的伺服器模式</span><span class="sxs-lookup"><span data-stu-id="031cb-113">Determine the Server Mode of an Analysis Services Instance</span></span>](../instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
