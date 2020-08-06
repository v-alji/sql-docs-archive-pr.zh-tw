---
title: 使用我的報表 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 49c3c1da-b106-41f6-9173-16ff225bade8
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 91d44c0aa8471064753d9b4fb0ecc0de89aa8396
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593813"
---
# <a name="using-my-reports-report-builder-and-ssrs"></a><span data-ttu-id="33dd6-102">使用我的報表 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="33dd6-102">Using My Reports (Report Builder and SSRS)</span></span>
  <span data-ttu-id="33dd6-103">在設定為原生模式的報表伺服器上，[我的報表] 資料夾是個人的工作空間，可以用來儲存和使用您所擁有的報表。</span><span class="sxs-lookup"><span data-stu-id="33dd6-103">On a report server configured in native mode, the My Reports folder is a personal workspace that you can use to store and work with reports that you own.</span></span> <span data-ttu-id="33dd6-104">其他報表伺服器資料夾都是公開的，通常使用者必須具備進階權限才可以加入或修改資料夾內容。</span><span class="sxs-lookup"><span data-stu-id="33dd6-104">Other report server folders are public and typically require users to have advanced permissions to add to or modify folder contents.</span></span> <span data-ttu-id="33dd6-105">相對地，[我的報表] 資料夾是使用者自行管理的工作空間。</span><span class="sxs-lookup"><span data-stu-id="33dd6-105">In contrast, the My Reports folder is a user-managed workspace.</span></span> <span data-ttu-id="33dd6-106">您可以加入或移除報表和資料夾，以及使用個人化的設定來儲存連結報表。</span><span class="sxs-lookup"><span data-stu-id="33dd6-106">You can add or remove reports and folders and save linked reports with personalized settings.</span></span>  
  
 <span data-ttu-id="33dd6-107">在概念上，[我的報表] 資料夾類似於 Windows 檔案系統的 [我的文件] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="33dd6-107">Conceptually, the My Reports folder is similar to the My Documents folder in the Windows file system.</span></span> <span data-ttu-id="33dd6-108">雖然每一位使用者都有稱為 [我的報表] 的資料夾，但每一位使用者存取的資料夾與其他人都不相同。</span><span class="sxs-lookup"><span data-stu-id="33dd6-108">Although each user has a folder called My Reports, the folder that each accesses is different from all other users.</span></span> <span data-ttu-id="33dd6-109">除了報表伺服器管理員之外，其他使用者都無法存取屬於您的 [我的報表] 資料夾的內容。</span><span class="sxs-lookup"><span data-stu-id="33dd6-109">Except for report server administrators, other users cannot access the contents of the My Reports folder that belongs to you.</span></span>  
  
 <span data-ttu-id="33dd6-110">[我的報表] 功能是選擇性的，可以由報表伺服器管理員停用。</span><span class="sxs-lookup"><span data-stu-id="33dd6-110">The My Reports feature is optional and can be disabled by a report server administrator.</span></span> <span data-ttu-id="33dd6-111">如果有啟用「我的報表」，您就會在 [主資料夾] 資料夾中看到 [我的報表] 資料夾，您可以使用報表管理員或 Web 瀏覽器來存取其內容。</span><span class="sxs-lookup"><span data-stu-id="33dd6-111">If it is enabled, you will see a My Reports folder in the Home folder, which you can access using the Report Manager or a Web browser.</span></span> <span data-ttu-id="33dd6-112">如需詳細資訊，請參閱[在報表管理員中尋找及檢視報表 &#40;報表產生器及 SSRS&#41;](finding-and-viewing-reports-in-the-web-portal-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="33dd6-112">For more information, see [Finding and Viewing Reports in Report Manager &#40;Report Builder and SSRS&#41;](finding-and-viewing-reports-in-the-web-portal-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="33dd6-113">在設定為 SharePoint 整合模式的報表伺服器上，[我的報表] 資料夾沒有任何對等項目。</span><span class="sxs-lookup"><span data-stu-id="33dd6-113">On a report server configured in SharePoint integrated mode, there is no equivalent to the My Reports folder.</span></span> <span data-ttu-id="33dd6-114">如需詳細資訊，請參閱 [尋找、檢視和管理報表 &#40;報表產生器及 SSRS &#41;](finding-viewing-and-managing-reports-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="33dd6-114">For more information, see [Finding, Viewing, and Managing Reports &#40;Report Builder and SSRS &#41;](finding-viewing-and-managing-reports-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="ways-to-use-my-reports"></a><span data-ttu-id="33dd6-115">使用我的報表的方式</span><span class="sxs-lookup"><span data-stu-id="33dd6-115">Ways to Use My Reports</span></span>  
 <span data-ttu-id="33dd6-116">在您加入報表、資料夾和其他項目之前，[我的報表] 是空的。</span><span class="sxs-lookup"><span data-stu-id="33dd6-116">My Reports is empty until you add reports, folders, and other items.</span></span> <span data-ttu-id="33dd6-117">以下是將內容加入至 [我的報表] 的一些方法。</span><span class="sxs-lookup"><span data-stu-id="33dd6-117">Here are some ways to add content to My Reports.</span></span>  
  
-   <span data-ttu-id="33dd6-118">建立個人的連結報表，並將它儲存至 [我的報表]。</span><span class="sxs-lookup"><span data-stu-id="33dd6-118">Create a personal linked report and store it in My Reports.</span></span> <span data-ttu-id="33dd6-119">並非所有的報表都可以連結。</span><span class="sxs-lookup"><span data-stu-id="33dd6-119">Not all reports are available for linking.</span></span> <span data-ttu-id="33dd6-120">如需詳細資訊，請參閱 [建立連結報表](../reports/create-a-linked-report.md)。</span><span class="sxs-lookup"><span data-stu-id="33dd6-120">For more information, see [Create a Linked Report](../reports/create-a-linked-report.md).</span></span>  
  
-   <span data-ttu-id="33dd6-121">從檔案系統上傳報表定義檔 (.rdl)、報表模型檔 (.smdl) 或其他檔案。</span><span class="sxs-lookup"><span data-stu-id="33dd6-121">Upload a report definition (.rdl) file, report model (.smdl) file, or other files from the file system.</span></span> <span data-ttu-id="33dd6-122">您可以上傳任何檔案，但報表伺服器只會處理副檔名為 .rdl 或 .smdl 的報表檔案。</span><span class="sxs-lookup"><span data-stu-id="33dd6-122">You can upload any file, but the report server only processes report files that have an .rdl or .smdl file extension.</span></span> <span data-ttu-id="33dd6-123">如需詳細資訊，請參閱《SQL Server 線上叢書》中 [Reporting Services 文件](https://go.microsoft.com/fwlink/?linkid=121312)的＜報表定義＞以及[上傳檔案或報表 &#40;報表管理員&#41;](../reports/upload-a-file-or-report-report-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="33dd6-123">For more information, see Report Definitions" in the [Reporting Services documentation](https://go.microsoft.com/fwlink/?linkid=121312) in SQL Server Books Online and [Upload a File or Report &#40;Report Manager&#41;](../reports/upload-a-file-or-report-report-manager.md).</span></span>  
  
-   <span data-ttu-id="33dd6-124">建立並發行自己的報表至 [我的報表]。</span><span class="sxs-lookup"><span data-stu-id="33dd6-124">Create and publish your own reports to My Reports.</span></span> <span data-ttu-id="33dd6-125">如需詳細資訊，請參閱[報表設計檢視 &#40;報表產生器&#41;](report-design-view-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="33dd6-125">For more information, see [Report Design View &#40;Report Builder&#41;](report-design-view-report-builder.md).</span></span>  
  
 <span data-ttu-id="33dd6-126">通常 [我的報表] 的權限設定，可以讓您自行管理此資料夾。</span><span class="sxs-lookup"><span data-stu-id="33dd6-126">Usually, permissions on My Reports allow you to manage the folder yourself.</span></span> <span data-ttu-id="33dd6-127">不過，報表伺服器管理員才是最終決定使用者可執行哪些工作的人。</span><span class="sxs-lookup"><span data-stu-id="33dd6-127">However, the report server administrator ultimately determines which tasks users can perform.</span></span> <span data-ttu-id="33dd6-128">如果因權限不足而無法使用 [我的報表]，請洽詢報表伺服器管理員。</span><span class="sxs-lookup"><span data-stu-id="33dd6-128">If insufficient permissions prevent you from working with My Reports, see your report server administrator.</span></span>  
  
## <a name="searching-my-reports"></a><span data-ttu-id="33dd6-129">搜尋 [我的報表]</span><span class="sxs-lookup"><span data-stu-id="33dd6-129">Searching My Reports</span></span>  
 <span data-ttu-id="33dd6-130">在搜尋報表伺服器資料庫時，[我的報表] 資料夾的內容將包含在搜尋中，但是會排除其他使用者的 [我的報表] 資料夾的內容。</span><span class="sxs-lookup"><span data-stu-id="33dd6-130">When you search a report server database, the contents of your My Reports folder are included in the search, while the contents of other user's My Reports folders are excluded.</span></span> <span data-ttu-id="33dd6-131">搜尋結果清單只會包含您有權存取的報表。</span><span class="sxs-lookup"><span data-stu-id="33dd6-131">Search results list only the reports to which you have access.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33dd6-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="33dd6-132">See Also</span></span>  
 [<span data-ttu-id="33dd6-133">尋找、檢視和管理報表 &#40;報表產生器及 SSRS &#41;</span><span class="sxs-lookup"><span data-stu-id="33dd6-133">Finding, Viewing, and Managing Reports &#40;Report Builder and SSRS &#41;</span></span>](finding-viewing-and-managing-reports-report-builder-and-ssrs.md)  
  
  
