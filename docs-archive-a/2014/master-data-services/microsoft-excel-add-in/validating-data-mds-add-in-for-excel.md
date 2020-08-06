---
title: 驗證資料 (適用於 Excel 的 MDS 增益集) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 71eda98f-01a4-4fff-8246-be3133782523
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: f8e97ff6481996b2e16436e1f78478bd234fe6ce
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596081"
---
# <a name="validating-data-mds-add-in-for-excel"></a><span data-ttu-id="4a530-102">驗證資料 (適用於 Excel 的 MDS 增益集)</span><span class="sxs-lookup"><span data-stu-id="4a530-102">Validating Data (MDS Add-in for Excel)</span></span>
  <span data-ttu-id="4a530-103">在 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]中，當您發行資料時，會進行下列兩種驗證類型：</span><span class="sxs-lookup"><span data-stu-id="4a530-103">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], when you publish data, two types of validation take place:</span></span>  
  
-   <span data-ttu-id="4a530-104">任何已定義的商務規則會套用至資料。</span><span class="sxs-lookup"><span data-stu-id="4a530-104">Any defined business rules are applied to the data.</span></span>  
  
-   <span data-ttu-id="4a530-105">對允許的屬性值 (例如，字元數目或資料類型) 檢查資料。</span><span class="sxs-lookup"><span data-stu-id="4a530-105">Data is checked against allowed attribute values (for example, number of characters or type of data).</span></span>  
  
 <span data-ttu-id="4a530-106">在每種情況下，有效資料都會發行到 MDS 儲存機制。</span><span class="sxs-lookup"><span data-stu-id="4a530-106">In each case, valid data is published to the MDS repository.</span></span> <span data-ttu-id="4a530-107">無效資料已反白顯示，而且在狀態資料行中顯示錯誤的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="4a530-107">Data that is not valid is highlighted, and details of the error can be shown in status columns.</span></span>  
  
## <a name="when-validation-occurs"></a><span data-ttu-id="4a530-108">當發生驗證時</span><span class="sxs-lookup"><span data-stu-id="4a530-108">When Validation Occurs</span></span>  
 <span data-ttu-id="4a530-109">在 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]中，當您發行新的或已變更的資料時，或當您手動套用商務規則時，會發生驗證。</span><span class="sxs-lookup"><span data-stu-id="4a530-109">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], validation occurs when you publish new or changed data, or when you manually apply business rules.</span></span>  
  
 <span data-ttu-id="4a530-110">當商務規則失敗時，資料仍然會發行到 MDS 儲存機制。</span><span class="sxs-lookup"><span data-stu-id="4a530-110">When business rules fail, the data is still published to the MDS repository.</span></span> <span data-ttu-id="4a530-111">當輸入驗證失敗時，資料就不會發行到儲存機制。</span><span class="sxs-lookup"><span data-stu-id="4a530-111">When input validation fails, the data is not published to the repository.</span></span>  
  
## <a name="validation-statuses"></a><span data-ttu-id="4a530-112">驗證狀態</span><span class="sxs-lookup"><span data-stu-id="4a530-112">Validation Statuses</span></span>  
 <span data-ttu-id="4a530-113">在 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]中，可能出現下列幾種驗證狀態：</span><span class="sxs-lookup"><span data-stu-id="4a530-113">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], the following validation statuses are possible.</span></span>  
  
|<span data-ttu-id="4a530-114">狀態</span><span class="sxs-lookup"><span data-stu-id="4a530-114">Status</span></span>|<span data-ttu-id="4a530-115">描述</span><span class="sxs-lookup"><span data-stu-id="4a530-115">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="4a530-116">錯誤</span><span class="sxs-lookup"><span data-stu-id="4a530-116">Error</span></span>|<span data-ttu-id="4a530-117">對 MDS 管理員所定義的商務規則，資料列中一個或多個值的驗證失敗。</span><span class="sxs-lookup"><span data-stu-id="4a530-117">One or more values in the row failed validation against business rules defined by an MDS administrator.</span></span>|  
|<span data-ttu-id="4a530-118">未驗證</span><span class="sxs-lookup"><span data-stu-id="4a530-118">Not Validated</span></span>|<span data-ttu-id="4a530-119">尚未對商務規則驗證資料列中的值。</span><span class="sxs-lookup"><span data-stu-id="4a530-119">Values in the row have not yet been validated against business rules.</span></span>|  
|<span data-ttu-id="4a530-120">Success</span><span class="sxs-lookup"><span data-stu-id="4a530-120">Success</span></span>|<span data-ttu-id="4a530-121">資料列中的所有值已經通過商務規則驗證。</span><span class="sxs-lookup"><span data-stu-id="4a530-121">All values in the row have passed validation against business rules.</span></span>|  
  
## <a name="input-statuses"></a><span data-ttu-id="4a530-122">輸入狀態</span><span class="sxs-lookup"><span data-stu-id="4a530-122">Input Statuses</span></span>  
 <span data-ttu-id="4a530-123">在 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]中，可能出現下列幾種輸入狀態：</span><span class="sxs-lookup"><span data-stu-id="4a530-123">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], the following input statuses are possible</span></span>  
  
|<span data-ttu-id="4a530-124">狀態</span><span class="sxs-lookup"><span data-stu-id="4a530-124">Status</span></span>|<span data-ttu-id="4a530-125">描述</span><span class="sxs-lookup"><span data-stu-id="4a530-125">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="4a530-126">錯誤</span><span class="sxs-lookup"><span data-stu-id="4a530-126">Error</span></span>|<span data-ttu-id="4a530-127">資料列中一或多個值不符合系統需求，如長度或資料類型。</span><span class="sxs-lookup"><span data-stu-id="4a530-127">One or more values in the row don't meet system requirements like length or data type.</span></span> <span data-ttu-id="4a530-128">MDS 儲存機制中的值未更新。</span><span class="sxs-lookup"><span data-stu-id="4a530-128">The value is not updated in the MDS repository.</span></span>|  
|<span data-ttu-id="4a530-129">新資料列</span><span class="sxs-lookup"><span data-stu-id="4a530-129">New Row</span></span>|<span data-ttu-id="4a530-130">資料列中的值尚未發行到 MDS 儲存機制。</span><span class="sxs-lookup"><span data-stu-id="4a530-130">The values in the row have not yet been published to the MDS repository.</span></span>|  
|<span data-ttu-id="4a530-131">唯讀</span><span class="sxs-lookup"><span data-stu-id="4a530-131">Read Only</span></span>|<span data-ttu-id="4a530-132">登入的使用者有資料列中一個或多個值的唯讀權限，而且值無法更新。</span><span class="sxs-lookup"><span data-stu-id="4a530-132">The logged in user has Read-only permissions to one or more values in the row and the value(s) cannot be updated.</span></span>|  
|<span data-ttu-id="4a530-133">未變更</span><span class="sxs-lookup"><span data-stu-id="4a530-133">Unchanged</span></span>|<span data-ttu-id="4a530-134">工作表中尚未變更資料列中的任何值。</span><span class="sxs-lookup"><span data-stu-id="4a530-134">No values in the row have been changed in the worksheet.</span></span> <span data-ttu-id="4a530-135">這不表示儲存機制中的值尚未變更；若要取得工作表中最新的資料，請在 [連接和載入]\*\*\*\* 群組中，請按一下 [載入或重新整理]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4a530-135">This does not mean the values in the repository have not changed; to get the latest data in the sheet, in the **Connect and Load** group, click **Load or Refresh**.</span></span><br /><br /> <span data-ttu-id="4a530-136">這是每個資料列的預設值。</span><span class="sxs-lookup"><span data-stu-id="4a530-136">This is the default setting for each row.</span></span>|  
  
## <a name="related-tasks"></a><span data-ttu-id="4a530-137">相關工作</span><span class="sxs-lookup"><span data-stu-id="4a530-137">Related Tasks</span></span>  
  
|<span data-ttu-id="4a530-138">工作描述</span><span class="sxs-lookup"><span data-stu-id="4a530-138">Task Description</span></span>|<span data-ttu-id="4a530-139">主題</span><span class="sxs-lookup"><span data-stu-id="4a530-139">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="4a530-140">判斷哪些值未通過已定義的商務規則。</span><span class="sxs-lookup"><span data-stu-id="4a530-140">Determine which values do not pass the defined business rules.</span></span>|[<span data-ttu-id="4a530-141">套用商務規則 &#40;適用於 Excel 的 MDS 增益集&#41;</span><span class="sxs-lookup"><span data-stu-id="4a530-141">Apply Business Rules &#40;MDS Add-in for Excel&#41;</span></span>](apply-business-rules-mds-add-in-for-excel.md)|  
|<span data-ttu-id="4a530-142">若要更正驗證錯誤，請檢視成員進行的所有交易。</span><span class="sxs-lookup"><span data-stu-id="4a530-142">To help correct validation errors, view all transactions that have taken place for a member.</span></span>|[<span data-ttu-id="4a530-143">檢視成員的所有註解或交易 &#40;適用於 Excel 的 MDS 增益集&#41;</span><span class="sxs-lookup"><span data-stu-id="4a530-143">View All Annotations or Transactions for a Member &#40;MDS Add-in for Excel&#41;</span></span>](view-all-annotations-or-transactions-for-a-member-mds-add-in-for-excel.md)|  
  
## <a name="related-content"></a><span data-ttu-id="4a530-144">相關內容</span><span class="sxs-lookup"><span data-stu-id="4a530-144">Related Content</span></span>  
  
-   [<span data-ttu-id="4a530-145">發行資料 &#40;適用于 Excel 的 MDS 增益集&#41;</span><span class="sxs-lookup"><span data-stu-id="4a530-145">Publishing Data &#40;MDS Add-in for Excel&#41;</span></span>](overview-importing-data-from-excel-mds-add-in-for-excel.md)  
  
  
