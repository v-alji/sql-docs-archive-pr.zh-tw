---
title: Reporting Services 中的程式碼存取安全性 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- code groups [Reporting Services]
- code access security [Reporting Services]
- permission sets [Reporting Services]
- evidence [Reporting Services]
- code access security [Reporting Services], about code access security
- named permission sets [Reporting Services]
ms.assetid: 97480368-1fc3-4c32-b1b0-63edfb54e472
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ebe023b13a003895845bbb119f0bc93a0d01203a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607271"
---
# <a name="code-access-security-in-reporting-services"></a><span data-ttu-id="316c1-102">Reporting Services 中的程式碼存取安全性</span><span class="sxs-lookup"><span data-stu-id="316c1-102">Code Access Security in Reporting Services</span></span>
  <span data-ttu-id="316c1-103">程式碼存取安全性是以下列核心概念為主：辨識項、程式碼群組與具名使用權限集合。</span><span class="sxs-lookup"><span data-stu-id="316c1-103">Code access security centers on these core concepts: evidence, code groups, and named permission sets.</span></span> <span data-ttu-id="316c1-104">在 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 中，報表管理員、報表設計師和報表伺服器元件都各自具有一個原則檔，其中針對自訂組件以及資料、傳遞、轉譯和安全性延伸模組設定了程式碼存取安全性。</span><span class="sxs-lookup"><span data-stu-id="316c1-104">In [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], the Report Manager, Report Designer, and Report Server components each have a policy file that configures code access security for custom assemblies as well as data, delivery, rendering, and security extensions.</span></span> <span data-ttu-id="316c1-105">下列各節將提供程式碼存取安全性的概觀。</span><span class="sxs-lookup"><span data-stu-id="316c1-105">The following sections provide an overview of code access security.</span></span> <span data-ttu-id="316c1-106">如需此節中涵蓋之主題的詳細資訊，請參閱 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK 文件中的＜安全性原則模型＞。</span><span class="sxs-lookup"><span data-stu-id="316c1-106">For more detailed information about the topics covered in this section, see "Security Policy Model" in the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK documentation.</span></span>  
  
 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="316c1-107">使用程式碼存取安全性的原因是，雖然報表伺服器是以 [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] 技術為基礎，但是一般 [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] 應用程式與報表伺服器之間仍有大幅差異。</span><span class="sxs-lookup"><span data-stu-id="316c1-107">uses code access security because, although the report server is built on [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] technology, there is a substantial difference between a typical [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] application and the report server.</span></span> <span data-ttu-id="316c1-108">一般 [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] 應用程式不會執行使用者程式碼。</span><span class="sxs-lookup"><span data-stu-id="316c1-108">A typical [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] application does not execute user code.</span></span> <span data-ttu-id="316c1-109">反之，[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 會使用開放且可延伸的架構，允許使用者使用報表定義語言的 **Code** 項目針對報表定義檔案進行程式設計，以及在自訂組件中開發專用功能，以便用於報表中。</span><span class="sxs-lookup"><span data-stu-id="316c1-109">In contrast, [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] uses an open and extensible architecture that allows users to program against the report definition files using the **Code** element of the Report Definition Language and to develop specialized functionality into a custom assembly for use in reports.</span></span> <span data-ttu-id="316c1-110">此外，開發人員可以設計和開發功能強大的延伸模組，以便強化報表伺服器的功能。</span><span class="sxs-lookup"><span data-stu-id="316c1-110">Furthermore, developers can design and deploy powerful extensions that enhance the capabilities of the report server.</span></span> <span data-ttu-id="316c1-111">由於這項強大功能與彈性，因此產生了盡可能提供保護與安全性的需求。</span><span class="sxs-lookup"><span data-stu-id="316c1-111">With this power and flexibility comes the need to provide as much protection and security as possible.</span></span>  
  
 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="316c1-112">開發人員可以在報表中使用任何 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 組件，而且能以原生方式呼叫所有部署至全域組件快取之組件的功能。</span><span class="sxs-lookup"><span data-stu-id="316c1-112">developers can use any [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] assembly in their reports and natively call upon all of the functionality of assemblies deployed to the global assembly cache.</span></span> <span data-ttu-id="316c1-113">報表伺服器唯一可控制的事項就是要針對報表運算式和載入的自訂組件提供哪些權限。</span><span class="sxs-lookup"><span data-stu-id="316c1-113">The only thing that the report server can control is what permissions are given for report expressions and loaded custom assemblies.</span></span> <span data-ttu-id="316c1-114">在 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 中，自訂組件預設會收到僅限**執行**的權限。</span><span class="sxs-lookup"><span data-stu-id="316c1-114">In [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], custom assemblies receive **Execute**-only permissions by default.</span></span>  
  
## <a name="evidence"></a><span data-ttu-id="316c1-115">辨識項</span><span class="sxs-lookup"><span data-stu-id="316c1-115">Evidence</span></span>  
 <span data-ttu-id="316c1-116">辨識項是指 Common Language Runtime (CLR) 用來決定程式碼組件之安全性原則的資訊。</span><span class="sxs-lookup"><span data-stu-id="316c1-116">Evidence is the information that the common language runtime (CLR) uses to determine a security policy for code assemblies.</span></span> <span data-ttu-id="316c1-117">辨識項會向執行階段指出程式碼具有特定特性。</span><span class="sxs-lookup"><span data-stu-id="316c1-117">Evidence indicates to the runtime that code has a particular characteristic.</span></span> <span data-ttu-id="316c1-118">常見的辨識項形式包括數位簽章和組件的位置。</span><span class="sxs-lookup"><span data-stu-id="316c1-118">Common forms of evidence include digital signatures and the location of an assembly.</span></span> <span data-ttu-id="316c1-119">不過，您也可以自行設計辨識項，以便表示對應用程式有意義的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="316c1-119">Evidence can also be custom designed to represent other information that is meaningful to the application.</span></span>  
  
 <span data-ttu-id="316c1-120">組件和應用程式網域都是根據辨識項收到權限。</span><span class="sxs-lookup"><span data-stu-id="316c1-120">Both assemblies and application domains receive permissions based on evidence.</span></span> <span data-ttu-id="316c1-121">例如，[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 嘗試存取之組件的位置是其中一種常見的弱式名稱組件辨識項形式。</span><span class="sxs-lookup"><span data-stu-id="316c1-121">For example, the location of an assembly that [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] is attempting to access is one common form of evidence for weak-named assemblies.</span></span> <span data-ttu-id="316c1-122">這稱為 URL 辨識項。</span><span class="sxs-lookup"><span data-stu-id="316c1-122">This is known as URL evidence.</span></span> <span data-ttu-id="316c1-123">部署至報表伺服器之自訂資料處理延伸模組的 URL 辨識項可能是 "C:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer\bin\Microsoft.Samples.ReportingServices.FsiDataExtension.dll"。</span><span class="sxs-lookup"><span data-stu-id="316c1-123">URL evidence for a custom data processing extension deployed to a report server might be "C:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer\bin\Microsoft.Samples.ReportingServices.FsiDataExtension.dll".</span></span> <span data-ttu-id="316c1-124">組件的強式名稱或數位簽章是另一種常見的辨識項形式。</span><span class="sxs-lookup"><span data-stu-id="316c1-124">The strong name or digital signature of an assembly is another common form of evidence.</span></span> <span data-ttu-id="316c1-125">在此情況下，辨識項就是組件的公開金鑰資訊。</span><span class="sxs-lookup"><span data-stu-id="316c1-125">In this case, the evidence is the public key information for an assembly.</span></span>  
  
## <a name="code-groups"></a><span data-ttu-id="316c1-126">程式碼群組</span><span class="sxs-lookup"><span data-stu-id="316c1-126">Code Groups</span></span>  
 <span data-ttu-id="316c1-127">程式碼群組是具有指定成員資格條件的程式碼邏輯群組。</span><span class="sxs-lookup"><span data-stu-id="316c1-127">A code group is a logical grouping of code that has a specified condition for membership.</span></span> <span data-ttu-id="316c1-128">任何符合成員資格條件的程式碼都包含在此群組中。</span><span class="sxs-lookup"><span data-stu-id="316c1-128">Any code that meets the membership condition is included in the group.</span></span> <span data-ttu-id="316c1-129">系統管理員會透過管理程式碼群組及其相關聯的權限集合，設定安全性原則。</span><span class="sxs-lookup"><span data-stu-id="316c1-129">Administrators configure a security policy by managing code groups and their associated permission sets.</span></span>  
  
 <span data-ttu-id="316c1-130">程式碼群組的成員資格條件是以辨識項為基礎。</span><span class="sxs-lookup"><span data-stu-id="316c1-130">A membership condition for a code group is based on evidence.</span></span> <span data-ttu-id="316c1-131">例如，程式碼群組的 URL 成員資格是以 URL 辨識項為基礎。</span><span class="sxs-lookup"><span data-stu-id="316c1-131">For example, a URL membership for a code group is based on URL evidence.</span></span> <span data-ttu-id="316c1-132">Common Language Runtime (CLR) 會使用識別特性 (例如 URL 辨識項) 來描述程式碼以及判斷是否符合群組的成員資格條件。</span><span class="sxs-lookup"><span data-stu-id="316c1-132">The common language runtime (CLR) uses identifying characteristics such as URL evidence to describe the code and to determine whether a group's membership condition has been met.</span></span> <span data-ttu-id="316c1-133">例如，如果程式碼群組的成員資格條件是「組件中的程式碼 C:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer\bin\Microsoft.Samples.ReportingServices.FsiDataExtension.dll」，執行階段就會檢查辨識項，以便判斷程式碼是否源自該位置。</span><span class="sxs-lookup"><span data-stu-id="316c1-133">For example, if the membership condition of a code group is "code in the assembly C:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer\bin\Microsoft.Samples.ReportingServices.FsiDataExtension.dll", the runtime examines the evidence to determine whether the code originates from that location.</span></span> <span data-ttu-id="316c1-134">這種程式碼群組的組態項目範例可能如下所示：</span><span class="sxs-lookup"><span data-stu-id="316c1-134">An example of a configuration entry for this type of code group might look like the following:</span></span>  
  
```  
<CodeGroup class="UnionCodeGroup"  
   version="1"  
   PermissionSetName="FullTrust"  
   Name="MyCodeGroup"  
   Description="Code group for my data processing extension">  
      <IMembershipCondition class="UrlMembershipCondition"  
         version="1"  
         Url="C:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer\bin\Microsoft.Samples.ReportingServices.FsiDataExtension.dll"  
       />  
</CodeGroup>  
```  
  
 <span data-ttu-id="316c1-135">您應該與系統管理員或應用程式部署專家一起判斷自訂組件或 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 延伸模組所需的程式碼存取安全性和程式碼群組類型。</span><span class="sxs-lookup"><span data-stu-id="316c1-135">You should work with your system administrator or application deployment expert to determine the type of code access security and code groups that your custom assemblies or [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] extensions require.</span></span>  
  
## <a name="named-permission-sets"></a><span data-ttu-id="316c1-136">具名使用權限集合</span><span class="sxs-lookup"><span data-stu-id="316c1-136">Named Permission Sets</span></span>  
 <span data-ttu-id="316c1-137">具名使用權限集合是指系統管理員可用來與程式碼群組建立關聯的權限集合。</span><span class="sxs-lookup"><span data-stu-id="316c1-137">A named permission set is a set of permissions that administrators can associate with a code group.</span></span> <span data-ttu-id="316c1-138">大部分具名使用權限集合都至少包含一個權限、名稱和權限集合的描述。</span><span class="sxs-lookup"><span data-stu-id="316c1-138">Most named permission sets consist of at least one permission, a name, and description for the permission set.</span></span> <span data-ttu-id="316c1-139">系統管理員可以使用具名使用權限集合來建立或修改程式碼群組的安全性原則。</span><span class="sxs-lookup"><span data-stu-id="316c1-139">Administrators can use named permission sets to establish or modify the security policy for code groups.</span></span> <span data-ttu-id="316c1-140">相同的具名使用權限集合可以與多個程式碼群組產生關聯。</span><span class="sxs-lookup"><span data-stu-id="316c1-140">More than one code group can be associated with the same named permission set.</span></span> <span data-ttu-id="316c1-141">CLR 提供了一些內建的具名使用權限集合，包括 **Nothing**、**Execution**、**Internet**、**LocalIntranet**、**Everything** 和 **FullTrust**。</span><span class="sxs-lookup"><span data-stu-id="316c1-141">The CLR provides built-in named permission sets; among these are **Nothing**, **Execution**, **Internet**, **LocalIntranet**, **Everything**, and **FullTrust**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="316c1-142">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 中的自訂資料、傳遞、轉譯和安全性延伸模組必須在 **FullTrust** 權限集合底下執行。</span><span class="sxs-lookup"><span data-stu-id="316c1-142">Custom data, delivery, rendering, and security extensions in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] must run under the **FullTrust** permission set.</span></span> <span data-ttu-id="316c1-143">請與系統管理員一起針對 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 延伸模組加入適當的程式碼群組和成員資格條件。</span><span class="sxs-lookup"><span data-stu-id="316c1-143">Work with your system administrator to add the appropriate code group and membership conditions for your [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] extensions.</span></span>  
  
 <span data-ttu-id="316c1-144">您可以將自己使用之自訂組件的自訂權限等級與報表產生關聯。</span><span class="sxs-lookup"><span data-stu-id="316c1-144">You can associate your own custom levels of permissions for custom assemblies that you use with reports.</span></span> <span data-ttu-id="316c1-145">例如，如果您想要允許組件存取特定檔案，就可以建立具有特定檔案 I/O 存取權的具名使用權限集合，然後將該權限集合指派給程式碼群組。</span><span class="sxs-lookup"><span data-stu-id="316c1-145">For example, if you want to allow an assembly to access a specific file, you can create a new named permission set with specific file I/O access and then assign the permission set to your code group.</span></span> <span data-ttu-id="316c1-146">下列權限集合會授與 MyFile.xml 檔的唯讀存取權：</span><span class="sxs-lookup"><span data-stu-id="316c1-146">The following permission set grants read-only access to the file MyFile.xml:</span></span>  
  
```  
<PermissionSet class="NamedPermissionSet"  
   version="1"  
   Name="MyNewFilePermissionSet"  
   Description="A special permission set that grants read access to my file.">  
    <IPermission class="FileIOPermission"  
       version="1"  
       Read="C:\MyFile.xml"/>  
    <IPermission class="SecurityPermission"  
       version="1"  
       Flags="Assertion, Execution"/>  
</PermissionSet>  
```  
  
 <span data-ttu-id="316c1-147">您授與此權限集合的程式碼群組可能如下所示：</span><span class="sxs-lookup"><span data-stu-id="316c1-147">A code group that you grant this permission set might look like the following:</span></span>  
  
```  
<CodeGroup class="UnionCodeGroup"  
   version="1"  
   PermissionSetName="MyNewFilePermissionSet"  
   Name="MyNewCodeGroup"  
   Description="A special code group for my custom assembly.">  
   <IMembershipCondition class="UrlMembershipCondition"  
      version="1"  
      Url="C:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer\bin\MyCustomAssembly.dll"/>  
</CodeGroup>  
```  
  
## <a name="see-also"></a><span data-ttu-id="316c1-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="316c1-148">See Also</span></span>  
 [<span data-ttu-id="316c1-149">安全開發 &#40;Reporting Services&#41;</span><span class="sxs-lookup"><span data-stu-id="316c1-149">Secure Development &#40;Reporting Services&#41;</span></span>](secure-development-reporting-services.md)  
  
  
