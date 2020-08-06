---
title: 將獨立版本的報表產生器 (報表產生器) 卸載 |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 009538c6-4941-4393-b14b-9144cffdbdaf
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: cda13248d1aa14ee3d57a951872d3ad8ded17da9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598744"
---
# <a name="uninstall-the-stand-alone-version-of-report-builder-report-builder"></a><span data-ttu-id="e6106-102">解除安裝單機版報表產生器 (報表產生器)</span><span class="sxs-lookup"><span data-stu-id="e6106-102">Uninstall the Stand-Alone Version of Report Builder (Report Builder)</span></span>
  <span data-ttu-id="e6106-103">您可以從控制台或命令列解除安裝單機版本的報表產生器。</span><span class="sxs-lookup"><span data-stu-id="e6106-103">You can uninstall the stand-alone version of Report Builder from the control panel or the command line.</span></span> <span data-ttu-id="e6106-104">如果沒有解除安裝 [!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)]，您就不能解除安裝 [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] 版本的報表產生器。</span><span class="sxs-lookup"><span data-stu-id="e6106-104">You cannot uninstall the [!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)] version of Report Builder without uninstalling [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)].</span></span>  
  
 <span data-ttu-id="e6106-105">從命令列解除安裝報表產生器所用的語法與用來安裝報表產生器的語法完全相同，不過您會使用 /x 選項來取代 /i 選項。</span><span class="sxs-lookup"><span data-stu-id="e6106-105">Uninstalling Report Builder from the command line uses syntax that is identical to the syntax you use to install Report Builder, except you use the /x option instead of the /i option.</span></span> <span data-ttu-id="e6106-106">解除安裝的命令列也可以包含 /quiet 選項和其他標準選項。</span><span class="sxs-lookup"><span data-stu-id="e6106-106">Command lines for uninstalling can also include the /quiet option and other standard options.</span></span> <span data-ttu-id="e6106-107">如果已經移除了報表產生器的 Windows Installer 套件 (ReportBuilder3_x86.msi)，您就無法輕鬆地使用命令列來解除安裝報表產生器。</span><span class="sxs-lookup"><span data-stu-id="e6106-107">If the Report Builder Windows Installer Package (ReportBuilder3_x86.msi) has been removed, you cannot use the command line easily to uninstall Report Builder.</span></span> <span data-ttu-id="e6106-108">若要深入了解有關如何使用 GUID 來移除報表產生器的詳細資訊，請參閱 MSDN Library 上 msiexec 程式的文件集。</span><span class="sxs-lookup"><span data-stu-id="e6106-108">To learn more about how you might be able to remove Report Builder by using its GUID, see the documentation for the msiexec program in the msdn library.</span></span>  
  
 <span data-ttu-id="e6106-109">如果報表產生器使用的資料夾包含自訂檔案，移除報表產生器時便會保留這些資料夾和檔案。</span><span class="sxs-lookup"><span data-stu-id="e6106-109">If folders used by Report Builder include custom files, the folders and the files are preserved when Report Builder is removed.</span></span> <span data-ttu-id="e6106-110">系統只會移除報表產生器的檔案。</span><span class="sxs-lookup"><span data-stu-id="e6106-110">Only the Report Builder files are removed.</span></span>  
  
### <a name="to-uninstall-report-builder-from-the-control-panel"></a><span data-ttu-id="e6106-111">若要從控制台解除安裝報表產生器</span><span class="sxs-lookup"><span data-stu-id="e6106-111">To uninstall Report Builder from the control panel</span></span>  
  
1.  <span data-ttu-id="e6106-112">在 **[開始]** 功能表上，按一下 **[控制台]** 。</span><span class="sxs-lookup"><span data-stu-id="e6106-112">On the **Start** menu, click **Control Panel**.</span></span>  
  
2.  <span data-ttu-id="e6106-113">在 [控制台] 中，按一下 **[程式和功能]**。</span><span class="sxs-lookup"><span data-stu-id="e6106-113">In the Control Panel, click **Programs and Features**.</span></span>  
  
3.  <span data-ttu-id="e6106-114">在 [名稱]\*\*\*\* 清單中找出 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 報表產生器，然後按一下它。</span><span class="sxs-lookup"><span data-stu-id="e6106-114">Locate [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Report Builder in the **Name** list and click it.</span></span>  
  
4.  <span data-ttu-id="e6106-115">按一下 [解除安裝]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e6106-115">Click **Uninstall**.</span></span>  
  
5.  <span data-ttu-id="e6106-116">如果出現確認解除安裝報表產生器的提示，請按一下 **[是]**。</span><span class="sxs-lookup"><span data-stu-id="e6106-116">If prompted to confirm the uninstall of Report Builder, click **Yes**.</span></span>  
  
### <a name="to-uninstall-report-builder-from-the-command-line"></a><span data-ttu-id="e6106-117">若要從命令列解除安裝報表產生器</span><span class="sxs-lookup"><span data-stu-id="e6106-117">To uninstall Report Builder from the command line</span></span>  
  
1.  <span data-ttu-id="e6106-118">在 **[開始]** 功能表上，按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="e6106-118">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="e6106-119">在 [**開啟**] 文字方塊中，輸入`cmd.`</span><span class="sxs-lookup"><span data-stu-id="e6106-119">In the **Open** text box, type `cmd.`</span></span>  
  
3.  <span data-ttu-id="e6106-120">在 [命令提示字元] 視窗中，導覽至包含 ReportBuilder3_x86.msi 的資料夾。</span><span class="sxs-lookup"><span data-stu-id="e6106-120">In the command prompt window, navigate to the folder with ReportBuilder3_x86.msi.</span></span>  
  
4.  <span data-ttu-id="e6106-121">輸入如下的基本命令列：</span><span class="sxs-lookup"><span data-stu-id="e6106-121">Type a basic command line such as the following:</span></span>  
  
 `msiexec /x ReportBuilder3_x86.msi /quiet /l*v install.log`  
  
 <span data-ttu-id="e6106-122">如果可以包含記錄功能，請使用如下所示的命令列：</span><span class="sxs-lookup"><span data-stu-id="e6106-122">If you can to include logging, use a command line such as the following:</span></span>  
  
 `msiexec /x ReportBuilder3_x86.msi /quiet /l*v c:\junk\install.log`  
  
1.  <span data-ttu-id="e6106-123">按 **Enter**。</span><span class="sxs-lookup"><span data-stu-id="e6106-123">Press **Enter**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6106-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e6106-124">See Also</span></span>  
 <span data-ttu-id="e6106-125">[安裝、卸載和報表產生器支援](../install-uninstall-and-report-builder-support.md) </span><span class="sxs-lookup"><span data-stu-id="e6106-125">[Install, Uninstall, and Report Builder Support](../install-uninstall-and-report-builder-support.md) </span></span>  
 [<span data-ttu-id="e6106-126">安裝獨立版本的報表產生器 &#40;報表產生器&#41;</span><span class="sxs-lookup"><span data-stu-id="e6106-126">Install the Stand-Alone Version of Report Builder &#40;Report Builder&#41;</span></span>](install-report-builder.md)  
  
  
