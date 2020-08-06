---
title: CDC 分隔器 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.cdcsplitter.f1
ms.assetid: 167bc5c6-fa36-439d-987c-b20acd1a77e2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 45dd16602625b28d2ca7e16f2fa6b0d62294fe81
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597247"
---
# <a name="cdc-splitter"></a><span data-ttu-id="868c2-102">CDC 分隔器</span><span class="sxs-lookup"><span data-stu-id="868c2-102">CDC Splitter</span></span>
  <span data-ttu-id="868c2-103">CDC 分隔器會將 CDC 來源資料流程中變更資料列的單一流程分割為插入、更新和刪除作業的不同資料流程。</span><span class="sxs-lookup"><span data-stu-id="868c2-103">The CDC splitter splits a single flow of change rows from a CDC source data flow into different data flows for Insert, Update and Delete operations.</span></span> <span data-ttu-id="868c2-104">資料流程是根據 `__$operation` 變更資料表中的必要資料行 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 及其標準值分割的。</span><span class="sxs-lookup"><span data-stu-id="868c2-104">The data flow is split based on the required column `__$operation` and its standard values in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] change tables.</span></span>  
  
|<span data-ttu-id="868c2-105">作業值</span><span class="sxs-lookup"><span data-stu-id="868c2-105">Value of Operation</span></span>|<span data-ttu-id="868c2-106">輸出</span><span class="sxs-lookup"><span data-stu-id="868c2-106">Output</span></span>|<span data-ttu-id="868c2-107">描述</span><span class="sxs-lookup"><span data-stu-id="868c2-107">Description</span></span>|  
|------------------------|------------|-----------------|  
|<span data-ttu-id="868c2-108">1</span><span class="sxs-lookup"><span data-stu-id="868c2-108">1</span></span>|<span data-ttu-id="868c2-109">刪除</span><span class="sxs-lookup"><span data-stu-id="868c2-109">Delete</span></span>|<span data-ttu-id="868c2-110">已刪除的資料列</span><span class="sxs-lookup"><span data-stu-id="868c2-110">Deleted Row</span></span>|  
|<span data-ttu-id="868c2-111">2</span><span class="sxs-lookup"><span data-stu-id="868c2-111">2</span></span>|<span data-ttu-id="868c2-112">插入</span><span class="sxs-lookup"><span data-stu-id="868c2-112">Insert</span></span>|<span data-ttu-id="868c2-113">插入的資料列 (在使用 [Net with Merge (淨 (含合併))]  CDC 模式時無法使用)</span><span class="sxs-lookup"><span data-stu-id="868c2-113">Inserted row (not available when using **Net with Merge** CDC mode)</span></span>|  
|<span data-ttu-id="868c2-114">3</span><span class="sxs-lookup"><span data-stu-id="868c2-114">3</span></span>|<span data-ttu-id="868c2-115">更新</span><span class="sxs-lookup"><span data-stu-id="868c2-115">Update</span></span>|<span data-ttu-id="868c2-116">更新前資料列 (僅在使用 [All with Old Values (全部 (含舊值))]  CDC 模式時才可使用)</span><span class="sxs-lookup"><span data-stu-id="868c2-116">Before-update row (available only when using **All with Old Values** CDC mode)</span></span>|  
|<span data-ttu-id="868c2-117">4</span><span class="sxs-lookup"><span data-stu-id="868c2-117">4</span></span>|<span data-ttu-id="868c2-118">更新</span><span class="sxs-lookup"><span data-stu-id="868c2-118">Update</span></span>|<span data-ttu-id="868c2-119">更新後資料列 (在更新前之後)</span><span class="sxs-lookup"><span data-stu-id="868c2-119">After-update row (follows the Before-update)</span></span>|  
|<span data-ttu-id="868c2-120">5</span><span class="sxs-lookup"><span data-stu-id="868c2-120">5</span></span>|<span data-ttu-id="868c2-121">更新</span><span class="sxs-lookup"><span data-stu-id="868c2-121">Update</span></span>|<span data-ttu-id="868c2-122">合併資料列 (僅在使用 [Net with Merge (淨 (含合併))]  CDC 模式時才可使用)</span><span class="sxs-lookup"><span data-stu-id="868c2-122">Merge row (available only when using **Net with Merge** CDC mode)</span></span>|  
|<span data-ttu-id="868c2-123">其他</span><span class="sxs-lookup"><span data-stu-id="868c2-123">Other</span></span>|<span data-ttu-id="868c2-124">錯誤</span><span class="sxs-lookup"><span data-stu-id="868c2-124">Error</span></span>||  
  
 <span data-ttu-id="868c2-125">您可以使用分隔器連接到預先定義的 INSERT、DELETE 和 UPDATE 輸出，以供進一步處理。</span><span class="sxs-lookup"><span data-stu-id="868c2-125">You can use the splitter to connect to pre-defined INSERT, DELETE, and UPDATE outputs for further processing.</span></span>  
  
 <span data-ttu-id="868c2-126">CDC 分隔器轉換有一個一般輸入和一個錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="868c2-126">The CDC Splitter transformation has one regular input and one error output.</span></span>  
  
## <a name="error-handling"></a><span data-ttu-id="868c2-127">錯誤處理</span><span class="sxs-lookup"><span data-stu-id="868c2-127">Error Handling</span></span>  
 <span data-ttu-id="868c2-128">CDC 分隔器轉換有錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="868c2-128">The CDC Splitter transformation has an error output.</span></span> <span data-ttu-id="868c2-129">含 $operation 資料行無效值的輸入資料列是視為錯誤的，會依據輸入的 **ErrorRowDisposition** 屬性來處理。</span><span class="sxs-lookup"><span data-stu-id="868c2-129">Input rows with an invalid value of the $operation column are considered erroneous and are handled according to the **ErrorRowDisposition** property of the input.</span></span>  
  
 <span data-ttu-id="868c2-130">此元件的錯誤輸出包含下列輸出資料行：</span><span class="sxs-lookup"><span data-stu-id="868c2-130">The component error output includes the following output columns:</span></span>  
  
-   <span data-ttu-id="868c2-131">**錯誤碼**：設為 1。</span><span class="sxs-lookup"><span data-stu-id="868c2-131">**Error Code**: Set to 1.</span></span>  
  
-   <span data-ttu-id="868c2-132">**錯誤資料行**：造成錯誤 (用於轉換錯誤) 的來源資料行。</span><span class="sxs-lookup"><span data-stu-id="868c2-132">**Error Column**: The source column causing the error (for conversion errors).</span></span>  
  
-   <span data-ttu-id="868c2-133">**錯誤資料列資料行**：造成錯誤之資料列的輸入資料行。</span><span class="sxs-lookup"><span data-stu-id="868c2-133">**Error Row Columns**: The input columns of the row that caused the error.</span></span>  
  
## <a name="configuring-the-cdc-splitter"></a><span data-ttu-id="868c2-134">設定 CDC 分隔器</span><span class="sxs-lookup"><span data-stu-id="868c2-134">Configuring the CDC Splitter</span></span>  
 <span data-ttu-id="868c2-135">CDC 分隔器沒有可設定的屬性。</span><span class="sxs-lookup"><span data-stu-id="868c2-135">There are no configurable properties for the CDC splitter.</span></span>  
  
 <span data-ttu-id="868c2-136">如需有關使用 CDC 分隔器的詳細資訊，請參閱＜Microsoft SQL Server Integration Services 的 CDC 元件＞。</span><span class="sxs-lookup"><span data-stu-id="868c2-136">For more information about using the CDC splitter, see CDC Components for Microsoft SQL Server Integration Services.</span></span>  
  
 <span data-ttu-id="868c2-137">**[進階編輯器]** 對話方塊包含可以程式設計方式設定的屬性。</span><span class="sxs-lookup"><span data-stu-id="868c2-137">The **Advanced Editor** dialog box contains the properties that can be set programmatically.</span></span>  
  
 <span data-ttu-id="868c2-138">若要開啟 **[進階編輯器]** 對話方塊：</span><span class="sxs-lookup"><span data-stu-id="868c2-138">To open the **Advanced Editor** dialog box:</span></span>  
  
-   <span data-ttu-id="868c2-139">在 **專案的** [資料流程] [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] 畫面中，以滑鼠右鍵按一下 CDC 分隔器，然後選取 **[顯示進階編輯器]** 。</span><span class="sxs-lookup"><span data-stu-id="868c2-139">In the **Data Flow** screen of your [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] project, right click the CDC splitter and select **Show Advanced Editor**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="868c2-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="868c2-140">See Also</span></span>  
 [<span data-ttu-id="868c2-141">依據變更類型來導向 CDC 資料流</span><span class="sxs-lookup"><span data-stu-id="868c2-141">Direct the CDC Stream According to the Type of Change</span></span>](direct-the-cdc-stream-according-to-the-type-of-change.md)  
  
  
