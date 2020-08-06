---
title: 設定或變更封裝的保護等級 |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- passwords [Integration Services]
- packages [Integration Services],security
- security [Integration Services],protection levels
- protection level for packages [Integration Services]
ms.assetid: 904a5580-82ba-4a26-b0c5-d1c989975f61
author: chugugrace
ms.author: chugu
ms.openlocfilehash: da8e63028498097b4321e4ef1383fbc8aa5845b6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708486"
---
# <a name="set-or-change-the-protection-level-of-packages"></a><span data-ttu-id="9178e-102">設定或變更封裝的保護等級</span><span class="sxs-lookup"><span data-stu-id="9178e-102">Set or Change the Protection Level of Packages</span></span>
  <span data-ttu-id="9178e-103">若要控制封裝內容以及其中包含之機密值 (例如密碼) 的存取權，請設定 `ProtectionLevel` 屬性的值</span><span class="sxs-lookup"><span data-stu-id="9178e-103">To control access to the contents of packages and to the sensitive values that they contain, such as passwords, set the value of the `ProtectionLevel` property.</span></span> <span data-ttu-id="9178e-104">包含在專案中的封裝需要有和專案相同的保護層級，才能建立專案。</span><span class="sxs-lookup"><span data-stu-id="9178e-104">The packages contained in a project need to have the same protection level as the project, to build the project.</span></span> <span data-ttu-id="9178e-105">如果您變更專案上的 `ProtectionLevel` 屬性設定，就需要手動更新封裝的屬性設定。</span><span class="sxs-lookup"><span data-stu-id="9178e-105">If you change the `ProtectionLevel` property setting on the project, you need to manually update the property setting for the packages.</span></span>  
  
 <span data-ttu-id="9178e-106">如需如何在 `ProtectionLevel` 封裝生命週期的不同階段判斷封裝適用之設定的詳細資訊，請參閱封裝[中的敏感性資料存取控制](security/access-control-for-sensitive-data-in-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="9178e-106">For information about how to determine the `ProtectionLevel` settings that are appropriate for your packages at different stages in the package life cycle, see [Access Control for Sensitive Data in Packages](security/access-control-for-sensitive-data-in-packages.md).</span></span> <span data-ttu-id="9178e-107">如需 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 安全性功能的概觀，請參閱[安全性概觀 &#40;Integration Services&#41;](security/security-overview-integration-services.md)。</span><span class="sxs-lookup"><span data-stu-id="9178e-107">For an overview of security features in [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], see [Security Overview &#40;Integration Services&#41;](security/security-overview-integration-services.md).</span></span>  
  
 <span data-ttu-id="9178e-108">本主題中的程序說明如何使用 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 或 dtutil 命令提示字元公用程式來變更 `ProtectionLevel` 屬性。</span><span class="sxs-lookup"><span data-stu-id="9178e-108">The procedures in this topic describe how to use either [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] or the dtutil command prompt utility to change the `ProtectionLevel` property.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9178e-109">除了本主題中的程序之外，您通常可以在匯入或匯出封裝時，設定或變更封裝的 `ProtectionLevel` 屬性。</span><span class="sxs-lookup"><span data-stu-id="9178e-109">In addition to the procedures in this topic, you can typically set or change the `ProtectionLevel` property of a package when you import or export the package.</span></span> <span data-ttu-id="9178e-110">您也可以在使用 [[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 匯入和匯出精靈] 來儲存封裝時，變更封裝的 `ProtectionLevel` 屬性。</span><span class="sxs-lookup"><span data-stu-id="9178e-110">You can also change the `ProtectionLevel` property of a package when you use the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Import and Export Wizard to save a package.</span></span>  
  
### <a name="to-set-or-change-the-protection-level-of-a-package-in-sql-server-data-tools"></a><span data-ttu-id="9178e-111">若要在 SQL Server 資料工具中設定或變更封裝的保護等級</span><span class="sxs-lookup"><span data-stu-id="9178e-111">To set or change the protection level of a package in SQL Server Data Tools</span></span>  
  
1.  <span data-ttu-id="9178e-112">`ProtectionLevel`在[設定封裝的保護等級](security/access-control-for-sensitive-data-in-packages.md)主題中，檢查屬性的可用值，並決定您的封裝的適當值。</span><span class="sxs-lookup"><span data-stu-id="9178e-112">Review the available values for the `ProtectionLevel` property in the topic, [Setting the Protection Level of Packages](security/access-control-for-sensitive-data-in-packages.md), and determine the appropriate value for your package.</span></span>  
  
2.  <span data-ttu-id="9178e-113">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，開啟包含封裝的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="9178e-113">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package.</span></span>  
  
3.  <span data-ttu-id="9178e-114">在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 設計器中，開啟封裝。</span><span class="sxs-lookup"><span data-stu-id="9178e-114">Open the package in the [!INCLUDE[ssIS](../includes/ssis-md.md)] designer.</span></span>  
  
4.  <span data-ttu-id="9178e-115">如果 [屬性] 視窗並未顯示封裝屬性，請按一下設計介面。</span><span class="sxs-lookup"><span data-stu-id="9178e-115">If the Properties window does not show the properties of the package, click the design surface.</span></span>  
  
5.  <span data-ttu-id="9178e-116">在 [屬性視窗的 [**安全**] 群組中，為屬性選取適當的值 `ProtectionLevel` 。</span><span class="sxs-lookup"><span data-stu-id="9178e-116">In the Properties window, in the **Security** group, select the appropriate value for the `ProtectionLevel` property.</span></span>  
  
     <span data-ttu-id="9178e-117">如果您選取了需要密碼的保護等級，請輸入密碼作為 **PackagePassword** 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="9178e-117">If you select a protection level that requires a password, enter the password as the value of the **PackagePassword** property.</span></span>  
  
6.  <span data-ttu-id="9178e-118">在 [檔案]\*\*\*\* 功能表上，選取 [儲存選取項目]\*\*\*\* 以儲存修改過的封裝。</span><span class="sxs-lookup"><span data-stu-id="9178e-118">On the **File** menu, select **Save Selected Items** to save the modified package.</span></span>  
  
### <a name="to-set-or-change-the-protection-level-of-packages-at-the-command-prompt"></a><span data-ttu-id="9178e-119">在命令提示字元設定或變更封裝的保護等級</span><span class="sxs-lookup"><span data-stu-id="9178e-119">To set or change the protection level of packages at the command prompt</span></span>  
  
1.  <span data-ttu-id="9178e-120">`ProtectionLevel`在[設定封裝的保護等級](security/access-control-for-sensitive-data-in-packages.md)主題中，檢查屬性的可用值，並決定您的封裝的適當值。</span><span class="sxs-lookup"><span data-stu-id="9178e-120">Review the available values for the `ProtectionLevel` property in the topic, [Setting the Protection Level of Packages](security/access-control-for-sensitive-data-in-packages.md), and determine the appropriate value for your package.</span></span>  
  
2.  <span data-ttu-id="9178e-121">`Encrypt`在[Dtutil 公用程式](dtutil-utility.md)主題中，檢查選項的對應，並判斷要當做所選屬性值使用的適當整數 `ProtectionLevel` 。</span><span class="sxs-lookup"><span data-stu-id="9178e-121">Review the mappings for the `Encrypt` option in the topic, [dtutil Utility](dtutil-utility.md), and determine the appropriate integer to use as the value of the selected `ProtectionLevel` property.</span></span>  
  
3.  <span data-ttu-id="9178e-122">開啟命令提示字元視窗。</span><span class="sxs-lookup"><span data-stu-id="9178e-122">Open a Command Prompt window.</span></span>  
  
4.  <span data-ttu-id="9178e-123">在命令提示字元，導覽至您要設定其 `ProtectionLevel` 屬性之封裝的所在資料夾。</span><span class="sxs-lookup"><span data-stu-id="9178e-123">At the command prompt, navigate to the folder that contains the package or packages for which you want to set the `ProtectionLevel` property.</span></span>  
  
     <span data-ttu-id="9178e-124">下列步驟所示的語法範例假設此資料夾為目前的資料夾。</span><span class="sxs-lookup"><span data-stu-id="9178e-124">The syntax examples shown in the following step assume that this folder is the current folder.</span></span>  
  
5.  <span data-ttu-id="9178e-125">使用類似於下列其中一個範例的命令，設定或變更封裝的保護等級：</span><span class="sxs-lookup"><span data-stu-id="9178e-125">Set or change the protection level of the package or packages by using a command similar to the one of the following examples:</span></span>  
  
    -   <span data-ttu-id="9178e-126">下列命令會將檔案系統中個別封裝的 `ProtectionLevel` 屬性設為層級 2「機密資料以密碼加密」，並且將密碼設為 "strongpassword"：</span><span class="sxs-lookup"><span data-stu-id="9178e-126">The following command sets the `ProtectionLevel` property of an individual package in the file system to level 2, "Encrypt sensitive with password", with the password, "strongpassword":</span></span>  
  
         `dtutil.exe /file "C:\Package.dtsx" /encrypt file;"C:\Package.dtsx";2;strongpassword`  
  
    -   <span data-ttu-id="9178e-127">下列命令會將檔案系統中特定資料夾內所有封裝的 `ProtectionLevel` 屬性設為層級 2「機密資料以密碼加密」，並且將密碼設為 "strongpassword"：</span><span class="sxs-lookup"><span data-stu-id="9178e-127">The following command sets the `ProtectionLevel` property of all packages in a particular folder in the file system to level 2, "Encrypt sensitive with password", with the password, "strongpassword":</span></span>  
  
         `for %f in (*.dtsx) do dtutil.exe /file %f /encrypt file;%f;2;strongpassword`  
  
         <span data-ttu-id="9178e-128">如果您要對批次檔使用類似命令，請將檔案預留位置 "%f" 改輸入為批次檔適用的 "%%f"。</span><span class="sxs-lookup"><span data-stu-id="9178e-128">If you use a similar command in a batch file, enter the file placeholder, "%f", as "%%f" in the batch file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9178e-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9178e-129">See Also</span></span>  
 [<span data-ttu-id="9178e-130">dtutil 公用程式</span><span class="sxs-lookup"><span data-stu-id="9178e-130">dtutil Utility</span></span>](dtutil-utility.md)  
  
  
