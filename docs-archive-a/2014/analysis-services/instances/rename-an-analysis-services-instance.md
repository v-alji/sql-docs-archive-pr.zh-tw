---
title: 重新命名 Analysis Services 實例 |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- instances of Analysis Services, renaming
- renaming instances of Analysis Services
- names [Analysis Services], renaming instances
- names [Analysis Services]
ms.assetid: 87494741-4a2e-4fed-8061-418fd1e111c3
author: minewiskan
ms.author: owend
ms.openlocfilehash: 763986d82dda7424f2187daf401424fd256ddd64
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702064"
---
# <a name="rename-an-analysis-services-instance"></a><span data-ttu-id="66278-102">重新命名 Analysis Services 執行個體</span><span class="sxs-lookup"><span data-stu-id="66278-102">Rename an Analysis Services Instance</span></span>
  <span data-ttu-id="66278-103">您可以 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 使用 [**重新命名實例**] 對話方塊來重新命名現有的實例。</span><span class="sxs-lookup"><span data-stu-id="66278-103">You can rename an existing instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] by using the **Rename Instance** dialog box.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="66278-104">重新命名執行個體時， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Instance Rename Tool 會以更高的權限執行，並更新與該執行個體相關聯的 Windows 服務名稱、安全性帳戶，以及登錄項目。</span><span class="sxs-lookup"><span data-stu-id="66278-104">While renaming the instance, the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Instance Rename tool runs under elevated privileges, updating the Windows service name, security accounts, and registry entries associated with that instance.</span></span> <span data-ttu-id="66278-105">為確保執行這些動作，請務必以本機系統管理員身分執行此工具。</span><span class="sxs-lookup"><span data-stu-id="66278-105">To ensure that these actions are performed, be sure to run this tool as a local system administrator.</span></span>  
  
 <span data-ttu-id="66278-106">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Instance Rename Tool 不會修改針對原始執行個體建立的程式資料夾。</span><span class="sxs-lookup"><span data-stu-id="66278-106">The [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Instance Rename tool does not modify the program folder that was created for the original instance.</span></span> <span data-ttu-id="66278-107">請勿修改程式資料夾名稱以符合您要重命名的執行個體。</span><span class="sxs-lookup"><span data-stu-id="66278-107">Do not modify the program folder name to match the instance you are renaming.</span></span> <span data-ttu-id="66278-108">變更程式資料夾名稱可以防止安裝程式修復或移除安裝。</span><span class="sxs-lookup"><span data-stu-id="66278-108">Changing a program folder name can prevent Setup from repairing or uninstalling the installation.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="66278-109">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體重新命名工具不適用於叢集環境。</span><span class="sxs-lookup"><span data-stu-id="66278-109">The [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Instance Rename tool is not supported for use in a cluster environment.</span></span>  
  
### <a name="to-rename-an-instance-of-analysis-services"></a><span data-ttu-id="66278-110">若要重新命名 Analysis Services 的執行個體</span><span class="sxs-lookup"><span data-stu-id="66278-110">To rename an instance of Analysis Services</span></span>  
  
1.  <span data-ttu-id="66278-111">從 C:\Program Files\Microsoft SQL Server\110\tools\binn\managementstudio 啟動**實例重新命名**工具， **asinstancerename.exe**</span><span class="sxs-lookup"><span data-stu-id="66278-111">Launch the **Instance Rename** tool, **asinstancerename.exe**, from C:\Program Files\Microsoft SQL Server\110\Tools\Binn\ManagementStudio.</span></span>  
  
2.  <span data-ttu-id="66278-112">在 [重新命名執行個體]\*\*\*\* 對話方塊的 [要重新命名的執行個體]\*\*\*\* 清單中，選取您要重新命名的執行個體。</span><span class="sxs-lookup"><span data-stu-id="66278-112">In the **Rename Instance** dialog box, in the **Instance to rename** list, select the instance that you want to rename.</span></span>  
  
3.  <span data-ttu-id="66278-113">在 [新執行個體名稱]\*\*\*\* 方塊中，輸入執行個體的新名稱。</span><span class="sxs-lookup"><span data-stu-id="66278-113">In the **New instance name** box, enter the new name for the instance.</span></span>  
  
4.  <span data-ttu-id="66278-114">確認使用者名稱和密碼正確，然後按一下 [重新命名]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="66278-114">Verify that the user name and password are correct, and then click **Rename**.</span></span>  
  
     <span data-ttu-id="66278-115">Analysis Services 執行個體將會停止，並在名稱變更時重新啟動。</span><span class="sxs-lookup"><span data-stu-id="66278-115">The Analysis Services instance will be stopped and restarted as part of the name change.</span></span>  
  
### <a name="post-rename-checklist"></a><span data-ttu-id="66278-116">重新命名後的清單</span><span class="sxs-lookup"><span data-stu-id="66278-116">Post-rename checklist</span></span>  
  
1.  <span data-ttu-id="66278-117">若要繼續存取在重新命名之執行個體上執行的資料庫，您必須在 Excel 或其他用戶端應用程式中手動更新資料連接。</span><span class="sxs-lookup"><span data-stu-id="66278-117">To resume access to databases that are running on the renamed instance, you will need to manually update the data connections in Excel or other client applications.</span></span> <span data-ttu-id="66278-118">此外，請檢查任何預先定義的連接，例如 Reporting Services 共用資料來源、Excel ODC 檔，或可能參考您剛重新命名之執行個體 BI 語意模型連接檔案。</span><span class="sxs-lookup"><span data-stu-id="66278-118">Also check any predefined connections, such as Reporting Services shared data sources, Excel ODC files, or BI Semantic Model connection files that might reference the instance you just renamed.</span></span> <span data-ttu-id="66278-119">如需相關資訊，請參閱 [連接到 Analysis Services](connect-to-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="66278-119">For more information, see [Connect to Analysis Services](connect-to-analysis-services.md).</span></span>  
  
2.  <span data-ttu-id="66278-120">更新您例行用來備份、同步處理或處理資料庫的 PowerShell 指令碼或 AMO 指令碼。</span><span class="sxs-lookup"><span data-stu-id="66278-120">Update PowerShell scripts or AMO scripts that you routinely use to backup, synchronize, or process databases.</span></span>  
  
3.  <span data-ttu-id="66278-121">更新您在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 中處理之 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]專案的專案屬性。</span><span class="sxs-lookup"><span data-stu-id="66278-121">Update project properties for [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] projects that you work with in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].</span></span> <span data-ttu-id="66278-122">針對表格式模式伺服器執行個體，請務必更新 model.bim 檔案的 [工作空間伺服器] 屬性，以及專案的 [伺服器] 屬性。</span><span class="sxs-lookup"><span data-stu-id="66278-122">For tabular mode server instances, be sure to update the Workspace Server property on the model.bim file, as well as the Server property on the project.</span></span>  
  
4.  <span data-ttu-id="66278-123">根據您指定服務帳戶的方式而定，您可能需要更新授與資料存取權限給服務的資料庫登入或檔案權限 (例如，如果您使用服務帳戶處理資料或存取其他伺服器上的連結物件)。</span><span class="sxs-lookup"><span data-stu-id="66278-123">Depending on how you specified the service account, you might need to update database logins or file permissions that grant data access rights to the service (for example, if you use the service account to process data or access linked objects on another server).</span></span>  
  
     <span data-ttu-id="66278-124">如果您使用虛擬帳戶佈建服務，將需要更新資料庫登入或檔案權限。</span><span class="sxs-lookup"><span data-stu-id="66278-124">Updating a database login or file permissions will be necessary if you used a virtual account to provision the service.</span></span> <span data-ttu-id="66278-125">虛擬帳戶是以執行個體名稱為基礎，因此，如果您重新命名執行個體，同時也會更新虛擬帳戶。</span><span class="sxs-lookup"><span data-stu-id="66278-125">Virtual accounts are based on the instance name, so if you rename the instance, the virtual account is also updated at the same time.</span></span> <span data-ttu-id="66278-126">也就是說，您針對先前的執行個體所建立的任何先前登入或權限都不再有效。</span><span class="sxs-lookup"><span data-stu-id="66278-126">This means that any previous logins or permissions that you created for the previous instance are no longer valid.</span></span>  
  
     <span data-ttu-id="66278-127">下列範例提供說明。</span><span class="sxs-lookup"><span data-stu-id="66278-127">The following example provides an illustration.</span></span> <span data-ttu-id="66278-128">假設您使用預設虛擬帳戶，將表格式模式伺服器安裝為名為 "表格式" 的實例，則會產生下列設定：</span><span class="sxs-lookup"><span data-stu-id="66278-128">Suppose you installed a tabular mode server as an instance named "Tabular" using the default virtual account, resulting in the following configuration:</span></span>  
  
    1.  <span data-ttu-id="66278-129">實例名稱 = \<server> \TABULAR</span><span class="sxs-lookup"><span data-stu-id="66278-129">Instance name = \<server>\TABULAR</span></span>  
  
    2.  <span data-ttu-id="66278-130">服務名稱 = MSOLAP$TABULAR</span><span class="sxs-lookup"><span data-stu-id="66278-130">Service name = MSOLAP$TABULAR</span></span>  
  
    3.  <span data-ttu-id="66278-131">虛擬帳戶 = NT Service\ MSOLAP$TABULAR</span><span class="sxs-lookup"><span data-stu-id="66278-131">Virtual account = NT Service\ MSOLAP$TABULAR</span></span>  
  
     <span data-ttu-id="66278-132">現在假設您將實例重新命名為 "TAB2"。</span><span class="sxs-lookup"><span data-stu-id="66278-132">Now suppose you rename the instance to "TAB2".</span></span> <span data-ttu-id="66278-133">名稱變更之後，您的設定現在看起來如下：</span><span class="sxs-lookup"><span data-stu-id="66278-133">As a result of the name change, your configuration would now look like the following:</span></span>  
  
    1.  <span data-ttu-id="66278-134">實例名稱 = \<server> \TAB2</span><span class="sxs-lookup"><span data-stu-id="66278-134">Instance name = \<server>\TAB2</span></span>  
  
    2.  <span data-ttu-id="66278-135">服務名稱 = MSOLAP$TAB2</span><span class="sxs-lookup"><span data-stu-id="66278-135">Service name = MSOLAP$TAB2</span></span>  
  
    3.  <span data-ttu-id="66278-136">虛擬帳戶 = NT Service\ MSOLAP$TAB2</span><span class="sxs-lookup"><span data-stu-id="66278-136">Virtual account = NT Service\ MSOLAP$TAB2</span></span>  
  
     <span data-ttu-id="66278-137">如您所見，先前授與 "NT Service \ MSOLAP $ 表格式" 的資料庫和檔案許可權已不再有效。</span><span class="sxs-lookup"><span data-stu-id="66278-137">As you can see, database and file permissions that were previously granted to "NT Service\ MSOLAP$TABULAR" are no longer valid.</span></span> <span data-ttu-id="66278-138">若要確保服務所執行的工作和作業如之前一樣執行，您現在需要將新的資料庫和檔案許可權授與 "NT Service \ MSOLAP $ TAB2"。</span><span class="sxs-lookup"><span data-stu-id="66278-138">To ensure that tasks and operations performed by the service run as before, you would now need to grant new database and file permissions to "NT Service\ MSOLAP$TAB2".</span></span>  
  
  
