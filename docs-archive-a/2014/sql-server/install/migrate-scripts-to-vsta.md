---
title: 將腳本遷移至 VSTA |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- SSIS Script task, converting scripts
- Script component [Integration Services], converting scripts
- Script task [Integration Services], converting scripts
- SSIS Script component, converting scripts
ms.assetid: d685098b-86a1-46bf-939a-63d56951e009
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: afbc19c35f99a5abc5a6ebd92024e42baa6a9237
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708061"
---
# <a name="migrate-scripts-to-vsta"></a><span data-ttu-id="cf1e2-102">將指令碼移轉到 VSTA</span><span class="sxs-lookup"><span data-stu-id="cf1e2-102">Migrate Scripts to VSTA</span></span>
  <span data-ttu-id="cf1e2-103">當您將 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 封裝升級為時，會將 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 任何腳本工作或腳本元件中的腳本，遷移至 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 適用于應用程式 (VSTA) 的工具。</span><span class="sxs-lookup"><span data-stu-id="cf1e2-103">When you upgrade [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] packages to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] migrates the scripts in any Script tasks or Script components to [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA).</span></span> <span data-ttu-id="cf1e2-104">VSTA 是 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 所使用的指令碼環境。</span><span class="sxs-lookup"><span data-stu-id="cf1e2-104">VSTA is the scripting environment that [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] uses.</span></span> <span data-ttu-id="cf1e2-105">在中 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ，的腳本環境 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 適用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 于 (VSA) 的應用程式。</span><span class="sxs-lookup"><span data-stu-id="cf1e2-105">In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], the scripting environment for [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] is [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] for Applications (VSA).</span></span>  
  
 <span data-ttu-id="cf1e2-106">如果指令碼工作或指令碼元件中的指令碼會參考介面，您可能必須在升級封裝以前修改這些參考。</span><span class="sxs-lookup"><span data-stu-id="cf1e2-106">If the scripts in either the Script tasks or Script components reference interfaces, you might have to modify those references before you upgrade the package.</span></span> <span data-ttu-id="cf1e2-107">否則，此封裝將無法升級或指令碼將無法驗證 (視您所使用的升級方法而定)。</span><span class="sxs-lookup"><span data-stu-id="cf1e2-107">Otherwise, the package will not be upgraded or the scripts will not be validated, depending on the upgrade method that you use.</span></span> <span data-ttu-id="cf1e2-108">若要修改這些參考，請以對應的 IDTS*xxx*100 介面的參考取代 IDTS*xxx*90 介面的參考。</span><span class="sxs-lookup"><span data-stu-id="cf1e2-108">To modify these references, replace references to IDTS*xxx*90 interfaces with references to the corresponding IDTS*xxx*100 interfaces.</span></span>  
  
 <span data-ttu-id="cf1e2-109">如需如何遷移腳本和升級封裝的詳細資訊，請參閱[升級 Integration Services 套件](../../integration-services/install-windows/upgrade-integration-services-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="cf1e2-109">For more information about how to migrate scripts and upgrade packages, see [Upgrade Integration Services Packages](../../integration-services/install-windows/upgrade-integration-services-packages.md).</span></span>  
  
## <a name="understanding-migration-failures"></a><span data-ttu-id="cf1e2-110">了解移轉失敗</span><span class="sxs-lookup"><span data-stu-id="cf1e2-110">Understanding Migration Failures</span></span>  
 <span data-ttu-id="cf1e2-111">當您移轉指令碼時，移轉可能會因為下列其中一個原因而失敗：</span><span class="sxs-lookup"><span data-stu-id="cf1e2-111">When you migrate the scripts, the migration can fail because of one of the following reasons:</span></span>  
  
-   <span data-ttu-id="cf1e2-112">VSA 指令碼的進入點已重新命名。</span><span class="sxs-lookup"><span data-stu-id="cf1e2-112">The entry point for the VSA script was renamed.</span></span>  
  
     <span data-ttu-id="cf1e2-113">進入點將 VSTA 專案中 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 執行階段所呼叫的 `ScriptMain` 類別方法指定為指令碼工作程式碼的進入點。</span><span class="sxs-lookup"><span data-stu-id="cf1e2-113">The entry point specifies the method in the `ScriptMain` class in the VSTA project that the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] runtime calls as the entry point into the Script task code.</span></span> <span data-ttu-id="cf1e2-114">`ScriptMain` 類別是指令碼範本所產生的預設類別。</span><span class="sxs-lookup"><span data-stu-id="cf1e2-114">The `ScriptMain` class is the default class that the script templates generate.</span></span>  
  
-   <span data-ttu-id="cf1e2-115">VSA 指令碼中沒有任何進入點，或者含有多個進入點。</span><span class="sxs-lookup"><span data-stu-id="cf1e2-115">There is no entry point or there are multiple entry points in the VSA script.</span></span>  
  
-   <span data-ttu-id="cf1e2-116">無法加入組件參考。</span><span class="sxs-lookup"><span data-stu-id="cf1e2-116">Assembly references could not be added.</span></span>  
  
-   <span data-ttu-id="cf1e2-117">`ScriptMain` 類別已修改為除了 `ScriptObjectModelSSIS` 類別之外，也會繼承其他類別。</span><span class="sxs-lookup"><span data-stu-id="cf1e2-117">The `ScriptMain` class was modified to inherit from other classes in addition to the `ScriptObjectModelSSIS` class.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)]<span data-ttu-id="cf1e2-118">不 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 支援多重繼承。</span><span class="sxs-lookup"><span data-stu-id="cf1e2-118">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] does not support multiple inheritance.</span></span>  
  
 <span data-ttu-id="cf1e2-119">您無法將使用的 VSA 腳本轉換成 [!INCLUDE[vbprvblong](../../includes/vbprvblong-md.md)] 使用的 VSTA 腳本 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csharp_orcas_long](../../includes/csharp-orcas-long-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="cf1e2-119">You cannot convert a VSA script that uses [!INCLUDE[vbprvblong](../../includes/vbprvblong-md.md)] to a VSTA script that uses [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csharp_orcas_long](../../includes/csharp-orcas-long-md.md)].</span></span> <span data-ttu-id="cf1e2-120">不過，您可以建立使用的新 VSTA 腳本 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csharp_orcas_long](../../includes/csharp-orcas-long-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="cf1e2-120">However, you can create a new VSTA script that uses [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csharp_orcas_long](../../includes/csharp-orcas-long-md.md)].</span></span> <span data-ttu-id="cf1e2-121">如需詳細資訊，請參閱[指令碼工作的程式碼撰寫和偵錯](../../integration-services/control-flow/script-task.md)和[指令碼元件的程式碼撰寫和偵錯](../../integration-services/data-flow/transformations/script-component.md)。</span><span class="sxs-lookup"><span data-stu-id="cf1e2-121">For more information, see [Coding and Debugging the Script Task](../../integration-services/control-flow/script-task.md) and [Coding and Debugging the Script Component](../../integration-services/data-flow/transformations/script-component.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf1e2-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cf1e2-122">See Also</span></span>  
 [<span data-ttu-id="cf1e2-123">使用指令碼擴充套件</span><span class="sxs-lookup"><span data-stu-id="cf1e2-123">Extending Packages with Scripting</span></span>](../../relational-databases/server-management-objects-smo/tasks/scripting.md)  
  
  
