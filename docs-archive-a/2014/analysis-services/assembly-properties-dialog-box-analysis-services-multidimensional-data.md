---
title: 元件屬性對話方塊 (Analysis Services-多維度資料) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.assemblyproperties.f1
ms.assetid: da1174d6-d82b-4337-ac19-7368dbd95a84
author: minewiskan
ms.author: owend
ms.openlocfilehash: b9fdd506da42c5088b173db0981b5df94f91e5f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593184"
---
# <a name="assembly-properties-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="7be0a-102">組件屬性對話方塊 (Analysis Services - 多維度資料)</span><span class="sxs-lookup"><span data-stu-id="7be0a-102">Assembly Properties Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="7be0a-103">使用 **中的** [組件屬性] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 對話方塊，即可設定 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 資料庫中之組件參考的屬性。</span><span class="sxs-lookup"><span data-stu-id="7be0a-103">Use the **Assembly Properties** dialog box in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to set the properties of an assembly reference in an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="7be0a-104">以滑鼠右鍵按一下物件總管\*\*\*\* 中的組件，然後選取 [屬性]\*\*\*\*，即可顯示 [組件屬性]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="7be0a-104">You can display the **Assembly Properties** dialog box by right-clicking an assembly in **Object Explorer** and selecting **Properties**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="7be0a-105">選項</span><span class="sxs-lookup"><span data-stu-id="7be0a-105">Options</span></span>  
  
|<span data-ttu-id="7be0a-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="7be0a-106">Term</span></span>|<span data-ttu-id="7be0a-107">定義</span><span class="sxs-lookup"><span data-stu-id="7be0a-107">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="7be0a-108">**名稱**</span><span class="sxs-lookup"><span data-stu-id="7be0a-108">**Name**</span></span>|<span data-ttu-id="7be0a-109">鍵入即可變更組件參考的名稱。</span><span class="sxs-lookup"><span data-stu-id="7be0a-109">Type to change the name of the assembly reference.</span></span><br /><br /> <span data-ttu-id="7be0a-110">注意：變更此值並不會改變此組件參考所參考的組件名稱，但會變更 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 執行個體或資料庫在參考此組件參考時所使用的名稱。</span><span class="sxs-lookup"><span data-stu-id="7be0a-110">Note: Changing this value does not change the name of the assembly referred to by the assembly reference, but instead changes the name used the by the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance or database when referring to the assembly reference.</span></span>|  
|<span data-ttu-id="7be0a-111">**識別碼**</span><span class="sxs-lookup"><span data-stu-id="7be0a-111">**ID**</span></span>|<span data-ttu-id="7be0a-112">顯示組件參考所參考的組件識別碼。</span><span class="sxs-lookup"><span data-stu-id="7be0a-112">Displays the identifier of the assembly referred to by the assembly reference.</span></span>|  
|<span data-ttu-id="7be0a-113">**說明**</span><span class="sxs-lookup"><span data-stu-id="7be0a-113">**Description**</span></span>|<span data-ttu-id="7be0a-114">鍵入即可變更組件參考的描述。</span><span class="sxs-lookup"><span data-stu-id="7be0a-114">Type to change the description of the assembly reference.</span></span>|  
|<span data-ttu-id="7be0a-115">**建立時間戳記**</span><span class="sxs-lookup"><span data-stu-id="7be0a-115">**Create Timestamp**</span></span>|<span data-ttu-id="7be0a-116">顯示建立組件參考的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="7be0a-116">Displays the date and time the assembly reference was created.</span></span>|  
|<span data-ttu-id="7be0a-117">**上次結構描述更新**</span><span class="sxs-lookup"><span data-stu-id="7be0a-117">**Last Schema Update**</span></span>|<span data-ttu-id="7be0a-118">顯示上次更新組件參考之中繼資料的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="7be0a-118">Displays the date and time the metadata for the assembly reference was last updated.</span></span>|  
|<span data-ttu-id="7be0a-119">**型別**</span><span class="sxs-lookup"><span data-stu-id="7be0a-119">**Type**</span></span>|<span data-ttu-id="7be0a-120">顯示組件參考的類型。</span><span class="sxs-lookup"><span data-stu-id="7be0a-120">Displays the type of the assembly reference.</span></span> <span data-ttu-id="7be0a-121">會顯示下列各值：</span><span class="sxs-lookup"><span data-stu-id="7be0a-121">The following values are displayed:</span></span><br /><br /> <span data-ttu-id="7be0a-122">**.Net 元件**：元件參考是指 [!INCLUDE[msCoName](../includes/msconame-md.md)] .NET Framework 元件。</span><span class="sxs-lookup"><span data-stu-id="7be0a-122">**.NET Assembly**: The assembly reference refers to a [!INCLUDE[msCoName](../includes/msconame-md.md)] .NET Framework assembly.</span></span><br /><br /> <span data-ttu-id="7be0a-123">**COM DLL**：元件參考指的是 com 程式庫。</span><span class="sxs-lookup"><span data-stu-id="7be0a-123">**COM DLL**: The assembly reference refers to a COM library.</span></span>|  
|<span data-ttu-id="7be0a-124">**Source**</span><span class="sxs-lookup"><span data-stu-id="7be0a-124">**Source**</span></span>|<span data-ttu-id="7be0a-125">顯示組件參考的來源。</span><span class="sxs-lookup"><span data-stu-id="7be0a-125">Displays the source of the assembly reference.</span></span> <span data-ttu-id="7be0a-126">這個屬性通常包含組件參考所參考之組件的完整路徑和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="7be0a-126">This property typically contains the full path and file name of the assembly referred to by the assembly reference.</span></span>|  
|<span data-ttu-id="7be0a-127">**權限集合**</span><span class="sxs-lookup"><span data-stu-id="7be0a-127">**Permission Set**</span></span>|<span data-ttu-id="7be0a-128">選取用來決定是否可以存取組件參考的權限集合。</span><span class="sxs-lookup"><span data-stu-id="7be0a-128">Select the permission set used to determine access to the assembly reference.</span></span> <span data-ttu-id="7be0a-129">如需有關此屬性之可用值的詳細資訊，請參閱 <xref:Microsoft.AnalysisServices.ClrAssembly.PermissionSet%2A>。</span><span class="sxs-lookup"><span data-stu-id="7be0a-129">For more information about the available values for this property, see <xref:Microsoft.AnalysisServices.ClrAssembly.PermissionSet%2A>.</span></span>|  
|<span data-ttu-id="7be0a-130">**模擬資訊**</span><span class="sxs-lookup"><span data-stu-id="7be0a-130">**Impersonation Info**</span></span>|<span data-ttu-id="7be0a-131">選取在存取組件參考時要使用的模擬資訊。</span><span class="sxs-lookup"><span data-stu-id="7be0a-131">Select the impersonation information to use when accessing the assembly reference.</span></span> <span data-ttu-id="7be0a-132">如需此屬性之可用值的詳細資訊，請參閱 [ImpersonationInfo 元素 &#40;ASSL&#41;](https://docs.microsoft.com/bi-reference/assl/properties/impersonationinfo-element-assl)</span><span class="sxs-lookup"><span data-stu-id="7be0a-132">For more information about the available values for this property, see [ImpersonationInfo Element &#40;ASSL&#41;](https://docs.microsoft.com/bi-reference/assl/properties/impersonationinfo-element-assl)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7be0a-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7be0a-133">See Also</span></span>  
 <span data-ttu-id="7be0a-134">[Analysis Services 的設計工具和對話方塊 &#40;多維度資料&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="7be0a-134">[Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="7be0a-135">多維度模型組件管理</span><span class="sxs-lookup"><span data-stu-id="7be0a-135">Multidimensional Model Assemblies Management</span></span>](multidimensional-models/multidimensional-model-assemblies-management.md)  
  
  
