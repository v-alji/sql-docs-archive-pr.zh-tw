---
title: 使用強式名稱自訂組件 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- AllowPartiallyTrustedCallersAttribute attribute
- strong-named custom assemblies [Reporting Services]
- strong names [Reporting Services]
- assemblies [Reporting Services], strong names
- custom assemblies [Reporting Services], strong-named
ms.assetid: ca9f19d7-6e86-46f2-b9ad-9bf807eaa52e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5e685ecda39e0487eb4b469920820fa6e4a10daa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585156"
---
# <a name="using-strong-named-custom-assemblies"></a><span data-ttu-id="91e13-102">使用強式名稱自訂組件</span><span class="sxs-lookup"><span data-stu-id="91e13-102">Using Strong-Named Custom Assemblies</span></span>
  <span data-ttu-id="91e13-103">強式名稱會識別組件，並且含括組件的文字名稱、四部分的版本號碼、文化特性資訊 (若有提供)、公用金鑰，以及儲存在組件資訊清單中的數位簽章。</span><span class="sxs-lookup"><span data-stu-id="91e13-103">A strong name identifies an assembly and includes the assembly's text name, four-part version number, culture information (if provided), a public key, and a digital signature stored in the assembly's manifest.</span></span> <span data-ttu-id="91e13-104">強式名稱可唯一識別 Common Language Runtime (CLR) 並確保二進位的完整性。</span><span class="sxs-lookup"><span data-stu-id="91e13-104">A strong name uniquely identifies an assembly to the common language runtime (CLR) and ensures binary integrity.</span></span>  
  
## <a name="using-allowpartiallytrustedcallersattribute"></a><span data-ttu-id="91e13-105">使用 AllowPartiallyTrustedCallersAttribute</span><span class="sxs-lookup"><span data-stu-id="91e13-105">Using AllowPartiallyTrustedCallersAttribute</span></span>  
 <span data-ttu-id="91e13-106">若要在報表中使用強式名稱組件，則必須允許使用組件的 **AllowPartiallyTrustedCallers** 屬性之部分信任程式碼，呼叫強式名稱組件。</span><span class="sxs-lookup"><span data-stu-id="91e13-106">To use strong-named assemblies with reports, you must allow your strong-named assembly to be called by partially trusted code using the assembly's **AllowPartiallyTrustedCallers** attribute.</span></span> <span data-ttu-id="91e13-107">您可以使用 **AllowPartiallyTrustedCallersAttribute**，來允許報表設計師或是報表運算式中的報表伺服器呼叫強式名稱組件。</span><span class="sxs-lookup"><span data-stu-id="91e13-107">You can use **AllowPartiallyTrustedCallersAttribute** to allow strong-named assemblies to be called by Report Designer or the report server in report expressions.</span></span> <span data-ttu-id="91e13-108">若要允許部分信任的程式碼呼叫強式名稱組件，請將下列組件層級屬性加入組件屬性檔。</span><span class="sxs-lookup"><span data-stu-id="91e13-108">To allow partially trusted code to call strong-named assemblies, add the following assembly-level attribute to your assembly attribute file.</span></span>  
  
```vb  
<assembly:AllowPartiallyTrustedCallers>  
```  
  
```csharp  
[assembly:AllowPartiallyTrustedCallers]  
```  
  
 <span data-ttu-id="91e13-109">**AllowPartiallyTrustedCallersAttribute** 只有在組件層級由強式名稱組件套用時才有效。</span><span class="sxs-lookup"><span data-stu-id="91e13-109">**AllowPartiallyTrustedCallersAttribute** is effective only when applied by a strong-named assembly at the assembly level.</span></span> <span data-ttu-id="91e13-110">如需在元件層級套用屬性的詳細資訊，請參閱 SDK 檔中的「套用屬性」 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="91e13-110">For more information about applying attributes at the assembly level, see "Applying Attributes" in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK documentation.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="91e13-111">當 **AllowPartiallyTrustedCallersAttribute** 存在時，會防止預設的 **FullTrustLinkDemand** 安全性檢查，以確定可從任何其他部分信任的組件呼叫組件。</span><span class="sxs-lookup"><span data-stu-id="91e13-111">When **AllowPartiallyTrustedCallersAttribute** is present, the default **FullTrustLinkDemand** security checks are prevented, making the assembly callable from any other partially trusted assembly.</span></span> <span data-ttu-id="91e13-112">所有的安全性檢查都必須明確地陳述，包括類別層級或是方法層級宣告的安全性屬性。</span><span class="sxs-lookup"><span data-stu-id="91e13-112">All security checks, including class-level or method-level declarative security attributes, must be explicitly stated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91e13-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="91e13-113">See Also</span></span>  
 [<span data-ttu-id="91e13-114">將自訂組件與報表搭配使用</span><span class="sxs-lookup"><span data-stu-id="91e13-114">Using Custom Assemblies with Reports</span></span>](using-custom-assemblies-with-reports.md)  
  
  
