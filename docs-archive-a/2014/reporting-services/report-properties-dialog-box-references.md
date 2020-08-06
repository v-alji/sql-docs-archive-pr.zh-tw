---
title: 報表屬性對話方塊、參考 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10530"
- sql12.rtp.rptdesigner.reportproperties.references.f1
ms.assetid: 4639d368-9918-4bb1-9953-7a724ca78dea
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4b28ea0865d37bdc56054d6b23dc8c82d9279b08
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702397"
---
# <a name="report-properties-dialog-box-references"></a><span data-ttu-id="4b665-102">報表屬性對話方塊、參考</span><span class="sxs-lookup"><span data-stu-id="4b665-102">Report Properties Dialog Box, References</span></span>
  <span data-ttu-id="4b665-103">選取 **[報表屬性]** 對話方塊上的 **[參考]** ，即可將參考加入報表定義中運算式所使用的自訂或其他外部組件以及自訂類別執行個體，或從中移除。</span><span class="sxs-lookup"><span data-stu-id="4b665-103">Select **References** on the **Report Properties** dialog box to add or remove references to custom or other external assemblies and custom class instances that are used by expressions in the report definition.</span></span>  
  
## <a name="options"></a><span data-ttu-id="4b665-104">選項</span><span class="sxs-lookup"><span data-stu-id="4b665-104">Options</span></span>  
 <span data-ttu-id="4b665-105">**加入或移除組件**</span><span class="sxs-lookup"><span data-stu-id="4b665-105">**Add or remove assemblies**</span></span>  
 <span data-ttu-id="4b665-106">列出報表參考的組件。</span><span class="sxs-lookup"><span data-stu-id="4b665-106">Lists the assemblies that the report references.</span></span> <span data-ttu-id="4b665-107">組件必須可以在安裝設計報表所使用之工具的電腦和報表伺服器上使用。</span><span class="sxs-lookup"><span data-stu-id="4b665-107">The assembly must be available on the computer on which the tool you are using to design the report is installed and on the report server.</span></span> <span data-ttu-id="4b665-108">參考的名稱必須與 **\<CodeModule>** 報表定義語言中標記的內容完全相符 ( .rdl) 檔案。</span><span class="sxs-lookup"><span data-stu-id="4b665-108">The name of the reference must match the contents of **\<CodeModule>** tags in the Report Definition Language (.rdl) file exactly.</span></span>  
  
 <span data-ttu-id="4b665-109">**加入**</span><span class="sxs-lookup"><span data-stu-id="4b665-109">**Add**</span></span>  
 <span data-ttu-id="4b665-110">按一下即可加入組件。</span><span class="sxs-lookup"><span data-stu-id="4b665-110">Click to add an assembly.</span></span> <span data-ttu-id="4b665-111">按一下省略號 ( ... ) ] 按鈕以開啟 [**開啟**] 對話方塊，並選取完成報表處理和運算式評估所需的元件。</span><span class="sxs-lookup"><span data-stu-id="4b665-111">Click the ellipsis (...) button to open the **Open** dialog box and select the assemblies necessary to complete report processing and expression evaluation.</span></span>  
  
 <span data-ttu-id="4b665-112">**刪除**</span><span class="sxs-lookup"><span data-stu-id="4b665-112">**Delete**</span></span>  
 <span data-ttu-id="4b665-113">若要從清單中移除組件參考，請選取組件名稱，再按一下 **[移除]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="4b665-113">To remove an assembly reference from the list, select the assembly name and click the **Remove** button.</span></span>  
  
 <span data-ttu-id="4b665-114">**加入或移除類別**</span><span class="sxs-lookup"><span data-stu-id="4b665-114">**Add or remove classes**</span></span>  
 <span data-ttu-id="4b665-115">列出報表所使用的類別執行個體。</span><span class="sxs-lookup"><span data-stu-id="4b665-115">Lists the class instances that are used by the report.</span></span> <span data-ttu-id="4b665-116">類別清單僅供以執行個體為基礎的成員使用，並非供靜態成員使用。</span><span class="sxs-lookup"><span data-stu-id="4b665-116">The class list is used only by instance-based members, not static members.</span></span>  
  
 <span data-ttu-id="4b665-117">**加入**</span><span class="sxs-lookup"><span data-stu-id="4b665-117">**Add**</span></span>  
 <span data-ttu-id="4b665-118">按一下即可加入類別參考。</span><span class="sxs-lookup"><span data-stu-id="4b665-118">Click to add a class reference.</span></span> <span data-ttu-id="4b665-119">按一下省略號 ( ... ) ] 按鈕以開啟 [**開啟**] 對話方塊，並選取完成報表處理和運算式評估所需的類別。</span><span class="sxs-lookup"><span data-stu-id="4b665-119">Click the ellipsis (...) button to open the **Open** dialog box and select the classes necessary to complete report processing and expression evaluation.</span></span>  
  
 <span data-ttu-id="4b665-120">**刪除**</span><span class="sxs-lookup"><span data-stu-id="4b665-120">**Delete**</span></span>  
 <span data-ttu-id="4b665-121">若要刪除類別執行個體，請選取該執行個體，並按一下 **[移除]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="4b665-121">To delete the class instance, select it and click the **Remove** button.</span></span>  
  
 <span data-ttu-id="4b665-122">**設定**</span><span class="sxs-lookup"><span data-stu-id="4b665-122">**Up**</span></span>  
 <span data-ttu-id="4b665-123">若為具有相依性的類別，您可將這個參考移動至清單中的較高位置。</span><span class="sxs-lookup"><span data-stu-id="4b665-123">For classes that have dependencies, you can move this reference higher in the list.</span></span>  
  
 <span data-ttu-id="4b665-124">**Down**</span><span class="sxs-lookup"><span data-stu-id="4b665-124">**Down**</span></span>  
 <span data-ttu-id="4b665-125">若為具有相依性的類別，您可將這個參考移動至清單中的較低位置。</span><span class="sxs-lookup"><span data-stu-id="4b665-125">For classes that have dependencies, you can move this reference lower in the list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b665-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4b665-126">See Also</span></span>  
 <span data-ttu-id="4b665-127">[報表設計師中運算式的自訂程式碼及組件參考 &#40;SSRS&#41;](report-design/custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4b665-127">[Custom Code and Assembly References in Expressions in Report Designer &#40;SSRS&#41;](report-design/custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md) </span></span>  
 <span data-ttu-id="4b665-128">[報表和群組變數集合參考 &#40;報表產生器和 SSRS&#41;](report-design/built-in-collections-report-and-group-variables-references-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="4b665-128">[Report and Group Variables Collections References &#40;Report Builder and SSRS&#41;](report-design/built-in-collections-report-and-group-variables-references-report-builder.md) </span></span>  
 [<span data-ttu-id="4b665-129">運算式範例 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="4b665-129">Expression Examples &#40;Report Builder and SSRS&#41;</span></span>](report-design/expression-examples-report-builder-and-ssrs.md)  
  
  
