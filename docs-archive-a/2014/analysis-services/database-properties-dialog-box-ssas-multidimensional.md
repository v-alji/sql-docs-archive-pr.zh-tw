---
title: '[資料庫屬性] 對話方塊 (SSAS-多維度) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.databaseproperties.f1
ms.assetid: 70f000b7-917f-4699-b142-7a0d13ff767c
author: minewiskan
ms.author: owend
ms.openlocfilehash: a465c333557f19e9572cd9c2b1f7c80aaf4ab5bd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686532"
---
# <a name="database-properties-dialog-box-ssas---multidimensional"></a><span data-ttu-id="e2b66-102">資料庫屬性對話方塊 (SSAS - 多維度)</span><span class="sxs-lookup"><span data-stu-id="e2b66-102">Database Properties Dialog Box (SSAS - Multidimensional)</span></span>
  <span data-ttu-id="e2b66-103">使用 **中的** [資料庫屬性] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 對話方塊，即可設定 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 資料庫中之資料庫的屬性。</span><span class="sxs-lookup"><span data-stu-id="e2b66-103">Use the **Database Properties** dialog box in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to set the properties of a database in an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="e2b66-104">您可以在 [物件總管] 中以滑鼠右鍵按一下資料庫，然後選取 [屬性]\*\*\*\*，藉以顯示 [資料庫屬性]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="e2b66-104">You can display the **Database Properties** dialog box by right-clicking a database in Object Explorer and selecting **Properties**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="e2b66-105">選項</span><span class="sxs-lookup"><span data-stu-id="e2b66-105">Options</span></span>  
  
|<span data-ttu-id="e2b66-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="e2b66-106">Term</span></span>|<span data-ttu-id="e2b66-107">定義</span><span class="sxs-lookup"><span data-stu-id="e2b66-107">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="e2b66-108">**名稱**</span><span class="sxs-lookup"><span data-stu-id="e2b66-108">**Name**</span></span>|<span data-ttu-id="e2b66-109">輸入以變更資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="e2b66-109">Type to change the name of the database.</span></span>|  
|<span data-ttu-id="e2b66-110">**識別碼**</span><span class="sxs-lookup"><span data-stu-id="e2b66-110">**ID**</span></span>|<span data-ttu-id="e2b66-111">顯示資料庫的識別碼。</span><span class="sxs-lookup"><span data-stu-id="e2b66-111">Displays the identifier of the database.</span></span>|  
|<span data-ttu-id="e2b66-112">**說明**</span><span class="sxs-lookup"><span data-stu-id="e2b66-112">**Description**</span></span>|<span data-ttu-id="e2b66-113">鍵入以變更資料庫的描述。</span><span class="sxs-lookup"><span data-stu-id="e2b66-113">Type to change the description of the database.</span></span>|  
|<span data-ttu-id="e2b66-114">**建立時間戳記**</span><span class="sxs-lookup"><span data-stu-id="e2b66-114">**Create Timestamp**</span></span>|<span data-ttu-id="e2b66-115">顯示建立資料庫的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="e2b66-115">Displays the date and time the database was created.</span></span>|  
|<span data-ttu-id="e2b66-116">**上次結構描述更新**</span><span class="sxs-lookup"><span data-stu-id="e2b66-116">**Last Schema Update**</span></span>|<span data-ttu-id="e2b66-117">顯示上次更新資料庫的中繼資料的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="e2b66-117">Displays the date and time the metadata for the database was last updated.</span></span>|  
|<span data-ttu-id="e2b66-118">**上次更新**</span><span class="sxs-lookup"><span data-stu-id="e2b66-118">**Last Update**</span></span>|<span data-ttu-id="e2b66-119">顯示上次更新資料庫之資料的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="e2b66-119">Displays the date and time the data for the database was last updated.</span></span>|  
|<span data-ttu-id="e2b66-120">**資料來源模擬資訊**</span><span class="sxs-lookup"><span data-stu-id="e2b66-120">**Data Source Impersonation Info**</span></span>|<span data-ttu-id="e2b66-121">與資料庫中的資料來源進行連接和互動時，請選取資料庫使用的模擬資訊。</span><span class="sxs-lookup"><span data-stu-id="e2b66-121">Select the impersonation information used by the database when connecting to and interacting with data sources contained by the database.</span></span> <span data-ttu-id="e2b66-122">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="e2b66-122">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="e2b66-123">**ImpersonateAccount** (使用特定的 Windows 使用者名稱和密碼)。</span><span class="sxs-lookup"><span data-stu-id="e2b66-123">**ImpersonateAccount** (use a specific Windows user name and password).</span></span><br /><br /> <span data-ttu-id="e2b66-124">**ImpersonateService** (使用服務帳戶)。</span><span class="sxs-lookup"><span data-stu-id="e2b66-124">**ImpersonateService** (use the service account).</span></span><br /><br /> <span data-ttu-id="e2b66-125">**ImpersonateCurrentUser** (使用目前使用者的認證)。</span><span class="sxs-lookup"><span data-stu-id="e2b66-125">**ImpersonateCurrentUser** (use the credentials of the current user).</span></span><br /><br /> <span data-ttu-id="e2b66-126">**預設值** (使用服務帳戶進行 MOLAP 作業，而使用目前使用者進行資料採礦)。</span><span class="sxs-lookup"><span data-stu-id="e2b66-126">**Default** (use the service account for MOLAP operations and current user for data mining).</span></span><br /><br /> <span data-ttu-id="e2b66-127">雖然您可以在資料庫層級進行資料來源模擬設定，不過這樣做只會影響針對其模擬設定指定 **[繼承]** 的這些資料來源。</span><span class="sxs-lookup"><span data-stu-id="e2b66-127">Although you can set data source impersonation settings at the database level, doing so will only affect those data sources that specify **Inherit** for their impersonation settings.</span></span> <span data-ttu-id="e2b66-128">直接針對資料來源指定的模擬設定一定會覆寫在資料庫層級指定的任何設定。</span><span class="sxs-lookup"><span data-stu-id="e2b66-128">Impersonation settings specified directly on the data source will always override any settings that are specified at the database level.</span></span><br /><br /> <span data-ttu-id="e2b66-129">選擇模擬選項時，請考慮需要系統支援的作業類型。</span><span class="sxs-lookup"><span data-stu-id="e2b66-129">When choosing an impersonation option, consider the types of operations that will need to be supported.</span></span> <span data-ttu-id="e2b66-130">某些作業 (例如處理) 無法執行</span><span class="sxs-lookup"><span data-stu-id="e2b66-130">Some operations, such as processing, cannot be performed by</span></span>|  
|<span data-ttu-id="e2b66-131">**上次處理**</span><span class="sxs-lookup"><span data-stu-id="e2b66-131">**Last Processed**</span></span>|<span data-ttu-id="e2b66-132">顯示上次處理資料庫的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="e2b66-132">Displays the date and time the database was last processed.</span></span>|  
|<span data-ttu-id="e2b66-133">**估計的大小**</span><span class="sxs-lookup"><span data-stu-id="e2b66-133">**Estimated Size**</span></span>|<span data-ttu-id="e2b66-134">顯示資料庫之估計的大小。</span><span class="sxs-lookup"><span data-stu-id="e2b66-134">Displays the estimated size of the database.</span></span>|  
|<span data-ttu-id="e2b66-135">**儲存位置**</span><span class="sxs-lookup"><span data-stu-id="e2b66-135">**Storage Location**</span></span>|<span data-ttu-id="e2b66-136">指定資料庫的位置。</span><span class="sxs-lookup"><span data-stu-id="e2b66-136">Specifies the location of the database.</span></span> <span data-ttu-id="e2b66-137">如果資料庫位於預設資料目錄中，此值為空白。</span><span class="sxs-lookup"><span data-stu-id="e2b66-137">If the database is located in the default Data directory, this value will be empty.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e2b66-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e2b66-138">See Also</span></span>  
 <span data-ttu-id="e2b66-139">[Analysis Services 的設計工具和對話方塊 &#40;多維度資料&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="e2b66-139">[Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="e2b66-140">多維度模型資料庫 &#40;SSAS&#41;</span><span class="sxs-lookup"><span data-stu-id="e2b66-140">Multidimensional Model Databases &#40;SSAS&#41;</span></span>](multidimensional-models/multidimensional-model-databases-ssas.md)  
  
  
