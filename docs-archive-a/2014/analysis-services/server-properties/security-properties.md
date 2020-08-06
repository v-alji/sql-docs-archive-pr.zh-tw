---
title: 安全性屬性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- security [Analysis Services], properties
- SecurityPackageList property
- BuiltinAdminsAreServerAdmins property
- DisableClientImpersonation property
- ErrorMessageMode property
- RequiredProtectionLevel property
- ServiceAccountIsServerAdmin property
- RequireClientAuthentication property
ms.assetid: 2fc7fe10-0cbb-49ac-aa8c-8ec3f7a7705f
author: minewiskan
ms.author: owend
ms.openlocfilehash: 20133554835803908a340c5369eb66e86b119d72
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595305"
---
# <a name="security-properties"></a><span data-ttu-id="2e58b-102">安全性屬性</span><span class="sxs-lookup"><span data-stu-id="2e58b-102">Security Properties</span></span>
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="2e58b-103">支援下表列出的安全性伺服器屬性。</span><span class="sxs-lookup"><span data-stu-id="2e58b-103">supports the security server properties listed in the following table.</span></span> <span data-ttu-id="2e58b-104">如需有關其他伺服器屬性及如何設定伺服器屬性的詳細資訊，請參閱＜ [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md)＞。</span><span class="sxs-lookup"><span data-stu-id="2e58b-104">For more information about additional server properties and how to set them, see [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md).</span></span>  
  
 <span data-ttu-id="2e58b-105">**適用於：** 多維度與表格式伺服器模式</span><span class="sxs-lookup"><span data-stu-id="2e58b-105">**Applies to:** Multidimensional and Tabular server mode</span></span>  
  
## <a name="properties"></a><span data-ttu-id="2e58b-106">屬性</span><span class="sxs-lookup"><span data-stu-id="2e58b-106">Properties</span></span>  
 `RequireClientAuthentication`  
 <span data-ttu-id="2e58b-107">指出是否需要用戶端驗證的布林屬性。</span><span class="sxs-lookup"><span data-stu-id="2e58b-107">A Boolean property that indicates whether client authentication is required.</span></span>  
  
 <span data-ttu-id="2e58b-108">此屬性的預設值為 True，表示用戶端驗證是必要的。</span><span class="sxs-lookup"><span data-stu-id="2e58b-108">The default value for this property is True, which indicates that client authentication is required.</span></span>  
  
 `SecurityPackageList`  
 <span data-ttu-id="2e58b-109">此為字串屬性，包含 SSPI 封裝的逗號分隔清單，供伺服器的用戶端驗證使用。</span><span class="sxs-lookup"><span data-stu-id="2e58b-109">A string property that contains a comma-separated list of SSPI packages used by server for client authentication.</span></span>  
  
 `DisableClientImpersonation`  
 <span data-ttu-id="2e58b-110">此為布林值屬性，指出用戶端模擬 (例如，從預存程序) 是否停用。</span><span class="sxs-lookup"><span data-stu-id="2e58b-110">A Boolean property that indicates whether client impersonation (for example, from stored procedures) is disabled.</span></span>  
  
 <span data-ttu-id="2e58b-111">此屬性的預設值為 False，表示用戶端模擬是啟用的。</span><span class="sxs-lookup"><span data-stu-id="2e58b-111">The default value for this property is False, which indicates that client impersonation is enabled.</span></span>  
  
 `BuiltinAdminsAreServerAdmins`  
 <span data-ttu-id="2e58b-112">此為布林值屬性，指出本機電腦管理員群組的成員是否為 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 管理員。</span><span class="sxs-lookup"><span data-stu-id="2e58b-112">A Boolean property that indicates whether members of the local machine administrators group are [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] administrators.</span></span>  
  
 `ServiceAccountIsServerAdmin`  
 <span data-ttu-id="2e58b-113">指出服務帳戶是否為伺服器管理員的布林屬性。</span><span class="sxs-lookup"><span data-stu-id="2e58b-113">A Boolean property that indicates whether the service account is a server administrator.</span></span>  
  
 <span data-ttu-id="2e58b-114">此屬性的預設值為 True，表示服務帳戶為伺服器管理員。</span><span class="sxs-lookup"><span data-stu-id="2e58b-114">The default value for this property is True, which indicates that the service account is a server administrator.</span></span>  
  
 `ErrorMessageMode`  
 <span data-ttu-id="2e58b-115">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="2e58b-115">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `DataProtection\ RequiredProtectionLevel`  
 <span data-ttu-id="2e58b-116">此為帶正負號的 32 位元整數屬性，其中定義所有必要的用戶端要求保護層級。</span><span class="sxs-lookup"><span data-stu-id="2e58b-116">A signed 32-bit integer property that defines the required protection level for all client requests.</span></span> <span data-ttu-id="2e58b-117">此屬性的值為下表列出的值之一。</span><span class="sxs-lookup"><span data-stu-id="2e58b-117">This property has one of the values listed in the following table.</span></span>  
  
|<span data-ttu-id="2e58b-118">值</span><span class="sxs-lookup"><span data-stu-id="2e58b-118">Value</span></span>|<span data-ttu-id="2e58b-119">描述</span><span class="sxs-lookup"><span data-stu-id="2e58b-119">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2e58b-120">*0*</span><span class="sxs-lookup"><span data-stu-id="2e58b-120">*0*</span></span>|<span data-ttu-id="2e58b-121">無，允許純文字。</span><span class="sxs-lookup"><span data-stu-id="2e58b-121">None, clear text allowed.</span></span>|  
|<span data-ttu-id="2e58b-122">*1*</span><span class="sxs-lookup"><span data-stu-id="2e58b-122">*1*</span></span>|<span data-ttu-id="2e58b-123">(預設值) 需要有加密，不能以純文字記錄。</span><span class="sxs-lookup"><span data-stu-id="2e58b-123">(Default) Encryption required, no clear-text logging.</span></span>|  
|<span data-ttu-id="2e58b-124">*2*</span><span class="sxs-lookup"><span data-stu-id="2e58b-124">*2*</span></span>|<span data-ttu-id="2e58b-125">允許純文字要求，但僅限於有簽章時 (保護弱於加密)。</span><span class="sxs-lookup"><span data-stu-id="2e58b-125">Clear-text requests allowed but only with signatures (weaker protection than encryption).</span></span>|  
  
 `AdministrativeDataProtection\ RequiredProtectionLevel`  
 <span data-ttu-id="2e58b-126">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="2e58b-126">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e58b-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2e58b-127">See Also</span></span>  
 <span data-ttu-id="2e58b-128">[在 Analysis Services 中設定伺服器屬性](server-properties-in-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="2e58b-128">[Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md) </span></span>  
 [<span data-ttu-id="2e58b-129">判斷 Analysis Services 執行個體的伺服器模式</span><span class="sxs-lookup"><span data-stu-id="2e58b-129">Determine the Server Mode of an Analysis Services Instance</span></span>](../instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
