---
title: 歷程記錄屬性選項 (緩時變維度精靈) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.loaddimwizard.histattriboption.f1
ms.assetid: a176ec66-ec39-4c99-99d1-c1afa8450e1e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fad005d6b8f80973abeb47dd881ef02b669d7b27
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599110"
---
# <a name="historical-attribute-options-slowly-changing-dimension-wizard"></a><span data-ttu-id="4033f-102">記錄屬性選項 (緩時變維度精靈)</span><span class="sxs-lookup"><span data-stu-id="4033f-102">Historical Attribute Options (Slowly Changing Dimension Wizard)</span></span>
  <span data-ttu-id="4033f-103">使用 [記錄屬性選項]  對話方塊，依開始和結束日期來顯示記錄屬性，或者在基於此目的而建立的資料行中記錄記錄屬性。</span><span class="sxs-lookup"><span data-stu-id="4033f-103">Use the **Historical Attributes Options** dialog box to show historical attributes by start and end dates, or to record historical attributes in a column specially created for this purpose.</span></span>  
  
 <span data-ttu-id="4033f-104">若要深入了解這個精靈，請參閱＜ [Slowly Changing Dimension Transformation](slowly-changing-dimension-transformation.md)＞。</span><span class="sxs-lookup"><span data-stu-id="4033f-104">To learn more about this wizard, see [Slowly Changing Dimension Transformation](slowly-changing-dimension-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="4033f-105">選項。</span><span class="sxs-lookup"><span data-stu-id="4033f-105">Options</span></span>  
 <span data-ttu-id="4033f-106">**使用單一資料行顯示目前與逾期記錄**</span><span class="sxs-lookup"><span data-stu-id="4033f-106">**Use a single column to show current and expired records**</span></span>  
 <span data-ttu-id="4033f-107">如果您選擇使用單一資料行來記錄記錄屬性的狀態，則可以使用下列選項：</span><span class="sxs-lookup"><span data-stu-id="4033f-107">If you choose to use a single column to record the status of historical attributes, the following options are available:</span></span>  
  
|<span data-ttu-id="4033f-108">選項</span><span class="sxs-lookup"><span data-stu-id="4033f-108">Option</span></span>|<span data-ttu-id="4033f-109">描述</span><span class="sxs-lookup"><span data-stu-id="4033f-109">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="4033f-110">**指出目前記錄的資料行**</span><span class="sxs-lookup"><span data-stu-id="4033f-110">**Column to indicate current record**</span></span>|<span data-ttu-id="4033f-111">選取要指出目前記錄的資料行。</span><span class="sxs-lookup"><span data-stu-id="4033f-111">Select a column in which to indicate the current record.</span></span>|  
|<span data-ttu-id="4033f-112">**目前值**</span><span class="sxs-lookup"><span data-stu-id="4033f-112">**Value when current**</span></span>|<span data-ttu-id="4033f-113">使用 [True]  或 [目前]  來顯示記錄是否為目前的。</span><span class="sxs-lookup"><span data-stu-id="4033f-113">Use either **True** or **Current** to show whether the record is current.</span></span>|  
|<span data-ttu-id="4033f-114">**逾期值**</span><span class="sxs-lookup"><span data-stu-id="4033f-114">**Expiration value**</span></span>|<span data-ttu-id="4033f-115">使用 [False]  或 [逾期]  來顯示記錄是否為記錄值。</span><span class="sxs-lookup"><span data-stu-id="4033f-115">Use either **False** or **Expired** to show whether the record is a historical value.</span></span>|  
  
 <span data-ttu-id="4033f-116">**使用開始和結束日期以識別目前與逾期記錄**</span><span class="sxs-lookup"><span data-stu-id="4033f-116">**Use start and end dates to identify current and expired records**</span></span>  
 <span data-ttu-id="4033f-117">此選項的維度資料表必須包含日期資料行。</span><span class="sxs-lookup"><span data-stu-id="4033f-117">The dimension table for this option must include a date column.</span></span> <span data-ttu-id="4033f-118">如果您選擇依開始和結束日期顯示記錄屬性，則可以使用下列選項：</span><span class="sxs-lookup"><span data-stu-id="4033f-118">If you choose to show historical attributes by start and end dates, the following options are available:</span></span>  
  
|<span data-ttu-id="4033f-119">選項</span><span class="sxs-lookup"><span data-stu-id="4033f-119">Option</span></span>|<span data-ttu-id="4033f-120">描述</span><span class="sxs-lookup"><span data-stu-id="4033f-120">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="4033f-121">**開始日期資料行**</span><span class="sxs-lookup"><span data-stu-id="4033f-121">**Start date column**</span></span>|<span data-ttu-id="4033f-122">選取維度資料表中的資料行以包含開始日期。</span><span class="sxs-lookup"><span data-stu-id="4033f-122">Select the column in the dimension table to contain the start date.</span></span>|  
|<span data-ttu-id="4033f-123">**結束日期資料行**</span><span class="sxs-lookup"><span data-stu-id="4033f-123">**End date column**</span></span>|<span data-ttu-id="4033f-124">選取維度資料表中的資料行以包含結束日期。</span><span class="sxs-lookup"><span data-stu-id="4033f-124">Select the column in the dimension table to contain the end date.</span></span>|  
|<span data-ttu-id="4033f-125">**設定日期值的變數**</span><span class="sxs-lookup"><span data-stu-id="4033f-125">**Variable to set date values**</span></span>|<span data-ttu-id="4033f-126">從清單中選取日期變數。</span><span class="sxs-lookup"><span data-stu-id="4033f-126">Select a date variable from the list.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4033f-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4033f-127">See Also</span></span>  
 [<span data-ttu-id="4033f-128">使用緩時變維度精靈來設定輸出</span><span class="sxs-lookup"><span data-stu-id="4033f-128">Configure Outputs Using the Slowly Changing Dimension Wizard</span></span>](configure-outputs-using-the-slowly-changing-dimension-wizard.md)  
  
  
