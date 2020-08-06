---
title: 固定與變更屬性選項 (緩時變維度精靈) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.loaddimwizard.attriboption.f1
ms.assetid: c841345c-7d03-452f-9379-1c8c464f029c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: df654cd97b343179828ebd94dea40eacc90e003d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592778"
---
# <a name="fixed-and-changing-attribute-options-slowly-changing-dimension-wizard"></a><span data-ttu-id="c52b9-102">固定與變更屬性選項 (緩時變維度精靈)</span><span class="sxs-lookup"><span data-stu-id="c52b9-102">Fixed and Changing Attribute Options (Slowly Changing Dimension Wizard</span></span>
  <span data-ttu-id="c52b9-103">使用 **[固定與變更屬性選項]** 對話方塊，來指定如何回應固定與變更屬性中的變更。</span><span class="sxs-lookup"><span data-stu-id="c52b9-103">Use the **Fixed and Changing Attribute Options** dialog box to specify how to respond to changes in fixed and changing attributes.</span></span>  
  
 <span data-ttu-id="c52b9-104">若要深入了解這個精靈，請參閱＜ [Slowly Changing Dimension Transformation](slowly-changing-dimension-transformation.md)＞。</span><span class="sxs-lookup"><span data-stu-id="c52b9-104">To learn more about this wizard, see [Slowly Changing Dimension Transformation](slowly-changing-dimension-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="c52b9-105">選項。</span><span class="sxs-lookup"><span data-stu-id="c52b9-105">Options</span></span>  
 <span data-ttu-id="c52b9-106">**固定屬性**</span><span class="sxs-lookup"><span data-stu-id="c52b9-106">**Fixed attributes**</span></span>  
 <span data-ttu-id="c52b9-107">針對固定的屬性，指出在固定屬性中偵測到變更時，工作是否應視為失敗。</span><span class="sxs-lookup"><span data-stu-id="c52b9-107">For fixed attributes, indicate whether the task should fail if a change is detected in a fixed attribute.</span></span>  
  
 <span data-ttu-id="c52b9-108">**變更屬性**</span><span class="sxs-lookup"><span data-stu-id="c52b9-108">**Changing attributes**</span></span>  
 <span data-ttu-id="c52b9-109">針對變更的屬性，指出在變更屬性中偵測到變更時，除了目前的記錄外，工作是否還應變更過期或逾時的記錄。</span><span class="sxs-lookup"><span data-stu-id="c52b9-109">For changing attributes, indicate whether the task should change outdated or expired records, in addition to current records, when a change is detected in a changing attribute.</span></span> <span data-ttu-id="c52b9-110">逾時的記錄是由記錄屬性中的變更，以較新的記錄所取代的記錄 (也就是「Type 2」變更)。</span><span class="sxs-lookup"><span data-stu-id="c52b9-110">An expired record is a record that has been replaced with a newer record by a change in a historical attribute (a Type 2 change).</span></span> <span data-ttu-id="c52b9-111">選取這個選項，可能會對在關聯式資料倉儲上建構的多維度物件造成其他的處理需求。</span><span class="sxs-lookup"><span data-stu-id="c52b9-111">Selecting this option may impose additional processing requirements on a multidimensional object constructed on the relational data warehouse.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c52b9-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c52b9-112">See Also</span></span>  
 [<span data-ttu-id="c52b9-113">使用緩時變維度精靈來設定輸出</span><span class="sxs-lookup"><span data-stu-id="c52b9-113">Configure Outputs Using the Slowly Changing Dimension Wizard</span></span>](configure-outputs-using-the-slowly-changing-dimension-wizard.md)  
  
  
