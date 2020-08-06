---
title: 啟用維度回寫 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- modifying dimensions
- writeback [Analysis Services], setting up
- dimensions [Analysis Services], Business Intelligence enhancements
- Business Intelligence enhancements [Analysis Services], writeback
- dimensions [Analysis Services], writeback
- writeback [Analysis Services]
- dimensions [Analysis Services], modifying
- manual dimension structure modifications
ms.assetid: a4b5eb5a-366d-4fc8-ad0d-5bdb8e7b4163
author: minewiskan
ms.author: owend
ms.openlocfilehash: cba4a54e8a51d022c6f84a4c81d32f359a95692a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593661"
---
# <a name="enable-dimension-writeback"></a><span data-ttu-id="a2822-102">[啟用維度回寫]</span><span class="sxs-lookup"><span data-stu-id="a2822-102">Enable Dimension Writeback</span></span>
  <span data-ttu-id="a2822-103">加入維度回寫增強功能至 Cube 或維度，以允許使用者手動修改維度結構和成員。</span><span class="sxs-lookup"><span data-stu-id="a2822-103">Add the dimension writeback enhancement to a cube or dimension to allow users to manually modify the dimension structure and members.</span></span> <span data-ttu-id="a2822-104">可寫入維度的更新會直接記錄在維度資料表中。</span><span class="sxs-lookup"><span data-stu-id="a2822-104">Updates to a write-enabled dimension are recorded directly in the dimension table.</span></span> <span data-ttu-id="a2822-105">這項增強功能會變更維度的 `WriteEnabled` 屬性設定。</span><span class="sxs-lookup"><span data-stu-id="a2822-105">This enhancement changes the `WriteEnabled` property setting for a dimension.</span></span>  
  
 <span data-ttu-id="a2822-106">若要加入維度回寫，您可使用 [商業智慧精靈]，並於 [選擇增強功能]\*\*\*\* 頁面上選取 [啟用維度回寫]\*\*\*\* 選項。</span><span class="sxs-lookup"><span data-stu-id="a2822-106">To add dimension writeback, you use the Business Intelligence Wizard, and select the **Enable dimension writeback** option on the **Choose Enhancement** page.</span></span> <span data-ttu-id="a2822-107">然後，此精靈會引導您逐步完成選取要套用維度回寫的維度，並為選取的維度設定此選項。</span><span class="sxs-lookup"><span data-stu-id="a2822-107">This wizard then guides you through the steps of selecting a dimension to which you want to apply dimension writeback and setting this option for the selected dimension.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a2822-108">只有 SQL Server 關聯式資料庫和資料超市才支援回寫。</span><span class="sxs-lookup"><span data-stu-id="a2822-108">Writeback is supported for SQL Server relational databases and data marts only.</span></span>  
  
## <a name="selecting-a-dimension"></a><span data-ttu-id="a2822-109">選取維度</span><span class="sxs-lookup"><span data-stu-id="a2822-109">Selecting a Dimension</span></span>  
 <span data-ttu-id="a2822-110">在精靈的第一個 [啟用維度回寫]\*\*\*\* 頁面上，您會指定要套用維度回寫的維度。</span><span class="sxs-lookup"><span data-stu-id="a2822-110">On the first **Enable Dimension Writeback** page of the wizard, you specify the dimension to which you want to apply dimension writeback.</span></span> <span data-ttu-id="a2822-111">加入到此選取維度的維度回寫增強功能會產生維度的變更。</span><span class="sxs-lookup"><span data-stu-id="a2822-111">The dimension writeback enhancement added to this selected dimension will result in changes to the dimension.</span></span> <span data-ttu-id="a2822-112">包含選取之維度的所有 Cube，都會繼承這些變更。</span><span class="sxs-lookup"><span data-stu-id="a2822-112">These changes will be inherited by all cubes that include the selected dimension.</span></span>  
  
## <a name="setting-dimension-writeback-capability"></a><span data-ttu-id="a2822-113">設定維度回寫功能</span><span class="sxs-lookup"><span data-stu-id="a2822-113">Setting Dimension Writeback Capability</span></span>  
 <span data-ttu-id="a2822-114">在精靈的第二個 [啟用維度回寫]\*\*\*\* 頁面上，您可實際設定 [在維度中啟用回寫]\*\*\*\* 選項。</span><span class="sxs-lookup"><span data-stu-id="a2822-114">On the second **Enable Dimension Writeback** page of the wizard, you actually set the **Enable writeback in the dimension** option.</span></span> <span data-ttu-id="a2822-115">選取此選項會自動將維度的 `WriteEnabled` 屬性設定為 `True`。</span><span class="sxs-lookup"><span data-stu-id="a2822-115">Selecting this option automatically sets the `WriteEnabled` property of the dimension to `True`.</span></span> <span data-ttu-id="a2822-116">而清除此選項則會自動將屬性設定為 `False`。</span><span class="sxs-lookup"><span data-stu-id="a2822-116">Clearing this option automatically sets the property to `False`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a2822-117">備註</span><span class="sxs-lookup"><span data-stu-id="a2822-117">Remarks</span></span>  
 <span data-ttu-id="a2822-118">建立新的成員時，您必須包含維度中的每個屬性。</span><span class="sxs-lookup"><span data-stu-id="a2822-118">When you create a new member, you must include every attribute in a dimension.</span></span> <span data-ttu-id="a2822-119">您不能插入成員時不指定維度之索引鍵屬性的值。</span><span class="sxs-lookup"><span data-stu-id="a2822-119">You cannot insert a member without specifying a value for the key attribute of the dimension.</span></span> <span data-ttu-id="a2822-120">因此，建立成員時要受到維度資料表上之已定義的任何條件約束 (例如非 Null 索引鍵值)。</span><span class="sxs-lookup"><span data-stu-id="a2822-120">Therefore, creating members is subject to any constraints (such as non-null key values) that are defined on the dimension table.</span></span> <span data-ttu-id="a2822-121">您也應該考慮以維度屬性選擇性指定的資料行，例如在 `CustomRollupColumn`、`CustomRollupPropertiesColumn` 或 `UnaryOperatorColumn` 維度屬性中指定的資料行。</span><span class="sxs-lookup"><span data-stu-id="a2822-121">You should also consider columns optionally specified by dimension properties, such as columns specified in the `CustomRollupColumn`, `CustomRollupPropertiesColumn` or the `UnaryOperatorColumn` dimension properties.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="a2822-122">如果您使用 SQL Azure 做為執行回寫至 Analysis Services 資料庫中的資料來源，作業會失敗。</span><span class="sxs-lookup"><span data-stu-id="a2822-122">If you use SQL Azure as a data source to perform writeback into an Analysis Services database, the operation fails.</span></span> <span data-ttu-id="a2822-123">這是設計所限，因為預設不會開啟可啟用 Multiple Active Result Sets (MARS) 的提供者選項。</span><span class="sxs-lookup"><span data-stu-id="a2822-123">This is by design, because the provider option that enables multiple active result sets (MARS) is not turned on by default.</span></span>  
>   
>  <span data-ttu-id="a2822-124">解決方法是，在連接字串中加入下列設定，以支援 MARS 並啟用回寫：</span><span class="sxs-lookup"><span data-stu-id="a2822-124">The workaround is to add the following setting in the connection string, to support MARS and to enable writeback:</span></span>  
>   
>  `"MultipleActiveResultSets=True"`  
>   
>  <span data-ttu-id="a2822-125">如需詳細資訊，請參閱[使用 Multiple Active Result Sets &#40;MARS&#41;](../../relational-databases/native-client/features/using-multiple-active-result-sets-mars.md)。</span><span class="sxs-lookup"><span data-stu-id="a2822-125">For more information see [Using Multiple Active Result Sets &#40;MARS&#41;](../../relational-databases/native-client/features/using-multiple-active-result-sets-mars.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2822-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a2822-126">See Also</span></span>  
 [<span data-ttu-id="a2822-127">可寫入維度</span><span class="sxs-lookup"><span data-stu-id="a2822-127">Write-Enabled Dimensions</span></span>](../multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md)  
  
  
