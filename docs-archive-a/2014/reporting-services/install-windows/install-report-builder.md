---
title: 安裝獨立版本的報表產生器 (報表產生器) |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 6b2291bb-1d20-4d08-81cb-a16dd8e01faf
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2ba8c132125f56ad833a71a1c82221e2bf28d13e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597632"
---
# <a name="install-the-stand-alone-version-of-report-builder-report-builder"></a><span data-ttu-id="ec045-102">安裝單機版報表產生器 (報表產生器)</span><span class="sxs-lookup"><span data-stu-id="ec045-102">Install the Stand-Alone Version of Report Builder (Report Builder)</span></span>
  <span data-ttu-id="ec045-103">您可以從 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [Microsoft 下載中心](https://www.microsoft.com/download/details.aspx?id=53613)的功能套件安裝報表產生器，或在已下載 ReportBuilder3_x86.msi （報表產生器的 Windows Installer 套件）的位置（例如公用資料夾）。</span><span class="sxs-lookup"><span data-stu-id="ec045-103">You can install Report Builder from the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] feature pack on the [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=53613) or a location such as public folder to which the ReportBuilder3_x86.msi, the Windows Installer Package for Report Builder, has been downloaded.</span></span>  
  
 <span data-ttu-id="ec045-104">您也可以執行報表產生器的命令列安裝，並提供引數來自訂安裝。</span><span class="sxs-lookup"><span data-stu-id="ec045-104">You can also perform a command line installation of Report Builder and provide arguments to customize the installation.</span></span> <span data-ttu-id="ec045-105">除了標準的 MSI 內建參數以外，您還可以使用報表產生器所提供的自訂參數：RBINSTALLDIR 和 REPORTSERVERURL。</span><span class="sxs-lookup"><span data-stu-id="ec045-105">In addition to the standard MSI intrinsic parameters, you can use the custom parameters that Report Builder provides: RBINSTALLDIR and REPORTSERVERURL.</span></span> <span data-ttu-id="ec045-106">RBINSTALLDIR 會指定報表產生器的根安裝資料夾。</span><span class="sxs-lookup"><span data-stu-id="ec045-106">RBINSTALLDIR specifies the root installation folder for Report Builder.</span></span> <span data-ttu-id="ec045-107">REPORTSERVERURL 會指定報表產生器用來在伺服器上儲存報表的預設報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="ec045-107">REPORTSERVERURL specifies the default report server that Report Builder uses to save reports on the server.</span></span>  
  
 <span data-ttu-id="ec045-108">如果您想要進行完全無訊息的安裝 (完全沒有使用者介面互動)，請指定 **/quiet** 選項。</span><span class="sxs-lookup"><span data-stu-id="ec045-108">If you want a completely silent installation, with no user interface interaction at all, specify the **/quiet** option.</span></span> <span data-ttu-id="ec045-109">根據設計，quiet 選項旗標會隱藏安裝錯誤。</span><span class="sxs-lookup"><span data-stu-id="ec045-109">By design, the quiet option flag suppresses installation errors.</span></span> <span data-ttu-id="ec045-110">因此，當您使用 quiet 選項時，建議您加入 **/l** 選項 (指定記錄)。</span><span class="sxs-lookup"><span data-stu-id="ec045-110">It is therefore recommended that you include the **/l** option, which specifies logging, when you use the quiet option.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="ec045-111">Windows Vista 和 Windows 7 安全性功能需要更高的權限才能執行命令列作業，並且會提示執行命令列的權限。</span><span class="sxs-lookup"><span data-stu-id="ec045-111">Windows Vista and Windows 7 security features require elevated permissions to run command line operations and will prompt for permission to run the command line.</span></span> <span data-ttu-id="ec045-112">安裝不是無訊息的。</span><span class="sxs-lookup"><span data-stu-id="ec045-112">The installation is not silent.</span></span> <span data-ttu-id="ec045-113">若要進行無訊息安裝，您必須以管理員的身分執行命令列。</span><span class="sxs-lookup"><span data-stu-id="ec045-113">To make the installation silent, you need to run the command line as an administrator.</span></span>  
  
### <a name="to-install-report-builder-from-the-download-site"></a><span data-ttu-id="ec045-114">若要從下載網站安裝報表產生器</span><span class="sxs-lookup"><span data-stu-id="ec045-114">To install Report Builder from the download site</span></span>  
  
1.  <span data-ttu-id="ec045-115">移至[Microsoft SQL Server 2012 報表產生器](https://go.microsoft.com/fwlink/?LinkID=219138)，並找出網頁的 [報表產生器] 區段。</span><span class="sxs-lookup"><span data-stu-id="ec045-115">Go to [Microsoft SQL Server 2012 Report Builder](https://go.microsoft.com/fwlink/?LinkID=219138) and locate the Report Builder section of the Web page.</span></span>  
  
2.  <span data-ttu-id="ec045-116">按一下 [ **X86 套件**]。</span><span class="sxs-lookup"><span data-stu-id="ec045-116">Click **X86 Package**.</span></span>  
  
3.  <span data-ttu-id="ec045-117">在 [檔案**下載**] 對話方塊中，按一下 [**執行**]。</span><span class="sxs-lookup"><span data-stu-id="ec045-117">In the **File Download** dialog box, click **Run**.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="ec045-118">僅從信任的來源下載檔案。</span><span class="sxs-lookup"><span data-stu-id="ec045-118">Download only files from trusted sources.</span></span>  
  
4.  <span data-ttu-id="ec045-119">在 [Internet Explorer] 對話方塊中，按一下 [**執行**]。</span><span class="sxs-lookup"><span data-stu-id="ec045-119">In the Internet Explorer dialog box, click **Run**.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="ec045-120">僅從信任的來源執行檔案。</span><span class="sxs-lookup"><span data-stu-id="ec045-120">Run only files from trusted sources.</span></span>  
  
5.  <span data-ttu-id="ec045-121">[Microsoft SQL Server 報表產生器精靈] 隨即啟動。</span><span class="sxs-lookup"><span data-stu-id="ec045-121">The Microsoft SQL Server Report Builder Wizard is launched.</span></span>  
  
6.  <span data-ttu-id="ec045-122">在 [**歡迎使用安裝精靈]** 頁面上，按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="ec045-122">On the **Welcome to the Installation Wizard** page, click **Next**.</span></span>  
  
7.  <span data-ttu-id="ec045-123">閱讀 [**授權合約**] 頁面上的合約，然後選取 [**我接受授權合約中的條款**] 選項。</span><span class="sxs-lookup"><span data-stu-id="ec045-123">On the **License Agreement** page, read the agreement and then select the **I accept the terms in the license agreement** option.</span></span> <span data-ttu-id="ec045-124">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="ec045-124">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="ec045-125">提供您的個人姓名和公司名稱。</span><span class="sxs-lookup"><span data-stu-id="ec045-125">Provide your personal name and company name.</span></span> <span data-ttu-id="ec045-126">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="ec045-126">Click **Next**.</span></span>  
  
9. <span data-ttu-id="ec045-127">在 [**特徵選取**] 頁面上，選擇性地按一下 **[流覽] 或 [** **磁片成本**]。</span><span class="sxs-lookup"><span data-stu-id="ec045-127">On the **Feature Selection** page, optionally click **Browse** or **Disk Cost**.</span></span> <span data-ttu-id="ec045-128">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="ec045-128">Click **Next**.</span></span>  
  
    -   <span data-ttu-id="ec045-129">按一下 **[流覽]** 以查看報表產生器的預設位置，並加以更新。</span><span class="sxs-lookup"><span data-stu-id="ec045-129">Click **Browse** to see the default location of Report Builder and update it.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="ec045-130">報表產生器的預設安裝資料夾為 \<drive> Program Files\Microsoft SQL Server。</span><span class="sxs-lookup"><span data-stu-id="ec045-130">The default installation folder for Report Builder is \<drive>Program Files\Microsoft SQL Server.</span></span>  
  
    -   <span data-ttu-id="ec045-131">按一下 [**磁片成本**] 以瞭解報表產生器使用多少磁碟空間。</span><span class="sxs-lookup"><span data-stu-id="ec045-131">Click **Disk Cost** to learn how much disk space Report Builder consumes.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="ec045-132">如果磁碟區沒有足夠的可用磁碟空間數量，該磁碟區就會反白顯示。</span><span class="sxs-lookup"><span data-stu-id="ec045-132">If a volume does not have sufficient amount of free disk space, the volume is highlighted.</span></span>  
  
10. <span data-ttu-id="ec045-133">在 **[預設的目標伺服器]** 頁面上，選擇性地提供目標報表伺服器的 URL (如果它與預設值不同的話)。</span><span class="sxs-lookup"><span data-stu-id="ec045-133">On the **Default Target Server** page, optionally provide the URL to the target report server if it is different from the default.</span></span> <span data-ttu-id="ec045-134">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="ec045-134">Click **Next**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ec045-135">如果您計畫在報表產生器連接至報表伺服器時使用它，此時提供伺服器的 URL 比較方便。</span><span class="sxs-lookup"><span data-stu-id="ec045-135">If you plan to work with Report Builder when it is connected to a report server, it is convenient to provide the URL to the server at this time.</span></span> <span data-ttu-id="ec045-136">不過，當您在報表產生器中工作時，也可以從 [**選項**] 對話方塊執行此動作。</span><span class="sxs-lookup"><span data-stu-id="ec045-136">However, you can also do this from the **Options** dialog box when you are working in Report Builder.</span></span>  
  
11. <span data-ttu-id="ec045-137">按一下 [**安裝**]，完成報表產生器的安裝。</span><span class="sxs-lookup"><span data-stu-id="ec045-137">Click **Install** to complete the installation of Report Builder.</span></span>  
  
### <a name="to-install-report-builder-from-a-share"></a><span data-ttu-id="ec045-138">若要從共用位置安裝報表產生器</span><span class="sxs-lookup"><span data-stu-id="ec045-138">To install Report Builder from a share</span></span>  
  
1.  <span data-ttu-id="ec045-139">如需您在本機電腦上安裝報表產生器所執行之 ReportBuilder3_x86.msi.msi 的位置，請連絡系統管理員。</span><span class="sxs-lookup"><span data-stu-id="ec045-139">Contact your administrator for the location of ReportBuilder3_x86.msi.msi that you run to install Report Builder on your local computer.</span></span>  
  
2.  <span data-ttu-id="ec045-140">瀏覽並找出 ReportBuilder3_x86.msi.msi (報表產生器的 Windows 安裝程式套件 (MSI))，然後按一下此檔案。</span><span class="sxs-lookup"><span data-stu-id="ec045-140">Browse to locate the ReportBuilder3_x86.msi.msi, the Windows Installer Package (MSI) for Report Builder, and click it.</span></span>  
  
     <span data-ttu-id="ec045-141">[Microsoft SQL Server 報表產生器精靈] 隨即啟動。</span><span class="sxs-lookup"><span data-stu-id="ec045-141">The Microsoft SQL Server Report Builder Wizard is launched.</span></span>  
  
3.  <span data-ttu-id="ec045-142">在 [**歡迎使用安裝精靈]** 頁面上，按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="ec045-142">On the **Welcome to the Installation Wizard** page, click **Next**.</span></span>  
  
4.  <span data-ttu-id="ec045-143">閱讀 [**授權合約**] 頁面上的合約，然後選取 [**我接受授權合約中的條款**] 選項。</span><span class="sxs-lookup"><span data-stu-id="ec045-143">On the **License Agreement** page, read the agreement and then select the **I accept the terms in the license agreement** option.</span></span> <span data-ttu-id="ec045-144">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="ec045-144">Click **Next**.</span></span>  
  
5.  <span data-ttu-id="ec045-145">提供您的個人姓名和公司名稱。</span><span class="sxs-lookup"><span data-stu-id="ec045-145">Provide your personal name and company name.</span></span> <span data-ttu-id="ec045-146">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="ec045-146">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="ec045-147">在 [**特徵選取**] 頁面上，選擇性地按一下 **[流覽] 或 [** **磁片成本**]。</span><span class="sxs-lookup"><span data-stu-id="ec045-147">On the **Feature Selection** page, optionally click **Browse** or **Disk Cost**.</span></span> <span data-ttu-id="ec045-148">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="ec045-148">Click **Next**.</span></span>  
  
    -   <span data-ttu-id="ec045-149">按一下 **[流覽]** 以查看報表產生器的預設位置，並加以更新。</span><span class="sxs-lookup"><span data-stu-id="ec045-149">Click **Browse** to see the default location of Report Builder and update it.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="ec045-150">報表產生器的預設安裝資料夾為 \<drive> Program Files\Microsoft SQL Server。</span><span class="sxs-lookup"><span data-stu-id="ec045-150">The default installation folder for Report Builder is \<drive>Program Files\Microsoft SQL Server.</span></span>  
  
    -   <span data-ttu-id="ec045-151">按一下 [**磁片成本**] 以瞭解報表產生器使用多少磁碟空間。</span><span class="sxs-lookup"><span data-stu-id="ec045-151">Click **Disk Cost** to learn how much disk space Report Builder consumes.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="ec045-152">如果磁碟區沒有足夠的可用磁碟空間數量，該磁碟區就會反白顯示。</span><span class="sxs-lookup"><span data-stu-id="ec045-152">If a volume does not have sufficient amount of free disk space, the volume is highlighted.</span></span>  
  
7.  <span data-ttu-id="ec045-153">在 **[預設的目標伺服器]** 頁面上，選擇性地提供目標報表伺服器的 URL (如果它與預設值不同的話)。</span><span class="sxs-lookup"><span data-stu-id="ec045-153">On the **Default Target Server** page, optionally provide the URL to the target report server if it is different from the default.</span></span> <span data-ttu-id="ec045-154">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="ec045-154">Click **Next**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ec045-155">如果您計畫在報表產生器連接至報表伺服器時使用它，此時提供伺服器的 URL 比較方便。</span><span class="sxs-lookup"><span data-stu-id="ec045-155">If you plan to work with Report Builder when it is connected to a report server, it is convenient to provide the URL to the server at this time.</span></span> <span data-ttu-id="ec045-156">不過，當您在報表產生器中工作時，也可以從 [**選項**] 對話方塊執行此動作。</span><span class="sxs-lookup"><span data-stu-id="ec045-156">However, you can also do this from the **Options** dialog box when you are working in Report Builder.</span></span>  
  
8.  <span data-ttu-id="ec045-157">按一下 [**安裝**]，完成報表產生器的安裝。</span><span class="sxs-lookup"><span data-stu-id="ec045-157">Click **Install** to complete the installation of Report Builder.</span></span>  
  
### <a name="to-install-report-builder-from-the-command-line"></a><span data-ttu-id="ec045-158">若要從命令列安裝報表產生器</span><span class="sxs-lookup"><span data-stu-id="ec045-158">To install Report Builder from the command line</span></span>  
  
1.  <span data-ttu-id="ec045-159">移至[Microsoft SQL Server 2012 報表產生器](https://go.microsoft.com/fwlink/?LinkID=219138)，並找出 [報表產生器] 區段。</span><span class="sxs-lookup"><span data-stu-id="ec045-159">Go to [Microsoft SQL Server 2012 Report Builder](https://go.microsoft.com/fwlink/?LinkID=219138) and locate the Report Builder section.</span></span>  
  
2.  <span data-ttu-id="ec045-160">按一下 [ **X86 套件**]。</span><span class="sxs-lookup"><span data-stu-id="ec045-160">Click **X86 Package**.</span></span>  
  
3.  <span data-ttu-id="ec045-161">按一下 [儲存]。</span><span class="sxs-lookup"><span data-stu-id="ec045-161">Click Save.</span></span>  
  
4.  <span data-ttu-id="ec045-162">（選擇性）流覽至要儲存的位置，確認 [**另存**新檔] 選項是**Windows Installer 封裝**]，然後按一下 [**儲存**]。</span><span class="sxs-lookup"><span data-stu-id="ec045-162">Optionally, browse to the location to save to, verify the **Save as** option is **Windows Installer Package**, and then click **Save**.</span></span>  
  
5.  <span data-ttu-id="ec045-163">在 **[開始]** 功能表上，按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="ec045-163">On the **Start** menu, click **Run**.</span></span>  
  
6.  <span data-ttu-id="ec045-164">在 [開啟] 文字方塊中，輸入 `cmd.`</span><span class="sxs-lookup"><span data-stu-id="ec045-164">In the Open text box, type `cmd.`</span></span>  
  
7.  <span data-ttu-id="ec045-165">在 [命令提示字元] 視窗中，巡覽至儲存 ReportBuilder3_x86.msi 的資料夾。</span><span class="sxs-lookup"><span data-stu-id="ec045-165">In the Command Prompt window, navigate to the folder where you saved ReportBuilder3_x86.msi.</span></span>  
  
8.  <span data-ttu-id="ec045-166">輸入下列格式的命令：</span><span class="sxs-lookup"><span data-stu-id="ec045-166">Type a command with the following format:</span></span>  
  
     `msiexec/i ReportBuilder3_.msi /option [value] [/option [value]]`  
  
     <span data-ttu-id="ec045-167">安裝報表產生器的兩個專屬選項是：RBINSTALLDIR 和 REPORTSERVERURL。</span><span class="sxs-lookup"><span data-stu-id="ec045-167">The two options specific to installing Report Builder are: RBINSTALLDIR and REPORTSERVERURL.</span></span> <span data-ttu-id="ec045-168">您不需要在命令列中包含這兩個引數。</span><span class="sxs-lookup"><span data-stu-id="ec045-168">It not required that you include these arguments in the command line.</span></span> <span data-ttu-id="ec045-169">以下為基準命令：</span><span class="sxs-lookup"><span data-stu-id="ec045-169">The following is the baseline command:</span></span>  
  
     `msiexec /i ReportBuilder3_x86.msi /quiet`  
  
9. <span data-ttu-id="ec045-170">若要執行命令，請按 Enter 鍵。</span><span class="sxs-lookup"><span data-stu-id="ec045-170">To run the command, press Enter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec045-171">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ec045-171">See Also</span></span>  
 <span data-ttu-id="ec045-172">[安裝、卸載和報表產生器支援](../install-uninstall-and-report-builder-support.md) </span><span class="sxs-lookup"><span data-stu-id="ec045-172">[Install, Uninstall, and Report Builder Support](../install-uninstall-and-report-builder-support.md) </span></span>  
 [<span data-ttu-id="ec045-173">將獨立版本的報表產生器 &#40;報表產生器卸載&#41;</span><span class="sxs-lookup"><span data-stu-id="ec045-173">Uninstall the Stand-Alone Version of Report Builder &#40;Report Builder&#41;</span></span>](install-report-builder.md)  
  
  
