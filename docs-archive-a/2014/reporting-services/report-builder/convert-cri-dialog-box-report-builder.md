---
title: 轉換 CRI 對話方塊 (報表產生器) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10008"
helpviewer_keywords:
- CRI
- custom report items
ms.assetid: 2a3f2ac6-667e-4498-8b73-9c40beb993f5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 97a6c14b9486b2cc82d514bd7a7fa8210bc22204
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592499"
---
# <a name="convert-cri-dialog-box-report-builder"></a><span data-ttu-id="ec4a4-102">轉換 CRI 對話方塊 (報表產生器)</span><span class="sxs-lookup"><span data-stu-id="ec4a4-102">Convert CRI Dialog Box (Report Builder)</span></span>
  <span data-ttu-id="ec4a4-103">此報表包含自訂報表項目 (CRI) 與不支援的功能。</span><span class="sxs-lookup"><span data-stu-id="ec4a4-103">This report contains custom report items (CRIs) with unsupported features.</span></span> <span data-ttu-id="ec4a4-104">CRI 是報表定義語言 (RDL) 的延伸模組，支援在報表中顯示資料的自訂物件。</span><span class="sxs-lookup"><span data-stu-id="ec4a4-104">CRIs are extensions to the Report Definition Language (RDL) that support custom objects that display data in a report.</span></span> <span data-ttu-id="ec4a4-105">CRI 包括軟體協力廠商所提供的設計階段和執行階段元件。</span><span class="sxs-lookup"><span data-stu-id="ec4a4-105">CRIs include design-time and run-time components that are supplied by third-party software vendors.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ec4a4-106">選擇在報表伺服器上支援自訂報表項目是由系統管理員所做的決定。</span><span class="sxs-lookup"><span data-stu-id="ec4a4-106">Choosing to support custom report items on a report server is a decision made by the system administrator.</span></span> <span data-ttu-id="ec4a4-107">若要檢視報表中的 CRI，必須在報表撰寫用戶端上安裝 CRI 元件才能預覽報表，並在報表伺服器上檢視已發行或已上傳的報表。</span><span class="sxs-lookup"><span data-stu-id="ec4a4-107">To view CRIs in a report, the CRI components must be installed on the report authoring client to preview a report and on the report server to view a published or uploaded report.</span></span> <span data-ttu-id="ec4a4-108">如需詳細資訊，請參閱 [Custom Report Items](../custom-report-items/custom-report-items.md)以及軟體協力廠商的文件。</span><span class="sxs-lookup"><span data-stu-id="ec4a4-108">For more information, see [Custom Report Items](../custom-report-items/custom-report-items.md), and documentation from the third-party software vendor.</span></span>  
  
 <span data-ttu-id="ec4a4-109">某些 CRI 可以轉換成新報表定義格式的報表項目。</span><span class="sxs-lookup"><span data-stu-id="ec4a4-109">Some CRIs can be converted to report items in the new report definition format.</span></span> <span data-ttu-id="ec4a4-110">當您開啟報表時，系統會提示您是否要升級。</span><span class="sxs-lookup"><span data-stu-id="ec4a4-110">When you open the report, you are prompted whether to upgrade.</span></span> <span data-ttu-id="ec4a4-111">您可以使用下列資訊來決定是否要轉換此報表中的 CRI：</span><span class="sxs-lookup"><span data-stu-id="ec4a4-111">Use the following information to decide whether to convert the CRIs in this report:</span></span>  
  
-   <span data-ttu-id="ec4a4-112">**是** ：選擇 **[是]** ，在可能的情況下轉換報表中的所有 CRI。</span><span class="sxs-lookup"><span data-stu-id="ec4a4-112">**Yes** Choose **Yes** to convert all the CRIs in the report, where possible.</span></span> <span data-ttu-id="ec4a4-113">在 CRI 中不支援的功能無法升級，而且會從報表定義檔案中移除。</span><span class="sxs-lookup"><span data-stu-id="ec4a4-113">Unsupported features in the CRIs cannot be upgraded and are removed from the report definition file.</span></span> <span data-ttu-id="ec4a4-114">如需不支援的功能清單，請參閱 [升級報表](../install-windows/upgrade-reports.md)。</span><span class="sxs-lookup"><span data-stu-id="ec4a4-114">For the list of unsupported features, see [Upgrade Reports](../install-windows/upgrade-reports.md).</span></span> <span data-ttu-id="ec4a4-115">檢視報表時，您可能會看到 CRI 在報表中顯示的方式有些差異。</span><span class="sxs-lookup"><span data-stu-id="ec4a4-115">When you view the report, you might see differences in the way the CRI displays in the report.</span></span>  
  
-   <span data-ttu-id="ec4a4-116">**否** ：當您不要轉換報表中的 CRI 時，選擇 **[否]** 。</span><span class="sxs-lookup"><span data-stu-id="ec4a4-116">**No** Choose **No** when you do not want to convert the CRIs in the report.</span></span> <span data-ttu-id="ec4a4-117">這些 CRI 無法透過報表處理器顯示在其目前的版本中。</span><span class="sxs-lookup"><span data-stu-id="ec4a4-117">These CRIs cannot be displayed by the report processor in their current version.</span></span> <span data-ttu-id="ec4a4-118">如果您的系統管理員打算安裝軟體協力廠商所提供，而且與新報表定義格式相容的新版 CRI，您應該選擇 **[否]** 。</span><span class="sxs-lookup"><span data-stu-id="ec4a4-118">If your system administrator is planning to install a new version of the CRI from the third-party software vendor that is compatible with the new report definition format, you should choose **No**.</span></span> <span data-ttu-id="ec4a4-119">在新版本提供之前，CRI 會在報表中顯示為一個有紅色 X 的空文字方塊。</span><span class="sxs-lookup"><span data-stu-id="ec4a4-119">Until new versions are available, the CRIs display in the report as an empty text box with a red X.</span></span>  
  
 <span data-ttu-id="ec4a4-120">不論是哪一種情況，都會將報表升級為新的報表定義格式，並將原始報表的備份副本儲存為 *\<Report Name>* `-` backup .rdl。</span><span class="sxs-lookup"><span data-stu-id="ec4a4-120">In either case, the report is upgraded to the new report definition format and a backup copy of the original report is saved as *\<Report Name>* `-` Backup.rdl.</span></span> <span data-ttu-id="ec4a4-121">如果您以報表撰寫工具儲存報表，您就是以新的報表定義格式儲存升級的報表。</span><span class="sxs-lookup"><span data-stu-id="ec4a4-121">If you save the report in your report authoring tool, you are saving the upgraded report in the new report definition format.</span></span> <span data-ttu-id="ec4a4-122">如果您發行報表，此報表會先儲存在您的電腦中，然後再發行到報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="ec4a4-122">If you publish the report, the report is first saved on your computer, and then published to the report server.</span></span> <span data-ttu-id="ec4a4-123">您會將升級版本的報表發行至報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="ec4a4-123">You are publishing the upgraded version of the report to the report server.</span></span>  
  
 <span data-ttu-id="ec4a4-124">如果您沒有儲存報表，原始報表就會維持不變。</span><span class="sxs-lookup"><span data-stu-id="ec4a4-124">If you do not save the report, the original report remains unchanged.</span></span> <span data-ttu-id="ec4a4-125">不過，您無法在 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 的更新版 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] 中，或使用此報表定義格式的報表撰寫環境中編輯此報表。</span><span class="sxs-lookup"><span data-stu-id="ec4a4-125">However, you cannot edit this report in a [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] later version of [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] or a report authoring environment that uses this report definition format.</span></span> <span data-ttu-id="ec4a4-126">您可以使用報表管理員將原始版本的報表上傳到 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 或更新版的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 報表伺服器，繼續執行該報表。</span><span class="sxs-lookup"><span data-stu-id="ec4a4-126">You can continue to run the original version of the report by uploading it to a [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] or later [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report server by using Report Manager.</span></span> <span data-ttu-id="ec4a4-127">如需詳細資訊，請參閱[上傳檔案或報表 &#40;報表管理員&#41;](../reports/upload-a-file-or-report-report-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="ec4a4-127">For more information, see [Upload a File or Report &#40;Report Manager&#41;](../reports/upload-a-file-or-report-report-manager.md).</span></span>  
  
 <span data-ttu-id="ec4a4-128">對於您上傳 (而非發行) 到報表伺服器的報表，報表處理器會決定是否可以在第一次使用時升級報表。</span><span class="sxs-lookup"><span data-stu-id="ec4a4-128">For reports that you upload instead of publish to a report server, the report processor determines whether the report can be upgraded on first use.</span></span> <span data-ttu-id="ec4a4-129">無法升級的報表會在回溯相容性模式下處理，而且會如同在舊版 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]中繼續顯示。</span><span class="sxs-lookup"><span data-stu-id="ec4a4-129">Reports that cannot be upgraded are processed in backward-compatibility mode, and continue to display as they did in the earlier version of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="ec4a4-130">如需詳細資訊，請參閱 [Upgrade Reports](../install-windows/upgrade-reports.md)。</span><span class="sxs-lookup"><span data-stu-id="ec4a4-130">For more information, see [Upgrade Reports](../install-windows/upgrade-reports.md).</span></span>  
  
 <span data-ttu-id="ec4a4-131">若要識別報表、報表伺服器或您報表撰寫環境的目前報表定義格式，請參閱[尋找報表定義結構描述版本 &#40;SSRS&#41;](../reports/find-the-report-definition-schema-version-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="ec4a4-131">To identify the current report definition format for a report, for a report server, or for your report authoring environment, see [Find the Report Definition Schema Version &#40;SSRS&#41;](../reports/find-the-report-definition-schema-version-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec4a4-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ec4a4-132">See Also</span></span>  
 [<span data-ttu-id="ec4a4-133">對話方塊、窗格和精靈的報表產生器說明</span><span class="sxs-lookup"><span data-stu-id="ec4a4-133">Report Builder Help for Dialog Boxes, Panes, and Wizards</span></span>](../report-builder-help-for-dialog-boxes-panes-and-wizards.md)  
  
  
