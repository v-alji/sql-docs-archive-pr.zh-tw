---
title: 報表屬性對話方塊、參考 (報表產生器) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10082"
ms.assetid: 3414c857-8ea6-4fc4-a6d5-b4883c039efa
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2c28e9053a1c13f8d0e0b7b44f3b1a037976c318
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702402"
---
# <a name="report-properties-dialog-box-references-report-builder"></a><span data-ttu-id="53336-102">報表屬性對話方塊、參考 (報表產生器)</span><span class="sxs-lookup"><span data-stu-id="53336-102">Report Properties Dialog Box, References (Report Builder)</span></span>
  <span data-ttu-id="53336-103">選取 **[報表屬性]** 對話方塊上的 **[參考]** ，即可將參考加入報表定義中運算式所使用的自訂或其他外部組件以及自訂類別執行個體，或從中移除。</span><span class="sxs-lookup"><span data-stu-id="53336-103">Select **References** on the **Report Properties** dialog box to add or remove references to custom or other external assemblies and custom class instances that are used by expressions in the report definition.</span></span> <span data-ttu-id="53336-104">在報表產生器的本機模式中不支援自訂組件。</span><span class="sxs-lookup"><span data-stu-id="53336-104">Custom assemblies are not supported in local mode in Report Builder.</span></span> <span data-ttu-id="53336-105">若要撰寫使用自訂群組件的報表，請使用中的報表設計師 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="53336-105">To author reports that use custom assemblies, use Report Designer in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
## <a name="options"></a><span data-ttu-id="53336-106">選項</span><span class="sxs-lookup"><span data-stu-id="53336-106">Options</span></span>  
 <span data-ttu-id="53336-107">**加入或移除組件**</span><span class="sxs-lookup"><span data-stu-id="53336-107">**Add or remove assemblies**</span></span>  
 <span data-ttu-id="53336-108">列出報表參考的組件。</span><span class="sxs-lookup"><span data-stu-id="53336-108">Lists the assemblies that the report references.</span></span> <span data-ttu-id="53336-109">組件必須可以在安裝設計報表所使用之工具的電腦和報表伺服器上使用。</span><span class="sxs-lookup"><span data-stu-id="53336-109">The assembly must be available on the computer on which the tool you are using to design the report is installed and on the report server.</span></span> <span data-ttu-id="53336-110">參考的名稱必須與 **\<CodeModule>** 報表定義語言中標記的內容完全相符 ( .rdl) 檔案。</span><span class="sxs-lookup"><span data-stu-id="53336-110">The name of the reference must match the contents of **\<CodeModule>** tags in the Report Definition Language (.rdl) file exactly.</span></span>  
  
 <span data-ttu-id="53336-111">**加入**</span><span class="sxs-lookup"><span data-stu-id="53336-111">**Add**</span></span>  
 <span data-ttu-id="53336-112">按一下即可加入組件。</span><span class="sxs-lookup"><span data-stu-id="53336-112">Click to add an assembly.</span></span> <span data-ttu-id="53336-113">按一下省略號 ( ... ) ] 按鈕以開啟 [**開啟**] 對話方塊，並選取完成報表處理和運算式評估所需的元件。</span><span class="sxs-lookup"><span data-stu-id="53336-113">Click the ellipsis (...) button to open the **Open** dialog box and select the assemblies necessary to complete report processing and expression evaluation.</span></span>  
  
 <span data-ttu-id="53336-114">**移除**</span><span class="sxs-lookup"><span data-stu-id="53336-114">**Remove**</span></span>  
 <span data-ttu-id="53336-115">若要從清單中移除組件參考，請選取組件名稱，再按一下 **[移除]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="53336-115">To remove an assembly reference from the list, select the assembly name and click the **Remove** button.</span></span>  
  
 <span data-ttu-id="53336-116">**加入或移除類別**</span><span class="sxs-lookup"><span data-stu-id="53336-116">**Add or remove classes**</span></span>  
 <span data-ttu-id="53336-117">列出報表所使用的類別執行個體。</span><span class="sxs-lookup"><span data-stu-id="53336-117">Lists the class instances that are used by the report.</span></span> <span data-ttu-id="53336-118">類別清單僅供以執行個體為基礎的成員使用，並非供靜態成員使用。</span><span class="sxs-lookup"><span data-stu-id="53336-118">The class list is used only by instance-based members, not static members.</span></span>  
  
 <span data-ttu-id="53336-119">**加入**</span><span class="sxs-lookup"><span data-stu-id="53336-119">**Add**</span></span>  
 <span data-ttu-id="53336-120">按一下即可加入類別參考。</span><span class="sxs-lookup"><span data-stu-id="53336-120">Click to add a class reference.</span></span> <span data-ttu-id="53336-121">按一下省略號 ( ... ) ] 按鈕以開啟 [**開啟**] 對話方塊，並選取完成報表處理和運算式評估所需的類別。</span><span class="sxs-lookup"><span data-stu-id="53336-121">Click the ellipsis (...) button to open the **Open** dialog box and select the classes necessary to complete report processing and expression evaluation.</span></span>  
  
 <span data-ttu-id="53336-122">**移除**</span><span class="sxs-lookup"><span data-stu-id="53336-122">**Remove**</span></span>  
 <span data-ttu-id="53336-123">若要刪除類別執行個體，請選取該執行個體，並按一下 **[移除]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="53336-123">To delete the class instance, select it and click the **Remove** button.</span></span>  
  
 <span data-ttu-id="53336-124">**設定**</span><span class="sxs-lookup"><span data-stu-id="53336-124">**Up**</span></span>  
 <span data-ttu-id="53336-125">若為具有相依性的類別，您可將這個參考移動至清單中的較高位置。</span><span class="sxs-lookup"><span data-stu-id="53336-125">For classes that have dependencies, you can move this reference higher in the list.</span></span>  
  
 <span data-ttu-id="53336-126">**Down**</span><span class="sxs-lookup"><span data-stu-id="53336-126">**Down**</span></span>  
 <span data-ttu-id="53336-127">若為具有相依性的類別，您可將這個參考移動至清單中的較低位置。</span><span class="sxs-lookup"><span data-stu-id="53336-127">For classes that have dependencies, you can move this reference lower in the list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53336-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="53336-128">See Also</span></span>  
 <span data-ttu-id="53336-129">[對話方塊、窗格和嚮導的報表產生器說明](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md) </span><span class="sxs-lookup"><span data-stu-id="53336-129">[Report Builder Help for Dialog Boxes, Panes, and Wizards](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md) </span></span>  
 [<span data-ttu-id="53336-130">運算式 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="53336-130">Expressions &#40;Report Builder and SSRS&#41;</span></span>](report-design/expressions-report-builder-and-ssrs.md)  
  
  
