---
title: 使用數位簽章來識別套件的來源 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- signing packages [Integration Services]
- certificates [Integration Services]
- packages [Integration Services], security
- security [Integration Services], certificates
- signing policies [Integration Services]
ms.assetid: a433fbef-1853-4740-9d5e-8a32bc4ffbb2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 90c0e2e3db13ba4b228b70ccfffddbc2ff221774
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710701"
---
# <a name="identify-the-source-of-packages-with-digital-signatures"></a><span data-ttu-id="eb825-102">使用數位簽章來識別封裝的來源</span><span class="sxs-lookup"><span data-stu-id="eb825-102">Identify the Source of Packages with Digital Signatures</span></span>
  <span data-ttu-id="eb825-103">您可以使用數位憑證來簽署 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝，以便識別其來源。</span><span class="sxs-lookup"><span data-stu-id="eb825-103">An [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package can be signed with a digital certificate to identify its source.</span></span> <span data-ttu-id="eb825-104">當您已經使用數位憑證來簽署封裝之後，就可以讓 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 檢查數位簽章，然後再載入封裝。</span><span class="sxs-lookup"><span data-stu-id="eb825-104">After a package has been signed with a digital certificate, you can have [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] check the digital signature before loading the package.</span></span> <span data-ttu-id="eb825-105">若要讓 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 檢查簽章，您可以在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 或 **dtexec** 公用程式 (dtexec.exe) 中設定選項，或設定選擇性登錄值。</span><span class="sxs-lookup"><span data-stu-id="eb825-105">To have [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] check the signature, you set an option in either [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] or in the **dtexec** utility (dtexec.exe), or set an optional registry value.</span></span>  
  
## <a name="signing-a-package-with-a-digital-certificate"></a><span data-ttu-id="eb825-106">使用數位憑證來簽署封裝</span><span class="sxs-lookup"><span data-stu-id="eb825-106">Signing a Package with a Digital Certificate</span></span>  
 <span data-ttu-id="eb825-107">您必須先取得或建立數位憑證，然後才能使用該憑證來簽署封裝。</span><span class="sxs-lookup"><span data-stu-id="eb825-107">Before you can sign a package with a digital certificate, you first have to obtain or create the certificate.</span></span> <span data-ttu-id="eb825-108">當您擁有憑證之後，就可以使用這個憑證來簽署封裝。</span><span class="sxs-lookup"><span data-stu-id="eb825-108">After you have the certificate, you can then use this certificate to sign the package.</span></span> <span data-ttu-id="eb825-109">如需如何取得憑證以及使用該憑證來簽署封裝的詳細資訊，請參閱 [使用數位憑證來簽署封裝](../sign-a-package-by-using-a-digital-certificate.md)。</span><span class="sxs-lookup"><span data-stu-id="eb825-109">For more information about how to obtain a certificate and sign a package with that certificate, see [Sign a Package by Using a Digital Certificate](../sign-a-package-by-using-a-digital-certificate.md).</span></span>  
  
## <a name="setting-an-option-to-check-the-package-signature"></a><span data-ttu-id="eb825-110">設定檢查封裝簽章的選項</span><span class="sxs-lookup"><span data-stu-id="eb825-110">Setting an Option to Check the Package Signature</span></span>  
 <span data-ttu-id="eb825-111">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 和 **dtexec** 公用程式都具有一個選項，可設定 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 來檢查已簽署封裝的數位簽章。</span><span class="sxs-lookup"><span data-stu-id="eb825-111">Both [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] and the **dtexec** utility have an option that configures [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] to check the digital signature of a signed package.</span></span> <span data-ttu-id="eb825-112">您應該使用 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 或 **dtexec** 公用程式，取決於您想要檢查所有封裝或只檢查特定封裝：</span><span class="sxs-lookup"><span data-stu-id="eb825-112">Whether you use [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] or the **dtexec** utility depends on whether you want to check all packages or just specific ones:</span></span>  
  
-   <span data-ttu-id="eb825-113">若要在設計階段載入封裝之前檢查所有封裝的數位簽章，請在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 中設定 [載入封裝時檢查數位簽章]  選項。</span><span class="sxs-lookup"><span data-stu-id="eb825-113">To check the digital signature of all packages before loading the packages at design time, set the **Check digital signature when loading a package** option in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="eb825-114">這個選項是 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中所有封裝的全域設定。</span><span class="sxs-lookup"><span data-stu-id="eb825-114">This option is a global setting for all packages in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="eb825-115">如需相關資訊，請參閱 [General Page](../general-page-of-integration-services-designers-options.md)。</span><span class="sxs-lookup"><span data-stu-id="eb825-115">For more information, see [General Page](../general-page-of-integration-services-designers-options.md).</span></span>  
  
-   <span data-ttu-id="eb825-116">若要檢查個別封裝的數位簽章，請在 `/VerifyS[igned]` 使用**dtexec**公用程式來執行封裝時，指定選項。</span><span class="sxs-lookup"><span data-stu-id="eb825-116">To check the digital signature of an individual package, specify the `/VerifyS[igned]` option when you use the **dtexec** utility to run the package.</span></span> <span data-ttu-id="eb825-117">如需詳細資訊，請參閱 [dtexec Utility](../packages/dtexec-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="eb825-117">For more information, see [dtexec Utility](../packages/dtexec-utility.md).</span></span>  
  
## <a name="setting-a-registry-value-to-check-the-package-signature"></a><span data-ttu-id="eb825-118">設定檢查封裝簽章的登錄值</span><span class="sxs-lookup"><span data-stu-id="eb825-118">Setting a Registry Value to Check the Package Signature</span></span>  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="eb825-119">也支援選擇性登錄值 **BlockedSignatureStates**，可讓您用來管理載入已簽署和未簽署封裝的組織原則。</span><span class="sxs-lookup"><span data-stu-id="eb825-119">also supports an optional registry value, **BlockedSignatureStates**, that you can use to manage an organization's policy for loading signed and unsigned packages.</span></span> <span data-ttu-id="eb825-120">如果封裝未經簽署或是具有無效或不受信任的簽章，此登錄值可以防止載入封裝。</span><span class="sxs-lookup"><span data-stu-id="eb825-120">The registry value can prevent packages from loading if the packages are unsigned, or have invalid or untrusted signatures.</span></span> <span data-ttu-id="eb825-121">如需如何設定此登錄值的詳細資訊，請參閱 [透過設定登錄值實作簽署原則](../implement-a-signing-policy-by-setting-a-registry-value.md)。</span><span class="sxs-lookup"><span data-stu-id="eb825-121">For more information about how to set this registry value, see [Implement a Signing Policy by Setting a Registry Value](../implement-a-signing-policy-by-setting-a-registry-value.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="eb825-122">選擇性的 **BlockedSignatureStates** 登錄值所指定的設定，可以比 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 中所設定或 **dtexec** 命令列上所設定的數位簽章選項更具限制性。</span><span class="sxs-lookup"><span data-stu-id="eb825-122">The optional **BlockedSignatureStates** registry value can specify a setting that is more restrictive than the digital signature option set in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] or at the **dtexec** command line.</span></span> <span data-ttu-id="eb825-123">在此情況下，更具限制性的登錄設定會覆寫其他設定。</span><span class="sxs-lookup"><span data-stu-id="eb825-123">In this situation, the more restrictive registry setting overrides the other settings.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb825-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eb825-124">See Also</span></span>  
 <span data-ttu-id="eb825-125">[Integration Services &#40;SSIS&#41; 封裝](../integration-services-ssis-packages.md) </span><span class="sxs-lookup"><span data-stu-id="eb825-125">[Integration Services &#40;SSIS&#41; Packages](../integration-services-ssis-packages.md) </span></span>  
 [<span data-ttu-id="eb825-126">安全性概觀 (Integration Services)</span><span class="sxs-lookup"><span data-stu-id="eb825-126">Security Overview &#40;Integration Services&#41;</span></span>](security-overview-integration-services.md)  
  
  
