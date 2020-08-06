---
title: 一般頁面 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Business_Intelligence_Designers.Data_Transformation_Designers.General
ms.assetid: d695690a-923b-4036-945e-7621e8651deb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 59073ac29f95f1e64bd0a9382366e9539ce1408a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592136"
---
# <a name="general-page"></a><span data-ttu-id="e90e4-102">一般頁面</span><span class="sxs-lookup"><span data-stu-id="e90e4-102">General Page</span></span>
  <span data-ttu-id="e90e4-103">在 [選項] 對話方塊上使用 [Integration Services 設計師] 頁面上的 [一般] 頁面，指定用來載入、顯示及升級封裝的選項。</span><span class="sxs-lookup"><span data-stu-id="e90e4-103">Use the **General** page of the **Integration Services Designers** page in the **Options** dialog box to specify the options for loading, displaying, and upgrading packages.</span></span>  
  
 <span data-ttu-id="e90e4-104">若要開啟 [一般]  頁面，請在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中的 [工具]  功能表上按一下 [選項]  ，然後展開 [商業智慧設計師]  ，再選取 [Integration Services 設計師]  。</span><span class="sxs-lookup"><span data-stu-id="e90e4-104">To open the **General** page, in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], on the **Tools** menu, click **Options**, expand **Business Intelligence Designers**, and select **Integration Services Designers**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="e90e4-105">選項。</span><span class="sxs-lookup"><span data-stu-id="e90e4-105">Options</span></span>  
 <span data-ttu-id="e90e4-106">**載入封裝時檢查數位簽章**</span><span class="sxs-lookup"><span data-stu-id="e90e4-106">**Check digital signature when loading a package**</span></span>  
 <span data-ttu-id="e90e4-107">選取即可讓 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 在載入封裝時檢查數位簽章。</span><span class="sxs-lookup"><span data-stu-id="e90e4-107">Select to have [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] check the digital signature when loading a package.</span></span> [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="e90e4-108">只會檢查數位簽章是否存在、是否有效，以及是否來自信任的來源。</span><span class="sxs-lookup"><span data-stu-id="e90e4-108">will only check whether the digital signature is present, is valid, and is from a trusted source.</span></span> [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="e90e4-109">將不會檢查此封裝在簽署之後是否已經變更。</span><span class="sxs-lookup"><span data-stu-id="e90e4-109">will not check whether the package has been changed since the package was signed.</span></span>  
  
 <span data-ttu-id="e90e4-110">如果您設定 **BlockedSignatureStates** 登錄值，此登錄值會覆寫 [載入封裝時檢查數位簽章]  選項。</span><span class="sxs-lookup"><span data-stu-id="e90e4-110">If you set the **BlockedSignatureStates** registry value, this registry value overrides the **Check digital signature when loading a package** option.</span></span> <span data-ttu-id="e90e4-111">如需詳細資訊，請參閱 [透過設定登錄值實作簽署原則](implement-a-signing-policy-by-setting-a-registry-value.md)。</span><span class="sxs-lookup"><span data-stu-id="e90e4-111">For more information, see [Implement a Signing Policy by Setting a Registry Value](implement-a-signing-policy-by-setting-a-registry-value.md).</span></span>  
  
 <span data-ttu-id="e90e4-112">如需詳細資訊，請參閱 [使用數位簽章來識別封裝的來源](security/identify-the-source-of-packages-with-digital-signatures.md)。</span><span class="sxs-lookup"><span data-stu-id="e90e4-112">For more information about digital certificates and packages, see [Identify the Source of Packages with Digital Signatures](security/identify-the-source-of-packages-with-digital-signatures.md).</span></span>  
  
 <span data-ttu-id="e90e4-113">**如果封裝沒有簽章則顯示警告**</span><span class="sxs-lookup"><span data-stu-id="e90e4-113">**Show warning if package is unsigned**</span></span>  
 <span data-ttu-id="e90e4-114">選取此選項即可在載入未簽署的封裝時顯示警告。</span><span class="sxs-lookup"><span data-stu-id="e90e4-114">Select to display a warning when loading a package that is not signed.</span></span>  
  
 <span data-ttu-id="e90e4-115">**顯示優先順序約束條件標籤**</span><span class="sxs-lookup"><span data-stu-id="e90e4-115">**Show precedence constraint labels**</span></span>  
 <span data-ttu-id="e90e4-116">選取在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中檢視封裝時，要在優先順序條件約束上顯示哪一個標籤 (成功、失敗或完成)。</span><span class="sxs-lookup"><span data-stu-id="e90e4-116">Select which label-Success, Failure, or Completion-to display on precedence constraints when viewing packages in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="e90e4-117">**指令碼語言**</span><span class="sxs-lookup"><span data-stu-id="e90e4-117">**Scripting language**</span></span>  
 <span data-ttu-id="e90e4-118">選取新指令碼工作和指令碼元件的預設指令碼語言。</span><span class="sxs-lookup"><span data-stu-id="e90e4-118">Select the default scripting language for new Script tasks and Script components.</span></span>  
  
 <span data-ttu-id="e90e4-119">**更新連接字串以使用新的提供者名稱**</span><span class="sxs-lookup"><span data-stu-id="e90e4-119">**Update connection strings to use new provider names**</span></span>  
 <span data-ttu-id="e90e4-120">在開啟或升級 [!INCLUDE[ssISversion2005](../includes/ssisversion2005-md.md)] 封裝時，請為目前版本的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]更新連接字串，以使用下列提供者的名稱：</span><span class="sxs-lookup"><span data-stu-id="e90e4-120">When opening or upgrading [!INCLUDE[ssISversion2005](../includes/ssisversion2005-md.md)] packages, update connection strings to use the names for the following providers, for the current release of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]:</span></span>  
  
-   [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] <span data-ttu-id="e90e4-121">OLE DB 提供者</span><span class="sxs-lookup"><span data-stu-id="e90e4-121">OLE DB provider</span></span>  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="e90e4-122">Native Client{2}</span><span class="sxs-lookup"><span data-stu-id="e90e4-122">Native Client</span></span>  
  
 <span data-ttu-id="e90e4-123">[ [!INCLUDE[ssIS](../includes/ssis-md.md)] 封裝升級精靈] 只會更新儲存在連線管理員中的連接字串。</span><span class="sxs-lookup"><span data-stu-id="e90e4-123">The [!INCLUDE[ssIS](../includes/ssis-md.md)] Package Upgrade Wizard updates only connection strings that are stored in connection managers.</span></span> <span data-ttu-id="e90e4-124">此精靈不會更新使用 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 運算式語言或使用指令碼工作中之程式碼以動態方式建構的連接字串。</span><span class="sxs-lookup"><span data-stu-id="e90e4-124">The wizard does not update connection strings that are constructed dynamically by using the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] expression language, or by using code in a Script task.</span></span>  
  
 <span data-ttu-id="e90e4-125">**建立新的封裝識別碼**</span><span class="sxs-lookup"><span data-stu-id="e90e4-125">**Create new package ID**</span></span>  
 <span data-ttu-id="e90e4-126">在升級 [!INCLUDE[ssISversion2005](../includes/ssisversion2005-md.md)] 封裝時，針對升級版本的封裝建立新的封裝識別碼。</span><span class="sxs-lookup"><span data-stu-id="e90e4-126">When upgrading [!INCLUDE[ssISversion2005](../includes/ssisversion2005-md.md)] packages, create new package IDs for the upgraded versions of the packages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e90e4-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e90e4-127">See Also</span></span>  
 <span data-ttu-id="e90e4-128">[安全性概觀 (Integration Services)](security/security-overview-integration-services.md) </span><span class="sxs-lookup"><span data-stu-id="e90e4-128">[Security Overview &#40;Integration Services&#41;](security/security-overview-integration-services.md) </span></span>  
 [<span data-ttu-id="e90e4-129">使用指令碼擴充套件</span><span class="sxs-lookup"><span data-stu-id="e90e4-129">Extending Packages with Scripting</span></span>](extending-packages-scripting/extending-packages-with-scripting.md)  
  
  
