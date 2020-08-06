---
title: 使用 Reporting Services 安全性原則檔 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- code groups [Reporting Services]
- CodeGroup elements
- configuration files [Reporting Services]
- code access security [Reporting Services], security policies
- security policies [Reporting Services]
- security configuration files [Reporting Services]
- named permission sets [Reporting Services]
ms.assetid: 2280fff6-3de7-44b1-87da-5db0ec975928
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 15c5422741137505bc29a2de861fca1420e455d8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606639"
---
# <a name="using-reporting-services-security-policy-files"></a><span data-ttu-id="fc17b-102">使用 Reporting Services 安全性原則檔</span><span class="sxs-lookup"><span data-stu-id="fc17b-102">Using Reporting Services Security Policy Files</span></span>
  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="fc17b-103">會將元件安全性原則資訊儲存在安裝過程中複製到檔案系統的三個組態檔內。</span><span class="sxs-lookup"><span data-stu-id="fc17b-103">stores component security policy information in three configuration files that are copied to the file system during setup.</span></span> <span data-ttu-id="fc17b-104">這些組態檔可能會包含 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 中程式碼組件之內部使用和使用者定義安全性原則的組合。</span><span class="sxs-lookup"><span data-stu-id="fc17b-104">These configuration files can contain a combination of internal-use and user-defined security policies for code assemblies in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="fc17b-105">這三個組態檔會對應至 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 中的三個安全性實體元件：報表伺服器和 Windows 服務、報表管理員 Web 應用程式，以及報表設計師預覽視窗。</span><span class="sxs-lookup"><span data-stu-id="fc17b-105">The three configuration files correspond to three securable components in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]: The report server and Windows service, the Report Manager Web application, and the Report Designer preview window.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fc17b-106">報表設計師有兩個預覽模式：當在 **DebugLocal** 模式中啟動報表專案時，會啟動預覽索引標籤與快顯預覽視窗。</span><span class="sxs-lookup"><span data-stu-id="fc17b-106">There are two preview modes for Report Designer: the preview tab and the pop-up preview window that is launched when your Report Project is started in **DebugLocal** mode.</span></span> <span data-ttu-id="fc17b-107">[預覽]  索引標籤並非安全性實體元件，而且不會套用安全性原則設定。</span><span class="sxs-lookup"><span data-stu-id="fc17b-107">The **Preview** tab is not a securable component and does not apply security policy settings.</span></span> <span data-ttu-id="fc17b-108">預覽視窗是用以模擬報表伺服器功能，因此具有原則組態檔，而且您或系統管理員必須修改該檔案，才能在報表設計師中使用自訂組件和自訂延伸模組。</span><span class="sxs-lookup"><span data-stu-id="fc17b-108">The preview window is meant to simulate the report server functionality and therefore has a policy configuration file that you or an administrator must modify to use custom assemblies and custom extensions in Report Designer.</span></span>  
  
 <span data-ttu-id="fc17b-109">這些安全性原則組態檔包含安全性類別資訊、某些預設的具名權限集合，以及 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 中組件的程式碼群組。</span><span class="sxs-lookup"><span data-stu-id="fc17b-109">The security policy configuration files contain security class information, some default named permission sets, and the code groups for assemblies in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="fc17b-110">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 的原則組態檔與 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 中決定與電腦和企業層級原則相關聯之程式碼群組階層和權限集合的 Security.config 檔很相似。</span><span class="sxs-lookup"><span data-stu-id="fc17b-110">The policy configuration files of [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] are similar to the Security.config file that determines the code group hierarchy and permission sets associated with machine and enterprise level policies in the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="fc17b-111">這個檔案的位置是 C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\CONFIG\security.config。</span><span class="sxs-lookup"><span data-stu-id="fc17b-111">The location of this file is C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\CONFIG\security.config.</span></span>  
  
## <a name="policy-files-in-reporting-services"></a><span data-ttu-id="fc17b-112">Reporting Services 中的原則檔</span><span class="sxs-lookup"><span data-stu-id="fc17b-112">Policy Files in Reporting Services</span></span>  
 <span data-ttu-id="fc17b-113">下表將列出 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 中的原則組態檔、其位置 (假設是預設安裝)，以及其個別功能。</span><span class="sxs-lookup"><span data-stu-id="fc17b-113">The following table lists the policy configuration files in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], their locations (assuming a default installation), and their respective functions.</span></span>  
  
|<span data-ttu-id="fc17b-114">檔案名稱</span><span class="sxs-lookup"><span data-stu-id="fc17b-114">File name</span></span>|<span data-ttu-id="fc17b-115">位置 (預設安裝)</span><span class="sxs-lookup"><span data-stu-id="fc17b-115">Location (default installation)</span></span>|<span data-ttu-id="fc17b-116">描述</span><span class="sxs-lookup"><span data-stu-id="fc17b-116">Description</span></span>|  
|---------------|---------------------------------------|-----------------|  
|<span data-ttu-id="fc17b-117">rssrvpolicy.config</span><span class="sxs-lookup"><span data-stu-id="fc17b-117">rssrvpolicy.config</span></span>|<span data-ttu-id="fc17b-118">C:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer</span><span class="sxs-lookup"><span data-stu-id="fc17b-118">C:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer</span></span>|<span data-ttu-id="fc17b-119">報表伺服器原則組態檔。</span><span class="sxs-lookup"><span data-stu-id="fc17b-119">The report server policy configuration file.</span></span> <span data-ttu-id="fc17b-120">一旦報表部署至報表伺服器時，這些安全性原則主要會影響報表運算式和自訂組件。</span><span class="sxs-lookup"><span data-stu-id="fc17b-120">These security policies primarily affect report expressions and custom assemblies once a report is deployed to a report server.</span></span> <span data-ttu-id="fc17b-121">這個原則檔也會影響部署至報表伺服器的自訂資料、傳遞、轉譯和安全性延伸模組。</span><span class="sxs-lookup"><span data-stu-id="fc17b-121">This policy file also affects custom data, delivery, rendering and security extensions deployed to the report server.</span></span>|  
|<span data-ttu-id="fc17b-122">rsmgrpolicy.config</span><span class="sxs-lookup"><span data-stu-id="fc17b-122">rsmgrpolicy.config</span></span>|<span data-ttu-id="fc17b-123">C:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportManager</span><span class="sxs-lookup"><span data-stu-id="fc17b-123">C:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportManager</span></span>|<span data-ttu-id="fc17b-124">報表管理員原則組態檔。</span><span class="sxs-lookup"><span data-stu-id="fc17b-124">Report Manager policy configuration file.</span></span> <span data-ttu-id="fc17b-125">這些安全性原則會影響擴充報表管理員的所有組件。例如，自訂傳遞的訂閱使用者介面延伸模組。</span><span class="sxs-lookup"><span data-stu-id="fc17b-125">These security policies affect all assemblies that extend Report Manager; for example, subscription user interface extensions for custom delivery.</span></span>|  
|<span data-ttu-id="fc17b-126">rspreviewpolicy.config</span><span class="sxs-lookup"><span data-stu-id="fc17b-126">rspreviewpolicy.config</span></span>|<span data-ttu-id="fc17b-127">C:\Program Files\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies</span><span class="sxs-lookup"><span data-stu-id="fc17b-127">C:\Program Files\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies</span></span>|<span data-ttu-id="fc17b-128">報表設計師獨立預覽原則組態檔。</span><span class="sxs-lookup"><span data-stu-id="fc17b-128">The Report Designer stand-alone preview policy configuration file.</span></span> <span data-ttu-id="fc17b-129">這些安全性原則會影響預覽和部署期間用於報表中的自訂組件和報表運算式。</span><span class="sxs-lookup"><span data-stu-id="fc17b-129">These security policies affect custom assemblies and report expressions that are used in reports during preview and development.</span></span> <span data-ttu-id="fc17b-130">這些原則也會影響部署至報表設計師的自訂延伸模組，例如資料處理延伸模組。</span><span class="sxs-lookup"><span data-stu-id="fc17b-130">These policies also affect custom extensions, such as data processing extensions, that are deployed to Report Designer.</span></span>|  
  
## <a name="modifying-configuration-files"></a><span data-ttu-id="fc17b-131">修改組態檔</span><span class="sxs-lookup"><span data-stu-id="fc17b-131">Modifying Configuration Files</span></span>  
 <span data-ttu-id="fc17b-132">組態設定會指定為 XML 元素或屬性。</span><span class="sxs-lookup"><span data-stu-id="fc17b-132">Configuration settings are specified as either XML elements or attributes.</span></span> <span data-ttu-id="fc17b-133">如果您了解 XML 和組態檔，就可以使用文字或程式碼編輯器來修改可由使用者定義的設定。</span><span class="sxs-lookup"><span data-stu-id="fc17b-133">If you understand XML and configuration files, you can use a text or code editor to modify user-definable settings.</span></span> <span data-ttu-id="fc17b-134">安全性組態檔包含與 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 中原則層級相關聯之程式碼群組階層和權限集合的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="fc17b-134">Security configuration files contain information about the code group hierarchy and permission sets associated with a policy level in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="fc17b-135">建議您先使用 .NET Framework 組態公用程式 (Mscorcfg.msc) 或程式碼存取安全性原則公用程式 (Caspol.exe) 來修改 Security.config 檔中的安全性原則，讓原則變更對應至原則檔的有效 XML 組態元素。</span><span class="sxs-lookup"><span data-stu-id="fc17b-135">It is recommended that you use the .NET Framework Configuration Utility (Mscorcfg.msc) or Code Access Security Policy Utility (Caspol.exe) to modify security policies in the Security.config file first, so that policy changes correspond to valid XML configuration elements for policy files.</span></span> <span data-ttu-id="fc17b-136">一旦您完成此步驟之後，就可以從 Security.config 剪下新的程式碼群組和權限集合並貼入您要加入程式碼權限之元件的原則檔中。</span><span class="sxs-lookup"><span data-stu-id="fc17b-136">Once you have done that, you can cut and paste the new code groups and permission sets from Security.config to the policy file for the component to which you are adding code permissions.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="fc17b-137">進行任何變更之前，您應該先備份原則組態檔。</span><span class="sxs-lookup"><span data-stu-id="fc17b-137">You should backup your policy configuration files prior to making any changes.</span></span>  
  
 <span data-ttu-id="fc17b-138">使用這種方法可達成兩項目的。</span><span class="sxs-lookup"><span data-stu-id="fc17b-138">Using this approach accomplishes two things.</span></span> <span data-ttu-id="fc17b-139">首先，它可讓您使用視覺化工具來建立 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 的程式碼群組和權限集合。</span><span class="sxs-lookup"><span data-stu-id="fc17b-139">First, it enables you to use a visual tool to build your code groups and permission sets for [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="fc17b-140">這比從頭開始撰寫 XML 組態元素更簡單。</span><span class="sxs-lookup"><span data-stu-id="fc17b-140">This is much easier than writing XML configuration elements from scratch.</span></span> <span data-ttu-id="fc17b-141">其次，它可確保您不會使用格式錯誤的 XML 元素和屬性來損毀安全性原則組態檔。</span><span class="sxs-lookup"><span data-stu-id="fc17b-141">Secondly, it ensures that you do not corrupt the security policy configuration files with malformed XML elements and attributes.</span></span> <span data-ttu-id="fc17b-142">如需有關程式碼存取安全性原則公用程式的詳細資訊，請參閱 MSDN 上的＜使用 Reporting Services 安全性原則檔＞。</span><span class="sxs-lookup"><span data-stu-id="fc17b-142">For more information about the Code Access Security Policy Utility, see Using Reporting Services Security Policy Files on MSDN.</span></span>  
  
 <span data-ttu-id="fc17b-143">修改原則組態檔之前，您應該先閱讀本節和相關主題中的所有可用資訊。</span><span class="sxs-lookup"><span data-stu-id="fc17b-143">Before modifying policy configuration files, you should read all the information available in this section and related topics.</span></span> <span data-ttu-id="fc17b-144">修改 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 的原則組態可能會對 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 元件執行外部程式碼模組的方式造成重大安全性影響。</span><span class="sxs-lookup"><span data-stu-id="fc17b-144">Modifying the policy configuration of [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] can have a significant security impact on how [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] components execute external code modules.</span></span>  
  
## <a name="placement-of-codegroup-elements-for-extensions"></a><span data-ttu-id="fc17b-145">延伸模組之 CodeGroup 元素的放置方式</span><span class="sxs-lookup"><span data-stu-id="fc17b-145">Placement of CodeGroup Elements for Extensions</span></span>  
 <span data-ttu-id="fc17b-146">CodeGroup 元素在安全性原則檔中的放置方式很重要。</span><span class="sxs-lookup"><span data-stu-id="fc17b-146">The placement of CodeGroup elements in a security policy file is important.</span></span> <span data-ttu-id="fc17b-147">針對您開發的延伸模組和自訂組件，建議您將自訂程式碼群組直接放在 URL 成員資格 "$CodeGen$/\*" 的現有項目底下，如下面所示：</span><span class="sxs-lookup"><span data-stu-id="fc17b-147">For extensions and custom assemblies that you develop, it is recommended that you place your custom code groups directly below the existing entry for the URL membership "$CodeGen$/\*", as indicated by the following:</span></span>  
  
```  
<CodeGroup  
    class="UnionCodeGroup"  
    version="1"  
    PermissionSetName="FullTrust">  
    <IMembershipCondition   
        class="UrlMembershipCondition"  
        version="1"  
        Url="$CodeGen$/*"  
    />  
</CodeGroup>  
<CodeGroup   
    class="UnionCodeGroup"  
    version="1"  
    PermissionSetName="FullTrust"  
    Name="MyCustomCodeGroup"  
    Description="Code group for my custom extension">  
        <IMembershipCondition class="UrlMembershipCondition"  
        version="1"  
        Url="C:\Program Files\Microsoft SQL Server\MSSQL\Reporting Services\ReportServer\bin\MyAssembly.dll"  
        />  
</CodeGroup>  
```  
  
 <span data-ttu-id="fc17b-148">您可以依次加入其他程式碼群組。</span><span class="sxs-lookup"><span data-stu-id="fc17b-148">Additional code groups can be added one after another.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc17b-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fc17b-149">See Also</span></span>  
 [<span data-ttu-id="fc17b-150">了解安全性原則</span><span class="sxs-lookup"><span data-stu-id="fc17b-150">Understanding Security Policies</span></span>](understanding-security-policies.md)  
  
  
