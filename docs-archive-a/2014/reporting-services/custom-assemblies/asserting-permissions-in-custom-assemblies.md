---
title: 自訂組件中的判斷提示權限 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- secure calls [Reporting Services]
- custom assemblies [Reporting Services], permissions
- permission sets [Reporting Services]
- asserting permissions
- permissions [Reporting Services], custom assemblies
- limited permission sets
- security configuration files [Reporting Services]
ms.assetid: 3afb9631-f15e-405e-990b-ee102828f298
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: cba3c0b74712b6b4d0f6b5c58925cfd562f0df77
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584286"
---
# <a name="asserting-permissions-in-custom-assemblies"></a><span data-ttu-id="ae3be-102">自訂組件中的判斷提示權限</span><span class="sxs-lookup"><span data-stu-id="ae3be-102">Asserting Permissions in Custom Assemblies</span></span>
  <span data-ttu-id="ae3be-103">根據預設，自訂組譯碼會使用有限的 **Execution** 權限集合執行。</span><span class="sxs-lookup"><span data-stu-id="ae3be-103">By default, custom assembly code runs with the limited **Execution** permission set.</span></span> <span data-ttu-id="ae3be-104">在某些情況下，您可能希望實作自訂組件，以安全地呼叫在安全性系統中受保護的資源 (例如檔案或是登錄)。</span><span class="sxs-lookup"><span data-stu-id="ae3be-104">In some cases, you may wish to implement a custom assembly that makes secured calls to protected resources within your security system (such as a file or the registry).</span></span> <span data-ttu-id="ae3be-105">若要完成這個動作，您必須執行下列項目：</span><span class="sxs-lookup"><span data-stu-id="ae3be-105">In order to accomplish this, you must do the following:</span></span>  
  
1.  <span data-ttu-id="ae3be-106">識別您程式碼所需的完整權限，以進行安全的呼叫。</span><span class="sxs-lookup"><span data-stu-id="ae3be-106">Identify the exact permissions that your code needs in order to make the secured call.</span></span> <span data-ttu-id="ae3be-107">如果這個方法是程式庫的一部分 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] ，這項資訊應該包含在方法檔中。</span><span class="sxs-lookup"><span data-stu-id="ae3be-107">If this method is part of a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] library, this information should be included in the method documentation.</span></span>  
  
2.  <span data-ttu-id="ae3be-108">修改報表伺服器原則組態檔，以授與自訂組件所需的權限。</span><span class="sxs-lookup"><span data-stu-id="ae3be-108">Modify the report server policy configuration files in order to grant the custom assembly the required permissions.</span></span> <span data-ttu-id="ae3be-109">如需安全性原則設定檔的詳細資訊，請參閱[使用 Reporting Services 安全性原則檔](../extensions/secure-development/using-reporting-services-security-policy-files.md)。</span><span class="sxs-lookup"><span data-stu-id="ae3be-109">For more information about the security policy configuration files, see [Using Reporting Services Security Policy Files](../extensions/secure-development/using-reporting-services-security-policy-files.md).</span></span>  
  
3.  <span data-ttu-id="ae3be-110">判斷提示所需的權限，做為進行安全呼叫的方法之一部分。</span><span class="sxs-lookup"><span data-stu-id="ae3be-110">Assert the required permissions as part of the method in which the secure call is made.</span></span> <span data-ttu-id="ae3be-111">這是必要的動作，因為報表伺服器所呼叫的自訂組譯碼是報表運算式主機組件的一部分，報表運算式主機組件預設會以 **Execution** 權限執行。</span><span class="sxs-lookup"><span data-stu-id="ae3be-111">This is required because the custom assembly code that is called by the report server is part of the report expression host assembly, which runs with **Execution** permission by default.</span></span> <span data-ttu-id="ae3be-112">**Execution** 權限集合允許執行程式碼，但不允許使用受保護的資源。</span><span class="sxs-lookup"><span data-stu-id="ae3be-112">The **Execution** permission set enables code to run, but not to use protected resources.</span></span>  
  
4.  <span data-ttu-id="ae3be-113">如果使用強式名稱簽署自訂組件，請將它標示為 **AllowPartiallyTrustedCallersAttribute**。</span><span class="sxs-lookup"><span data-stu-id="ae3be-113">Mark the custom assembly with **AllowPartiallyTrustedCallersAttribute** if it is signed with a strong name.</span></span> <span data-ttu-id="ae3be-114">這是必要的動作，因為自訂組件是從報表運算式中呼叫，而報表運算式是報表運算式主機組件的一部分，所以預設不會授與 **FullTrust**，因此它屬於「部分信任的」呼叫端。</span><span class="sxs-lookup"><span data-stu-id="ae3be-114">This is required because custom assemblies are called from a report expression that is part of the report expression host assembly, which, by default, is not granted **FullTrust**; thus it is a "partially trusted" caller.</span></span> <span data-ttu-id="ae3be-115">如需詳細資訊，請參閱[使用強式名稱自訂組件](using-strong-named-custom-assemblies.md)。</span><span class="sxs-lookup"><span data-stu-id="ae3be-115">For more information, see [Using Strong-Named Custom Assemblies](using-strong-named-custom-assemblies.md).</span></span>  
  
## <a name="implementing-a-secure-call"></a><span data-ttu-id="ae3be-116">實作安全呼叫</span><span class="sxs-lookup"><span data-stu-id="ae3be-116">Implementing a Secure Call</span></span>  
 <span data-ttu-id="ae3be-117">您可以修改原則組態檔，以授與組件特定權限。</span><span class="sxs-lookup"><span data-stu-id="ae3be-117">You can modify the policy configuration files to grant your assembly specific permissions.</span></span> <span data-ttu-id="ae3be-118">例如，如果您正在撰寫用來進行貨幣轉換的自訂組件，可能需要從檔案讀取目前的貨幣匯率。</span><span class="sxs-lookup"><span data-stu-id="ae3be-118">For example, if you were writing a custom assembly to handle currency conversion, you might need to read the current currency exchange rates from a file.</span></span> <span data-ttu-id="ae3be-119">若要擷取匯率資訊，您需要將額外的安全性權限 **FileIOPermission** 新增至組件的權限集合。</span><span class="sxs-lookup"><span data-stu-id="ae3be-119">To retrieve the rate information, you would need to add an additional security permission, **FileIOPermission**, to your permission set for the assembly.</span></span> <span data-ttu-id="ae3be-120">您可以在原則組態檔中建立下列其他項目：</span><span class="sxs-lookup"><span data-stu-id="ae3be-120">You can make the following additional entry in the policy configuration file:</span></span>  
  
```  
<PermissionSet class="NamedPermissionSet"  
   version="1"  
   Name="CurrencyRatesFilePermissionSet"  
   Description="A special permission set that grants read access to my currency rates file.">  
      <IPermission class="FileIOPermission"  
         version="1"  
         Read="C:\CurrencyRates.xml"/>  
      <IPermission class="SecurityPermission"  
         version="1"  
         Flags="Execution, Assertion"/>  
</PermissionSet>  
```  
  
 <span data-ttu-id="ae3be-121">然後，您可以加入參考該權限集合的程式碼群組：</span><span class="sxs-lookup"><span data-stu-id="ae3be-121">You then add a code group that references that permission set:</span></span>  
  
```  
<CodeGroup class="UnionCodeGroup"  
   version="1"  
   PermissionSetName="CurrencyRatesFilePermissionSet"  
   Name="MyNewCodeGroup"  
   Description="A special code group for my custom assembly.">  
   <IMembershipCondition class="UrlMembershipCondition"  
      version="1"  
      Url="C:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\MSSQL\Reporting Services\ReportServer\bin\CurrencyConversion.dll"/>  
</CodeGroup>  
```  
  
 <span data-ttu-id="ae3be-122">為了讓您的程式碼取得適當的權限，必須在自訂組件程式碼中判斷提示權限。</span><span class="sxs-lookup"><span data-stu-id="ae3be-122">In order for your code to acquire the appropriate permission, you must assert the permission within your custom assembly code.</span></span> <span data-ttu-id="ae3be-123">例如，如果您想要將唯讀存取權加入 XML 檔案 C:\CurrencyRates.xml 中，必須將下列程式碼加入您的方法：</span><span class="sxs-lookup"><span data-stu-id="ae3be-123">For example, if you want to add read-only access to an XML file, C:\CurrencyRates.xml, you must add the following code to your method:</span></span>  
  
```  
// C#  
FileIOPermission permission = new FileIOPermission(FileIOPermissionAccess.Read, @"C:\CurrencyRates.xml");  
try  
{  
   permission.Assert();  
   // Load the XML currency rates file  
   XmlDocument doc = new XmlDocument();  
   doc.Load(@"C:\CurrencyRates.xml");  
...  
```  
  
 <span data-ttu-id="ae3be-124">您也可以加入判斷提示，將其做為方法屬性：</span><span class="sxs-lookup"><span data-stu-id="ae3be-124">You can also add the assertion as a method attribute:</span></span>  
  
```  
[FileIOPermissionAttribute(SecurityAction.Assert, Read=@"C:\CurrencyRates.xml")]  
```  
  
 <span data-ttu-id="ae3be-125">如需詳細資訊，請參閱＜.NET Framework 開發人員指南＞中的＜.NET Framework 安全性＞。</span><span class="sxs-lookup"><span data-stu-id="ae3be-125">For more information, see ".NET Framework Security" in the .NET Framework Developer's Guide.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae3be-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ae3be-126">See Also</span></span>  
 [<span data-ttu-id="ae3be-127">將自訂組件與報表搭配使用</span><span class="sxs-lookup"><span data-stu-id="ae3be-127">Using Custom Assemblies with Reports</span></span>](using-custom-assemblies-with-reports.md)  
  
  
